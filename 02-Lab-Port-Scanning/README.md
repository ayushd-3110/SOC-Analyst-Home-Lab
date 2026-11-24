# Lab 2: Network Connection and Port-Scan Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** Windows endpoint 192.168.234.133
- **Evidence date:** 2 July 2026
- **SIEM:** Splunk Enterprise

I reviewed the recorded scan and Windows network telemetry. The investigation shows 8,072 Event 5156 records, including browser, DNS and Splunk forwarding activity.

## Investigation limitations

The dashboard reflects total permitted connections, not 8,072 scan attempts. The Windows endpoint is the leading source in the dashboard. Event 5158 indicates a local port bind and cannot establish scanning independently.

## Analyst verdict

Controlled network reconnaissance exercise; exploitation not established.

Separate background traffic from the documented test activity; record direction, source, destination, time window and evidence limitations.

## Documentation

- [Evidence and screenshot observations](Evidence-Observed.md)
- [Incident report](Incident-Report.md)
- [Lab Setup](Lab-Setup.md)
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
