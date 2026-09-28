# Incident Report

## Incident Information

* Incident ID: SOC-LAB-04
* Incident Name: Suspicious PowerShell Execution
* Severity: High
* Analyst: Ayush
* Status: Closed

## Executive Summary

Splunk detected suspicious PowerShell execution on a Windows workstation. The command line contained `-ExecutionPolicy Bypass`, a parameter frequently associated with attacker activity.

The event was investigated using Sysmon process creation logs.

## Affected Asset

* Host: DESKTOP-PB7DOG9
* User: ayush

## Evidence

Primary Evidence

- PowerShell Operational Log (Event ID 4104)
- Script Block Logging

Secondary Evidence

- Windows Security Event ID 4688
- Process Creation Events
- Splunk Dashboard

## MITRE ATT&CK

* T1059.001 – PowerShell

## Risk Assessment

* Likelihood: High
* Impact: Medium
* Business Risk: Unauthorized script execution and potential malware delivery.

## Recommendations

* Monitor PowerShell activity.
* Alert on `ExecutionPolicy Bypass`.
* Enable Script Block Logging.
* Restrict unnecessary PowerShell usage.
* Investigate PowerShell download activity.

## Conclusion

The activity matched known PowerShell attacker tradecraft. In this lab, the event was generated intentionally to validate detection capabilities and SOC investigation procedures.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
