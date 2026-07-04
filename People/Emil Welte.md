---
team: Welte & Marqua Gartenservice
role: Kunde / Mitgründer
tags:
  - People
last updated: 2026-06-14
---

## Overview

Emil Welte ist einer von zwei Gründern eines neu aufzubauenden Gartenservice-Betriebs in der Region Bonn / Sankt Augustin. Er beauftragt Wagerick Studio mit der Erstellung einer Landing Page inkl. Kontaktformular und hochwertigen Web-Animationen (3D, Scroll).

- Partner: [[Tom Marqua]]
- Betrieb: Gartenservice (im Aufbau, Firmenname noch nicht festgelegt)
- Region: Bonn / Sankt Augustin
- Projekt: [[Gartenservice Welte Marqua - Website]]

## Notes

- Kein eigenes Logo oder Fotos vorhanden (Stand 2026-06-14)
- Firmenname noch offen

## Interactions

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

- [[Tom Marqua]]
- [[Gartenservice Welte Marqua - Website]]
