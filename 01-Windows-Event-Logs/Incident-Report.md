# Incident Report — Windows Authentication Monitoring

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-01 |
| Analyst | Ayush Dhumal |
| Evidence date | 27 June 2026 |
| Affected asset | DESKTOP-5T5E396 |
| Severity | Informational |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed Windows Security events 4624 and 4625 in Splunk. The dashboard shows 85 successful and 3 failed logon records in the displayed window. At 16:00:32.888, a type 2 logon for LEO failed with status 0xC000006D and substatus 0xC000006A.

## Evidence limitations and false positives

The per-user panel attributes the same three failures to LEO and the computer account. Its counts are not independent. Service and machine logons also affect the successful-logon total.

## Analyst verdict

Expected authentication test; no unauthorized access established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Validate the target account and distinguish interactive, network and service logons. Report event counts separately from unique users. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
