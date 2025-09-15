---
name: fix
description: Create a numbered patch plan based on the latest critique.
arguments:
  - name: file
    description: Path to the draft or outline to fix.
    required: true
---

Generate `fix_spec.md` for `$file`:

1. Read the associated critique.
2. List 3–8 numbered changes.
3. Keep each item single-purpose and clear.
