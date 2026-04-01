---
priority:
date_from:
date_to:
tags:
  - Project
last updated:
---

## Objective

> [!info] What is this project trying to achieve?
> State the goal in 1-2 sentences. Be specific about the desired outcome and how you'll know it's done. A good objective answers: *What will be different when this is complete?*

- ...

## Key Results

> [!tip] Measurable outcomes that define success
> List 3-5 concrete, measurable results. Use checkboxes to track completion. Each should be independently verifiable.

- [ ] ...
- [ ] ...
- [ ] ...

## Stakeholders

> [!info] Who is involved and what are their roles?
> Link to People with `[[Name]]`. Note their role in this project (sponsor, contributor, reviewer, etc.)

- ...

## Progress

> [!note] Living record of how this project is evolving
> Update this section regularly. Move older updates under a collapsible heading if the list grows long.

### Current Status

- ...

### Decisions Made

> [!tip] Capture decisions so you don't revisit them
> Record what was decided, when, by whom, and the rationale. This prevents decision fatigue and circular discussions.

- ...

### Blockers

> [!warning] What's preventing progress?
> Be specific: who or what is blocking, what's needed to unblock, and any escalation actions taken.

- ...

## Related Journals

> [!note] Meeting notes and journal entries related to this project
> This table auto-populates with any Journal entry that links back to this Project.

```base
filters:
  and:
    - file.inFolder("Journal")
properties:
  file.name:
    displayName: Title
  note.date:
    displayName: Date
  note.tags:
    displayName: Tags
views:
  - type: table
    name: Related Journals
    filters:
      and:
        - file.hasLink(this.file)
    order:
      - file.name
      - date
      - tags
    sort:
      - property: date
        direction: DESC
    columnSize:
      file.name: 420

```

## See Also

> [!tip] Related links
> Link to related Areas, Techniques, or external resources that support this project.

- ...
