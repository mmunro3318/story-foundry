---
name: packet
description: Run a story packet end-to-end: briefing → write → critique.
arguments:
  - name: name
    description: Packet identifier (e.g., designing-principle, swain-scene-cards).
    required: true
  - name: dry-run
    description: If true, only create the briefing without writing.
    type: boolean
---

Execute the story packet named **$name**:

1. Researcher: prepare ≤900-token digest from references.
2. Writer: draft the packet artifact.
3. Editor: run QA; save critique alongside.
4. If not `dry-run`, promote artifact into `workspace/<theory>/`.
5. Version bump if a prior file exists.
