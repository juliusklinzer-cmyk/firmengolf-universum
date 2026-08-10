# Grundsatz-Entscheidungen (datiert, neueste oben)

- **2026-08-03** — **Kein Mini-Pilot** (Julius). Der früher geplante
  geschlossene Mini-Pilot (1 Firma, ≤ 20 Mitglieder, Wo. 10-14) ist
  GESTRICHEN. Stattdessen: Das Design wird vollständig und bis ins Detail
  umgesetzt (komplett ausgearbeitete Prozesse), dann wird alles mit
  Beispieldaten durchgetestet, bis es läuft; erst danach kommen echte
  Nutzer (Go-live auf eigenem Server). Arbeitsteilung der zwei parallelen
  Claude-Sessions: eine Frontend (Mitglieder-App), eine Backend/Portal.

- **2026-08-03** — **Onboarding-Abschluss (Julius, App-Session):**
  (1) Platzreife im Onboarding ist SELBSTAUSKUNFT (ein Tipp auf "Ja" genügt,
  wird gespeichert und auditiert); die geprüfte Platzreife über die
  Kurs-Journey bleibt unberührt. (2) Heimatclub-Wahl: Wohnort-Eingabe mit
  Ortsvorschlägen (Google sobald Key da, bis dahin OpenStreetMap), Plätze des
  Modells im Umkreis-Verfahren 30 km, sonst 50, sonst 100, sonst alle,
  sortiert nach Entfernung. (3) Zahlung: eigener Zusammenfassungs-Schritt vor
  dem Stripe-Absprung; solange die Zahlung offen ist, ist die Modell-/
  Club-Wahl umstellbar, ab aktiver Mitgliedschaft nicht mehr.

- **2026-08-03** — **Anmelde-Regel (Julius, App-Session): Niemand wird
  abgewiesen.** (1) Die Domain-Erkennung zeigt ihre Optionen DIREKT im ersten
  Registrier-Schritt; ohne erkannten oder gewählten Arbeitgeber gibt es keinen
  Konto-Schritt. (2) Drei Wege bei unbekannter Domain: Firma ist schon Partner
  (aus Liste wählen, Freigabe-Anfrage mit Mail-Domain geht an den Arbeitgeber),
  Arbeitgeber vorschlagen (Lead), Newsletter (Double-Opt-in wie Website, eigene
  Tabelle in der App-DB, unbestätigte Einträge verfallen nach 7 Tagen).
  (3) Domain-Freigabe heilt offene Anfragen: wird die Firmen-Domain
  nachträglich verifiziert, werden offene Freischaltungs-Anfragen bei GENAU
  dieser Firma automatisch aktiv (Domain-Freigabe = Firmen-Freigabe);
  HR-Ablehnungen (blocked) bleiben unangetastet.

- **2026-08-03** — **Arbeitsmodus: Codex/GPT-Delegation beendet** (Julius).
  Genug Claude-Tokens vorhanden; alle Arbeiten inkl. Prüf-Läufe macht Claude
  selbst. Der unabhängige Review-Pass (ADR-002) bleibt Pflicht, läuft aber
  als Claude-Agent.

- **2026-08-01** — **Zahlung + Heimatclub (Julius, App-Session):**
  (1) Zahlungsmittel in der App: Karte, SEPA, Apple Pay, Google Pay, PayPal
  (Stripe-Checkout). (2) Bei Eigenanteil 0 € (AG-Anteil deckt alles) wird die
  Mitgliedschaft OHNE Zahlungsmittel-Hinterlegung direkt aktiviert — bewusste
  Abweichung vom Design-Prototyp ("Zahlungsart hinterlegen"); erst wenn der
  Eigenanteil über 0 steigt, muss hinterlegt werden (Nachforderung bei
  AG-Anteil-Änderung: Phase 3). (3) Heimatclub-Wahl wirkt SOFORT, keine
  Club-Freigabe; Clubs können die Aufnahme neuer Heimatclub-Mitglieder im
  Portal pausieren.

- **2026-07-31** — **FG-Betreiber-Rollen in der App: Schema von Julius
  freigegeben** (Einzelfreigabe laut Arbeitsmodus, in der Arbeitssession).
  Umsetzung der abgenommenen Rollen-Matrix: Tabelle `platform_staff` mit
  Rollen support/finance/super_admin; Vergabe NUR per CLI (`grant-admin`),
  kein Selbst-Service in der App. Mini-Admin (Phase 2) nutzt davon
  Freischaltung, Punkte-Korrektur (nur als adjust-Buchung, auditiert,
  kein Selbst-Aufbuchen), DSGVO-Auskunft/-Löschung nach Löschkonzept.
  **2FA für FG-Rollen: eigener, noch offener Freigabepunkt — hartes Gate
  vor jedem Deployment über die lokale Dev-Umgebung hinaus.** Unabhängiger
  Review-Pass (ADR-002) gelaufen: Urteil mergefähig nach Fix-Runde.

