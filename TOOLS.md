# TOOLS.md — Marco, Programme Manager

## API Credentials
- `BASE_URL=http://mission-control-backend:8000`
- `AUTH_TOKEN` — load from `.env` in this directory (gitignored, never committed)
- `AGENT_NAME=Marco`
- `AGENT_ID=c1aeb3f8-a258-448f-afcb-f518bdc47bca`
- `BOARD_ID=3f1be9c8-87e7-4a5d-9d3b-99756c35e3a9`
- `WORKSPACE_ROOT=/home/node/workspace`
- `WORKSPACE_PATH=/home/node/workspace/agents/agent-programme-manager`
- Required tools: `curl`, `jq`

## Environment

- **Programme manager repo:** `/home/node/workspace/agents/agent-programme-manager`
- **Org root:** `/home/node/workspace/` (CONTEXT.md, BACKLOG.md, proposals/, etc.)
- **Field reports:** `/home/node/workspace/agents/agent-programme-manager/field-reports/`

See the **mc-api** shared skill for OpenAPI refresh, discovery policy, and usage examples:
`/home/node/workspace/skills/mc-api/SKILL.md`
