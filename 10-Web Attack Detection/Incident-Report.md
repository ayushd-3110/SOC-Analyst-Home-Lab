# Incident Report — IIS Web Security Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-10 |
| Analyst | Ayush Dhumal |
| Evidence date | 31 August 2026 |
| Affected asset | Windows IIS endpoint 192.168.234.130 |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed the archived IIS dashboard showing 2,560 classified request events from 192.168.234.129. The available screenshots include missing-resource responses and an application warning for SQL-like input.

## Evidence limitations and false positives

Counts represent classified requests, not successful attacks. The warning and HTTP response codes do not establish database access or unauthorized file disclosure. Two dashboard tabs retain default labels.

## Analyst verdict

Controlled web request investigation; exploitation not established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Record request classification, status, source, time and application response without equating a match to compromise. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
