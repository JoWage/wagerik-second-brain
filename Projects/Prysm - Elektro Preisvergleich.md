---
priority: high
date_from: 2026-06-10
date_to:
tags:
  - Project
  - Wagerick
  - Prysm
  - SaaS
last updated: 2026-06-12
status: Auth-System fertig — wartet auf Credentials von Thorsten
---

## Objective

Prysm ist ein Wagerick-Studio-Eigenprodukt — eine Web-App die Elektrikern automatisch tagesaktuelle Preise von ihren Großhändlern anzeigt (mit kundenspezifischen Konditionen). MVP wird an [[ELTESA - Thorsten Sawade]] als erstem Testnutzer validiert, danach als SaaS an viele Elektriker verkauft.

Prysm unterscheidet sich von normalen Wagerick-Kundenprojekten: kein Framer, kein Sanity — eigener Full-Stack (Node.js + Playwright + React).

## Key Results

- [ ] Backend scrapt alle 3 Phase-1-Händler erfolgreich (eldis, Fohrer Panno, H. Gautzsch)
- [ ] Frontend zeigt Preistabelle mit Günstigster-Hervorhebung
- [ ] Thorsten startet App lokal per `start.bat` ohne Hilfe
- [ ] Cache funktioniert (TTL 2h, wiederholte Suchen sofort)
- [ ] Übergabe an Thorsten inkl. Kurzanleitung

## Stakeholders

- [[ELTESA - Thorsten Sawade]] — Erster Testkunde, gibt Login-Daten + Feedback
- [[Jonathan Wagener]] — Entwicklung (Wagerick Studio)
- Lukas Rickert — Co-Founder [[Projects/Wagerick-Studio]]

## Tech Stack (abweichend vom Wagerick-Standard)

| Bereich | Tech |
|---|---|
| Backend | Node.js 20 + Express 4 |
| Browser-Automatisierung | Playwright (Chromium) |
| Datenbank / Cache | SQLite (better-sqlite3) |
| Frontend | React 18 + Vite + Tailwind CSS |
| Hosting Phase 1 | Lokal auf Kundens-PC |
| Hosting Phase 2+ | TBD (VPS / Cloud) |

## Phasen-Übersicht

**Phase 1 (aktuell) — MVP lokal:**
- Händler: eldis, Fohrer Panno (Zander Gruppe), H. Gautzsch
- Deployment: lokal, kein Auth, kein Hosting
- Ziel: funktionierender Preisvergleich für Thorsten

**Phase 2+ (geplant):**
- Browser Extension (Referenz: `prysm-extension-demo.html`)
- Weitere Händler: Sonepar, GC Gruppe, Uni Elektro
- Multi-Tenant SaaS, Auth, Cloud-Hosting
- Abo-Modell ~39 €/Monat

## Progress

### Current Status

**Auth-System implementiert (2026-06-12)**
- Username + Passwort Account-System (SQLite `users`-Tabelle, PBKDF2, Bearer-Token-Sessions)
- Login-Screen, Konto-erstellen-Flow, Logout-Button im Header
- AccountSection in Settings: Name ändern, Passwort ändern (Session bleibt aktiv)
- Security-Fix: PATCH /account verlangt validen Session-Token

**Phase 1B + 1C abgeschlossen (2026-06-10)**
- Login-Scraper für alle 3 Händler implementiert
- React-Frontend fertig (Dashboard + Settings)
- Credentials-API, start.bat, README auf GitHub

- **Nächster Schritt:** Credentials von Thorsten → Search-Selektoren finalisieren → DB vor Übergabe zurücksetzen (Test-Account löschen)

### Decisions Made

- Lokal-first für Phase 1 — kein Hosting-Aufwand bis MVP validiert
- Browser Extension auf Phase 2+ verschoben
- Phase-1-Händler auf eldis/Fohrer Panno/Gautzsch beschränkt (von Thorsten gewünscht)
- AES-256-CBC für Credentials; für SaaS Phase 2 auf keytar umstellen
- Credentials über UI (Settings-Seite) eingeben, nicht via .env
- Datanorm-Import + FTS5-Suche als Phase 2B geplant

### Blockers

- Thorstens Händler-Credentials ausstehend
- Search-Selektoren aller 3 Händler brauchen echten Login zur Verifikation
- Eldis: `eldis.obeta.de` antwortet nicht — Login-URL mit Thorsten klären
- Fohrer Panno: Station-Feld unklar — bei Thorsten nachfragen

## Related Journals

```base
filters:
  and:
    - file.inFolder("Journal")
properties:
  file.name:
    displayName: Title
  note.date:
    displayName: Date
  note.date_from:
    displayName: Date From
  note.date_to:
    displayName: Date To
  note.tags:
    displayName: Tags
views:
  - type: table
    name: Journals
    filters:
      and:
        - file.hasLink(this.file)
    order:
      - file.name
      - date
      - tags
    sort:
      - property: date
        direction: DESC
      - property: date_from
        direction: DESC
    columnSize:
      file.name: 420

```

## See Also

- [[ELTESA - Thorsten Sawade]] — Erster Testkunde
- [[Projects/Wagerick-Studio]] — Übergeordnetes Business
- [[Jonathan Wagener]]
- Projektordner: `kunden/EltesaPreisvergleich/`
- Design-Referenzen: `prysm-clickdummy.html` (Dashboard), `prysm-extension-demo.html` (Phase 2)
- Technik-Referenz: [[Techniques/Headless-CMS-mit-Sanity]] (analog für CMS-Verständnis)
