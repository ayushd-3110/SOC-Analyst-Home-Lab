# Persistence Activity

## Goal

Demonstrate how a SOC analyst can detect a scheduled-task persistence mechanism without creating a harmful task.

## Create a Harmless Script

```cmd
mkdir C:\SOC-Final-Project
echo @echo off > C:\SOC-Final-Project\persistence-test.cmd
echo echo SOC Enterprise Persistence Simulation >> C:\SOC-Final-Project\persistence-test.cmd
echo echo Persistence test executed ^> C:\SOC-Final-Project\persistence-test.log >> C:\SOC-Final-Project\persistence-test.cmd
```

## Create the Scheduled Task

```cmd
schtasks /create /tn "SOC-Enterprise-Persistence-Test" /tr "cmd.exe /c C:\SOC-Final-Project\persistence-test.cmd" /sc onlogon /f
```

## Verify

```cmd
schtasks /query /tn "SOC-Enterprise-Persistence-Test" /fo LIST /v
```

## Remove It After Investigation

```cmd
schtasks /delete /tn "SOC-Enterprise-Persistence-Test" /f
```

## Important

This task is only a lab artifact. It should be removed after the investigation.
