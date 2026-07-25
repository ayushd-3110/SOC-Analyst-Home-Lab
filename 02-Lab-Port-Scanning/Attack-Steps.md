Step 1
Verify connectivity.

From Kali:
ping 192.168.234.133


Step 2

Run a basic scan.

nmap 192.168.234.133


Step 3

Run service detection.

nmap -sV 192.168.234.133


Step 4

Run an aggressive scan.

nmap -A 192.168.234.133

Step 5

Save the output.

nmap -A 192.168.234.133 -oN scan.txt




