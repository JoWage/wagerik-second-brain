---
type: technique
tags: [cms, sanity, backend, client-features]
related: "[[Projects/Cafe-Roller-Frankenbad]], [[Techniques/CMS-Scaffolding-Skill]], [[Projects/Gartenservice Welte Marqua - Website]]"
created: 2026-06-08
updated: 2026-06-17
status: produktiv
---

# Headless CMS mit Sanity.io

> [!tip] Automatisiert
> Für neue Kunden gibt es jetzt den Skill **`/cms <kunde>`**, der den kompletten Aufbau unten scaffoldet → [[Techniques/CMS-Scaffolding-Skill]].

## Was ist das?

Ein Headless CMS trennt Inhaltsverwaltung (Backend) vom Frontend.
Der Kunde pflegt Inhalte in einem sauberen Dashboard — die Website holt sich die Daten automatisch per API.

Kein FTP, kein Code, kein Anruf bei Jonathan.

---

## Die drei Teile

| Teil | Was es macht |
|------|-------------|
| **Sanity Studio** | Dashboard für den Kunden (Felder, Formulare, Bilder) |
| **Sanity API (GROQ)** | Verbindung zwischen Dashboard und Website |
| **index.html** | Holt Daten dynamisch, kein hardcoded HTML mehr |

---

## Wann einsetzen?

**Sinnvoll wenn der Kunde selbst pflegen will:**
- Speisekarte (Preise, neue Einträge)
- News / Aktuelles
- Öffnungszeiten
- Team-Mitglieder
- Veranstaltungen
- Impressum / Datenschutz (Betreiberdaten)

**Nicht nötig für:**
- Hero-Text & Design
- Animationen
- Struktur der Seite
- Dinge die sich nie ändern (z.B. Google Maps Embed → fix im Code lassen!)

---

## Implementierung (Vanilla JS, kein Build-Tool)

```javascript
// GROQ-Query an Sanity schicken
const query = encodeURIComponent('*[_type == "menuItem"]{ name, price }')
const url = `https://PROJECTID.apicdn.sanity.io/v2024-01-01/data/query/DATASET?query=${query}`
const { result } = await (await fetch(url)).json()
```

### Portable Text rendern (Datenschutz, Langtexte)

```javascript
function renderPortableText(blocks) {
  return blocks.map(block => {
    if (block._type !== 'block') return '';
    const text = (block.children || []).map(span => {
      let t = escHtml(span.text || '');
      if (span.marks?.includes('strong')) t = `<strong>${t}</strong>`;
      if (span.marks?.includes('em')) t = `<em>${t}</em>`;
      return t;
    }).join('');
    switch (block.style) {
      case 'h2': return `<h2>${text}</h2>`;
      case 'h3': return `<h3>${text}</h3>`;
      default: return `<p>${text}</p>`;
    }
  }).join('\n');
}
```

### Mehrzeilige Adressfelder

Für Felder die Zeilenumbrüche brauchen (Adressen, Namen): **`type: 'text'`** statt `type: 'string'`.
Im Frontend: `value.replace(/\n/g, '<br>')` — nie `textContent`, immer `innerHTML` verwenden.

---

## Gotchas & Fallstricke

| Problem | Ursache | Fix |
|---------|---------|-----|
| Google Maps X-Frame-Fehler | Sanity-Feld hat normalen Maps-Link überschrieben | Maps-Embed fix im Code, kein CMS-Feld |
| CORS-Fehler lokal | Origin nicht in Sanity whitelist | manage.sanity.io → API → CORS Origins |
| Schema-Änderung nicht sichtbar | Studio gecacht | `npx sanity deploy` oder Studio neu starten |
| `string`-Feld zeigt keine Zeilenumbrüche | `string` = einzeilig | `type: 'text'` verwenden |

---

## Neues Kundenprojekt aufsetzen — Schritt für Schritt

### Schritt 1 — Sanity Studio anlegen

```bash
cd kunden/[kunde-name]
npm create sanity@latest
```

Beim Setup:
- **Project name:** `[kunde-name]` (z.B. `cafe-roller-frankenbad`)
- **Dataset:** `production`
- **TypeScript:** Nein
- **Schema:** Leer starten (keine Vorlage)
- Ordner: `sanity-studio/`

### Schritt 2 — Schemas definieren

**Immer anlegen** (Basis für jeden Kunden):

| Schema | Inhalt |
|--------|--------|
| `siteSettings` | Telefon, E-Mail, Instagram, Adresse (text), Öffnungszeiten, Impressum-Felder |
| `legalContent` | Datenschutz (Portable Text: H2/H3/Bold/Kursiv/Link), Impressum-Extras |

**Je nach Kunde ergänzen:**
- `menuCategory` + `menuItem` → Speisekarte
- `newsItem` → News / Aktuelles
- `galleryImage` → Galerie
- `teamMember` → Team
- `heroContent` → Hero-Text, rotierende Phrasen
- `aboutContent` → Über-uns-Texte
- `shopPartner` → Partner / Kooperationen
- etc....

**Wichtig bei Feldern:**
- Adressen, mehrzeilige Namen → immer `type: 'text'` (nicht `string`)
- Langtexte mit Formatierung → `array` of `block` (Portable Text) mit H2/H3/Bold/Kursiv/Link
- Google Maps → **nie** als Sanity-Feld, fix im HTML verankern

### Schritt 3 — CORS einrichten

→ [manage.sanity.io](https://manage.sanity.io) → Projekt → **API → CORS Origins**

Eintragen:
- `http://localhost:3333` (lokales Testen)
- Netlify-URL (nach erstem Deploy)

### Schritt 4 — Frontend-Integration in index.html

