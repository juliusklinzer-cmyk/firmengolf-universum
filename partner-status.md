# Partner-Status & offene Klärungen

Stand: 18.07.2026 · Konditionen maschinenlesbar in `inc/partners.php` (Website),
Verträge in `Claude Firmengolf/03_Vertrieb-Golfplätze/Partnerplätze/`.

## Überblick

- **20 Anlagen** auf der Website (19 Partner + Maxlrain als Gast-Eintrag),
  alle mit voll ausgebauten Detailseiten (Kurse, Pros, Galerie, Gastro, Fakten).
- Entscheidung Julius (17.07.2026): Alle Partner bleiben live, auch ohne im Ordner
  abgelegten Vertrag — freundschaftlicher Kontakt zu allen Clubs.

## Vertragslage (Lücken)

| Club | Status |
|---|---|
| Hamburg-Ahrensburg | kein Vertrag im Ordner |
| Bergkramerhof | kein Vertrag im Ordner |
| Mangfalltal | kein Vertrag im Ordner |
| Gut Grambek | nur unsignierter Entwurf |

## Offene Klärungen mit Clubs (bei Vorstellungs-Terminen einsammeln)

- [ ] **Weidenhof**: Platzfoto fehlt komplett (Bilder-Ordner leer) — Cover offen
- [ ] **Wiggensbach**: Gastro-Name/Betreiber unklar (Drittquellen widersprechen sich)
- [ ] **Stiftland**: CSV nennt Access+ — Website zeigt nur D/D+/Access. Was gilt?
- [ ] **Wiggensbach**: CSV nennt D+ — Website zeigt D/Access/A+. Was gilt?
- [ ] **Mangfalltal**: keine Galerie-Fotos, Logo nur als SVG-Rekonstruktion
- [ ] **Jersbek / St. Eurach / Open9**: D+-Greenfee-Preise in Verträgen leer

## Abgleich Website ↔ Events-Plattform (19.07.2026)

Die Events-Plattform führt dieselben ~20 Anlagen als Event-Partner
(`firmengolf-events/docs/partner-uebersicht.csv`). Gefundene Differenzen:

- **Assets synchronisiert (19.07.2026, lokal):** 9 Anlagen ohne Logo/Bilder auf
  der Events-Plattform wurden aus den Website-Assets befüllt (Bayerwald, Chieming,
  Escheburg, Grambek, Mangfalltal, Maxlrain, Igling, Schwäbisch Hall, St. Eurach) —
  nur Lücken gefüllt, bestehende Club-Uploads unangetastet.
  ⚠️ Nur in der LOKALEN Events-Instanz — muss noch auf firmengolf-events.de
  (nächstes Events-Deploy oder manuell im Live-Admin).
  ⚠️ Ausnahme Bayerwald: NICHT mehr deployen — der Club hat live inzwischen selbst
  sein neues Titan-Logo hochgeladen (siehe „Besondere Absprachen"), der lokale
  Gap-Fill (altes GLC-Logo) ist dafür obsolet.
- ~~Testdaten in Events~~: erledigt — Augusta National + Test Greeneagle sind
  lokal wie live bereits gelöscht; nur `docs/partner-uebersicht.csv` war ein
  veralteter Snapshot.
- ~~Orts-Check Bayerwald~~: geklärt (19.07.) — offizielle Adresse ist
  Poppenreut 11, 94118 **Jandelsbrunn** (Waldkirchen nur Bezugsort im Seitentitel);
  Website und Events sind beide korrekt.
- Kontaktdaten (Ansprechpartner/Mail/Telefon) sind in der Events-Liste fast
  überall leer — die Website hat inzwischen info@-Adressen + Telefon je Club.

## Besondere Absprachen

- **Bayerwald → „Titan Golfclub Bayerwald"** (Termin Julius, 30.07.2026): Neuer
  Sponsor „Titan", Club umbenannt inkl. neuem Logo. Club hat das Logo selbst auf
  firmengolf-events.de hochgeladen (`Neues_Logo_Bayerwald.png`, 29.07.); Website
  firmengolf.app am 30.07. nachgezogen (Name in `inc/partners.php` + Logo-Assets
  `glc-bayerwald-logo.jpg/.webp`, Slug bleibt `glc-bayerwald`). ⚠️ Die Club-eigene
  Website gc-bayerwald.de nennt sich Stand 30.07. noch „Golf- und Landclub
  Bayerwald e.V." — Vertragsdokumente laufen weiter auf den alten Namen (GLC).
- **Schwäbisch Hall** (Ingo, Präsident, 16.07.2026): Schnupperkurs 6–10 Personen;
  Gastro heißt „Brassie — das Restaurant am Grün" (gut für Workshops → Verweis auf
  firmengolf-events.de); Platzreife = „Power-Paket" (Club-Preis 599 €), via Discover:
  12 Monate Bindung oder 499 € Eigenanteil; Pro-Foto (Marco Melik) freigegeben.
- **Gut Kaden**: Access = „Kaden Woche" Mo–Fr.

## Indoor-Partner auf der Events-Plattform (firmengolf-events.de)

Stand 10.09.2026. Simulator-Ansprache läuft in drei Wellen (Doku im Events-Repo unter `docs/simulatoren-*`).

| Anlage | Status |
|---|---|
| RUFF Indoor Golf Dreieich | erste Indoor-Partneranlage, Weihnachtsfeier buchbar (84 bis 119 € p. P.), Event `/firmenevents/weihnachtsfeier-im-ruff/` |
| Tap Inn Wasserburg | Rückmeldung: Selbstversorger-Lounge ohne Personal, Antwort mit Selbstversorger-Format im Entwurf |
| Welle 1 (21 Mails) | am 10.09. gesendet |
| Welle 2 (25 Mails) | als Outlook-Entwürfe vorbereitet |
