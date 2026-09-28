
---

# 12. `Incident-Report.md`

```markdown
# Incident Report

## Incident Information

| Field | Details |
|---|---|
| Incident ID | SOC-LAB14-INC-001 |
| Title | Threat Hunting – Suspicious Windows Endpoint Activity |
| Category | Threat Hunting / Endpoint Investigation |
| Severity | Medium |
| Priority | P2 |
| Status | Closed – Controlled Lab Simulation |
| Analyst | Ayush Dhumal |
| Host | DESKTOP-NH5RCBO |
| IP | 192.168.234.130 |
| User | ayush |

---

## Executive Summary

A proactive threat-hunting investigation was performed on a Windows workstation after intelligence suggested possible unauthorized activity.

The analyst searched Windows endpoint telemetry for authentication events, process creation, PowerShell execution, and system discovery commands.

Controlled laboratory activity was generated to test the hunting hypothesis.

---

## Investigation Findings

The investigation examined:

- Windows authentication activity
- Process creation
- PowerShell execution
- User discovery
- System discovery
- Network discovery
- Process relationships

The available telemetry was correlated in Splunk to build an investigation timeline.

---

## Evidence

Primary evidence sources:

- Windows Event ID 4624
- Windows Event ID 4625
- Windows Event ID 4688
- Splunk search results
- Process command lines
- Parent-child process information

---

## Analysis

PowerShell and Windows discovery commands were identified as part of the controlled laboratory activity.

The presence of these commands alone does not establish malicious activity because the commands are also legitimate administrative functions.

The investigation therefore considered process relationships, authentication activity, command lines, users, and timestamps.

---

## Final Classification

**Controlled Threat-Hunting Simulation**

No real-world compromise was established from this laboratory exercise.

---

## Recommended Real-SOC Actions

If similar activity were detected in a production environment, an analyst could:

1. Validate the affected user.
2. Verify whether the activity was authorized.
3. Investigate the source IP.
4. Review the complete process tree.
5. Review PowerShell logs.
6. Check for persistence mechanisms.
7. Review additional endpoint activity.
8. Search for the same indicators across other hosts.
9. Preserve relevant evidence.
10. Escalate if evidence supports compromise.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
