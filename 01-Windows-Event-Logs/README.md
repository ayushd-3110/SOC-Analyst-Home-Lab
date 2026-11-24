# Lab 1: Windows Authentication Monitoring

## Purpose

I used this controlled SOC exercise to practice reviewing Windows or web telemetry in Splunk, interpreting the available evidence and documenting an analyst verdict.

## Environment and observed results

- **Asset:** DESKTOP-5T5E396
- **Evidence date:** 27 June 2026
- **SIEM:** Splunk Enterprise

I reviewed Windows Security events 4624 and 4625 in Splunk. The dashboard shows 85 successful and 3 failed logon records in the displayed window. At 16:00:32.888, a type 2 logon for LEO failed with status 0xC000006D and substatus 0xC000006A.

## Investigation limitations

The per-user panel attributes the same three failures to LEO and the computer account. Its counts are not independent. Service and machine logons also affect the successful-logon total.

## Analyst verdict

Expected authentication test; no unauthorized access established.

Validate the target account and distinguish interactive, network and service logons. Report event counts separately from unique users.

## Documentation

- [Evidence and screenshot observations](Evidence-Observed.md)
- [Incident report](Incident-Report.md)
- [Lab Setup](Lab-Setup.md)
- [Scenario](Scenario.md)
- [Investigation](Investigation.md)
- [Splunk Queries](Splunk-Queries.md)
- [MITRE](MITRE.md)

The original screenshots and dashboard exports are retained as historical evidence. The scripts, searches and scenarios in this folder are training materials; only results explicitly supported by the archived evidence are treated as observed. No new dashboard execution is claimed.
