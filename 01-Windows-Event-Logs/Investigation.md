# Investigation — Windows Authentication Monitoring

## Question

What does the archived telemetry establish about activity on DESKTOP-5T5E396, and what remains uncertain?

## Observations

I reviewed Windows Security events 4624 and 4625 in Splunk. The dashboard shows 85 successful and 3 failed logon records in the displayed window. At 16:00:32.888, a type 2 logon for LEO failed with status 0xC000006D and substatus 0xC000006A.

## Analysis

The per-user panel attributes the same three failures to LEO and the computer account. Its counts are not independent. Service and machine logons also affect the successful-logon total.

## Conclusion and follow-up

Expected authentication test; no unauthorized access established. Validate the target account and distinguish interactive, network and service logons. Report event counts separately from unique users.

[Evidence observations](Evidence-Observed.md) · [Incident report](Incident-Report.md)
