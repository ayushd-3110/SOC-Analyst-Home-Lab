# Splunk Queries

## Verify Authentication Events

### Failed Logins

```spl
index=main EventCode=4625
```

### Successful Logins

```spl
index=main EventCode=4624
```

---

## Total Failed Logins

```spl
index=main EventCode=4625
| stats count 
```

---

## Total Successful Logins

```spl
index=main EventCode=4624
| stats count
```

---

## Failed Logins by User

```spl
index=main EventCode=4625
| stats count by Account_Name
```

---

## Successful Logins by User

```spl
index=main EventCode=4624
| stats count by Account_Name
```

---

## Authentication Timeline

```spl
index=main (EventCode=4624 OR EventCode=4625)
| timechart span=1m count by EventCode
```

---

## Event Distribution

```spl
index=main (EventCode=4624 OR EventCode=4625)
| stats count by EventCode
```

---

## Failed Logins by Computer

```spl
index=main EventCode=4625
| stats count by ComputerName
```

---

## Authentication Events Table

```spl
index=main (EventCode=4624 OR EventCode=4625)
| table _time EventCode ComputerName Message
```

```