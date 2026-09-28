Questions to Answer
Q1
Which IP initiated the scan?
Answer: 192.168.234.129

Q2
Which host was targeted?
192.168.234.133

Q3
How many ports were scanned?
Use:index=sysmon EventCode=3
| stats dc(DestinationPort)


Q4
What protocol was used?
TCP

Q5
What time did the scan begin?

Use:
index=sysmon EventCode=3
| sort _time


Q6
Was the scan successful?

Review the Nmap output and the network logs to identify which ports were open and responsive.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