- **2026-07-30** — **Firmengolf-App: Projektstart mit genehmigtem Plan**
  (Details + ADRs in `firmengolf-app/docs/`). Stack: TypeScript-Monorepo —
  Mitglieder-App mit Expo Router (Web/PWA jetzt, native später aus derselben
  Codebasis), Portale/Admin mit Next.js, Fastify-REST-API, Postgres 18,
  Hetzner Cloud VPS (eigene Infrastruktur, getrennt vom Webhosting).
  Rechtsgültige Rechnungen via Lexoffice (E-Rechnungspflicht). **Punkte-System
  bestätigt: 100 P/Monat, Verfall am Monatsende, kein Rollover** (siehe
  `punktesystem.md`). Arbeitsmodus: Migrationen/Auth/Zahlungen/Settlement nur
  mit Einzelfreigabe durch Julius.

- **2026-07-19** — **firmen.golf hat genau eine Aufgabe: 301-Weiterleitung auf
  firmengolf.app.** Mail-Adressen @firmen.golf werden nicht mehr verwendet —
  weder als Absender noch als Empfänger, in keinem Projekt. (Domain liegt noch
  beim Ex-Partner; Transfer angestrebt, bis dahin Redirect via Plugin.)

- **2026-07-19** — Zentrales Wissens-Repo `firmengolf-universum` eingeführt:
  projektübergreifende Wahrheit + Historie via Git, Sync-Merker je Projekt.
- **2026-07-18** — Firmengolf-App wird eigenes Projekt (`~/projects/firmengolf-app`,
  eigenes Git-Repo). Langfristig wird das App-Backend Quelle der Wahrheit für
  Partner-/Modelldaten; Website konsumiert dann per API.
- **2026-07-17** — Website-Domain ist **firmengolf.app** (nicht firmen.golf);
  firmen.golf leitet per 301 um. Alle Partner bleiben live, auch ohne abgelegten
  Vertrag (freundschaftlicher Kontakt; Klärung in Vorstellungs-Terminen).
- **2026-07-17** — Mail-Stack: M365-Postfächer + Brevo-Versand; alle
  Website-Mails im HTML-Design mit persönlicher Julius-Signatur.
- **2026-07-13** — Website-Neustart auf Basis des neuen Design-Handoffs; alte
  Design-Vorgaben gelten nicht mehr. firmengolf-events bleibt separates Projekt.

## 03.08.2026 — Portale komplett, Vertragsdaten-Regeln (App-Session)

- **AG-Anteil-Selbstservice**: Nur der Portal-OWNER einer Firma darf den
  Arbeitgeberanteil ändern (nicht AG-Admins, Rollen-Matrix bestätigt).
  Maximum 49,90 € (Rundungssicherheit Finanzamt), wirkt nach F3 ab
  Folgemonat, append-only historisiert.
- **HR-Nutzungsstatistik nur als eingefrorene Monatsabschlüsse**: write-once
  je Firma und Monat, Mindestgruppe 5 je Monat auf Basis des eingefrorenen
  Werts, laufender Monat nie sichtbar. Grund: Differenzbildung bei
  Mitglieder-Wechseln hätte Einzelnutzung verraten (Threat-Model T1).
  Arbeitgeber sehen nie schwebende Kündigungen oder Zahlungsstatus.
- **Stammdaten zentral**: Golfplätze UND Firmen haben ihre Darstellungs- und
  Vertragsstammdaten (Adresse, Kontakt, DGV/USt-ID, Branche, Logo) in der
  App-Datenbank; Pflege im Admin, Selbstpflege der Portale folgt über die
  Freigaben-Queue. Bild-Upload: PNG/JPG/WebP max 2 MB, bewusst kein SVG.
- **Greenfee-Sonderpreise sind Platz-Selbstservice** (Owner/Manager,
  auditiert, sofort wirksam); vertragliche Club-Preise bleiben exklusiv
  bei Firmengolf. Modell-Erweiterung nur mit Firmengolf-Freigabe.
- **Vier Test-Partnerplätze** (Jersbek, Bergkramerhof, Holledau, Chieming)
  mit echten Daten aus Partnerliste + DGV-Tabelle als Testumgebung;
  Konten testplatz_admin_1-4@visionpunch.de, vor Launch bereinigen.

## 05.08.2026 — Geldfluss beschlossen: Forderungen und Vergütung (App-Session)

Julius hat die vollständige Abrechnungslogik festgelegt. Sie gilt ab sofort
projektübergreifend als verbindliche Rechenregel; Website und Events dürfen
keine abweichenden Zahlen kommunizieren.

**Einnahmen (Forderungsseite)**
- Jedes aktive Mitglied erzeugt je Monat eine Beitragszeile mit dem vollen
  Monatsbeitrag, aufgeteilt in Arbeitgeberanteil und Eigenanteil.
- Unternehmen bekommen EINE monatliche Sammelrechnung, die ausschließlich
  Arbeitgeberanteile enthält. Eigenanteile und Kurs-Selbstzahlerbeträge
  rechnet Firmengolf direkt mit den Mitgliedern ab und zeigt sie dem
  Arbeitgeber nie.
