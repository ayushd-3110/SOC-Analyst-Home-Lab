# Incident Report — Endpoint Threat Hunting

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-14 |
| Analyst | Ayush Dhumal |
| Evidence date | 26 September 2026 |
| Affected asset | DESKTOP-NH5RCBO |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed the archived dashboard and mixed authentication/process timeline. The discovery chart groups 11 network, 8 user, 2 process and 1 system discovery matches.

## Evidence limitations and false positives

The suspicious process panel includes ordinary Splunk forwarding activity. An event list does not establish an authentication-to-process chain; the displayed results include unrelated background telemetry.

## Analyst verdict

Controlled hunt completed; no confirmed compromise or causal chain established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

State the hypothesis and its observed limitations, validate authorized activity, and distinguish findings from investigation leads. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
