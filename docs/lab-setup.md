# Splunk SOC Home Lab Setup

## Overview

This document describes the implementation of a small Security Operations Center (SOC) home lab using Splunk Enterprise, Sysmon, and Splunk Universal Forwarder. The lab is designed to simulate attack scenarios, collect endpoint telemetry, investigate security events, and perform incident response.

---

# Lab Components

## Windows A (Host)

**Role**

- Splunk Enterprise Server
- Oracle VirtualBox Host

**Software Installed**

- Windows 11
- Splunk Enterprise
- Oracle VirtualBox

**Responsibilities**

- Receive logs from endpoints
- Search and analyze events
- Create alerts and dashboards
- Perform investigations

---

## Kali Linux VM

**Role**

Attacker Machine

**Software**

- Kali Linux
- Nmap
- Metasploit Framework
- OpenSSH Client

**Responsibilities**

- Simulate attacks
- Network reconnaissance
- Payload generation
- Reverse shell listener

---

## Windows B (Endpoint)

**Role**

Monitored Endpoint

**Software**

- Windows 11
- Sysmon
- Splunk Universal Forwarder

**Responsibilities**

- Generate endpoint telemetry
- Collect Windows Event Logs
- Forward logs to Splunk Enterprise

---

# Network Configuration

**Local Network**

```text
Windows A (Splunk)
        │
        │
192.168.31.x
        │
        │
Windows B (Endpoint)
```

**Communication**

| Component | Port |
|-----------|------|
| Splunk Receiving | 9997 |
| Splunk Web | 8000 |
| SSH | 22 |

---

# Splunk Enterprise Configuration

**Receiving Port**

```text
9997
```

**Enabled Event Sources**

- Application
- Security
- System
- Microsoft-Windows-Sysmon/Operational
- Microsoft-Windows-PowerShell/Operational

---

# Splunk Universal Forwarder Configuration

**Forwarder sends logs to**

```text
Windows A
Port 9997
```

**Configuration Files**

- outputs.conf
- inputs.conf

---

# Sysmon Configuration

**Installed Version**

```text
Sysmon v15.x
```

**Configuration**

```text
sysmonconfig-export.xml
```

**Primary Event IDs Used**

| Event ID | Description |
|-----------|-------------|
| 1 | Process Creation |
| 3 | Network Connection |
| 5 | Process Terminated |
| 11 | File Create |

---

# Attack Scenario

## Completed

✔ PowerShell Reverse Shell

**Detection Sources**

- Sysmon
- Windows Security Logs
- PowerShell Operational Logs

## Future Scenario

- SSH Brute Force

---

# Log Flow

```text
Attack
        │
        ▼
Windows Endpoint
        │
        ▼
Sysmon
        │
        ▼
Windows Event Logs
        │
        ▼
Splunk Universal Forwarder
        │
        ▼
TCP 9997
        │
        ▼
Splunk Enterprise
        │
        ▼
Search
        │
        ▼
Alert
        │
        ▼
Investigation
        │
        ▼
Incident Response
```

---

# Project Structure

```text
Splunk-Home-Lab/
│
├── configs/
├── docs/
├── attacks/
├── reports/
├── screenshots/
├── spl/
└── diagrams/
```

---

# Skills Demonstrated

- Splunk Enterprise Administration
- SIEM Log Collection
- Sysmon Deployment
- Windows Event Log Monitoring
- Endpoint Telemetry
- SPL Query Development
- Threat Detection
- Incident Investigation
- Incident Response
- SOC Operations

---

# Future Improvements

- SSH brute-force detection
- Custom dashboards
- Scheduled alerts
- Additional attack simulations
- Threat hunting use cases
- Detection engineering
