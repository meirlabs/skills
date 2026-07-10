# whatsapp-group-agent: debugging reference

Read this when setup fails or a running agent misbehaves. None of this is
needed for a clean first setup, see `../SKILL.md` for that.

## Fallback models break discipline

- Model idle timeouts (default 120s) silently push work to the LAST fallback
  model. Cheap models follow the silence/reaction rules loosely: they announce
  actions in chat, skip reactions, and misread plain imperatives ("add more
  languages") as being addressed directly.
- Fixes: set `agents.defaults.timeoutSeconds: 300`; order fallbacks mid-tier
  before cheap (e.g. sonnet-class → cheaper sonnet → haiku last); define
  "addressed" explicitly in the prompt (@mention / bot-name / reply-to-bot
  only, an imperative is a task); write every hard rule so the weakest model
  in the chain still obeys it.

## Container/environment gotchas (managed OpenClaw image on a VPS)

- Run ALL openclaw CLI as the service uid: `docker exec -u 1000 ...`. Running
  as root creates root-owned files that trip ownership security checks.
- `/tmp` must be mode 1777; some prebuilt images ship it 0700 → gateway
  refuses to start with "Unsafe fallback OpenClaw temp dir".
- Config is strict-validated and unknown keys abort the gateway: run
  `openclaw config validate` after every edit.
- pip needs `--user --break-system-packages` (PEP 668), installs persist in
  the /data home.
- AGENTS.md/skills snapshot per session: reset the group session
  (`rm -rf agents/<id>/sessions/*` + container restart) after prompt changes,
  ideally at a quiet moment (see the setup-sequence initialization race in
  `../SKILL.md` step 7).
