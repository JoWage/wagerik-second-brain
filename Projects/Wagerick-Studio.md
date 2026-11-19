---
priority: 1
date_from: 2026-01-01
date_to:
tags:
  - Project
  - Wagerick
  - Business
last updated: 2026-11-19
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

## Repo-Landschaft (seit 2026-11-19, Git-first)

Vier eigenständige private GitHub-Repos unter `C:\Users\sandr\dev\` — kein Cloud-Sync (OneDrive/iCloud) mehr als Arbeitsort. `wagerick-studio` (dieses Repo), `wagerik-second-brain`, `prysm`, `euroscope-gnd-plugin`. Details → `CLAUDE.md` im Repo-Root, Memory → [[project_git_first_migration]] (Memory-Ordner von `dev\wagerick-studio`).

## Prozesse & Skills

- **`/cms <kunde>`** — scaffoldet ein komplettes Sanity-CMS für neue Kunden (Premium-Paket) in einem Befehl → [[Techniques/CMS-Scaffolding-Skill]]. Macht das Premium-Paket schnell wiederholbar.
- **`/wrapup`** — Session-Abschluss: Journal-Eintrag + Projekt-Note-Update + Memory-Konsolidierung in einem Befehl.

## Zuletzt gemacht (2026-11-19)

Git-first-Migration abgeschlossen: vier Repos unter `dev/` angelegt, Inhalt aus OneDrive/iCloud zusammengeführt und verifiziert, beide Custom-Skills (`/cms`, `/wrapup`) migriert und korrigiert, Memory auf die vier neuen Projekt-Namespaces verteilt, Vault aufgeräumt (Template-Demos archiviert, `Areas/Webdesign` gefüllt). Details → [[Journal/2026-11-19 - Git-Migration und Vault-Aufräumen]].

**Offene Punkte:**
- [ ] Auf Mac: alle vier Repos nach `~/dev/...` klonen
- [ ] Zwei Dateigruppen aus `iCloudDrive\Wagerick-Business` nachkopieren (iCloud-Cloud-Timeout verhinderte Migration — eine Vorlagen-E-Mail, 6 Dateien im `eiscafe-giardino`-Archiv)
- [ ] `iCloudDrive\Wagerick-Business` umbenennen/archivieren (Zugriff zum Migrationszeitpunkt verweigert)
- [ ] Alten OneDrive-Projektordner nach Sessionende selbst archivieren

## See Also

- [[Jonathan Wagener]]
- [[Areas/Webdesign]]
- [[Techniques/Headless-CMS-mit-Sanity]]
- [[Techniques/CMS-Scaffolding-Skill]]
