# Capture Stage – CLAUDE.md

## Purpose

Guide brainstorming and information-gathering for a novel project.  
Draw out the author’s ideas, record them, and prepare materials for Distillation.

---

## Inputs

- Author prompts, notes, or free-form “info dumps”.
- Files in `projects/<project>/author-notes/`.
- Optional reference digests prepared by **researcher** (e.g., Truby, Swain, Story Genius).

## Outputs

- `author-notes/session-notes-[##].md` (verbatim record via archivist)
- `capture-summary.md` (≤300 words: key takeaways + next-step outline plan)
- Updates to `story-bible.json` and `README.md` (archivist only)

---

## Subagents

| Role                   | Purpose                                                           |
| ---------------------- | ----------------------------------------------------------------- |
| **archivist**          | Log session text; update bible & README                           |
| **idea-generator**     | Generate incremental ideas                                        |
| **wildcard-generator** | Offer orthogonal / unexpected options                             |
| **backstory-expert**   | Help surface formative events & misbeliefs (Truby / Story Genius) |
| **plot-expert**        | Identify structural hooks & gaps                                  |

> _Other craft agents (worldbuilder, dialogue-expert, etc.) may be invoked if the author requests specialised brainstorming._

---

## Phases

### 1️⃣ Intake

- Primary stance: **listen and record**.
- Encourage uninterrupted info-dump from author.
- Archivist mirrors content to `session-notes`.
- Researcher may prep quick digests if theory prompts are needed.

### 2️⃣ Ideate

- When author wants exploration or feedback:
  - Run 2× `idea-generator` + 1× `wildcard-generator` in parallel; keep results in `workspace/`.
  - Use `plot-expert` for premise/goal clarity or structural needs.
  - Call `backstory-expert` for wounds, ghosts, or misbelief discovery.

> These phases can alternate fluidly — follow author intent.

---

## Actions & Handoff

1. Keep a lightweight log of subagent suggestions in `workspace/`.
2. At session end:
   - Archivist finalises session-notes.
   - Archivist updates `story-bible.json` and project README (if needed).
   - Summarise main findings and recommended outline focus in `capture-summary.md`.
3. Signal readiness for Distillation with:

   /handoff capture

### Slash Commands

/ingest <path> # Load any supporting docs (optional)
/idea # Spawn idea-generators
/wildcard # Spawn wildcard-generator
/plot # Call plot-expert for strategy memo
/backstory # Call backstory-expert
/summary # Produce capture-summary.md
/handoff capture # Pass work to distillation stage

---

## Notes

- Respect project boundaries: never read notes from a different project unless author requests.
- Keep prose inside `session-notes` exactly as the author gave it; do not edit voice or style.
- Keep `capture-summary.md` concise and action-oriented:
  - highlight strongest concepts
  - list unknowns / gaps
  - suggest which packet(s) Distillation should begin with.
