## Draft a new scene

```sh
/draft_scene scene_id=12 focus="Kai confronts sister in scrapyard"
```

→ Produces `workspace/agent-draft-12.md`

## Critique it

```sh
/critique_scene scene_id=12
```

→ Produces:

- `workspace/critique-12.md` (analysis, comments, suggestions)
- `fix_spec-$scene_id.md` (the actionable patch plan)

## Revise

```sh
/revise_scene scene_id=12
```

→ Produces:

- `agent-draft-rev-12.md` (polished prose)
- `editor_log-12.md` (bullet record of changes)

## Archive

```sh
/archive_session project=my-story include_changelog=true include_index=true
```

→ Produces:

- `projects/my-story/author-notes/session-notes-2025-09-19.md`
- `projects/my-story/CHANGELOG.md` // Appends
