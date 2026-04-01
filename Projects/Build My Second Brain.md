---
priority: 1
date_from: 2026-04-01
date_to:
tags:
  - Project
  - Knowledge-Management
last updated: 2026-04-01T09:54:00
---

## Objective

> [!info] What is this project trying to achieve?
> State the goal in 1-2 sentences. Be specific about the desired outcome and how you'll know it's done. A good objective answers: *What will be different when this is complete?*

- Set up a working [[Building a Second Brain]] vault using CODE/PARA and Obsidian. Complete when the vault has a functioning folder structure, templates for each note type, at least 10 Area notes covering my key knowledge domains, and a journal habit established.

## Key Results

> [!tip] Measurable outcomes that define success
> List 3-5 concrete, measurable results. Use checkboxes to track completion. Each should be independently verifiable.

- [ ] PARA folder structure created with all supporting folders (Journal, People, Templates, Attachments)
- [ ] Templates set up for each note type (Area, Technique, Resource, Project, Person, Meeting, Weekly, Monthly)
- [ ] At least 10 Area notes created covering key knowledge domains
- [ ] First journal completed using [[Progressive Summarization]] principles
- [ ] At least 3 Techniques distilled from existing knowledge

## Stakeholders

> [!info] Who is involved and what are their roles?
> Link to People with `[[Name]]`. Note their role in this project (sponsor, contributor, reviewer, etc.)

- Just me - this is a personal knowledge management project

## Progress

> [!note] Living record of how this project is evolving
> Update this section regularly. Move older updates under a collapsible heading if the list grows long.

### Current Status

- 2026-04-01 - Project started. Forked the [obsidian-ai-second-brain](https://github.com/jamesmcroft/obsidian-ai-second-brain) template repository. Folder structure and templates are in place. Read [[The PARA Method - Forte Labs]] to ground the approach.

### Decisions Made

> [!tip] Capture decisions so you don't revisit them
> Record what was decided, when, by whom, and the rationale. This prevents decision fatigue and circular discussions.

- **Start with Areas before Techniques.** Rationale: Areas define the knowledge domains; Techniques distill from them. You need the domains before you can distill.
- **Use Obsidian over Notion.** Rationale: markdown-first means files are portable, Git-versioned, and AI-readable. Wikilinks create a native knowledge graph without proprietary lock-in.

### Blockers

> [!warning] What's preventing progress?
> Be specific: who or what is blocking, what's needed to unblock, and any escalation actions taken.

- None - this is a greenfield setup with no dependencies.

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
        - file.hasLink(this.file)
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

## See Also

> [!tip] Related links
> Link to related Areas, Techniques, or external resources that support this project.

- [[Building a Second Brain]]
- [[Progressive Summarization]]
- [[The PARA Method - Forte Labs]]
- [AI-Augmented Second Brain Blog Series](https://www.jamescroft.co.uk/why-your-second-brain-needs-an-ai-companion/)
