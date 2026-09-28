PHISHING INVESTIGATION TIMELINE
================================

1. Suspicious email identified
   ↓
2. Email sender and subject analyzed
   ↓
3. Phishing indicators identified
   ↓
4. Suspicious /verify URL investigated
   ↓
5. HTTP request generated from Kali test machine
   ↓
6. IIS activity collected by Splunk
   ↓
7. Source IP and URL activity investigated
   ↓
8. IOCs extracted
   ↓
9. Evidence correlated
   ↓
10. Final SOC assessment completed


---

# 7. `Investigation.md`

```markdown
# Investigation — Phishing Investigation

## Investigation Summary

A suspicious email was analyzed after being reported as potentially malicious.

The email claimed to originate from an IT Security team and requested account verification.

The message used urgency and threatened account suspension.

---

## Investigation Timeline

1. Suspicious email identified.
2. Sender analyzed.
3. Subject analyzed.
4. URL extracted.
5. Phishing indicators identified.
6. URL safely investigated from Kali.
7. HTTP activity generated.
8. IIS logs reviewed.
9. Splunk searched for related activity.
10. Source IP identified.
11. URL path identified.
12. IOCs extracted.
13. MITRE ATT&CK mapping performed.
14. Final assessment documented.

---

## Email Analysis

Sender:

```text
security-alert@company-security.example

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
