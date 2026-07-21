# Account Creation Investigation

## Objective
Detect and investigate the creation of a new local Windows user account using Wazuh.

## Detection Source
- Windows Security Logs
- Event ID: 4720
- Detection Platform: Wazuh
- MITRE ATT&CK: T1136 (Create Account)

## Scenario
A new local account named "labuser" was created on the Windows endpoint to simulate account manipulation activity.

## Investigation Steps
1. Created a new user account using PowerShell.
2. Opened the Wazuh dashboard.
3. Searched for events from the homelab endpoint.
4. Located Event ID 4720.
5. Reviewed details about the created account.

## Findings
Wazuh successfully detected the creation of a new local user account and forwarded the event to the central dashboard.

## MITRE ATT&CK Mapping
- T1136 - Create Account

## Evidence
See screenshots in account-creation

## Outcome
Successfully demonstrated centralized detection of account creation activity using Wazuh.
