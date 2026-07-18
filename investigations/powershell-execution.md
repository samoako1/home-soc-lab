# PowerShell Execution Investigation

## Objective

Detect and investigate PowerShell execution activity on a Windows endpoint using Sysmon telemetry and Wazuh alerting.

## Detection Source

- Log Source: Sysmon
- Event ID: 1 (Process Creation)
- Detection Platform: Wazuh
- Wazuh Rule: 92027 - Powershell process spawned powershell instance
- MITRE ATT&CK: T1059.001 - Command and Scripting Interpreter: PowerShell

## Scenario

Multiple PowerShell commands were executed on the Windows 11 endpoint to validate Sysmon process monitoring and Wazuh detection capabilities.

The following commands were tested:

```powershell
whoami
Get-Process
Get-Service
powershell.exe -NoProfile -ExecutionPolicy Bypass -Command "Get-ChildItem C:\Users"\
