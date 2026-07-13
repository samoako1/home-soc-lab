# Home SOC Lab Setup

## Objective

The objective of this project is to build a home Security Operations Center (SOC) environment to practice endpoint monitoring, security event analysis, and threat detection.

The lab simulates a small enterprise environment where security telemetry is collected from a Windows endpoint and analyzed for suspicious activity.

## Current Environment

### Host Machine

- Operating System: macOS
- Processor: Intel
- Virtualization Platform: VirtualBox

### Virtual Machines

#### Windows Endpoint

Purpose:
- Generate security events
- Collect endpoint telemetry
- Simulate user activity and security scenarios

Configuration:
- Operating System: Windows 11 Home
- Monitoring Tool: Sysmon

#### SOC Server 

Purpose:
- Centralize security logs
- Create alerts
- Analyze endpoint activity

Planned Technology:
- Ubuntu Server
- Wazuh SIEM

## Completed Setup

- [x] Installed VirtualBox
- [x] Created Windows 11 virtual machine
- [x] Installed Sysmon
- [x] Verified Sysmon service is running
- [x] Verified Sysmon Event ID 1 process creation logging
- [x] Captured PowerShell execution telemetry

## Planned Improvements

- [ ] Configure Windows security auditing
- [ ] Create failed login detection scenario
- [ ] Create account creation detection scenario
- [ ] Add suspicious process investigations
- [ ] Deploy Wazuh SIEM
- [ ] Forward Windows logs to centralized monitoring
- [ ] Create security dashboards and alerts

## Skills Practiced

- Virtual machine deployment
- Windows endpoint administration
- Sysmon configuration
- Event log analysis
- PowerShell monitoring
- Security investigation workflows
