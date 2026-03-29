# Backend config source of truth

## Current rule
- Non-sensitive backend config source of truth: `worker/wrangler.repo.toml`
- Deployment workflow copies `worker/wrangler.repo.toml` -> `worker/wrangler.toml`
- Sensitive runtime values remain in Cloudflare Worker secrets/bindings

## Sensitive values not stored in repo
- `JWT_SECRET`
- `ADMIN_PASSWORDS`
- `TELEGRAM_BOT_TOKEN`

## Operational rule
- To change non-sensitive backend config, edit `worker/wrangler.repo.toml`
- Do not reintroduce full TOML in GitHub Secrets
- Do not treat Cloudflare Dashboard vars as the primary source for non-sensitive config
