# 01 – Incident Scenario

## Incident

**INC-2026-001 – Suspected Windows Endpoint Compromise**

## Scenario

The SOC receives an alert for unusual authentication activity against a Windows workstation.

The initial evidence shows multiple failed authentication attempts followed by a successful authentication.

The analyst then finds endpoint process activity and PowerShell execution. Further investigation identifies account, system, network, and process discovery. Additional controlled activity is generated to demonstrate persistence, credential access, SMB/lateral-movement investigation, and impact detection.

The analyst must determine what happened, what can actually be proven by the logs, and what response actions are appropriate.

## Investigation Question

> Does the available telemetry support a suspicious endpoint activity chain, and what can the analyst confidently conclude from the evidence?

## Objectives

1. Investigate authentication anomalies.
2. Correlate authentication with process execution.
3. Identify PowerShell and discovery activity.
4. Investigate simulated persistence.
5. Investigate credential-access behavior without extracting credentials.
6. Review SMB activity as a lateral-movement investigation.
7. Detect harmless ransomware-style activity.
8. Perform threat hunting.
9. Document containment, eradication, and recovery.
10. Produce a professional incident report.

## Supplied Screenshot Evidence

The current repository contains four final-project screenshots:

1. `01-Final-Project-Environment.png` – hostname `DESKTOP-NH5RCBO`, user `desktop-nh5rcbo\ayush`, IPv4 `192.168.234.130`, gateway `192.168.234.2`.
2. `02-logging and audit verification.png` – Logon auditing is **Success and Failure**; Process Creation auditing is **Success**; `Sysmon64` is **RUNNING**. The displayed `sc query SplunkForwarder` command returns service-not-found, so the screenshot does not prove that the Windows service named `SplunkForwarder` is installed.
3. `03-splunk telementry verification.png` – Splunk search `index=main EventCode=4688` returned **3,429 events** for the displayed 26–27 Sep 2026 window. The visible rows show `SplunkForwarder` process activity on `DESKTOP-NH5RCBO`.
4. `04-Initial Access Failed authentication .png` – the displayed combined 4624/4625 search returned **124 events**, but the visible rows are **SYSTEM / computer-account logon type 5** records with no source network address. This screenshot does not prove the intended `ayush` failed-authentication scenario.

## Evidence Boundary
Only these four screenshots are currently present in the final-project screenshot folder. Later project phases should not be described as screenshot-verified unless their screenshots are actually added. The screenshot folder has not been changed.
