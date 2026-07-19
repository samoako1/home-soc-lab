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
- Monitoring:
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

- Operating System: Ubuntu Server
- SIEM Platform: Wazuh
- Log Collection: Filebeat
- Search Engine: Elasticsearch
- Dashboard: Wazuh Dashboard

---

# Network Architecture
