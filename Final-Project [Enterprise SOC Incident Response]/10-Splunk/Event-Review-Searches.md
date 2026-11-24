# Event Review Searches

Run each SPL block separately. Confirm field names and the time range for your workspace.

## Authentication anomaly

```spl
index=main EventCode=4625
| table _time host Account_Name Source_Network_Address Logon_Type Authentication_Package
| sort - _time
```

## Process creation

```spl
index=main EventCode=4688
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort - _time
```

## Scheduled task creation

```spl
index=main EventCode=4698
| table _time host Account_Name Task_Name Task_Content
| sort - _time
```

## PowerShell process activity

```spl
index=main EventCode=4688
| where like(lower(New_Process_Name),"%powershell.exe%")
    OR like(lower(Process_Command_Line),"%powershell%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort - _time
```
