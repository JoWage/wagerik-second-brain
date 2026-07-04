# 2026-06-08 — Sanity CMS Cafe Roller

## Was wurde gemacht
- `vorlagen/`-Ordner sortiert: Headless-CMS-Note → Techniques/, veraltete Project-Note gelöscht
- Vollständige Sanity CMS Integration für V1 (index.html) geplant und implementiert
- 13 Sanity-Schemas erstellt (Speisekarte, News, Öffnungszeiten, Galerie, Team, Texte, Impressum, DSE)
- index.html erweitert: Loading-Fade-in, DOM-IDs, Sanity-Fetch-Script (~250 Zeilen)
- Sanity Studio live deployed unter `https://cafe-roller-frankenbad.sanity.studio`
- Node.js v26 Kompatibilitätsproblem gelöst → Sanity v5 + React v19

## Entscheidungen
- V1 (index.html) statt V2 als CMS-Basis
- Client-side Fetch (kein Build-Tool, Netlify bleibt unverändert)
- Hosted Sanity Studio, öffentliches Dataset (kein API-Token im Client nötig)
- Datenschutz-Volltext und Impressum-Felder ebenfalls per CMS pflegbar
- Fade-in Animation: dynamische Sektionen starten `opacity:0`, faden nach Fetch ein (3-Sek-Fallback)

## Offene Punkte / Next Steps
- [ ] `http://localhost` in Sanity CORS Origins eintragen → lokalen Test abschließen
- [ ] Netlify-Domain in Sanity CORS eintragen
- [ ] Inhalte im Studio befüllen: Speisekarte, Öffnungszeiten, News, Team, Galerie, Texte
- [ ] Impressum + Datenschutz Betreiberdaten im Studio eintragen
- [ ] Netlify Deploy nach Content-Befüllung
- [ ] Telefonnummer beim Kunden erfragen

## Verknüpfte Notes
- [[Projects/Cafe-Roller-Frankenbad]]
- [[Techniques/Headless-CMS-mit-Sanity]]
