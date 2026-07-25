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
Failed Logins by Username

index=main EventCode=4625
| stats count by Account_Name
Visualization:  Bar Chart


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