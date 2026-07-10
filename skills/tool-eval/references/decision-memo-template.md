# Decision memo template

Used by Phase 5 (the synthesis agent). Fill every section; do not skip the why-not paragraphs or switch triggers, they are the point of the memo.

```markdown
# <Category> Decision Memo

## 1. TL;DR

**Winner: <candidate>.** **Runner-up: <candidate>.** One paragraph: why the winner beats
the runner-up against the buyer's ranked priorities, and what it lets the buyer do
(start cheap, avoid a migration, etc).

If a candidate that looked planned/likely going in should NOT be bought, say so here
by name with the one disqualifying fact.

## 2. Recommendation in depth

### Buy now (current stage: <scale/usage shape from buyer context>)

**<Plan/tier name, price>.**

Why this tier and not cheaper or pricier: the load-bearing facts that put the floor
and ceiling on tier choice (what's gated below it, what's wasted above it).

### Growth path on the same platform (no migration)

Numbered list of upgrade levers in the order the buyer will hit them, each with:
trigger condition, what it unlocks, price delta. Close with an illustrative
monthly total-cost-of-ownership at 2-3 scale points.

## 3. Scorecard

| Finalist | <Judge lens 1> | <Judge lens 2> | <Judge lens 3> | Notes |
|---|---|---|---|---|
| Winner | x/10 | x/10 | x/10 | |
| Runner-up | x/10 | x/10 | x/10 | |
| ... | | | | |

Where judges disagreed, resolve it explicitly against the buyer's priority order
and say why, don't just print the table.

## 4. Why not the others

One paragraph per eliminated finalist: the specific disqualifying fact or pattern
(not "it was fine but worse").

## 5. Switch triggers

Concrete, checkable conditions under which the runner-up (or a different candidate)
becomes the right call. Not vague ("if needs grow") - tie each to a metric or event
the buyer can actually observe (mailbox count, monthly spend, a feature ships, a
tier's cap is hit).

## 6. Setup plan

Numbered steps to go from decision to live, with costs at each step called out.
```

## Notes for the synthesis agent

- Be decisive. A ranked tie between finalists is a failure mode, resolve it against
  the buyer's #1 priority.
- Every price in the memo must trace to a verified claim from Phase 3, not Phase 1
  research. If Phase 3 corrected a Phase 1 number, use the correction.
- See `outreach/strategy/platform-decision.md` in this repo for a memo written in
  this format end to end.
