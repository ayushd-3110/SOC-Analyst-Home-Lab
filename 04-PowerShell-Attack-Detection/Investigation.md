# Investigation

## Alert

Suspicious PowerShell execution detected.

## Evidence

* PowerShell process creation observed.
* `-ExecutionPolicy Bypass` detected.
* Command-line arguments extracted from Sysmon logs.

## Key Findings

| Item            | Value                  |
| --------------- | ---------------------- |
| Host            | DESKTOP-PB7DOG9        |
| User            | ayush                  |
| Process         | powershell.exe         |
| Event ID        | 1                      |
| Technique       | PowerShell             |
| Suspicious Flag | ExecutionPolicy Bypass |

## Analysis

The command line contained parameters commonly used by attackers to bypass PowerShell execution restrictions.

The activity was generated intentionally within the lab for detection validation.

## Recommendation

* Monitor PowerShell execution continuously.
* Alert on `ExecutionPolicy Bypass`.
* Alert on hidden PowerShell windows.
* Investigate PowerShell download activity.
* Enable PowerShell Script Block Logging in production environments.
