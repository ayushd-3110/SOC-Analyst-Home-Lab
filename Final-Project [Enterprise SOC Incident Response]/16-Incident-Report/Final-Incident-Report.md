# Final Incident Report

## INC-2026-001 – Suspected Windows Endpoint Compromise

| Field | Value |
|---|---|
| Incident ID | INC-2026-001 |
| Severity | Medium |
| Priority | P2 |
| Status | Closed – Controlled Lab Simulation |
| Analyst | Ayush Dhumal |
| Host | DESKTOP-NH5RCBO |
| IP | 192.168.234.130 |
| User | ayush |
| Simulation Host | 192.168.234.129 |
| SIEM | Splunk Enterprise |
| Index | main |

---

## 1. Executive Summary

A controlled enterprise SOC incident simulation was performed against a Windows workstation.

The project was designed to investigate repeated failed authentication followed by possible successful authentication and endpoint activity. In the supplied final-project screenshots, the environment and telemetry are verified, while the visible initial-access screenshot shows system/computer-account logon type 5 records rather than a confirmed `ayush` authentication sequence. Additional controlled activity represented discovery, persistence, credential access, SMB/lateral movement, and impact behavior.

The investigation was performed using Splunk and Windows endpoint telemetry.

---

## 2. Initial Detection

The planned first investigation lead was an authentication anomaly. The supplied final-project authentication screenshot does not, by itself, prove that anomaly because the visible rows are SYSTEM/computer-account logon type 5 records.

**Failed authentication → successful authentication** was the intended investigation hypothesis. The screenshot evidence currently available for the final project does not visibly confirm the complete sequence for `ayush`.

The analyst should review:

- account
- source address
- logon type
- authentication package
- timestamps

This pattern justified additional investigation but did not independently prove account compromise.

---

## 3. Execution

Event ID 4688 was used to investigate process creation. The supplied telemetry screenshot shows 3,429 Event ID 4688 results in the displayed 26–27 Sep 2026 window, with visible `SplunkForwarder` process activity.

PowerShell activity was identified using process name and command-line searches.

The analyst checked the parent process, user, command line, and timestamp.

---

## 4. Discovery

Controlled discovery commands included:

- `whoami`
- `net user`
- `systeminfo`
- `ipconfig`
- `arp -a`
- `route print`
- `tasklist`
- PowerShell discovery commands

These events were correlated with the earlier authentication and execution activity.

---

## 5. Persistence

A harmless scheduled task named:

`SOC-Enterprise-Persistence-Test`

was created for the exercise.

The task was investigated and then removed.

---

## 6. Credential Access

Credential-access behavior was simulated using harmless command execution.

No real credentials were extracted and Mimikatz was not executed.

Event 4672 was reviewed separately, with account context checked before interpretation.

---

## 7. Lateral Movement

SMB activity between the controlled Kali and Windows systems was investigated.

The analyst reviewed:

- source address
- target host
- account
- authentication result
- process activity

The activity was part of the lab exercise.

---

## 8. Impact Simulation

Harmless test files were created and renamed with `.locked` extensions.

No encryption algorithm was used and no destructive ransomware was executed.

---

## 9. Response

### Triage
The analyst built a timeline from authentication and endpoint telemetry.

### Containment
The simulation was stopped and the persistence artifact was removed.

### Eradication
The scheduled task and temporary simulation artifacts were removed.

### Recovery
The Windows endpoint and logging pipeline were checked after cleanup.

---

## 10. MITRE ATT&CK

Relevant techniques practiced or investigated include:

- T1110 – Brute Force
- T1021.002 – SMB/Windows Admin Shares
- T1078 – Valid Accounts
- T1059 – Command and Scripting Interpreter
- T1059.001 – PowerShell
- T1059.003 – Windows Command Shell
- T1082 – System Information Discovery
- T1087 – Account Discovery
- T1057 – Process Discovery
- T1016 – System Network Configuration Discovery
- T1053.005 – Scheduled Task/Job: Scheduled Task
- T1486 – Data Encrypted for Impact (simulation only)

---

## 11. Evidence Limitations

The following points are important:

- Some behaviors were simulated rather than malicious.
- A successful authentication is not automatically a compromise.
- A process containing a suspicious keyword is not automatically malicious.
- A 200 HTTP response does not prove successful exploitation.
- A 4672 event must be attributed using its actual account and context.
- No real malware or credential theft was performed.
- No fabricated hashes are included.

---

## 12. Final Conclusion

The project successfully demonstrated an end-to-end SOC investigation workflow in a controlled environment.

The evidence supports a sequence of intentionally generated security behaviors that can be investigated using Splunk and Windows telemetry.

Because the activity was deliberately generated for training, the project does not establish a real-world compromise.

**Incident status: Closed – Controlled Lab Simulation**

## Supplied Screenshot Evidence

The current repository contains four final-project screenshots:

1. `01-Final-Project-Environment.png` – hostname `DESKTOP-NH5RCBO`, user `desktop-nh5rcbo\ayush`, IPv4 `192.168.234.130`, gateway `192.168.234.2`.
2. `02-logging and audit verification.png` – Logon auditing is **Success and Failure**; Process Creation auditing is **Success**; `Sysmon64` is **RUNNING**. The displayed `sc query SplunkForwarder` command returns service-not-found, so the screenshot does not prove that the Windows service named `SplunkForwarder` is installed.
3. `03-splunk telementry verification.png` – Splunk search `index=main EventCode=4688` returned **3,429 events** for the displayed 26–27 Sep 2026 window. The visible rows show `SplunkForwarder` process activity on `DESKTOP-NH5RCBO`.
4. `04-Initial Access Failed authentication .png` – the displayed combined 4624/4625 search returned **124 events**, but the visible rows are **SYSTEM / computer-account logon type 5** records with no source network address. This screenshot does not prove the intended `ayush` failed-authentication scenario.

## Evidence Boundary
Only these four screenshots are currently present in the final-project screenshot folder. Later project phases should not be described as screenshot-verified unless their screenshots are actually added. The screenshot folder has not been changed.
