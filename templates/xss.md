# XSS — [Target Endpoint]

## Summary

A [Reflected/Stored/DOM-based] Cross-Site Scripting vulnerability was identified at `[ENDPOINT]`. User input in the `[PARAMETER]` parameter is reflected/stored without proper sanitization, allowing execution of arbitrary JavaScript in the context of the victim's browser session.

## Severity

- **CVSS 3.1**: 6.1 (Medium) — `CVSS:3.1/AV:N/AC:L/PR:N/UI:R/S:C/C:L/I:L/A:N`
- **CWE**: [CWE-79](https://cwe.mitre.org/data/definitions/79.html) — Improper Neutralization of Input During Web Page Generation

## Steps to Reproduce

1. Navigate to `[URL]`
2. Inject the following payload in the `[PARAMETER]` field:
   ```
   <script>alert(document.domain)</script>
   ```
3. Submit / trigger the request
4. Observe JavaScript execution in the browser

## Impact

An attacker could:
- Steal session cookies and authentication tokens
- Perform actions on behalf of the victim
- Redirect users to phishing pages
- Deface the application
- Keylog user input on the page

## Proof of Concept

### Payload
```
[PAYLOAD HERE]
```

### URL (for reflected XSS)
```
https://[target]/[path]?[parameter]=[PAYLOAD_URL_ENCODED]
```

### Screenshots
<!-- Attach screenshots showing the alert/execution -->

## Remediation

1. Encode all user input before rendering in HTML context
2. Implement Content-Security-Policy headers
3. Use framework-native escaping (React JSX, Vue templates, etc.)
4. Validate and sanitize input on the server side
5. Set `HttpOnly` and `Secure` flags on session cookies
