# 📚 Creative Writing Agentic System

> **Purpose:** a full-featured agent ecosystem for outlining and drafting novels in VS Code via Claude Code CLI.

This workspace provides a **three-stage pipeline** — Capture → Distillation → Production — backed by subagents, slash commands, and theory packets.

This is primarily an experiment and learning project for context engineering. I'm using Claude Code CLI as my main scaffolding, but will be adding some docs to direct any AI agent to work within this space. I have very limited usage plans with the various models, so I bounce between Claude Code, Gemini CLI, and Copilot. When brainstorming and writing, I'll want to be able to quickly spin up whatever models I still have usage on and get right into it. I just really like the structure of Claude's subagents setup -- but Gemini won't use agents, but _can_ take the persona. You do _not_ have to use the slash commands. I've included them for future work/experimentation to automate the story generation process for game development. Humans are messier writers, but I want to algorithmatize the process for agents.

I've outlined an example quick start / workflow below, but I'll often chat with Claude or ChatGPT in the browser to get a lot of ideas out, and then dump these in the project author notes. I'll want to add timestamps and tracking so the AI's don't read all of my notes when working unless I direct them to.

I'm a huge fan of the following books on writing, and reference their theory heavily in this project:

- **Anatomy of Story** – John Truby
- **Scene & Structure** – Dwight Swain
- **Story Genius** – Lisa Cron
- **Storygrid** – Story Grid (Shawn Coyne)

---

## 🚀 Quick-Start: From Blank Page to Draft

### Setup

1. **Install \[Claude Code CLI]** and enable the `/.claude` folder.
   - You'll also need to download the VS Code extension

### Workflow

1. **Initialize New Story Project**

   ```bash
   /story_init project_name=my-story include_readme=true
   ```

   > Open the JSON and fill in voice, canon, characters, constraints.

2. **Brainstorm (Capture Stage)**

Use slash commands (e.g., `/idea`, `/outline_scene`, `/draft_scene`) to interact with subagents, or simply engage with Claude through the terminal conversationally.

- Start Claude Code CLI in VS Code.
- Run:
  ```bash
  /capture project=my-story
  ```
- Dump ideas freely; use `/wildcard` or `/idea` if you need prompts.
- When done, let the archivist save notes → `workspace/capture-summary.md`.

3. **Outline (Distillation Stage)**

   - Generate a global plan:
     ```bash
     /outline_story packets=truby-22-steps-1,story-genius-core-1,foolscap
     ```
   - Break into scenes:
     ```bash
     /outline_scene packets=swain-scenes-sequels,story-genius-scenes-3
     ```
   - For deeper work on one card:
     ```bash
     /deep_outline_scene scene_id=5
     ```

4. **Draft & Polish (Production Stage)**
   - Write prose for a scene:
     ```bash
     /draft_scene scene_id=5 focus="Kai confronts sister in scrapyard"
     ```
   - Critique + fix spec:
     ```bash
     /critique_scene scene_id=5
     ```
   - Revise:
     ```bash
     /revise_scene scene_id=5
     ```

✅ At any point, inspect `workspace/` for drafts, critiques, and numbered **fix_specs**.  
Once a scene or outline is approved, promote them with the **archivist** or move it into `content/` → your growing manuscript.

---

## 🗂️ Directory Layout

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

### 📂 How to Use This Project Tree

This layout separates _theory_, _agents_, and _story content_ so humans and AIs stay organised:

- **.claude/** — brains of the system: subagent specs and slash commands.
- **docs/** — static reference material: theory packets and templates (e.g., Story Genius, Truby).
- **workflow/** — per-stage CLAUDE files describing how each step (Capture, Distillation, Production) operates.
- **projects/** — your actual stories:
  - `author-notes/` = raw brainstorming, never edited by AIs.
  - `workspace/` = active files: scene cards, drafts, critiques, fix specs.
  - `content/` = approved outlines, polished drafts, and final manuscript.
  - `story-bible.json` = voice, canon, constraints

> Rule of thumb: _Workspace is for work-in-progress; Content is for sign-off._  
> Packets live in `docs/packets/` — they’re loaded into subagents as reference, not edited mid-session.

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
