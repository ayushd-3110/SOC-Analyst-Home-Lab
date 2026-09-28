# Execution Simulation

After the authentication investigation, controlled process activity was generated on the Windows endpoint.

## Commands

```cmd
cmd /c echo SOC Enterprise Incident Simulation
whoami
hostname
powershell -NoProfile -Command "Write-Output 'SOC Enterprise Incident PowerShell Simulation'"
powershell -NoProfile -Command "Get-Process"
powershell -NoProfile -Command "Get-Service"
```

## Why These Commands?

They create normal-looking endpoint telemetry that can be investigated for:

- command execution
- PowerShell execution
- process creation
- parent/child relationships

No malicious payload is executed.
