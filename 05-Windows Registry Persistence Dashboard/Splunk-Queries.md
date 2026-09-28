# Splunk Queries

## Process Creation

```spl
index=main EventCode=4688
| search New_Process_Name="*reg.exe"
| table _time New_Process_Name Process_Command_Line Creator_Process_Name
```

---

## Registry Value Modified

```spl
index=main EventCode=4657
| table _time ComputerName ObjectName ObjectValueName user
```

---

## Registry Object Access

```spl
index=main EventCode=4663
| table _time ObjectName AccessMask ProcessName user
```

---

## Timeline

```spl
index=main (EventCode=4657 OR EventCode=4663 OR EventCode=4688)
| timechart span=5m count by EventCode
```