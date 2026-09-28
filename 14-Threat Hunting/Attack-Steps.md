# Attack Simulation – Threat Hunting

## Important Note

This is a controlled simulation.

No real malware or destructive attack was performed.

The purpose is to generate endpoint telemetry for threat-hunting practice.

---

## Step 1 – Host Information

```cmd
hostname
whoami
ipconfig
date /t

Step 2 – User Discovery
whoami
net user
net user ayush


Step 3 – System Discovery
hostname
systeminfo

Step 4 – Network Discovery
ipconfig /all
arp -a
route print


Step 5 – Process Discovery
tasklist
tasklist /svc

Step 6 – PowerShell Activity
powershell -NoProfile -Command "Get-Process"
powershell -NoProfile -Command "Get-Service"
powershell -NoProfile -Command "Get-ComputerInfo | Select-Object WindowsProductName,WindowsVersion,OsArchitecture"
Step 7 – Suspicious Process Chain Simulation
cmd /c powershell -NoProfile -Command "Write-Output 'SOC Threat Hunting Simulation'"
Expected process relationship:

cmd.exe
   └── powershell.exe
Step 8 – Controlled File Discovery
dir C:\Users\ayush\Desktop
dir C:\Users\ayush\Documents
dir C:\SOC-Malware-Lab
Step 9 – Controlled Network Activity
curl http://192.168.234.130/
