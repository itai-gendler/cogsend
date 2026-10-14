---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens Posts and picks a tab
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: "The Product lists that tab's posts with their counts, each card showing its accounts, its text and when it will publish, published or was last edited"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text, Last edited] }
      - { entity: delivery, effect: reads, facts: [Scheduled time, Link] }
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { web: { place: web::app::posts } }
---

# Review posts by state

## Trigger

The Admin wants to see what is coming up or what went out.

## Outcome

The Admin sees the posts in that state and where each one stands per account.

## Decision points

### Narrowing

Does the Admin narrow the list?

- They pick one account under All accounts → only posts going to that account are listed
- They type in the search box → only posts whose text matches are listed
- Neither → every post in the tab is listed

## Edge cases

- Times show in the Admin's own time zone with how far away they are.
- The tab, account and search stay in the address, so reloading or coming back from editing keeps them.
