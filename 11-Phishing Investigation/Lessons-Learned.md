
---

# 11. `Lessons-Learned.md`

```markdown
# Lessons Learned — Phishing Investigation

## 1. Phishing Often Uses Social Engineering

The simulated email used:

- Urgency
- Fear
- Account-security concerns
- Threat of account suspension

These techniques are designed to encourage quick user action.

---

## 2. URLs Require Investigation

A suspicious URL should not automatically be opened in a normal browser.

The lab demonstrated controlled investigation using:

```bash
curl -I