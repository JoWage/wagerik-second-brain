---
name: vault-note-creation
description: Create new notes in the Obsidian vault following established templates and PARA conventions. Supports creating Areas, Techniques, Resources, Projects, and People notes. Automatically decomposes topics into multiple linked notes when appropriate, searches the existing knowledge base for cross-links, and reactivates archived content instead of duplicating it. Use when the user asks to add, create, or document a new topic, technology, process, person, or project in their vault.
---

# Obsidian Vault Note Creation

Create new notes in the user's Obsidian Second Brain following the established templates and PARA organizational structure. This skill supports all stages of the **CODE** workflow - from Capturing new knowledge to Organizing it in the right PARA folder, with proper frontmatter, sections, and cross-links.

Before creating anything, this skill performs a **knowledge base scan** to discover existing related content, identify opportunities for cross-linking, decompose complex topics into multiple linked notes, and reactivate archived content rather than recreating it.

## Supported Note Types

| Type | Folder | Template | Tag | When to Use |
|------|--------|----------|-----|-------------|
| Area | `Areas/` | `_Templates/Template - Area.md` | `Area` | New knowledge domain, technology, tool, team, or responsibility |
| Technique | `Techniques/` | `_Templates/Template - Technique.md` | `Technique` | Distilled, actionable knowledge synthesized from experience |
| Resource | `Resources/` | `_Templates/Template - Resource.md` | `Resource` | External reference material (articles, blueprints, emails) |
| Project | `Projects/` | `_Templates/Template - Project.md` | `Project` | Active task with a clear goal and deadline |
| Person | `People/` | `_Templates/Template - Person.md` | `People` | New colleague or contact to track interactions with |

## Instructions

Your task is to:

### Phase 1 — Knowledge Base Scan

Before creating any note, perform a discovery pass over the existing vault to understand the landscape.

1. **Search for existing coverage.** For each topic keyword or concept in the user's request:
   - Search **active folders first** (`Areas/`, `Techniques/`, `Resources/`, `Projects/`, `People/`) using file name globs and text search across frontmatter and body content.
   - Then search **`Archive/`** (mirrors the same PARA structure: `Archive/Areas/`, `Archive/Techniques/`, etc.) for archived notes on the same or closely related topics.
   - Record every match with its path, type, and a brief summary of what it covers.

2. **Classify each match:**
   - **Exact duplicate**: a note with the same topic already exists in an active folder. **Do not create a new note.** Instead, inform the user and suggest using the `vault-note-update` skill to enrich the existing note.
   - **Archived match**: a note on this topic exists in `Archive/`. Flag it for **reactivation** (see Phase 2).
   - **Related content**: an existing note that covers an adjacent or overlapping topic. Record it as a **cross-link candidate**.
   - **No match**: the topic is genuinely new. Proceed with creation.

3. **Decompose the topic into note candidates.** Evaluate whether the user's request should produce a single note or multiple linked notes:
   - If the user describes a **knowledge domain** (what something is) *and* a **process** (how to do something with it), plan both an Area and a Technique.
   - If the user provides **external reference material** alongside a concept, plan both an Area (or Technique) and a Resource.
   - If the user describes a **person** in the context of a **project or team**, plan both a Person note and cross-links to the relevant Project/Area.
   - If the topic naturally spans **multiple distinct knowledge domains** (e.g., "how we use responsible AI patterns with multi-agent AI systems"), plan separate notes for each domain facet and link them: an Area and a Technique for the combined approach.
   - Present the proposed note plan to the user before proceeding if more than two notes will be created.

### Phase 2 — Archive Reactivation

If Phase 1 found archived notes relevant to the user's request:

4. **Reactivate instead of recreate.** For each archived match:
   - Move the file from `Archive/<Type>/...` back to its active counterpart folder (e.g., `Archive/Areas/Responsible AI.md` → `Areas/Responsible AI.md`). Preserve the original file name and subfolder structure.
   - Update its `last updated` frontmatter property to today's date and time.
   - Review its content — if it is outdated or sparse, enrich it with the new information the user provided (following the template structure).
   - Add any new cross-links discovered during the scan.
   - Report to the user that the note was reactivated rather than created fresh, and summarize what was updated.

5. **Track reactivation trends.** If multiple archived notes from the same domain are being reactivated (e.g., several `Archive/Areas/AI` notes becoming relevant again), note this pattern to the user. Suggest a broader review of that archived domain to pull back any other still-relevant content.

