# Lab 12 — Account Compromise Investigation

## Overview

This lab simulates a suspected Windows account compromise using controlled authentication activity.

The investigation focuses on multiple failed logins, a successful authentication, possible privileged activity, and post-authentication process execution.

Splunk is used to collect, detect, correlate, and investigate Windows Security events.

---

## Scenario

The SOC receives an alert indicating suspicious authentication activity against a Windows workstation.

The analyst observes:

- Multiple failed authentication attempts
- A successful authentication
- Possible privileged activity
- Process creation after authentication

The objective is to determine whether the activity represents suspicious account behavior.

---

## Objectives

- Detect failed authentication attempts
- Investigate Event ID 4625
- Investigate Event ID 4624
- Investigate Event ID 4672
- Investigate Event ID 4688
- Identify authentication source IP
- Correlate authentication and endpoint activity
- Extract IOCs
- Map activity to MITRE ATT&CK
- Build a Splunk dashboard
- Create a SOC incident report

---

## Lab Environment

| Component | Description |
|---|---|
| SIEM | Splunk Enterprise |
| Attacker/Test System | Kali Linux |
| Victim | Windows VM |
| Log Collector | Splunk Universal Forwarder |
| Index | main |
| Authentication Logs | Windows Security |
| Process Logs | Windows Security / Sysmon where available |

---

## Attack Simulation

The following controlled activities were performed:

1. Multiple incorrect SMB authentication attempts
2. Successful SMB authentication
3. Harmless command execution
4. Investigation of privileged activity
5. Splunk correlation

---

## Windows Events

| Event ID | Description |
|---|---|
| 4625 | Failed Logon |
| 4624 | Successful Logon |
| 4672 | Special Privileges Assigned |
| 4688 | Process Creation |

---

## Detection

The lab detects:

- Multiple failed logins
- Successful authentication
- Source IP activity
- Privileged activity
- Post-authentication process execution

---

## Investigation

The investigation correlates:

```text
Failed Authentication
        ↓
Successful Authentication
        ↓
Privileged Activity
        ↓
Process Creation

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