- Selbstzahlerbeträge sind trotzdem vollständig bei uns hinterlegt
  (Beitrags-Eigenanteile und Kurs-Eigenanteile getrennt auswertbar).
- Freigegebene Rechnungen sind unveränderlich.

**Ausgaben (Vergütungsseite), Anlage 2**
- Vermittlungspauschale Firmengolf: 15 Prozent vom VOLLEN Monatsbeitrag.
- Zahlungsabwicklung: die tatsächliche Stripe-Gebühr der jeweiligen Zahlung,
  nicht ein pauschaler Schätzwert.
- Was übrig bleibt, wird halbiert: 50 Prozent gehen als monatlicher Fixanteil
  an den Heimatclub, 50 Prozent in einen Pool. Ein ungerader Cent bleibt beim
  Fixanteil, weil der die monatlich verlässliche Größe für den Club ist.
- Der Pool wird halbjährlich nach Nutzungsfaktoren ausgeschüttet, und zwar JE
  MITGLIED, nicht global. Nur so bleibt clubübergreifendes Spielen korrekt
  zugeordnet: wer vier Runden auf Platz A und eine auf Platz B spielt,
  verteilt seinen eigenen Poolanteil im Verhältnis 4 zu 1.
- Obergrenze je Nutzung: höchstens ein volles Greenfee des jeweiligen Platzes.
  Was darüber liegt (Wenigspieler), geht an den Heimatplatz.
- Wer im Halbjahr gar nicht spielt: der komplette Poolanteil geht an den
  Heimatplatz.
- Ohne Heimatclub und ohne Nutzung bleibt der Betrag als "unverteilt"
  ausgewiesen. Geld verschwindet nie stillschweigend.
- Discover und Discover Plus laufen NICHT über das Faktorenmodell, sondern
  über Anlage 1: Club-Preis je dokumentierter Nutzung plus 15 Euro
  Fixvergütung je Discover-Plus-Mitglied und Monat.
- Freigegebene Vergütungsläufe sind unveränderlich. Korrekturen ausschließlich
  als Korrekturposten mit Begründung.

**Halbjährliche Platzmeldung (Stichtage)**
- Zu den Stichtagen Ende Juni und Ende Dezember liefert jeder Partnerplatz
  einen Export seiner erfassten Nutzungen (Semikolon-Datei, Kopfzeile
  datum;uhrzeit;email;leistung).
- Die Meldung wird gegen unsere Check-ins abgeglichen und zwar in beide
  Richtungen: was der Platz meldet und wir nicht haben, und was wir haben und
  in der Meldung fehlt.
- Die Meldung verändert KEINE Auszahlung. Grundlage der Vergütung bleiben
  ausschließlich unsere Check-ins mit ihren eingefrorenen Snapshots. Wer
  abweichen will, braucht einen Korrekturposten mit Begründung.

## 05.08.2026 (Nachtrag) — Zahlungsgebühren und Beitragsbeginn

**Zahlungsgebühren (recherchiert, Stripe-Preisliste 05.08.2026)**
Stripe kostet uns: EWR-Standardkarte 1,5 Prozent plus 0,25 Euro,
EWR-Premiumkarte 2,8 Prozent plus 0,25 Euro, Karte aus dem Vereinigten
Königreich 2,5 Prozent, internationale Karte 3,15 Prozent (plus 2 Prozent
bei Währungsumrechnung), SEPA-Lastschrift 0,35 Euro pauschal ohne
Prozentsatz. Auf Abo-Zahlungen kommen 0,7 Prozent Billing-Gebühr obendrauf.

Festgelegt (Julius: oberen Satz nehmen und aufrunden):
- **Eigenanteil der Mitglieder: 3,5 Prozent plus 0,25 Euro.** Das ist
  Premiumkarte plus Billing und deckt jede EWR-Karte ab. Eine Karte von
  außerhalb des EWR läge mit rund 3,85 Prozent darüber.
- **Sammelrechnung der Unternehmen: 0,7 Prozent plus 0,35 Euro.** Das ist
  SEPA-Lastschrift plus Billing. Zahlt das Unternehmen per Überweisung,
  entstehen gar keine Zahlungskosten, dann gehört dort 0 hinein.
- Abrechnungslogik: Für Unternehmen ist es EINE Zahlung je Monat, ihre
  Gebühr wird im Verhältnis der Arbeitgeberanteile auf die Beitragszeilen
  verteilt. Für Selbstzahler ist es eine Zahlung je Mitglied und Monat.
- Die Sätze sind im Admin gepflegt und append-only historisiert (ein neuer
  Satz gilt ab dem nächsten Monatsersten, gerechnete Monate bleiben
  unverändert). Sobald die tatsächliche Stripe-Gebühr einer Zahlung
  vorliegt, überschreibt sie den Satz.

**Beitragsbeginn bei Eintritt mitten im Monat**
- **Volle Monatspakete, keine Tagesanteile** — weder beim Mitglied noch
  beim Arbeitgeber. Wer am 10. beitritt, bekommt die vollen 100 Punkte und
  zahlt den vollen Monatsbeitrag; der Arbeitgeber bekommt nie anteilige
  Positionen auf seiner Sammelrechnung. Begründung: Die Leistung wird
  ohnehin im Monatspaket gewährt (100 Punkte, Verfall am Monatsende), also
  wird sie auch im Monatspaket berechnet. Anteilige Sachbezüge hätten die
  Lohnabrechnung der Firmenkunden unnötig verkompliziert.
