# Production Stage – CLAUDE.md

## Purpose

Transform approved outlines and scene cards into polished prose.  
Manage drafting, critique, and revision of story material while maintaining voice, continuity, and structural intent.

---

## Inputs

- `story-outline.md` or `scene-outline-[##].md` from Distillation
- `story-bible.json` (voice, canon, constraints)
- Packets as needed (Truby step notes, Swain scene cards, SG misbelief data, Foolscap sheet)
- Prior scene drafts or editorial notes

## Outputs

- `final-scene-draft-[##].md` – polished prose for each scene
- `critique.md` – concise editor feedback (≤200 words, bullets)
- `fix_spec.md` – numbered patch plan derived from critique
- `agent-draft-rev.md` – revision implementing fix_spec
- `editor_log.md` – 3–5 bullets describing what merged to canon

---

## Subagents

| Agent                    | Purpose                                               |
| ------------------------ | ----------------------------------------------------- |
| **writer-author**        | Generate prose according to voiceSpec & constraints   |
| **scene-architect**      | Keep beats aligned with scene outline                 |
| **dialogue-expert**      | Shape and polish dialogue passages                    |
| **continuity-expert**    | Check facts & tone against story-bible and prior text |
| **editor**               | Run quality gates; produce critique & editor log      |
| _(opt)_ **worldbuilder** | Ensure physical details / lore stay coherent          |

> Only the **archivist** may commit approved drafts or editor logs to `content/`.

---

## Workflow

### 1️⃣ Draft

- Writer-author composes scene from outline, respecting POV/tense, word caps, tone.
- Scene-architect monitors pacing and beat coverage.

### 2️⃣ Critique

- Editor reviews draft → `critique.md`.
- Continuity-expert flags canon conflicts; dialogue-expert comments on voice.

### 3️⃣ Fix / Revise

- Writer-author prepares `fix_spec.md` (patch plan).
- Apply changes → `agent-draft-rev.md`.
- Editor merges approved revision into canonical `final-scene-draft-[##].md` + `editor_log.md`.

### 4️⃣ Commit

- Archivist moves approved file to `content/manuscript/`.
- Update `INDEX.md` & `CHANGELOG.md`.

---

## Slash Commands (Production)

/draft scene <id> # Create prose for scene
/critique <file> # Editor runs QA & writes critique.md
/fix <file> # Draft numbered patch plan (fix_spec.md)
/revise <fix_spec> # Apply fixes to create agent-draft-rev.md
/merge <rev> # Promote revision → final-scene-draft & editor_log
/export prose # Bundle finished scenes for delivery

---

## QA Gates

- ✅ Scene satisfies outline beats and intended POV/tense.
- ✅ Voice, tone, and style align with `story-bible.json`.
- ✅ Dialogue authentic and purposeful.
- ✅ Continuity: names, world, timeline, stakes all match canon.
- ✅ Word count ≤ `constraints.max_tokens`.
- ✅ Editor_log clearly states what merged.

---

## Notes

- Production never edits the `story-bible.json` except through archivist requests.
- Keep working files (`agent-draft.md`, `critique.md`, `fix_spec.md`, `agent-draft-rev.md`) in `workspace/drafts/` until merged.
- Approved scenes belong in `content/manuscript/` with running numbering or folder by act.
