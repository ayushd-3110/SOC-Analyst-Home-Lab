# Lab 11: Phishing Link Triage

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** Windows IIS endpoint 192.168.234.130
- **Evidence date:** 25 September 2026
- **SIEM:** Splunk Enterprise

I reviewed seven recorded HTTP requests from 192.168.234.129 between 14:35:20 and 14:38:32. All returned HTTP 404. The paths were /verify, /account and /login.

## Investigation limitations

The requests reflect controlled URL investigation, not confirmed victim interaction. An original email file and independently verified mail-header authentication are not available in this repository.

## Analyst verdict

Suspicious sample email investigated; no credential submission or compromise established.

Preserve an original email and headers when available; distinguish mail-delivery, URL access and credential-submission evidence.

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
