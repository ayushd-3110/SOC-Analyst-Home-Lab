# Lab 5: Registry Persistence Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-PB7D0G9
- **Evidence date:** 26 July 2026
- **SIEM:** Splunk Enterprise

I verified the controlled Run-key entry Lab5Persistence and reviewed the archived dashboard, which displays six registry-related records.

## Investigation limitations

The dashboard's object name, value name and user columns are blank; broad object-access and process creation records do not independently prove changes to the particular value. Execution at the next logon has not been demonstrated.

## Analyst verdict

Controlled registry artifact observed; attacker persistence not established.

Document the actual registry value and distinguish creation, execution and cleanup evidence.

## Documentation

- [Evidence and screenshot observations](Evidence-Observed.md)
- [Incident report](Incident-Report.md)
- [Scenario](Scenario.md)
- [Objectives](Objectives.md)
- [Detection](Detection.md)
- [Investigation](Investigation.md)
- [Splunk Queries](Splunk-Queries.md)
- [Dashboard](Dashboard.md)
- [IOC](IOC.md)
- [MITRE Mapping](MITRE-Mapping.md)
- [Lessons Learned](Lessons-Learned.md)
- [References](References.md)

The original screenshots and dashboard exports are retained as historical evidence. The scripts, searches and scenarios in this folder are training materials; only results explicitly supported by the archived evidence are treated as observed. No new dashboard execution is claimed.
