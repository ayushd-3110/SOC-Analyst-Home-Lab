# Lab 7 — LOLBins Detection & Investigation

## Overview

This lab demonstrates the detection and investigation of potentially
abused Windows Living-off-the-Land Binaries (LOLBins).

The lab uses Windows Security Event ID 4688 and Splunk Enterprise to
detect process execution and investigate the associated user, host,
parent process, and command line.

## Environment

- Windows Victim
- Splunk Enterprise
- Splunk Universal Forwarder
- Windows Security Logs
- Event ID 4688

## LOLBin Used

certutil.exe

## Objective

Detect and investigate suspicious execution of legitimate Windows
binaries using SIEM-based process telemetry.

## Attack Simulation

certutil -dump C:\Windows\System32\notepad.exe

The command was executed in a controlled lab environment.

## Detection

Windows Security Event ID 4688 was used to detect the creation of
certutil.exe.

## Investigation

The following information was investigated:

- User
- Host
- Process
- Parent process
- Command line
- Timestamp

## MITRE ATT&CK

T1218 — System Binary Proxy Execution

## Result

The activity was successfully detected and investigated in Splunk.

The observed activity was classified as controlled/benign lab activity.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
