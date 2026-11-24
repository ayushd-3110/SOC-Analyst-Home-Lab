# Indicators of Compromise

| IOC                 | Value                   |
| ------------------- | ----------------------- |
| Host                | DESKTOP-PB7D0G9         |
| User                | ayush                   |
| Process             | powershell.exe          |
| Technique           | PowerShell Execution    |
| Suspicious Argument | -ExecutionPolicy Bypass |
| Suspicious Argument | -WindowStyle Hidden     |
| Suspicious Function | DownloadString          |
| Event ID            | 1                       |

These are lab investigation indicators, not confirmed malicious IOCs. The archived Event Code 1 capture is a SecurityCenter Application event, not Sysmon process creation.
