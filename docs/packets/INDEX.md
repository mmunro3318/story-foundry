# 📚 Packet Index

A catalog of all theory/reference **packets** for story development.  
(Located in `docs/packets/`)

> Agents don’t read this file; it’s for humans to browse and copy paths into `references:` blocks or `/command --packets`.

---

## Truby – _Anatomy of Story_

| File                  | Description                         | Last Updated |
| --------------------- | ----------------------------------- | ------------ |
| `truby-22-steps-1.md` | Seven Key Steps (1–7)               | 2025-09-18   |
| `truby-22-steps-2.md` | Middle Escalation (8–15)            | 2025-09-18   |
| `truby-22-steps-3.md` | Resolution & Moral Decision (16–22) | 2025-09-18   |

---

## Swain – _Scene & Structure_

| File                      | Description                                                                           | Last Updated |
| ------------------------- | ------------------------------------------------------------------------------------- | ------------ |
| `swain-scenes-sequels.md` | Scene / Sequel framework (Goal → Conflict → Disaster → Reaction → Dilemma → Decision) | 2025-09-19   |
| `swain-mru.md`            | Motivation–Reaction Units (micro beat cause/effect)                                   | 2025-09-19   |
| `swain-scaling-pacing.md` | Scaling & pacing with scenes & sequels                                                | 2025-09-19   |

---

## Story Genius – _Lisa Cron_

| File                                | Description                         | Last Updated |
| ----------------------------------- | ----------------------------------- | ------------ |
| `story-genius-core-1.md`            | Core philosophy & 16-step system    | 2025-09-19   |
| `story-genius-misbelief-2.md`       | Misbelief & backstory scenes        | 2025-09-19   |
| `story-genius-scenes-3.md`          | Scene cards & Third Rail            | 2025-09-19   |
| `story-genius-troubleshooting-4.md` | Troubleshooting & genre adaptations | 2025-09-19   |

---

## Foolscap – _Story Grid_

| File          | Description                                                                      | Last Updated |
| ------------- | -------------------------------------------------------------------------------- | ------------ |
| `foolscap.md` | One-page global story diagnostic (Beginning Hook → Middle Build → Ending Payoff) | 2025-09-19   |

---

### How to Use

- Include only the needed packets in a subagent’s `references:` block.
- For commands, pass packets by filename (minus `.md`) with `--packets`.
- Keep packets under ~1k words; update **Last Updated** when revised.
- If a packet becomes obsolete, move it to `docs/packets/archive/` and note its status here.

---

✅ Workflow for Maintaining

1. Every time you add/edit a packet, update INDEX.md.

2. If a packet becomes obsolete, move it to docs/packets/archive/ and note in the index.

3. Keep INDEX.md short — just enough info to help humans navigate.
