# Incident Report

## Incident Name

Windows Registry Persistence

---

## Severity

Medium

---

## MITRE ATT&CK

T1547.001

---

## Summary

A registry Run Key was created using reg.exe to establish persistence.

---

## Evidence

- Event ID 4688
- Event ID 4663
- Event ID 4657

---

## Impact

The attacker can execute code automatically after user logon.

---

## Recommendations

- Remove unauthorized Run Keys
- Restrict registry modification privileges
- Monitor Event IDs 4688, 4663, and 4657
- Review startup registry locations regularly

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
