---
name: outline_scenes
description: Generate a batch of scene cards (1–15) using the unified template — either for specified IDs or as new cards from current packets.
arguments:
    - name: ids
      description: Optional list/range of scene IDs to outline (e.g., S07, S10–S12).
      required: false
  - name: count
    description: Number of cards to generate (default 5, max 15).
    type: integer
---

Determine scope:

- If `$ids` provided → fetch those outline entries and create cards for them.
- Else → scan `capture-summary.md`, packets, and current outline for the next logical $count scenes.

Using story packets, current outline, and capture summary:

1. Produce up to $count **scene cards** using `docs/templates/scene-card-template.md`:
   - Fill External Spine (Goal / Conflict / Disaster / Turning Points).
   - Fill Third Rail (desire, misbelief, stakes, realization).
   - Add subplot links & optional sequel beats.
2. Keep cards in order; stop if a natural act break appears before $count.
3. Save as `workspace/outlines/scenes/scene-cards-[timestamp].md`.
