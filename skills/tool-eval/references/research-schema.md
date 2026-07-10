# Research schema

Used by Phase 1 (research sweep). Give each research agent this schema verbatim plus
the `CONTEXT` block from Phase 0.

## Per-candidate agent (one sonnet agent per candidate)

Instruct the agent to fetch the OFFICIAL pricing page and docs, never rely on memory,
be specifically skeptical about tier-gating of the buyer's hard requirements, and
lower confidence whenever a fact can't be verified from an official source.

```yaml
candidate: <name>
pricing:
  - plan: <name>
    price: <amount + billing period>
    caps: <usage limits, seats, sends, requests, whatever the buyer's usage shape needs>
hard_requirement_gating:
  # one entry per hard requirement from CONTEXT
  - requirement: <e.g. "API + webhooks">
    gated_at_tier: <plan name or "all tiers">
    source_url: <official docs/pricing URL>
ecosystem_infra: <integrations, API surface, self-host option, notable infra choices>
community_reputation:
  summary: <what practitioners say>
  sources: [<urls>]
company_trajectory: <funding, direction, layoffs, notable pivots, last ~18mo>
lock_in_migration_pain: <what it costs to leave, export options, proprietary formats>
fit_notes: <how this candidate maps to CONTEXT's ranked priorities, one line per priority>
source_urls: [<every URL cited above>]
confidence: <high | medium | low, and why>
```

## Cross-cutting sweep agents (2-3 sonnet agents)

These see the whole candidate set, not one candidate. Assign each a distinct lens so
they don't duplicate the per-candidate work:

1. **Practitioner sentiment at the buyer's target scale.** What do people actually
   running this workload use, not what's generically popular. Reddit, X, comparison
   posts from the last ~18 months. Flag if sentiment splits by scale (great at 10
   users, bad at 10,000).
2. **Landscape shifts that change the game.** Platform crackdowns, regulation,
   pricing-model trends, category consolidation. Anything that would make a
   currently-good pick age badly within the buyer's planning horizon.
3. **Unit economics at 2-3 scale points relevant to the buyer.** Cost per unit
   (per seat, per send, per request, whatever fits) at the buyer's current scale, a
   plausible near-term scale, and a stretch scale. This is what feeds the memo's
   growth-path section.

Each sweep agent returns findings as prose with inline source URLs, not the
per-candidate schema, since it's cross-cutting rather than per-candidate.
