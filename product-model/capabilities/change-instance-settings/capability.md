---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/settings/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/app-settings.ts#rememberAppName }
  - { kind: code, role: implementation, target: src/lib/domain/instance-name.ts }
---

# Change instance settings

Name the instance and choose whether release candidates are offered, under Settings, Instance.
