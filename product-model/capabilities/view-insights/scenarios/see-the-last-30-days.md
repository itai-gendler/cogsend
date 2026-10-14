---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens Insights and picks 7, 30 or 90 days
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::insights } }
  - text: "The Product records the browser's time zone as the Admin's and counts each day in it"
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Time zone] }
    contexts: { web: { place: web::app::insights } }
  - text: The Product shows what was published and what failed in that period against the one before, the failures by reason and a row per account
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Scheduled time, Error] }
      - { entity: account, effect: reads, facts: [Platform, Handle] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::insights } }
---

# See the last 30 days

## Trigger

The Admin wants to know how posting has gone lately.

## Outcome

The Admin sees the trend, what failed and why, per account.

## Edge cases

- Ninety days are bucketed by week.
- A disconnected account with history is still shown, marked Archived.