### Phase 3 — Enrichment

Before writing content, gather additional context from the user's activity and the public web to produce richer, more accurate notes.

6. **Query recent journals for internal context.** Explore any `Journals/` related to the topic. Craft targeted queries based on the note being created:
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

7. **Search the public web for enrichment.** Use the `fetch_webpage` tool to gather publicly available information that would strengthen the note:
   - For an **Area**: Fetch the official documentation page, product overview, or key blog posts to populate the Overview and Key Concepts sections with accurate, current information.
   - For a **Technique**: Search for best practices, tutorials, or reference architectures that validate or complement the user's approach.
   - For a **Resource**: If the user provided a URL, fetch that page to extract Summary and Key Takeaways. If they described content without a URL, search for the likely source.
   - For a **Project**: Skip web enrichment unless the project involves a public technology or framework that needs documentation context.
   - For a **Person**: Skip web enrichment — people notes should only contain information the user provides.
   - **Guidelines for web enrichment:**
     - Only fetch pages that are clearly relevant and public (official docs, blog posts, GitHub repos, product pages).
     - Distill fetched content into the user's own note format — do not copy-paste large blocks of external text.
     - Always attribute external sources: include the URL in the `source` frontmatter (for Resources) or in a See Also section.
     - If the topic is internal/proprietary (e.g., an internal team process, an internal tool), rely on any internal sources (if available) and the user's input instead of web search.

8. **Synthesize enrichment into the note plan.** Combine the user's input, knowledge base scan results, journal context, and web research into unified content for each section. Prioritize sources in this order:
   1. User-provided information (highest priority — this is their perspective).
   2. Journal activity (firsthand internal context).
   3. Existing PARA vault content (preserves knowledge graph consistency).
   4. Public web sources (supplements with accurate external detail).

### Phase 4 — Note Creation

For each genuinely new note to create:

9. **Determine the note type.** Parse the user's request to identify what kind of note they want to create. Use these signals:
   - "Add a new area/topic/technology for X" → **Area**
   - "Document how to X" / "Create a technique for X" → **Technique**
   - "Save this article/blueprint/reference" → **Resource**
   - "Start tracking project X" / "Create a project for X" → **Project**
   - "Add a person/colleague X" → **Person**
   - If ambiguous, ask the user to clarify. If they describe a domain → Area. If they describe a process or how-to → Technique. If they reference external content → Resource.

10. **Read the corresponding template** from `_Templates/` to get the exact structure, frontmatter properties, and section layout.

11. **Determine the file path:**
   - **Area**: `Areas/<Name>.md`. If it fits an existing domain subfolder (e.g. `Technologies/`, `Tools/`, `Processes/`), place it there.
   - **Technique**: `Techniques/<Descriptive Name>.md`. Use a clear, action-oriented name (e.g., "Running Responsible AI Checklists for Multi-Agent AI Systems.md", not "Multi-Agent Responsible AI.md"). Place in relevant subfolder if one exists.
   - **Resource**: Determine the subfolder based on type — e.g. `Resources/Articles/` for articles. If a new subfolder category is needed, create it.
   - **Project**: `Projects/<Name>.md`.
   - **Person**: `People/<Full Name>.md`.

12. **Populate the frontmatter** using the template's properties and any information the user provides:
   - **Area**: Set `acronym` if provided, `tags: [Area]` (add topic tags as appropriate), `last updated` to today's date and time.
   - **Technique**: Set `tags: [Technique]` (add topic tags as appropriate), `last updated` to today's date and time.
   - **Resource**: Set `source` (URL or origin), `tags: [Resource]` (add topic tags as appropriate), `last updated` to today's date and time.
   - **Project**: Set `priority`, `date_from` to today, `date_to` if a deadline or end date is given, `tags: [Project]` (add topic tags as appropriate), `last updated` to today's date and time.
   - **Person**: Set `team` (wikilink to team Area), `role`, `tags: [People]`, `last updated` to today's date and time.

