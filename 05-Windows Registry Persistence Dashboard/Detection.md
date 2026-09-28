# Detection

## Data Source

Windows Security Logs

---

## Event IDs

4688 — Process Creation

4663 — Registry Object Access

4657 — Registry Value Modified

---

## Detection Logic

Process Creation

↓

Registry Access

↓

Registry Modification

---

## Detection Workflow

reg.exe

↓

Registry Key Access

↓

Registry Value Modified

↓

Persistence Established