# Vertragsänderungen für das Pilotjahr 2027

**Zweck** (Julius, 06.08.2026): Die laufenden Verträge gelten nur für 2026 und
werden NICHT mehr angefasst. Alles, was sich im Betrieb als Änderung oder
Ergänzung herausstellt, wird hier gesammelt und Ende 2026 in einen neuen
Vertrag für das Pilotjahr 2027 überführt. Dieser Vertrag kommuniziert dann in
einem Zug die Verlängerung und alle Änderungen und wird von den Partnern
abgesegnet.

Stand der Referenztexte: `design/project/uploads/` im App-Repo
(Kooperationsvereinbarung Golfplatz mit Anlagen 1 bis 4, Unternehmensvertrag,
Discover, AGB), Fassung vom 30.07.2026.

---

## A. Zahlungsabwicklung (Anlage 2, Ziffer 5)

**Ist im Vertrag:** "Zahlungsabwicklungskosten ca. 1,5 bis 3 Prozent."

**Neu:** Die tatsächlichen Kosten je Zahlungsweg statt einer Spanne.
- Eigenanteil der Mitglieder: Kartenzahlung über Stripe, 3,5 Prozent plus
  0,25 Euro (EWR-Premiumkarte 2,8 Prozent plus 0,7 Prozent Abo-Gebühr).
- Sammelrechnung der Unternehmen: SEPA-Lastschrift, 0,35 Euro pauschal je
  Unternehmen und Monat, unabhängig von der Rechnungshöhe.
- Die Sätze sind im System gepflegt und historisiert; eine Änderung wirkt immer
  erst ab dem folgenden Monatsersten und verändert abgerechnete Monate nie.

Formulierungsvorschlag: statt einer Spanne den Passus "die tatsächlich
angefallenen Kosten der Zahlungsabwicklung, je Zahlungsweg gesondert
ausgewiesen".

## B. Halbjährliche Meldung (Anlage 3)

**Ist im Vertrag:** "Halbjährlich erfolgt die Übermittlung einer CSV-Datei."
Ohne Stichtag, ohne Frist, ohne Folge bei Nichtlieferung.

**Neu:**
- Stichtage: 30. Juni und 31. Dezember, Lieferung binnen vier Wochen.
- Der Upload erfolgt im Golfplatzportal, nicht per Mail.
- Die Meldung ist ein Abgleich, kein Abrechnungsdokument: Grundlage der
  Auszahlung bleiben die im System dokumentierten Nutzungen. Abweichungen
  werden vor der Freigabe eines Laufs gemeinsam geklärt.
- Feldprofil: Der Vertrag nennt Mitglieds-ID, Datum, Art, Club-ID. Genau so
  wird es umgesetzt, sobald die Firmengolf-Nummern in den Portalen sichtbar
  sind (bisher lief es über die E-Mail-Adresse, das entfällt).

## C. Beitragsbeginn und volle Monatspakete (AGB, Unternehmensvertrag)

**Fehlt im Vertrag komplett.**

**Neu:** Beitrag und Leistung werden ausschließlich in vollen Monatspaketen
berechnet, nie tageweise. Wer im laufenden Monat beitritt, erhält das volle
Monatsbudget an Punkten und zahlt den vollen Monatsbeitrag; der Arbeitgeber
erhält entsprechend nie anteilige Positionen auf der Sammelrechnung. Das
entspricht der üblichen Praxis in Golfclubs (Beitrag ab dem Eintrittsmonat) und
hält die Lohnabrechnung der Firmenkunden einfach.

Wichtig für die Kommunikation: Wer sich zum Monatsende anmeldet, zahlt einen
vollen Monat. Das muss in AGB und Unternehmensvertrag klar und auffindbar
stehen, sonst gibt es Diskussionen mit Firmenkunden.

## D. Kursbindung und Übungsflächen (Anlage 1, AGB)

**Fehlt im Vertrag komplett** (Beschluss 04.08.2026).

**Neu:**
- Firmengolf trägt je Kurs höchstens den Zuschuss-Deckel von vier
  Monatsbeiträgen (199,60 Euro). Was darüber liegt, ist Selbstzahleranteil des
  Mitglieds und wird direkt im Club bezahlt; Firmengolf zieht ihn nicht ein und
  vergütet dem Platz entsprechend nur den Zuschuss.
- Der Zuschuss refinanziert sich über eine Mindestlaufzeit ab Kursstart: je
  angefangenem Monatsbeitrag im Zuschuss ein Monat, höchstens vier. Eine
  Kündigung wird frühestens zum Bindungsende wirksam, ein Kursabbruch ändert
  die Bindung nicht.
- Während der gesamten Bindung eines Platzreifekurses gilt der Kurs-Modus:
  keine Punkte-Gutschrift, dafür **unbegrenzte Nutzung der Übungsanlagen am
  durchführenden Platz**. Dieser Passus MUSS in den Kooperationsvertrag, weil
  er eine Leistung des Platzes beschreibt, die über die Kurspauschale
  abgegolten ist. An fremden Plätzen bleibt das Mitglied Selbstzahler.

## E. Heimatclub und Jahresbindung (Anlage 2)

**Neu, zur Klarstellung:**
- Der Heimatclub stellt den DGV-Ausweis für das Kalenderjahr aus. Ein Wechsel
  ist deshalb nur zum 1. Januar möglich und muss vorher angemeldet werden.
- Der Fixanteil steht dem Heimatclub des Kalenderjahres zu, auch wenn das
  Mitglied unterjährig auf ein höheres Modell wechselt.
- Passt der Heimatclub nach einem Upgrade nicht mehr zum Modell, wählt das
  Mitglied zum Jahreswechsel einen neuen Heimatclub.
- OFFEN, siehe F: Wie der Mehrertrag aus einem unterjährigen Upgrade verteilt
  wird.

## F. Obergrenze je Nutzung (Anlage 2, Ziffer 5.2) — KLÄRUNGSBEDARF

**Ist im Vertrag:** "Je Nutzung gilt ein maximaler Auszahlungsbetrag, der sich
am regulären Greenfee des jeweiligen Golfplatzes orientiert. Übersteigende
Anteile werden dem Heimatclub zugeordnet."

**Julius' Beschreibung des tatsächlichen Modells (06.08.2026):** Die variable
Ausschüttung wird rein über die Faktorentabelle verteilt; mit Greenfee-Preisen
wird nicht gerechnet. Die im System gepflegten Greenfees sind Sonderkonditionen
für Nutzer OHNE Spielrecht auf dem jeweiligen Angebot, werden vor Ort im Club
bezahlt und berühren unsere Zahlläufe nicht.

Das ist ein Widerspruch zum Vertragstext und muss vor dem Vertrag 2027
entschieden werden. Umsetzung aktuell: Der Deckel greift dort, wo ein Greenfee
hinterlegt ist; wo keines steht, zählt allein der Faktor. Kein Geld
verschwindet in beiden Fällen.

---

## Nicht vertragsrelevant, aber zu kommunizieren

- Die Betriebs-Sperre eines Platzes (Turnier, Witterung, Umbau) setzt der Platz
  selbst im Portal. Mitglieder sehen die Sperre in der App.
- Drei Wege der Startzeitbuchung: direkt im Firmengolf-System (Plätze ohne
  eigenes System), Weiterleitung ins eigene System des Clubs (Regelfall, dazu
  die Dokumentationshilfe für die halbjährliche Meldung), später Anbindung an
  Albatros, PC Caddie und Club in One.
