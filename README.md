# burp-quicknotes

**Structured bug bounty report templates for Burp Suite**

[![License: MIT](https://img.shields.io/badge/License-MIT-238636?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Burp%20Suite-orange?style=flat-square)](https://portswigger.net/burp)

Pre-built, structured report templates for the most common web vulnerabilities — drop them into Burp Suite's note fields and fill in the blanks. No more scrambling to remember CVSS scores or remediation steps mid-engagement.

---

## Included templates

| Template | Vulnerability | Severity |
|----------|--------------|----------|
| `SSRF.md` | Server-Side Request Forgery | High / Critical |
| `IDOR.md` | Insecure Direct Object Reference | Medium / High |
| `XSS.md` | Cross-Site Scripting (Reflected, Stored, DOM) | Medium / High |
| `AUTH_BYPASS.md` | Authentication Bypass | Critical |
| `SQLi.md` | SQL Injection | High / Critical |
| `OPEN_REDIRECT.md` | Open Redirect | Low / Medium |
| `XXE.md` | XML External Entity Injection | High |
| `RCE.md` | Remote Code Execution | Critical |

---

## Template structure

Every template follows the same format for consistency across reports:

```markdown
## [VULN-TYPE] — [Target/Endpoint]

**Severity:** [Critical / High / Medium / Low / Informational]
**CVSS Score:** [0.0–10.0] ([Vector String])
**CWE:** [CWE-XXX]

### Summary
[One paragraph description of the vulnerability]

### Affected endpoint
- URL: 
- Method: 
- Parameter: 

### Steps to reproduce
1. 
2. 
3. 

### Proof of Concept
\```http
[Request/Response]
\```

### Impact
[What an attacker can achieve]

### Remediation
[Specific fix guidance]

### References
- [OWASP link]
- [CVE if applicable]
```

---

## Usage

### Option A — Copy into Burp Notes

1. Open Burp Suite → **Target** tab → right-click a request → **Send to Repeater**
2. Open the **Notes** tab in any Burp tool
3. Paste the relevant template and fill in the blanks

### Option B — Use with Burp's Reporting

1. Copy the template into **Burp Scanner** → **Issue definitions** → custom notes
2. Reference the template when writing manual findings in the **Audit** view

### Option C — CLI quick-copy (macOS/Linux)

```bash
# Copy SSRF template to clipboard
cat templates/SSRF.md | pbcopy   # macOS
cat templates/SSRF.md | xclip    # Linux
```

---

## Why structured templates?

- **Consistency** — uniform format across all reports on a program
- **Speed** — skip the blank-page problem mid-engagement
- **Completeness** — CVSS, CWE, remediation, and references baked in
- **Client-ready** — templates are written for technical and non-technical audiences

---

## Contributing

Have a template for a vulnerability type not listed here? PRs welcome.

See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## License

MIT — free to use in personal and commercial engagements.

---

**Built by [AliceLabs LLC](https://alicelabs.site) · Security Research Division**  
[contacto@alicelabs.site](mailto:contacto@alicelabs.site)
