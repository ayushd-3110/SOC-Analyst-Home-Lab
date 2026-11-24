# Lab 9: Ransomware-Style File Activity Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-NH5RCBO
- **Evidence date:** 29 August 2026
- **SIEM:** Splunk Enterprise

I reviewed the terminal evidence of 20 test-file rename operations and the archived dashboard, which shows one process marker at 15:12:44.913.

## Investigation limitations

The dashboard marker is not file-operation telemetry and does not independently prove all 20 operations. Renaming files does not encrypt their contents.

## Analyst verdict

Harmless file-activity exercise; no ransomware or encryption established.

Separate observed filesystem outcomes from process evidence and document encryption-for-impact as a conceptual simulation only.

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
