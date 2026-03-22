# How to Review and Approve a Pull Request

This guide explains how to review and merge a PR (pull request) using either the GitHub website or VS Code.

---

## What is a PR?

A pull request is a proposal to merge changes from one branch into another (usually `main`). You review the diff — what changed — and either approve and merge it, or request changes.

---

## Option A — GitHub Website

### 1. Open the PR

Go to the repository on GitHub. Click the **Pull requests** tab. You'll see the open PR — click it.

### 2. Review the changes

Click the **Files changed** tab. This shows a diff — lines in green were added, lines in red were removed.

For PDFs and binary files, GitHub will just show "Binary file changed" — that's normal.

### 3. Leave a review (optional)

Click **Review changes** (top right of the Files changed view). You can:
- Leave a comment
- Select **Approve** (you're happy with it)
- Select **Request changes** (you want something fixed first)

Then click **Submit review**.

### 4. Merge the PR

Back on the **Conversation** tab, scroll to the bottom. Click **Merge pull request**, then **Confirm merge**.

The branch is merged into `main`. You can delete the feature branch after merging — GitHub offers this immediately.

---

## Option B — VS Code

### Requirements

You need the **GitHub Pull Requests** extension installed. If it's not there, install it from the Extensions panel (`Ctrl+Shift+X`), search "GitHub Pull Requests".

### 1. Open the PR panel

In the left sidebar, click the GitHub icon (looks like a circle with branches). You'll see **Pull Requests** listed. Find the open PR and click it.

### 2. Check out the branch (optional)

Click **Checkout** to switch to the PR branch locally. This lets you run and test the code if needed.

### 3. Review the diff

Click any file in the PR to see the diff inline. Green = added, red = removed.

### 4. Approve and merge

In the PR panel, click **Approve** (thumbs up icon or the button at the top of the PR view). Then click **Merge Pull Request**.

---

## Quick decision guide

| Situation | Action |
|-----------|--------|
| Changes look good | Approve → Merge |
| Something is wrong or unclear | Leave a comment or Request Changes |
| Not sure | Leave a comment asking a question — no need to approve or reject yet |

---

_For this project, PRs are created by Claude Code. Koen reviews and merges._
