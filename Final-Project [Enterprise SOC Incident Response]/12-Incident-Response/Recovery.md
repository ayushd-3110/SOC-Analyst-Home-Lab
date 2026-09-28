# Recovery

## Lab Recovery Checklist

- Scheduled task removed
- Temporary simulation artifacts removed
- Windows endpoint still operational
- Splunk logging still available
- No real malware executed
- No real credentials extracted
- Final evidence preserved

## Validation

The endpoint should be checked for:

- normal login
- normal process activity
- expected network connectivity
- working log forwarding
- absence of the test persistence artifact

## Production Example

Recovery could include restoring services, resetting credentials, reimaging a host when required, monitoring the endpoint closely, and confirming business functionality.
