---
kind: person
acts: external
relations:
  - { entity: post, verb: owns, cardinality: one-to-many }
  - { entity: account, verb: owns, cardinality: one-to-many }
  - { entity: api-key, verb: holds, cardinality: one-to-one }
  - { entity: ai-agent, verb: connects, cardinality: one-to-many }
references:
  - { kind: code, role: implementation, target: src/lib/server/db/schema.ts#users }
  - { kind: code, role: implementation, target: src/lib/domain/profile-settings.ts }
  - { kind: code, role: implementation, target: src/lib/server/auth.ts#getAdminUser }
  - { kind: doc, role: intent, target: docs/configuration.md, title: The login }
---

# Admin

The one person an instance belongs to. They sign in with an email, a password
and an authenticator code, connect their social accounts, write and publish
posts, and run the instance's settings.

## Information kept

- **Email** — the address they sign in with
- **Password** — kept only as a hash; at least eight characters
- **Display name** — the name the app greets them by, up to 80 characters; the email's first part when empty
- **Profile picture** — an https image address shown on their avatar and in the composer
- **Time zone** — the browser's time zone, recorded when the app opens; Insights counts days in it
- **Default Mastodon visibility** — Public, Unlisted, Followers or Direct, applied to new posts
- **Preselected accounts** — the accounts a new post starts with; empty means every active account
- **Authenticator** — the authenticator app secret their six-digit codes come from, kept encrypted
- **Backup codes** — ten one-time codes for signing in without the authenticator, kept only as hashes

## States

### Awaiting two-factor setup

The account exists but no authenticator is enrolled yet; signing in leads to
setting one up.

### Two-factor active

An authenticator is enrolled; every sign-in asks for a code from it or a
backup code.
