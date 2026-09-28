# Credential Access Detection

## Simulation Search

```spl
index=main EventCode=4688
| search Process_Command_Line="*Credential Access Simulation*"
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Credential-Access Keyword Hunt

```spl
index=main EventCode=4688
| where like(lower(Process_Command_Line),"%credential%")
    OR like(lower(Process_Command_Line),"%mimikatz%")
    OR like(lower(Process_Command_Line),"%lsass%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Privileged Activity

```spl
index=main EventCode=4672
| table _time host Account_Name Privilege_List
| sort - _time
```

## Important Interpretation Rule

Do not automatically attribute every 4672 event to the simulated user. Check the actual `Account_Name` and event context first.

## Conclusion

The lab demonstrates credential-access detection concepts without performing real credential extraction.
