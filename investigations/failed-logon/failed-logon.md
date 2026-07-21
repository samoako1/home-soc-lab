# Failed Login Investigation

## Objective
Detect and investigate failed login attempts on a Windows endpoint using Wazuh.

## Detection Source
- Windows Security Logs
- Event ID: 4625
- Detection Platform: Wazuh
- MITRE ATT&CK: T1110 (Brute Force)

## Scenario
Multiple failed login attempts were generated on the Windows 11 endpoint by entering an incorrect password during authentication.

## Investigation Steps
1. Opened the Wazuh Dashboard.
2. Navigated to Security Events.
3. Filtered for:
   agent.name: homelab
4. Identified Windows Security Event ID 4625.
5. Reviewed event details including:
   - Username
   - Source host
   - Timestamp
   - Failure reason

## Findings
Wazuh successfully collected and indexed Windows Security Event ID 4625 from the endpoint. The event was visible in the dashboard and contained authentication failure details that could indicate password guessing or brute-force activity.

## MITRE ATT&CK Mapping
- Technique: T1110
- Name: Brute Force

## Evidence
See screenshots in:
failed-logon

## Outcome
Successfully demonstrated centralized detection and investigation of failed login attempts using Wazuh.
