# X.com Reading LLM Wiki Initialization Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Initialize a Markdown knowledge base for x.com reading using the LLM Wiki methodology.

**Architecture:** Preserve clipped x.com materials in `raw/`, maintain synthesized knowledge in `wiki/`, and document agent behavior in `AGENTS.md`. Keep the first version lightweight so it works immediately with Obsidian Web Clipper.

**Tech Stack:** Markdown, Obsidian, git.

---

### Task 1: Create Knowledge Base Structure

**Files:**
- Create: `raw/README.md`
- Create: `raw/x/README.md`
- Create: `raw/assets/.gitkeep`
- Create: `wiki/README.md`
- Create: `wiki/sources/README.md`
- Create: `wiki/topics/README.md`
- Create: `wiki/people/README.md`
- Create: `wiki/orgs/README.md`
- Create: `wiki/digests/README.md`
- Create: `wiki/questions/README.md`
- Create: `wiki/lint/README.md`

- [x] **Step 1: Create directories**

Run:

```bash
mkdir -p raw/x raw/assets wiki/sources wiki/topics wiki/people wiki/orgs wiki/digests wiki/questions wiki/lint
```

Expected: directories exist.

- [x] **Step 2: Add README files**

Add concise Markdown explanations for the raw and wiki layers.

- [x] **Step 3: Verify structure**

Run:

```bash
find raw wiki -maxdepth 2 -type d -print
```

Expected: raw and wiki subdirectories are listed.

### Task 2: Add Operating Schema And Navigation

**Files:**
- Create: `AGENTS.md`
- Create: `README.md`
- Create: `index.md`
- Create: `log.md`

- [x] **Step 1: Add project README**

Document the daily workflow: clip to `raw/x/`, ingest with Codex, update `wiki/`, generate digests, run lint.

- [x] **Step 2: Add agent schema**

Document source immutability, ingest/query/digest/lint workflows, naming conventions, and writing style in `AGENTS.md`.

- [x] **Step 3: Initialize index and log**

Create an empty content index and an initial log entry dated `2026-07-05`.

### Task 3: Add Reusable Templates

**Files:**
- Create: `templates/source-note.md`
- Create: `templates/topic-page.md`
- Create: `templates/digest.md`

- [x] **Step 1: Add source note template**

Include metadata, summary, key points, entities, topic links, contradictions, follow-up questions, and updates made.

- [x] **Step 2: Add topic template**

Include summary, current claims, open questions, debates, related people, related organizations, and sources.

- [x] **Step 3: Add digest template**

Include executive summary, main themes, notable sources, people and organizations to watch, and follow-up questions.

### Task 4: Verify Initialization

**Files:**
- Inspect: all Markdown files

- [x] **Step 1: List files**

Run:

```bash
rg --files
```

Expected: initialized files are listed.

- [x] **Step 2: Check git status**

Run:

```bash
git status --short
```

Expected: new files are staged or visible as untracked before commit.

