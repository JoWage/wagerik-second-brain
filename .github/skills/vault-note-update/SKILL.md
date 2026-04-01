---
name: vault-note-update
description: Update, enrich, or restructure existing notes in the Obsidian vault. Merges new information into existing sections, adds cross-links to related content, decomposes overloaded notes into properly linked multi-note structures, and reactivates archived content when relevant. Use when the user asks to update, edit, expand, enrich, revise, or reorganize an existing note or topic in their vault.
---

# Obsidian Vault Note Update

Update existing notes in the user's Obsidian Second Brain while preserving their established structure, frontmatter, and cross-links. This skill enriches the knowledge graph by merging new information into the right places, strengthening connections between notes, and keeping the PARA organization healthy.

This skill shares the **Knowledge Base Scan** approach with `vault-note-creation` — every update begins with a discovery pass to find related content, identify decomposition opportunities, and surface archived notes that should be reactivated.

## When to Use This Skill

| Signal | Action |
|--------|--------|
| "Update the note on X" / "Add this to my X note" | Merge new content into an existing note |
| "Expand the X section of Y" | Add detail to a specific section |
| "This note is getting too big" / "Break this apart" | Decompose into multiple linked notes |
| "Link X to Y" / "Connect these notes" | Add cross-links between existing notes |
| "Move X out of archive" / "X is relevant again" | Reactivate archived content |
| "Refresh my notes on X" / "My X note is outdated" | Review and modernize stale content |
| User provides new info on a topic that already has a note | Merge into existing rather than creating a duplicate |

## Instructions

Your task is to:

### Phase 1 — Locate and Understand the Target

1. **Identify the target note(s).** From the user's request, determine which note(s) need updating:
   - If the user names a specific note, search for it by file name across active folders (`Areas/`, `Techniques/`, `Resources/`, `Projects/`, `People/`).
   - If the user describes a topic without naming a file, search by keyword across file names, frontmatter, and body content. Prioritize active folders, then check `Archive/`.
   - If multiple notes match, present the candidates and ask the user to confirm which one(s) to update.

2. **Read the target note(s) in full.** Understand the current state:
   - Frontmatter properties and their values.
   - Which sections exist and what content they contain.
   - Existing cross-links (wikilinks to other notes).
   - The `last updated` timestamp — how stale is this note?

3. **Read the corresponding template** from `_Templates/` to understand the canonical structure for this note type. This ensures any additions follow the expected format.

### Phase 2 — Knowledge Base Scan

Before making changes, perform a discovery pass identical to the one in `vault-note-creation`.

4. **Search for related content across the vault:**
   - Search **active folders first** (`Areas/`, `Techniques/`, `Resources/`, `Projects/`, `People/`) for notes related to the new information the user wants to add.
   - Then search **`Archive/`** for archived notes on related topics.
   - Record every match with its path, type, and a brief summary.

5. **Classify each match:**
   - **Already linked** — the target note already references this match. No action needed unless the link context should be updated.
   - **New cross-link candidate** — a related note exists but isn't linked from the target. Flag for linking.
   - **Archived and relevant** — an archived note is relevant to this update. Flag for reactivation (see Phase 3).
   - **Decomposition candidate** — the new information being added represents a distinct enough topic that it warrants its own note rather than being crammed into the target.

6. **Evaluate decomposition.** If the update would make the target note cover too many distinct concepts:
   - Identify which parts should be **extracted** into their own notes (new Area, Technique, or Resource).
   - Plan the extraction: what content moves out, what stays, and how the notes will link to each other.
   - A note that covers both "what X is" (Area) and "how to do Y with X" (Technique) should generally be split.
   - A note that contains substantial reference material from an external source should have that material extracted into a Resource, with the original note linking to it.
   - Present the decomposition plan to the user before proceeding if it involves creating more than one new note.

### Phase 3 — Archive Reactivation

If the scan found archived notes relevant to the update:

