---
date_from:
date_to:
tags:
  - Journal
  - Monthly
---

## What went well this month?

> [!tip] Themes of progress across the month
> Synthesize across your weekly journals. Don't just list events, identify the *themes* and *arcs* that defined your month. What moved forward meaningfully? Link to People, Projects, and Areas.

- ...

## What didn't go well this month?

> [!warning] Recurring friction, structural issues, and missed goals
> Look for patterns across weeks. A one-off setback is noise; a repeated theme is signal. What kept showing up as a problem?

- ...

## What were my biggest challenges this month?

> [!info] The tensions that defined this period
> Name 1-3 structural challenges/underlying tensions. What tradeoffs did you face? What constraints shaped your decisions?

- ...

## What did I learn this month?

> [!tip] Insights that will change how you work going forward
> These should be durable lessons, things you now believe or understand differently. Strong candidates for new Techniques in your vault.

- ...

## Monthly Journals

> [!note] All journal entries from this month
> This table auto-populates with all entries within the date range, including meetings, 1:1s, and weekly reflections.

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
  note.team:
    displayName: Team
views:
  - type: table
    name: Journals
    filters:
      and:
        - date >= this.date_from
        - date <= this.date_to
    order:
      - file.name
      - team
      - tags
    sort:
      - property: date
        direction: DESC
    columnSize: {}
```
