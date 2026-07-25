1. Total Connections:
index=main EventCode=5156 | stats count

2. Destination Ports

Since your logs keep networking information inside the Message field, use rex to extract them:

index=main EventCode=5156
| rex field=Message "Source Address:\s+(?<src_ip>\S+)"
| rex field=Message "Destination Address:\s+(?<dest_ip>\S+)"
| rex field=Message "Destination Port:\s+(?<dest_port>\d+)"
| stats count by dest_port
| sort -count


3. Source IP

index=main EventCode=5156
| rex field=Message "Source Address:\s+(?<src_ip>\S+)"
| stats count by src_ip

4. Destination IP

index=main EventCode=5156
| rex field=Message "Destination Address:\s+(?<dest_ip>\S+)"
| stats count by dest_ip

5. Process Name

index=main EventCode=5156
| rex field=Message "Application Name:\s+(?<process>.+)"
| stats count by process

6. Timeline

index=main EventCode=5156
| timechart span=1m count

7. Raw Investigation

index=main EventCode=5156
| table _time ComputerName Message