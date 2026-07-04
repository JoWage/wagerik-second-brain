# 2026-06-17 — Welte & Marqua: VN-Slider-Fix, Paket-Anfrage, Hero-Hintergrundfoto

## Was wurde gemacht
- Vorher/Nachher-Slider: Labels aus den geclippten Containern gezogen (waren teils unsichtbar) und die Bild/Label-Zuordnung korrigiert (links/rechts war technisch vertauscht — Vorher und Nachher zeigten das jeweils falsche Foto)
- Preiskarten (Basic/Komfort/Premium) verlinken jetzt mit Paket-Vorauswahl ins Kontaktformular (`data-package` + `applyPackageToForm()`)
- Formspree-Integration ausgebaut: dynamischer `_subject` je Paket, Honeypot-Feld (`_gotcha`) gegen Spam
- Nav-CTA „Jetzt anfragen" vergrößert — Bug dabei gefunden und gefixt: `.nav__links li a` hatte höhere CSS-Spezifität als `.nav__cta` und überschrieb Font-Size/Padding
- Hero-Hintergrund umgebaut: von floatender Foto-Karte zu echtem Vollflächen-Hintergrundfoto hinter der Three.js-Linien-Animation (Renderer auf `alpha:true` + transparente ClearColor gestellt, Foto gedimmt/grün abgetönt)

## Entscheidungen
- Hero-3D-Animation, Text und Layout bleiben unverändert — Foto nur als zusätzliche Ebene dahinter
- Formspree-URL bleibt bewusst Platzhalter bis echter Account existiert

## Offene Punkte / Next Steps
- [ ] Visuell im Browser gegenchecken (lokaler Server läuft auf Port 8731): VN-Slider über ganzen Reglerbereich, Hero-Hintergrundfoto, Nav-Button-Größe
- [ ] Formspree-Account + echte Action-URL + AV-Vertrag
- [ ] Echte Fotos statt Unsplash-Platzhalter
- [ ] Finaler Firmenname, Impressum-Pflichtangaben, Domain, Netlify-Deploy

## Verknüpfte Notes
- [[Projects/Gartenservice Welte Marqua - Website]]
