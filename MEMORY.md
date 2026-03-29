# MEMORY.md

Durable facts and decisions only.
No daily logs. No secrets.

## Current Delivery Status

### Goal
Coordinate the IDEA programme — cross-agent planning and delivery health

### Current State
- State: Working
- Last updated: 2026-03-19 20:03 UTC
- What is happening now: 10 tasks loaded into inbox by Koen ~16:29 UTC; awaiting sequencing, assignment, and kickoff direction
- Key constraint/signal: All 10 tasks unassigned; no agents on board yet beyond lead (max_agents=1 on this board)
- Why blocked (if any): Need Koen's direction on priorities and agent provisioning to begin execution
- Next step: Present task inventory to Koen; propose sequencing and agent assignments; await green light

### What Changed Since Last Update
- 2026-03-19 ~16:29 UTC: Koen added 10 tasks across four workstreams: brand/comms, teacher docs, funding, website

### Decisions / Assumptions
- Board rule: require_approval_for_done = true
- max_agents = 1 (lead only on Programme Manager board; workers live on their own boards)

### Evidence (short)
- `GET /healthz` → `{"ok":true}`
- `GET /api/v1/agent/boards/{id}/tasks` → 10 tasks in inbox, all unassigned

### Request Now
- Direction on priority order and which workstream to start first
- Confirm: should I begin creating specialist agents and assigning tasks?

### Success Criteria
- All agents have clear goals; blockers resolved; backlog current

### Stop Condition
- Programme is fully staffed, tasks sequenced, and delivery is flowing


## Operational Model

**Work cycle trigger:** Every work cycle begins with the CEO (Koen) starting it directly. Nothing moves autonomously without a CEO message.

**Standard cycle:**
1. CEO messages an agent with a task instruction
2. Agent shows plan (plan mode always on) → CEO approves or amends
3. Agent executes → produces: PR / design doc / proposal / report
4. Agent creates a review task for one reviewer agent via MC API (once per task iteration)
5. Pi cron detects the `auto-review` tagged task and auto-triggers the reviewer in an isolated session
6. Reviewer reads the artifact, writes a response, marks task done
7. CEO reviews complete output (primary + review) → approves, amends, or rejects

**Creating a review task (auto-review protocol):**
```
POST /api/v1/agent/boards/{reviewer_board_id}/tasks
{
  "title": "Review: [your task title]",
  "description": "Self-contained context. Review question. ⚠ Depth-1 auto-review: do not create further tasks.",
  "status": "inbox",
  "tags": ["auto-review"]
}
```
Create this task once per task iteration, when your primary output is ready for review.
Reviewer board IDs:
- Axle (Engine Dev):        6bddb9d2-c06f-444d-8b18-b517aeaa6aa8
- Pixel (Console Dev):      ac508766-e9e3-48a0-b6a5-54c6ffcdc1a3
- Beacon (Site Dev):        7cc2a1cf-fa22-485f-b842-bb22cb758257
- Veri (Quality Manager):   d0cfa49e-edcb-4a23-832b-c2ae2c99bf67
- Marco (Programme Mgr):    3f1be9c8-87e7-4a5d-9d3b-99756c35e3a9

**Hard rule — if your session was triggered by an `auto-review` task:**
Read the artifact → write your response to the PR / file → mark task done → stop.
Do NOT create any tasks during this session. No exceptions.

**Heartbeat:** External event polling only (e.g. CI failures, grant deadlines, stale PRs). Not for status reporting. Only activated when a specific external event warrants it.

**Standup:** Optional, CEO-triggered via `/standup` command. Not a daily cron. Run at CEO's discretion — weekly at most.

**Output types:**
- **PR** — code/config/doc change on a feature branch; never merge to main yourself; CEO merges
- **Design doc** — approach decision record before implementation; written to `idea/design/`; auto-reviewed by Veri
- **Proposal** — argument for a new backlog item; written to `idea/proposals/`; CEO merges to create MC task
- **Report** — narrative for human consumption (field update, quality summary); committed directly, no PR

## Durable decisions
- 2026-03-01: Bootstrap completed — first session, no prior state. Board empty at launch.
- 2026-03-02: Extended API outage (~21hr, 04:05 UTC Mar 2 – 01:36 UTC Mar 3). Board unreachable all day. No tasks lost (board was empty). Recovered cleanly at ~01:36 UTC Mar 3.

## Reusable playbooks
- (TODO)
## Telegram Channel

You have a **dedicated Telegram group** for direct communication with the CEO.

- **Bot:** @Idea911Bot
- **CEO Telegram ID:** `8320646468`
- **Your group:** IDEA - Marco · **Chat ID:** `-5141459717`
- **How it works:** The OpenClaw gateway binds your group to this agent exclusively via a `peer` filter in `openclaw.json`. Messages in your group go only to you; other agents have their own separate groups.

## Communication Standards

**No markdown tables or ASCII art tables in Telegram.** Both render poorly (Mac desktop / iPhone).
Use the `telegram-table` skill (`/home/node/workspace/skills/telegram-table/`) to render tables as PNG images.
For simple label/value lists, use plain bullets instead.
