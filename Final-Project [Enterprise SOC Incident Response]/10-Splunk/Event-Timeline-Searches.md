# Event Timeline Searches

Run each SPL block separately. Confirm field names and the time range for your workspace.

## Authentication → execution

```spl
index=main (EventCode=4625 OR EventCode=4624 OR EventCode=4688)
| eval Event_Type=case(
    EventCode=4625,"Failed Authentication",
    EventCode=4624,"Successful Authentication",
    EventCode=4688,"Process Creation"
)
| table _time EventCode Event_Type host Account_Name Source_Network_Address New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Full incident event stream

```spl
index=main (EventCode=4624 OR EventCode=4625 OR EventCode=4672 OR EventCode=4688 OR EventCode=4698)
| eval Event_Type=case(
    EventCode=4624,"Successful Authentication",
    EventCode=4625,"Failed Authentication",
    EventCode=4672,"Special Privileges",
    EventCode=4688,"Process Creation",
    EventCode=4698,"Scheduled Task Created",
    true(),"Other"
)
| table _time EventCode Event_Type host Account_Name Source_Network_Address Logon_Type New_Process_Name Creator_Process_Name Process_Command_Line Task_Name
| sort _time
```
