# Incident Report — Network Connection and Port-Scan Investigation

| Field | Detail |
|---|---|
| Incident ID | SOC-LAB-02 |
| Analyst | Ayush Dhumal |
| Evidence date | 2 July 2026 |
| Affected asset | Windows endpoint 192.168.234.133 |
| Severity | Medium (potential risk) |
| Disposition | Closed — controlled training exercise |

## Investigation findings

I reviewed the recorded scan and Windows network telemetry. The investigation shows 8,072 Event 5156 records, including browser, DNS and Splunk forwarding activity.

## Evidence limitations and false positives

The dashboard reflects total permitted connections, not 8,072 scan attempts. The Windows endpoint is the leading source in the dashboard. Event 5158 indicates a local port bind and cannot establish scanning independently.

## Analyst verdict

Controlled network reconnaissance exercise; exploitation not established. No production impact was established in the supplied evidence. The severity describes the hypothetical risk in a real environment, not a confirmed incident.

## Response and lessons learned

Separate background traffic from the documented test activity; record direction, source, destination, time window and evidence limitations. No production containment action was taken or claimed for this exercise.

## Evidence reference

See [Evidence-Observed.md](Evidence-Observed.md) and the original screenshots in this lab. The archived dashboard is historical evidence; any revised detection or presentation must be validated separately in Splunk.
