# Screenshot Evidence Review

The screenshots show execution of the Windows LOLBin **certutil.exe**. The visible 4688 event contains:

- Account: **ayush**
- Host: **DESKTOP-NH5RCBO**
- New process: `C:\Windows\System32\certutil.exe`
- Parent process: `C:\Windows\System32\cmd.exe`
- Command line: `certutil -dump C:\Windows\System32\notepad.exe`

The screenshot set also contains Splunk detection and investigation views plus a LOLBin Detection dashboard.

## Evidence Boundary
The command demonstrates LOLBin execution. It does not by itself prove malicious intent.

## Additional review findings

A legitimate signed utility being executed does not establish abuse. The panel titled Total single value is an archived presentation issue.

**Disposition:** Benign controlled utility execution.
