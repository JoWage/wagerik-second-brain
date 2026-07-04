# 2026-06-10 — Cafe Roller: IGK entfernt, Nav-Fix, Galerie

## Was wurde gemacht
- "In guten Kreisen"-Sektion komplett aus `index.html` entfernt (Nav-Link, CSS, HTML-Sektion, Kontakt-Block, Bohnen-Hinweis, JS `applyShop` + Query)
- Sanity Studio vollständig bereinigt: `shopPartner.js` gelöscht, aus `schemas/index.js` entfernt, `seed.mjs` gesäubert, Studio neu deployed (`npx sanity deploy`), Dokument aus DB gelöscht (`npx sanity documents delete shopPartner`)
- Nav-Bug gefixt: auf Desktop öffnete sich das Mobile-Dropdown beim Klick auf Nav-Links — `toggleNav()` jetzt nur noch auf Mobile (`offsetParent !== null` Check)
- Galerie-Sektion: Hintergrund auf `#071429` (dunkelblau wie alter IGK-Abschnitt), Überschrift + Label weiß/akzentfarben
- 13 Skills von `Leonxlnx/taste-skill` im Projekt-Root installiert (`design-taste-frontend`, `high-end-visual-design`, `stitch-design-taste` u.a.)

## Entscheidungen
- Kundenmitteilung: Cafe Roller besitzt den Laden "in guten Kreisen" nicht mehr → alle Referenzen entfernt
- Skills im Projekt-Root `Website SIdehussle/.agents/skills/` (nicht global, nicht im Unterordner)

## Offene Punkte / Next Steps
- [ ] Netlify-Deploy mit den aktuellen Website-Änderungen durchführen
- [ ] Galerie-Bilder durch echte Kundenfotos ersetzen
- [ ] Betreiberdaten im Studio eintragen
- [ ] Telefonnummer beim Kunden erfragen

## Verknüpfte Notes
- [[Projects/Cafe-Roller-Frankenbad]]
