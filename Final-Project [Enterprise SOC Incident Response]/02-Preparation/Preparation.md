# Preparation

Before starting the incident simulation, I verified the basic SOC environment.

## Checklist

- Windows VM is running.
- Kali VM is running.
- Splunk is accessible.
- Windows logs are reaching Splunk.
- Event ID 4624 can be searched.
- Event ID 4625 can be searched.
- Event ID 4688 can be searched.
- Sysmon is running where configured.
- Windows process auditing is enabled.
- The lab network allows the required test traffic.

## Why Preparation Matters

A SOC investigation is only as good as its telemetry. If logs are missing, the analyst may not be able to reconstruct the incident.

## Analyst Practice

I first verify that the logging pipeline works before generating the suspicious activity. This gives me a known-good baseline.

## Supplied Screenshot Evidence

The current repository contains four final-project screenshots:

1. `01-Final-Project-Environment.png` – hostname `DESKTOP-NH5RCBO`, user `desktop-nh5rcbo\ayush`, IPv4 `192.168.234.130`, gateway `192.168.234.2`.
2. `02-logging and audit verification.png` – Logon auditing is **Success and Failure**; Process Creation auditing is **Success**; `Sysmon64` is **RUNNING**. The displayed `sc query SplunkForwarder` command returns service-not-found, so the screenshot does not prove that the Windows service named `SplunkForwarder` is installed.
3. `03-splunk telementry verification.png` – Splunk search `index=main EventCode=4688` returned **3,429 events** for the displayed 26–27 Sep 2026 window. The visible rows show `SplunkForwarder` process activity on `DESKTOP-NH5RCBO`.
4. `04-Initial Access Failed authentication .png` – the displayed combined 4624/4625 search returned **124 events**, but the visible rows are **SYSTEM / computer-account logon type 5** records with no source network address. This screenshot does not prove the intended `ayush` failed-authentication scenario.

## Evidence Boundary
Only these four screenshots are currently present in the final-project screenshot folder. Later project phases should not be described as screenshot-verified unless their screenshots are actually added. The screenshot folder has not been changed.
