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

* Sysmon Event ID 1
* PowerShell process creation
* Suspicious command-line arguments

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
