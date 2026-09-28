# Impact Simulation – Harmless Ransomware Behavior

## Goal

Demonstrate how mass file creation and renaming could look in endpoint telemetry without encrypting or damaging real data.

## Create Test Files

```cmd
mkdir C:\SOC-Final-Project\Ransomware-Test
cd /d C:\SOC-Final-Project\Ransomware-Test

for /L %i in (1,1,20) do echo SOC Ransomware Test File %i > file%i.txt
for /L %i in (1,1,20) do echo SIMULATED RANSOMWARE ACTIVITY >> file%i.txt
for /L %i in (1,1,20) do ren file%i.txt file%i.locked
```

## Safety

The files are disposable lab files. No encryption algorithm is used.

## SOC Relevance

A real ransomware investigation would look for unusual file-write/rename volume, process context, user, host, and timing. This lab only simulates the visible pattern.
