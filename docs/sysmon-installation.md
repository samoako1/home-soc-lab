# Sysmon Installation and Configuration

## Overview

Sysmon (System Monitor) is a Windows Sysinternals tool that provides detailed endpoint telemetry for security monitoring and threat detection. Unlike standard Windows logs, Sysmon provides additional visibility into system activity including process creation, command-line execution, parent-child process relationships, network connections, and file activity.

In this SOC lab, Sysmon is installed on a Windows 11 endpoint to collect security telemetry that can later be forwarded to a SIEM platform such as Wazuh.

---

## Environment

| Component | Details |
|---|---|
| Host Machine | Windows 11 Home|
| Virtualization Platform | VMware Workstation Pro |
| Endpoint Operating System | Windows 11 Pro |
| Monitoring Tool | Sysmon |
| Sysmon Configuration | SwiftOnSecurity Sysmon Configuration |

---

# Installation Steps

## 1. Create Sysmon Directory

A dedicated directory was created on the Windows endpoint to store Sysmon files:
C:\Sysmon

The Sysmon executable and configuration file are stored in this directory.

---

## 2. Download Sysmon

Sysmon was downloaded from Microsoft Sysinternals:

https://learn.microsoft.com/sysinternals/downloads/sysmon

The Sysmon executable was extracted into:
C:\Sysmon

---

## 3. Install SwiftOnSecurity Sysmon Configuration

A community-maintained Sysmon configuration created by SwiftOnSecurity was used to improve telemetry collection and enable additional security monitoring capabilities.

The configuration provides enhanced logging for:

- Process creation
- Process termination
- Network connections
- File creation events
- Registry activity
- Driver loading
- Image loading
- Suspicious execution patterns

The configuration file was downloaded and placed in:
C:\Sysmon\sysmonconfig.xml

---

## 4. Install Sysmon with Configuration

PowerShell was opened as Administrator and the Sysmon directory was accessed:
cd C:\Sysmon

Sysmon was installed using:
.\Sysmon64.exe -accepteula -i sysmonconfig.xml

Sysmon service verified using:
Get-Service *Sysmon*


