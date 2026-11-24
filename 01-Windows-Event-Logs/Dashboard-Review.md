# Archived dashboard review

I reviewed Windows Security events 4624 and 4625 in Splunk. The dashboard shows 85 successful and 3 failed logon records in the displayed window. At 16:00:32.888, a type 2 logon for LEO failed with status 0xC000006D and substatus 0xC000006A.

The per-user panel attributes the same three failures to LEO and the computer account. Its counts are not independent. Service and machine logons also affect the successful-logon total.

The dashboard image remains unchanged. Any proposed improvement needs validation in Splunk before it is presented as an updated result.
