# Tickets

Where actionable work for this repo gets filed. `bookmark-triage` and `drain-tickets`
read this file to know where to write; any other skill that says "file a ticket"
should follow it too.

**Destination for this repo: local markdown in `ops/tickets/`.**

Delete the options you did not pick.

## Local markdown (default)

Tickets live as files under `ops/tickets/` in this repo. One file per ticket,
`ops/tickets/<NN>-<slug>.md`, numbered from `01`. A `Status:` line near the top records
state (`open` / `in-progress` / `done`). Good for repos with no external tracker or for
solo work you want in git. Dedupe before creating: skip if an open ticket already
references the same source URL.

## GitHub Issues

Tickets live in this repo's GitHub Issues, created with the `gh` CLI
(`gh issue create --title ... --body ... --label ...`). Use when the work is
code-scoped and belongs next to the PRs that close it. Dedupe before creating: skip if
an open issue already references the same source URL.

## Your issue tracker (Linear, Jira, etc.)

Tickets go to an external tracker you name here. Fill in the details and the agent
wires it:

- Tracker: `<Linear | Jira | Asana | ...>`
- Where to create: `<API endpoint / project or team id / board>`
- Auth: `<how the agent gets the token: an env var it reads, a secret manager, etc.
  Never commit the token to the repo and never print it.>`
- Create the ticket via the tracker's API, set the target project/team, add a category
  label, and set a priority so the backlog stays ranked.
- Dedupe before creating: skip if an open ticket already references the same source URL.
