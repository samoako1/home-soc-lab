# Home SOC Lab Setup

## Objective

The objective of this project is to build a home Security Operations Center (SOC) environment to practice endpoint monitoring, security event analysis, threat detection, and incident investigation.

The lab simulates a small enterprise environment where endpoint telemetry is collected from a Windows machine, forwarded to a centralized SIEM, and analyzed for suspicious security activity.

---

# Current Environment

## Host Machine

- Operating System: macOS
- Processor: Intel
- Virtualization Platform: VirtualBox

---

# Virtual Machines

## Windows Endpoint

Purpose:

- Generate security telemetry
- Simulate security events
- Execute investigation scenarios
- Provide endpoint data to the SOC server

Configuration:

- Operating System: Windows 11 Home
- Monitoring Tools:
  - Sysmon
  - Wazuh Agent
  - Windows Security Logs

Collected Telemetry:

- Process creation events
- PowerShell activity
- Authentication failures
- User account creation
- Registry modifications
- Windows event log clearing

---

## SOC Server

Purpose:

- Centralize endpoint telemetry
- Analyze security events
- Generate detection alerts
- Map activity to MITRE ATT&CK techniques

Configuration:

- Operating System: Ubuntu Server 24.04 LTS
- SIEM Platform: Wazuh
- Log Collection: Filebeat
- Search Engine: Elasticsearch
- Visualization: Wazuh Dashboard

---

# Network Architecture

```
                 VirtualBox Network

        +-----------------------------+
        |                             |
        |                             |
 Windows 11 VM                 Ubuntu SOC Server
 192.168.222.131               192.168.222.130

        |                             |
        |                             |
  Wazuh Agent                  Wazuh Manager
  Sysmon Logs                  Filebeat
  Security Logs                Elasticsearch
                              Wazuh Dashboard

```

---

# Completed Setup

- [x] Installed VirtualBox
- [x] Created Windows 11 virtual machine
- [x] Created Ubuntu SOC server
- [x] Installed Sysmon on Windows endpoint
- [x] Installed Wazuh Agent on Windows endpoint
- [x] Connected Windows endpoint to Wazuh Manager
- [x] Verified endpoint communication
- [x] Configured Filebeat log ingestion
- [x] Verified Windows telemetry appears in Wazuh
- [x] Created security investigation scenarios
- [x] Mapped detections to MITRE ATT&CK techniques

---

# Detection Scenarios Implemented

| Scenario | Log Source | Event ID / Rule | MITRE ATT&CK |
|---|---|---|---|
| Failed Login Attempts | Windows Security Logs | Event ID 4625 | T1110 - Brute Force |
| PowerShell Execution | Sysmon | Event ID 1 | T1059.001 - PowerShell |
| User Account Creation | Windows Security Logs | Event ID 4720 | T1136 - Create Account |
| Registry Modification | Wazuh FIM / Syscheck | Rule ID 752 | T1112 - Modify Registry |
| Event Log Clearing | Windows Security Logs | Event ID 1102 | T1070.001 - Clear Windows Event Logs |

---

# Skills Practiced

- Virtual machine deployment
- Windows endpoint administration
- Linux server administration
- SIEM deployment and configuration
- Endpoint telemetry collection
- Sysmon event analysis
- Windows security log investigation
- Threat detection engineering
- MITRE ATT&CK mapping
- Security alert investigation workflows