- Der Einnahmenlauf läuft deshalb **täglich** statt nur am Monatsersten,
  damit ein Beitritt mitten im Monat noch auf der laufenden Sammelrechnung
  landet und uns keine Kosten ohne Gegenwert entstehen.
- **Sammelrechnungen werden erst nach Monatsende freigegeben.** Eine
  freigegebene Rechnung ist unveränderlich; wer im laufenden Monat noch
  beitritt, gehört noch darauf.
- Marktvergleich: EGYM Wellpass lässt Mitgliedschaften immer zum
  Monatsersten starten (Anmeldeschluss der 20.), Golfclubs rechnen bei
  unterjährigem Eintritt ab dem Eintrittsmonat in vollen Monaten. Unsere
  Regel entspricht der Golfclub-Praxis und ist für Mitglieder freundlicher,
  weil sie sofort spielen können.
- **Kurs-Eigenanteil zahlt das Mitglied direkt im Club** (Julius 05.08.),
  Firmengolf zieht ihn nicht ein und vergütet dem Platz nur den Zuschuss.

## 06.08.2026 — Zahlungswege und Heimatclub-Jahresbindung

- **Unternehmen zahlen per Banküberweisung** auf eine normale Rechnung. Dabei
  läuft kein Stripe mit, also entstehen keine Zahlungskosten, die den Plätzen
  abgezogen werden dürften. Der Gebührensatz für Firmenrechnungen steht
  deshalb auf null. Nur Selbstzahler verursachen Stripe-Kosten
  (3,5 Prozent plus 0,25 Euro). Steigt ein Unternehmen später auf
  SEPA-Lastschrift um, gehören dort 0,35 Euro hinein.
- **Der Heimatclub ist an das Kalenderjahr gebunden** (DGV-Realität, Julius
  06.08.): Der Heimatclub stellt den DGV-Ausweis für das ganze Jahr aus und
  meldet das Mitglied für dieses Jahr an den Verband. Ein Wechsel mitten im
  Jahr ist damit ausgeschlossen und wird im System abgelehnt; er wirkt immer
  erst zum 1. Januar. Wichtige Folge für die Abrechnung: In der
  Halbjahres-Ausschüttung kann kein Clubwechsel stattgefunden haben, ein
  Snapshot des Heimatclubs je Monat ist deshalb nicht nötig.
- **Discover hat keinen Heimatclub**: Ein Discover-Mitglied ist nur bei
  Firmengolf Mitglied, nicht in einem Golfclub. Erst ab Discover Plus gibt es
  eine echte Clubmitgliedschaft mit Ausweis.
- **Volle Monatspakete gelten auch bei Eintritt kurz vor Monatsende**
  (bestätigt Julius 06.08.). Wer am 25. eintritt, löst den vollen
  Arbeitgeberanteil aus. Das entspricht der Praxis der Golfclubs (Beitrag ab
  Eintrittsmonat) und MUSS in AGB und Kooperations-/Firmenverträgen klar
  stehen, damit es bei den Firmenkunden nicht zu Diskussionen führt.

## 06.08.2026 (Nachtrag) — Nummern, Buchungswege, Vertragspflege

- **Verträge werden 2026 NICHT mehr angepasst.** Die laufenden Verträge gelten
  nur für dieses Jahr. Alle Änderungen und Ergänzungen werden in
  `vertrag-2027.md` gesammelt und Ende des Jahres in einen neuen Vertrag für
  das Pilotjahr 2027 überführt, der Verlängerung und Änderungen in einem Zug
  kommuniziert und abgesegnet wird.
- **Firmengolf-Nummern** für Golfplätze, Unternehmen und Mitglieder, automatisch
  bei der Anlage vergeben: Format `FG-P-0001`, `FG-U-0001`, `FG-M-0001`
  (Gruppenkürzel, laufende Nummer). Bewusst OHNE Modell im Schlüssel, damit ein
  Upgrade die Nummer nicht ändert und der Ausweis in der Tasche weiter zu den
  Meldedateien der Plätze passt. Ersetzt mittelfristig die E-Mail-Adresse in
  den CSV-Wegen und entspricht damit Anlage 3 des Vertrags.
- **SEPA-Mandat von Anfang an** für die Sammelrechnungen der Unternehmen, weil
  es im Betrieb deutlich einfacher ist als Überweisungen nachzuhalten. Kosten
  0,35 Euro je Unternehmen und Monat.
- **Drei Wege der Startzeitbuchung** (Julius 06.08.): (1) Buchung direkt im
  Firmengolf-System für Plätze ohne eigenes Startzeitensystem, etwa mit
  Ballspirale. (2) Weiterleitung in das eigene Buchungssystem des Clubs, etwa
  PC Caddie — der Regelfall; dazu bekommt der Club eine Anleitung, wie er
  Mitglieder und Nutzungen so dokumentiert, dass die halbjährliche CSV
  auswertbar ist. (3) Später: Schnittstellen zu Albatros, PC Caddie und
  Club in One.
