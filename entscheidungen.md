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
