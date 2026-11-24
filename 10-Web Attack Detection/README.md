# Lab 10: IIS Web Security Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** Windows IIS endpoint 192.168.234.130
- **Evidence date:** 31 August 2026
- **SIEM:** Splunk Enterprise

I reviewed the archived IIS dashboard showing 2,560 classified request events from 192.168.234.129. The available screenshots include missing-resource responses and an application warning for SQL-like input.

## Investigation limitations

Counts represent classified requests, not successful attacks. The warning and HTTP response codes do not establish database access or unauthorized file disclosure. Two dashboard tabs retain default labels.

## Analyst verdict

Controlled web request investigation; exploitation not established.

Record request classification, status, source, time and application response without equating a match to compromise.

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
