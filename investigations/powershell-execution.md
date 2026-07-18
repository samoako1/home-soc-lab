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
```
The final command was selected as the primary investigation artifact because it generated a Wazuh detection and demonstrated visibility into PowerShell execution parameters, including the use of -ExecutionPolicy Bypass


## Investigation Steps

1. Executed PowerShell commands on the Windows endpoint.
2. Verified that Sysmon captured the activity through Event ID 1 (Process Creation).
3. Reviewed Sysmon event details including:
   - Process name
   - Command-line arguments
   - User account
   - Parent process
   - Process hashes
4. Confirmed that Wazuh received and analyzed the Sysmon event.
5. Reviewed the generated Wazuh alert.

## Findings

Sysmon successfully captured the PowerShell process creation event with detailed execution information.

The event contained the following details:

- Process:
  - `powershell.exe`

- User:
  - `homelab\samoa`

- Command Line:
  - `powershell.exe -NoProfile -ExecutionPolicy Bypass -Command "Get-ChildItem C:\Users"`

- Parent Process:
  - `powershell.exe`

Wazuh generated an alert:

- Rule ID: 92027
- Description: Powershell process spawned powershell instance
- Agent: homelab

The detection demonstrates Wazuh's ability to collect endpoint telemetry and identify potentially suspicious PowerShell execution behavior.

## MITRE ATT&CK Mapping

- Technique ID: T1059.001
- Technique Name: Command and Scripting Interpreter: PowerShell
- Tactic: Execution

## Evidence

Screenshots:

- Sysmon Event ID 1 showing PowerShell process creation:
  - `screenshots/sysmon/`

- Wazuh PowerShell detection alert:
  - `screenshots/powershell/`

## Outcome

Successfully demonstrated centralized detection of PowerShell execution activity using Sysmon and Wazuh. The investigation shows how endpoint telemetry can be collected, analyzed, and mapped to MITRE ATT&CK techniques.
