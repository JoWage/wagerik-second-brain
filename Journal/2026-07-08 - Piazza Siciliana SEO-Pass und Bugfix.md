# 2026-07-08 — Piazza Siciliana SEO-Pass und Bugfix

## Was wurde gemacht
- SEO-/Polish-Pass auf allen 7 Seiten der Akquise-Demo: Favicon (`img/favicon.svg`, ovales Schild-Echo in Bordeaux/Gold), Open-Graph- + Twitter-Card-Tags (seitenspezifisch, 5 öffentliche Seiten), schema.org-Restaurant-JSON-LD + Hero-Preload auf der Startseite
- Bugfix: Hero-Öffnungszeiten zeigten wörtlich `&amp;` — doppeltes Escaping in `js/cms-integration.js` (`esc()` vor `setText`/`textContent`); nur mit live geladenen CMS-Daten sichtbar
- Verifikation: alle Seiten + Favicon HTTP 200, JSON-LD valide, Startseite + Speisekarte im headless Edge gerendert (Screenshots)
- Sanity-CMS live gegen die API bestätigt: 73 Gerichte, 7 Kategorien, 9 Singletons, 5 Bilder — CMS komplett fertig
- Demo-CLAUDE.md + Projekt-Note aktualisiert, Feedback-Memory zum Escaping-Bug geschrieben

## Entscheidungen
- OG-/JSON-LD-Bildpfade root-relativ (`/img/…`), weil noch keine Domain existiert — Umstellung auf absolute URLs ist neuer Go-live-Checklistenpunkt
- Kein Netlify-Deploy: Demo bleibt lokal bis zur Kundenzusage; fürs Erstgespräch ggf. neutrale Netlify-Subdomain

## Offene Punkte / Next Steps
- [ ] Erstgespräch mit Eugenio Triscari vereinbaren (02241/205157) — alle weiteren Punkte kundenblockiert (Formspree, Foodfotos, Impressumsdaten, Domain-Umzug)

## Verknüpfte Notes
- [[Projects/Piazza-Siciliana-da-Sebastiano]]
- [[People/Piazza-Siciliana-da-Sebastiano]]
