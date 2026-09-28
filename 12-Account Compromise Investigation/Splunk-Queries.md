Detection
Detection 1 — Multiple Failed Logins
index=main EventCode=4625
| stats count as Failed_Logins
        values(Account_Name) as Accounts
        values(Source_Network_Address) as Source_IPs
        values(host) as Hosts
| where Failed_Logins >= 3
Purpose

Detect repeated failed authentication attempts.

Detection 2 — Failed Logins by Source
index=main EventCode=4625
| stats count as Failed_Logins by Account_Name Source_Network_Address
| where Failed_Logins >= 3
| sort - Failed_Logins
Purpose

Identify the account and source responsible for repeated failures.

Detection 3 — Successful Authentication
index=main EventCode=4624
| table _time host Account_Name Source_Network_Address Logon_Type Authentication_Package
| sort - _time
Detection 4 — Privileged Activity
index=main EventCode=4672
| table _time host Account_Name Privilege_List
| sort - _time
Detection 5 — Process Creation
index=main EventCode=4688
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort - _time
Account Compromise Correlation

This is the main correlation query for the lab:

index=main (EventCode=4625 OR EventCode=4624 OR EventCode=4672 OR EventCode=4688)
| eval Event_Type=case(
    EventCode=4625,"Failed Login",
    EventCode=4624,"Successful Login",
    EventCode=4672,"Special Privileges",
    EventCode=4688,"Process Creation"
)
| table _time EventCode Event_Type host Account_Name Source_Network_Address Logon_Type New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time

Expected investigation sequence:

4625 → 4625 → 4625 → 4624 → 4672/4688

Only report the sequence that is actually present in your Splunk evidence.