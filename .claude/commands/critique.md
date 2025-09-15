---
name: critique
description: Provide a short critique for an outline or draft.
arguments:
  - name: file
    description: Path to the artifact being reviewed.
    required: true
---

Evaluate `$file`:

1. Check structure, clarity, and voice.
2. Note continuity issues or style drift.
3. Output ≤200 words in bullets to `workspace/critiques/<basename>-critique.md`.
