---
name: idea-protocol
description: "Structured idea-to-market pipeline for research, pitching, and implementation. Use when: (1) User submits /idea via Discord, (2) Researching new project opportunities, (3) Creating implementation plans, (4) Pitching ideas for approval, (5) Entering locked-in execution mode. Handles full lifecycle from idea capture through research, security checks, planning, pitch, and execution."
---

# Idea Protocol

A structured pipeline for turning ideas into implementation-ready plans.

---

## Phase 1 — Idea Capture

**Trigger:** `/idea <content>` via Discord or any configured channel

**Input accepted:** Written idea, URL, GitHub repo, YouTube video, blog post

**Actions:**
1. Create timestamped entry in `IDEAS.md`
2. Set status to `PENDING`
3. Send Discord confirmation: *"Got it. I've logged your idea and will begin research now"*

**IDEAS.md format:**
```markdown
## [2025-02-28] Agentic AI Video Editor
- Status: PENDING
- Input: "An agentic first AI video editor"
- Research Started: —
- Research Completed: —
- Project Directory: —
- Pitch Sent: —
- Approved: —
```

Add tags: `#tool`, `#saas`, `#automation`, `#ai-agent`, etc.

---

## Phase 2 — Deep Research

Create directory: `projects/[idea-name]/research/`

### Step 1 — Web & Market Research
- Web search for existing products/competitors
- X.com search for discussions
- GitHub search for repos

**GitHub evaluation criteria:**
- Star count (community trust)
- Open vs closed issues ratio (maintenance health)
- Contributor count (longevity)
- Last commit date (active development)
- License compatibility

### Step 2 — Security Checks (MANDATORY)
Before using ANY downloaded code:
- Run static analysis (Semgrep/Bandit)
- Check package manifests for suspicious deps
- Scan for known CVEs
- Verify repo authenticity

If flagged: Discord message explaining issue + wait for approval

### Step 3 — Planning
Create `IMPLEMENTATION_PLAN.md` with:
- **Concept Summary** — What it is, problem solved
- **Technical Architecture** — System structure, components
- **Tools & Stack** — Repos, APIs, MCP servers with links + rationale
- **Step-by-Step Build Plan** — Ordered milestones
- **Who This Benefits** — Target user + pain points
- **Use Cases** — Real-world examples
- **Monetisation Strategy** — SaaS, one-time, API, white-label, etc.
- **What I Need From You** — API keys, payments, domains, creative direction

---

## Phase 3 — The Pitch

Send Discord message with:
- Project name
- 2-3 sentence overview
- Project file path
- What's ready to go
- Request for approval: *"Reply with 'go' to start, or let me know if you'd like changes to the plan."*

**Do NOT begin implementation until approved.**

---

## Phase 4 — Locked In Mode

**Trigger:** User replies "go"

**Actions:**
1. Set `status.json` to `LOCKED_IN`
2. Pause all cron jobs
3. No new idea research
4. Full focus on building

Send Discord: *"Locked in on [project name]. I'll update you at key milestones and when it's done."*

**On completion:** Send final Discord message with path, summary, and review prompt.

---

## Enhancements to Implement

- `/ideastatus` — Query current status, queue, completed
- `/prioritise [idea]` — Bump to top of queue
- Idea scoring on intake (2-min feasibility scan)
- Cost estimation in implementation plan