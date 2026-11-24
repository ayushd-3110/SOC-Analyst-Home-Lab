# Incident Report — Brute-Force Authentication Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-03 |
| Analyst | Ayush Dhumal |
| Evidence date | 24 July 2026 (archived logs) |
| Affected asset | DESKTOP-PB7D0G9 |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed repeated Event 4625 records around 15:26 and Event 4624 records around 15:27–15:32. The archived dashboard shows 54 failed and 346 successful logon events.

## Evidence limitations and false positives

The displayed records do not establish that the same account and source succeeded after failures. The protocol and alert trigger are not independently established. The username panel includes missing and machine accounts and inconsistent capitalization; a revised panel is documented but has not been rerun.

## Analyst verdict

Repeated authentication failures observed; successful compromise unverified. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Validate target-account fields and authentication context; record only evidenced timestamps. Review account-lockout and access-control policies. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
