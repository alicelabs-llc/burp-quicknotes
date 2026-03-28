# IDOR — [Target Endpoint]

## Summary

An Insecure Direct Object Reference vulnerability was identified at `[ENDPOINT]`. By modifying the `[PARAMETER]` parameter, a low-privileged user can access or modify resources belonging to other users without proper authorization checks.

## Severity

- **CVSS 3.1**: 6.5 (Medium) — `CVSS:3.1/AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:N/A:N`
- **CWE**: [CWE-639](https://cwe.mitre.org/data/definitions/639.html) — Authorization Bypass Through User-Controlled Key

## Steps to Reproduce

1. Log in as User A (attacker account)
2. Navigate to `[URL]` and note your resource ID: `[ID_A]`
3. Intercept the request with Burp Suite
4. Change `[PARAMETER]` from `[ID_A]` to `[ID_B]` (User B's resource)
5. Forward the request
6. Observe that User B's data is returned

## Impact

An attacker could:
- Read other users' personal data, documents, or settings
- Modify or delete other users' resources
- Enumerate all valid resource IDs via sequential/predictable patterns
- Escalate to full account takeover if profile endpoints are affected

## Proof of Concept

### Request (as User A, accessing User B's data)
```http
GET /api/[endpoint]/[USER_B_ID] HTTP/1.1
Host: [target]
Authorization: Bearer [USER_A_TOKEN]
```

### Response (User B's data returned)
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "[USER_B_ID]",
  "email": "[REDACTED]",
  "data": "[REDACTED]"
}
```

## Remediation

1. Implement server-side authorization checks on every request
2. Verify the authenticated user owns the requested resource
3. Use UUIDs instead of sequential integers for resource IDs
4. Add rate limiting to prevent enumeration
