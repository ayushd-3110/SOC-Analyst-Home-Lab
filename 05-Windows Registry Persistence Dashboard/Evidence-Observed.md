# Screenshot Evidence Review

The screenshots show a Registry Run-key persistence exercise. The verification screenshot displays:

`HKCU\Software\Microsoft\Windows\CurrentVersion\Run`

and a lab entry named **Lab5Persistence** with the value:

`C:\Temp\lab5.bat`

The screenshots also show registry logging verification, creation of a test file, Run-key creation, verification, and a **Windows Registry Persistence Detection** dashboard.

## Evidence Boundary
The persistence mechanism shown is a controlled lab artifact. The screenshot does not establish persistence by an unknown attacker.

## Additional review findings

The dashboard's object name, value name and user columns are blank; broad object-access and process creation records do not independently prove changes to the particular value. Execution at the next logon has not been demonstrated.

**Disposition:** Controlled registry artifact observed; attacker persistence not established.
