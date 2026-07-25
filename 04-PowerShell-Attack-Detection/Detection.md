# Detection

## Detection Overview

PowerShell is frequently abused by attackers for:

* Defense evasion
* Payload execution
* Downloading malware
* Credential theft
* Lateral movement

The SOC monitors for suspicious PowerShell command-line arguments.

## Detection Indicators

* `powershell.exe`
* `-ExecutionPolicy Bypass`
* `-WindowStyle Hidden`
* `-NoProfile`
* `IEX`
* `DownloadString`
* Encoded commands

## Key Events

| Source             | Event ID | Description                       |
| ------------------ | -------- | --------------------------------- |
| Sysmon             | 1        | Process Create                    |
| Windows PowerShell | 4104     | Script Block Logging (if enabled) |

## Detection Logic

Alert when PowerShell executes with suspicious arguments associated with attacker tradecraft.
