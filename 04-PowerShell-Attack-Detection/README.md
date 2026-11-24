# Lab 4: PowerShell Activity Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-PB7D0G9
- **Evidence date:** 25–26 July 2026
- **SIEM:** Splunk Enterprise

I reviewed Windows process and PowerShell Operational telemetry. The archived dashboard includes Event 4104 and 799 total PowerShell events, while the activity-by-host panel shows 13 records.

## Investigation limitations

The panels use different scopes that have not been reconciled. ScriptBlockText is blank and the user is NOT_TRANSLATED. Event Code 1.png is a SecurityCenter Application event, not Sysmon process creation.

## Analyst verdict

Suspicious-looking test activity observed; no malicious payload established.

Validate the event provider, source, account resolution and field availability before interpreting dashboard counts.

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

The original screenshots and dashboard exports are retained as historical evidence. The scripts, searches and scenarios in this folder are training materials; only results explicitly supported by the archived evidence are treated as observed. No new dashboard execution is claimed.
