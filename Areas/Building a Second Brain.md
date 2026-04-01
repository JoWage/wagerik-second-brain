---
acronym:
tags:
  - Area
  - Knowledge-Management
last updated: 2026-04-01
---

## Overview

> [!info] What is this area and why does it matter?
> Describe this knowledge domain, technology, or responsibility in 2-3 sentences. Focus on what it is, why it's relevant to your work, and what value it provides. Link to related Areas with `[[Area Name]]`.

- Building a Second Brain is a personal knowledge management methodology created by Tiago Forte. It combines the **CODE** workflow (Capture → Organize → Distill → Express) with the **PARA** organizational structure (Projects, Areas, Resources, Archive) to create a trusted system for externalizing knowledge. The goal is to reduce cognitive overload by building a reliable external system that captures, organizes, and surfaces the right information at the right time, freeing your mind for creative and analytical work rather than storage and recall.

## Key Concepts

> [!tip] What are the essential things to know?
> Bullet the core ideas, principles, or components someone needs to understand about this area. Think of this as your personal cheat sheet.

### CODE - The Workflow

- **Capture**: Save insights, ideas, and information that resonate with you. Not everything, only what genuinely stands out. The goal is to eliminate the fear of forgetting without creating information hoarding.
- **Organize**: Sort captured information using PARA based on *actionability*, not topic. Ask "what project or goal does this help me with?" rather than "what category does this belong to?"
- **Distill**: Summarize key points so their essence is immediately apparent. Use [[Progressive Summarization]] to layer highlights over time, making notes increasingly discoverable for your future self.
- **Express**: Turn distilled knowledge into outputs, such as a blog post, presentation, decision, or new project. This is where the system creates value. A Second Brain that only stores information is a filing cabinet; one that produces output is a thinking partner.

### PARA - The Structure

- **Projects**: Active tasks with a clear goal and deadline (e.g., "Launch website," "Write quarterly report")
- **Areas**: Ongoing responsibilities that require maintenance but have no end date (e.g., "Health," "Professional development," "Team management")
- **Resources**: Topics of interest or reference material not tied to a specific responsibility (e.g., "Book notes," "Design inspiration," "Industry trends")
- **Archive**: Inactive items from the above three categories, preserved for future reference but hidden from daily view

### Core Principles

- **Organize for actionability, not categorization** - the question is "when will I use this?" not "what is this about?"
- **Keep things moving** - notes should flow between PARA categories as their status changes; a completed Project moves to Archive, an Area that loses relevance gets archived
- **Favor retrievability over completeness** - a note that's easy to find and scan beats a comprehensive note you'll never revisit
- **Small, composable notes over monolithic documents** - individual ideas that can be recombined are more versatile than long, single-purpose documents

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
    columnSize:
      file.name: 420
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

- [[Progressive Summarization]]
- [Building a Second Brain — Tiago Forte](https://www.buildingasecondbrain.com/)
- [The PARA Method — Forte Labs](https://fortelabs.com/blog/para/)
- [Building a Second Brain (Book)](https://www.buildingasecondbrain.com/book)
