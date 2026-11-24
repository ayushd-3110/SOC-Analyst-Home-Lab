# Incident Report — PowerShell Activity Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-04 |
| Analyst | Ayush Dhumal |
| Evidence date | 25–26 July 2026 |
| Affected asset | DESKTOP-PB7D0G9 |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed Windows process and PowerShell Operational telemetry. The archived dashboard includes Event 4104 and 799 total PowerShell events, while the activity-by-host panel shows 13 records.

## Evidence limitations and false positives

The panels use different scopes that have not been reconciled. ScriptBlockText is blank and the user is NOT_TRANSLATED. Event Code 1.png is a SecurityCenter Application event, not Sysmon process creation.

## Analyst verdict

Suspicious-looking test activity observed; no malicious payload established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Validate the event provider, source, account resolution and field availability before interpreting dashboard counts. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
