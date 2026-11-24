# Incident Report — Phishing Link Triage

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-11 |
| Analyst | Ayush Dhumal |
| Evidence date | 25 September 2026 |
| Affected asset | Windows IIS endpoint 192.168.234.130 |
| Severity | Low / Informational |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed seven recorded HTTP requests from 192.168.234.129 between 14:35:20 and 14:38:32. All returned HTTP 404. The paths were /verify, /account and /login.

## Evidence limitations and false positives

The requests reflect controlled URL investigation, not confirmed victim interaction. An original email file and independently verified mail-header authentication are not available in this repository.

## Analyst verdict

Suspicious sample email investigated; no credential submission or compromise established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Preserve an original email and headers when available; distinguish mail-delivery, URL access and credential-submission evidence. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
