# LAB 8 — Credential Access Detection & Privileged Activity Investigation

## Overview

This lab focuses on detecting and investigating suspicious credential-access
and privileged activity on a Windows endpoint using Windows Security Event Logs
and Splunk.

Instead of executing real credential-dumping malware, a controlled Mimikatz
credential-access simulation was performed using harmless command-line
activity. The objective was to generate realistic security telemetry and
practice how a SOC analyst would identify, correlate, and investigate the
activity.

The investigation used Windows Security Event IDs:

- 4624 — Successful Logon
- 4648 — Logon Attempted Using Explicit Credentials
- 4672 — Special Privileges Assigned to a New Logon
- 4688 — A New Process Has Been Created

The collected events were forwarded to Splunk using the Windows Splunk
Universal Forwarder.

---

## Real-World Scenario

An employee workstation is suspected of being targeted by an attacker
attempting to access credentials.

The attacker may use credential-access tools such as Mimikatz after gaining
access to the endpoint. Before investigating actual credential theft, a SOC
analyst should look for supporting telemetry such as:

- Suspicious process creation
- Credential-related command lines
- Explicit credential usage
- Privileged logons
- Elevated tokens
- Suspicious parent-child process relationships

In this lab, the credential-access behavior was simulated safely rather than
performing an actual credential dump.

---

## Lab Environment

| Component | Purpose |
|---|---|
| Windows VM | Victim endpoint |
| Kali Linux | Security testing / attacker machine |
| Splunk Enterprise | SIEM and investigation platform |
| Splunk Universal Forwarder | Log forwarding |
| Windows Security Logs | Primary telemetry source |
| Sysmon | Additional endpoint telemetry |

---

## Objectives

1. Generate controlled credential-access simulation activity.
2. Generate Windows Security Event ID 4624.
3. Generate Windows Security Event ID 4648.
4. Generate Windows Security Event ID 4672.
5. Generate Windows Security Event ID 4688.
6. Identify suspicious process creation.
7. Investigate privileged logon activity.
8. Correlate authentication, privilege, and process events.
9. Search for Mimikatz-related indicators.
10. Build Splunk detection queries.
11. Create SOC dashboard panels.
12. Extract potential IOCs.
13. Map the activity to MITRE ATT&CK.
14. Produce an incident investigation report.

---

## Events Observed

### Event ID 4624

Successful logon.

This event provides authentication information such as:

- Account name
- Logon type
- Logon ID
- Authentication package
- Elevated token status

---

### Event ID 4648

A logon was attempted using explicit credentials.

This is useful when investigating activity where credentials are explicitly
provided to a Windows process.

---

### Event ID 4672

Special privileges were assigned to a new logon.

The investigation observed privileges including:

- SeDebugPrivilege
- SeBackupPrivilege
- SeRestorePrivilege
- SeTakeOwnershipPrivilege
- SeLoadDriverPrivilege
- SeImpersonatePrivilege
- SeSecurityPrivilege

These privileges can be important during investigations involving
privilege abuse or credential-access behavior.

---

### Event ID 4688

A new process was created.

This event was particularly important because the process command line
contained the controlled credential-access simulation:

    cmd /c echo mimikatz credential access simulation

---

## Detection Logic

The investigation correlated:

4624 + 4648 + 4672 + 4688

The strongest indicator in this lab was the combination of:

- Successful authentication
- Explicit credential usage
- Privileged logon
- Suspicious process creation
- Credential-related command-line keywords

---

## Important Lab Limitation

This lab did not execute the actual Mimikatz credential-dumping tool.

The activity was intentionally simulated using harmless commands so that
Windows security telemetry could be generated without extracting real
credentials.

Therefore, the lab demonstrates detection and investigation methodology,
not successful credential dumping.

---

## MITRE ATT&CK

Primary technique:

- T1003 — OS Credential Dumping

Supporting technique:

- T1059.003 — Windows Command Shell

The Mimikatz reference is treated as a simulated indicator rather than proof
that actual credential dumping occurred.

---

## Deliverables

- Attack-Simulation.md
- Detection.md
- Investigation.md
- IOC.md
- MITRE-Mapping.md
- Incident-Report.md
- Lessons-Learned.md
- References.md
- Splunk-Queries.md
- README.md

---

## Skills Demonstrated

- Windows Security Event Analysis
- Splunk SIEM Investigation
- Process Creation Analysis
- Authentication Analysis
- Privilege Analysis
- Credential Access Detection
- Event Correlation
- IOC Extraction
- MITRE ATT&CK Mapping
- SOC Incident Investigation
- Security Dashboard Development

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
