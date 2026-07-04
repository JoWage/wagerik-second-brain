# 2026-06-08 — Sanity Seed und lokaler Test

## Was wurde gemacht
- CORS für `http://localhost` in Sanity eingetragen → lokaler Test auf port 3333 erfolgreich
- `seed.mjs` erstellt: alle Inhalte aus index.html per `@sanity/client` API in Sanity eingetragen
- Seed ausgeführt: siteSettings, heroContent, aboutContent, 4 Kategorien, 33 Menu Items, 5 Qualitätssäulen, 3 News, shopPartner, legalContent (Platzhalter)
- Token-Problem: erster Token war Viewer → kein Schreibrecht → neuer Editor-Token erstellt
- Bash vs. PowerShell: `$env:` funktioniert nur in PowerShell, nicht via `!`-Befehl (Bash)

## Entscheidungen
- `seed.mjs` mit fixen `_id`s und `createOrReplace` → idempotent, kann beliebig oft ausgeführt werden
- Bilder können per Script nicht hochgeladen werden → manuell im Studio

## Offene Punkte / Next Steps
- [ ] Beide API-Tokens in sanity.io/manage löschen (im Chat sichtbar)
- [ ] Telefonnummer + Betreiberdaten im Studio eintragen (siteSettings)
- [ ] Echte Datenschutzerklärung im Studio eintragen (legalContent)
- [ ] Bilder hochladen: Galerie, Team, About, Shop
- [ ] localhost:3333 neu laden und Content mit echten Sanity-Daten prüfen
- [ ] Netlify Deploy

## Verknüpfte Notes
- [[Projects/Cafe-Roller-Frankenbad]]
- [[Techniques/Headless-CMS-mit-Sanity]]
