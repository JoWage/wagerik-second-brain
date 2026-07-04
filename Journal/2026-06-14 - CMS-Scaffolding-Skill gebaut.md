---
date: 2026-06-14
tags:
  - Journal
  - Daily
---

# 2026-06-14 — CMS-Scaffolding-Skill & Agency-Link

## Was wurde gemacht
- **Wagener & Rickert Footer-Link** ins CMS gebracht: neues `agencySettings`-Schema (`agencyUrl`), in `index.html` als `#footer-agency-link` verdrahtet. Sichtbarkeit über **Rollen-Check** in `structure.js` (`context.currentUser.roles` → administrator) — nur Agentur, nicht der Café-Betreiber (Editor).
- **Formspree-Briefing** erstellt (`BRIEFING-Formspree.html` + PDF): Kunde erstellt selbst Account → Form-ID → trägt sie im CMS ein.
- **`/cms`-Skill gebaut** — Komplettpaket-Scaffolding für neue Kunden: 21 Dateien (SKILL.md + 11 universelle Schemas + Studio-Config + JS-Integrationskit + 2 Briefing-Vorlagen + CLAUDE.md-Vorlage), registriert per Junction in `.claude/skills/cms`.
- **Second Brain verankert**: [[Techniques/CMS-Scaffolding-Skill]] neu, bidirektional verlinkt mit Headless-CMS-Note, Café-Roller- und Wagerick-Studio-Projektnoten.

## Entscheidungen
- `/cms`: **Komplettpaket** + branchenspezifische Schemas werden **aus der Kunden-Website abgeleitet** (keine festen Presets).
- Agency-Link über **Rollen-Check** statt nur Sidebar-Ausblenden — sauberere Trennung Agentur/Kunde.
- `/cms` vorerst **nicht** an Welte & Marqua getestet (auf Wunsch).

## Offene Punkte / Next Steps
- [ ] index.html-Änderungen (u.a. Agency-Link) auf **Netlify** deployen — Studio ist live, Website-HTML noch nicht.
- [ ] `/cms` beim ersten echten Lauf: einmalig `npx sanity login`.
- [ ] Welte & Marqua als erster `/cms`-Testkandidat, wenn gewünscht.

## Verknüpfte Notes
- [[Projects/Cafe-Roller-Frankenbad]]
- [[Projects/Wagerick-Studio]]
- [[Techniques/CMS-Scaffolding-Skill]]
- [[Techniques/Headless-CMS-mit-Sanity]]
