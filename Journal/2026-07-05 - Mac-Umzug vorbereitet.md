# 2026-07-05 — Mac-Umzug vorbereitet

## Was wurde gemacht
- Alle 6 Git-Repos geprüft, bereinigt, committed & gepusht (inkl. Merge einer echten Remote-Divergenz bei `prysm`)
- Obsidian-Vault von Junk-Dateien befreit und nach iCloud verschoben (Git-Repo bleibt intakt)
- Kundenprojekte ohne Git (`cafe-roller-frankenbad`, `welte-marqua-gartenservice`) ohne `node_modules` nach iCloud übernommen
- Claude-Code-Konfiguration gesichert (`claude-config-backup.zip`, MCP-Liste)
- iCloudDrive-Struktur an „Website SIdehussle" angelehnt: `kunden/`, `demos/`, `tools/lead-finder/`, `vorlagen/`, `Wagerick-Business/`, `Obsidian/`, `Schule/`

## Entscheidungen
- Nur eigene Dateien migrieren — Familien-Ordner (Pictures, Dateien Wagener) bleiben unangetastet in OneDrive
- Downloads-Ordner und Flugsim-Hobbyprojekte (inkl. `PLuginEuroscope`, 170 MB) komplett ausgeklammert
- `plugin-sdk2` (Duplikat) und `endless-atc-voice-control` (Fremd-Repo) nicht migriert
- `prysm`: lokales Login-System behalten, GitHub-Fortschritt (Scraper, Frontend) reingemerged
- `Präsentationlaura.pptx` endgültig gelöscht

## Offene Punkte / Next Steps
- [ ] `leads.csv.xlsx` manuell aus `iCloudDrive\.Trash` retten (0-Byte-Stub in Wagerick-Business liegt noch da)
- [ ] Leftover `node_modules`/`dist` in alten `kunden/`-Ordnerresten (Website SIdehussle) aufräumen
- [ ] Auf dem Mac: `~/Developer/` anlegen, Repos aus `git-repos-liste.txt` klonen
- [ ] Azure-DevOps-PAT für `EuroSopePlugIn` auf dem Mac einrichten

## Verknüpfte Notes
- [[Projects/Wagerick-Studio]]
