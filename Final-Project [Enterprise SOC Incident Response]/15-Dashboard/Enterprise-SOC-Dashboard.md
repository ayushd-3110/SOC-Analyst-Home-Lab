# Enterprise SOC Dashboard

## Dashboard Name

**Enterprise SOC Incident Response Dashboard**

## Purpose

The dashboard provides a single place to review the main incident signals.

## Recommended Panels

### 1. Authentication Activity

```spl
index=main (EventCode=4624 OR EventCode=4625)
| timechart count by EventCode
```

### 2. Process Creation Timeline

```spl
index=main EventCode=4688
| timechart count
```

### 3. PowerShell Activity

```spl
index=main EventCode=4688
| where like(lower(New_Process_Name),"%powershell.exe%")
    OR like(lower(Process_Command_Line),"%powershell%")
| timechart count
```

### 4. Persistence Activity

```spl
index=main EventCode=4698
| timechart count
```

### 5. Incident Timeline

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

## Analyst Workflow

Start with the authentication panel, move to process activity, inspect PowerShell, review persistence, and then use the timeline to understand the sequence.
