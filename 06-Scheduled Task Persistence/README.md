# Lab 6: Scheduled Task Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-PB7D0G9
- **Evidence date:** 20 August 2026
- **SIEM:** Splunk Enterprise

I reviewed Event 4698 at 20:39:19.368 for task WindowsUpdateCheck, created by ayush. The archived dashboard shows two creation records.

## Investigation limitations

The dashboard's extracted user column is blank despite the account appearing in the raw event. Creation does not establish later execution or deletion.

## Analyst verdict

Authorized scheduled-task exercise; no malicious payload established.

Document the creator, task identity, trigger, action, and any separately verified execution or cleanup.

## Documentation

- [Evidence and screenshot observations](Evidence-Observed.md)
- [Incident report](Incident-Report.md)
- [Scenario](Scenario.md)
- [Objectives](Objectives.md)
- [Detection](Detection.md)
- [Investigation](Investigation.md)
- [Splunk Queries](Splunk-Queries.md)
- [IOC](IOC.md)
- [MITRE Mapping](MITRE-Mapping.md)
- [Lessons Learned](Lessons-Learned.md)
- [References](References.md)

The original screenshots and dashboard exports are retained as historical evidence. The scripts, searches and scenarios in this folder are training materials; only results explicitly supported by the archived evidence are treated as observed. No new dashboard execution is claimed.
