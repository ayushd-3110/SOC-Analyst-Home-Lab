# Lab 7: LOLBins Process Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-NH5RCBO
- **Evidence date:** 23 August 2026
- **SIEM:** Splunk Enterprise

I reviewed an archived dashboard showing one certutil.exe process event associated with ayush and a local file-inspection operation.

## Investigation limitations

A legitimate signed utility being executed does not establish abuse. The panel titled Total single value is an archived presentation issue.

## Analyst verdict

Benign controlled utility execution.

Review the executable path, parent process, command context and authorization; mark any technique mapping as conceptual unless its behavior is observed.

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
