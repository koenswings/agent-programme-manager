# Marco — Programme Manager Memory

## Agent Identity
- Name: **Marco** 🌍
- Role: Programme Manager — field coordination, supporter comms, fundraising
- Workspace: `/home/node/workspace/agents/agent-programme-manager/`
- Telegram group: `-5141459717`

## Infrastructure Facts
- MC API: `http://mission-control-backend:8000`
- MC Board ID: `3f1be9c8-87e7-4a5d-9d3b-99756c35e3a9`
- AUTH_TOKEN: in `.env` (board-scoped)
- MC_PLATFORM_TOKEN: in `.env` (admin, for cross-board writes)
- GITHUB_TOKEN: in `.env` (gitignored, never commit)
- GitHub repo: `koenswings/agent-programme-manager`

## Field Contacts
- **Tapiwa**: field coordinator (he/him)
- **Misheck**: local team member; owns Nextcloud activity log
- **Justice**: local team member; leads methodology; suggested curriculum mapping approach
- **Default SSH password on field Pis**: intentional for current Tapiwa upgrade cycle

## Programme Documents (all PRs merged, PDFs committed)
- field/programme.md — visit schedule, goals, role assignments
- field/visit-checklist.md, field/report-template.md, field/attendance-register.md
- field/troubleshooting-guide.md — 8 sections; for Tapiwa on-site
- presentations/kolibri-classroom-setup, kolibri-lessons-and-quizzes
- presentations/nextcloud-user-registration, nextcloud-classroom-use
- presentations/wikipedia-offline (added to fill Week 1–3 gap)
- reference-cards/quick-reference-kolibri, nextcloud, wikipedia
- reference-cards/student-login-guide (fill in WiFi per site before printing)
- README.md

## Key Clarifications (affecting all documents)
- Users access apps via engine-1.local in Chromium — status page showing all running apps
- Clicking a running app name opens it. No direct app URLs.
- Kolibri restart = undock and re-dock the Kolibri disk (not server restart)
- WiFi name: appnet (confirm per site; student login guide uses appnet as default)
- Kolibri admin credentials: admin / admin911! — treat as sensitive; in programme.md Week 1

## Open PRs
- PR #13: feature/new-training-docs (4 new docs — wikipedia presentation, troubleshooting guide, reference cards ×3, student login guide) — open, awaiting review
- PR #19: memory/updates (open, pending merge — contains AGENTS.md updates)

## Open Items
- Confirm actual WiFi name per site with Tapiwa
- Koen to reply to Justice with curriculum feedback response
- Curriculum mapping worksheet (item #5 from proposed docs list) — deferred
- Cycle review template (item #6) — deferred
- programme.pdf: Koen regenerated on Pi after his edits; confirm whether committed

## Cross-Agent Communication
- All cross-agent comms go through Koen (Telegram relay). Do not message agents directly.
- Send "📨 For [Agent]: [message]" in own Telegram group; Koen forwards.
- Atlas reviews external-facing content for factual consistency before CEO sees it
- Content for website: open PRs with files in content-drafts/ for Beacon (site-dev) to implement

## Key Lessons
- Never commit programme.md without verifying it matches current edits — uncommitted changes lost if branch switches
- All outputs are drafts for CEO review — never send, post, or publish autonomously
- md-to-pdf skill at /home/node/workspace/skills/md-to-pdf/SKILL.md — use for PDF generation
