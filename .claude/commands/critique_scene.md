---
name: critique_scene
description: |
  Provide a structured critique of an existing scene draft and (optionally) generate a numbered fix spec.
arguments:
  - name: scene_id
    description: Scene identifier or card number.
    required: true
  - name: packets
    description: Packets for style/structure (default: story-genius-scenes-3, story-genius-troubleshooting-4).
    required: false
  - name: include_fix_spec
    description: "true/false — if true, create fix_spec-$scene_id.md with numbered revision plan"
    required: false
    default: true
output:
  files:
    - workspace/critique-$scene_id.md
    - workspace/fix_specs/fix_spec-$scene_id.md
token_budget: 500
---

**Steps**

1. Read `agent-draft-$scene_id.md`.
2. Load chosen packets (Scene craft, Troubleshooting).
3. Write ≤500 words of critique → `workspace/critique-$scene_id.md`.
4. If `include_fix_spec` is true:
   - Create `workspace/fix_specs/fix_spec-$scene_id.md`:
     - 5–7 numbered steps for revision, referencing critique points.
