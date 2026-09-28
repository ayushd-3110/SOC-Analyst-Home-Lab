# Authentication Activity

## Failed Authentication

```spl
index=main EventCode=4625
| table _time host Account_Name Source_Network_Address Logon_Type Authentication_Package
| sort - _time
```

## Successful Authentication

```spl
index=main EventCode=4624
| table _time host Account_Name Source_Network_Address Logon_Type Authentication_Package
| sort - _time
```

## Combined Timeline

```spl
index=main (EventCode=4625 OR EventCode=4624)
| eval Event_Type=case(
    EventCode=4625,"Failed Authentication",
    EventCode=4624,"Successful Authentication"
)
| table _time EventCode Event_Type host Account_Name Source_Network_Address Logon_Type Authentication_Package
| sort _time
```

## Correlation

```spl
index=main (EventCode=4625 OR EventCode=4624)
| eval Event_Type=case(
    EventCode=4625,"Failed Login",
    EventCode=4624,"Successful Login"
)
| stats count as Attempts
        values(Event_Type) as Authentication_Events
        values(Source_Network_Address) as Source_IP
        earliest(_time) as First_Seen
        latest(_time) as Last_Seen
        by Account_Name host
| convert ctime(First_Seen) ctime(Last_Seen)
| sort - Last_Seen
```

## Analyst Interpretation

The useful question is not simply “did a login happen?”

The analyst asks:

- How many failures occurred?
- Which account was targeted?
- Which source generated them?
- Was a success recorded?
- What happened immediately afterward?

## Supplied Screenshot Evidence

The current repository contains four final-project screenshots:

1. `01-Final-Project-Environment.png` – hostname `DESKTOP-NH5RCBO`, user `desktop-nh5rcbo\ayush`, IPv4 `192.168.234.130`, gateway `192.168.234.2`.
2. `02-logging and audit verification.png` – Logon auditing is **Success and Failure**; Process Creation auditing is **Success**; `Sysmon64` is **RUNNING**. The displayed `sc query SplunkForwarder` command returns service-not-found, so the screenshot does not prove that the Windows service named `SplunkForwarder` is installed.
3. `03-splunk telementry verification.png` – Splunk search `index=main EventCode=4688` returned **3,429 events** for the displayed 26–27 Sep 2026 window. The visible rows show `SplunkForwarder` process activity on `DESKTOP-NH5RCBO`.
4. `04-Initial Access Failed authentication .png` – the displayed combined 4624/4625 search returned **124 events**, but the visible rows are **SYSTEM / computer-account logon type 5** records with no source network address. This screenshot does not prove the intended `ayush` failed-authentication scenario.

## Evidence Boundary
Only these four screenshots are currently present in the final-project screenshot folder. Later project phases should not be described as screenshot-verified unless their screenshots are actually added. The screenshot folder has not been changed.
