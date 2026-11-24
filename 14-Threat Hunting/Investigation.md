# Investigation — Endpoint Threat Hunting

## Question

What does the archived telemetry establish about activity on DESKTOP-NH5RCBO, and what remains uncertain?

## Observations

I reviewed the archived dashboard and mixed authentication/process timeline. The discovery chart groups 11 network, 8 user, 2 process and 1 system discovery matches.

## Analysis

The suspicious process panel includes ordinary Splunk forwarding activity. An event list does not establish an authentication-to-process chain; the displayed results include unrelated background telemetry.

## Conclusion and follow-up

Controlled hunt completed; no confirmed compromise or causal chain established. State the hypothesis and its observed limitations, validate authorized activity, and distinguish findings from investigation leads.

[Evidence observations](Evidence-Observed.md) · [Incident report](Incident-Report.md)
