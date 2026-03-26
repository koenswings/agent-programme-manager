# IDEA Programme Manager

**IDEA — Initiative for Digital Education in Africa** deploys offline computer systems to rural African schools. This repository contains the operational documents, training materials, and reference content produced and maintained by the Programme Manager role.

---

## Repository Structure

```
field/                      Operational documents for the field team
presentations/              Training presentations — Tapiwa uses these in sessions
reference-cards/            One-page handouts for teachers and students
memory/                     Session memory for the Programme Manager agent (Marco)
outputs/                    Session output records
```

---

## Field Documents (`field/`)

Documents used by Tapiwa and Misheck during site visits. All are printable.

| File | Purpose | Audience |
|------|---------|---------|
| `programme.md` | Full programme plan: team roles, 6-week curriculum, visit structure, escalation model, payment | Full team |
| `visit-checklist.md` | Step-by-step checklist for every visit | Tapiwa, Misheck |
| `report-template.md` | Template for the weekly field report | Misheck |
| `attendance-register.md` | Sign-in sheet for teachers and students per visit | Misheck |
| `troubleshooting-guide.md` | On-site technical troubleshooting reference | Tapiwa |

---

## Presentations (`presentations/`)

Training materials Tapiwa uses to deliver sessions at schools. One folder per presentation, each containing a Markdown source and a generated PDF.

| Folder | Used in | Covers |
|--------|---------|--------|
| `kolibri-classroom-setup/` | Week 1 | Creating a class, enrolling students, building a first lesson |
| `kolibri-lessons-and-quizzes/` | Weeks 2–5 | Richer lessons, quizzes, reading progress data; Week 6 curriculum mapping |
| `nextcloud-user-registration/` | Week 1 | Creating teacher and student accounts, class groups |
| `nextcloud-classroom-use/` | Weeks 2–5 | Sharing materials, file drop, collaborative documents, Talk |
| `wikipedia-offline/` | Weeks 1–3 | Accessing offline Wikipedia, searching, using in lessons |

---

## Reference Cards (`reference-cards/`)

Short printable handouts. Teachers keep the quick reference cards on their desks; the student login guide is handed out in Week 3.

| File | Audience |
|------|---------|
| `quick-reference-kolibri.md` | Teachers |
| `quick-reference-nextcloud.md` | Teachers |
| `quick-reference-wikipedia.md` | Teachers |
| `student-login-guide.md` | Students — fill in WiFi name and credentials per site before printing |

---

## Generating PDFs

PDFs are generated from Markdown using a shared skill in the workspace:

```bash
# Single file
bash /home/node/workspace/skills/md-to-pdf/scripts/md-to-pdf.sh <path/to/file.md>

# From agent-engine-dev (alternative)
cd /home/node/workspace/agents/agent-engine-dev
node_modules/.bin/zx script/md-to-pdf.ts <path/to/file.md>
```

PDFs are committed alongside their source `.md` files. After editing any Markdown document, regenerate and commit the PDF before pushing.

---

## How This Repo Is Maintained

This repository is maintained by **Marco**, the IDEA Programme Manager agent. All changes go through pull requests — nothing is committed directly to `main`.

- **Field documents** are updated as the programme evolves
- **Presentations** are reviewed and updated between cycles based on field feedback
- **Reference cards** are updated whenever the system or curriculum changes

The agent's session memory lives in `memory/YYYY-MM-DD.md` files, committed to a long-lived `memory/updates` branch and merged periodically by Koen.
