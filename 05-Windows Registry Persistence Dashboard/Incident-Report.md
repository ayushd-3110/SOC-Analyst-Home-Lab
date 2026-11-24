# Incident Report — Registry Persistence Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-05 |
| Analyst | Ayush Dhumal |
| Evidence date | 26 July 2026 |
| Affected asset | DESKTOP-PB7D0G9 |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I verified the controlled Run-key entry Lab5Persistence and reviewed the archived dashboard, which displays six registry-related records.

## Evidence limitations and false positives

The dashboard's object name, value name and user columns are blank; broad object-access and process creation records do not independently prove changes to the particular value. Execution at the next logon has not been demonstrated.

## Analyst verdict

Controlled registry artifact observed; attacker persistence not established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Document the actual registry value and distinguish creation, execution and cleanup evidence. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
