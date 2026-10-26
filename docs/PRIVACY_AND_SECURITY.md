# Privacy, security and human oversight

## Minimum Phase (1) controls
- Validate file type, size and content; generate server-side storage names.
- Keep uploads outside public web roots.
- Use environment variables for secrets and exclude `.env` files from Git.
- Enforce authentication and role checks on the backend.
- Restrict records by organization/tenant where multi-tenant behavior is enabled.
- Avoid logging document bodies, credentials or sensitive model prompts by default.
- Show whether external AI services are used and what data is sent.
- Keep human approval for high-risk or uncertain findings.
- Do not auto-publish content or silently rewrite the source document.

## Planned controls
Encryption-at-rest configuration, configurable retention/deletion, stronger tenant isolation testing, detailed audit trails and private/on-premise inference are not complete until implemented and verified.

## Threats to consider
Malicious uploads, prompt injection embedded in documents, cross-tenant access, leaked API keys, over-permissive roles, model hallucinations, stale source material and unsafe generated corrections.
