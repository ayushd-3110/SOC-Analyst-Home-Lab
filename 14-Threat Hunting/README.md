# Lab 14 – Threat Hunting

## Overview

This lab demonstrates a proactive Threat Hunting investigation using Windows endpoint telemetry and Splunk.

Unlike traditional detection, where an alert is already generated, threat hunting starts with a hypothesis and searches available telemetry for evidence of suspicious activity.

In this controlled lab, Windows discovery commands, PowerShell activity, process execution, and authentication activity were simulated. Splunk was then used to investigate and correlate the resulting events.

---

## Scenario

The SOC receives intelligence that a Windows workstation may have been compromised.

There is no confirmed malware alert. The SOC analyst is therefore asked to proactively hunt for signs of compromise.

The investigation focuses on:

- User discovery
- System discovery
- Network discovery
- Process discovery
- PowerShell execution
- Suspicious parent-child process relationships
- Authentication activity
- Process and authentication correlation

All activity was generated in a controlled SOC home lab.

---

## Lab Environment

| Component | Details |
|---|---|
| Attacker / Simulation Machine | Kali Linux |
| Kali IP | 192.168.234.129 |
| Victim Machine | Windows |
| Windows IP | 192.168.234.130 |
| Hostname | DESKTOP-NH5RCBO |
| User | ayush |
| SIEM | Splunk Enterprise |
| Splunk Index | main |
| Primary Event | Windows Event ID 4688 |

---

## Objectives

1. Understand proactive threat hunting.
2. Create a threat-hunting hypothesis.
3. Generate controlled endpoint activity.
4. Hunt for PowerShell activity.
5. Hunt for Windows discovery commands.
6. Analyze parent-child process relationships.
7. Correlate authentication with process execution.
8. Build an activity timeline.
9. Extract potential investigation indicators.
10. Document the investigation like a SOC analyst.

---

## Threat-Hunting Hypothesis

> If a Windows endpoint has been compromised, suspicious command execution may appear through PowerShell or Windows Command Shell, followed by discovery activity and unusual process execution.

The hypothesis is tested against Windows endpoint telemetry collected in Splunk.

---

## Main Investigation Flow

```text
Threat Intelligence / Suspicion
             ↓
       Hunting Hypothesis
             ↓
     Windows Telemetry
             ↓
       Splunk Hunting
             ↓
     PowerShell Activity
             ↓
      Discovery Activity
             ↓
   Process Chain Analysis
             ↓
 Authentication Correlation
             ↓
      Investigation Timeline
             ↓
      Hunting Conclusion

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