- **Greenfee-Preise sind reine Information** für Nutzer OHNE Spielrecht auf
  dem jeweiligen Angebot und werden vor Ort im Club bezahlt. Sie berühren
  unsere Zahlläufe nicht. Die variable Ausschüttung läuft über die
  Faktorentabelle. ACHTUNG: Der Vertrag nennt in Anlage 2 Ziffer 5.2 eine
  Obergrenze je Nutzung am regulären Greenfee — Widerspruch, siehe
  `vertrag-2027.md` Abschnitt F.

## 06.08.2026 (2. Nachtrag) — Upgrade-Regel, Nummernkreise, Platzsicht

- **Unterjähriges Upgrade: Überschuss geht in den Pool** (entschieden Julius).
  Wechselt ein Mitglied unterjährig auf ein höheres Modell, das sein
  Heimatclub nicht führt, bleibt der Heimatclub bis Jahresende Heimatclub und
  bekommt genau den Fixanteil, der zu SEINEM Modell gehört. Der Mehrertrag
  wandert vollständig in den variablen Pool und damit zu den Anlagen, auf
  denen die neuen Spielrechte tatsächlich genutzt werden. Beispiel Access auf
  Access Plus: Der Heimatclub behält 61,47 Euro im Monat, die zusätzlichen
  20,37 Euro gehen in den Pool. Zum Jahreswechsel wählt das Mitglied einen
  Heimatclub, der das neue Modell führt.
- **Nummernkreise** (Julius 06.08.): Einrichtungen und Personen getrennt.
  Einrichtungen: `PP-0001` Partnerplatz, `PU-0001` Partnerunternehmen.
  Personen: `MA-0001` Mitglied, `GP-0001` Person am Golfplatz, `UP-0001`
  Person im Unternehmen, `FGSA/FGFI/FGSU-0001` Firmengolf-Team nach Rolle.
  Die Mitgliedsnummer ist bewusst NICHT aus der Firmennummer abgeleitet, damit
  sie bei Firmenwechsel oder privater Fortführung bestehen bleibt. Außer beim
  Firmengolf-Team steht keine Rolle im Schlüssel, weil Rollen wechseln und
  eine Person mehrere gleichzeitig haben kann.
- **Reguläres Greenfee ist Pflichtangabe** je Angebot: Es dient der
  Kommunikation (welcher Platz bietet welchen Nachlass) UND als vertragliche
  Obergrenze je Nutzung für den Wenigspieler-Fall.
- **Monatsauswertung je Platz**: Wer wann und wie oft gespielt hat, mit Modell,
  Faktor und Firmengolf-Nummer; eigene Heimatmitglieder namentlich mit
  Fixvergütung, Gastspieler mit Heimatclub. Dazu eine grafische Vorschau auf
  den variablen Anteil des laufenden Halbjahres, ausdrücklich als Pool
  gekennzeichnet, dessen genaue Ausschüttung erst mit der Halbjahresauswertung
  feststeht. Kursteilnehmer in der Bindung werden als künftige Einnahme
  ausgewiesen.
- **Halbjahreslauf niemals automatisch**: Er macht einen erheblichen Teil der
  Jahresvergütung aus. Vorher prüft eine Bereitschaftsansicht, ob je Platz
  entweder eigene Check-ins oder die hochgeladene Meldung vorliegen. Der
  Monatslauf läuft automatisch am 3. und erzeugt nur einen Entwurf.

## 06.08.2026 (3. Nachtrag) — Umsatzsteuer, Ausfallrisiko, Lexoffice

- **KORREKTUR der Vermittlungspauschale**: Die 15 Prozent berechnen sich auf den
  NETTOUMSATZ, nicht auf den Bruttobeitrag. Die Beitragspreise sind
  Endkundenpreise brutto: In 149,00 Euro stecken 23,79 Euro Umsatzsteuer, die
  dem Finanzamt gehören und nicht in den Topf dürfen, der mit den Plätzen
  geteilt wird. Richtig ist also 15 Prozent von 125,21 Euro gleich 18,78 Euro
  statt der bisher gerechneten 22,35 Euro. Der Code hatte es falsch und ist
  korrigiert; entsprechend sinkt der Betrag an die Plätze bei Access von 122,93
  auf 102,71 Euro NETTO. Bei einem umsatzsteuerpflichtigen Platz kommt dessen
  Umsatzsteuer obendrauf (Überweisung dann 122,22 Euro), bei einem
  Kleinunternehmer nicht.
- **Das Ausfallrisiko trägt Firmengolf**: Die Golfplätze bekommen ihre
  Vergütung sofort und unabhängig davon, ob Unternehmen oder Mitglieder bezahlt
  haben. Ausnahmen sind die Kursbindung (Auszahlung nach vier Monaten) und
  später vereinbarte Zahlungsziele. Bleibt eine Forderung offen, wird erinnert,
  gemahnt, gesperrt und zuletzt rechtlich vorgegangen — bei einer offenen
  Firmenrechnung trifft die Sperre alle Mitglieder des Unternehmens, bei einem
  offenen Eigenanteil nur die eine Person.
