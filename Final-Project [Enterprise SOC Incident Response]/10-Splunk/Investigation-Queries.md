# Investigation Queries

Run each SPL block separately. Confirm field names and the time range for your workspace.

## Failed authentication

```spl
index=main EventCode=4625
| stats count as Failed_Logins values(Account_Name) as Accounts values(Source_Network_Address) as Source_IPs by host
| sort - Failed_Logins
```

## Successful authentication

```spl
index=main EventCode=4624
| table _time host Account_Name Source_Network_Address Logon_Type Authentication_Package
| sort - _time
```

## PowerShell

```spl
index=main EventCode=4688
| where like(lower(New_Process_Name),"%powershell.exe%")
    OR like(lower(Process_Command_Line),"%powershell%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Discovery

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