7. **Reactivate archived notes** instead of duplicating their content into the target:
   - Move the file from `Archive/<Type>/...` back to its active counterpart folder. Preserve the original file name and subfolder structure.
   - Update its `last updated` frontmatter to today's date.
   - Enrich it with any new information from the user's request.
   - Add cross-links between the reactivated note and the target note being updated.
   - Report the reactivation to the user.

8. **Track reactivation trends.** If multiple archived notes from the same domain are surfacing as relevant, flag this pattern. Suggest a broader review of that archived domain.

### Phase 4 — Enrichment

Before applying edits, gather additional context from the user's activity and the public web to produce richer, more accurate updates.

9. **Query recent journals for internal context.** Explore any `Journals/` related to the topic. Craft targeted queries based on the note being created:
   - For an **Area or Technique**: `"What have I discussed, shared, or worked on related to {topic} in the past month?"` — surfaces meetings and conversations that provide firsthand context.
   - For a **Project**: `"What meetings and discussions have I had about {project name} recently?"` — captures coordination, decisions, and progress.
   - For a **Person**: `"What are my recent interactions with {person name}?"` — populates interaction history.
   - For a **Resource**: `"Have I shared or received any documents, links, or emails about {topic}?"` — finds the original source and any internal discussion around it.
   - If journals returns relevant results, extract:
     - Key decisions or conclusions from meetings and chats.
     - People involved (as `[[wikilink]]` candidates).
     - Dates and timelines.
     - Technical details, status updates, or blockers discussed.
   - If journals returns nothing relevant, proceed without — do not fabricate internal context.

10. **Search the public web for enrichment.** Use the `fetch_webpage` tool to gather publicly available information that would strengthen the update:
   - For **updating an Area**: Fetch the latest official documentation page, product overview, or key blog posts since the note's `last updated` date to capture what has changed.
   - For **updating a Technique**: Search for updated best practices, new approaches, or community learnings that complement or validate the user's existing technique.
   - For **enriching a Resource**: If the update involves a new external source, fetch that page to extract additional Summary and Key Takeaways content.
   - For a **Project**: Skip web enrichment unless the project involves a public technology or framework that needs documentation context.
   - For a **Person**: Skip web enrichment — people notes should only contain information the user provides.
   - **Guidelines for web enrichment:**
     - Only fetch pages that are clearly relevant and public (official docs, blog posts, GitHub repos, product pages).
     - Distill fetched content into the user's own note format — do not copy-paste large blocks of external text.
     - Always attribute external sources: include the URL in the `source` frontmatter (for Resources) or in a See Also section.
     - If the topic is internal/proprietary (e.g., an internal team process, an internal tool), rely on any internal sources (if available) and the user's input instead of web search.

11. **Synthesize enrichment into the update plan.** Combine the user's new input, knowledge base scan results, journal context, and web research. Prioritize sources in this order:
   1. User-provided information (highest priority — this is their perspective).
   2. Journal activity (firsthand internal context).
   3. Existing PARA vault content (preserves knowledge graph consistency).
   4. Public web sources (supplements with accurate external detail).

### Phase 5 — Apply Updates

12. **Merge new content into the target note.** Follow these principles:
   - **Preserve existing structure.** Do not reorganize sections, remove callout blocks, or change the template layout. Add content within the existing section framework.
   - **Append, don't overwrite.** Add new bullets, paragraphs, or sub-sections below existing content in the relevant section. Do not delete or rewrite existing content unless the user explicitly asks for a correction or replacement.
   - **Respect section purpose.** Place content in the correct section based on the template's callout prompts:
     - *Area*: factual description → Overview. Core concepts → Key Concepts.
     - *Technique*: problem statement → Context. Strategy → Approach. Steps → Process. Learnings → Insights. Deliverables → Outputs.
     - *Resource*: what it covers → Summary. Key points → Key Takeaways.
     - *Project*: goal → Objective. Metrics → Key Results. Status → Progress. Issues → Blockers.
   - **Incorporate enrichment naturally.** When adding content from journals or web research:
     - Weave journal findings into the relevant section (e.g., meeting decisions into Overview or Context, people into cross-links, technical findings into Key Concepts or Process).
     - Distill web research into concise bullets matching the note's existing style. Attribute sources with URLs in a See Also section.
     - Draw from all sources in priority order: user input → journal context → existing PARA vault content → web research.
   - **Maintain consistent formatting.** Match the existing bullet style, heading levels, and wikilink conventions.
   - **Update frontmatter** when appropriate:
     - Always update `last updated` to today's date and time in ISO 8601 format.
     - Add new tags if the update introduces a new topic dimension (e.g., adding `AI` tag when AI content is added to an Area).
     - For Techniques, add new `areas` entries if the update introduces a new parent Area relationship.

