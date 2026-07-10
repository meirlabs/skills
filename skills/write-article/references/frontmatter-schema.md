# Frontmatter schema (all fields required unless noted)

```yaml
---
title: "How Much Does AI Adoption Actually Cost a Small Business?"
description: "One-sentence meta description. This is the search snippet, make it earn the click."
slug: "how-much-does-ai-adoption-cost"        # MUST match the filename
translationKey: "ai-adoption-cost"            # groups the same article across locales for hreflang
locale: "en"
publishedAt: "2026-07-09"                      # YYYY-MM-DD
updatedAt: "2026-07-09"                        # bump when you materially edit
author: "Meir Rosenschein"
authorUrl: "https://meirlabs.com/about"
ogImage: "/logo.png"
ogImageAlt: "meirlabs logo"
heroImage: "/articles/how-much-does-ai-adoption-cost/hero.png"  # OPTIONAL lead image under the title — most articles omit it (see Images)
heroImageAlt: "A short description of what the hero image shows"  # required ONLY if heroImage is set (build fails otherwise)
heroCaption: "Optional one-line caption under the hero"           # optional
status: "published"                            # "draft" | "published" — draft still routes, but is not indexed
noindex: false
primaryQuestion: "How much does AI adoption cost for a small business?"
answerSummary: "…"                             # the extractable answer — see rules below
tags: ["ai-adoption", "cost", "getting-started"]
stats:                                         # optional; omit entirely if there are no numbers worth surfacing
  - value: "$3k–$5k"
    label: "To automate one simple task, like drafting routine emails"
    icon: "wrench"
sources:                                       # 2–3 real, reputable URLs
  - title: "Anthropic: Claude API pricing"
    url: "https://platform.claude.com/docs/en/about-claude/pricing"
---
```

`primaryQuestion` doesn't render as visible text, it feeds the FAQPage JSON-LD
(`apps/web/lib/article-seo.ts`) and must closely match the H1 title in meaning.
What renders under the H1 is the `answerSummary` TL;DR. Treat both as the most
important lines in the file.

For the full `stats` field spec (icon keys, value formatting, label rules),
see `references/stats-strip.md`.
