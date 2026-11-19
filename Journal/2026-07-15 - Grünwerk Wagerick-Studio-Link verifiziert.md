# 2026-07-15 — Grünwerk Wagerick-Studio-Link verifiziert

## Was wurde gemacht
- Geprüft, ob der Footer-Link „Website von Wagerick Studio" auf der Grünwerk-Website im privaten Sanity-Bereich steuerbar ist
- Ergebnis: Feature war bereits vollständig gebaut — Schema `agencySettings` (admin-only Singleton, Feld `agencyUrl`), in `structure.js` nur für Administratoren sichtbar, in `index.html`/`netlify-deploy/index.html` per GROQ auf `#footer-agency-link` verdrahtet (inkl. `target="_blank"`/`rel="noopener"`)
- Kunden-`CLAUDE.md` mit bestätigtem Stand aktualisiert (CMS-Abschnitt + Open Todos)
- Memory `project_welte_marqua_cms.md` ergänzt

## Entscheidungen
- Keine Code-Änderung nötig, nur Dokumentation nachgezogen

## Offene Punkte / Next Steps
- [ ] Emil & Tom als Editor ins Sanity-Projekt einladen
- [ ] Rechtsform/Firmierung + USt-IdNr. im CMS eintragen
- [ ] Formspree-AV-Vertrag abschließen
- [ ] Rechtsfrage Vertretung bei Minderjährigkeit klären
- [ ] Echte Fotos & Logo einpflegen
- [ ] Domain registrieren

## Verknüpfte Notes
- [[Projects/Gartenservice Welte Marqua - Website]]
