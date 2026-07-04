# 2026-06-08 — Cafe Roller V3 gebaut und animiert

## Was wurde gemacht
- `CLAUDE.md` repariert — 2 veraltete Pfade korrigiert (`SecondBrain/` → `wagerik-second-brain/`, fehlendes `kunden/`-Prefix im Hosting-Pfad)
- `index-v3.html` + `style-v3.css` neu erstellt: komplett anderes Design als V2 ("Warm Editorial Block")
- Vollständiges Animation-Upgrade auf V3 durchgeführt:
  - Clip-Path Wipe-Reveals (`inset(0 0 100% 0)` und horizontal `inset(0 100% 0 0)`)
  - Hero-Parallax mit 3 unterschiedlichen Scroll-Speeds (Motion.one `scroll()`)
  - Bento-Cards 3D-Tilt via CSS Custom Properties + `mousemove`
  - Stat-Counter (1900→2019) mit rAF ease-out
  - Glassmorphism-Nav (`backdrop-filter: blur(16px)` beim Scrollen)
  - Float-Label-Formular (CSS `:placeholder-shown`, Label nach Input)
  - Modal Scale-In-Animation (`visibility+opacity` statt `display:none`)
  - Staggered Mobile-Drawer-Link-Reveal
- Screenshots mit Playwright (Node.js lokal) erstellt und reviewed

## Entscheidungen
- **Motion.one v10** statt React+Framer Motion — gleiche API, CDN-kompatibel, kein Build-Tool nötig
- **"Warm Editorial Block"** Design: cream Hintergrund, hard-edged navy/rot/gold Farbblöcke, Oswald 700 Bold Headlines
- `visibility+opacity` statt `display:none` für Modal-Transitions (CSS transitions funktionieren nicht mit display:none)
- Float-Label-Trick: `placeholder=" "` (Leerzeichen) damit `:placeholder-shown` den leeren Zustand erkennt

## Offene Punkte / Next Steps
- [ ] Impressum + Datenschutz: echte Betreiberdaten eintragen
- [ ] Telefonnummer eintragen
- [ ] Unsplash-Platzhalter durch echte Fotos ersetzen
- [ ] Formspree auf echtem Server testen
- [ ] Motion.one CDN in DevTools prüfen (kein 404)
- [ ] Entscheiden: V2 oder V3 als finale `index.html` für Netlify

## Verknüpfte Notes
- [[Projects/Cafe-Roller-Frankenbad]]
