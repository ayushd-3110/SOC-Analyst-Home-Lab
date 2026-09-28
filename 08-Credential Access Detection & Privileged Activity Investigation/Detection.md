# Detection

## Detection Objective

Detect potential credential-access activity by identifying suspicious
Windows process creation and correlating it with authentication and
privilege-related events.

---

## Primary Detection Event

Event ID:

    4688

Description:

    A new process has been created.

The lab generated:

    cmd /c echo mimikatz credential access simulation

---

## Supporting Events

| Event ID | Description | Investigation Value |
|---|---|---|
| 4624 | Successful Logon | Establishes authentication |
| 4648 | Explicit Credentials | Indicates explicit credential usage |
| 4672 | Special Privileges | Identifies privileged sessions |
| 4688 | Process Creation | Identifies executed commands |

---

## Basic Detection

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4688
| search "mimikatz"
| table _time host EventCode Message
| sort - _time