| Observed Activity                                          | MITRE ATT&CK                                  |
| ---------------------------------------------------------- | --------------------------------------------- |
| Web endpoint reconnaissance                                | **T1595 – Active Scanning**                   |
| Searching for `/admin`, `/login`, `/backup`, `/robots.txt` | **T1595 – Active Scanning**                   |
| SQL injection-style request                                | **T1190 – Exploit Public-Facing Application** |
| Path traversal-style request                               | **T1190 – Exploit Public-Facing Application** |


Explanation
T1595 – Active Scanning

The attacker actively probes the web application for available resources and endpoints.

T1190 – Exploit Public-Facing Application

The SQL injection and path traversal requests represent attempts to exploit a web-facing application.

For your report, write "attempted exploitation", rather than saying the attacker successfully exploited the server.