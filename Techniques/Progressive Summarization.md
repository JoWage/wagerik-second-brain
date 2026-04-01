---
areas:
  - "[[Building a Second Brain]]"
tags:
  - Technique
  - Knowledge-Management
last updated: 2026-04-01T09:54:00
---

## Context

> [!info] What problem or challenge does this technique address?
> Describe the situation that makes this technique necessary. What pain point, gap, or opportunity does it respond to? Link to relevant Areas with `[[Area Name]]`.

- The Distill stage of the CODE workflow in [[Building a Second Brain]] is where most knowledge systems break down. You capture notes, but when you return to them weeks or months later, they're dense, unfamiliar walls of text. You don't remember why you saved them or what mattered. Re-reading the entire note defeats the purpose of having saved it in the first place.
- Progressive Summarization addresses this by creating layers of distillation that make the essential insights discoverable at a glance without losing the full context for when you need it.

## Approach

> [!tip] How does this technique work at a high level?
> Explain the strategy or mental model. Which Areas of knowledge are combined? Which Resources informed this approach? This is the *why* behind the process.

- The approach is **layered highlighting**. Each time you revisit a note, you add one more layer of summarization rather than rewriting the whole thing. This is opportunistic, not scheduled: you add layers when you naturally encounter the note, not on a fixed review cadence.
- The key insight is that your attention is the scarcest resource. Progressive Summarization leverages the moments when you're already engaging with a note (searching for something, preparing a presentation, working on a project) to incrementally refine it.

## Process

> [!note] Step-by-step: how to execute this technique
> Number the steps clearly. Someone (including future you) should be able to follow these without additional context.

1. **Layer 1 - Original capture.** Save the raw content: meeting notes, article excerpts, quotes, observations. Don't filter heavily at this stage, capture what resonates.
2. **Layer 2 - Bold the key passages.** On your first revisit, **bold** the sentences or phrases that contain the core insights. This should reduce the readable content to roughly 10-20% of the original.
3. **Layer 3 - Highlight the highlights.** On a subsequent revisit, ==highlight== the most critical points within your bolded passages. This creates an ultra-compressed layer that's scannable in seconds.
4. **Layer 4 - Executive summary.** Write a brief summary at the top of the note, 2-4 sentences in your own words capturing the essential takeaway. This is the layer that answers "why did I save this?" instantly.
5. **Layer 5 - Remix and express.** Use the distilled note as input for creating something new: a blog post, a presentation, a decision document, or a new Technique in your vault. This is the Express stage of CODE, where captured knowledge becomes output.

## Insights

> [!tip] What did you learn from applying this technique?
> Capture lessons learned, surprising findings, edge cases, or refinements. These insights are the distilled value, the reason this Technique exists.

- **Most notes never get past Layer 1 and that's fine.** Not every note deserves deep distillation. The act of layering happens naturally when you encounter a note that's actually useful. Notes that never get revisited stay at Layer 1, and that's a signal about their value.
- **Layer 4 (executive summary) has the highest return on investment.** A 2-sentence summary at the top of a note saves more future time than any amount of bolding or highlighting. If you only do one layer beyond capture, make it this one.
- **Progressive Summarization works exceptionally well with AI skills.** An AI skill that reads a note can identify the bolded and highlighted layers, giving it a pre-prioritized view of what matters. This is one of the reasons structure matters for AI-augmented knowledge management.
- **The technique scales where scheduled review doesn't.** "Review all your notes weekly" is a practice that dies with the first busy week. "Add a layer whenever you happen to open a note" survives because it requires no scheduling, it piggybacks on work you're already doing.

## Outputs

> [!example] What did this technique produce?
> Link to tangible outputs: blog posts, GitHub repos, presentations, documentation, internal posts, or shared artifacts. This is the *Express* stage of CODE.

- This Technique note itself, a distilled reference on Progressive Summarization that can be shared or revisited quickly
- Applied across the vault to progressively refine meeting notes, article summaries, and knowledge domain descriptions

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

- [[Building a Second Brain]] - The parent methodology
- [[The PARA Method - Forte Labs]]
- [Progressive Summarization - Forte Labs](https://fortelabs.com/blog/progressive-summarization-a-practical-technique-for-designing-discoverable-notes/)
