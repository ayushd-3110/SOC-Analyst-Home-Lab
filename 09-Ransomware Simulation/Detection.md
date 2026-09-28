
# Detection

## Detection Objective

The objective was to identify suspicious process activity associated with the controlled ransomware simulation.

Windows Security Event ID 4688 was used as the primary telemetry source.

---

## Primary Detection Query

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| search command_line="*SOC-Ransomware-Lab*"
    OR command_line="*RANSOMWARE*"
    OR command_line="*.locked*"
| table _time host EventCode command_line Message
| sort - _time

What the Detection Looks For

The query searches for process creation events containing:

SOC-Ransomware-Lab
RANSOMWARE
.locked

These indicators are specific to the controlled lab simulation.

Observed Event

Event ID:

4688

Process:

C:\Windows\System32\cmd.exe

User:

ayush

Host:

DESKTOP-NH5RCBO

The logs showed that CMD was used to access the ransomware simulation directory.
