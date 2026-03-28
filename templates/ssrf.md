# SSRF — [Target Endpoint]

## Summary

A Server-Side Request Forgery vulnerability was identified at `[ENDPOINT]`. An authenticated/unauthenticated user can manipulate the `[PARAMETER]` parameter to force the server to make HTTP requests to arbitrary internal or external destinations, including cloud metadata endpoints and internal network services.

## Severity

- **CVSS 3.1**: 7.5 (High) — `CVSS:3.1/AV:N/AC:L/PR:L/UI:N/S:C/C:H/I:N/A:N`
- **CWE**: [CWE-918](https://cwe.mitre.org/data/definitions/918.html) — Server-Side Request Forgery

## Steps to Reproduce

1. Navigate to `[URL]`
2. Intercept the request with Burp Suite
3. Modify the `[PARAMETER]` parameter:
   ```
   [PARAMETER]=http://169.254.169.254/latest/meta-data/
   ```
4. Forward the request
5. Observe the server response contains cloud metadata / internal data

## Impact

An attacker could:
- Access cloud instance metadata (AWS/GCP/Azure credentials)
- Scan internal network ports and services
- Read internal-only APIs and admin panels
- Potentially pivot to Remote Code Execution via internal services

## Proof of Concept

### Request
```http
POST /api/[endpoint] HTTP/1.1
Host: [target]
Content-Type: application/json
Authorization: Bearer [token]

{
  "[parameter]": "http://169.254.169.254/latest/meta-data/iam/security-credentials/"
}
```

### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "result": "[PASTE SERVER RESPONSE HERE]"
}
```

### Screenshots
<!-- Attach screenshots here -->

## Remediation

1. Implement an allowlist of permitted domains/IPs for outbound requests
2. Block requests to private IP ranges (10.x, 172.16-31.x, 192.168.x, 169.254.x)
3. Block requests to cloud metadata endpoints
4. Use a dedicated HTTP client that does not follow redirects
5. Validate URL scheme (allow only `https://`)
