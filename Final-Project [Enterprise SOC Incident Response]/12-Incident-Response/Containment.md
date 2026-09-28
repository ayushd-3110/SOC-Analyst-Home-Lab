# Containment

## Lab Containment Actions

The controlled activity was contained by:

1. Stopping the simulation.
2. Removing the scheduled-task persistence artifact.
3. Removing temporary test files.
4. Keeping the investigation evidence and screenshots.
5. Verifying the endpoint remained stable.

## Scheduled Task Removal

```cmd
schtasks /delete /tn "SOC-Enterprise-Persistence-Test" /f
```

## Production Example

In a real incident, containment could include:

- isolating the endpoint
- disabling a compromised account
- blocking malicious infrastructure
- stopping malicious processes
- preserving forensic evidence

The exact action would depend on evidence and organizational procedure.
