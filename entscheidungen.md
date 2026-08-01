# Grundsatz-Entscheidungen (datiert, neueste oben)

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
  mit Einzelfreigabe durch Julius. Früher Mini-Pilot ab ~Woche 10 (1 Firma,
  1 Platz, ≤ 20 Mitglieder, manuelle Abrechnung).

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
