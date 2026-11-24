# Investigation — Suspected Account Compromise Investigation

## Question

What does the archived telemetry establish about activity on DESKTOP-NH5RCBO, and what remains uncertain?

## Observations

I reviewed the documented four failed logons for ayush from 192.168.234.129. The archived dashboard shows 90 authentication events; the visible successful-logon rows are SYSTEM/computer-account type 5 entries.

## Analysis

The available Lab 12 screenshots do not prove a successful ayush logon or link post-authentication processes to that account. The displayed process rows are dominated by Splunk forwarding activity.

## Conclusion and follow-up

Suspicious authentication failures observed; confirmed account compromise not established. Check matching account, source, time and session context before attributing subsequent activity; preserve the gap in the record.

[Evidence observations](Evidence-Observed.md) · [Incident report](Incident-Report.md)
