---
kind: primary
routes:
  web: Web
steps:
  - text: "A tick arrives and a delivery's scheduled time has come"
    kind: condition
    unattended: true
    entities:
      - { entity: delivery, effect: reads, facts: [Scheduled time] }
    contexts: { web: { place: web::app::posts } }
  - text: "The Product records the Instance's last tick and sends the post to that account"
    kind: product
    entities:
      - { entity: instance, effect: changes, facts: [Last tick] }
      - { entity: delivery, effect: changes, from: Scheduled, to: Publishing, facts: [Attempts] }
      - { entity: account, effect: reads, facts: [Credentials] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: The platform accepts it and the Product records where it landed
    kind: product
    entities:
      - { entity: delivery, effect: changes, from: Publishing, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Scheduled, to: Published, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Publish a post at its time

## Trigger

A scheduled post's time comes.

## Outcome

The post is published and shows as Published in Posts.

## Edge cases

- A thread that failed half-way resumes after the cards that went out, so nothing is posted twice.
- Deliveries to an archived account are never attempted.
