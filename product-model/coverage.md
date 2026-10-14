---
scope: The CogSend Worker application — web app, HTTP API, MCP server and scheduler tick — for sign-in, composing, publishing and scheduling posts, Posts, Insights, connected accounts and settings.
method: Static inspection of source, schema and documentation at the pinned commit; nothing was run.
covered:
  - description: Composer components, compose route and the client-side editing, splitting, quoting and image shrinking they do.
    paths: [src/routes/compose/, src/lib/components/Editor.svelte, src/lib/components/compose-session.svelte.ts, src/lib/components/XQuoteCard.svelte, src/lib/components/LinkPreview.svelte, src/lib/components/PostStatusBanner.svelte, src/lib/components/shrink-image.ts, src/lib/components/posts-notice.ts]
  - description: Draft, override, media, duplicate, publish and schedule endpoints and the shared operations behind the API and MCP server.
    paths: [src/routes/api/drafts/, src/lib/server/api/, src/lib/server/draft-record.ts, src/routes/api/validate/, src/routes/api/link-preview/, src/lib/server/opengraph.ts, src/lib/server/x-post-preview.ts]
  - description: Publishing engine, delivery planning, call budget and per-delivery cancel, retry and reschedule endpoints.
    paths: [src/lib/server/publish.ts, src/lib/server/publish-plan.ts, src/lib/server/budget.ts, src/routes/api/targets/, src/lib/server/providers/]
  - description: Scheduler tick, failure digest, publishing health and the tick token.
    paths: [src/lib/server/scheduler.ts, src/lib/server/tick-token.ts, src/routes/api/internal/, src/routes/api/scheduler/, .github/workflows/scheduler-tick.yml]
  - description: Posts list, queue listing and the old addresses that redirect to it.
    paths: [src/routes/posts/, src/lib/server/post-list.ts, src/routes/api/queue/, src/routes/drafts/, src/routes/outbox/]
  - description: Accounts page, connect, reconnect, check and disconnect flows, Zernio and platform app credentials.
    paths: [src/routes/accounts/, src/routes/connections/, src/routes/api/connections/, src/routes/api/settings/platform-apps/, src/lib/server/oauth-callback.ts, src/lib/server/oauth-state.ts, src/lib/server/zernio.ts, src/lib/server/zernio-import.ts, src/lib/server/platform-credentials.ts, src/lib/server/platform-setup.ts, src/lib/server/connection-list.ts]
  - description: Login pages, account claim, password sign-in, two-factor enrolment, verification and rotation, and their throttling.
    paths: [src/routes/login/, src/routes/api/auth/claim/, src/routes/api/auth/login/, src/routes/api/auth/logout/, src/routes/api/auth/totp/, src/lib/server/auth.ts, src/lib/server/auth-gate.ts, src/lib/server/totp.ts, src/lib/server/qr.ts]
  - description: Settings page and its settings, login, API key endpoints, and request authorization by session, key scope or tick credential.
    paths: [src/routes/settings/, src/routes/api/settings/+server.ts, src/routes/api/account/, src/routes/api/key/, src/lib/server/api-keys.ts, src/lib/server/app-settings.ts, src/lib/server/require.ts, src/hooks.server.ts]
  - description: Dashboard, Insights page and report, and the app shell.
    paths: [src/routes/+page.svelte, src/routes/+page.server.ts, src/routes/+layout.svelte, src/routes/+layout.server.ts, src/routes/+layout.ts, src/routes/insights/, src/routes/api/insights/, src/lib/server/insights-report.ts]
  - description: MCP server and its key check.
    paths: [src/routes/api/mcp/, src/lib/server/mcp-auth.ts]
  - description: Shared domain logic for posts, threads, limits, validation, scheduling and settings.
    paths: [src/lib/domain/]
  - description: Database schema and the media store that back the kept facts.
    paths: [src/lib/server/db/, src/lib/server/media.ts, src/lib/server/public-media.ts, src/lib/server/image-dimensions.ts, src/lib/server/serialize.ts, src/routes/api/media/]
exclusions:
  - description: Tests and test fixtures.
    paths: [tests/, playwright.config.ts]
  - description: Database migrations.
    paths: [drizzle/]
  - description: Documentation, the in-app API reference page and repository templates.
    paths: [docs/, src/routes/api/+page.svelte, README.md, CONTRIBUTING.md, SECURITY.md, THIRD-PARTY-NOTICES.md, .github/ISSUE_TEMPLATE/, .github/PULL_REQUEST_TEMPLATE.md, .github/FUNDING.yml]
  - description: Continuous integration, release workflows and build configuration.
    paths: [.github/workflows/ci.yml, .github/workflows/release.yml, .github/workflows/deploy.yml.example, vite.config.ts, eslint.config.js, prettier.config.js, tsconfig.json, wrangler.jsonc, package.json, release.json]
  - description: Visual assets and presentation-only components.
    paths: [static/, src/lib/assets/, src/routes/layout.css, src/lib/components/AccountAvatar.svelte, src/lib/components/PlatformLogo.svelte, src/lib/components/SocialIcon.svelte, src/lib/components/CopyButton.svelte, src/lib/components/ConfirmDialog.svelte, src/lib/components/dialog-focus.ts, src/lib/components/menu-nav.ts, src/lib/components/initials.ts, src/lib/components/platform-color.ts, src/lib/components/session-expired.ts]
  - description: Request plumbing, encryption, cookies, CSRF, rate limiting and security headers.
    paths: [src/lib/server/http.ts, src/lib/server/env.ts, src/lib/server/crypto.ts, src/lib/server/cookies.ts, src/lib/server/csrf.ts, src/lib/server/rate-limit.ts, src/lib/server/security-headers.ts, src/lib/server/derived-secrets.ts, src/app.d.ts, src/app.html, src/lib/index.ts]
unmapped:
  - description: In-app updater, release checks, update notice and health probe.
    paths: [src/lib/server/updater/, src/lib/server/release.ts, src/routes/api/update/, src/routes/api/release/, src/routes/api/health/, src/lib/components/UpdatePanel.svelte, src/lib/components/update-notice.svelte.ts]
  - description: Session lookup and account deletion endpoint.
    paths: [src/routes/api/auth/me/]
  - description: Operator scripts for setup, deploy, secrets, diagnosis and login reset.
    paths: [scripts/]
limitations:
  - description: Platform adapters whose answers decide whether a failure is temporary, permanent or an expired credential.
    paths: [src/lib/server/providers/]
---

# Coverage
