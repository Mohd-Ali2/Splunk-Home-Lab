# PowerShell Reverse Shell Detection

## Objective

Simulate a PowerShell reverse shell from the monitored Windows endpoint and detect the activity using Splunk Enterprise, Sysmon, and Windows Event Logs.

---

# Attack Environment

Attacker

- Kali Linux VM

Target

- Windows 11 Endpoint

Monitoring

- Splunk Enterprise
- Splunk Universal Forwarder
- Sysmon

---

# Attack Steps

1. Generate a PowerShell reverse shell payload.
2. Start a listener on the Kali Linux VM.
3. Execute the payload on the Windows endpoint.
4. Establish a reverse shell connection.
5. Generate Windows and Sysmon telemetry.
6. Forward logs to Splunk Enterprise.
7. Investigate the activity using SPL queries.

---

# Detection

Primary Log Sources

- Sysmon Operational Log
- Windows PowerShell Operational Log
- Windows Security Log

Relevant Sysmon Events

- Event ID 1 – Process Creation
- Event ID 3 – Network Connection

Indicators

- powershell.exe execution
- Encoded commands
- Outbound network connection
- Suspicious parent-child process relationship

---

# MITRE ATT&CK

| Technique | Description |
|----------|-------------|
| T1059.001 | PowerShell |
| T1105 | Ingress Tool Transfer (if applicable) |

---

# Result

The attack was successfully detected in Splunk and investigated using endpoint telemetry collected from Sysmon and Windows Event Logs.