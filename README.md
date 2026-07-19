# Home SOC Lab

Built a home SOC environment using VirtualBox, Windows 11, Sysmon, and Wazuh to collect and analyze security telemetry. Created detections for PowerShell execution, failed logons, user account creation, event log clearing, and registry modifications mapped to MITRE ATT&CK techniques.

## Current Environment

- Host: Intel MacBook
- Virtualization: VirtualBox
- Endpoint: Windows 11 Home
- Monitoring: Sysmon
- SIEM: Wazuh 

## Objectives

- Collect Windows security telemetry using Sysmon
- Forward endpoint logs to a centralized SIEM
- Detect authentication failures
- Monitor account management activity
- Identify PowerShell execution
- Detect event log tampering
- Monitor registry modifications
- Investigate alerts using Wazuh

## Completed

- [x] Installed VirtualBox
- [x] Created Windows 11 VM
- [x] Installed Sysmon
- [x] Verified Sysmon Event ID 1 logging
- [x] Configure Wazuh
- [x] Create security alerts

## Investigations

| Scenario | Log Source | Event ID / Rule ID | Detection Platform | MITRE ATT&CK | Description |
|----------|------------|-------------------|-------------------|--------------|-------------|
| PowerShell Execution | Sysmon | Event ID 1 | Wazuh | T1059.001 | Analyzed PowerShell activity, command-line arguments, and execution behavior. |
| Event Log Clearing | Windows Security | Event ID 1102 | Wazuh | T1070.001 | Detected clearing of Windows Event Logs, a common defense evasion technique. |
| Failed Login Attempts | Windows Security | Event ID 4625 | Wazuh | T1110 | Detected unsuccessful authentication attempts and potential brute-force activity. |
| User Account Creation | Windows Security | Event ID 4720 | Wazuh | T1136 | Monitored creation of new user accounts and account management activity. |
| Registry Modification | Wazuh FIM / Syscheck | Rule ID 752 | Wazuh | T1112 | Detected Windows registry value additions and modifications through File Integrity Monitoring. |
