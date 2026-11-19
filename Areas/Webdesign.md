---
acronym:
tags:
  - Area
  - Webdesign
last updated: 2026-11-19
---

## Overview

Webdesign ist das Kerngeschäft von **Wagerick Studio**: Websites für lokale Betriebe in Bonn / Sankt Augustin — Framer als primäres Tool, Custom HTML/CSS/JS für Projekte mit eigenem Stack, optional Sanity als Headless-CMS für Kunden, die ihre Inhalte selbst pflegen wollen. Zwei Produktstufen: Basispaket (statisch) und Premium (+ Sanity CMS, +20–40 €/Monat Wartung).

## Key Concepts

- **Build-Standard:** Jeder Build wird sofort vollständig umgesetzt — Platzhalter-Fotos (Unsplash), echte Impressum/Datenschutz-Seiten, Scroll-Animationen (GSAP/ScrollTrigger), mehrere Unterseiten statt Single-Page. Platzhalter nur für Dinge, die ohne Kundendaten technisch nicht gehen (Formspree-Konto, Domain, Firmenname, echte Fotos).
- **CMS-Entscheidung:** Bei jedem neuen Kunden aktiv fragen, ob Sanity integriert werden soll — nicht automatisch annehmen.
- **Stack-Gotchas, die immer wieder auftreten:** CDN-SRI-Hashes erst kurz vor Go-live final setzen, GROQ-Bild-Referenzen nie dereferenzieren (`asset->{_ref}` → null), GSAP `.to()` kennt kein `from:`, CSS-Modifier-Klassen brauchen gleiche/höhere Spezifität als die Basis-Selektoren.
- **Rechtliches:** deutsches Recht, DSGVO-konform, bei minderjährigen Vertragspartnern Eltern-Mitzeichnung.

## Techniques

```base
filters:
  and:
    - file.inFolder("Techniques")
properties:
  file.name:
    displayName: Title
  note.tags:
    displayName: Tags
  note.last updated:
    displayName: Last Updated
views:
  - type: table
    name: Techniques
    filters:
      and:
        - file.hasLink(this.file)
    order:
      - file.name
      - last updated
      - tags
    sort:
      - property: file.name
        direction: ASC
    columnSize:
      file.name: 420

```

## Resources

```base
filters:
  and:
    - file.inFolder("Resources")
properties:
  file.name:
    displayName: Title
  note.source:
    displayName: Source
  note.tags:
    displayName: Tags
  note.last updated:
    displayName: Last Updated
views:
  - type: table
    name: Resources
    filters:
      and:
        - file.hasLink(this.file)
    order:
      - file.name
      - source
      - last updated
      - tags
    columnSize:
      file.name: 420

```

## See Also

- [[Projects/Wagerick-Studio]]
- [[Projects/Cafe-Roller-Frankenbad]]
- [[Projects/Gartenservice Welte Marqua - Website]]
- [[Projects/Piazza-Siciliana-da-Sebastiano]]
- [[People/Jonathan Wagener]]