13. **Populate the sections** following the template structure, incorporating enrichment data from Phase 3. For each section:
    - Read the template's callout prompts (the `> [!info]`, `> [!tip]`, `> [!note]` blocks) to understand what content belongs there.
    - Fill in content drawing from `all sources` in priority order: user input → journal context → existing PARA vault content → web research.
    - When incorporating journal findings, weave them naturally into the relevant section (e.g., meeting decisions into Context or Overview, people into cross-links, technical details into Key Concepts or Process).
    - When incorporating web research, distill it into the user's note format — concise bullets with `[[wikilinks]]` where appropriate. Attribute the source.
    - If they provide rich context (or enrichment surfaced substantial detail), write detailed content. If context is minimal even after enrichment, write a concise starting point and leave placeholders for the user to expand.
    - **Preserve the callout prompts** in the output — they serve as ongoing guidance for the user.

14. **Add cross-links** using the results from Phase 1 and Phase 3:
    - Link to every related note discovered during the knowledge base scan using `[[wikilinks]]`.
    - Link to related Areas, Techniques, Resources, Projects, and People.
    - For Areas: add links in the Overview section and ensure the `base` query will pick up related Techniques.
    - For Techniques: add links in the Overview section to linked Areas and add links to informing Resources in the Approach section.
    - For Resources: add links to related Areas and Techniques in the See Also section.
    - If a linked note doesn't exist yet, still create the wikilink and consider creating the detail of the linked note as a follow-up task.

15. **Include base query blocks** where the template uses them. These auto-populate tables in Obsidian:
    - Area templates include `base` queries for linked Techniques and Resources.
    - Technique templates include `base` queries for linked Areas and Resources.
    - Project templates include `base` queries for related Journal entries.
    - Person templates include `base` queries for interactions.
    - Copy these blocks exactly from the template.

16. **Back-link from existing notes.** When creating a new note that is strongly related to an existing note, consider adding a wikilink to the new note from the existing note's relevant section (e.g., adding `[[New Technique]]` to an Area's Overview or See Also). Only do this when the relationship is clear and the edit is minimal (appending a bullet or link). Use the `vault-note-update` skill principles for these edits.

### Phase 5 — Reporting

17. **Save all files** — new notes and any modified existing notes.

18. **Report back** to the user with:
    - **Created notes**: file paths, brief summary of what was populated.
    - **Reactivated notes**: file paths (old → new location), summary of updates applied.
    - **Enrichment sources used**: summarize what was pulled from journals (e.g., "Found 3 1-1 conversations and a meeting from last week on this topic") and web research (e.g., "Incorporated key concepts from the official docs page").
    - **Cross-links added**: which existing notes were linked to/from.
    - **Suggestions**: additional notes that could be created or updated to strengthen the knowledge graph. Mention any unresolved wikilinks that represent future note opportunities.
    - **Archive trends**: if archived content was found to be increasingly relevant, recommend a domain-level review.

## Guidelines

- Always read the template from `_Templates/` before creating a note. Do not rely on memory of the template structure — templates may evolve.
- **Always perform Phase 1 (Knowledge Base Scan) before creating any note.** This is not optional — it prevents duplicates, surfaces reactivation candidates, and ensures rich cross-linking.
- Follow the template's section order exactly. Do not add extra sections unless the user specifically requests them.
- Preserve the Obsidian callout blocks (`> [!info]`, `> [!tip]`, `> [!note]`, `> [!warning]`, `> [!example]`) — they serve as contextual guidance within the vault.
- Use `[[wikilinks]]` for all internal cross-references. This enables Obsidian's backlink graph.
- When the user provides a URL or external source, capture it in the `source` frontmatter property (for Resources) or in the `See Also` section (for other types).
- Set `last updated` to today's date and time in ISO 8601 format.
- If the user asks to create multiple related notes at once (e.g., "Create an Area for X and a Technique for how to use it"), create them in dependency order — the Area first, then the Technique that links to it.
- **Never create a duplicate note.** If a note with the same or very similar name exists in an active folder, redirect to updating it. If it exists in `Archive/`, reactivate it.
- **Prefer reactivation over recreation.** An archived note that covers the topic — even if outdated — should be moved back, refreshed, and enriched rather than recreated from scratch. This preserves backlinks, history, and the knowledge graph.
- Keep the initial content focused and concise. It's better to create a well-structured skeleton that the user can expand than to generate excessive content that needs trimming.
- If the user provides enough context for a rich note, write it. If they provide just a name or topic, create a minimal but properly structured note.
- When decomposing a topic into multiple notes, create them in dependency order: Areas first, then Techniques that reference those Areas, then Resources. Cross-link all of them.
- When searching the knowledge base, prioritize **active (non-archived) content** for cross-linking. Include archived content in the scan but flag it clearly as archived in your report.
