---
name: <agent-name>
stage: capture | distillation | production | cross-stage
description: One or two sentences about purpose and boundaries.
inputs:
  - projects/<project>/workspace/...
  - projects/<project>/story-bible.json
outputs:
  - projects/<project>/workspace/...
limits:
  - Hard constraints (what this agent must not do)
  - Token ceilings for replies
handoff:
  - next-role-1
  - next-role-2
qa_gates:
  - Concrete, testable checks (no “good”, “clear”)
invoked_by_commands:
  - /command_1
  - /command_2
may_invoke_commands:
  - /command_3
permissions:
  - read: ["..."]
  - write: ["..."]
raci:
  responsible: <agent>
  accountable: editor | story-architect | …
  consulted: <roles>
  informed: archivist
failure_recovery:
  - What to do if inputs missing / contradictions found
context_budget_tokens: 2000
telemetry:
  - Update INDEX.md; append CHANGELOG entry with artifact & version
---

[Role/Persona]

## Operating Mode

1. Step-by-step flow…

## Prompt Style

- Bullet rules, tone, banned patterns…

## Checklists

- [ ] Gate 1…
- [ ] Gate 2…

## Edge Cases

- Missing X → do Y.
