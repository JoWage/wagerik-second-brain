---
date: 2026-06-12
tags:
  - Journal
  - Daily
  - Prysm
---

## 🌙 End of Day

### What progress did I make today?

> [!tip] Evidence of movement

- Prysm-Frontend war bereits vollständig vorhanden (war vergessen worden) — kein Neuaufbau nötig
- Lokales Login-System implementiert: erst Passwort-only, dann auf **Username + Passwort** (Account-System) umgestellt
- `users`-Tabelle in SQLite, PBKDF2-Hashing (Node built-ins), Bearer-Token-Sessions (8h TTL)
- `PATCH /api/auth/account` Endpunkt für Name- und Passwortänderung — mit Session-Check (Security-Fix)
- `AccountSection` in Settings: Avatar-Initial, Formulare mit aktuellem Passwort als Bestätigung
- Passwortänderung behält Session aktiv (kein Zwangs-Logout) — auf Jonathans Wunsch
- Vollständig verifiziert via Playwright (Screenshots) + PowerShell API-Tests

### What created friction today?

> [!warning] Delays, confusion, blockers, or energy drains

- Frontend-Ordner beim ersten Glob nicht gefunden (Glob-Tool hat `frontend/` übersehen) — manuelle Verifikation mit `ls` nötig
- Test-Hash in DB (`test1234`) nach Backend-Tests übriggeblieben → DB-Zustand zwischen Test-Runs unklar
- Security-Plugin hat nachträglich gemeldete, validen Finding: PATCH /account brauchte Session-Check

### What should I do differently tomorrow?

> [!info] Small adjustment

- DB nach jedem Verifikationstest explizit bereinigen, nicht auf Migration verlassen
- `ls`-Check immer vor Glob bei ersten Erkundungen neuer Ordner

## Daily highlights

> [!note] Three moments worth remembering

- Prysm hat jetzt ein richtiges Account-System mit Avatar, Name ändern, Passwort ändern
- Security-Review-Plugin hat einen echten Bug gefunden (fehlender Session-Check auf PATCH-Route) — direkt gefixt
- Playwright-Screenshots zeigen eine saubere, professionelle App — Thorsten wird beeindruckt sein

## Verknüpfte Notes

- [[Projects/Prysm - Elektro Preisvergleich]]
