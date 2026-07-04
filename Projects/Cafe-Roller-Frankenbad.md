---
priority: 1
date_from: 2026-06-01
date_to:
tags:
  - Project
  - Webdesign
  - Kunde
last updated: 2026-06-18
---

## Objective

Website für Cafe Roller Frankenbad live schalten mit Sanity CMS — Kunde kann alle Inhalte selbst pflegen. Fertig wenn: echte Fotos + Betreiberdaten im Studio, Formspree getestet, auf Netlify deployed.

## Key Results

- [ ] Betreiberdaten im Sanity Studio eintragen (Name, Privatadresse, USt-ID)
- [ ] Telefonnummer beim Kunden erfragen + im Studio eintragen
- [ ] Echte Fotos im Studio hochladen (Galerie, Team, About)
- [ ] Formspree auf echtem Server testen (Form-ID: `mjgzdwob`)
- [x] Netlify-Domain in Sanity CORS Origins eintragen → `cosmic-hummingbird-49511b.netlify.app`
- [ ] Go-live mit Kunde absprechen + Studio übergeben
- [ ] index.html-Änderungen auf Netlify deployen (Agency-Link, Standort/Headings dynamisch)
- [ ] Kunde als **Editor** (nicht Admin) ins Studio einladen
- [x] Sanity Studio deployt: `https://cafe-roller-frankenbad.sanity.studio`
- [x] Sanity CMS vollständig in index.html integriert (alle Sektionen dynamisch)
- [x] Seed ausgeführt: 33 Menu Items, 9 Dokumente importiert
- [x] CORS: localhost:3333 + `cosmic-hummingbird-49511b.netlify.app` eingetragen, lokal + live getestet
- [x] Google Maps Embed fix (hardcodiert, kein Sanity-Override)
- [x] Mobile Nav: schließt automatisch bei Link-Klick
- [x] Datenschutzerklärung: Portable Text aus Sanity, mit Styling
- [x] Impressum: alle Felder dynamisch aus Sanity (mehrzeilige Adressfelder)

## Stakeholders

- [[Jonathan Wagener]] — Developer (Wagerick Studio)
- [[People/Cafe-Roller-Frankenbad]] — Kunde

## Technische Details

| Aspekt | Wert |
|--------|------|
| Aktive Datei | `kunden/cafe-roller-frankenbad/index.html` |
| Sanity Project-ID | `deuzbc3c` |
| Sanity Dataset | `production` (public) |
| Sanity Studio | `https://cafe-roller-frankenbad.sanity.studio` |
| Hosting | Netlify, Ordner `kunden/cafe-roller-frankenbad/` |
| Formspree Form-ID | `mjgzdwob` |
| Lokales Testen | `npx serve "kunden\cafe-roller-frankenbad" -l tcp://localhost:3333` |

**Sanity Schemas (16):** siteSettings, agencySettings, heroContent, legalContent, aboutContent, sectionHeadings, locationContent, menuCategory, menuItem, drinkModal, allergen, newsItem, galleryImage, qualityPillar, teamMember, blockContent

## Progress

### Current Status

- 2026-06-18 — Sanity-Deployment-Checkliste geprüft (siehe [[Journal/2026-06-18 - Sanity CORS Doku-Korrektur]]): Code saubere, CLAUDE.md-CORS-Status war veraltet, korrigiert. Live-URL: `https://cosmic-hummingbird-49511b.netlify.app/`
- 2026-06-14 — Agency-Link (Wagener & Rickert) im Footer über `agencySettings` editierbar, nur für Admins sichtbar (Rollen-Check in structure.js). Formspree-Briefing erstellt. Café Roller diente als Vorlage für den neuen [[Techniques/CMS-Scaffolding-Skill]]. **Offen:** index.html-Änderungen auf Netlify deployen.
- 2026-06-10 — "In guten Kreisen"-Sektion komplett entfernt (Kundenmitteilung: Laden nicht mehr ihr), Nav-Desktop-Bug gefixt, Galerie-Hintergrund dunkelblau
- 2026-06-09 — Maps-Bug behoben (Sanity-Override entfernt), Nav Auto-Close mobile, Datenschutz + Impressum komplett aus Sanity, alle Adressfelder mehrzeilig, Studio deployed
- 2026-06-08 — Sanity CMS vollständig in V1 (index.html) integriert. Seed-Daten importiert. Studio deployt.
- 2026-06-08 — V3 "Warm Editorial Block" fertig gebaut (Motion.one, archiviert)
- 2026-06-01 — V2 "Elevated Brand + Cinematic Scroll" erstellt (GSAP + Lenis, archiviert)

### Decisions Made

- **Aktive Version:** `index.html` (V1) — V2/V3 archiviert
- **CMS:** Sanity v5 (Node.js v26 kompatibel), client-side Fetch, kein Build-Tool
- **Google Maps:** Fix hardcodiert in HTML, kein Sanity-Feld (X-Frame-Options-Problem bei normalem Maps-Link)
- **Hosting:** Netlify

### Blockers

- Echte Fotos und Betreiberdaten noch nicht vom Kunden erhalten

## Related Journals

```base
filters:
  and:
    - file.inFolder("Journal")
properties:
  file.name:
    displayName: Title
  note.date:
    displayName: Date
  note.tags:
    displayName: Tags
views:
  - type: table
    name: Journals
    filters:
      and:
        - file.hasLink(this.file)
    sort:
      - property: date
        direction: DESC
    columnSize:
      file.name: 420
```

## See Also

- [[People/Cafe-Roller-Frankenbad]]
- [[Areas/Webdesign]]
- [[Techniques/Headless-CMS-mit-Sanity]]
- [[Techniques/CMS-Scaffolding-Skill]] — dieses Projekt ist die Vorlage für den `/cms`-Skill
