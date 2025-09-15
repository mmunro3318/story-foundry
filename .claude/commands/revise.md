---
name: revise
description: Apply a fix_spec to produce a new revision of a draft.
arguments:
  - name: spec
    description: Path to the fix_spec.md file.
    required: true
---

Implement the patch plan from `$spec`:

1. Open the corresponding draft.
2. Apply fixes, preserving author voice.
3. Save as `agent-draft-rev.md` in the same folder.
