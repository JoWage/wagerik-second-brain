# 2026-07-13 — Grünwerk Formular und Impressum-Finalisierung

## Was wurde gemacht
- Formularfeld „Häufigkeit" durch „Werkzeug vor Ort" (vorhanden / muss mitgebracht werden) ersetzt (`index.html` + `netlify-deploy/index.html`)
- Beim Sanity-CMS-Check festgestellt: Emil & Tom hatten am 2026-07-05 bereits selbst reale Daten eingetragen (E-Mail, Telefon, Adresse, echte Formspree-Form-ID `xgojdnbe`) — als HTML-Fallback in Impressum/Datenschutz/Kontaktformular übernommen
- Neues Sanity-Schema-Feld `operatorLegalForm` (Rechtsform/Firmenzusatz) angelegt, Studio neu deployed (`npm install` + `sanity deploy -y`, appId jetzt in `sanity.cli.js`)
- Impressum-Logik erweitert: Rechtsform/USt-ID/Verantwortlicher werden automatisch aus dem CMS injiziert und verlieren dabei ihre Platzhalter-Optik
- `netlify-deploy/`-Ordner gegen Hauptordner geprüft — vollständig synchron
- Hinweis-Boxen („vor Go-live entfernen") aus Impressum & Datenschutz entfernt (auf Jonathans Wunsch, auch ohne dass alle Daten vorliegen)
- Minderjährigkeits-Hinweis unter „Vertreten durch" im Impressum entfernt (auf Jonathans Wunsch)

## Entscheidungen
- Firmenname bleibt Platzhalter „Grünwerk"
- Rechtsform/USt-ID werden künftig direkt von Emil & Tom im Sanity Studio gepflegt statt manuell im Code
- Formspree-AV-Vertrag & Eltern-Mitzeichnung sind reine Vertrags-/Rechtsthemen außerhalb der Website, nicht CMS-integrierbar
- Rechtliche Frage der Vertretung bei Minderjährigkeit bleibt ungeklärt — nur nicht mehr auf der Website sichtbar (explizit in Kunden-CLAUDE.md dokumentiert, damit es nicht in Vergessenheit gerät)

## Offene Punkte / Next Steps
- [ ] Emil & Tom: Rechtsform, USt-ID, redaktionell Verantwortlicher im Sanity Studio eintragen
- [ ] Formspree-AV-Vertrag abschließen
- [ ] Rechtsfrage der Vertretung bei Minderjährigkeit klären
- [ ] Echte Fotos & Logo einpflegen
- [ ] Domain registrieren
- [ ] Emil & Tom als Editor ins Sanity-Projekt einladen

## Verknüpfte Notes
- [[Projects/Gartenservice Welte Marqua - Website]]
