# Lab 3: Brute-Force Authentication Investigation

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-PB7D0G9
- **Evidence date:** 24 July 2026 (archived logs)
- **SIEM:** Splunk Enterprise

I reviewed repeated Event 4625 records around 15:26 and Event 4624 records around 15:27–15:32. The archived dashboard shows 54 failed and 346 successful logon events.

## Investigation limitations

The displayed records do not establish that the same account and source succeeded after failures. The protocol and alert trigger are not independently established. The username panel includes missing and machine accounts and inconsistent capitalization; a revised panel is documented but has not been rerun.

## Analyst verdict

Repeated authentication failures observed; successful compromise unverified.

Validate target-account fields and authentication context; record only evidenced timestamps. Review account-lockout and access-control policies.

## Documentation

- [Evidence and screenshot observations](Evidence-Observed.md)
- [Incident report](Incident-Report.md)
- [Lab Setup](Lab-Setup.md)
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
