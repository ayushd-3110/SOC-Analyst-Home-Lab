# Investigation

## Summary

A persistence technique was detected using Windows Registry Run Keys.

---

## Evidence

- Process Creation (4688)
- Registry Access (4663)
- Registry Value Modified (4657)

---

## Observed Process

reg.exe

---

## Modified Registry

HKCU\Software\Microsoft\Windows\CurrentVersion\Run

---

## Created Value

WindowsUpdate

---

## Impact

Persistence established after user logon.

---

## Conclusion

The attack successfully created a Registry Run Key. Windows Security Logs provided sufficient evidence to detect and investigate the persistence technique.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
