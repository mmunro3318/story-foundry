---
name: story_init
description: |
  Initialize a new story project. Creates a folder under `projects/`, 
  copies the `story-bible.json` template, and sets up core subfolders.
arguments:
  - name: project_name
    description: "Name of the new project (used as folder name)."
    required: true
  - name: include_readme
    description: "true/false — create a blank README.md in the project."
    required: false
    default: true
output:
  files:
    - projects/$project_name/story-bible.json
    - projects/$project_name/README.md
    - projects/$project_name/author-notes/
    - projects/$project_name/content/
    - projects/$project_name/workspace/
token_budget: 300
---

**Steps**

1. Create `projects/$project_name/`.
2. Copy `docs/templates/story-bible.json` → `projects/$project_name/story-bible.json`.
3. Make subfolders:
   - `author-notes/`
   - `content/`
     - `outlines/`
     - `drafts/`
     - `manuscript/`
   - `workspace/`
     - `scene-cards/`
     - `fix_specs/`
4. If `include_readme` is true, add a blank `README.md` to the project root with a header and usage hint.
5. Confirm success and list paths.
