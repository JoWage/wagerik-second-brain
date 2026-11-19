---
priority: high
date_from: 2026-06-14
date_to:
tags:
  - Project
last updated: 2026-07-15
zuletzt gemacht: 2026-07-15 — Wagerick-Studio-Footer-Link verifiziert: war bereits vollständig über `agencySettings` (admin-only) steuerbar, nur CLAUDE.md/Memory nachdokumentiert
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
- [x] Kontaktformular via Formspree funktioniert → echte Form-ID `xgojdnbe` (von Emil & Tom selbst in Sanity eingetragen, 2026-07-05), AV-Vertrag steht noch aus
- [x] Website auf Netlify deployed → `https://effulgent-monstera-c08996.netlify.app/`
- [ ] Firmenname final abgestimmt (bleibt vorerst „Grünwerk"), Rechtsform/Firmierung noch offen
- [ ] Eigene Fotos & Logo eingepflegt
- [ ] Emil & Tom als Editor ins Sanity-Projekt einladen
- [x] `netlify-deploy/`-Ordner mit nur Deploy-relevanten Dateien angelegt — 2026-06-17
- [x] Hero-Bild-Änderbarkeit über CMS bestätigt (Code-Review) — 2026-06-17
- [x] Impressum/Datenschutz mit echten Kundendaten (Adresse, Telefon, E-Mail) aus Sanity befüllt — 2026-07-13, USt-IdNr./Kleinunternehmerstatus noch offen
- [x] Formular-Feld „Häufigkeit" → „Werkzeug vor Ort" (vorhanden/muss mitgebracht werden) — 2026-07-13
- [x] Neues CMS-Feld `operatorLegalForm` (Rechtsform) angelegt + Sanity Studio redeployed — 2026-07-13
- [x] Hinweis-Boxen („vor Go-live entfernen") + Minderjährigkeits-Hinweis unter „Vertreten durch" aus dem Impressum entfernt — 2026-07-13 (auf Jonathans Wunsch, rechtliche Frage bleibt separat offen)

## Stakeholders

- [[Emil Welte]] — Kunde / Mitgründer
- [[Tom Marqua]] — Kunde / Mitgründer
- Jonathan Wagener — Projektleitung Wagerick Studio
- Lukas Rickert — Entwicklung / Design

## Progress

### Current Status

**2026-07-15:** Jonathan wollte den Footer-Link „Website von Wagerick Studio" im privaten Sanity-Bereich steuerbar machen. Check ergab: bereits vorhanden — `agencySettings` (admin-only Singleton, Feld `agencyUrl`) ist deployed und in `index.html`/`netlify-deploy/index.html` per GROQ auf `#footer-agency-link` verdrahtet. Kein neuer Code, nur Kunden-CLAUDE.md und Memory nachdokumentiert.

**2026-07-13 (fortgeführt):** Neues Sanity-Feld `operatorLegalForm` (Rechtsform/Firmenzusatz) angelegt, Studio neu deployed (`node_modules` fehlte im iCloud-Ordner, `npm install` nötig; appId jetzt in `sanity.cli.js` hinterlegt, kein erneuter Prompt mehr). Impressum-Logik injiziert Rechtsform/USt-ID/Verantwortlichen jetzt automatisch aus dem CMS und entfernt dabei das Placeholder-Styling. Auf Jonathans ausdrücklichen Wunsch wurden die gelben „Hinweis (vor Go-live entfernen)"-Boxen sowie der Minderjährigkeits-Hinweis unter „Vertreten durch" aus dem Impressum entfernt — **die zugrunde liegenden rechtlichen Fragen (Rechtsform, USt-Status, Vertretung bei Minderjährigkeit) sind damit nicht gelöst, nur nicht mehr auf der Website sichtbar.** `netlify-deploy/`-Ordner wurde nach jeder Änderung gegen den Hauptordner verglichen und ist vollständig synchron.

**2026-07-13:** Kontaktformular-Feld „Häufigkeit" durch „Werkzeug vor Ort" (vorhanden / muss mitgebracht werden) ersetzt — in `index.html` + `netlify-deploy/index.html`. Beim Blick in Sanity zeigte sich, dass Emil & Tom zwischenzeitlich (2026-07-05) bereits reale Daten selbst eingetragen hatten: E-Mail, Telefon, Adresse und eine echte Formspree-Form-ID. Diese Werte wurden als HTML-Fallback in Impressum, Datenschutz und Formular übernommen (lokal mit `serve` verifiziert, 200 + korrekte Werte im HTML). Noch offen für den Launch: USt-IdNr./Kleinunternehmerstatus, Rechtsform/Firmierung von „Grünwerk", Formspree-AV-Vertrag, sowie die (vom Website-Text unabhängige) rechtliche Frage der geschäftlichen Mitzeichnung durch die Erziehungsberechtigten, da Emil & Tom minderjährig sind.

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

- Keine Fotos / kein Logo vorhanden
- USt-IdNr./Kleinunternehmerstatus, Rechtsform und redaktionell Verantwortlicher fehlen noch im CMS
- Formspree-AV-Vertrag nicht abgeschlossen
- Rechtsfrage der Vertretung bei Minderjährigkeit ungeklärt (nur nicht mehr auf Website sichtbar)

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
