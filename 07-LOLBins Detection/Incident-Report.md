# Incident Report — LOLBins Process Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-07 |
| Analyst | Ayush Dhumal |
| Evidence date | 23 August 2026 |
| Affected asset | DESKTOP-NH5RCBO |
| Severity | Low / Informational |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed an archived dashboard showing one certutil.exe process event associated with ayush and a local file-inspection operation.

## Evidence limitations and false positives

A legitimate signed utility being executed does not establish abuse. The panel titled Total single value is an archived presentation issue.

## Analyst verdict

Benign controlled utility execution. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Review the executable path, parent process, command context and authorization; mark any technique mapping as conceptual unless its behavior is observed. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
