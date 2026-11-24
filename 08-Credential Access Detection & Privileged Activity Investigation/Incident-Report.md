# Incident Report — Credential-Access Indicator and Privileged Logon Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-08 |
| Analyst | Ayush Dhumal |
| Evidence date | 25–28 August 2026 |
| Affected asset | DESKTOP-NH5RCBO |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed a harmless credential-access keyword marker in Event 4688 and separate authentication and privilege events. At 01:05:40.279 on 25 August, Event 4624 shows logon type 5 and Event 4672 identifies SYSTEM with logon ID 0x3E7.

## Evidence limitations and false positives

The service logon is not an interactive ayush session, and SYSTEM privileges cannot be attributed to ayush. The archived dashboard shows one marker, no process-panel results and a missing username.

## Analyst verdict

Keyword-based detection concept demonstrated; no credential dumping or privilege escalation established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Review account and session identity before associating events; treat a keyword match as an investigation lead. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
