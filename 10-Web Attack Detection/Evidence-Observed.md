# Screenshot Evidence Review

The IIS/web-attack screenshots show a controlled web-security lab on **192.168.234.130**.

### Web Enumeration
Requests to `/Lab10/admin`, `/Lab10/Login`, `/Lab10/robots.txt`, and `/Lab10/backup` returned **HTTP 404 Not Found** with **Microsoft-IIS/10.0** visible in the response.

### SQL-like Input
The vulnerable lab page visibly displays the test input `1' OR '1'='1` and reports **Suspicious SQL-Like input detected**.

### Other Evidence
The screenshot set contains IIS log collection, Nikto scanning, path-traversal testing, Splunk detection/investigation, correlation, and a Web Attack Detection dashboard.

## Evidence Boundary
The screenshots demonstrate attack attempts and detection logic. The 404 responses and lab warning do not prove successful exploitation of IIS.
