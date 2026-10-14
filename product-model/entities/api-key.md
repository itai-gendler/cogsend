---
references:
  - { kind: code, role: implementation, target: src/lib/server/api-keys.ts }
  - { kind: code, role: implementation, target: src/lib/domain/api-scopes.ts }
  - { kind: code, role: implementation, target: src/routes/api/key/+server.ts }
---

# API key

The Admin's personal API key, which scripts and AI agents present instead of
signing in. There is one active key at a time: generating a replacement stops
the old one.

## Information kept

- **Prefix** — the first characters, shown so the key can be recognised; the full key is shown once and only its hash is kept
- **Scope** — Read-only, or Read + write
- **Created** — when it was generated
- **Last used** — when a request last presented it

## States

### Active

Accepted on the API and the MCP server.

### Revoked

Stopped, by revoking it or generating a replacement; it is refused from then
on.
