---
name: vault-knowledge-retrieval
description: Search and retrieve knowledge from the PARA knowledge base (Areas, Techniques, Resources). Use when the user asks about a technology, concept, process, or domain, or when you need background context from their Second Brain to support another task.
---

# Obsidian Vault Knowledge Retrieval

Search and synthesize information from the user's PARA-organized knowledge base, spanning Areas (knowledge domains), Techniques (distilled actionable knowledge), and Resources (reference material). This skill supports the **Organize** and **Distill** stages of the CODE workflow by helping the user find and connect what they already know.

## Inputs

### Vault Structure (PARA)

The knowledge base is organized using the PARA system:

- **Areas**: `Areas/<Area Name>.md` for ongoing knowledge domains, technologies, and responsibilities. May contain subfolders for logical domain grouping (e.g., `Areas/AI/`). Frontmatter properties: `acronym`, `tags: [Area]`, `last updated`. Sections include Overview, Key Concepts, and auto-populated Techniques/Resources tables via `base` queries.
- **Techniques**: `Techniques/<Technique Name>.md` for distilled, actionable knowledge synthesized from Areas and Resources. Frontmatter properties: `tags: [Technique]`, `last updated`. Sections include Context, Approach, Process, Insights, Outputs, and auto-populated Linked Areas/Resources tables.
- **Resources**: `Resources/` organized in subfolders by type (e.g. `Articles/`, `Blueprints/`, etc.). Frontmatter properties: `source`, `tags: [Resource]`, `last updated`. Sections include Summary and Key Takeaways.
- **Projects**: `Projects/<Project Name>.md` for active tasks with goals and deadlines. Frontmatter properties: `priority`, `date_from`, `date_to`, `tags: [Project]`, `last updated`.
- **Archive**: `Archive/` mirrors the PARA structure for completed or inactive items.

### Base Files

Base files at the vault root provide structured views across content types. These are useful for discovery and navigation:

- `Knowledge.base` — Unified view across Areas, Techniques, and Resources with type filtering.
- `Projects.base` — Active project tracking with status and priority.
- `Techniques.base` — All techniques with linked Areas.

### Key Conventions

- Areas are linked as wikilinks: `[[Area Name]]` (e.g., `[[Kubernetes]]`, `[[TypeScript]]`).
- Techniques link to their parent Areas via the `areas` frontmatter property: `areas: ["[[Kubernetes]]"]`.
- Resources link to related Areas and Techniques via inline wikilinks in content.
- The `last updated` frontmatter property tracks when content was last revised.

## Instructions

Your task is to:

1. **Parse the user's query** to identify the retrieval intent. Determine which combination of filters applies:
   - **Content type** - Area, Technique, Resource, Project, or all types.
   - **Topic or keyword** — a technology, concept, domain, or theme (e.g., "second brain", "knowledge management", "AI").
   - **Relationship** — what connects to what (e.g., "What exist for this domain?", "What resources support this area?").
   - **Recency** — recent additions or updates vs. the full knowledge base.

2. **Locate matching files** using workspace tools:
   - Use glob patterns to find candidate files by folder and name (e.g., `Areas/**/*.md`, `Techniques/*AI*.md`).
   - Use text search to scan frontmatter properties (`tags`, `acronym`, `source`) and body content for matching keywords.
   - When searching for a topic, search across all PARA folders - a query about "AI" may match an Area (`Areas/Responsible AI.md`), Techniques (`Techniques/Deploying Multi-Agent AI Systems.md`), and Resources (`Resources/Articles/`).

3. **Read and extract relevant content** from matching files:
   - For Areas: Overview and Key Concepts sections. Note which Techniques and Resources are linked.
   - For Techniques: Context, Approach, and Process sections. Note which Areas and Resources inform it, and what Outputs it produced (Express stage).
   - For Resources: Summary and Key Takeaways. Note the source.
   - For Projects: Objective, Key Results, and current Progress/Blockers.

4. **Trace connections** across the knowledge graph:
   - If an Area has linked Techniques (via the `base` query or inline wikilinks), mention them.
   - If a Technique references Areas it builds on, note those relationships.
   - If the user asks "what do I know about X?", search across all PARA folders for a complete picture.

5. **Synthesize a coherent response** that directly answers the user's question:
   - Lead with a concise summary of what the vault contains on the topic.
   - Support with specifics drawn from the vault, organized by type (Areas → Techniques → Resources) or by relevance.
   - Attribute each piece of information to its source file.
   - If the query spans multiple related notes, connect the dots — show how Areas, Techniques, and Resources relate to each other.

6. **Identify gaps** when relevant:
   - If an Area exists but has no linked Techniques, note that distillation hasn't happened yet.
   - If a topic appears in Journal entries but has no Area note, suggest creating one.
   - If a Technique has no Outputs section filled in, note the Express stage is incomplete.

## Guidelines

- **Read before responding.** Always read and understand the retrieved content before generating any response.
- **Vault-only sourcing.** Only respond with information found in the vault files. Do not fabricate or supplement with outside knowledge. If no matching entries exist, say so clearly.
- **Cite everything.** Attribute every piece of information with its source file path in brackets, e.g., `[Areas/Responsible AI.md]` or `[Techniques/Deploying Multi-Agent AI Systems.md]`.
- **Cast a wide net for ambiguous queries.** When a query is broad (e.g., "what do I know about AI?"), search across Areas, Techniques, and Resources, then organize the results by relevance.
- **Preserve the user's language.** Use their terminology and phrasing from the notes, not your own paraphrase.
- **Organize by type.** When listing multiple entries, order by type (Areas first, then Techniques, then Resources) unless the user requests otherwise.
- **Check the Archive.** If the user asks about historical or deprecated knowledge, search `Archive/` folders — but note that these items are archived.
