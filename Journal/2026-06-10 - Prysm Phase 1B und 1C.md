# 2026-06-10 — Prysm Phase 1B und 1C

## Was wurde gemacht

- Login-Scraper für alle 3 Händler implementiert (eldis, Fohrer Panno, H. Gautzsch)
  - Fohrer Panno: Angular Material, `formcontrolname`-Selektoren (stabiler als mat-input-N IDs)
  - Gautzsch: Form-POST zu `onlinesystem.de`, Erfolg = URL-Check auf onlinesystem.de
  - Eldis: Primär `eldis.obeta.de`, Fallback Navigation von `eldis.de` (obeta.de timeout im Test)
- `BaseScraper` um `dismissCookies()` erweitert; flaky `waitForNavigation` durch `waitForURL` ersetzt
- React-Frontend gebaut: Dashboard (Suche + Preistabelle, günstigster grün), Settings (Credentials pro Händler)
- Backend Credentials-API (`/api/credentials`) — AES-256, SQLite, Vorrang vor env vars
- `start.bat` für Ein-Klick-Start erstellt
- README + Pre-Test-Checkliste auf GitHub gepusht

## Entscheidungen

- Credentials über UI eingeben (nicht `.env`) — benutzerfreundlicher für Thorsten
- Fohrer-Panno Station-Feld optional (unklar ob Thorstens Account es braucht)
- Jonathan testet zuerst selbst → dann Übergabe-Paket für Thorsten
- Datanorm-Import als Phase 2B geplant (FTS5-Suche + Hybrid-Ansatz)

## Offene Punkte / Next Steps

- [ ] Credentials von Thorsten erhalten (alle 3 Händler)
- [ ] Test auf Jonathans PC mit `start.bat`
- [ ] Search-Selektoren nach echtem Login finalisieren (Debug-Screenshots helfen)
- [ ] Eldis-Login-URL klären (eldis.obeta.de Timeout — mit echtem Account testen)
- [ ] Fohrer-Panno Station-Feld bei Thorsten nachfragen
- [ ] Nach Test: Übergabe-Ordner + Kurzanleitung für Thorsten erstellen

## Verknüpfte Notes

- [[Projects/Prysm - Elektro Preisvergleich]]
- [[People/ELTESA - Thorsten Sawade]]
