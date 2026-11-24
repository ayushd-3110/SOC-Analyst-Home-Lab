# Incident Report — Suspected Account Compromise Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-12 |
| Analyst | Ayush Dhumal |
| Evidence date | 26 September 2026 |
| Affected asset | DESKTOP-NH5RCBO |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed the documented four failed logons for ayush from 192.168.234.129. The archived dashboard shows 90 authentication events; the visible successful-logon rows are SYSTEM/computer-account type 5 entries.

## Evidence limitations and false positives

The available Lab 12 screenshots do not prove a successful ayush logon or link post-authentication processes to that account. The displayed process rows are dominated by Splunk forwarding activity.

## Analyst verdict

Suspicious authentication failures observed; confirmed account compromise not established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Check matching account, source, time and session context before attributing subsequent activity; preserve the gap in the record. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
