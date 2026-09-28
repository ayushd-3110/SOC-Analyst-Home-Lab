# Indicators of Compromise (IOC)

## Lab 8 – Credential Access / Mimikatz Detection

### Overview

During this lab, a controlled credential-access simulation was performed on the Windows victim machine.

The objective was to generate security telemetry associated with suspicious credential-access activity and investigate it using Splunk.

No real credentials were dumped or exfiltrated during the simulation.

---

## 1. Host Indicators

| Indicator | Value |
|---|---|
| Hostname | DESKTOP-NH5RCBO |
| User Account | ayush |
| Domain | DESKTOP-NH5RCBO / WORKGROUP |
| Splunk Index | main |
| Security Log Source | WinEventLog:Security |

---

## 2. Event-Based Indicators

| Event ID | Description | Relevance |
|---|---|---|
| 4624 | Successful Logon | Authentication context |
| 4648 | Logon using Explicit Credentials | Credential-related activity |
| 4672 | Special Privileges Assigned | Privileged account activity |
| 4688 | Process Creation | Suspicious process execution |

---

## 3. Suspicious Command-Line Indicator

Observed command line:

`cmd /c echo mimikatz credential access simulation`

This was intentionally generated as part of the lab.

It should be treated as a **simulation indicator**, not evidence that Mimikatz actually executed.

---

## 4. Suspicious Keywords

The investigation searched for the following credential-access-related keywords:

- mimikatz
- sekurlsa
- logonpasswords
- lsass
- credential
- privilege::debug

These keywords can be used as detection indicators, but keyword matches alone should not be treated as proof of credential theft.

---

## 5. Privilege Indicators

Event ID 4672 showed several privileges, including:

- SeDebugPrivilege
- SeTakeOwnershipPrivilege
- SeBackupPrivilege
- SeRestorePrivilege
- SeImpersonatePrivilege
- SeSecurityPrivilege

`SeDebugPrivilege` was considered particularly relevant to the investigation because of its relationship to privileged process access.

---

## 6. IOC Assessment

### Confirmed

- Windows Security Event ID 4688
- Suspicious Mimikatz-related command string
- Event ID 4672
- Special privileges
- Event ID 4624
- Successful authentication
- Event ID 4648
- Explicit credential usage

### Not Confirmed

- Actual credential dumping
- Credential exfiltration
- Password theft
- LSASS memory dumping
- Lateral movement
- Data exfiltration

---

## Conclusion

The collected indicators provide sufficient evidence to investigate the activity as a potential credential-access event.

However, because the Mimikatz activity was simulated using an `echo` command, the evidence does not prove that credentials were actually compromised.