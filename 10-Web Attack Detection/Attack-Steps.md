## Step 1 — Verify the victim
From Kali:

ping 192.168.234.130
In your environment, ICMP did not respond, but HTTP connectivity worked.

You verified the web server using:

curl -I http://192.168.234.130
The server returned:

HTTP/1.1 200 OK
Server: Microsoft-IIS/10.0
Explanation
This confirmed that the IIS server was reachable over HTTP even though the Windows firewall/server did not respond to ping.

## Step 2 — Access the application
curl http://192.168.234.130/Lab10/
This confirmed that the Lab 10 application was accessible.

## Step 3 — SQL Injection Simulation
curl "http://192.168.234.130/Lab10/default.asp?id=1%27%20OR%20%271%27=%271"
Explanation
The encoded characters represent a SQL injection-style input.

The important part is:

' OR '1'='1
This is a classic example of an attacker attempting to alter the logic of a SQL query.

Important: In the SOC lab, this is primarily used to generate and detect suspicious web traffic. A 200 response alone does not prove that SQL injection successfully compromised a database.

## step 4 - Path Traversal Simulation
curl "http://192.168.234.130/Lab10/default.asp?file=../../../../Windows/win.ini"
Explanation
The attacker uses:

../
to attempt to move outside the application's expected directory.

The target:

Windows/win.ini
is a Windows system file.

From a SOC perspective, the important evidence is the suspicious traversal pattern in the HTTP request.

## Step 5 - Web Enumeration
Requests were generated against:

/admin
/login
/backup
/robots.txt
Example:

curl -I http://192.168.234.130/Lab10/admin
Explanation
An attacker commonly performs enumeration before attempting exploitation.

They may search for:

Login pages

Admin panels

Backup files

Configuration files

Robots.txt

Hidden application endpoints

In the IIS logs, several of these requests returned 404, which is still useful evidence because it shows the attacker was probing for resources.