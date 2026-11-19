---
priority: 1
date_from: 2026-01-01
date_to:
tags:
  - Project
  - Wagerick
  - Business
last updated: 2026-07-06
---

## Objective

Wagerick Studio als funktionierendes Webdesign-Sidebusiness aufbauen — wiederkehrende lokale Kunden in Bonn / Sankt Augustin, standardisierter Stack, skalierbare Prozesse.

## Key Results

- [ ] Erstes Kundenprojekt live schalten (Cafe Roller Frankenbad)
- [ ] Angebots- und Vertragsvorlage fertigstellen
- [ ] Pricing-Modell definieren (Einmalig + Wartungspauschale)
- [ ] Lead-Pipeline etablieren (Lead-Finder Tool in `tools/lead-finder/`)
- [ ] 3 zahlende Kunden bis Ende 2026

## Stakeholders

- [[Jonathan Wagener]] — Gründer, Entwicklung
- Lukas Rickert — Partner, Co-Founder

## Standard-Stack

| Komponente | Tool |
|-----------|------|
| Design / No-Code | Framer |
| Custom HTML-Seiten | HTML / CSS / JS (kein Build-Tool) |
| CMS (Premium) | Sanity v5 |
| Hosting | Netlify |
| Formulare | Formspree |
| Domain | Kunde beschafft |

## Pricing-Modell (Entwurf)

| Paket | Leistung | Preis |
|-------|---------|-------|
| Basis | Statische Website, 5 Sektionen | einmalig |
| Premium | + Sanity CMS, Kunde pflegt selbst | einmalig + ~20–40 €/Mo Wartung |

## Aktive Projekte

- [[Projects/Cafe-Roller-Frankenbad]] — Website in Entwicklung (HTML/CSS/JS + Sanity CMS)
- [[Projects/Piazza-Siciliana-da-Sebastiano]] — Akquise-Demo in Arbeit (Restaurant, Sankt Augustin-Hangelar)
- [[Prysm - Elektro Preisvergleich]] — Eigenprodukt SaaS, Testkunde [[ELTESA - Thorsten Sawade]]

## Prozesse & Skills

- **`/cms <kunde>`** — scaffoldet ein komplettes Sanity-CMS für neue Kunden (Premium-Paket) in einem Befehl → [[Techniques/CMS-Scaffolding-Skill]]. Macht das Premium-Paket schnell wiederholbar.

## Zuletzt gemacht (2026-07-06)

Mac-Umzug Status-Check: Backup-Stand geprüft (Claude-Config-ZIP + MCP-Liste vorhanden, SSH-Backup fehlt), alle 7 Git-Repos nur-lesend auf Push-Stand geprüft. Details → [[Journal/2026-07-06 - Mac-Umzug Status-Check]].

**Offene Punkte:**
- [ ] `leads.csv.xlsx` manuell aus iCloud-Trash retten
- [ ] SSH-Key-Standort klären, `ssh-backup.zip` nachholen
- [ ] `wagerik-second-brain`-Vault: uncommitted changes committen & pushen?
- [ ] `git-repos-liste.txt` ist spurlos verschwunden — Ursache klären, ggf. neu erstellen
- [ ] Auf Mac: Repos klonen, Azure-PAT für EuroSopePlugIn einrichten

## See Also

- [[Jonathan Wagener]]
- [[Areas/Webdesign]]
- [[Techniques/Headless-CMS-mit-Sanity]]
- [[Techniques/CMS-Scaffolding-Skill]]
