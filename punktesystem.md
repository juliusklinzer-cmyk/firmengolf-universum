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

## Offen / in Klärung

- [ ] Punktpreise pro Leistung final je Club bestätigen (aktuelle Werte = Vertragsstand)
- [ ] Können Punkte für Kurse/Schnuppertermine eingesetzt werden?
- [ ] Übertragbarkeit / Team-Punkte?

> Änderungen am Punktesystem hier dokumentieren + CHANGELOG-Eintrag — betrifft
> App (Backend/UI), Website (Platz-Detailseiten, FAQ) und ggf. Events (Pakete).
