# Punktesystem (Discover-Punktekonto)

Stand: Juli 2026 — Basis-Mechanik live auf der Website, Details entstehen mit der App.

## Aktueller Stand

- Discover-Mitglieder haben ein **Punktekonto** in der Firmengolf App und lösen
  damit Leistungen auf Partnerplätzen ein — v. a. **Driving Range** und **Kurzplatz**.
- Je Partner sind Punktwerte hinterlegt (`punkte` => `range` / `kurz` in
  `inc/partners.php` der Website, z. B. Range 15 P., Kurzplatz 20 P.).
- Kommunikation auf der Website: „Discover: übers Punktekonto · Access & Access+:
  unlimitiert".

## Entschieden (Julius, 30.07.2026 — App-Planungsrunde)

- [x] **Budget: 100 Punkte/Monat** (bestätigt; stand bereits als
  `fg_punkte_budget()` im Website-Code und in der Website-Kommunikation).
- [x] **Verfall am Monatsende, KEIN Rollover** — jeden Monat frische 100 P,
  Rest verfällt. Begründung: einfachste Kommunikation („Monatsbudget"),
  planbare Kosten gegenüber den Plätzen, einfaches Datenmodell
  (Perioden-Ledger statt FIFO-Credits).
- [x] **Punkte-System gilt für die App** — der Design-Prototyp zeigte
  stattdessen Frei-Kontingente (4×/2× pro Monat); diese Mechanik wird NICHT
  gebaut, die betroffenen Screens (Check-in, Profil, Mitgliedschaft) werden
  auf Punkte-Anzeige angepasst.

- [x] **Kurse laufen außerhalb der Punkte** (30.07.2026): je Nutzer 1×
  Grundlagenkurs + 1× Platzreifekurs (danach dauerhaft abgeschlossen, nie
  wieder buchbar).
- [x] **Kursbindungs-Modell** (04.08.2026, ersetzt die alte 350-€-Schwelle):
  Firmengolf trägt je Kurs maximal den Zuschuss-Deckel von 4 Monatsbeiträgen
  (199,60 €, kommuniziert "bis 200 €"); alles darüber ist Selbstzahleranteil
  des Mitglieds (Beispiel Gut Kaden: Platzreife 359 € → 159,40 € Eigenanteil).
  Der Zuschuss refinanziert sich über eine Mindestlaufzeit ab KURSSTART: je
  angefangenem Monatsbeitrag im Zuschuss ein Monat, maximal 4. Kündigung wird
  frühestens zum Bindungsende wirksam (wie Jahresvertrag); Kursabbruch ändert
  die Bindung nicht; bei Jobwechsel wird privat weitergeführt.
  Beim PLATZREIFEKURS gilt für die GESAMTE Bindung der Kurs-Modus: keine
  Punkte-Gutschrift, dafür unbegrenzte Übungsanlagen-Nutzung am durchführenden
  Platz (über die Kurspauschale abgegolten, MUSS so in den Kooperationsvertrag),
  an fremden Plätzen Selbstzahler. Ohne Punkte-Nutzungskosten ist der Zuschuss
  durch die laufenden Beiträge praktisch exakt gegenfinanziert. Der
  Grundlagenkurs erzeugt nur die Mindestlaufzeit (kein Kurs-Modus).
  Member-App: Kurs-Modus als eigene Oberfläche ("Platzreife-Programm"),
  nach Bindungsende öffnet sich die Punkte-Golfwelt.
- [x] **D+-Fixvergütung: Standard 15 Euro** (05.08.2026, Julius): Je
  aufgenommenem Discover-Plus-Mitglied und Monat zahlt Firmengolf dem
  Heimatclub eine Fixvergütung. Pilotrahmen 10 bis 20 Euro (je nach Satzung
  des Clubs verhandelbar), **Standard 15 Euro**. Der Wert steht je Platz im
  System (courses.dplus_fix_cents) und wird im Admin gepflegt; Grundlage für
  die Abrechnung ab Phase 5.
- [x] **Bestandsänderungen** (05.08.2026): Modellwechsel im Bestand (Upgrade
  sofort, Downgrade zum Laufzeitende und nie vor Ende einer Kursbindung),
  Heimatclub-Wechsel (sofort), Firmenaustritt nach F5 (Monatsmodell: Ende zum
  Monatsende; Jahresvertrag zusätzlich privat fortführen bis 31.12. oder
  Übertrag zu einem Partnerunternehmen), Kooperationsende nach F6 (alle
  Mitgliedschaften zum 31.12.) und administratives Beenden im Support-Notfall.
- [x] **Keine Team-Punkte, keine Übertragbarkeit** (30.07.2026).
- [x] **Umrechnung: 1 € = 2 Punkte** (30.07.2026): Punkte sind Gegenwerte der
  festen Club-Preise; der Admin erfasst bei Vertragserstellung den €-Preis je
  Leistung, das System rechnet in Punkte um (10 € Range = 20 P, 5 € = 10 P).
  Kalkulatorisch bewusst: Worst Case zahlt Firmengolf drauf.
- [x] **Access/Access+ auf reinen Discover-/D+-Plätzen** (30.07.2026): kein
  Spielrecht (keine variable Auszahlung dort); optional kann der Platz ein
  vergünstigtes Rangefee anbieten (Zahlung im Club).

## Offen / in Klärung

- [ ] Punktpreise pro Leistung final je Club bestätigen (aktuelle Werte = Vertragsstand)
- [x] **Begriff entschieden (31.07.2026): „Grundlagenkurs"** ist der offizielle
  Name (statt „Schnupperkurs"). App nutzt ihn ab sofort; Website-Texte bei
  nächster Gelegenheit nachziehen (Kursnamen auf Platz-Detailseiten, FAQ).

> Änderungen am Punktesystem hier dokumentieren + CHANGELOG-Eintrag — betrifft
> App (Backend/UI), Website (Platz-Detailseiten, FAQ) und ggf. Events (Pakete).
