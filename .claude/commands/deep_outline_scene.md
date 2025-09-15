---
name: deep_outline_scene
description: Expand one scene card into a full, beat-by-beat outline including turning points, emotional shifts, and sequel structure.
arguments:
  - name: id
    description: The scene-card ID to deepen (e.g., S07).
    required: true
  - name: format
    description: Output format: "md" (default) or "yaml"
    type: string
    required: false
---

Deep outline the scene with ID **$id**:

1. Load the scene card from `workspace/outlines/scenes/scene-cards-*.md`.
2. Extract external spine (goal, conflict, disaster, turning points) and internal “Third Rail” elements.
3. Break down the scene into a **beat sheet**:
   - **Opening Hook** – Set up character, stakes, and setting; introduce goal.
   - **Inciting Beat** – First external obstacle arises.
   - **Progressive Conflicts** – 2–3 pins that escalate challenge.
   - **Midpoint Twist/Turning Point** – Major complication altering stakes or strategy.
   - **Pre-Climax Crisis** – Highest tension, often marked by character’s greatest misbelief pressure.
   - **Climax (Disaster)** – Confrontation of goal with failure or complication (“Yes, but…” or “No, and…”).
   - **Internal Moment** – Stark emotional reaction or realization.
   - **Sequel Beats**:
     - **Reaction** – Emotional reflection of disaster (physiology, mood).
     - **Dilemma** – 2–3 tough choices or paths forward.
     - **Decision** – What the POV character decides, establishing next goal.
4. For each beat, note:
   - Scene purpose (why it’s here).
   - Internal stakes (what misbelief is pressed; what’s being learned/faulted).
   - Emotional tone or hook.
5. Save as: `workspace/outlines/scenes/scene-detail-$id.md`
