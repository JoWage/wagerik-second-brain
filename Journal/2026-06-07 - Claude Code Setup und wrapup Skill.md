---
date: 2026-06-07
tags:
  - Journal
  - Daily
  - ClaudeCode
  - WagerickStudio
---

## 🌅 Start of Day

### Was war der Fokus?
Claude Code Setup optimieren — globale Konfiguration anlegen und Session-Abschluss-Workflow bauen.

## 🌙 End of Day

### Was wurde gemacht?

- **Claude Setup PDF** analysiert und mit bestehendem Setup verglichen → 6 Lücken identifiziert
- **Globale `~/.claude/CLAUDE.md`** angelegt mit 7 Workflow-Regeln (Plan-Mode, Subagents, Self-Improvement-Loop, Verification before Done, Demand Elegance, Autonomous Bug Fixing, Skill Authoring)
- **`marketing-skills`-Paket** installiert via `npx skills add coreyhaines31/marketingskills` (43 Skills)
- **Statusline** installiert (zeigt live Kontext-Auslastung + Token-Kosten im Terminal)
- **`/wrapup`-Skill** erstellt — nach mehreren Fehlversuchen korrekt über Windows-Junction in `.claude/skills/` registriert

### Was hat Friction erzeugt?

> [!warning] Skill-Registrierung war komplex
> Drei Fehlversuche bevor die richtige Struktur gefunden wurde:
> 1. Skill in `plugins/marketplaces/` → wird ignoriert
> 2. Skill in `plugins/cache/` + `installed_plugins.json` → Plugin-System ignoriert manuell Hinzugefügtes
> 3. Skill in `.agents/skills/` ohne Junction → Claude Code scannt `.claude/skills/`, nicht `.agents/skills/`
> 
> **Lösung:** `.claude/skills/wrapup` als Windows-Junction anlegen, die auf `.agents/skills/wrapup` zeigt — genau wie `npx skills add` es automatisch macht.

### Was anders machen?

> [!info] Für neue Projekte
> `/wrapup` ist aktuell nur für dieses Projekt (Junction in `.claude/skills/`).
> Bei neuem Projekt: Junction manuell anlegen oder `npx skills add` mit eigenem Repo nutzen.

## Daily highlights

- Globale CLAUDE.md gibt Claude jetzt projekt-übergreifende Arbeitsregeln
- Skills in Claude Code = `.claude/skills/[name]` als Junction → `.agents/skills/[name]`
- `/wrapup` funktioniert jetzt als echter Slash-Command (74 Skills gesamt)

## Verknüpfte Notes

- [[Projects/Build My Second Brain]]
