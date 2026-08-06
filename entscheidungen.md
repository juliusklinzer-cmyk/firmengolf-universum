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

