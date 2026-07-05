# X.com Reading LLM Wiki Initialization Design

## Goal

Initialize this repository as a lightweight LLM Wiki for organizing information clipped from x.com with Obsidian Web Clipper.

## Chosen Approach

Use a source-first plus topic-compilation structure. Each clipped x.com item remains as an immutable raw source, while Codex creates structured source notes and updates durable topic, people, organization, digest, and question pages.

## Repository Layers

- `raw/`: original sources, treated as read-only by default.
- `wiki/`: LLM-maintained knowledge layer.
- `templates/`: reusable Markdown page templates.
- `index.md`: content-oriented navigation map.
- `log.md`: append-only chronological activity record.
- `AGENTS.md`: operating schema for future Codex sessions.

## Web Clipper Assumptions

Obsidian Web Clipper saves x.com content into `raw/x/`. Images and attachments are downloaded into `raw/assets/`. The clipped source file remains the source of truth.

## Maintenance Rules

Codex updates `wiki/`, `index.md`, and `log.md` during ingest, query filing, digest generation, and lint passes. Codex does not modify `raw/` unless the user explicitly asks.

## Success Criteria

- The repository has a clear raw/wiki/schema structure.
- A future Codex session can read `AGENTS.md` and perform ingest consistently.
- The user can start clipping x.com content into `raw/x/` immediately.
- The index and log are initialized.

