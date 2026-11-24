# Lab 8: Credential-Access Indicator and Privileged Logon Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-NH5RCBO
- **Evidence date:** 25–28 August 2026
- **SIEM:** Splunk Enterprise

I reviewed a harmless credential-access keyword marker in Event 4688 and separate authentication and privilege events. At 01:05:40.279 on 25 August, Event 4624 shows logon type 5 and Event 4672 identifies SYSTEM with logon ID 0x3E7.

## Investigation limitations

The service logon is not an interactive ayush session, and SYSTEM privileges cannot be attributed to ayush. The archived dashboard shows one marker, no process-panel results and a missing username.

## Analyst verdict

Keyword-based detection concept demonstrated; no credential dumping or privilege escalation established.

Review account and session identity before associating events; treat a keyword match as an investigation lead.

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
