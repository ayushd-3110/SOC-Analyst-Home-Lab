# Detection

## Detection Objective

Detect execution of potentially abused Windows LOLBins using Windows
Security Event ID 4688.

## Primary Telemetry

Event ID: 4688
Source: WinEventLog:Security

## Primary LOLBin

certutil.exe

## Detection Logic

The detection searches Windows process creation events for known
LOLBin executable names.

A LOLBin execution is treated as suspicious activity requiring
investigation. It is not automatically classified as malicious.

## Observed Activity

Process:

C:\Windows\System32\certutil.exe

Parent:

C:\Windows\System32\cmd.exe

Command Line:

certutil -dump C:\Windows\System32\notepad.exe