13. **Add cross-links** discovered during Phase 2 and Phase 4:
    - Insert `[[wikilinks]]` to newly discovered related notes in the appropriate sections (Overview, See Also, Approach, etc.).
    - For bidirectional linking, also add a link from the related note back to the updated note — but only when the relationship is clearly relevant and the edit is minimal (e.g., appending a bullet to a See Also section).

14. **Handle decomposition** if Phase 2 identified it:
    - Extract the appropriate content from the target note into new note(s), following the `vault-note-creation` skill's Phase 3 instructions (read template, populate frontmatter, populate sections).
    - Replace the extracted content in the original note with a brief summary and a wikilink to the new note. For example: `- See [[Running Responsible AI Checklists for Multi-Agent AI Systems]] for the detailed technique.`
    - Ensure all new notes link back to the original and to each other as appropriate.

### Phase 6 — Reporting

15. **Save all modified and created files.**

16. **Report back** to the user with:
    - **Updated notes**: file paths, summary of what was added or changed in each.
    - **Reactivated notes**: file paths (old → new location), summary of updates applied.
    - **Enrichment sources used**: summarize what was pulled from journals (e.g., "Found 3 1-1 conversations and a meeting from last week on this topic") and web research (e.g., "Incorporated key concepts from the official docs page").
    - **Cross-links added**: which existing notes were linked to/from.
    - **Suggestions**: additional notes that could be created or updated to strengthen the knowledge graph. Mention any unresolved wikilinks that represent future note opportunities.
    - **Archive trends**: if archived content was found to be increasingly relevant, recommend a domain-level review.

## Guidelines

- **Always perform Phase 1 and Phase 2 before editing.** Read the target note and scan the knowledge base first. Never edit blindly.
- **Never delete content** unless the user explicitly requests removal or correction. Updates are additive by default.
- **Preserve callout blocks** (`> [!info]`, `> [!tip]`, `> [!note]`, `> [!warning]`, `> [!example]`). These are structural elements of the template, not content to be removed.
- **Preserve `base` query blocks** exactly as they are. Do not modify the base queries — they are auto-populated by Obsidian.
- Use `[[wikilinks]]` for all internal cross-references.
- Set `last updated` to today's date in ISO 8601 format on every note that is modified.
- **Prefer reactivation over recreation.** If the user's update relates to content that exists in `Archive/`, move it back rather than adding that information to a different note where it doesn't structurally belong.
- **Decompose when warranted, not eagerly.** Only extract content into new notes when there is a clear structural mismatch (e.g., technique content in an Area note, or a note covering two genuinely distinct domains). Minor tangents or cross-references do not warrant decomposition.
- When decomposing, always leave a summary and wikilink in the original note so the knowledge graph remains navigable.
- When updating multiple notes in a single request, process them in dependency order: Areas first, then Techniques, then Resources, then Projects.
- Keep edits focused on what the user requested. Do not reorganize, reformat, or "improve" sections that are not part of the update.
- When searching the knowledge base, prioritize **active (non-archived) content** for cross-linking. Include archived content in the scan but flag it clearly as archived in the report.
- If a user's request is ambiguous about whether they want a new note or an update to an existing one, default to checking for an existing note first. If one exists, update it. If none exists, create using `vault-note-creation`.
