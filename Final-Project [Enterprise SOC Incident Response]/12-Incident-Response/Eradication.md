# Eradication

## Lab Eradication

The lab artifacts were removed:

- scheduled task
- simulation files
- temporary ransomware test files
- other temporary artifacts created specifically for the exercise

## Verification

Check that the scheduled task no longer exists:

```cmd
schtasks /query /tn "SOC-Enterprise-Persistence-Test"
```

A failure indicating that the task is not found is expected after removal.

## Production Example

A real eradication phase would include identifying and removing the actual persistence or malware mechanism, validating the endpoint, and documenting every action.
