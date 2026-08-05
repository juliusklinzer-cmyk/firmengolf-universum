# Changelog — was ist neu im Universum

Neueste Einträge oben. Nur Änderungen mit Wirkung über ein Projekt hinaus.

## 2026-08-05

- **Geldfluss vollständig festgelegt** (Details `entscheidungen.md`):
  15 Prozent Vermittlung vom vollen Beitrag, tatsächliche Zahlungsgebühren,
  Rest halbiert in monatlichen Fixanteil an den Heimatclub und halbjährlichen
  Pool nach Nutzungsfaktoren mit Greenfee-Deckel je Nutzung. Discover und
  Discover Plus separat über Anlage 1. Wirkung über die App hinaus: Website
  und Vertrieb dürfen keine abweichenden Prozentsätze oder Auszahlungsregeln
  nennen.
- **Halbjährliche Platzmeldung** als Kontrollinstrument eingeführt (Stichtage
  Ende Juni und Ende Dezember, reiner Abgleich ohne Wirkung auf die
  Auszahlung). Relevant für Kooperationsverträge und Partnerkommunikation.

## 2026-08-03 (Nachtrag)

- **Kein Mini-Pilot mehr**: volle Design-Umsetzung, dann Test mit
  Beispieldaten bis alles läuft, dann Go-live (Details entscheidungen.md).

## 2026-08-03

- **App: Anmelde-Flow komplett, Regel „niemand wird abgewiesen"** (Details in
  `entscheidungen.md`): Code-Verifikation per Mail, Optionen bei der
  Domain-Erkennung (Partner wählen / Firma vorschlagen / Newsletter mit
  Double-Opt-in), automatische Aktivierung offener Anfragen bei
  Domain-Freigabe. Newsletter-Anmeldungen aus der App landen in der App-DB
  (nicht bei der Website); bei einer späteren Zusammenführung der
  Verteiler beachten.

- **Arbeitsmodus: Codex/GPT-Delegation beendet**, Claude macht alles selbst
  (Review-Pflicht ADR-002 unverändert).

## 2026-07-31

- **App: FG-Betreiber-Rollen freigegeben + Mini-Admin gebaut** (Details in
  `entscheidungen.md`): platform_staff (support/finance/super_admin),
  Freischaltung/Punkte-Korrektur/DSGVO-Funktionen im Portal unter /admin.
  2FA für FG-Rollen bleibt offener Freigabepunkt vor Staging.

- **Discover+-Preis auf der Website korrigiert und live: 59,90 €** (vorher
  fälschlich 49 €) — fuer-dich + fuer-unternehmen. **Begriff festgelegt:
  „Grundlagenkurs"** statt „Schnupperkurs" (Website-Texte nachziehen).
  App: Rollen-Matrix (13 Rollen) und DB-Schema von Julius freigegeben.

## 2026-07-30

- **Spielrechte-/Punkte-Matrix der App von Julius abgenommen** — inkl. neuer
  Festlegungen: **Discover+ kostet 59,90 € (10 € Eigenanteil)** — ⚠️ Website
  zeigt noch 49 €, Korrektur nötig; Punkte-Umrechnung 1 € = 2 P; Kursregeln
  (1× Grundlagenkurs + 1× Platzreife je Nutzer, Punktekonto während Platzreife
  ausgesetzt); D+-Fixum 10–20 €/Mon. Details: `mitgliedschaften.md`,
  `punktesystem.md`, verbindlich `firmengolf-app/docs/product/
  entscheidungsmatrix-spielrechte.md`.

- **Firmengolf-App: Projektstart.** Plan von Julius genehmigt (Repo
  `firmengolf-app`, docs/architecture/plan.md + ADRs). Stack: Expo (Mitglieder-
  App) + Next.js (Portale) + Fastify-API + Postgres, Hetzner Cloud.
  **Punktesystem entschieden: 100 P/Monat, Verfall am Monatsende** —
  `punktesystem.md` aktualisiert. Betrifft Website (Punkte-Kommunikation
  bleibt gültig) und künftig die Partnerdaten-Hoheit (Phase 7: Website
  konsumiert App-API).

