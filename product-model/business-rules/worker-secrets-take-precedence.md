---
appliesTo:
  - { type: capability, id: save-platform-app }
  - { type: capability, id: connect-account }
  - { type: entity, id: platform-app, facts: [Source] }
references:
  - { kind: code, role: implementation, target: src/lib/server/platform-credentials.ts#configuredByEnv }
  - { kind: doc, role: intent, target: docs/configuration.md, title: "Secrets" }
---

# A platform app set as Worker secrets takes precedence

When the operator set a platform's app as Worker secrets, those are used and the accounts dialog cannot save another.
