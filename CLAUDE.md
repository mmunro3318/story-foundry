# CLAUDE.md – Orchestrator

## Purpose

Coordinate an agentic workflow for writing a novel in VS Code.  
Guide the author through **Capture → Distillation → Production**, managing subagents, reference docs, and project files.

---

## Directory Map

```
# Project Directory Structure

.
├── CLAUDE.md                     # Top-level orchestrator spec
├── README.md                     # Project readme & usage guide
│
├── .claude/                      # Agent & command definitions
│   ├── agents/                   # Subagent specs
│   │   ├── archivist.md
│   │   ├── backstory-expert.md
│   │   ├── continuity-expert.md
│   │   ├── dialogue-expert.md
│   │   ├── editor.md
│   │   ├── plot-expert.md
│   │   ├── scene-architect.md
│   │   ├── story-architect.md
│   │   ├── wildcard-generator.md
│   │   ├── writer-author.md
│   │   └── ... (any others)
│   │
│   └── commands/                 # Slash command templates
│       ├── capture.md
│       ├── outline_story.md
│       ├── outline_scene.md
│       ├── deep_outline_scene.md
│       ├── draft_scene.md
│       ├── critique_scene.md
│       ├── revise_scene.md
│       └── ... (future commands)
│
├── docs/
│   ├── packets/                  # Theory reference packets
│   │   ├── truby-22-steps-1.md
│   │   ├── truby-22-steps-2.md
│   │   ├── truby-22-steps-3.md
│   │   ├── swain-scenes-sequels.md
│   │   ├── swain-mru.md
│   │   ├── swain-scaling-pacing.md
│   │   ├── story-genius-core-1.md
│   │   ├── story-genius-misbelief-2.md
│   │   ├── story-genius-scenes-3.md
│   │   ├── story-genius-troubleshooting-4.md
│   │   └── foolscap.md
│   │
│   └── templates/                # Reusable templates
│       ├── scene-card-template.md
│       ├── story-bible.json
│       └── ... (any future templates)
│
├── workflow/
│   ├── capture/
│   │   └── CLAUDE.md             # Stage-specific spec
│   ├── distillation/
│   │   └── CLAUDE.md
│   └── production/
│       └── CLAUDE.md
│
└── projects/
    └── <project-name>/           # One folder per story
        ├── author-notes/         # Raw input from brainstorming
        │   ├── session-notes-001.md
        │   └── ...
        │
        ├── content/              # Finalised materials
        │   ├── outlines/
        │   │   ├── story-outline.md
        │   │   └── scene-outline-01.md
        │   ├── drafts/
        │   │   ├── scene-01-draft.md
        │   │   └── ...
        │   └── manuscript/
        │       ├── ch01.md
        │       └── ...
        │
        ├── workspace/            # Active work area
        │   ├── capture-summary.md
        │   ├── agent-draft-12.md
        │   ├── critique-12.md
        │   ├── fix_specs/
        │   │   ├── fix_spec-12.md
        │   │   └── ...
        │   ├── scene-cards/
        │   │   ├── card-01.md
        │   │   └── ...
        │   └── ...
        │
        └── story-bible.json      # Canon/voice for this project

```

---

## Reference Docs

- **Anatomy of Story** – John Truby
- **Scene & Structure** – Dwight Swain
- **Story Genius** – Lisa Cron
- **Foolscap Primer** – Story Grid (Shawn Coyne)

> Only the **researcher** loads these fully; other subagents receive briefing digests.

---

## Subagents

| Group              | Agents                                                               | Role                      |
| ------------------ | -------------------------------------------------------------------- | ------------------------- |
| Core Orchestrators | `story-architect`, `scene-architect`, `writer-author`                | Outlines & prose          |
| Craft Experts      | `plot-expert`, `backstory-expert`, `dialogue-expert`, `worldbuilder` | Theory & content          |
| Admin & QA         | `archivist`, `editor`, `continuity-expert`, `researcher`             | Logs, quality gates, refs |
| Idea Engines       | `idea-generator`, `wildcard-generator`                               | Divergent thinking        |

---

## Workflow Stages

### 1️⃣ Capture

- Goal: collect all author ideas / context.
- Agents: archivist, idea-generator, wildcard-generator, backstory-expert, plot-expert.
- Outputs:
  - `author-notes/session-notes-[##].md`
  - `capture-summary.md` (≤300 words)
  - Updates to `story-bible.json` & project README (see `docs/templates/story-bible.json` for template).

### 2️⃣ Distillation

- Goal: transform captured material into **packets** & outlines.
- Agents: story-architect, scene-architect, plot-expert, researcher, editor, archivist.
- Outputs: YAML/JSON packets (Truby, Swain, Story Genius, Foolscap), `structure-map.json`, `full-story-outline.md`, `scene-cards/`.

### 3️⃣ Production

- Goal: draft, revise, and polish prose.
- Agents: writer-author, scene-architect, dialogue-expert, continuity-expert, editor.
- Outputs: `final-scene-draft-[##].md`, `critique.md`, `fix_spec.md`, `editor_log.md`.

---

## Slash Commands (global)

/ingest <path> # Index reference docs
/mode story|scene # Choose outline target
/packet <name> # Run one packet (brief → draft → critique)
/outline start # Build Story-Outline
/outline scene # Build Scene-Outline
/critique <artifact> # Editor QA & notes
/reconcile <draft> <critique> # Merge deltas
/crosswalk update # Sync Truby↔Swain↔SG links
/todo # Create todo-strategy.md
/handoff capture # Pass summary to distillation
/export # Bundle canonical outputs

---

## Project Data Files

### `story-bible.json`

Single source of truth for:

- **voiceSpec** – style comparables, do/don’t
- **canon** – setting, era, tech
- **constraints** – POV, tense, token caps
- **characters** – profiles & arcs
- **settings** – locations, culture, rules
- **plot** – storylines, timeline
  > Only the **archivist** edits this file.

### Workspace

- Packets: `workspace/truby/*.yaml`, `workspace/swain/*.yaml`, etc.
- Drafts & critiques: `workspace/drafts/`, `workspace/critiques/`.

---

## Operating Notes

- Only work inside the project the author initializes.
- Use **briefing digests** (≤900 tokens) to feed theory to craft agents.
- Respect stage boundaries: each `CLAUDE.md` governs its own phase.
- Record every major output in `workspace/INDEX.md` and `CHANGELOG.md`.

---
