# 🧠 Obsidian AI Second Brain

A starter template for building an **AI-augmented Second Brain** using [Obsidian](https://obsidian.md/), the CODE/PARA methodology, and [GitHub Copilot](https://github.com/features/copilot) skills.

> **Your Second Brain shouldn't be a passive filing cabinet — it should be an active collaborator that strengthens its own structure over time.**

This repository is the companion to the [AI-Augmented Second Brain blog series](https://www.jamescroft.co.uk) — a 6-part guide to building a knowledge management system where AI actively participates in organizing, distilling, and connecting your knowledge.

> **This repo will evolve weekly** as new posts are published. Star ⭐ and watch 👁️ to follow along.

---

## The Three Pillars

This approach rests on three pillars that reinforce each other:

### 📂 Pillar 1 — Structured Knowledge Store (Obsidian + PARA)

An Obsidian vault organized using Tiago Forte's [PARA method](https://fortelabs.com/blog/para/), with a critical design constraint: **every structural choice must be machine-readable.**

Consistent templates. Typed frontmatter. Predictable section layouts. A README that serves as both human documentation and AI grounding context. This structure isn't just organization — it's a contract between you and the AI.

### 🔗 Pillar 2 — Knowledge Graphs in Plain Markdown

Obsidian's `[[wikilinks]]` create a knowledge graph where every note is a node and every link is an edge. Backlinks surface implicit relationships. Dynamic query blocks auto-populate relationship tables. The graph turns a flat collection of files into a **connected knowledge system** that an AI can traverse, query, and extend — and it encodes where work remains.

### 🤖 Pillar 3 — Specialized AI Skills

Custom skills — detailed, reusable instruction sets stored as markdown — tell GitHub Copilot CLI exactly how to perform specific knowledge workflows. Skills are not prompts. They encode your vault's actual folder paths, template structures, and cross-linking conventions, producing reliable, grounded output instead of hallucinated guesses.

### How They Reinforce Each Other

- **Structure enables AI** — Templates and conventions give the AI reliable patterns to follow
- **AI strengthens the graph** — Every skill-driven operation adds cross-links and fills gaps
- **The graph guides the AI** — Relationships and gaps show the AI what's connected and what's missing

The result: a **self-reinforcing loop** where the system compounds rather than decays.

---

## What's Inside (Planned Structure)

This repository will grow incrementally alongside the blog series. Here's where it's headed:

```
obsidian-ai-second-brain/
├── README.md                          # This file — CODE/PARA docs + setup guide
├── LICENSE                            # MIT
│
├── Projects/                          # Active tasks with goals and deadlines
├── Areas/                             # Ongoing knowledge domains
├── Resources/                         # Reference material (Articles, Blueprints, etc.)
├── Techniques/                        # Distilled actionable knowledge
├── Archive/                           # Completed/inactive items (mirrors PARA)
├── Journal/                           # Time-based capture (Meetings, Weekly, Monthly)
├── People/                            # Contact and colleague profiles
│
├── _Templates/                        # Note templates for each PARA type
├── _Attachments/                      # Images and file attachments
│
├── *.base                             # Dynamic index files (Knowledge, Projects, etc.)
│
└── .github/
    └── skills/                        # GitHub Copilot custom skills
```

---

## The CODE Workflow

[CODE](https://www.buildingasecondbrain.com/) defines how information flows through the vault:

| Stage | What happens | AI role |
|-------|-------------|---------|
| **Capture** | Save insights, meeting notes, ideas into `Journal/` | AI synthesizes notes with calendar and chat data |
| **Organize** | Sort into PARA folders based on actionability | AI scans for duplicates, reactivates archived notes, adds cross-links |
| **Distill** | Extract key insights into `Techniques/` | AI chains daily → weekly → monthly synthesis |
| **Express** | Turn knowledge into output — posts, talks, decisions | AI enables rapid recall and polished artifacts |

## The PARA Structure

[PARA](https://fortelabs.com/blog/para/) defines where information lives:

| Folder | Purpose |
|--------|---------|
| `Projects/` | Active tasks with clear goals and deadlines |
| `Areas/` | Ongoing responsibilities and knowledge domains |
| `Resources/` | Non-actionable content that supports learning |
| `Techniques/` | Distilled knowledge — bridges Distill ↔ Express |
| `Archive/` | Completed or inactive items from the above |

Supporting folders: `Journal/` (time-based capture), `People/` (relationships), `_Templates/` (note structure), `_Attachments/` (media).

---

## Getting Started

Full setup instructions are coming. For now, if you want to explore early:

1. **Star this repo** to follow along with the series
2. **Read [Part 1](https://www.jamescroft.co.uk/why-your-second-brain-needs-an-ai-companion/)** to understand the approach and the three pillars
3. **Install [Obsidian](https://obsidian.md/)** if you haven't already
4. **Get [GitHub Copilot](https://github.com/features/copilot)** — you'll need it for the AI skills

---

## Contributing

This project is in its early stages. Contributions, ideas, and feedback are welcome once the core structure is in place. In the meantime, [open an issue](https://github.com/jamesmcroft/obsidian-ai-second-brain/issues) if you have questions or suggestions.

---

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

- [Building a Second Brain](https://www.buildingasecondbrain.com/) by Tiago Forte — the foundational methodology
- [The PARA Method](https://fortelabs.com/blog/para/) — the organizational framework
- [Obsidian](https://obsidian.md/) — the knowledge platform
- [GitHub Copilot](https://github.com/features/copilot) — the AI agent platform
