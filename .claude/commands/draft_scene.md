---
name: draft_scene
description: |
  Generate a first prose draft for one scene using the writer-author subagent.
  Loads relevant packets (MRUs, Scene/Sequel, Story Genius scenes) and applies constraints from story-bible.json.
arguments:
  - name: scene_id
    description: Scene identifier or card number.
    required: true
  - name: focus
    description: Optional note on POV, mood, or beats to emphasise.
    required: false
  - name: packets
    description: Comma-separated packet IDs (default: swain-mru, swain-scenes-sequels, story-genius-scenes-3).
    required: false
output:
  files:
    - workspace/agent-draft-$scene_id.md
token_budget: 1200
---

**Steps**

1. Load the scene card (`workspace/scene-cards/scene-$scene_id.md`).
2. Load selected packets.
3. Write ≤1200 words of prose respecting MRUs, Third Rail, and scene goals.
4. Save as `agent-draft-$scene_id.md`.