```javascript
// 1. Alle dynamischen Sektionen unsichtbar starten
// In CSS:
// #about, #angebot, #news, #kontakt { opacity: 0; transition: opacity 0.5s; }

// 2. Fetch-Funktion
(function() {
  var CDN = 'https://PROJECTID.apicdn.sanity.io/v2024-01-01/data/query/production';

  async function loadContent() {
    var query = encodeURIComponent('{ "settings": *[_type=="siteSettings"][0], "legal": *[_type=="legalContent"][0] }');
    var { result } = await (await fetch(CDN + '?query=' + query)).json();
    if (!result) return;
    applySettings(result.settings);
    applyLegal(result.legal, result.settings);
    // Sektionen einblenden
    document.querySelectorAll('[data-sanity]').forEach(el => el.style.opacity = '1');
  }

  // 3-Sek Fallback: Sektionen einblenden auch wenn Fetch scheitert
  setTimeout(() => {
    document.querySelectorAll('[data-sanity]').forEach(el => el.style.opacity = '1');
  }, 3000);

  document.addEventListener('DOMContentLoaded', loadContent);
})();
```

DOM-IDs für dynamische Targets setzen, z.B.:
- `id="kontakt-phone"`, `id="kontakt-email"`, `id="standort-iframe"`
- `id="imp-address"`, `id="imp-contact"`, `id="imp-vat"`, `id="imp-responsible"`
- `id="ds-content"` (Datenschutz-Container)

### Schritt 5 — Studio deployen

```bash
cd kunden/[kunde]/sanity-studio
npx sanity deploy
```

Studio-URL: `https://[projektname].sanity.studio`

### Schritt 6 — Lokal testen

```bash
npx serve "kunden/[kunde]" -l tcp://localhost:3333
```

Browser: `http://localhost:3333` — alle Sektionen müssen sichtbar sein, kein CORS-Fehler.

### Schritt 7 — Go-live Checkliste

- [ ] Netlify-Domain in Sanity CORS Origins eintragen
- [ ] Alle Inhalte im Studio befüllen
- [ ] Impressum + Datenschutz Betreiberdaten eintragen
- [ ] Formspree-Formular auf Netlify testen
- [ ] `kunden/[kunde]/CLAUDE.md` anlegen mit allen Infos
- [ ] Second Brain: `Projects/` + `People/` Note anlegen
- [ ] Studio-Zugang an Kunden übergeben + kurze Einweisung

---

## Studio deployen

```bash
cd kunden/[kunde]/sanity-studio
npx sanity deploy
```

→ Änderungen erscheinen sofort auf `https://[studio-name].sanity.studio`

## Lokal testen

```bash
# Website (Port muss in CORS eingetragen sein)
npx serve "kunden/[kunde]" -l tcp://localhost:3333

# Studio lokal
npx sanity dev --port 3334
```

---

## Kosten

| Plan | Kosten | Reicht für |
|------|--------|-----------|
| Free | 0 €/Monat | bis 3 Nutzer, 10GB — alle kleinen Kunden |
| Growth | ~19 €/Monat | größere Projekte |

---

## Variante: „In-Place-Override" statt Listen-Rebuild

> Fall: [[Projects/Gartenservice Welte Marqua - Website]] (2026-06-17)

Das `opacity:0` + `fadeIn()` + `innerHTML`-Rebuild-Muster oben geht davon aus, dass die Website
mit **leeren Platzhaltern** startet. Wenn die Website schon **fertigen, echten Content** hat
und **GSAP/ScrollTrigger-Animationen mit fest verdrahteter Element-Anzahl** (z.B. `.from()` auf
6 Karten), bricht dieses Muster zwei Dinge:

1. `innerHTML`-Rebuild ersetzt die Knoten, auf die ScrollTrigger zeigt → Animation läuft nicht mehr.
2. `opacity:0` versteckt echten, fertigen Inhalt, bis das CMS geantwortet hat — schlechter First Paint
   und bei CMS-Ausfall bleibt die Seite leer statt failsafe den echten HTML-Inhalt zu zeigen.

**Fix:** CMS überschreibt nur **Text/`src` vorhandener Knoten** (`querySelector` + `textContent`/`src`,
kein `innerHTML`-Rebuild, kein `opacity:0`). Konsequenzen:
- Keine `fadeIn()`/`DYNAMIC`-Logik nötig — Seite ist von Anfang an mit echtem Inhalt sichtbar.
- GSAP-Animationen bleiben unangetastet, da Knoten-Identität erhalten bleibt.
- **Dokumentierte Grenze:** Listen (Leistungen, Preis-Pakete, FAQ, Galerie) haben eine im HTML fixierte
  Maximalzahl. Kunde kann Texte ändern/umsortieren (`orderRank` + Index-Mapping in JS), aber keinen
  zusätzlichen Eintrag über die Baseline hinaus anlegen, ohne dass ein Dev das HTML erweitert.

**Wann welche Variante wählen:**
- Neue Website, noch kein Content fertig → Standard-Muster (`opacity:0`/`fadeIn`/`innerHTML`).
- Website schon fertig gebaut mit echtem Content + reichen Scroll-Animationen → In-Place-Override.

## Geschäftlich — Upsell-Argument

> *„Basispaket: statische Website, Änderungen über mich.
> Premium-Paket: + Admin-Bereich, Sie pflegen Preise und Inhalte selbst."*

Rechtfertigt +20–40 €/Monat Wartungspauschale.

---

## Ressourcen

- [sanity.io/docs](https://sanity.io/docs)
- [GROQ-Cheatsheet](https://www.sanity.io/docs/groq-cheat-sheet)
