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

## Detections and Alerts

I created several basic detection rules in Splunk to identify suspicious activity on the Windows endpoint.

Current detections include:

- Suspicious PowerShell Execution
- Suspicious Run Key Persistence
- Account Added to Local Administrators
- Suspicious Scheduled Task
- New Service Creation
- Multiple Failed Logons
- Possible Port Scan

The detections are configured as scheduled alerts in Splunk and are used as the starting point for investigation.


## Current Lab Capabilities

The current version of the lab can:

- Collect Windows logs in Splunk
- Monitor process creation with Sysmon
- Monitor PowerShell activity
- Detect failed logons and account changes
- Detect suspicious scheduled tasks and service creation
- Detect suspicious registry persistence
- Detect basic port scanning activity
- Generate scheduled alerts for investigation

## Future Improvements

I plan to continue improving this lab as I learn more.

Possible future additions include:

- Active Directory and Windows Server
- EDR or endpoint monitoring tools
- IDS/IPS for network monitoring
- Additional detection rules and alerts
- More realistic attack and investigation scenarios
