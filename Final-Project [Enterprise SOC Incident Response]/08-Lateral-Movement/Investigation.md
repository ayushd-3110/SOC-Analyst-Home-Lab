# Lateral Movement Investigation

## Investigation Questions

1. Which system initiated the SMB connection?
2. Which account was used?
3. Was authentication successful?
4. Were there failed attempts first?
5. Did suspicious process activity follow the authentication?
6. Was the activity expected in this lab?

## Correlation

```spl
index=main (EventCode=4624 OR EventCode=4625 OR EventCode=4688)
| eval Event_Type=case(
    EventCode=4625,"Failed Authentication",
    EventCode=4624,"Successful Authentication",
    EventCode=4688,"Process Creation"
)
| table _time EventCode Event_Type host Account_Name Source_Network_Address Logon_Type New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Finding

The SMB activity is a controlled lab action. The investigation demonstrates how a SOC analyst would validate a potential lateral-movement signal instead of relying on one event.
