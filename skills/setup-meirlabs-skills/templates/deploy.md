# Deploy

Deploy posture for this repo. The `deploy` skill reads this to know whether a bare
"ship it" is allowed to touch production without a checkpoint.

**Posture for this repo: confirm before prod.**

Keep the option you picked.

## Confirm before prod (default)

"Ship it" runs the full gate (typecheck, tests, production build, env check) and then
**stops to confirm** before the prod deploy step. The user has to say go for the
production alias to move. Preview deploys need no confirmation.

## Ship-it means prod

"Ship it" runs the gate and deploys straight to production with no extra confirmation.
Use only for a repo where you have decided every green build is safe to ship live.

## Target

Vercel. If this app depends on a package via a local `file:` path (a shared component
library not published to npm), follow the prebuilt flow in the `deploy` skill (build
locally with `npx vercel build --prod`, upload with
`npx vercel deploy --prebuilt --prod --yes`), never a plain `vercel --prod` and never
`git push`. Otherwise the generic Vercel flow in the `deploy` skill applies.
