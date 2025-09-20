---
name: archive_session
description: |
  Run the archivist subagent to save session notes, update project CHANGELOG.md, 
  and refresh docs/packets/INDEX.md if new or modified packets exist.
arguments:
  - name: project
    description: Target project folder under `projects/`.
    required: true
  - name: include_index
    description: "true/false — refresh INDEX.md with any new packets."
    required: false
    default: true
  - name: include_changelog
    description: "true/false — append a session summary to project CHANGELOG.md."
    required: false
    default: true
output:
  files:
    - projects/$project/author-notes/session-notes-[timestamp].md
    - projects/$project/CHANGELOG.md
    - docs/packets/INDEX.md
token_budget: 400
---

**Steps**

1. Save the current chat transcript or key points → `author-notes/session-notes-[timestamp].md`.
2. If `include_changelog`:
   - Append a concise entry to `projects/$project/CHANGELOG.md`:
     - Date / time
     - Summary of work done (commands run, packets added, etc.)
3. If `include_index`:
   - Scan `docs/packets/` for new or updated packets.
   - Update `INDEX.md` “Last Updated” or add new rows.
4. Confirm success with a short report in chat.
