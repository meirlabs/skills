# Supabase

This repo's Supabase project, so a skill never runs SQL against the wrong one. Written
for `supabase-ops` to read before any DB read, write, or migration once wired; until
then it documents the mapping for any agent working here. Fill the row; delete it and
write "This repo has no Supabase project." if it does not use Supabase.

## Project mapping

| App | Directory | Supabase project ref | How to reach the DB |
| --- | --- | --- | --- |
| <this app> | <repo dir> | <project-ref> | CLI (linked) or a service-role / `pg` script. NEVER the MCP unless `get_project_url` confirms this ref. |

Find the project ref: it is in this repo's `.env.local` as the subdomain of
`NEXT_PUBLIC_SUPABASE_URL` (`https://<project-ref>.supabase.co`), and in
`supabase/.temp/project-ref` if the CLI is linked.

## The trap

The `supabase` MCP server points at ONE fixed project and is usually NOT this repo's DB.
Before any MCP SQL call meant for this repo's tables, run `mcp__supabase__get_project_url`
and confirm the URL contains the ref above. If it does not, do not use the MCP for this
repo - use the CLI (`supabase db push`) or a `pg` / service-role script. A
`relation does not exist` from the MCP means you queried the wrong project, not that your
write failed. See `supabase-ops` for the full rule.

## When a new app gets a Supabase project

Add its row to the table above the same session, so the mapping never goes stale.
