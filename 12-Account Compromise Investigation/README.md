# Lab 12: Suspected Account Compromise Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-NH5RCBO
- **Evidence date:** 26 September 2026
- **SIEM:** Splunk Enterprise

I reviewed the documented four failed logons for ayush from 192.168.234.129. The archived dashboard shows 90 authentication events; the visible successful-logon rows are SYSTEM/computer-account type 5 entries.

## Investigation limitations

The available Lab 12 screenshots do not prove a successful ayush logon or link post-authentication processes to that account. The displayed process rows are dominated by Splunk forwarding activity.

## Analyst verdict

Suspicious authentication failures observed; confirmed account compromise not established.

Check matching account, source, time and session context before attributing subsequent activity; preserve the gap in the record.

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
