---
type: technique
tags: [cms, sanity, skill, automation, client-features, scaffolding]
related: "[[Techniques/Headless-CMS-mit-Sanity]], [[Projects/Cafe-Roller-Frankenbad]]"
created: 2026-06-14
updated: 2026-06-14
status: produktiv
---

# CMS-Scaffolding-Skill (`/cms`)

## Context

> [!info] Problem
> Jeder neue Kunde braucht dasselbe Sanity-CMS-System wie [[Projects/Cafe-Roller-Frankenbad]] — Studio, Schemas, JS-Anbindung, Briefings, CLAUDE.md. Das von Hand zu wiederholen ist langsam und fehleranfällig. Aufbauend auf [[Techniques/Headless-CMS-mit-Sanity]] gibt es jetzt einen **Claude-Code-Skill**, der das in einem Befehl scaffoldet.

## Approach

> [!tip] Idee
> Der Befehl **`/cms <kunde-slug>`** baut für einen Kunden, dessen Website schon steht, ein komplettes CMS nach dem Café-Roller-Vorbild. ~11 universelle Schemas sind als Vorlagen hinterlegt; **branchenspezifische Schemas (Speisekarte/Leistungen/Produkte) leitet Claude aus der vorhandenen `index.html` ab** — keine festen Presets.

**Trennung der Verantwortlichkeiten:**
- **Universell (Vorlage, 1:1):** siteSettings, agencySettings, heroContent, legalContent, aboutContent, sectionHeadings, locationContent, newsItem, galleryImage, teamMember, blockContent + die JS-Helfer (`imgUrl`, `ptHtml`, fetch-Bootstrap, fadeIn/Fallback).
- **Bespoke (abgeleitet):** alles, was die jeweilige Branche braucht — nach Café-Roller-Mustern (orderRankField, Referenzen, Detail-Popups, gefilterte Kategorie-Listen).

## Process

> [!note] Was der Skill tut
> Voller Ablauf in `.agents/skills/cms/SKILL.md`. Kurzform:

1. **Analyse:** Kunden-`index.html` lesen → Sektionen + DOM-Selektoren + Branchen-Inhalte erfassen.
2. **Projekt:** `sanity init` → neues Sanity-Projekt (Dataset `production` public), Project-ID abgreifen.
3. **Studio:** Vorlagen aus `templates/studio/` kopieren, Platzhalter ersetzen, `npm install`, Branchen-Schemas generieren, in `index.js` + `structure.js` einhängen.
4. **Anbindung:** `templates/integration/cms-integration.js` in die `index.html` einsetzen, `apply*()` an echte Selektoren anpassen, GROQ um Branchen-Typen erweitern.
5. **Briefings + CLAUDE.md:** aus Vorlagen → PDF via Edge headless.
6. **Deploy + Verify:** `sanity schema validate`, `sanity deploy`, lokal auf `:3333` testen, Go-live-Checkliste.

## Insights

> [!tip] Gelernt
> - `orderableDocumentListDeskItem` ist **lowercase** und gibt schon ein listItem zurück (nicht wrappen).
> - `orderRankField({type:...})` — Parameter heißt `type`, nicht `section`.
> - GROQ-Bild-Refs **nie** mit `asset->{_ref}` (wird `null`) — roh laden.
> - `sanity.cli.js` nutzt `studioHost`, nicht `deployment.appId`.
> - agencySettings (Agentur-Link) nur für **Admins** sichtbar → Rollen-Check in `structure.js`; Kunde wird als **Editor** eingeladen.

## Outputs

> [!example] Artefakte
> - Skill: `.agents/skills/cms/` (SKILL.md + `templates/`), registriert per Junction in `.claude/skills/cms`.
> - Referenz-Implementierung: [[Projects/Cafe-Roller-Frankenbad]].

## See Also

- [[Techniques/Headless-CMS-mit-Sanity]] — technische Grundlagen (GROQ, Portable Text, CORS, Gotchas)
- [[Projects/Cafe-Roller-Frankenbad]] — das Original, aus dem die Vorlagen generalisiert wurden
- [[Projects/Wagerick-Studio]] — Studio-Workflow
