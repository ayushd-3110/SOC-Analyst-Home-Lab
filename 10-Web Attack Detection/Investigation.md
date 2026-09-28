# Investigation Report — Lab 10

## Summary

During the investigation, multiple suspicious HTTP requests were identified
against the IIS web server.

The activity originated from 192.168.234.129 and targeted
192.168.234.130.

The attacker used curl/8.19.0 and generated requests associated with SQL
injection, path traversal and web endpoint enumeration.

## Findings

The following suspicious activity was observed:

- SQL injection-style parameter
- Path traversal-style parameter
- /admin enumeration
- /login enumeration
- /backup enumeration
- /robots.txt enumeration

Some requests returned HTTP 200 while several enumeration requests returned
HTTP 404.

## Assessment

The activity is consistent with automated or manual web reconnaissance and
attempted exploitation.

The available IIS logs demonstrate suspicious requests but do not by
themselves prove successful compromise.

## Severity

Medium

## Recommendation

Review the vulnerable application, implement proper input validation,
restrict unnecessary endpoints and continue monitoring IIS logs in Splunk.

## Screenshot Evidence

For the exact evidence visible in the supplied screenshots, see [`Evidence-Observed.md`](Evidence-Observed.md). The documentation uses the screenshot evidence as the boundary for claims and avoids treating simulation artifacts as real-world compromise.
