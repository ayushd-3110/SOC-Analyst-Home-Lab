# Discovery Threat Hunt

## Hunting Question

> After authentication and process execution, did the endpoint perform account, system, network, or process discovery?

## SPL

```spl
index=main EventCode=4688
| where like(lower(Process_Command_Line),"%whoami%")
    OR like(lower(Process_Command_Line),"%net user%")
    OR like(lower(Process_Command_Line),"%systeminfo%")
    OR like(lower(Process_Command_Line),"%ipconfig%")
    OR like(lower(Process_Command_Line),"%arp -a%")
    OR like(lower(Process_Command_Line),"%route print%")
    OR like(lower(Process_Command_Line),"%tasklist%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Analyst Interpretation

The important part is the sequence.

Discovery occurring after authentication and process execution is more useful for investigation than looking at a single command in isolation.
