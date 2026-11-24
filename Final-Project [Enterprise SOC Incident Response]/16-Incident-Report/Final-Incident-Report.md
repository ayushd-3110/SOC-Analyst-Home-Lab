# Final Incident Report — Suspected Windows Endpoint Activity

| Field | Detail |
|---|---|
| Incident ID | INC-2026-001 |
| Analyst | Ayush Dhumal |
| Evidence date | 27 September 2026 (with earlier background telemetry) |
| Affected host | DESKTOP-NH5RCBO |
| Endpoint IP | 192.168.234.130 |
| Test source | 192.168.234.129 |
| SIEM | Splunk Enterprise, index main |
| Severity | Medium — potential risk |
| Status | Closed — controlled exercise |

## Executive summary

I investigated authentication and endpoint activity in a private Windows/Splunk training environment. The aim was to determine whether the evidence supported an incident chain, not to assume that every matching event represented an intrusion.

The archived evidence confirms a successful network logon for ayush from the test source, subsequent user process activity, scheduled-task creation and harmless simulation markers. Repeated failures preceding that same successful logon, a common session linking subsequent processes, credential theft, lateral movement and actual encryption were not established.

## Evidence-backed timeline

These are timestamps displayed by the archived Splunk searches on 27 September 2026. They represent separate observations, not a proven causal chain.

| Time | Observation | Evidence |
|---|---|---|
| 15:12:04.251 | Event 4624, ayush, source 192.168.234.129, logon type 3, NTLM | 152056 |
| 15:35:52.128 | Harmless incident simulation marker | 161800 |
| 15:36:08.449 | Harmless PowerShell simulation marker | 161800 |
| 15:39:37.045 | User PowerShell process event | 154036 |
| 16:06:32.501 | Scheduled-task creation process event | 161024 |
| 16:07:24.145 | Task query process event | 161024 |
| 16:11:04.066 | Credential-access simulation marker | 161128 |
| 16:11:10.719 | Second credential-access simulation marker | 161147 |
| 16:17:19.417 | Impact simulation marker | 161800 |
| 16:17:24.949 | Directory inspection process event | 161800 |
| 16:32 capture | Nine historical task-name-related process records; task fields blank | 163212 |
| 16:34 capture | Host and directory recovery check | 163457 |
| 16:36 capture | Combined search showing 3,145 event records | 163611 |

See the [complete screenshot index](../Screenshots/README.md) for the exact filenames and interpretation.

## Investigation and limitations

- **Preparation:** Host identity, address, logon auditing and process auditing were displayed; Sysmon64 was running. The forwarder service check used a misspelled name and failed. Splunk nevertheless contains process events; current service state was not independently established.
- **Authentication:** The first combined capture displays service logons and omits EventCode. The later 4624-only capture includes a matching user network logon. A preceding failure sequence for the same account/source remains unverified.
- **Execution and discovery:** User PowerShell activity is visible, but broad searches include routine forwarding processes and older discovery records from 26 September. Timestamp proximity does not establish a shared session.
- **Persistence:** The terminal confirms creation and verification of the controlled scheduled task. At verification it was Ready; successful execution and final deletion are not independently shown by a task-status record. The later historical search returns process records, not confirmation of removal.
- **Credential access:** Two harmless process markers were observed. No credential extraction occurred or is claimed.
- **Lateral movement:** A network logon does not independently establish movement between compromised hosts or access to a particular share.
- **Impact:** Process markers and directory inspection are visible. Actual file encryption and destructive behavior are not established.

## Response and recovery

The exercise documents response considerations and a recovery check. The final recovery terminal shows the endpoint operational and the final-project directory absent from its displayed listing. This is partial cleanup evidence; the task's absence and ongoing forwarding health require separate verification. One archived capture contains planning instructions rather than execution evidence and is retained solely as context.

## Analyst verdict

The controlled exercise demonstrates investigation, evidence interpretation, timeline construction and reporting. It does not establish a confirmed host compromise or a completed adversary chain. No production impact was identified. Any ATT&CK mapping describes the behavior observed or the training objective, not proof of successful malicious activity.

## Follow-up

Preserve original events, document field extraction and source-specific context, and record fixed time windows for any rerun. The archived searches were not re-executed as part of this documentation revision.
