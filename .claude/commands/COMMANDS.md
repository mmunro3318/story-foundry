# COMMANDS.md — Slash Command Spec

Documentation/Cheat Sheet of Our Custom Slash Commands

## Purpose

A minimal, deterministic command layer that the orchestrator (you) can interpret inside chat. Each command:

- does **one** thing,
- produces **one** primary artifact (plus an index/changelog update),
- is **idempotent** (safe to re-run; will version-bump instead of clobbering),
- respects **stage boundaries** and agent permissions (e.g., only the archivist edits the story bible).

---

## Global Syntax

**Form**

/<verb> [subverb] [positional_args…] [--flag[=value] …]

**Conventions**

- **verb / subverb**: lowercase, hyphenless (e.g., `/outline start`, `/draft scene`).
- **positions**: angle brackets in docs indicate required args; you type plain values.
- **flags**: optional, `--flag` or `--flag=value`. Quote paths or IDs with spaces.
- **one artifact per command**: writers/editors may create supporting notes, but the command’s _primary_ artifact is singular and named in this spec.

**Return (in chat)**

- A brief confirmation line and the artifact path, e.g.:  
  `✅ Created workspace/truby/designing-principle.yaml (v2)`
- Any errors appear as `❌ <message>` with a suggested fix.

**Provenance header (top of every artifact)**

generated_by: "<command>"
timestamp: "YYYY-MM-DDThh:mmZ"
stage: "capture|distillation|production"
agents_involved: ["researcher","plot-expert", ...]
inputs_used: ["path/to/input1", "path/to/input2"]
version: 2

---

## Valid Packet Names (for `/packet`)

**Truby**: `designing-principle`, `moral-problem`, `dual-need`, `character-web`, `four-corners`, `story-world`, `symbol-web`, `structure-map`  
**Swain**: `swain-gcd-map`, `swain-scene-cards`, `swain-mru-guidelines`  
**StoryGenius**: `sg-misbelief-and-origin`, `sg-why-it-matters`, `sg-driving-questions`  
**Foolscap**: `foolscap-one-pager`

> Packets always land under `projects/<project>/workspace/<theory>/…` with schemas defined in your stage specs.

---

## Global Commands (available in all stages)

### `/ingest <path>`

Index reference docs and make a ≤900-token **briefing digest** available to craft agents.  
**Artifact**: none (log note only).  
**Notes**: Use for `docs/reference/*` or a specific file.

### `/mode story|scene`

Set the current outline target for this session.  
**Artifact**: `workspace/INDEX.md` updated with current mode.

### `/packet <name> [--dry-run]`

Run one packet end-to-end (brief → write → critique).  
**Artifact**: the packet’s canonical file (YAML/JSON/MD).  
**Flags**: `--dry-run` creates the briefing only (no writing).  
**Side effects**: records critique under `workspace/critiques/`.

### `/critique <artifact-path>`

Editor runs QA gates for the given artifact.  
**Artifact**: `workspace/critiques/<name>-critique.md`.

### `/reconcile <draft-path> <critique-path>`

Apply targeted deltas to address the critique.  
**Artifact**: revised draft alongside the original with `-vN` bump.

### `/crosswalk update`

Refresh `workspace/crosswalks/truby-swain-sg.yaml` mappings.  
**Artifact**: updated crosswalk file.

### `/todo`

Emit `workspace/todo-strategy.md` from unresolved `todo:` tags and critiques.

### `/handoff capture`

Signal Capture → Distillation boundary; attaches `capture-summary.md`.  
**Artifact**: none (index update only).

### `/export [what]`

Bundle deliverables for handoff or delivery.  
**Defaults**: `what=project` (outline + packets + summaries).  
**Artifact**: `workspace/exports/<bundle>.zip` (path printed in chat).

---

## Capture Commands

### `/idea`

Spawn **2× idea-generator**; write outputs to `workspace/ideas/…`.  
**Artifact**: `workspace/ideas/ideas-[timestamp].md` (merged list).

### `/wildcard`

Spawn **1× wildcard-generator** for orthogonal options.  
**Artifact**: `workspace/ideas/wildcards-[timestamp].md`.

