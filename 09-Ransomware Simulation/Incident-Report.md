# Incident Report — Ransomware-Style File Activity Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-09 |
| Analyst | Ayush Dhumal |
| Evidence date | 29 August 2026 |
| Affected asset | DESKTOP-NH5RCBO |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed the terminal evidence of 20 test-file rename operations and the archived dashboard, which shows one process marker at 15:12:44.913.

## Evidence limitations and false positives

The dashboard marker is not file-operation telemetry and does not independently prove all 20 operations. Renaming files does not encrypt their contents.

## Analyst verdict

Harmless file-activity exercise; no ransomware or encryption established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Separate observed filesystem outcomes from process evidence and document encryption-for-impact as a conceptual simulation only. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
