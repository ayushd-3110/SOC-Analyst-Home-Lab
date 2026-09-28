# Credential Access Simulation

## Safety First

This phase does **not** extract credentials and does not run Mimikatz.

The behavior is represented using harmless command execution so that the SOC analyst can practice detection and investigation.

## Simulation

```cmd
cmd /c echo SOC Enterprise Credential Access Simulation
cmd /c echo Simulated credential access investigation activity
```

## What I Investigate

I search for:

- credential-related keywords
- `mimikatz`
- `lsass`
- unusual process creation
- privileged activity

## Key Point

A keyword match such as `mimikatz` is an investigation signal. It should be validated using process path, command line, parent process, user, time, and surrounding events.