- **Bayerwald heißt jetzt „Titan Golfclub Bayerwald"** (neuer Sponsor, neues
  Logo). Events-Plattform hatte das neue Logo bereits (Club-Upload 29.07.);
  Website firmengolf.app nachgezogen und live deployt (Name + Logo, Slug
  unverändert). Details in `partner-status.md` → Besondere Absprachen.

## 2026-07-25

- **DENIC-Vorfall + one.com-Ablöse-Runbook.** Alle 5 .de-Domains waren offline
  (verpasste Inhaberdaten-Verifizierung via outlook.de-Postfach, behoben durch
  nachgeholte Verifizierung). Neuer Plan `one-com-abloese.md`: visionpunch-Zone
  zu Hetzner, benko + spotee sichern und neu aufsetzen, danach one.com kündigen.

## 2026-07-23

- **Neue Datei `kunden-updates.md`.** Sammelstelle für kundenfertige Update-Texte
  (Partner und Firmenkunden), die Julius regelmäßig als Mail verschickt. Regel für
  alle Projekte: nach jedem kundenrelevanten Release dort einen Eintrag ergänzen.
  Gestartet mit den Juli-Releases der Events-Plattform (glatte Preise, mehrere
  Ansprechpartner je Club, Website-Einbindung der Events, neue Startseite).

## 2026-07-19

- **Abgleich Website ↔ Events durchgeführt.** Differenzen dokumentiert in
  `partner-status.md` (fehlende Club-Assets + Testdaten auf der Events-Plattform,
  Orts-Check Bayerwald) und `infrastruktur.md` (veraltete Domain-/Hosting-Aussagen
  in den Events-Docs — bei Widerspruch gilt dieses Repo).

- **Universum-Repo angelegt** mit Erststand: Mitgliedschaften, Punktesystem
  (inkl. offener Fragen für die App), Partner-Status, Marke & Ton, Vertrieb,
  Infrastruktur, Entscheidungen. Alle drei Projekte sollen ab jetzt hier lesen
  (Sync-Mechanik: `.universum-stand` im Projektordner, siehe README).

## 03.08.2026 (App)

- **Alle drei Portale + Admin auf Design-Stand**: Admin (Dashboard, Nutzer,
  Unternehmen, Golfplätze mit Anlage nach Punkte-System, Logo-Uploads),
  Unternehmensportal (HR-Sichten mit Mindestgruppen-Schutz, DATEV-Export),
  Golfplatzportal (Check-ins, Heimatclub-Verwaltung, Greenfee-Selbstservice).
  Drei Migrationen (Platz-/Firmen-Stammdaten, Nutzungs-Snapshots), sieben
  Review-Pässe (Design, Kritik, Datenschutz) bestanden.

## 04.08.2026
- Kursbindungs-Modell beschlossen (Julius): Zuschuss-Deckel 4 Monatsbeiträge
  je Kurs, Rest Selbstzahler; Mindestlaufzeit ab Kursstart (max. 4 Monate);
  Platzreifekurs-Bindung = Kurs-Modus ohne Punkte mit freier Übungsnutzung am
  Kursplatz. Details in punktesystem.md. App setzt es um (Buchung, Punkte-Stopp,
  Kündigungssperre); OFFEN: Vertragspassus Übungsnutzung während der Bindung,
  Kurs-Modus-UI in der Member-App, AG-Kursfinanzierung als Phase-5-Baustein.
- Owner-Onboarding Golfplatzportal: Admin lädt per Knopf ein, Mail mit
  Passwort-festlegen-Link (Code-Flow), Status am Platz sichtbar.
- Modell-Farben fixiert (04.08., global): Discover #C19AF4, Discover+ #4279D1,
  Access #2C8C99, Access+ #20294D. Quelle: packages/tokens der App
  (--fg-modell-*). Details marke-und-ton.md.
- Zahlungsfehler behoben (05.08.): Jahresverträge wurden mit dem Monatsbetrag
  einmal pro Jahr abgebucht; alle Modelle laufen jetzt monatlich. Kündigung
  und Ende stoppen zusätzlich das Stripe-Abo.
- D+-Fixvergütung: Standard 15 Euro je Mitglied und Monat, je Platz pflegbar.
- Bestandsänderungen gebaut: Modellwechsel, Heimatclub-Wechsel, F5-Austritt,
  F6-Koop-Ende, administratives Beenden.
