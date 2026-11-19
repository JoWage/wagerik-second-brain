# 2026-11-19 — Git-Migration und Vault-Aufräumen

## Was wurde gemacht

- Komplette Umstellung von Cloud-Sync (OneDrive + iCloud, chaotisch) auf Git-first: vier private GitHub-Repos unter `C:\Users\sandr\dev\` angelegt — `wagerick-studio`, `wagerik-second-brain` (Historie erhalten), `prysm` (Historie erhalten, bewusst eigenständig), `euroscope-gnd-plugin` (neu).
- Inhalt byte-genau aus OneDrive/iCloud zusammengeführt und verifiziert; alte Orte aufgeräumt (iCloud-Vault-Kopie archiviert, OneDrive-Projektordner bis auf Verweis-`CLAUDE.md` geleert).
- Eigene Custom-Skills (`/cms`, `/wrapup`) in `wagerick-studio` neu registriert (Junction-Mechanismus); `/wrapup` zusätzlich inhaltlich korrigiert, da es den Vault bisher als Unterordner statt als eigenständiges Sibling-Repo erwartet hatte.
- Vier neue Projekt-Memory-Ordner angelegt (`~/.claude/projects/C--Users-sandr-dev-*`), bestehende Memories aufgeteilt/migriert, veraltete Pfad-Annahmen korrigiert.
- Second-Brain-Vault aufgeräumt: 4 generische Template-Demo-Notizen archiviert, leere `Areas/Webdesign.md` (war von 4 Notizen verlinkt, aber nie befüllt) mit echtem Inhalt gefüllt, verwaiste leere Technique-Notiz entfernt, ungenutzte Journal-Unterordner entfernt.

## Entscheidungen

- Second Brain + Prysm bleiben eigenständige Repos, werden nicht in `wagerick-studio` gemerged.
- Windows-PC bleibt Hauptrechner; Mac-Klon der vier Repos folgt, sobald verfügbar.
- Zwei kleine Dateigruppen (eine Vorlagen-E-Mail, 6 Dateien im archivierten `eiscafe-giardino`-Lead) wurden wegen eines persistenten iCloud-Cloud-Timeouts nicht migriert — bewusst als offener Punkt stehen gelassen statt endlos zu retryen.

## Offene Punkte / Next Steps

- [ ] Mac verfügbar → alle vier Repos nach `~/dev/...` klonen
- [ ] Zwei fehlende Dateigruppen aus `iCloudDrive\Wagerick-Business` nachkopieren, sobald iCloud sich beruhigt hat
- [ ] `iCloudDrive\Wagerick-Business` umbenennen/archivieren (Zugriff war zum Migrationszeitpunkt verweigert)
- [ ] Alten OneDrive-Projektordner nach Sessionende selbst archivieren (aktive cwd, bewusst nicht automatisiert)

## Verknüpfte Notes

- [[Projects/Wagerick-Studio]]
- [[Projects/Cafe-Roller-Frankenbad]]
- [[Projects/Gartenservice Welte Marqua - Website]]
- [[Projects/Piazza-Siciliana-da-Sebastiano]]
- [[Techniques/CMS-Scaffolding-Skill]]
