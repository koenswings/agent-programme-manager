# TOOLS.md — Programme Manager

## Environment

- **Projects root (host):** `/home/pi/idea/`
- **Projects root (container):** `/home/node/workspace/`
- **This workspace:** `/home/node/workspace/agents/agent-programme-manager`
- **Org root:** `/home/node/workspace/` (CONTEXT.md, BACKLOG.md, proposals/, standups/, etc.)

## Key Paths

- Own workspace: `./`
- Org root coordination files: `../../`
- Proposals: `../../proposals/`
- Engine repo: `../agent-engine-dev/`
- Console repo: `../agent-console-dev/`
- Site repo: `../agent-site-dev/`

## Notes

_(Add observations about workflows, field partner contacts, grant database quirks,
and WhatsApp group management as you discover them.)_

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

Replace `agent-programme-manager` and `BRANCH_NAME` with the actual values for your repo.
`GITHUB_TOKEN` must be present in `.env` (gitignored, never committed).
