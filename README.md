# meirlabs skills

These are the operating skills of meirlabs, a one-person AI product studio. They're not a demo set. They're the actual playbooks I run every day to build, ship, and maintain products: design engineering, deploy checks, security audits, testing standards, content writing rules, and the studio's own principles and go-to-market approach.

## Install

```bash
npx skills@latest add meirlabs/skills
```

Pick the skills you want and which coding agent(s) to install them on.

## Quickstart

1. Install the skills above.
2. Run `/setup-meirlabs-skills` in your agent. It asks a few questions (ticket destination, design context, where docs live) and wires the rest of the skills to your project.

That's it. Skills load themselves when they're relevant, or you can invoke one directly (e.g. `/deploy`, `/security-audit`).

## Skills

<!-- SKILL_TABLE_START -->
| Skill | What it does |
| --- | --- |
| [`aeo`](./skills/aeo/SKILL.md) | Framework and fix recipes for making a site quotable by AI answer engines. |
| [`bookmark-triage`](./skills/bookmark-triage/SKILL.md) | Turn saved X/Twitter bookmarks into Linear tickets automatically — a daily agent loop that reads new bookmarks via the shiori.sh CLI, classifies each against your idea taxonomy, auto-files tickets for the actionable ones, skips noise, and tags processed links so nothing is double-processed. |
| [`deploy`](./skills/deploy/SKILL.md) | Verify and ship a web app to Vercel - typecheck, build, env check, then deploy and report the URL. |
| [`design`](./skills/design/SKILL.md) | The meirlabs design rules for a product's visual layer — brand tokens, fixed structure, and the rules everything defers to. |
| [`loop-engineering`](./skills/loop-engineering/SKILL.md) | Orchestrate a goal end-to-end with fan-out haiku/sonnet/opus subagents, plan first. |
| [`loops`](./skills/loops/SKILL.md) | Design, pilot, and run scheduled watcher-scribe agent loops that escalate to a human, never act. |
| [`organize-idea`](./skills/organize-idea/SKILL.md) | Set up or reorganize a SaaS project into the standard ~/Ideas/ folder structure. |
| [`principles`](./skills/principles/SKILL.md) | The values and 5-Step Process that guide the work. |
| [`review-animations`](./skills/review-animations/SKILL.md) | Reviews animation and motion code against a high craft bar derived from Emil Kowalski's design engineering philosophy, calibrated to the meirlabs design system. |
| [`security-audit`](./skills/security-audit/SKILL.md) | Audit a repo or app for real, exploitable security issues. |
| [`setup-meirlabs-skills`](./skills/setup-meirlabs-skills/SKILL.md) | Configure this repo for the meirlabs skills - ticket destination, design context, deploy posture, analytics, and Supabase mapping. |
| [`testing`](./skills/testing/SKILL.md) | The meirlabs automated-testing standard. |
| [`tool-eval`](./skills/tool-eval/SKILL.md) | Runs a multi-agent evaluation to pick the right tool, platform, or vendor for a long-term decision. |
| [`ui-kit`](./skills/ui-kit/SKILL.md) | Reusable themeable (light & dark) component library at ~/Documents/business/meirlabs/product/ui-kit. |
| [`verify-frontend-change`](./skills/verify-frontend-change/SKILL.md) | Verify any UI change end-to-end before declaring it done — drive the change in a headless Playwright browser (never the user's Chrome), check console and mobile, screenshot before/after. |
| [`voice-profile`](./skills/voice-profile/SKILL.md) | Personal writing voice and communication style guide. |
| [`web-performance`](./skills/web-performance/SKILL.md) | Delivery, perceived-speed, and CI checklist for fast Next.js sites. |
| [`whatsapp-group-agent`](./skills/whatsapp-group-agent/SKILL.md) | Connects an AI agent to an existing WhatsApp group to auto-file tickets, index shared documents, and answer when mentioned. |
| [`write-article`](./skills/write-article/SKILL.md) | Write or edit an SEO/AEO article in apps/web/content/articles - frontmatter schema, answer-engine structure, editorial rules. |
<!-- SKILL_TABLE_END -->

Full docs for each skill: [meirlabs.com/skills](https://meirlabs.com/skills)

## License

MIT, see [LICENSE](./LICENSE).
