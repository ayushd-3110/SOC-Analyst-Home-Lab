# Lab 14: Endpoint Threat Hunting

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-NH5RCBO
- **Evidence date:** 26 September 2026
- **SIEM:** Splunk Enterprise

I reviewed the archived dashboard and mixed authentication/process timeline. The discovery chart groups 11 network, 8 user, 2 process and 1 system discovery matches.

## Investigation limitations

The suspicious process panel includes ordinary Splunk forwarding activity. An event list does not establish an authentication-to-process chain; the displayed results include unrelated background telemetry.

## Analyst verdict

Controlled hunt completed; no confirmed compromise or causal chain established.

State the hypothesis and its observed limitations, validate authorized activity, and distinguish findings from investigation leads.

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
