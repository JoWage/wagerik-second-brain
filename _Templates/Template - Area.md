---
acronym:
tags:
  - Area
last updated:
---

## Overview

> [!info] What is this area and why does it matter?
> Describe this knowledge domain, technology, or responsibility in 2-3 sentences. Focus on what it is, why it's relevant to your work, and what value it provides. Link to related Areas with `[[Area Name]]`.

- ...

## Key Concepts

> [!tip] What are the essential things to know?
> Bullet the core ideas, principles, or components someone needs to understand about this area. Think of this as your personal cheat sheet.

- ...

## Techniques

> [!note] Distilled knowledge that applies to this area
> This table auto-populates with any Technique that links back to this Area.

```base
filters:
  and:
    - file.inFolder("Techniques")
properties:
  file.name:
    displayName: Title
  note.tags:
    displayName: Tags
  note.last updated:
    displayName: Last Updated
views:
  - type: table
    name: Techniques
    filters:
      and:
        - file.hasLink(this.file)
    order:
      - file.name
      - last updated
      - tags
    columnSize:
      file.name: 420

```

## Resources

> [!note] Reference material that supports this area
> This table auto-populates with any Resource that links back to this Area.

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
> Link to related Areas, external docs, or useful URLs that provide additional context.

- ...
