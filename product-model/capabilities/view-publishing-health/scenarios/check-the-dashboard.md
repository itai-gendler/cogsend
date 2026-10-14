---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens the dashboard
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::dashboard } }
  - text: "The Product shows whether publishing is healthy, from the Instance's last tick and the deliveries stuck or waiting past their time, with the counts of drafts, scheduled and failed posts"
    kind: product
    actor: admin
    entities:
      - { entity: instance, effect: reads, facts: [Last tick] }
      - { entity: delivery, effect: reads, facts: [Scheduled time, Error] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::dashboard } }
---

# Check the dashboard

## Trigger

The Admin signs in.

## Outcome

The Admin sees All systems operational, or which problem needs attention.

## Edge cases

- Failed posts show a banner linking to Posts, Failed.
- Before the first tick the dashboard says scheduled posts are not published yet; a tick older than six hours reads as delayed.
