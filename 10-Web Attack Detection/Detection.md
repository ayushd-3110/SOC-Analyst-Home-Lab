D# Incident Response

## 1. Identification

The SOC detected suspicious HTTP requests originating from:

192.168.234.129

The requests targeted the IIS server:

192.168.234.130

---

## 2. Analysis

The attacker generated multiple suspicious requests including:

- SQL injection-style input
- Path traversal-style input
- Admin page enumeration
- Login page enumeration
- Backup path enumeration
- robots.txt enumeration

The User-Agent was:

curl/8.19.0

---

## 3. Containment

Recommended containment actions:

1. Block or restrict the suspicious source IP if appropriate.
2. Restrict unnecessary access to administrative URLs.
3. Review IIS request filtering rules.
4. Temporarily isolate the application if compromise is suspected.
5. Preserve IIS and Windows logs for further investigation.

---

## 4. Eradication

Recommended actions:

- Review the vulnerable ASP application.
- Remove insecure input handling.
- Implement proper input validation.
- Use parameterized database queries.
- Remove unnecessary files and endpoints.
- Review application permissions.

---

## 5. Recovery

After remediation:

- Restart/redeploy the application if required.
- Verify IIS functionality.
- Monitor new HTTP requests.
- Search Splunk for repeated attack patterns.
- Confirm that suspicious activity has stopped.

---

## 6. Lessons Learned

The lab demonstrated that web attacks can often be identified from HTTP
logs even when there is no obvious malware or Windows process activity.

Good logging and centralized SIEM monitoring are important for detecting
web reconnaissance and exploitation attempts.