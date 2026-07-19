# Home SOC Lab Setup

## Overview

This document explains the setup and architecture of the Home SOC Lab environment.

The lab consists of a Windows endpoint generating security telemetry and an Ubuntu-based SOC server collecting, analyzing, and visualizing security events through Wazuh.

---

# Lab Architecture

```
                 VirtualBox Host Machine
                    macOS Intel

                         |
                         |
                 VirtualBox Network

        +--------------------------------+
        |                                |
        |                                |
 Windows 11 Endpoint              Ubuntu SOC Server
 192.168.222.131                  192.168.222.130

        |                                |
        |                                |
  Wazuh Agent                     Wazuh Manager
  Sysmon                          Filebeat
  Windows Logs                    Elasticsearch
                                  Wazuh Dashboard

```

---

# Host Machine

## Hardware

- Device: Intel MacBook
- Virtualization Platform: VirtualBox

The host machine runs the virtualized Windows endpoint and Ubuntu SOC server.

---

# Windows Endpoint

## Purpose

The Windows virtual machine acts as the monitored endpoint within the SOC environment.

It is used to:

- Generate security events
- Execute test scenarios
- Provide endpoint telemetry
- Simulate attacker activity

## Configuration

- Operating System: Windows 11 Home
- Monitoring Tools:
  - Sysmon
  - Wazuh Agent

## Data Sources Collected

### Sysmon

Provides detailed endpoint telemetry including:

- Process creation
- Command-line execution
- Parent-child process relationships
- File creation activity

### Windows Security Logs

Provides authentication and system activity including:

- Failed login attempts
- User account creation
- Event log clearing

---

# SOC Server

## Purpose

The Ubuntu SOC server acts as the centralized monitoring platform.

Responsibilities:

- Receive endpoint telemetry
- Analyze security events
- Generate alerts
- Provide investigation dashboards

## Configuration

- Operating System: Ubuntu Server 24.04 LTS
- SIEM: Wazuh

Installed Components:

- Wazuh Manager
- Filebeat
- Elasticsearch
- Wazuh Dashboard

---

# Wazuh Agent Configuration

The Windows endpoint communicates with the SOC server through the Wazuh Agent.

Agent Information:

| Field | Value |
|---|---|
| Agent Name | homelab |
| Agent ID | 001 |
| Operating System | Windows 11 |
| IP Address | 192.168.222.131 |

Verification command:

```bash
sudo /var/ossec/bin/agent_control -l
```

Expected result:

```
ID: 001
Name: homelab
Status: Active
```

---

# Installation Workflow

## 1. Virtualization Setup

Completed:

- Installed VirtualBox
- Created Windows 11 VM
- Created Ubuntu SOC Server VM
- Configured internal network communication

---

## 2. Windows Monitoring Setup

Installed:

- Sysmon
- Wazuh Agent

Verified:

- Sysmon Event ID 1 process logging
- Windows security event collection
- Agent communication with Wazuh Manager

---

## 3. Wazuh Deployment

Configured:

- Wazuh Manager
- Filebeat integration
- Elasticsearch indexing
- Wazuh Dashboard access

Verified:

- Windows endpoint appears in Wazuh
- Security alerts generated
- Event data searchable through dashboard

---

# Network Configuration

| System | IP Address | Role |
|---|---|---|
| Windows Endpoint | 192.168.222.131 | Security telemetry source |
| Ubuntu SOC Server | 192.168.222.130 | SIEM and analysis platform |

---

# Future Improvements

Potential additions:

- Add additional Windows endpoints
- Create custom Wazuh detection rules
- Add malware simulation scenarios
- Configure automated incident response
- Integrate threat intelligence feeds
