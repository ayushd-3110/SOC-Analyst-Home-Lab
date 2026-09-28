# Final Enterprise SOC Incident Response Project

## INC-2026-001 – Suspected Windows Endpoint Compromise

This project connects the earlier SOC labs into one end-to-end incident investigation.

The purpose is not to create a perfect attack. The purpose is to show how a SOC analyst can take several suspicious signals, connect them into a timeline, investigate them, contain the simulated activity, clean up the lab, and write a clear incident report.

---

## 1. Incident Story

The investigation starts when the Windows workstation shows several failed authentication attempts.

A successful authentication follows.

After that, endpoint logs show:

- command execution
- PowerShell activity
- system and account discovery
- network discovery
- simulated persistence
- credential-access simulation
- SMB authentication activity
- harmless ransomware-style file activity

The analyst treats the activity as suspicious and investigates it step by step.

### High-Level Timeline

```text
Authentication Anomaly
        ↓
Failed Logons
        ↓
Successful Logon
        ↓
Process Creation
        ↓
PowerShell
        ↓
Discovery
        ↓
Persistence Simulation
        ↓
Credential Access Simulation
        ↓
SMB / Lateral-Movement Investigation
        ↓
Impact Simulation
        ↓
Threat Hunting
        ↓
Containment
        ↓
Eradication
        ↓
Recovery
        ↓
Final Report
```

---

## 2. Lab Environment

| Component | Value |
|---|---|
| SIEM | Splunk Enterprise |
| Splunk index | `main` |
| Windows victim | `192.168.234.130` |
| Windows hostname | `DESKTOP-NH5RCBO` |
| Windows user | `ayush` |
| Kali simulation host | `192.168.234.129` |
| Endpoint telemetry | Windows Security Logs + Sysmon |
| Log collection | Universal Forwarder / configured Windows forwarding |

> These systems belong to the controlled lab environment.

---

## 3. What This Project Demonstrates

### Detection
I can identify suspicious authentication, process, PowerShell, persistence, and file-activity signals.

### Investigation
I can move from a single event to a timeline and correlate multiple event types.

### Threat Hunting
I can start with a hypothesis and search for supporting or contradicting evidence.

### Incident Response
I can document triage, containment, eradication, recovery, and lessons learned.

### Reporting
I can explain technical findings in a way that another analyst or manager can understand.

---

## 4. Evidence Standard

Throughout this project, I use four labels:

| Label | Meaning |
|---|---|
| Observed | The event was actually seen in collected telemetry |
| Simulated | I intentionally generated the behavior |
| Attempted | I tested the behavior, but success was not proven |
| Not observed | The expected telemetry was not available |

This prevents the report from overstating what the evidence proves.

---

## 5. Safety

This is a controlled training project.

- No real malware was executed.
- No real credential extraction was performed.
- No destructive ransomware was used.
- Ransomware behavior was represented using harmless test files.
- Credential access was simulated.
- SMB activity was performed between the user's own lab systems.

---

## 6. Final Analyst Conclusion

The project demonstrates an end-to-end SOC investigation workflow.

The combined activity is suspicious enough to justify investigation in a real SOC, but the laboratory evidence must be interpreted in context. Because the activity was intentionally generated in a controlled environment, the project does **not** establish a real-world compromise.

---

## 7. Portfolio Skills Demonstrated

- Splunk SPL
- Windows Event ID analysis
- Authentication investigation
- Process investigation
- PowerShell investigation
- Detection engineering
- Threat hunting
- IOC collection
- MITRE ATT&CK mapping
- Incident response
- Incident reporting
- Evidence-based analysis

## Supplied Screenshot Evidence

The current repository contains four final-project screenshots:

1. `01-Final-Project-Environment.png` – hostname `DESKTOP-NH5RCBO`, user `desktop-nh5rcbo\ayush`, IPv4 `192.168.234.130`, gateway `192.168.234.2`.
2. `02-logging and audit verification.png` – Logon auditing is **Success and Failure**; Process Creation auditing is **Success**; `Sysmon64` is **RUNNING**. The displayed `sc query SplunkForwarder` command returns service-not-found, so the screenshot does not prove that the Windows service named `SplunkForwarder` is installed.
3. `03-splunk telementry verification.png` – Splunk search `index=main EventCode=4688` returned **3,429 events** for the displayed 26–27 Sep 2026 window. The visible rows show `SplunkForwarder` process activity on `DESKTOP-NH5RCBO`.
4. `04-Initial Access Failed authentication .png` – the displayed combined 4624/4625 search returned **124 events**, but the visible rows are **SYSTEM / computer-account logon type 5** records with no source network address. This screenshot does not prove the intended `ayush` failed-authentication scenario.

## Evidence Boundary
Only these four screenshots are currently present in the final-project screenshot folder. Later project phases should not be described as screenshot-verified unless their screenshots are actually added. The screenshot folder has not been changed.
