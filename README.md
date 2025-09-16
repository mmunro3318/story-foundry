# 📚 Creative Writing Agentic System

> **Purpose:** a full-featured agent ecosystem for outlining and drafting novels in VS Code via Claude Code CLI.

This workspace provides a **three-stage pipeline** — Capture → Distillation → Production — backed by subagents, slash commands, and theory packets.

---

## 🚦 Quick Start

1. **Install \[Claude Code CLI]** and enable the `/.claude` folder.
   - You'll also need to download the VS Code extension
2. Run `/init` in the terminal to choose:

   - Project directory (`projects/<title>`).
   - Stage (`capture`, `distillation`, `production`).

3. Use slash commands (e.g., `/idea`, `/outline_scene`, `/draft_scene`) to interact with subagents, or simply engage with Claude through the terminal conversationally.
4. Final outputs are promoted from `workspace/` to `content/` by the **archivist**.

---

## 🗂️ Directory Layout

```
.claude/
  agents/          # All agent specs (.md)
  commands/        # Slash commands (.md)
docs/
  reference/       # Theory primers
  templates/       # Cards, outlines, etc.
projects/
  <project>/
    author-notes/
    content/       # Canonical outlines, drafts, manuscript
    workspace/     # Active work (cards, drafts, critiques)
CLAUDE.md          # Top-level orchestrator
README.md
```

---

## 🧭 Agent Index

| Agent                  | Stage        | Role                                                  | Key Outputs                                 |
| ---------------------- | ------------ | ----------------------------------------------------- | ------------------------------------------- |
| **story-architect**    | Distillation | Designs global outline from capture-summary + packets | `full-story-outline.md`, `todo-strategy.md` |
| **scene-architect**    | Distillation | Builds scene cards & deep outlines                    | `scene-cards-*.md`, `scene-detail-*.md`     |
| **editor**             | Cross-stage  | Critiques outlines/prose; issues fix specs            | `*-critique.md`, `*-fix.md`                 |
| **writer-author**      | Production   | Drafts polished prose                                 | `agent-draft-v*.md`                         |
| **archivist**          | Cross-stage  | Moves workspace → content; maintains bible/logs       | `INDEX.md`, `CHANGELOG.md`, updated bible   |
| **continuity-expert**  | Production   | Checks IDs, chronology, POV, canon                    | `continuity-report-*.md`                    |
| **dialogue-expert**    | Production   | Reviews or writes dialogue                            | `dialogue-critique.md`, `alt-dialogue.md`   |
| **researcher**         | Cross-stage  | Finds & summarizes theory / factual info              | `research-*.md`                             |
| **plot-expert**        | Capture      | Diagnoses plot & stakes                               | `plot-diagnostic.md`                        |
| **backstory-expert**   | Capture      | Crafts origin & reinforcement scenes                  | `backstory-report.md`                       |
| **idea-generator**     | Capture      | Produces additive, logical ideas                      | `idea-burst-*.md`                           |
| **wildcard-generator** | Capture      | Proposes bold / orthogonal twists                     | `wild-burst-*.md`                           |
| **worldbuilder**       | Capture      | Designs setting, culture, tech/magic                  | `world-notes-*.md`                          |

> **Token/word budgets:** see each agent’s frontmatter (`context_budget_words`, `output_limit_words`).

---

## 💻 Slash Commands

> Each command is a single `.md` in `.claude/commands/`. Run via terminal with `/command_name`.

Core commands:

- **Capture:** `/idea`, `/wildcard`, `/packet backstory`, `/packet world`, `/packet plot`
- **Distillation:** `/outline_start`, `/outline_scene`, `/deep_outline_scene`
- **Production:** `/draft_scene`, `/critique`, `/fix`, `/revise`, `/merge`
- **Utility:** `/summary`, `/research`

> Arguments & options are described in each command file’s YAML header.

---

## 📌 Tips

- Keep **story-bible.json** the single source of truth for voice, canon, and constraints.
- Only the **archivist** edits bible, INDEX, or CHANGELOG.
- Large packets (>3k words) → summarize first with `/research` or `/packet`.

---
