<div align="center">

# burp-quicknotes

**Structured note templates for bug bounty hunting with Burp Suite**

[![License: MIT](https://img.shields.io/badge/License-MIT-238636?style=flat-square)](LICENSE)
[![Burp Suite](https://img.shields.io/badge/Burp_Suite-Community_&_Pro-FF6633?style=flat-square)](https://portswigger.net/burp)

Built by [AliceLabs LLC](https://alicelabs.site) · handle: `ulkoro`

</div>

---

## Why

Every bug bounty hunter wastes time formatting findings for reports. These templates give you copy-paste-ready markdown structures for every common vulnerability class, pre-filled with CVSS vectors, CWE references, and remediation guidance.

## Templates

| Template | File | Use when |
|----------|------|----------|
| **SSRF** | [`ssrf.md`](templates/ssrf.md) | Server-Side Request Forgery — internal network probing, cloud metadata |
| **IDOR** | [`idor.md`](templates/idor.md) | Insecure Direct Object Reference — unauthorized data access |
| **XSS** | [`xss.md`](templates/xss.md) | Cross-Site Scripting — reflected, stored, DOM-based |
| **Auth Bypass** | [`auth-bypass.md`](templates/auth-bypass.md) | Authentication/authorization flaws |
| **Info Disclosure** | [`info-disclosure.md`](templates/info-disclosure.md) | Sensitive data exposure, verbose errors, stack traces |
| **Subdomain Takeover** | [`subdomain-takeover.md`](templates/subdomain-takeover.md) | Dangling DNS records, unclaimed services |

## Usage

1. Find a vulnerability during testing
2. Copy the matching template
3. Fill in the specific details (URL, parameters, payload, screenshots)
4. Submit to the bug bounty platform (YesWeHack, Bugcrowd, Intigriti, HackerOne)

## Template structure

Every template follows this format:

```markdown
# [Vulnerability Type] — [Target Endpoint]

## Summary
One-paragraph description of the vulnerability.

## Severity
- CVSS: X.X (Vector string)
- CWE: CWE-XXX

## Steps to Reproduce
1. Step one
2. Step two
3. ...

## Impact
What an attacker could do.

## Proof of Concept
Request/response, screenshots, or video.

## Remediation
How to fix it.
```

## Platforms tested on

- YesWeHack
- Bugcrowd
- Intigriti
- HackerOne

## License

MIT — use, modify, share freely.

---

<div align="center">

**From the security research team at [AliceLabs LLC](https://alicelabs.site)**

</div>
