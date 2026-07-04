# 2026-06-18 — Sanity CORS Doku-Korrektur

## Was wurde gemacht
- `sanity-deployment-problem.md` (Notiz über localhost-Abhängigkeit + Safari-ITP-CORS-Blocking) durchgesehen
- Café Roller Frankenbad und Welte & Marqua Gartenservice per Explore-Agents gegen die Checkliste geprüft
- Beide Codebasen sind sauber: kein localhost im Production-Code, korrekte `apicdn.sanity.io`-Nutzung
- CLAUDE.md-Dateien beider Kunden enthielten veraltete CORS-Status-Angaben (suggerierten, CORS sei noch offen)
- Jonathan bestätigt: CORS ist für beide Projekte bereits korrekt eingetragen
- Live-URLs ermittelt: Café Roller → `cosmic-hummingbird-49511b.netlify.app`, Welte & Marqua → `effulgent-monstera-c08996.netlify.app`
- Beide `kunden/*/CLAUDE.md` korrigiert (CORS-Zeile, Live-URL, Open-Todo abgehakt)

## Entscheidungen
- Kein Code-Fix nötig, reine Dokumentationskorrektur
- Beide Projekte sind bereits live deployed auf Netlify-Subdomains (Doku-Stand war hier hinter der Realität)

## Offene Punkte / Next Steps
- [ ] Finale Custom-Domains für beide Kunden registrieren → danach zusätzlich in Sanity CORS eintragen
- [ ] Café Roller: Betreiberdaten, echte Fotos, Formspree-Test, Telefonnummer
- [ ] Welte & Marqua: Firmenname, Fotos, Logo, Formspree-Konto, Domain, Impressum/Datenschutz-Daten

## Verknüpfte Notes
- [[Projects/Cafe-Roller-Frankenbad]]
- [[Projects/Gartenservice Welte Marqua - Website]]
