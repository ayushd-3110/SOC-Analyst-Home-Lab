# Investigation — PowerShell Activity Investigation

## Question

What does the archived telemetry establish about activity on DESKTOP-PB7D0G9, and what remains uncertain?

## Observations

I reviewed Windows process and PowerShell Operational telemetry. The archived dashboard includes Event 4104 and 799 total PowerShell events, while the activity-by-host panel shows 13 records.

## Analysis

The panels use different scopes that have not been reconciled. ScriptBlockText is blank and the user is NOT_TRANSLATED. Event Code 1.png is a SecurityCenter Application event, not Sysmon process creation.

## Conclusion and follow-up

Suspicious-looking test activity observed; no malicious payload established. Validate the event provider, source, account resolution and field availability before interpreting dashboard counts.

[Evidence observations](Evidence-Observed.md) · [Incident report](Incident-Report.md)
