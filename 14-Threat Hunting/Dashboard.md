# Threat Hunting Dashboard

## Dashboard Name

Lab 14 - Threat Hunting Dashboard

## Panels

### ## Panel 1 — Threat Hunting Events by Type

Visualization:

Column Chart

index=main (EventCode=4624 OR EventCode=4625 OR EventCode=4688)
| eval Event_Type=case(
    EventCode=4625,"Failed Authentication",
    EventCode=4624,"Successful Authentication",
    EventCode=4688,"Process Creation"
)
| stats count by Event_Type
| sort - count


## Panel 2 — PowerShell Activity Timeline

Visualization:

Line Chart

index=main EventCode=4688
| where like(lower(New_Process_Name),"%powershell.exe%")
    OR like(lower(Process_Command_Line),"%powershell%")
| timechart span=1m count
## Panel 3 — Windows Discovery Commands

Visualization:

Bar Chart

index=main EventCode=4688
| where like(lower(Process_Command_Line),"%whoami%")
    OR like(lower(Process_Command_Line),"%systeminfo%")
    OR like(lower(Process_Command_Line),"%ipconfig%")
    OR like(lower(Process_Command_Line),"%arp -a%")
    OR like(lower(Process_Command_Line),"%route print%")
    OR like(lower(Process_Command_Line),"%tasklist%")
| eval Discovery_Type=case(
    like(lower(Process_Command_Line),"%whoami%"),"User Discovery",
    like(lower(Process_Command_Line),"%systeminfo%"),"System Discovery",
    like(lower(Process_Command_Line),"%ipconfig%"),"Network Discovery",
    like(lower(Process_Command_Line),"%arp -a%"),"Network Discovery",
    like(lower(Process_Command_Line),"%route print%"),"Network Discovery",
    like(lower(Process_Command_Line),"%tasklist%"),"Process Discovery"
)
| stats count by Discovery_Type
| sort - count
## Panel 4 — Suspicious Process Chain

Visualization:

Table

index=main EventCode=4688
| search New_Process_Name="*powershell.exe*"
| table _time host Account_Name Creator_Process_Name New_Process_Name Process_Command_Line
| sort - _time
## Panel 5 — Authentication and Process Correlation

Visualization:

Table / Timeline

index=main (EventCode=4624 OR EventCode=4625 OR EventCode=4688)
| eval Event_Type=case(
    EventCode=4625,"Failed Login",
    EventCode=4624,"Successful Login",
    EventCode=4688,"Process Creation"
)
| table _time Event_Type host Account_Name Source_Network_Address New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
Dashboard Purpose

The dashboard provides a centralized view of:

Authentication activity
PowerShell execution
Discovery behavior
Process relationships
Endpoint activity timeline

## Archived dashboard review

The suspicious process panel includes ordinary Splunk forwarding activity. An event list does not establish an authentication-to-process chain; the displayed results include unrelated background telemetry.

Treat the panel counts as historical search results, not confirmed incidents. Any proposed changes require a new Splunk run and screenshot; the original image has been preserved.
