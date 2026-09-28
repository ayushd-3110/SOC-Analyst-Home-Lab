# Persistence Detection

## Scheduled Task Creation

```spl
index=main EventCode=4698
| table _time host Account_Name Task_Name Task_Content
| sort - _time
```

If the field names are not extracted, use:

```spl
index=main EventCode=4698
| table _time host Account_Name *
| sort - _time
```

## Process-Based Hunt

```spl
index=main EventCode=4688
| where like(lower(Process_Command_Line),"%schtasks%")
    OR like(lower(Process_Command_Line),"%persistence-test%")
    OR like(lower(Process_Command_Line),"%soc-enterprise-persistence%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort - _time
```

## Investigation Note

If Event 4698 is missing, do not recreate the task repeatedly just to force an event. First verify that the required Task Scheduler Operational log is being collected.

## Conclusion

The scheduled task demonstrates how persistence can appear in Windows telemetry. In this lab it was intentionally created and then removed.
