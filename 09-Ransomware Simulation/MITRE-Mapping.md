# MITRE ATT&CK Mapping

## Overview

The ransomware simulation was mapped to relevant MITRE ATT&CK behaviors.

| MITRE ATT&CK | Technique | Relevance |
|---|---|---|
| T1059.003 | Windows Command Shell | CMD was used to execute the simulation commands |
| T1486 | Data Encrypted for Impact | Ransomware behavior being simulated; no real encryption was performed |


---

## Primary Technique

### T1059.003 – Windows Command Shell

The simulation used Windows CMD to execute file creation, modification, and renaming commands.

Observed process:

C:\Windows\System32\cmd.exe

---

## Ransomware Behavior

### T1486 – Data Encrypted for Impact

The lab was designed to simulate ransomware-like impact behavior.

However, no actual encryption was performed.

The lab simulated:

- Mass file modification
- File renaming
- Suspicious extension changes
- Ransom-note creation

Therefore, T1486 is included as the simulated behavior being modeled, not as proof of actual encryption.

---

## ATT&CK Assessment

The strongest directly observed technique in this lab is:

T1059.003 – Windows Command Shell

The ransomware impact behavior was simulated safely for detection and investigation training.