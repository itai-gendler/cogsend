---
kind: alternative
routes:
  web: Web
steps:
  - text: A due delivery is sent on a tick and the platform answers with a rate limit or times out
    kind: condition
    unattended: true
    entities:
      - { entity: delivery, effect: reads, facts: [Scheduled time] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product keeps the reason and sets the next attempt one minute later, doubling the wait each time up to thirty minutes
    kind: product
    entities:
      - { entity: delivery, effect: changes, from: Scheduled, to: Retrying, facts: [Error, Attempts, Scheduled time] }
    contexts: { web: { place: web::app::posts } }
  - text: A later tick sends it again and the platform accepts it
    kind: product
    entities:
      - { entity: delivery, effect: changes, from: Retrying, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Scheduled, to: Published, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Retry after a temporary failure

## Trigger

A platform is briefly unavailable when a post is due.

## Outcome

The post goes out once the platform recovers, without the Admin doing anything.
