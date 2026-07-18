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

| Scenario | Detection Source | Event ID | Description |
|---|---|---|---|
| Process Creation | Sysmon | Event ID 1 | Monitored process execution, command-line arguments, and parent-child relationships |
| PowerShell Execution | Sysmon | Event ID 1 | Analyzed PowerShell activity and command-line execution |
| Suspicious Process Creation | Sysmon | Event ID 1 | Investigated unusual processes, execution paths, and parent-child process relationships |
| Failed Login Attempts | Windows Security Logs + Wazuh SIEM | Event ID 4625 | Detected unsuccessful authentication attempts |
| Account Creation | Windows Security Logs | Event ID 4720 | Monitored creation of new user accounts |
