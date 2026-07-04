---
priority: low
date_from: 2026-06-15
date_to:
tags:
  - Project
  - EuroScope
  - VATSIM
  - privat
last updated: 2026-06-15
---

## Objective

> [!info] Persönliches/privates Projekt (kein Kundenauftrag)
> EuroScope-Plugin in C++ das **Bodenkonflikte am Flughafen EDDF (Frankfurt)** in Echtzeit erkennt und auf dem Ground-Radar als farbige Linien + Labels anzeigt. Läuft parallel zu einer live ATC-Session auf VATSIM.

- Detektiert HEAD_ON-, INTERSECTION- und PUSHBACK-Konflikte zwischen rollenden Flugzeugen
- Liegt temporär unter `PLuginEuroscope/EuroScope-GND-Conflict/` im Website-Sidehussle-Ordner

## Key Results

- [x] DLL baut sauber (32-bit Win32, VS 2026 Preview, CMake)
- [x] Echte EDDF-Taxiway-Geometrie aus VATGER EDGG Sectorpaket extrahiert (604 Edges)
- [x] Inbound/Outbound-Filter gegen Fehlalarme mit Parkern
- [x] Popup-Menü (ACK/Instruktionen) öffnet an Mausposition, funktioniert auch als Observer
- [x] Deploy-Paket `dist/` (DLL + ini + data + README)
- [ ] In EuroScope geladen & gegen echten/Sweatbox-Traffic getestet
- [ ] Schwellenwerte empirisch getunt
- [ ] Edge-Namen mit echten Taxiway-Buchstaben statt generischer IDs

## Stakeholders

> [!info] Beteiligte
- [[Jonathan Wagener]] – Entwicklung & Test (VATSIM-Lotse EDDF/Langen)

## Progress

### Current Status

- **2026-06-15:** Plugin baut und läuft. Echte EDDF-Daten aus dem VATGER-Paket
  (`EDGG-FULL_*.sct`, Layer `EDDF Groundlayout DFS Taxiways`) per
  Segment-Chaining-Extraktor zu einem Taxiway-Graphen verarbeitet
  (961 Nodes / 604 Edges). Zwei Praxis-Fixes ergänzt: Inbound/Outbound-Filter
  (`CanConflict()`) gegen Parker-Fehlalarme und Popup an Mausposition.
  Nächster Schritt: in EuroScope laden und Sweatbox-Test.

### Decisions Made

- **Win32 statt x64:** EuroScope ist ein 32-bit-Prozess; `EuroScopePlugInDll.lib`
  exportiert `__thiscall`-Symbole → x64 = LNK2019.
- **Sector-File-GEO statt benannter Taxiways:** EDGG-`.sct` hat keine
  individuellen Taxiway-Namen, nur visuelle Polylinien. Graph wird per
  Endpunkt-Chaining + Junction-Erkennung gebaut.
- **Inbound/Outbound-Konfliktregeln:**
  Outbound nur bei PUSHBACK/TAXIING; Inbound immer außer am Stand (GS<2kt).

### Blockers

- Keine. Test in EuroScope steht noch aus (manueller Schritt).

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
views:
  - type: table
    name: Journals
    filters:
      and:
        - file.hasLink(this.file)
    sort:
      - property: date
        direction: DESC
```

## See Also

- Projekt-CLAUDE.md: `PLuginEuroscope/EuroScope-GND-Conflict/CLAUDE.md` (vollständige Architektur)
- VATGER EDGG Sectorpaket: `Downloads/Euroscope/Sectorfiles/EDGG/`
- [[Wagerick-Studio]]
