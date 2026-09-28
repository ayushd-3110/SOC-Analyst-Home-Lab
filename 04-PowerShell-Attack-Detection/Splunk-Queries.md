# Splunk Queries

---

## Verify PowerShell Events

### Script Block Logging

```spl
index=main source="WinEventLog:Microsoft-Windows-PowerShell/Operational" EventCode=4104
```

---

### Process Creation

```spl
index=main EventCode=4688
```

---

## PowerShell Executions

```spl
index=main EventCode=4104
| table _time host ScriptBlockText
```

---

## Execution Policy Bypass

```spl
index=main EventCode=4104
"ExecutionPolicy"
```

---

## Encoded Commands

```spl
index=main EventCode=4104
("-enc" OR "-EncodedCommand")
```

---

## Hidden PowerShell

```spl
index=main EventCode=4104
"Hidden"
```

---

## Invoke-WebRequest Detection

```spl
index=main EventCode=4104
"Invoke-WebRequest"
```

---

## DownloadString Detection

```spl
index=main EventCode=4104
"DownloadString"
```

---

## WebClient Detection

```spl
index=main EventCode=4104
"Net.WebClient"
```

---

## Invoke-Expression Detection

```spl
index=main EventCode=4104
"IEX"
```

---

## Base64 Activity

```spl
index=main EventCode=4104
"FromBase64String"
```

---

## Top PowerShell Commands

```spl
index=main EventCode=4104
| top limit=10 ScriptBlockText
```

---

## Timeline

```spl
index=main EventCode=4104
| timechart span=1h count
```

---

## PowerShell Activity by Host

```spl
index=main EventCode=4104
| stats count by host
```

---

## Raw Investigation

```spl
index=main EventCode=4104
| table _time host ScriptBlockText
```

---

## Process Creation

```spl
index=main EventCode=4688
| table _time host ProcessName ParentProcessName
```

---

## Correlate Script Execution with Process Creation

```spl
index=main (EventCode=4104 OR EventCode=4688)
| stats values(EventCode) values(ProcessName) values(ScriptBlockText) by host
```