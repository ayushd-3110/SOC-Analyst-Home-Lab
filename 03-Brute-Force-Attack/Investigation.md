# Investigation — Brute-Force Authentication Investigation

## Question

What does the archived telemetry establish about activity on DESKTOP-PB7D0G9, and what remains uncertain?

## Observations

I reviewed repeated Event 4625 records around 15:26 and Event 4624 records around 15:27–15:32. The archived dashboard shows 54 failed and 346 successful logon events.

## Analysis

The displayed records do not establish that the same account and source succeeded after failures. The protocol and alert trigger are not independently established. The username panel includes missing and machine accounts and inconsistent capitalization; a revised panel is documented but has not been rerun.

## Conclusion and follow-up

Repeated authentication failures observed; successful compromise unverified. Validate target-account fields and authentication context; record only evidenced timestamps. Review account-lockout and access-control policies.

[Evidence observations](Evidence-Observed.md) · [Incident report](Incident-Report.md)