### `/plot`

Call plot-expert for a premise/goal strategy memo.  
**Artifact**: `workspace/strategy/plot-strategy-[timestamp].md`.

### `/backstory`

Call backstory-expert to surface wounds/ghost/misbelief leads.  
**Artifact**: `workspace/strategy/backstory-brief-[timestamp].md`.

### `/summary`

Create or update `capture-summary.md` (≤300 words).  
**Artifact**: `workspace/capture-summary.md`.

---

## Distillation Commands

### `/outline start`

Assemble **Story-Outline** from canonical packets (Truby 7→22, crosswalks, Foolscap).  
**Artifact**: `workspace/outlines/story/full-story-outline.md`.

### `/outline scene`

Generate **Scene-Outline** and/or scene cards list from Swain packets.  
**Artifact**: `workspace/outlines/scenes/scene-outline-[timestamp].md`.

---

## Production Commands

### `/draft scene <id> [--max=1200]`

Create `agent-draft.md` for scene `<id>` using outline + bible constraints.  
**Artifact**: `workspace/drafts/<id>/agent-draft-v1.md`.  
**Flags**: `--max` overrides `constraints.max_tokens` temporarily.

### `/critique <file>`

(Shared command; in Production it targets prose.)  
**Artifact**: `workspace/drafts/<id>/critique.md` (≤200 words).

### `/fix <file>`

Produce numbered patch plan from the latest critique.  
**Artifact**: `workspace/drafts/<id>/fix_spec.md`.

### `/revise <fix_spec>`

Apply the patch plan to draft.  
**Artifact**: `workspace/drafts/<id>/agent-draft-rev.md`.

### `/merge <rev>`

Promote revision to canonical `final-scene-draft-[##].md` + `editor_log.md`.  
**Artifacts**:

- `content/manuscript/final-scene-draft-[##].md`
- `workspace/drafts/<id>/editor_log.md`  
  **Note**: Archivist performs the actual file move.

### `/export prose`

Bundle finished scenes into a delivery set.  
**Artifact**: `workspace/exports/prose-[timestamp].zip`.

---

## Error Handling (standard)

- `❌ Unknown command` — Show `/help` excerpt with closest matches.
- `❌ Invalid packet name` — Print valid names from **Valid Packet Names**.
- `❌ Missing input` — Specify required file(s) and suggested command to create them.
- `❌ Permission` — E.g., attempts to edit `story-bible.json` without archivist.
- `❌ Stage mismatch` — Command not allowed in current stage; suggest proper command.

**Idempotency**

- Re-runs append `-vN` or timestamped filenames; canonical files are replaced only when an editor/archivist step says so (e.g., `/merge`).

---

## Naming & Paths (deterministic)

- **Packets** → `workspace/<theory>/<packet>.(yaml|json|md)`
- **Briefings** → `workspace/briefings/<packet>.md`
- **Outlines** → `workspace/outlines/{story|scenes}/…`
- **Drafts** → `workspace/drafts/<scene-id>/…`
- **Critiques** → `workspace/critiques/…`
- **Crosswalks** → `workspace/crosswalks/…`
- **Exports** → `workspace/exports/…`

---

## Quick Start (common flows)

**Capture → Distillation**

/idea
/wildcard
/plot
/summary
/handoff capture

**Packet loop (Distillation)**

/packet designing-principle
/packet moral-problem
/packet swain-scene-cards
/critique workspace/swain/scene-cards.yaml
/reconcile workspace/swain/scene-cards.yaml workspace/critiques/scene-cards-critique.md
/outline start
/outline scene

**Drafting loop (Production)**

---

## Security & Permissions

- **Archivist** is the only agent allowed to:

  - modify `story-bible.json` and project `README.md`,
  - move files into `content/` (canonical areas),
  - write `INDEX.md` and `CHANGELOG.md`.

- **Editor** can fail a gate; failing twice requires the story-architect to add a clarifying question to `todo-strategy.md` before further work.

---

## Help

Type `/help` to print this file’s command list summary (or link to it).  
For packet schemas and QA gates, see the stage CLAUDE files and `docs/templates/`.
