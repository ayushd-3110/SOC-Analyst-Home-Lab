# MITRE ATT&CK Mapping


## Overview

This lab demonstrates how attackers abuse Windows PowerShell to execute commands, evade security controls, and download additional payloads. Detection is performed using Windows PowerShell Operational Logs (Event ID 4104) and Windows Security Logs (Event ID 4688).

---

| MITRE Tactic | Technique ID | Technique | Why It Applies |
|--------------|--------------|-----------|----------------|
| Execution | T1059.001 | PowerShell | Attacker executes commands using PowerShell. |
| Defense Evasion | T1027 | Obfuscated Files or Information | Encoded (`-enc`) or obfuscated PowerShell commands hide malicious activity. |
| Defense Evasion | T1562.001 | Impair Defenses: Disable or Modify Tools | `-ExecutionPolicy Bypass` attempts to bypass PowerShell execution restrictions. |
| Command and Control | T1105 | Ingress Tool Transfer | `Invoke-WebRequest` or `DownloadString` downloads files or payloads from remote servers. |
| Discovery | T1082 | System Information Discovery | Commands such as `hostname`, `systeminfo`, and `ipconfig` gather system information. |
| Discovery | T1033 | System Owner/User Discovery | `whoami` identifies the current logged-on user. |
| Discovery | T1057 | Process Discovery | `Get-Process` enumerates running processes. |

---

## Primary Detection

**Log Source**
- Microsoft-Windows-PowerShell/Operational

**Primary Event ID**
- 4104 (PowerShell Script Block Logging)

**Secondary Log Source**
- Windows Security Log

**Secondary Event ID**
- 4688 (Process Creation)

---

## Detection Summary

During this lab, PowerShell Operational Logs captured executed script blocks, while Security Event ID 4688 recorded process creation. These events enabled detection of suspicious PowerShell activity, including execution policy bypass, encoded commands, download cradles, and system discovery commands.