- **Vergütung der Plätze läuft über Gutschriften** statt über Rechnungen der
  Plätze (Abrechnungsgutschrift nach Paragraf 14 Absatz 2 UStG). Voraussetzung
  ist eine vorherige Vereinbarung im Kooperationsvertrag, siehe
  `vertrag-2027.md`. Steuerdaten der Plätze (USt-IdNr, Steuernummer,
  Kleinunternehmer-Kennzeichen) sind im System vorbereitet.
- **Lexoffice-Anbindung zurückgestellt**: Die Schnittstelle gibt es erst im
  XL-Tarif (32,90 Euro im Monat), Firmengolf hat L (21,90 Euro). Bei einer
  Handvoll Firmenrechnungen im Monat lohnt der Aufpreis nicht. Ersatz ist eine
  Abrechnungsliste je Unternehmen im Admin, aus der die Rechnungen von Hand
  angelegt werden. Wieder aufgreifen ab etwa 20 Firmenkunden oder spätestens
  zur E-Rechnungspflicht (Ausstellen ab 2028, für kleine Unternehmen bis
  800.000 Euro Umsatz Übergangsfrist bis Ende 2027).


## Platzreife-Zeitraum: nur der Kursplatz (Julius, 06.08.2026)

Während ein Platzreifekurs läuft (Wochen bis Monate), spielt und bucht das
Mitglied ausschließlich am durchführenden Golfplatz: Driving Range und
Kurzplatz dort unbegrenzt und ohne Punkte, das Punktekonto pausiert. Andere
Partnerplätze sind im Kurszeitraum für Buchung und Check-in gesperrt, auch
ein Selbstzahler-Weg wird dort nicht angeboten. Das ersetzt die Regel aus dem
Kursbindungs-Modell vom 04.08., nach der fremde Plätze im Kurszeitraum als
Selbstzahler nutzbar gewesen wären. Stöbern, Profil und Mitgliedschaft bleiben
in der App uneingeschränkt; die App kommuniziert die Sperre freundlich.
Bis zum Kursstart gilt weiter der volle Zugriff mit Punkten. Der Fortschritt
der Kursmodule ergibt sich automatisch aus deren festen Terminen (kein
manuelles Abhaken); Terminänderungen durch Golflehrer oder Platz gehen als
Push-Nachricht an die Teilnehmer. Harte Durchsetzung der Sperre serverseitig
(offen, siehe App-Repo docs/backend-aufgaben-frontend.md Punkt 10).

## 06.08.2026 (4. Nachtrag) — Faktoren-Erfassung an Plätzen ohne Buchungssystem

Klarstellung Julius: Das Firmengolf-Startzeitensystem ist KEINE
Startzeiten-Lösung für den Golfplatz. Es dient ausschließlich dem Erfassen der
zahlungsrelevanten Faktoren unserer Mitglieder an Anlagen ohne eigenes System
(typisch: wenig Betrieb, Ballspirale am Abschlag).

- **Der Standardweg ist der QR-Scan am Abschlag**, auch für 9 und 18 Loch —
  wie an der Range. Die Startzeitbuchung in der App ist freiwilliger Komfort
  obendrauf, keine Pflicht.
- **Der Marshal-Scan bestätigt die Wahrnehmung**: Eine Buchung ist nur eine
  Reservierung. Scannt der Marshal den Spielerausweis, wird die Runde im
  selben Zug als dokumentierte Nutzung erfasst und der Faktor gewertet. Der
  Marshal sieht sofort, ob die Runde zählt oder warum nicht (etwa Punkte
  erschöpft, dann Verweis an die Rezeption).
- **Schabernack-Grenze**: Höchstens zwei Platzrunden je Mitglied und Tag, über
  alle Plätze hinweg. 36 Loch am Tag sind Spielbetrieb, die dritte Runde ist
  Faktoren-Sammeln. Nicht als perfekte Sicherheit gedacht, sondern so, dass
  normaler Spielbetrieb nie behindert wird.
- **Auffälligkeiten-Markierung im Admin**: Wer wiederholt Startzeiten bucht
  und ohne Absage nicht erscheint, wiederholt abgelehnte Check-ins sammelt
  oder mehrfach mit ungültigem Ausweis geprüft wird, erscheint mit
  Kontaktdaten in einer Liste. Kein automatischer Bann; ansprechen und
  entscheiden tut ein Mensch. Die Signale werden bei jedem Aufruf frisch
  berechnet, es gibt keinen gespeicherten Marker, der jemandem nachhängt.
- **Mitteilung an den Platz**: Bei jeder Gastbuchung und jeder Absage geht
  eine Mail an die Anlage, denn ohne sie erführe sie von einem
  Firmengolf-Gast nur durch Zufall. Dazu die Tagesliste im Portal fürs
  Starterhäuschen.
