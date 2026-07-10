# Analytics

Whether this repo sends product analytics, and to where. Written for `posthog-ops`
and the `analytics-wirer` agent to read once they are wired to this config; until
then it documents the decision for any agent working here.

**Analytics for this repo: standard PostHog setup.**

Keep the option you picked.

## Standard PostHog (default)

Wire PostHog: capture on the client using your PostHog project. See the `posthog-ops`
skill for the setup doc, an event naming convention, and the webdriver bot-drop gotcha.
Env vars go in `.env.local` (`NEXT_PUBLIC_POSTHOG_KEY`, `NEXT_PUBLIC_POSTHOG_HOST`); the
`NEXT_PUBLIC_` prefix is intended here since the project key is public by design. Fill
in your own project key and host below:

- Project key: `<NEXT_PUBLIC_POSTHOG_KEY>`
- Host: `<NEXT_PUBLIC_POSTHOG_HOST, e.g. https://us.i.posthog.com>`

If `posthog-js` is already in `package.json`, analytics is likely wired already - confirm
the events fire before adding more.

## Skip

This repo sends no product analytics. Skills that would otherwise add PostHog events
leave it alone.
