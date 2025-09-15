---
name: draft_scene
description: Create a prose draft for a scene based on its outline and story-bible.
arguments:
  - name: id
    description: Scene identifier (e.g., S07).
    required: true
  - name: max
    description: Max tokens for draft (overrides bible constraint).
    type: integer
---

Write a first draft for scene **$id**:

1. Load its outline and voice constraints.
2. Produce prose (≤ $max tokens if provided).
3. Save as `workspace/drafts/$id/agent-draft-v1.md`.
4. Do not critique or revise in this step.
