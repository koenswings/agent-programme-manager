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

## GitHub Push & PR

`gh` is not available in the sandbox. Use `git` + `curl` with `GITHUB_TOKEN` from `.env`.

### Push a branch
```bash
source .env
git remote set-url origin https://koenswings:${GITHUB_TOKEN}@github.com/koenswings/agent-programme-manager.git
git push origin BRANCH_NAME
git remote set-url origin https://github.com/koenswings/agent-programme-manager.git
```

### Open a PR
```bash
source .env
curl -s -X POST "https://api.github.com/repos/koenswings/agent-programme-manager/pulls" \
  -H "Authorization: token ${GITHUB_TOKEN}" \
  -H "Content-Type: application/json" \
  -d "{
    \"title\": \"PR TITLE\",
    \"head\": \"BRANCH_NAME\",
    \"base\": \"main\",
    \"body\": \"PR description\"
  }" | python3 -c "import sys,json; print(json.load(sys.stdin).get('html_url','error'))"
```

`GITHUB_TOKEN` must be present in `.env` (gitignored, never committed).
