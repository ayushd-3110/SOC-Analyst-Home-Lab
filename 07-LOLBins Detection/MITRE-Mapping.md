# MITRE ATT&CK Mapping

## Technique

T1218 — System Binary Proxy Execution

## Description

Attackers may abuse trusted and legitimate system binaries to execute
actions while blending into normal Windows activity.

## Observed Behavior

The lab executed:

C:\Windows\System32\certutil.exe

The process was launched by:

C:\Windows\System32\cmd.exe

## Evidence

Windows Security Event ID 4688.

## Important Note

The execution of certutil.exe alone does not prove malicious activity.
The command line, parent process, user, host, and surrounding events
must be investigated before determining malicious intent.