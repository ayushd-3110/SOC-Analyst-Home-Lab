# MITRE ATT&CK Mapping

| Technique | Name | Project Activity | Evidence Status |
|---|---|---|---|
| T1110 | Brute Force | Repeated failed authentication | Simulated |
| T1021.002 | SMB/Windows Admin Shares | SMB authentication between lab systems | Simulated / Investigated |
| T1078 | Valid Accounts | Successful use of lab account | Simulated / Investigated |
| T1059 | Command and Scripting Interpreter | Command execution | Observed in lab |
| T1059.001 | PowerShell | PowerShell commands | Observed in lab |
| T1059.003 | Windows Command Shell | `cmd.exe` activity | Observed in lab |
| T1082 | System Information Discovery | `systeminfo` / system information commands | Simulated |
| T1087 | Account Discovery | `net user` | Simulated |
| T1057 | Process Discovery | `tasklist` / `Get-Process` | Simulated |
| T1016 | System Network Configuration Discovery | `ipconfig`, `route print` | Simulated |
| T1053.005 | Scheduled Task/Job: Scheduled Task | Lab scheduled task | Simulated |
| T1218 | System Binary Proxy Execution | LOLBin activity from earlier lab work | Investigated in portfolio |
| T1486 | Data Encrypted for Impact | Ransomware-style file activity | Simulated; no encryption |

## Important

MITRE ATT&CK mapping describes the behavior being practiced. It does not mean that every mapped technique represents a confirmed malicious compromise.
