# Enterprise SOC Monitoring & Threat Detection Platform

## Project Overview

This project demonstrates a hands-on Security Operations Center (SOC) home lab built to collect endpoint telemetry, monitor activity, investigate security alerts, perform controlled network reconnaissance, and review detections using the MITRE ATT&CK framework.

The lab uses Wazuh as the SIEM platform, Sysmon for Windows endpoint telemetry, and Kali Linux for controlled reconnaissance against the Windows lab endpoint.

## Lab Architecture

| Component | Platform / Version | Purpose |
|---|---|---|
| SIEM platform | Wazuh 4.14.10 | Centralized security monitoring, event analysis, and alert investigation |
| SOC server | Ubuntu Server 24.04 LTS | Hosts the Wazuh all-in-one deployment |
| Monitored endpoint | Windows 11 | Generates endpoint activity and security telemetry |
| Endpoint telemetry | Microsoft Sysmon 15.22 | Records process creation and network connection events |
| Test machine | Kali Linux | Performs controlled network reconnaissance |
| Network tool | Nmap | Network discovery and port scanning |
| Virtualization | VMware Workstation | Runs the lab virtual machines |

### Lab Network

| System | Lab IP address |
|---|---|
| Wazuh Ubuntu server | `192.168.64.139` |
| Windows 11 endpoint | `192.168.64.1` |
| Kali Linux | `192.168.64.128` |

These addresses describe the VMware NAT lab network used during testing.

## Tools and Technologies

- Wazuh SIEM
- Ubuntu Server 24.04 LTS
- Windows 11
- Microsoft Sysmon 15.22
- Kali Linux
- Nmap
- VMware Workstation
- MITRE ATT&CK Framework

## Implementation and Testing

### 1. SOC Server Deployment

- Prepared an Ubuntu Server 24.04 virtual machine.
- Installed the Wazuh all-in-one deployment.
- Verified that the Wazuh Manager, Indexer, and Dashboard services were running.

### 2. Windows Endpoint Integration

- Installed the Wazuh Agent on the Windows 11 host.
- Configured the agent to communicate with the Wazuh Manager.
- Verified that the endpoint appeared as active in the Wazuh Dashboard.

### 3. Sysmon Configuration

- Installed Microsoft Sysmon 15.22.
- Configured SHA256 hashing.
- Enabled process creation and network connection telemetry.
- Configured the Wazuh Agent to collect the `Microsoft-Windows-Sysmon/Operational` event channel.

### 4. Controlled Network Reconnaissance

Performed a TCP connect scan from Kali Linux against the Windows lab endpoint.

**Command used:**

```bash
nmap -sT -Pn -p 135,445