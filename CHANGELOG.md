


## 2026-06-23 update — endpoint + auth sync
- All snippets now reference the canonical URL
  `https://elitetravelsales.com/api/backend/mcp`. The bare `/mcp`
  path is a 307 redirect to the canonical URL.
- Canonical env var for the agent token is now `TRAVASO_AGENT_TOKEN`.
  Older names (`TRAVASO_TOKEN`, `TRAVASO_API_KEY`) still accepted as
  fallbacks.
- Auth header is `Authorization: Bearer ***  fallback `x-travaso-agent-token: <token>` works for clients that
  can't set `Authorization`.
