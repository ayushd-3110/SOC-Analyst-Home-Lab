# Detection

## Detection Overview

This lab focuses on detecting suspicious PowerShell activity using native Windows logging and Splunk Enterprise.

Unlike previous labs that relied on Sysmon, this lab uses Windows built-in PowerShell Operational Logs and Windows Security Logs.

PowerShell Script Block Logging provides visibility into commands executed by PowerShell, while Security Event ID 4688 records process creation.

---

## Data Sources

### Windows PowerShell Operational Log

Log Name

Microsoft-Windows-PowerShell/Operational

Primary Event ID

4104

Purpose

Captures PowerShell Script Block Logging.

This provides complete visibility into PowerShell commands executed on the system.

---

### Windows Security Log

Log Name

Security

Event ID

4688

Purpose

Records new process creation.

Useful for determining:

- Parent Process
- Executed Process
- User Account
- Process Execution Time

---

## Detection Logic

The SOC continuously monitors PowerShell execution for suspicious activity.

Indicators include:

- ExecutionPolicy Bypass
- Encoded Commands
- Hidden Windows
- Invoke-WebRequest
- DownloadString
- Net.WebClient
- Invoke-Expression (IEX)
- Base64 Decoding
- Download Cradles

---

## Detection Workflow

Attacker Executes PowerShell

↓

Windows Generates Event ID 4104

↓

Security Log Generates Event ID 4688

↓

Universal Forwarder Sends Logs

↓

Splunk Indexes Events

↓

SOC Analyst Investigates

↓

Incident Confirmed

---

## Detection Severity

High

Reason

PowerShell is one of the most abused administrative tools by threat actors.

Monitoring Event ID 4104 significantly improves visibility into attacker behavior.

---

## MITRE ATT&CK

T1059.001 - PowerShell

T1027 - Obfuscated Files or Information

T1105 - Ingress Tool Transfer