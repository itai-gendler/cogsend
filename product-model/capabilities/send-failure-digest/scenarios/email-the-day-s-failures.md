---
kind: primary
routes:
  web: Web
steps:
  - text: A tick finishes, the Instance has a failure email and the last digest was more than a day ago
    kind: condition
    unattended: true
    entities:
      - { entity: instance, effect: reads, facts: [Failure email, Last failure digest] }
    contexts: { web: { place: web::app::dashboard } }
  - text: The Product emails the posts that failed since the last digest, each with its account and reason, and records when it sent it
    kind: product
    entities:
      - { entity: delivery, effect: reads, facts: [Error] }
      - { entity: account, effect: reads, facts: [Platform, Handle] }
      - { entity: post, effect: reads, facts: [Title, Text] }
      - { entity: instance, effect: changes, facts: [Last failure digest] }
    contexts: { web: { place: web::app::dashboard } }
---

# Email the day's failures

## Trigger

Posts failed while the Admin was away.

## Outcome

The Admin learns the next morning which posts failed and why.

## Edge cases

- At most twenty failures are listed, with a count of the rest.
- Deliveries still retrying on their own are not emailed.
- A failed send is not repeated until the next day.
