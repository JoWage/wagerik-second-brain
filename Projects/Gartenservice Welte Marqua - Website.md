---
priority: high
date_from: 2026-06-14
date_to:
tags:
  - Project
last updated: 2026-06-18
zuletzt gemacht: 2026-06-18 — Sanity-Deployment-Checkliste geprüft, CORS-Doku korrigiert (war bereits live eingetragen)
---

## Objective

Landing Page für den neuen Gartenservice von Emil Welte & Tom Marqua bauen. Ziel: Lokale Kunden in Bonn / Sankt Augustin über das Kontaktformular generieren. Website soll premium wirken und mit 3D- und Scroll-Animationen beeindrucken.

## Key Results

- [x] Vollständige Landing Page (alle 8 Sektionen) fertiggestellt — 2026-06-14
- [x] V2-Redesign „Gewachsene Präzision": Branching-Lines-Hero (Three.js), lokale Fonts, echte Legal-Seiten, SRI-Hashes — 2026-06-17
- [x] Lenis + GSAP Scroll-Animationen laufen
- [x] Vorher/Nachher-Slider-Bug gefixt (Label-Sichtbarkeit + falsche Bild/Label-Zuordnung) — 2026-06-17
- [x] Paket-Vorauswahl bei Preiskarten + Formspree-Subject/Honeypot — 2026-06-17
- [x] Hero-Hintergrundfoto hinter 3D-Animation integriert — 2026-06-17
- [x] Sanity-CMS aufgesetzt: 10 Schemas, In-Place-Integration (kein innerHTML-Rebuild), Legal-Daten zentral, Studio deployed unter welte-marqua-gartenservice.sanity.studio — 2026-06-17
- [ ] Kontaktformular via Formspree funktioniert (Placeholder-URL steht, Konto fehlt noch)
- [x] Website auf Netlify deployed → `https://effulgent-monstera-c08996.netlify.app/`
- [ ] Firmenname mit Kunden abgestimmt
- [ ] Eigene Fotos & Logo eingepflegt
- [ ] Emil & Tom als Editor ins Sanity-Projekt einladen
- [x] `netlify-deploy/`-Ordner mit nur Deploy-relevanten Dateien angelegt — 2026-06-17
- [x] Hero-Bild-Änderbarkeit über CMS bestätigt (Code-Review) — 2026-06-17

## Stakeholders

- [[Emil Welte]] — Kunde / Mitgründer
- [[Tom Marqua]] — Kunde / Mitgründer
- Jonathan Wagener — Projektleitung Wagerick Studio
- Lukas Rickert — Entwicklung / Design

## Progress

### Current Status

**2026-06-18:** Sanity-Deployment-Checkliste geprüft (siehe [[Journal/2026-06-18 - Sanity CORS Doku-Korrektur]]) — Code saubere, kein localhost-Leak. CLAUDE.md-Status zu CORS war veraltet (suggerierte "noch offen"), tatsächlich bereits eingetragen: `effulgent-monstera-c08996.netlify.app`. Website ist bereits live auf Netlify.

**Sanity-CMS steht (2026-06-17).** Studio live unter https://welte-marqua-gartenservice.sanity.studio, Schema validiert (0 Fehler), lokal mit Test-Daten verifiziert (DOM-Dump + Screenshot via Edge headless — alle Werte korrekt injiziert, keine JS-Fehler, Test-Dokumente danach wieder gelöscht). Integration ist „In-Place-Override" statt Café-Roller-Standard (innerHTML-Rebuild + fadeIn), weil die Website bereits vollständigen Content + feste GSAP-Animationen hatte — siehe [[Cafe-Roller-Frankenbad]] für den Vergleichsfall. Zusätzlich `netlify-deploy/`-Ordner mit nur den Deploy-relevanten Dateien angelegt (ohne CLAUDE.md/Sanity-Studio/Briefings) — direkt per Drag&Drop auf Netlify hochladbar. Hero-Bild-Änderbarkeit über CMS per Code-Review bestätigt (Live-Bildtest scheiterte nur an einem kaputten Test-Base64, nicht an der Anbindung). Wartet noch auf: Firmenname, eigene Fotos, Formspree-Konto, Domain, Netlify, Editor-Einladung für Emil & Tom.

### Decisions Made

- Stack: HTML/CSS/JS Custom (kein Framer) — wegen 3D & Animationen
- Libraries: GSAP + ScrollTrigger, Three.js, Lenis
- Formular: Formspree (mit dynamischem Subject je Paket + Honeypot)
- Hosting: Netlify
- Firmenname: noch offen — 3 Vorschläge im HTML-Kommentar: „Grünwerk" / „Welte & Marqua Gartenservice" / „GartenWerk Bonn"; Platzhalter aktuell: Grünwerk
- Three.js: prozedurales Branching-Lines-System (ersetzt V1-Partikelsystem), Canvas transparent für Hintergrundfoto, WebGL-Fallback auf CSS-Gradient
- Preiskarten verlinken mit Paket-Vorauswahl direkt ins Kontaktformular
- CMS: Sanity v5, Project-ID `utrjsi6k`, Dataset `production` (public). In-Place-Override statt Listen-Rebuild (siehe [[Headless-CMS-mit-Sanity]]), feste Anzahl Leistungen/Pakete/FAQ — dokumentierte Grenze, kein Add/Remove durch Kunde ohne Dev

### Blockers

- Firmenname nicht festgelegt
- Keine Fotos / kein Logo vorhanden

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

- [[Emil Welte]]
- [[Tom Marqua]]
- `kunden/welte-marqua-gartenservice/CLAUDE.md`
- [[Wagerick-Studio]]
