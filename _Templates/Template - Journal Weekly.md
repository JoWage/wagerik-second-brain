---
date_from:
date_to:
tags:
  - Journal
  - Weekly
---

## What went well this week?

> [!tip] Wins, progress, and positive moments
> Be specific: name the accomplishment, who was involved, and why it mattered. Link to People `[[Name]]`, Projects `[[Project]]`, and Areas `[[Area]]` to build connections across your vault.

- ...

## What didn't go well this week?

> [!warning] Setbacks, friction, and missed targets
> Be honest. Name what happened, why it happened, and what the impact was. This isn't self-criticism, it's pattern recognition.

- ...

## What's my biggest challenge right now?

> [!info] The single most important obstacle
> Zoom out from daily fires. What's the underlying constraint, tension, or gap that, if resolved, would unlock the most progress?

- ...

## What did I learn?

> [!tip] Insights worth carrying forward
> Capture knowledge that changed how you think or work. These are candidates for future Techniques, distilled wisdom from lived experience.

- ...

## Weekly Journals

> [!note] All journal entries from this week
> This table auto-populates with meetings, 1:1s, and other entries within the date range.

```base
filters:
  and:
    - file.inFolder("Journal")
properties:
  file.name:
    displayName: Title
  note.date:
    displayName: Date
  note.date_from:
    displayName: Date From
  note.date_to:
    displayName: Date To
  note.tags:
    displayName: Tags
views:
  - type: table
    name: Journals
    filters:
      and:
        - date >= this.date_from
        - date <= this.date_to
    order:
      - file.name
      - date
      - tags
    sort:
      - property: date
        direction: DESC
      - property: date_from
        direction: DESC
    columnSize:
      file.name: 420

```
