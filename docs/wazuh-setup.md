# Wazuh Setup

## Overview

Wazuh was deployed as the Security Information and Event Management (SIEM) platform for the Home SOC Lab.

The Wazuh deployment collects security telemetry from the Windows endpoint, analyzes events, applies detection rules, and provides dashboards for investigation.

---

# Wazuh Architecture

```
Windows 11 Endpoint
192.168.222.131

        |
        |
   Wazuh Agent
        |
        |
        v

Ubuntu SOC Server
192.168.222.130

        |
        |
   Wazuh Manager

        |
        |
   Filebeat

        |
        |
 Elasticsearch

        |
        |
 Wazuh Dashboard
```

---

# SOC Server Configuration

## Operating System

- Ubuntu Server 24.04 LTS

## Wazuh Components Installed

- Wazuh Manager
- Wazuh Indexer
- Filebeat
- Wazuh Dashboard

## Purpose of Each Component

### Wazuh Manager

Responsible for:

- Receiving endpoint data
- Analyzing security events
- Applying detection rules
- Generating alerts

---

### Wazuh Agent

Installed on the Windows endpoint to collect:

- Sysmon events
- Windows Security logs
- File integrity monitoring events
- System activity data

---

### Filebeat

Used to forward Wazuh alert data into Elasticsearch for indexing and dashboard visualization.

---

### Elasticsearch

Stores and indexes security event data collected by Wazuh.

---

### Wazuh Dashboard

Provides a graphical interface for:

- Searching alerts
- Investigating events
- Viewing agent status
- Analyzing security activity

---

# Windows Endpoint Configuration

## Agent Information

| Field | Value |
|---|---|
| Agent Name | homelab |
| Agent ID | 001 |
| Operating System | Windows 11 Home |
| IP Address | 192.168.222.131 |

---

# Agent Registration

The Windows endpoint was registered with the Wazuh Manager using the Wazuh agent enrollment process.

Verification command:

```bash
sudo /var/ossec/bin/agent_control -l
```

Expected output:

```
ID: 001
Name: homelab
Status: Active
```

The active status confirms successful communication between the endpoint and the Wazuh Manager.

---

# Filebeat Configuration

Filebeat was configured to ingest Wazuh alert data into Elasticsearch.

Configuration file:

```
/etc/filebeat/modules.d/wazuh.yml
```

Enabled Wazuh alerts:

```yaml
- module: wazuh
  alerts:
    enabled: true
    var.paths:
      - /var/ossec/logs/alerts/alerts.json
  archives:
    enabled: false
```

Configuration was verified using:

```bash
sudo filebeat test config
```

Expected result:

```
Config OK
```

---

# Windows Telemetry Collection

The Wazuh Agent collects security telemetry from multiple sources.

## Sysmon

Collected events:

- Event ID 1 - Process Creation
- Event ID 11 - File Creation

Used for:

- PowerShell monitoring
- Process investigation
- Suspicious activity detection

---

## Windows Security Logs

Collected events:

| Event ID | Description |
|---|---|
| 4625 | Failed login attempts |
| 4720 | User account creation |
| 1102 | Windows event log clearing |

---

## File Integrity Monitoring

Wazuh Syscheck was used to detect file and registry modifications.

Example detection:

```
Rule ID: 752
Description: Registry Value Entry Added to the System
MITRE: T1112 - Modify Registry
```

---

# Alert Verification

Wazuh alerts were verified through Elasticsearch.

Example command:

```bash
sudo curl -k -u admin \
'https://192.168.222.130:9200/_cat/indices?v'
```

Successful ingestion created Wazuh alert indices:

```
wazuh-alerts-4.x-2026.07.18
```

---

# Implemented Detection Scenarios

The following detections were successfully generated and investigated:

| Scenario | Source | Detection |
|---|---|---|
| PowerShell Execution | Sysmon | PowerShell process creation |
| Failed Login Attempts | Windows Security Logs | Authentication failure |
| User Account Creation | Windows Security Logs | New account creation |
| Event Log Clearing | Windows Security Logs | Defense evasion activity |
| Registry Modification | Wazuh FIM | Registry value modification |

---

# Troubleshooting Notes

## Filebeat Data Path Lock

If Filebeat is already running, manually starting another instance may produce:

```
data path already locked by another beat
```

Solution:

```bash
sudo systemctl stop filebeat
sudo filebeat -e
```

---

## Verifying Agent Communication

Check active agents:

```bash
sudo /var/ossec/bin/agent_control -l
```

Check Wazuh alerts:

```bash
sudo tail -f /var/ossec/logs/alerts/alerts.json
```

---

# Future Improvements

- Create custom Wazuh detection rules
- Add additional endpoints
- Integrate threat intelligence feeds
- Automate incident response actions
- Create custom dashboards