# Contributing to burp-quicknotes

## Adding a new template

1. Create `templates/VULN_NAME.md` following the standard structure (see README)
2. Include: Severity, CVSS score, CWE, Steps to reproduce, PoC format, Impact, Remediation, References
3. Add a row to the table in `README.md`
4. Open a PR

## Template quality checklist

- [ ] CVSS vector string is valid (use [cvss.js.org](https://cvss.js.org) to verify)
- [ ] CWE number is correct
- [ ] At least one OWASP or PortSwigger reference included
- [ ] Remediation is specific (not just "sanitize inputs")
- [ ] PoC section has a realistic HTTP request example

## Commit conventions

- `feat: add XXE template`
- `fix: correct CVSS score in SSRF template`
- `docs: improve IDOR remediation guidance`

---

Questions? → [contacto@alicelabs.site](mailto:contacto@alicelabs.site)
