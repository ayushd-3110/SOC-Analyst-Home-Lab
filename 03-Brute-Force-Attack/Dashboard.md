Panel 1
Total Failed Logins

index=main EventCode=4625
| stats count
Visualization:  Single Value


Panel 2
Successful Logins

index=main EventCode=4624
| stats count
Visualization:  Single Value


Panel 3
Failed Logons by Target Account

```spl
index=main EventCode=4625
| eval TargetAccount=lower(trim(TargetUserName))
| eval TargetDomain=lower(trim(TargetDomainName))
| eval AccountGroup=case(isnull(TargetAccount) OR TargetAccount="" OR TargetAccount="-","(missing target account)",match(TargetAccount,"[$]$"),"(machine account)",isnotnull(TargetDomain) AND TargetDomain!="" AND TargetDomain!="-",TargetDomain."\\".TargetAccount,true(),TargetAccount)
| stats count AS FailedLogons BY AccountGroup
| sort 0 -FailedLogons
```
Visualization: Bar Chart

Use the same absolute time range and data scope as Panel 1. This query assumes the XML target fields TargetUserName and TargetDomainName are extracted. Validate those fields on raw event XML before interpreting the missing bucket. Never substitute the generic Account_Name field, which can contain both subject and target values.

Run this search and compare the result with Panel 1:

```spl
index=main EventCode=4625
| eval TargetAccount=lower(trim(TargetUserName))
| eval TargetDomain=lower(trim(TargetDomainName))
| eval AccountGroup=case(isnull(TargetAccount) OR TargetAccount="" OR TargetAccount="-","(missing target account)",match(TargetAccount,"[$]$"),"(machine account)",isnotnull(TargetDomain) AND TargetDomain!="" AND TargetDomain!="-",TargetDomain."\\".TargetAccount,true(),TargetAccount)
| stats count AS FailedLogons BY AccountGroup
| sort 0 -FailedLogons
| stats sum(FailedLogons) AS BreakdownTotal
```


Panel 4
Authentication Timeline

index=main (EventCode=4624 OR EventCode=4625)
| timechart span=1m count by EventCode

Visualization: Line Chart


Panel 5
Event Distribution

index=main (EventCode=4624 OR EventCode=4625)
| stats count by EventCode

Visualization :  Pie Chart


Panel 6
Target Computers

index=main EventCode=4625
| stats count by ComputerName
Visualization: Column Chart


Panel 7
Raw Authentication Logs

index=main (EventCode=4624 OR EventCode=4625)
| table _time EventCode ComputerName Message
Visualization:  Table

## Archived dashboard review

The displayed records do not establish that the same account and source succeeded after failures. The protocol and alert trigger are not independently established. The username panel includes missing and machine accounts and inconsistent capitalization; a revised panel is documented but has not been rerun.

Treat the panel counts as historical search results, not confirmed incidents. Any proposed changes require a new Splunk run and screenshot; the original image has been preserved.