- **Spielerausweis in der App** zeigt Name, Modell, Firmengolf-Nummer,
  Profilbild (folgt), QR-Code und die heutige Startzeit mit Platz, Uhrzeit
  und Personenzahl.

## 07.08.2026 — Sperrzeiträume, Zeitfenster-Regel, Mitspieler

- **Sperrzeiträume je Platz**: Owner, Manager und Sachbearbeiter sperren
  geplante Zeiträume (Turnier, Veranstaltung, Witterung, Platzschaden, Umbau)
  mit Von, Bis und Notiz. Mitglieder sehen Grund und Zeitraum in der App und
  können darin keine Startzeiten buchen. Aufheben statt löschen, damit
  nachvollziehbar bleibt, was wann galt. Ergänzt die sofortige
  Betriebs-Sperre, ersetzt sie nicht.
- **Der Marshal-Scan ist nicht der Regelfall** (Julius: etwa jede zehnte Runde
  begegnet einem Marshal). Deshalb bestätigt der EIGENE QR-Scan am Abschlag
  eine gebuchte Startzeit genauso: Buchung wird wahrgenommen, Faktor gewertet.
  Marshal-Scan bleibt der zweite Weg, verfallene Buchungen ohne jeden Scan
  speisen die Auffälligkeiten-Liste.
- **Zeitfenster-Regel je Leistung**: Eine laufende Runde blockiert weitere
  Startzeiten derselben Person an ALLEN Plätzen — Kurzplatz eine Stunde,
  9 Loch anderthalb, 18 Loch dreieinhalb ab Startzeit. Zeiten nach Ablauf des
  Fensters sind vorab buchbar. Der Range-Check-in gilt ohnehin den ganzen Tag
  je Platz (ein Check-in je Leistung, Platz und Tag).
- **Mitspieler-Spiegelung**: Wer bei einer Buchung Kollegen aus dem EIGENEN
  Unternehmen über deren Firmengolf-Nummer mit einbucht, erzeugt bei jedem
  Kollegen eine gespiegelte Startzeit in dessen App; die Personen zählen nur
  einmal in der Kapazität, jeder Kollege wird beim Check-in einzeln erfasst.
  Absage des Buchers nimmt die Spiegel mit. Gäste ohne Firmengolf zählen nur
  in der Personenzahl.
- **Zur Einordnung, nicht in der App abzubilden** (Julius): Clubmitglieder des
  Platzes spielen nach dessen eigenen Regeln unbegrenzt und kostenlos,
  Gastspieler ohne Firmengolf zahlen das volle Greenfee und erhalten nicht
  die Firmengolf-Konditionen. Das regelt der Platz selbst.


## 07.08.2026 — Kurse als vollwertiges Produkt, Module bestimmen die Journey

- **Ein Kurs ist mehr als ein Termin** (Julius, Nachtschicht-Auftrag): Der
  Golfplatz pflegt beim Anlegen und Bearbeiten die komplette Anzeige, die das
  Mitglied in der App sieht: Titel, Beschreibung, Tags, Dauer, Golfpro aus
  dem eigenen Trainerteam, Leihschläger und Rangebälle inklusive, Kursbild,
  Besonderes.
- **Tags statt Einzel-Kategorie** (Julius, gleicher Tag): Firmengolf gibt ein
  festes Vokabular vor (Afterwork, Express, Intensiv, Wochenende), der Platz
  wählt per Mehrfachauswahl GENAU daraus, damit die Begriffe an allen Plätzen
  gleich heißen. "All Inclusive" ist bewusst kein Tag, das sagt schon die
  Preis-Anzeige "Inklusive".
- **Platzreife: bis zu zwölf Einzeltermine je Kurs, jeder Termin ist ein
  Modul** mit eigener Überschrift, Beschreibung, Praxis oder Theorie, Zeitpunkt
  und optionalem Trainer. Diese Module SIND die Golfweg-Journey des
  Teilnehmers in der App; der bisherige feste Sieben-Schritte-Katalog gilt nur
  noch als Rückfall für Altbestand. Kursbeginn und Kursende ergeben sich aus
  erstem und letztem Termin. Der Golflehrer bestätigt Modul für Modul, das
  letzte Modul setzt die Platzreife.
- **Grundlagenkurse als Serie**: wöchentlich oder monatlich mit Wochentag,
  Uhrzeit und Zeitraum angelegt; je Termin entsteht ein eigener buchbarer
  Kurs, damit einzelne Termine absagbar bleiben.
- **Preis und Mindestlaufzeit sind Vertragswerte** und im Formular des
  Platzes sichtbar, aber gesperrt. Das Kurs-Badge (z.B. "Beliebt") vergibt
  ausschließlich Firmengolf, nicht der Platz.

## 07.08.2026 — Kurs-Varianten und Platzprofil-Selbstpflege (Julius, Morgenrunde)

