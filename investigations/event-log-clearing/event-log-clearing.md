# Event Log Clearing Investigation

## Objective

Demonstrate Wazuh's ability to detect Windows Security Event Log clearing activity and identify behavior commonly associated with defense evasion techniques.

## Scenario

An event was generated after the Windows Security Event Log was cleared. Attackers may clear event logs to remove evidence of malicious activity and make forensic investigations more difficult.

## Detection Details

| Field | Value |
|---------|---------|
| Detection Platform | Wazuh |
| Windows Event ID | 1102 |
| Alert Description | Windows Security Event Log Cleared |
| MITRE ATT&CK | T1070.001 – Clear Windows Event Logs |
| Agent | homelab |

## Alert Evidence

Windows generated the following event:

```text
Event ID: 1102
The audit log was cleared.
```

Wazuh detected the event and generated an alert indicating that the Windows Security Event Log had been cleared.

## Analysis

Event log clearing is a common defense evasion technique used by attackers after gaining access to a system. By removing event logs, attackers attempt to hide evidence of malicious activity and reduce the effectiveness of security monitoring and forensic investigations.

During this investigation, Wazuh successfully detected the log clearing event and generated an alert, demonstrating the platform's ability to monitor and identify potentially suspicious administrative activity.

Potential malicious uses of event log clearing include:

- Removing evidence of unauthorized access
- Hiding malicious commands and processes
- Concealing account creation or privilege escalation
- Disrupting forensic investigations
- Evading security monitoring

## MITRE ATT&CK Mapping

### T1070.001 – Clear Windows Event Logs

Adversaries may clear Windows Event Logs to remove evidence of their actions and hinder incident response efforts.

## Outcome

This investigation confirmed that:

- Wazuh successfully detected Windows Security Event Log clearing activity.
- Windows Event ID 1102 was generated when the Security log was cleared.
- Security analysts can identify log tampering attempts through Wazuh alerts.
- The activity maps to MITRE ATT&CK technique T1070.001 (Clear Windows Event Logs).

## Screenshots

- Windows Event Viewer showing Event ID 1102
- Wazuh alert detecting Security Event Log clearing
- Wazuh alert details showing MITRE ATT&CK mapping
