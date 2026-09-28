# Splunk Queries

## 1. Verify Event ID 4688

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4688
| table _time host EventCode Message
| sort - _time


## 2. Basic Ransomware Simulation Detection

index=main sourcetype="WinEventLog:Security" EventCode=4688
| search "SOC-Ransomware-Lab"
| table _time host EventCode Message
| sort - _time


## 3. Ransomware Keyword Detection

index=main EventCode=4688
| search "RANSOMWARE"
| table _time host EventCode Message
| sort - _time


4. Locked Extension Search

index=main EventCode=4688
| search "locked"
| table _time host EventCode Message
| sort - _time


5. Investigation Query

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


6. Timeline Investigation

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Account Name:\s+(?<user>[^\r\n]+)"
| rex field=Message "New Process Name:\s+(?<process_name>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| search user="ayush"
| table _time host user process_name command_line
| sort _time


7. Correlation Query

index=main sourcetype="WinEventLog:Security"
(EventCode=4624 OR EventCode=4672 OR EventCode=4688)
| eval event_type=case(
    EventCode=4624,"Successful Logon",
    EventCode=4672,"Special Privileges Assigned",
    EventCode=4688,"Process Creation"
)
| stats count values(event_type) as event_types
    min(_time) as first_seen
    max(_time) as last_seen
    by host
| where count >= 2
| convert ctime(first_seen) ctime(last_seen)
| table host event_types count first_seen last_seen



Dashboard Queries


Panel 1 – Total Ransomware Simulation Events

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| search command_line="*SOC-Ransomware-Lab*"
    OR command_line="*RANSOMWARE*"
    OR command_line="*.locked*"
| stats count


Panel 2 – Users Associated

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Account Name:\s+(?<user>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| search command_line="*SOC-Ransomware-Lab*"
    OR command_line="*RANSOMWARE*"
    OR command_line="*.locked*"
| stats count by user
| sort - count


Panel 3 – Activity Timeline

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| search command_line="*SOC-Ransomware-Lab*"
    OR command_line="*RANSOMWARE*"
    OR command_line="*.locked*"
| timechart span=1m count


Panel 4 – Suspicious Process and Parent

index=main sourcetype="WinEventLog:Security" EventCode=4688
| rex field=Message "New Process Name:\s+(?<process_name>[^\r\n]+)"
| rex field=Message "Creator Process Name:\s+(?<parent_process>[^\r\n]+)"
| rex field=Message "Process Command Line:\s+(?<command_line>[^\r\n]+)"
| search command_line="*SOC-Ransomware-Lab*"
    OR command_line="*RANSOMWARE*"
    OR command_line="*.locked*"
| stats count by process_name parent_process
| sort - count


Panel 5 – Command Lines

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