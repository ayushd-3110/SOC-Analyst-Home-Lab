# Indicators of Compromise

## Processes

- reg.exe
- cmd.exe

---

## Registry Path

HKCU\Software\Microsoft\Windows\CurrentVersion\Run

---

## Registry Value

WindowsUpdate

---

## Windows Event IDs

- 4688
- 4663
- 4657

---

## Detection Keywords

- reg add
- CurrentVersion\Run
- WindowsUpdate

## Screenshot-Verified Registry Artifact

Run key: `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`

Lab value: `LabSPersistence` → `C:\Temp\lab5.bat`
