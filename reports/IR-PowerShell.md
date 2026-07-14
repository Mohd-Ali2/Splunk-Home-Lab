# Incident Response Report – PowerShell Reverse Shell

## Incident Summary

A malicious PowerShell payload established a reverse shell from the monitored Windows endpoint to the Kali Linux attacker machine.

---

# Identification

Detection Source

- Splunk Enterprise

Evidence

- PowerShell execution
- Sysmon Process Creation
- Network connection
- Suspicious command line

Status

Confirmed malicious activity.

---

# Containment

Actions Performed

- Disconnected endpoint from the network.
- Prevented additional outbound communication.

---

# Eradication

Actions Performed

- Terminated the malicious PowerShell process.
- Deleted the payload from the endpoint.
- Verified no malicious processes remained.

---

# Recovery

- Restored normal network connectivity.
- Confirmed endpoint functionality.
- Verified no further malicious activity was observed.

---

# Lessons Learned

- Sysmon significantly improves endpoint visibility.
- Splunk enables rapid investigation using centralized logs.
- PowerShell logging is valuable for detecting malicious execution.
- Centralized log collection reduces investigation time.

---

# Incident Status

Closed