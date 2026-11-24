# Dashboard Queries

Run each SPL block separately. Confirm field names and the time range for your workspace.

## Panel 1 – Authentication events

```spl
index=main (EventCode=4624 OR EventCode=4625)
| timechart count by EventCode
```

## Panel 2 – Process activity

```spl
index=main EventCode=4688
| timechart count
```

## Panel 3 – PowerShell activity

```spl
index=main EventCode=4688
| where like(lower(New_Process_Name),"%powershell.exe%")
    OR like(lower(Process_Command_Line),"%powershell%")
| timechart count
```

## Panel 4 – Scheduled task creation

```spl
index=main EventCode=4698
| timechart count
```

## Panel 5 – Incident timeline

```spl
index=main (EventCode=4624 OR EventCode=4625 OR EventCode=4672 OR EventCode=4688 OR EventCode=4698)
| eval Event_Type=case(
    EventCode=4624,"Successful Authentication",
    EventCode=4625,"Failed Authentication",
    EventCode=4672,"Special Privileges",
    EventCode=4688,"Process Creation",
    EventCode=4698,"Scheduled Task"
)
| timechart count by Event_Type
```
