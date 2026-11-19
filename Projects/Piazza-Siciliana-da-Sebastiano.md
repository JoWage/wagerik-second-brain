---
priority: 2
date_from: 2026-07-07
date_to:
tags:
  - Project
  - Webdesign
  - Akquise
last updated: 2026-07-08
---

## Objective

Akquise-Demo-Website für die **Piazza Siciliana da Sebastiano** (italienisches Familienrestaurant, Sankt Augustin-Hangelar) bauen, um den Betrieb als Kunden zu gewinnen. Fertig wenn: alle 7 Seiten stehen, Sanity-CMS angebunden, Demo lokal zeigbar für das Erstgespräch.

## Key Results

- [ ] Demo-Website komplett (Startseite, Restaurant, Speisekarte, Team, Kontakt, Impressum, Datenschutz)
- [ ] Vollständige Speisekarte (66 Gerichte + Getränke) 1:1 von der alten Website übernommen
- [ ] Sanity-CMS integriert + Studio deployed (Verkaufsargument: Kunde pflegt Preise selbst)
- [ ] Reservierungs- + Feedback-Formular (Formspree-Platzhalter)
- [ ] Erstgespräch mit Eugenio Triscari vereinbaren + Demo zeigen
- [ ] Bei Zusage: Migration `demos/` → `kunden/`, echte Formspree-ID, Domain, echte Foodfotos

## Stakeholders

- [[Jonathan Wagener]] — Developer (Wagerick Studio)
- [[People/Piazza-Siciliana-da-Sebastiano]] — potenzieller Kunde (Akquise)

## Technische Details

| Aspekt | Wert |
|--------|------|
| Status | **Akquise-Demo** — noch kein Kunde |
| Ordner | `Wagerick-Business/demos/piazza-siciliana-da-sebastiano/` |
| Stack | HTML/CSS/JS (kein Build-Tool) + Sanity v6 |
| Seiten | index, restaurant, speisekarte, team, kontakt, impressum, datenschutz |
| Design | Palette aus echtem Lokal: Bordeauxrot #7E211D (Logo-Schild) + Gold + Creme, Cormorant Garamond + Lora |
| Sanity Project-ID | `yfikj5l7` (Org WaRi Studio) |
| Sanity Studio | https://piazza-siciliana-da-sebastiano.sanity.studio |
| Formspree | Platzhalter-IDs (2 Formulare: Feedback + Reservierung), echte IDs via siteSettings |
| Lokales Testen | `npx serve "demos\piazza-siciliana-da-sebastiano" -l tcp://localhost:3333` |

**Sanity Schemas (12):** siteSettings, heroContent, legalContent, aboutContent, sectionHeadings, menuCategory, menuItem, menuInfo, terrasseContent, feiernContent, familyStoryContent, blockContent — locationContent/galleryImage/teamMember bewusst weggelassen (kein Frontend-Gegenstück)

## Progress

### Current Status

- 2026-07-08 — **SEO-/Polish-Pass:** Favicon (SVG, Schild-Echo), Open-Graph/Twitter-Tags auf allen öffentlichen Seiten, schema.org-Restaurant-JSON-LD + Hero-Preload auf der Startseite. Bugfix: Hero-Öffnungszeiten zeigten wörtlich `&amp;` (doppeltes Escaping in `cms-integration.js` — `esc()` vor `textContent`). Alles im Browser verifiziert.
- 2026-07-07 — **Demo komplett gebaut und verifiziert.** 7 Seiten, Sanity-CMS live (Studio deployed, 73 Gerichte + alle Inhalte geseedet, CMS-Roundtrip getestet: Änderung im Studio erscheint auf der Website). Echte Fotos der alten Wix-Seite hochauflösend übernommen (Fassade als Hero!), Unsplash-Platzhalter nur für Speisen. Offen: Erstgespräch mit Kunde. Details → `demos/piazza-siciliana-da-sebastiano/CLAUDE.md`.
- 2026-07-07 — Projekt gestartet. Alte Website (piazza-siciliana.de, Wix) analysiert: komplette Speisekarte mit Preisen extrahiert, 6 echte Fotos identifiziert (Innenraum ×4, Familienfoto, Fassade), Kontaktdaten + Öffnungszeiten übernommen.

### Decisions Made

- **Demo statt Kundenprojekt:** Ordner `demos/`, nicht `kunden/` — noch keine Zusage (2026-07-07)
- **Stack:** HTML/CSS/JS + Sanity — Framer+Sanity wurde abgewogen und verworfen (kein Präzedenzfall im Studio, Demo muss sofort fertig/zeigbar sein)
- **Design:** warm-mediterran, klassisch-traditionell (kein trendiges Editorial-Design) — passt zum 3-Generationen-Familienbetrieb
- **Seitenstruktur:** wie Original (vertraut für Stammgäste), nur professionell umgesetzt
- **Logo/Name:** unverändert übernommen, kein Rebranding
- **CSS/JS extern** (`css/style.css`, `js/cms-integration.js`) statt inline wie Café Roller — 7 Seiten teilen sich ein Stylesheet

### Blockers

- Kein Kontakt zum Betrieb bisher — Demo entsteht vor dem Erstgespräch

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

- [[People/Piazza-Siciliana-da-Sebastiano]]
- [[Projects/Cafe-Roller-Frankenbad]] — CMS-Referenzimplementierung (Vorlage für Schemas + Integration)
- [[Techniques/Headless-CMS-mit-Sanity]]
- [[Areas/Webdesign]]
