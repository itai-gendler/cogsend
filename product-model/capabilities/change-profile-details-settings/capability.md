---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/settings/+server.ts }
  - { kind: code, role: implementation, target: src/lib/domain/profile-settings.ts#isValidProfilePictureUrl }
  - { kind: code, role: implementation, target: src/routes/settings/+page.svelte }
---

# Change profile details

Change the Admin's display name and profile picture under Settings, Profile Details. The picture is an https image address; Remove picture clears it.
