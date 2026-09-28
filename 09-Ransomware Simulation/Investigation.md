
# Investigation

## Investigation Objective

The objective was to determine whether suspicious process activity was associated with ransomware-like behavior.

---

## Investigation Steps

### 1. Identify the Host

Host identified:

DESKTOP-NH5RCBO

### 2. Identify the User

The process creation event showed:

Account Name: ayush

### 3. Identify the Process

The observed process was:

C:\Windows\System32\cmd.exe

### 4. Identify the Parent Process

The 4688 event contained:

Creator Process Name

This allows the analyst to understand which process launched CMD.

### 5. Review the Command Line

Example observed command:

cmd /c dir C:\SOC-Ransomware-Lab

The command confirmed activity involving the dedicated ransomware simulation directory.

### 6. Review Timeline

The analyst should review surrounding 4688 events to determine whether multiple related processes were created within a short period.

---

## Investigation Query

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Account Name:\s+(?<user>[^\r\n]+)"
| rex field=Message "New Process Name:\s+(?<process_name>[^\r\n]+)"
| rex field=Message "Creator Process Name:\s+(?<parent_process>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| search command_line="*SOC-Ransomware-Lab*"
    OR command_line="*RANSOMWARE*"
    OR command_line="*.locked*"
| table _time host user process_name parent_process command_line
| sort - _time

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
