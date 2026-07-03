# Security Prompts

## Threat Model

```
Create a threat model for this system:

System: {{system-description}}
Tech stack: {{stack}}
Data handled: {{data-types}}

Identify:
1. Assets to protect (data, functionality, reputation)
2. Threat actors (external attackers, malicious insiders, accidental misuse)
3. Attack vectors (STRIDE: Spoofing, Tampering, Repudiation, Info Disclosure, DoS, Elevation)
4. Existing controls
5. Gaps and recommended mitigations

Provide:
- Threat matrix with likelihood and impact ratings
- Top 5 highest-risk threats
- Prioritized mitigation roadmap
```

## Authentication & Authorization Review

```
Review this authentication and authorization implementation:

{{code}}

Check for:
- Password hashing (bcrypt/argon2 with sufficient cost factor)
- JWT implementation (algorithm, expiry, secret strength)
- Session management (secure, httpOnly, sameSite cookies)
- OAuth2/OIDC implementation correctness
- Rate limiting on auth endpoints
- Account lockout after failed attempts
- Privilege escalation vulnerabilities
- Insecure direct object references (IDOR)
- Missing authorization checks

Provide:
- Vulnerabilities found with severity
- Specific line numbers
- Remediation code examples
```

## Input Validation Audit

```
Audit input validation across this codebase:

{{code-or-file-list}}

Check every user-controlled input for:
- SQL injection (raw queries, string concatenation)
- NoSQL injection (MongoDB operator injection)
- XSS (unescaped output in HTML context)
- Command injection (shell exec with user input)
- Path traversal (file operations with user-supplied paths)
- SSRF (user-controlled URLs in server-side requests)
- XXE (XML parsing with external entities enabled)
- Mass assignment (binding user input directly to models)

Provide:
- Each vulnerable location with attack scenario
- Severity rating
- Fixed code example
```

## Secrets & Credentials Scan

```
Scan this codebase for exposed secrets:

Check for:
- API keys (AWS, Stripe, Twilio, SendGrid patterns)
- Private keys and certificates (-----BEGIN)
- Database connection strings with credentials
- Hardcoded passwords or tokens
- .env files committed to git
- Secrets in comments or logs
- Base64-encoded credentials

Also check git history:
`git log --all --full-history -- "*.env"`
`git grep -i "password\|secret\|api_key" $(git rev-list --all)`

Provide:
- Each finding with file, line, and type of secret
- Whether it appears in git history (requires rotation even if removed)
- Remediation steps (rotate key, add to .gitignore, use secret manager)
```

## Dependency Vulnerability Review

```
Review project dependencies for security vulnerabilities:

Run and analyze:
- `npm audit --json` (Node.js)
- `pip-audit` (Python)
- `bundle audit` (Ruby)
- `cargo audit` (Rust)

For each vulnerability provide:
- Package name and version
- CVE identifier and severity
- Description of the vulnerability
- Whether it's exploitable in this project's usage
- Upgrade path or workaround

Prioritize:
1. Critical/High severity in direct dependencies
2. Critical/High in transitive dependencies
3. Medium severity
4. Low severity
```

## Security Headers Review

```
Review HTTP security headers for this web application:

Check for presence and correct configuration of:
- Content-Security-Policy (CSP)
- Strict-Transport-Security (HSTS)
- X-Content-Type-Options: nosniff
- X-Frame-Options or CSP frame-ancestors
- Referrer-Policy
- Permissions-Policy
- Cross-Origin-Opener-Policy (COOP)
- Cross-Origin-Resource-Policy (CORP)

Test with: https://securityheaders.com

Provide:
- Missing headers
- Misconfigured headers
- Recommended values for each
- Implementation code for the framework in use
```

## Cryptography Review

```
Review cryptographic implementations in this code:

{{code}}

Check for:
- Weak algorithms (MD5, SHA1 for security, DES, RC4, ECB mode)
- Insufficient key lengths (RSA < 2048, AES < 128)
- Hardcoded IVs or salts
- Predictable random number generation (Math.random() for security)
- Improper certificate validation
- Timing attacks in comparison functions

Provide:
- Each cryptographic issue with explanation of the risk
- Modern replacement recommendation
- Code example with correct implementation
```
