# TOOLS.md — Marco, Programme Manager

## API Credentials
- `BASE_URL=http://172.18.0.1:8000`
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

## OpenAPI refresh (run before API-heavy work)

```bash
mkdir -p api
curl -fsS "http://172.18.0.1:8000/openapi.json" -o api/openapi.json
jq -r '
  .paths | to_entries[] as $p
  | $p.value | to_entries[]
  | select((.value.tags // []) | index("agent-lead"))
  | "\(.key|ascii_upcase)\t\($p.key)\t\(.value.operationId // "-")\t\(.value["x-llm-intent"] // "-")\t\(.value["x-when-to-use"] // [] | join(" | "))\t\(.value["x-routing-policy"] // [] | join(" | "))"
' api/openapi.json | sort > api/agent-lead-operations.tsv
```

## API discovery policy
- Use operations tagged `agent-lead`.
- Prefer operations whose `x-llm-intent` and `x-when-to-use` match the current objective.
