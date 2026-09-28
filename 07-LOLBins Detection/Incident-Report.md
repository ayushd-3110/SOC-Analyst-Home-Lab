# Incident Report

## Incident Title

Potential LOLBin Execution — certutil.exe

## Incident Type

Suspicious Process Execution

## Severity

Low / Informational

## Affected Host

DESKTOP-NH5RCBO

## User

ayush

## Process

C:\Windows\System32\certutil.exe

## Parent Process

C:\Windows\System32\cmd.exe

## Command Line

certutil -dump C:\Windows\System32\notepad.exe

## Detection Source

Windows Security Event ID 4688

## SIEM

Splunk Enterprise

## Investigation Summary

A Windows process-creation event was generated when certutil.exe
was executed from Command Prompt.

The SOC investigation reviewed the executing user, affected host,
parent process, executable path, and command line.

The activity was intentionally generated as part of a controlled
SOC detection lab.

## Findings

No malicious payload, external destination, or confirmed compromise
was observed.

## Verdict

Benign / Controlled Security Testing

## Response

No containment required.

The event should be documented and the alert closed as authorized
lab activity.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
