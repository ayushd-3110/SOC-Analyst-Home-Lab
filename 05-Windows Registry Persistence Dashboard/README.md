# Lab 5 – Windows Registry Persistence Detection

## Overview

This lab demonstrates how attackers establish persistence by modifying Windows Registry Run Keys. Instead of relying on Sysmon, detection is performed using native Windows Security Event Logs collected in Splunk.

The attack uses `reg.exe` to create a malicious startup registry entry that automatically executes after user logon.

---

## Objectives

- Simulate Windows Registry Persistence
- Monitor registry modifications using Windows Security Logs
- Detect registry access and value changes
- Investigate persistence using Splunk
- Map the activity to the MITRE ATT&CK Framework

---

## Technologies Used

- Windows 10 Pro
- Kali Linux
- Splunk Enterprise
- Splunk Universal Forwarder
- Windows Security Logs
- VMware Workstation

---

## Event IDs Used

| Event ID | Description |
|----------|-------------|
| 4688 | Process Creation |
| 4663 | Registry Object Access |
| 4657 | Registry Value Modified |

---

## Attack

```
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run ^
/v WindowsUpdate ^
/t REG_SZ ^
/d "C:\Windows\System32\cmd.exe" ^
/f
```

---

## Detection

The attack is detected by correlating:

4688 → reg.exe executed

↓

4663 → Registry Key Accessed

↓

4657 → Registry Value Modified

---

## Outcome

The malicious registry modification was successfully detected using Windows Security Event Logs without Sysmon.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
