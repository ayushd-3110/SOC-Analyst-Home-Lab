# Lessons Learned

## What I Learned

This lab helped me understand how a SOC analyst investigates web attacks
using IIS logs.

I learned that individual HTTP requests may not always look dangerous.
However, when multiple requests are correlated, they can reveal a clear
attack pattern.

For example:

/admin
/login
/backup
/robots.txt

followed by suspicious parameters can indicate reconnaissance followed by
attempted exploitation.

I also learned how useful fields such as source IP, URI, query parameters,
HTTP status and User-Agent are during an investigation.

---

## Key SOC Skills Practiced

- IIS log analysis
- Splunk searching
- SPL development
- Web attack detection
- IOC extraction
- Attack correlation
- MITRE ATT&CK mapping
- Incident response
- Security reporting

---

## Improvement

In a real environment, I would improve the detection by adding:

- Rate-based detection
- Multiple failed requests from one IP
- SQL injection pattern detection
- Path traversal detection
- WAF integration
- Threat intelligence enrichment
- Automated alerting
- Risk scoring