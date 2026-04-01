---
tags:
  - Technique
last updated:
---

## Context

> [!info] What problem or challenge does this technique address?
> Describe the situation that makes this technique necessary. What pain point, gap, or opportunity does it respond to? Link to relevant Areas with `[[Area Name]]`.

- ...

## Approach

> [!tip] How does this technique work at a high level?
> Explain the strategy or mental model. Which Areas of knowledge are combined? Which Resources informed this approach? This is the *why* behind the process.

- ...

## Process

> [!note] Step-by-step: how to execute this technique
> Number the steps clearly. Someone (including future you) should be able to follow these without additional context.

1. ...
2. ...
3. ...

## Insights

> [!tip] What did you learn from applying this technique?
> Capture lessons learned, surprising findings, edge cases, or refinements. These insights are the distilled value, the reason this Technique exists.

- ...

## Outputs

> [!example] What did this technique produce?
> Link to tangible outputs: blog posts, GitHub repos, presentations, documentation, internal posts, or shared artifacts. This is the *Express* stage of CODE.

- ...

## Linked Areas

> [!note] Knowledge domains connected to this technique
> This table auto-populates with any Area that this Technique links to.

```base
filters:
  and:
    - file.inFolder("Areas")
properties:
  file.name:
    displayName: Title
  note.acronym:
    displayName: Acronym
  note.tags:
    displayName: Tags
  note.last updated:
    displayName: Last Updated
views:
  - type: table
    name: Areas
    filters:
      and:
        - file.hasLink(this.file)
    order:
      - file.name
      - acronym
      - last updated
      - tags
    columnSize:
      file.name: 420

```

## Linked Resources

> [!note] Reference material that informed this technique
> This table auto-populates with any Resource that this Technique links to.

```base
filters:
  and:
    - file.inFolder("Resources")
properties:
  file.name:
    displayName: Title
  note.source:
    displayName: Source
  note.tags:
    displayName: Tags
  note.last updated:
    displayName: Last Updated
views:
  - type: table
    name: Resources
    filters:
      and:
        - file.hasLink(this.file)
    order:
      - file.name
      - source
      - last updated
      - tags
    columnSize:
      file.name: 420

```

## See Also

> [!tip] Related links
> Link to other Techniques, external references, or anything else that provides useful context.

- ...
