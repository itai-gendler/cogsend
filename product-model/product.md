---
id: cogsend
summary: A self-hosted social scheduler on Cloudflare that writes a post once, tailors it per platform, and publishes or schedules it to Mastodon, Bluesky, LinkedIn, Threads and X.
category: social-media
tags: [social-media, scheduler, self-hosted, cloudflare-workers, mastodon, bluesky]
authors:
  - name: CogSend contributors
    url: https://github.com/cogsend/cogsend
license: MIT
languages: [en]
limitations:
  - One instance holds exactly one account, its Admin; there are no other people, roles or teams.
  - Two-factor authentication is always on and cannot be turned off.
  - A post that went out to every account it was sent to is never edited; it is duplicated to post again.
  - Deleting a post or disconnecting an account in CogSend never removes anything already published on a platform.
  - There is no emailed password reset; a forgotten password is reset from the operator's own Cloudflare deployment.
references:
  - { kind: doc, role: intent, target: README.md, title: README }
  - { kind: doc, role: intent, target: docs/composer.md, title: Writing and publishing }
  - { kind: doc, role: intent, target: docs/posts.md, title: Posts and Insights }
  - { kind: doc, role: context, target: AGENTS.md, title: Agent instructions }
---

# CogSend

CogSend is a social scheduler a person runs on their own Cloudflare account.
Its one Admin connects their Mastodon, Bluesky, LinkedIn, Threads and X
accounts, writes a post as a thread of cards with images and alt text, tailors
a version per platform where one platform needs different words, and then
publishes it at once or schedules it. Each account a post goes to gets its own
delivery with its own result, so a post can publish on four accounts and fail
on a fifth; temporary failures retry on their own and the rest wait in Posts
to be retried, rescheduled or cancelled. Insights shows how publishing has
gone over seven, thirty or ninety days. Beside the web app, a personal API key
lets scripts and AI agents (through an MCP server) read, draft, schedule and
publish, and a tick, the Worker's own cron or any external caller, publishes
whatever has come due.

## Intent

"Write a draft, customize it per platform, then publish it now or schedule
it." CogSend exists because hosted schedulers charge per channel and keep a
person's posts and tokens on their servers: here the data stays in the
operator's own database and bucket, posts go out through their own API
credentials (or through Zernio when they would rather not register developer
apps), and there is no subscription to keep paying. It is single-tenant and
secure by default, with encrypted credentials and two-factor authentication on
the admin account.
