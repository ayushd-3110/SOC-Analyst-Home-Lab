# Lateral Movement Investigation

## Goal

Investigate SMB activity between the two controlled lab systems.

## Verify SMB

From Kali:

```bash
nmap -Pn -p 445 192.168.234.130
```

Then:

```bash
smbclient -L //192.168.234.130 -U ayush
```

## Authentication Investigation

```spl
index=main (EventCode=4624 OR EventCode=4625)
| table _time EventCode host Account_Name Source_Network_Address Logon_Type Authentication_Package
| sort - _time
```

## Process Hunt

```spl
index=main EventCode=4688
| where like(lower(Process_Command_Line),"%smb%")
    OR like(lower(Process_Command_Line),"%net use%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Analyst Note

Do not label activity as confirmed lateral movement only because SMB was used. Correlate the source, destination, account, authentication event, and subsequent activity.

This lab uses the user's own systems.
