---
name: revise_scene
description: |
  Produce a revised draft of a scene after critique, using fix_spec.md if present.
arguments:
  - name: scene_id
    description: Scene identifier or card number.
    required: true
output:
  files:
    - workspace/agent-draft-rev-$scene_id.md
    - workspace/editor_log-$scene_id.md
token_budget: 1300
---

**Steps**

1. Load `agent-draft-$scene_id.md`, `critique-$scene_id.md`, and (if present) `fix_spec-$scene_id.md`.
2. Integrate critique while preserving voice, MRUs, and structural beats.
3. Write ≤1300 words revised draft → `agent-draft-rev-$scene_id.md`.
4. Log key edits (≤5 bullets) → `editor_log-$scene_id.md`.
