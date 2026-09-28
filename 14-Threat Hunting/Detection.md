# Detection

## Detection vs Threat Hunting

This lab primarily demonstrates threat hunting rather than traditional alert-based detection.

The analyst searches existing telemetry for suspicious behavior.

---

## PowerShell Hunt

```spl
index=main EventCode=4688
| where like(lower(New_Process_Name),"%powershell.exe%")
    OR like(lower(Process_Command_Line),"%powershell%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time



Discovery Hunt
index=main EventCode=4688
| where like(lower(Process_Command_Line),"%whoami%")
    OR like(lower(Process_Command_Line),"%systeminfo%")
    OR like(lower(Process_Command_Line),"%ipconfig%")
    OR like(lower(Process_Command_Line),"%arp -a%")
    OR like(lower(Process_Command_Line),"%route print%")
    OR like(lower(Process_Command_Line),"%tasklist%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time



Process Chain Hunt
index=main EventCode=4688
| search New_Process_Name="*powershell.exe*"
| table _time host Account_Name Creator_Process_Name New_Process_Name Process_Command_Line
| sort _time