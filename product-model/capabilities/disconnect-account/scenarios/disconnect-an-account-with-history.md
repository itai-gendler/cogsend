---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin chooses Disconnect on an account
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { web: { place: web::app::accounts } }
  - text: "The Product's confirmation says how many scheduled posts will go, how many drafts return and how many published posts stay"
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Admin confirms
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product removes its unpublished deliveries and returns posts left with nothing to send to Drafts
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: removes, from: Scheduled }
      - { entity: post, effect: changes, from: Scheduled, to: Draft, facts: [] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product archives the account, dropping its credentials and keeping its published history
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: changes, from: Active, to: Archived, facts: [Credentials] }
    contexts: { web: { place: web::app::accounts } }
---

# Disconnect an account with history

## Trigger

The Admin no longer wants to post to an account.

## Outcome

Nothing more goes to it; what it published stays in Posts and Insights, marked Archived.

## Edge cases

- Disconnecting in CogSend does not remove an account from Zernio.
- Disconnecting twice changes nothing more.
