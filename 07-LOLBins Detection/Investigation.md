# Investigation

## 1. Alert Identification

Identify the suspicious LOLBin execution.

Observed:

certutil.exe

## 2. User Investigation

Account:

ayush

Determine whether the account is expected to perform administrative
or troubleshooting activity.

## 3. Host Investigation

Host:

DESKTOP-NH5RCBO

Determine the role of the endpoint and whether the user normally
uses the system.

## 4. Process Investigation

New Process:

C:\Windows\System32\certutil.exe

## 5. Parent Process Investigation

Parent:

C:\Windows\System32\cmd.exe

The parent-child relationship should be reviewed for suspicious
execution chains.

## 6. Command-Line Investigation

Observed:

certutil -dump C:\Windows\System32\notepad.exe

The command was generated intentionally as part of this SOC lab.

## 7. Timeline Investigation

Review surrounding Event ID 4688 events and other available telemetry
to determine whether additional suspicious activity occurred.

## 8. Verdict

The observed activity is:

Benign / Controlled Lab Activity

No containment is required.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
