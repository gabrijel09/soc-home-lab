# SOC Home Lab

## Overview

This project is a small SOC home lab that I built to practice basic security monitoring and incident investigation.

The lab uses Splunk Enterprise, a Windows 11 endpoint, Sysmon, Windows event logs, PowerShell logging, and Kali Linux.

I use the lab to collect and analyze logs, create simple detection rules and alerts, and investigate suspicious activity such as PowerShell execution, persistence, failed logons, and port scanning.

## Lab Architecture

The lab is built in VMware and uses an isolated virtual network.

- **Windows host** – runs Splunk Enterprise
- **SOC-WIN11** – Windows 11 virtual machine used as the monitored endpoint
- **Kali Linux** – used to generate test network and security activity
- **Splunk Universal Forwarder** – sends logs from SOC-WIN11 to Splunk
- **Sysmon and Windows Event Logs** – provide endpoint and security telemetry

The main lab network is `192.168.64.0/24`.

Current systems:
- Splunk host: `192.168.64.1`
- SOC-WIN11: `192.168.64.10`
- Kali Linux: `192.168.64.20`

## Log Sources

SOC-WIN11 sends several types of logs to Splunk.

The main log sources used in the lab are:

- **Windows Security Logs** – used for logons, failed logons, account activity, and other security events
- **Sysmon** – provides detailed information about processes, network connections, file creation, registry changes, and DNS queries
- **PowerShell Operational Logs** – used to monitor PowerShell activity and Script Block Logging
- **Task Scheduler Logs** – used to monitor scheduled task activity
- **Windows Filtering Platform Logs** – used to detect blocked network traffic, such as port scanning attempts
