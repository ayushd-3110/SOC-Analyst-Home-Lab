# MITRE ATT&CK Mapping

## Primary Technique

### T1003 — OS Credential Dumping

Mimikatz is commonly associated with credential dumping techniques.

In this lab, T1003 is represented as a simulated detection scenario.

Important:

No actual credential dumping was performed.

---

## Supporting Technique

### T1059.003 — Windows Command Shell

The simulation used:

    cmd.exe

The command executed was:

    cmd /c echo mimikatz credential access simulation

This demonstrates how command-shell activity can provide telemetry for
credential-access detection.

---

## Detection Mapping

| Activity | MITRE ATT&CK |
|---|---|
| Mimikatz simulation | T1003 |
| cmd.exe execution | T1059.003 |
| Privileged logon | Supporting security telemetry |
| Process creation | Supporting security telemetry |
| Explicit credential use | Supporting authentication telemetry |

---

## SOC Perspective

The goal of MITRE mapping is not simply to label an event.

The analyst should connect:

    Technique
       ↓
    Windows Event
       ↓
    Process
       ↓
    User
       ↓
    Timeline
       ↓
    Investigation