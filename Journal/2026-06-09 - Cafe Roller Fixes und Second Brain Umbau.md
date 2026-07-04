# 2026-06-09 — Cafe Roller Fixes und Second Brain Umbau

## Was wurde gemacht

### Cafe Roller — Website-Fixes

- **Google Maps Embed behoben:** Wurzelursache war nicht die URL selbst, sondern das Sanity-Feld `mapsUrl` — das JS hat die korrekte `/maps/embed`-URL zur Laufzeit mit einem normalen Maps-Link aus Sanity überschrieben. Lösung: Sanity-Override entfernt, URL fix im HTML verankert, `mapsUrl`-Feld aus Schema gelöscht.
- **Datenschutzerklärung:** Portable Text Renderer in JS eingebaut — wenn Feld `legalContent.datenschutz` in Sanity befüllt ist, ersetzt es den hardcodierten Text vollständig. Unterstützt H2, H3, Bold, Kursiv, Links. Hardcodierter Text bleibt als Fallback.
- **Impressum:** Vollständig dynamisch aus Sanity (`siteSettings`). Alle Felder — Name, Adresse, Telefon, E-Mail, USt-ID, Verantwortlicher — werden zur Laufzeit befüllt.
- **Adressfelder mehrzeilig:** `address`, `operatorName`, `operatorAddress`, `operatorResponsible` von `string` auf `text`-Typ geändert. Im Studio: Enter = neue Zeile. Im Frontend: `\n` → `<br>`.
- **H2 in Datenschutz:** `legalContent.datenschutz` unterstützt jetzt auch H2-Überschriften.
- **Mobile Nav Auto-Close:** Bei Link-Klick im mobilen Menü schließt sich die Nav automatisch.
- **Versions-Klarstellung:** `index.html` ist die aktive Produktionsversion — V2/V3 sind archiviert. CLAUDE.md entsprechend korrigiert.
- **Sanity Studio deployed:** Schema-Änderungen mit `npx sanity deploy` auf `https://cafe-roller-frankenbad.sanity.studio` veröffentlicht.

### Second Brain & Struktur

- **`Jonathan Wagener.md`** erstellt — vollständiges Profil, Stack, Arbeitsweise, Business-Kontext
- **`People/Cafe-Roller-Frankenbad.md`** erstellt — Kunden-Profil mit Kontakt, Angebot, Status
- **`Projects/Wagerick-Studio.md`** erstellt — Studio als eigenständiges Projekt mit Ziele, Stack, Pricing
- **`Projects/Cafe-Roller-Frankenbad.md`** aktualisiert — alle heutigen Entscheidungen + erledigte Todos
- **`kunden/cafe-roller-frankenbad/CLAUDE.md`** erstellt — per-Kunde Instruktionsdatei mit allen Tech-Details, Todos, Entscheidungen
- **Projekt-CLAUDE.md** bereinigt — Cafe-Roller-Details entfernt, Pointer auf per-Kunde CLAUDE.md. Neue Regel: jeder Kundenordner bekommt eigene CLAUDE.md

## Entscheidungen

- **Google Maps immer fix im Code verankern**, nie in Sanity-Freitextfeld — dort landet leicht ein normaler Maps-Link ohne `output=embed` → X-Frame-Options-Fehler
- **Sanity `text`-Typ statt `string`** für alle Felder die mehrzeilig sein könnten (Adressen, Namen mit mehreren Personen)
- **Per-Kunde CLAUDE.md** als Standard-Pattern: Kundeninfos, Todos, Stack gehören in `kunden/[kunde]/CLAUDE.md`, nicht in die Haupt-CLAUDE.md

## Gelernte Lektionen

- **Google Maps X-Frame-Debugging:** Immer die Laufzeit-`src` prüfen (nicht nur HTML-Quelltext) — CMS-Felder können URLs überschreiben. Fehler zeigt `google.com`-Root = redirect = kein echter Embed-Link
- **`npx serve` Port-Syntax:** `-l tcp://localhost:3333` statt `--port 3333` (neue serve-Version)
- **PowerShell:** `&&` funktioniert nicht — stattdessen `;` oder separate Befehle
- **Sanity Studio neu starten nach Schema-Änderungen** — oder `npx sanity deploy` für das Online-Studio

## Offene Punkte / Next Steps

- [ ] Betreiberdaten im Studio eintragen (Name, Adresse, USt-ID, Verantwortlicher)
- [ ] Telefonnummer beim Kunden erfragen
- [ ] Echte Fotos liefern lassen → im Studio hochladen
- [ ] Formspree auf echtem Server testen
- [ ] Netlify-Domain in Sanity CORS Origins eintragen
- [ ] Go-live mit Kunde absprechen

## Verknüpfte Notes

- [[Projects/Cafe-Roller-Frankenbad]]
- [[People/Cafe-Roller-Frankenbad]]
- [[Projects/Wagerick-Studio]]
- [[Jonathan Wagener]]
- [[Techniques/Headless-CMS-mit-Sanity]]
