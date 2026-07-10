---
name: setup-meirlabs-skills
description: Configure this repo for the meirlabs skills - ticket destination, design context, deploy posture, analytics, and Supabase mapping. Run once before first use.
disable-model-invocation: true
---
# public variant, safe to publish

# Setup meirlabs skills

Run this once after installing the skills (`npx skills@latest add meirlabs/skills`)
to point the rest of the set at your repo instead of hard-coding answers. The config
is an `## Agent skills` block in this repo's `CLAUDE.md` (or `AGENTS.md`) pointing at
`docs/agents/*.md` files seeded from this skill's `templates/`. Today `bookmark-triage`,
`drain-tickets`, and `deploy` resolve their behavior through that block; the other
sections (design context, analytics, Supabase) are written for skills that will be
wired to read them, and are harmless until then. One skill set serves any tracker,
design context, or deploy posture.

Prompt-driven, not a script. Explore, present what you found, confirm, then write.

## 1. Explore

Read the repo before asking anything. Every section exploration settles is a question
you skip.

- `git remote -v` - is this a GitHub repo, and which one? Names the deploy target and
  the GitHub-Issues option.
- `CLAUDE.md` and `AGENTS.md` at the repo root - does either exist, and is there already
  an `## Agent skills` block? Decides which file you write and whether you update in place.
- `docs/agents/` - did a prior run already seed these files?
- `package.json` - `posthog-js` present (analytics likely already wired), `@supabase/*`
  present (needs a Supabase mapping row).
- App shape - an `app/` or `src/app/` with dashboard/table/form routes reads as SaaS; a
  marketing home, pricing, about, blog reads as landing. Propose what you find; do not
  guess silently.

Summarize present vs missing before you ask.

## 2. Ask

ONE batched `AskUserQuestion` call (max 4 questions), covering only the sections
exploration left unsettled. Lead every question with the recommended option and suffix
it `(Recommended)` so the user can accept in one tap. Look facts up; never ask the user
something the repo already answered.

- **Tickets**: local markdown in `ops/tickets/` (Recommended) / GitHub Issues / your
  issue tracker (Linear, Jira, etc.: name it and the agent wires it)
- **Design context**: landing / saas / both - propose what exploration found as the
  recommended one
- **Deploy posture**: confirm-before-prod (Recommended) / ship-it-means-prod
- **Analytics**: standard PostHog setup (Recommended) / skip - if `posthog-js` is already
  in `package.json`, recommend and note it looks wired

Drop any question whose section is already settled (e.g. analytics when `posthog-js` is
absent and the repo has no analytics need, or design context when the app shape is
unambiguous and the user has nothing to choose).

## 3. Confirm

Show the draft `## Agent skills` block plus the contents of each `docs/agents/*.md` file
you are about to write. Let the user edit before anything lands.

## 4. Write

**Pick the file:** edit `CLAUDE.md` if it exists, else `AGENTS.md` if it exists. If
neither exists, ask which to create - do not pick for them. Never create the one kind
when the other already exists.

If an `## Agent skills` block already exists, update it in place; do not append a
duplicate and do not touch the surrounding sections.

The block:

```markdown
## Agent skills

### Tickets

[one line: where tickets go]. See `docs/agents/tickets.md`.

### Design context

[one line: landing / saas / both]. See `docs/agents/design-context.md`.

### Deploy

[one line: confirm-before-prod or ship-it]. See `docs/agents/deploy.md`.

### Analytics

[one line: PostHog standard or skipped]. See `docs/agents/analytics.md`.

### Supabase

[one line: project ref, or "none"]. See `docs/agents/supabase.md`.
```

Seed each `docs/agents/*.md` from this skill's `templates/`:

- `templates/tickets.md`
- `templates/design-context.md`
- `templates/deploy.md`
- `templates/analytics.md`
- `templates/supabase.md` (always seed it; fill the project ref row when `@supabase/*`
  is present, otherwise write "This repo has no Supabase project." per the template, so
  the block's pointer never dangles)

Copy the template, then edit it down to the chosen option. Never overwrite an existing
`docs/agents/*.md` without showing the diff first.

## 5. Done

Tell the user setup is complete and which skills now read from these files. The
`docs/agents/*.md` files are hand-editable later; re-run this skill only to switch a
whole section or start over.
