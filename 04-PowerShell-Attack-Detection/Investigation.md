# Investigation

## Alert

Suspicious PowerShell execution detected.

## Evidence Collected

- PowerShell Operational Log (Event ID 4104)
- Windows Security Log (Event ID 4688)
- ScriptBlockText
- Process Creation Events
- Splunk Dashboard
- Timeline Analysis

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

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
