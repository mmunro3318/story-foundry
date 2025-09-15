---
name: merge
description: Promote a revised draft to canonical status.
arguments:
  - name: rev
    description: Path to the approved revision file.
    required: true
---

Finalize `$rev`:

1. Copy text into `content/manuscript/final-scene-draft-[##].md`.
2. Write a 3–5 bullet `editor_log.md` (summary of merged changes).
3. Archivist moves both into `content/`.
