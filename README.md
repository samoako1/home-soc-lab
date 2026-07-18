# Home SOC Lab

A cybersecurity home lab built using VirtualBox, Windows 11, Sysmon, and Wazuh to practice security monitoring, event analysis, and threat detection.

## Current Environment

- Host: Intel MacBook
- Virtualization: VirtualBox
- Endpoint: Windows 11 Home
- Monitoring: Sysmon
- SIEM: Wazuh 

## Objectives

- Collect Windows security telemetry
- Monitor process creation
- Analyze PowerShell activity
- Detect failed login attempts
- Detect account creation
- Centralize logs using Wazuh

## Completed

- [x] Installed VirtualBox
- [x] Created Windows 11 VM
- [x] Installed Sysmon
- [x] Verified Sysmon Event ID 1 logging
- [x] Configure Wazuh
- [x] Create security alerts

## Investigations

| Scenario | Log Source | Event ID | Detection Platform | MITRE ATT&CK | Description |
|----------|------------|----------|-------------------|--------------|-------------|
| Process Creation | Sysmon | Event ID 1 | Wazuh | T1059 | Monitored process execution, command-line arguments, and parent-child relationships. |
| PowerShell Execution | Sysmon | Event ID 1 | Wazuh | T1059.001 | Analyzed PowerShell activity and command-line execution. |
| Suspicious Process Execution | Sysmon | Event ID 1 | Wazuh | T1059 | Investigated unusual processes, execution paths, and parent-child relationships. |
| Failed Login Attempts | Windows Security Logs | Event ID 4625 | Wazuh | T1110 | Detected unsuccessful authentication attempts and potential brute-force activity. |
| User Account Creation | Windows Security Logs | Event ID 4720 | Wazuh | T1136 | Monitored creation of new user accounts and account management activity. |
| Registry Modification | Wazuh FIM / Syscheck | Rule ID 752 | Wazuh | T1112 | Detected Windows registry value additions and modifications through File Integrity Monitoring. |
