# Backend config migration (Phase 1)

This repo now carries `worker/wrangler.repo.toml` as the primary backend config source.

## Current behavior
- Preferred source: `worker/wrangler.repo.toml` committed in repo
- Workflow copies it to `worker/wrangler.toml` before deploy
- Fallback source: GitHub secret `BACKEND_TOML` (kept temporarily for rollback)

## Purpose
This removes the need to re-upload a full TOML file in GitHub Secrets for every config change.

## Temporary rollback path
If `worker/wrangler.toml` is removed, the workflow will still fall back to `BACKEND_TOML`.

## Next phase
- Move sensitive values to proper runtime secrets:
  - `JWT_SECRET`
  - `ADMIN_PASSWORDS`
  - `TELEGRAM_BOT_TOKEN`
- Keep non-sensitive structure in `worker/wrangler.repo.toml`
- After validation, retire `BACKEND_TOML`

## Phase 2 note
- `DEFAULT_DOMAINS` switched from `niubie.de` to `newbie.ma` to match the current primary site/domain.
