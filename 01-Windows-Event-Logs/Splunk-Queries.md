# Splunk authentication searches

These historical search examples use the documented index `main`. Validate the index and sourcetype locally before execution.

## Event review

```spl
index=main (EventCode=4624 OR EventCode=4625)
| stats count by EventCode
```

## Timeline

```spl
index=main (EventCode=4624 OR EventCode=4625)
| timechart count by EventCode
```

## Account attribution

The archived account chart groups a multivalued Account_Name field and can count both the subject and target account. Validate the target account against raw events before reporting per-user totals. Separate machine/service accounts from human logons; the revised results are not yet available.
