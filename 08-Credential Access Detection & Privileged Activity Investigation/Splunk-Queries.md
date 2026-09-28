# Splunk Queries

## 1. Find Event 4624 — Successful Logons

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4624
| table _time host EventCode Message
| sort - _time


2. Find Event 4648 — Explicit Credentials

index=main sourcetype="WinEventLog:Security" EventCode=4648
| table _time host EventCode Message
| sort - _time

3. Search for Mimikatz Indicators


index=main sourcetype="WinEventLog:Security" EventCode=4688
| search "mimikatz"
| table _time host Message
| sort - _time

4. Extract Process Information

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Account Name:\s+(?<user>[^\r\n]+)"
| rex field=Message "New Process Name:\s+(?<process_path>[^\r\n]+)"
| rex field=Message "Creator Process Name:\s+(?<parent_process>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| table _time host user process_path parent_process command_line
| sort - _time

5. Investigate Privileged Logons


index=main sourcetype="WinEventLog:Security" EventCode=4672
| table _time host Message
| sort - _time


6. Find Event 4688 — Process Creation


index=main sourcetype="WinEventLog:Security" EventCode=4688
| table _time host EventCode Message
| sort - _time


7. Credential Access Keyword Detection

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| eval command_line=lower(command_line)
| search command_line="*mimikatz*"
    OR command_line="*sekurlsa*"
    OR command_line="*logonpasswords*"
    OR command_line="*lsass*"
    OR command_line="*credential*"
    OR command_line="*privilege::debug*"
| table _time host command_line
| sort - _time


8.Suspicious Credential Access Correlation


index=main sourcetype="WinEventLog:Security"
(EventCode=4624 OR EventCode=4648 OR EventCode=4672 OR EventCode=4688)
| rex field=Message "Account Name:\s+(?<user>[^\r\n]+)"
| rex field=Message "New Process Name:\s+(?<process_path>[^\r\n]+)"
| rex field=Message "Creator Process Name:\s+(?<parent_process>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| eval suspicious=if(
    match(lower(command_line),
    "mimikatz|sekurlsa|logonpasswords|lsass|credential|privilege::debug"),
    "Yes",
    "No"
)
| table _time host EventCode user process_path parent_process command_line suspicious
| sort - _time




9. Investigation query

index=main sourcetype="WinEventLog:Security"
(EventCode=4624 OR EventCode=4648 OR EventCode=4672 OR EventCode=4688)
| rex field=Message "Account Name:\s+(?<username>[^\r\n]+)"
| rex field=Message "SubjectUserName\s+(?<subject_user>[^\r\n]+)"
| rex field=Message "New Process Name:\s+(?<process_path>[^\r\n]+)"
| rex field=Message "Creator Process Name:\s+(?<parent_process>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| eval username=coalesce(username,subject_user)
| eval event_type=case(
    EventCode=4624,"Successful Logon",
    EventCode=4648,"Explicit Credential Use",
    EventCode=4672,"Special Privileges",
    EventCode=4688,"Process Creation"
)
| eval suspicious=if(
    match(lower(command_line),"mimikatz|sekurlsa|logonpasswords|lsass|credential|privilege::debug"),
    "YES",
    "NO"
)
| table _time host EventCode event_type username process_path parent_process command_line suspicious
| sort _time


5 Splunk Dashboard Panel Queries

Panel 1 — Credential Access Events by Event ID
Visualization: Column/Bar Chart

Shows the volume of the important security events.

index=main sourcetype="WinEventLog:Security"
(EventCode=4624 OR EventCode=4648 OR EventCode=4672 OR EventCode=4688)
| stats count by EventCode
| sort EventCode
Title: Credential Access Events by Event ID

What it shows:

4624 → Successful Logon

4648 → Explicit Credentials

4672 → Special Privileges

4688 → Process Creation

Panel 2 — Mimikatz / Credential Access Activity
Visualization: Single Value

This is your most important detection panel.

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| eval command_line=lower(command_line)
| search command_line="*mimikatz*"
    OR command_line="*sekurlsa*"
    OR command_line="*logonpasswords*"
    OR command_line="*lsass*"
    OR command_line="*credential*"
    OR command_line="*privilege::debug*"
| stats count
Title: Suspicious Credential Access Events

This should show the number of suspicious process-creation events.

Your current data should detect the:

cmd /c echo mimikatz credential access simulation
events.

Panel 3 — Suspicious Process Creation Timeline
Visualization: Line Chart

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| eval command_line=lower(command_line)
| search command_line="*mimikatz*"
    OR command_line="*credential*"
    OR command_line="*lsass*"
    OR command_line="*sekurlsa*"
    OR command_line="*logonpasswords*"
| timechart span=5m count
Title: Suspicious Credential Access Timeline

This helps an analyst see when suspicious activity occurred and whether it happened repeatedly.

Panel 4 — Privileged Logon Activity
Visualization: Bar Chart

This focuses on Event ID 4672.

index=main sourcetype="WinEventLog:Security" EventCode=4672
| rex field=Message "Account Name:\s+(?<username>[^\r\n]+)"
| stats count by username
| sort - count
Title: Privileged Logon Activity

This shows which account generated special-privilege events.

Your screenshot provides evidence of:

Account Name: ayush
and also SYSTEM activity.

Panel 5 — High-Risk Privilege Activity
Visualization: Bar Chart

This is particularly useful because your 4672 event contains privileges such as SeDebugPrivilege.

index=main sourcetype="WinEventLog:Security" EventCode=4672
| eval privilege=case(
    like(Message,"%SeDebugPrivilege%"),"SeDebugPrivilege",
    like(Message,"%SeTakeOwnershipPrivilege%"),"SeTakeOwnershipPrivilege",
    like(Message,"%SeBackupPrivilege%"),"SeBackupPrivilege",
    like(Message,"%SeRestorePrivilege%"),"SeRestorePrivilege",
    like(Message,"%SeImpersonatePrivilege%"),"SeImpersonatePrivilege",
    true(),"Other Privilege"
)
| stats count by privilege
| sort - count
Title: High-Risk Privileges Detected

This gives the dashboard a stronger credential-access / privilege-abuse focus.
