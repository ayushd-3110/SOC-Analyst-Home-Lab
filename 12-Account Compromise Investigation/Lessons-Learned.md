Lessons Learned
Technical Lessons
Windows Security logs provide valuable authentication telemetry.
Event ID 4625 can identify failed authentication.
Event ID 4624 can identify successful authentication.
Event ID 4688 helps investigate post-authentication process execution.
Event ID 4672 should be correlated carefully with the actual account.
Source IP correlation helps identify where authentication originated.
Splunk makes it easier to correlate authentication and endpoint events.
SOC Analyst Lessons
A successful login after several failures deserves investigation.
One event alone may not provide enough context.
Time correlation is important.
Account, host, source IP and process information should be investigated together.
Analysts should distinguish suspicious activity from confirmed compromise.
Evidence should never be invented or assumed.