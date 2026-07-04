# 2026-06-17 — Sanity-CMS Welte-Marqua aufgesetzt

## Was wurde gemacht
- Sanity-v5-CMS für Welte & Marqua Gartenservice komplett aufgesetzt (Project-ID `utrjsi6k`, Studio deployed)
- 10 Schemas angepasst an die echte V2-Website statt Café-Roller-Standardset (kein Team/News/Standort/Portable-Text)
- CMS-Integration als "In-Place-Override" gebaut — überschreibt nur Text/`src` vorhandener DOM-Knoten, kein `innerHTML`-Rebuild/`fadeIn`
- Legal-Daten (Betreiberdaten) zentral aus `siteSettings` in `index.html` + `impressum.html` + `datenschutz.html` injiziert
- Mit Test-Dokumenten verifiziert (Edge-headless DOM-Dump + Screenshot), danach bereinigt
- Briefings für Kunde + Formspree als PDF erstellt
- `netlify-deploy/`-Ordner angelegt (nur Deploy-relevante Dateien) zum Hochladen auf Netlify
- Geprüft, dass das Hero-Bild über das CMS änderbar ist (Code-Review bestätigt; Live-Bildtest an kaputtem Test-Base64 gescheitert, nicht an der Anbindung)

## Entscheidungen
- In-Place-Override statt Standard-Café-Roller-Muster, weil Website bereits fertigen Content + feste GSAP-Animationen hatte — dokumentierte Grenze: feste Anzahl Leistungen (6) / Pakete (3) / FAQ (5)
- Legal-Daten zentral aus CMS statt manuell bei Go-live befüllt

## Offene Punkte / Next Steps
- [ ] Emil & Tom als Editor ins Sanity-Projekt einladen
- [ ] Formspree-Account anlegen + Form-ID eintragen
- [ ] Impressum-/Datenschutz-Echtdaten eintragen
- [ ] Firmenname final festlegen
- [ ] Echte Fotos (Hero, Über uns, Galerie, Vorher-Nachher) hochladen
- [ ] Domain registrieren + Netlify-Deploy + CORS-Domain in manage.sanity.io eintragen

## Verknüpfte Notes
- [[Projects/Gartenservice Welte Marqua - Website]]
- [[Techniques/Headless-CMS-mit-Sanity]]
