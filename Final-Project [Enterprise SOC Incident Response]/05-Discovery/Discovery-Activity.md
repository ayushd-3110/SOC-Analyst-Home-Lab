# Discovery Activity

## Controlled Commands

```cmd
whoami
net user
net user ayush
hostname
systeminfo
wmic os get Caption,Version,BuildNumber
ipconfig /all
arp -a
route print
tasklist
tasklist /svc
powershell -NoProfile -Command "Get-Process"
powershell -NoProfile -Command "Get-Service"
powershell -NoProfile -Command "Get-ComputerInfo | Select-Object WindowsProductName,WindowsVersion,OsArchitecture"
```

`wmic` may not be available on every Windows installation.

## What the Analyst Is Looking For

The commands represent common discovery categories:

- user discovery
- account discovery
- system discovery
- network discovery
- process discovery

The presence of a discovery command is a signal for investigation, not automatic proof of malicious intent.
