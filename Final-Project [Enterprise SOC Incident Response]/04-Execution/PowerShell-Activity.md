# PowerShell Activity

## Process Creation

```spl
index=main EventCode=4688
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort - _time
```

## PowerShell Detection

```spl
index=main EventCode=4688
| where like(lower(New_Process_Name),"%powershell.exe%")
    OR like(lower(Process_Command_Line),"%powershell%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort - _time
```

## Process Chain

```spl
index=main EventCode=4688
| search New_Process_Name="*powershell.exe*"
| table _time host Account_Name Creator_Process_Name New_Process_Name Process_Command_Line
| sort _time
```

## What I Look For

I check:

1. Which user launched PowerShell?
2. What process launched it?
3. What command line was used?
4. When did it run?
5. What happened before and after it?
