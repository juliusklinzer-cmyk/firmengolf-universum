# Changelog — was ist neu im Universum

Neueste Einträge oben. Nur Änderungen mit Wirkung über ein Projekt hinaus.

## 2026-07-30

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
