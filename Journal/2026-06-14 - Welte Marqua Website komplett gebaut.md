---
date: 2026-06-14
tags:
  - Journal
  - Gartenservice
  - Entwicklung
---

# 2026-06-14 — Welte Marqua Website komplett gebaut

## Was wurde gemacht
- `emil-design-eng` Skill installiert (Emil Kowalski's UI-Animations-Philosophie)
- Kundenordner `welte-marqua-gartenservice` gelesen und Spec aus CLAUDE.md aufgenommen
- Implementierungsplan erstellt und genehmigt
- `index.html` komplett gebaut: alle 8 Sektionen, CDN-Imports, Kontaktformular, Preistabelle (3 Pakete), FAQ (5 Fragen), Galerie + Vorher-Nachher-Slider
- `style.css` gebaut: Custom Properties, Glassmorphism-Nav, vollständig responsive (320px–1440px+), `prefers-reduced-motion`, `hover: hover` Media Queries
- `main.js` gebaut: Lenis Smooth Scroll, Three.js Partikel-Hero mit WebGL-Fallback, GSAP ScrollTrigger Animationen für alle Sektionen, Pointer-Capture VN-Slider, FAQ Accordion, Formspree-Submit mit JS
- Lokale Verifikation: 37/38 Checks bestanden, Server läuft auf Port 4321

## Entscheidungen
- Platzhalter-Firmenname: **„Grünwerk"** — 3 Vorschläge als HTML-Kommentar oben in `index.html`
- Three.js Konzept: Partikel-System (~180 Partikel in Grüntönen) statt 3D-Mesh — performanter & eleganter
- SRI-Hashes: vorerst nur `crossorigin="anonymous"` + TODO-Kommentar (falsche Hashes würden die Library-Loads blockieren — vor Go-live via srihash.org ergänzen)
- Emil-Design-Eng Regeln konsequent angewendet: `ease-out` durchgehend, `scale(0.97)` auf `:active`, `scale(0.95)` + opacity statt `scale(0)`, stagger max 80ms

## Offene Punkte / Next Steps
- [ ] Firmenname mit Emil & Tom abstimmen (Vorschläge: Grünwerk / Welte & Marqua Gartenservice / GartenWerk Bonn)
- [ ] Eigene Fotos einpflegen (Galerie + Hero + Über-uns)
- [ ] Logo erstellen und einpflegen
- [ ] Formspree Account anlegen → Placeholder-URL ersetzen
- [ ] SRI-Hashes vor Go-live ergänzen (srihash.org)
- [ ] Impressum & Datenschutz erstellen (DSGVO)
- [ ] Domain registrieren
- [ ] Netlify Deployment aufsetzen

## Verknüpfte Notes
- [[Projects/Gartenservice Welte Marqua - Website]]
- [[People/Emil Welte]]
- [[People/Tom Marqua]]