- **Kurs-Varianten**: Ein Golfplatz kann denselben Kurstyp in mehreren
  Ausbaustufen anbieten, z.B. Platzreife Standard 200 Euro (6 Trainerstunden,
  Platzbegehung, Prüfung, Theorieunterlagen) und XL 400 Euro (12 Stunden und
  alles Weitere), ebenso mehrere Grundlagenkurs-Varianten. Die Varianten samt
  Preisen legt Firmengolf im Admin an (Vertragswerte); der Platz wählt beim
  Kurs-Anlegen nur aus. Erwartung: Die meisten Plätze nutzen je einen
  Standardkurs. Buchungen frieren die Konditionen der gewählten Variante ein.
- **Platzprofil-Selbstpflege**: Owner und Manager pflegen Beschreibung,
  Kontakt, Öffnungszeiten, Ausstattung und "Gut zu wissen" selbst im
  Golfplatzportal; wirksam erst nach Firmengolf-Freigabe (Queue). Adresse,
  Name, Bilder und Steuerdaten bleiben bei Firmengolf.

## Punkte-Nachkauf zurückgestellt (Julius, 07.08.2026)

Idee: Mitglieder können Punkte über die Plattform nachkaufen (Stripe, übliche
Zahlungsmittel); zugekaufte Punkte verfallen nicht. Entscheidung: bewusst
zurückgestellt bis nach dem Launch, frühestens wenn erste zahlende Kunden
tatsächlich in die Situation kommen, dass ihnen Punkte fehlen. Bis dahin gilt
das bestehende Ventil Selbstzahler im Clubhaus. Vor einer Umsetzung zu klären:
Paketpreis über dem Modell-Punktwert (keine Kannibalisierung der Upgrades),
zweiter Punkte-Topf ohne Verfall mit Einlöse-Reihenfolge (Monatspunkte zuerst),
Settlement-Kennzeichnung und Umsatzsteuer (Mehrzweck-Guthaben, USt bei Einlösung).

## 07.08.2026 — Nutzerverwaltung im Admin, Impersonation gestrichen

- **"Als Nutzer anmelden" ist endgültig verworfen** (Julius) und wird nicht
  mehr nachgefasst. Support-Fälle laufen über die neue Detailsicht je Person.
- **Vier Nutzergruppen statt einer Tabelle**: Mitglieder, Unternehmens-Team
  (HR-Rollen), Platz-Team, Firmengolf-Team; jede Gruppe zeigt nur die für sie
  sinnvollen Spalten. Punkte sieht man nur bei Discover und Discover +, die
  Vollmodelle zeigen die Faktorsumme des Halbjahres.
- **Datenschutz-Leitplanken bestätigt**: Arbeitgeber sehen NIE Einzelnutzungen
  (nur Monatsaggregate ab Mindestgruppengröße); die Einzel-Spielhistorie im
  Admin, einschließlich der DSGVO-Vollauskunft, ist dem Super-Admin
  vorbehalten, weil zahlungsrelevant. Jede Einzelsicht wird auditiert.
- **Service-Standards**: Passwörter setzt immer der Nutzer selbst (Admin
  stößt nur die Code-Mail an); eine E-Mail-Änderung durch den Support macht
  die neue Adresse unverifiziert und informiert die alte Adresse per
  Sicherheits-Mail; Kündigungen im Auftrag folgen exakt den Regeln der
  Selbstkündigung; Sperren ist Support-Arbeit mit Pflicht-Begründung.

## 10.08.2026 — Auszahlungslogik: drei Grundsatzentscheidungen (Julius)

- **Der Heimatclub des laufenden Jahres bekommt die Vergütung.** Ein Wechsel
  gilt offiziell ab 1. Januar; rückwirkend darf er nie Geld verschieben.
  Technisch wird der Heimatclub deshalb je Abrechnungsmonat eingefroren.
- **Der Marshal-Scan ist eine Kontrolle, niemals ein Check-in.** Er zeigt dem
  Marshal nur, ob das Mitglied gültig und heute eingecheckt ist. Eingecheckt
  wird ausschließlich vom Mitglied selbst per QR am Abschlag oder über die
  CSV-Meldung des Clubsystems. Daraus folgt: EINE Runde ist EINE Erfassung
  je Leistung, Platz und Tag, egal über welchen Weg sie gemeldet wird.
- **Upgrade mit sofortiger Heimatplatz-Wahl fürs Folgejahr**: Wer z.B. auf
  Access Plus upgradet, wählt direkt den Heimatplatz für das nächste Jahr.
  Der bisherige Club bleibt bis 31.12. zugeordnet (und vergütet, gedeckelt
  nach seinem eigenen Modell); der neue Platz wird sofort informiert (Mail
  plus Liste "Kommende Heimatclub-Mitglieder" im Golfplatzportal) und kann
  die DGV-Meldung planen.
- **Greenfee-Preise sind Kundenkommunikation**, keine Abrechnungsgrundlage —
  mit einer Ausnahme: Als vertragliche Obergrenze je Auswärtsrunde im
  Wenigspieler-Schutz (Anlage 2 Ziffer 5.2) fließt das reguläre Greenfee in
  die Pool-Deckelung ein. Das Einfrieren dieses Werts am Check-in ist als
  Absicherung offen (Entscheidung Julius ausstehend).
