# Scenario - Threat Hunting

## Background

The SOC receives intelligence suggesting that an attacker may have gained access to a Windows workstation.

No confirmed malware alert has been generated.

Instead of waiting for a security alert, the SOC analyst performs proactive threat hunting against available Windows endpoint telemetry.

The analyst suspects that an attacker could use legitimate Windows utilities for reconnaissance and command execution.

---

## Suspected Activity

The hunt focuses on:

- User enumeration
- System information discovery
- Network information discovery
- Process enumeration
- PowerShell execution
- Windows Command Shell execution
- Authentication activity
- Parent-child process relationships

---

## Controlled Simulation

The activities were manually generated on the Windows laboratory machine.

No real malware was executed.

The purpose was to create realistic endpoint telemetry that could be investigated using Splunk.

---

## SOC Perspective

The analyst does not assume that every discovery command is malicious.

For example:

```text
systeminfo
ipconfig
tasklist
powershell.exe
```
