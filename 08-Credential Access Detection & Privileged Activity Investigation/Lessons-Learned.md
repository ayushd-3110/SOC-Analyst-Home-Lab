# Lessons Learned

## 1. One Event Is Not Always Enough

Event ID 4688 is useful for process creation, but investigating it alone
may not provide enough context.

Correlating 4624, 4648, 4672 and 4688 provides a much better timeline.

---

## 2. Privileged Accounts Require Extra Attention

Event ID 4672 showed that special privileges were assigned to the session.

Privileges such as SeDebugPrivilege can be particularly important during
credential-access investigations.

---

## 3. Command-Line Monitoring Is Valuable

The process command line provided the strongest detection indicator:

    cmd /c echo mimikatz credential access simulation

Command-line telemetry can reveal suspicious intent even when the executable
itself appears legitimate.

---

## 4. Keyword Detection Is Not Proof of Compromise

The word "mimikatz" generated an alert, but it did not prove that Mimikatz
was executed.

The analyst must investigate the complete event context.

---

## 5. Correlation Improves Detection

A stronger SOC detection can combine:

    Authentication
    +
    Privilege Assignment
    +
    Explicit Credentials
    +
    Process Creation
    +
    Suspicious Command Line

---

## 6. Lab Safety

The simulation demonstrated credential-access detection without actually
dumping credentials.

This is useful for practicing SOC investigation techniques safely.