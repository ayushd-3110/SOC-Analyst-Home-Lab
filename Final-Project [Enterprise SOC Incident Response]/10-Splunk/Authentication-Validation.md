# Validate failed logons followed by a successful logon

This candidate detection surfaces a successful logon preceded by at least five failures within five minutes for the same target host, domain/account and source IP. Run it as a historical search first and record the exact search window and time zone. Use an interval wide enough to include the full preceding five minutes. The query groups failures regardless of logon type and displays the success logon type for investigation.

## 1. Verify field extraction and inspect the matching events

Keep EventCode visible and map TargetUserName, TargetDomainName and IpAddress to fields verified against the Windows event XML. Compare the normalized host with the raw event computer value and scope the search to the lab host. Review records without a source address separately. The correlation excludes them.

```spl
index=main EventCode IN (4624,4625)
| table _time EventCode host ComputerName TargetUserName TargetDomainName IpAddress Source_Network_Address Logon_Type LogonType
| sort 0 +_time
```

## 2. Validate with synthetic evidence

Run this query with the time picker set to Last 24 hours. Expected result is a single row for training/positive with PriorFailures=5. The four-failure control and the success from a different source IP should produce no match.

```spl
| makeresults count=12
| streamstats count AS Row
| eval _time=relative_time(now(),"-10m")+Row*10, TargetHost="training-ws", TargetIdentity=if(Row<=6,"training/positive","training/benign"), SourceIP=case(Row<=6,"192.0.2.10",Row<=11,"192.0.2.20",true(),"192.0.2.21"), EventCode=if(Row=6 OR Row=11 OR Row=12,"4624","4625"), LogonType=3
| eval EventCode=tostring(EventCode)
| sort 0 +_time
| streamstats time_window=5m current=f count(eval(EventCode="4625")) AS PriorFailures BY TargetHost TargetIdentity SourceIP
| where EventCode="4624" AND PriorFailures>=5
| table _time TargetHost TargetIdentity SourceIP Logon_Type LogonType EventCode PriorFailures
```

## 3. Run against the capstone telemetry

Select the actual incident window in Splunk. Keep the raw event review from step 1 beside the result to show the failed records as well as the success. If you get an empty result, check field extraction, the search window and whether the matching events were collected. Document the evidence gap if it remains.

```spl
index=main EventCode IN (4624,4625)
| eval TargetAccount=lower(trim(TargetUserName)), TargetDomain=lower(trim(TargetDomainName)), SourceIP=lower(trim(coalesce(IpAddress,Source_Network_Address))), TargetHost=lower(coalesce(ComputerName,host))
| eval SourceIP=replace(SourceIP,"^::ffff:","")
| where isnotnull(TargetAccount) AND TargetAccount!="" AND TargetAccount!="-" AND NOT match(TargetAccount,"[$]$")
    AND isnotnull(SourceIP) AND SourceIP!="" AND SourceIP!="-" AND SourceIP!="::1" AND SourceIP!="127.0.0.1"
| eval TargetDomain=if(isnull(TargetDomain) OR TargetDomain="" OR TargetDomain="-","(unknown domain)",TargetDomain)
| eval TargetIdentity=TargetDomain."/".TargetAccount
| eval EventCode=tostring(EventCode)
| sort 0 +_time
| streamstats time_window=5m current=f count(eval(EventCode="4625")) AS PriorFailures BY TargetHost TargetIdentity SourceIP
| where EventCode="4624" AND PriorFailures>=5
| table _time TargetHost TargetIdentity SourceIP Logon_Type LogonType EventCode PriorFailures
```

## 4. Record the validation

| Check | Expected | Actual |
| --- | --- | --- |
| Synthetic match | One success with five prior failures | Pending Splunk execution |
| Synthetic controls | No matches | Pending Splunk execution |
| Capstone telemetry | Review any hits against source event records | Pending Splunk execution |

Record the actual result and attach a redacted export or screenshot with a fixed time window. Review same-timestamp events in the raw records before inferring order.

Live validation was blocked by an expired license on the local Splunk instance at the time of the portfolio review. The expected outcomes above describe the synthetic input.

[Splunk streamstats reference](https://help.splunk.com/en/splunk-enterprise/search/spl-search-reference/9.3/search-commands/streamstats)
