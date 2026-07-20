# Registry Modification Investigation

## Objective

Demonstrate Wazuh's ability to detect registry modifications on a Windows endpoint and identify activity that could be associated with persistence, defense evasion, or system configuration changes.

## Scenario

While monitoring the Windows 11 endpoint with Wazuh, a registry modification alert was generated indicating that a new registry value had been added to the system. Registry modifications are commonly monitored because attackers frequently use the Windows Registry to maintain persistence, alter system behavior, or evade detection.

## Detection Details

| Field | Value |
|---------|---------|
| Detection Platform | Wazuh |
| Rule ID | 752 |
| Alert Description | Registry Value Entry Added to the System |
| MITRE ATT&CK | T1112 – Modify Registry |
| Agent | homelab |
| Alert Level | 5 |

## Alert Evidence

Wazuh generated the following alert:

```text
Rule ID: 752
Description: Registry Value Entry Added to the System
MITRE ATT&CK: T1112 - Modify Registry
```

The alert identified a registry value being added within the Windows Firewall configuration area:

```text
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\
SharedAccess\Parameters\FirewallPolicy\
RestrictedServices\AppIso\FirewallRules
```

## Analysis

The registry modification was detected by Wazuh's file integrity and registry monitoring capabilities. The affected registry path is associated with Windows Firewall configuration settings.

Although this activity appeared to be legitimate Windows system behavior, the alert demonstrates that Wazuh can successfully monitor and detect registry changes that may be leveraged by attackers for persistence or system modification.

Potential malicious uses of registry modification include:

- Establishing persistence after reboot
- Disabling security controls
- Modifying firewall settings
- Hiding malicious activity
- Changing application execution behavior

## MITRE ATT&CK Mapping

### T1112 – Modify Registry

Adversaries may interact with the Windows Registry to store configuration information, establish persistence, or modify system behavior.

## Outcome

This investigation confirmed that:

- Wazuh successfully detected a registry modification event.
- Registry monitoring is functioning correctly on the Windows endpoint.
- Security analysts can identify and investigate registry changes through Wazuh alerts.
- Registry activity can be mapped to MITRE ATT&CK technique T1112 (Modify Registry).

## Screenshots

- Wazuh Alert: Rule 752 – Registry Value Entry Added to the System
- Alert Details Showing Registry Path
- Wazuh Dashboard Event View
