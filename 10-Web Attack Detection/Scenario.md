# Lab 10 — Attack Scenario

## Scenario

A Windows IIS web server is being monitored by the SOC team.

During monitoring, the SOC analyst notices multiple HTTP requests coming
from the same external/internal source.

The requests target unusual application parameters and sensitive-looking
web paths.

The activity includes:

- SQL injection-style parameters
- Path traversal-style parameters
- Requests for administrative pages
- Requests for backup files
- Requests for robots.txt

The SOC analyst must determine whether the requests are normal web traffic
or suspicious activity.

---

## Attacker

Kali Linux

IP:
192.168.234.129

## Victim

Windows IIS Server

IP:
192.168.234.130

---

## Analyst Task

The analyst must:

1. Identify the source IP.
2. Identify suspicious URLs and parameters.
3. Determine the attack types.
4. Check HTTP response codes.
5. Identify the User-Agent.
6. Correlate multiple requests.
7. Extract IOCs.
8. Determine the severity.
9. Recommend containment and remediation actions.