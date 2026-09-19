# Infrastruktur-Überblick

Stand: 19.07.2026. Zugangsdaten liegen NICHT hier, sondern je Projekt
(Website: `.deploy-creds.txt`) bzw. im Passwortmanager.

## Domains

| Domain | Zweck | Status |
|---|---|---|
| **firmengolf.app** | Website (live seit 17.07.2026) + künftig App/Benefit | Hetzner, DNS dort |
| **firmengolf-events.de** | Events-Plattform (live) | Hetzner |
| firmen.golf | NUR 301 → firmengolf.app, sonst nichts. Mails @firmen.golf werden NICHT mehr verwendet | ⚠️ Hosting beim Ex-Partner, Redirect via Plugin — Transfer anstreben |
| visionpunch.de | 301 → firmengolf-events.de, später Onepager | Hetzner |

## Hosting

- **Hetzner Webhosting L** (Account „VisionPunch", konsoleH, Server www733):
  beide Websites. Events-WP in `/public_html`, Website-WP in
  `/public_html/firmengolf.app`. DB-Server `ltyh.your-database.de`.
- **App-Backend**: braucht später eigene Infrastruktur (Hetzner Cloud o. ä.) —
  Webhosting reicht dafür nicht.
- **App-STAGING (seit 03.08.2026)**: läuft auf dem Wirtschaftln-Server mit
  (Hetzner Cloud CPX12, 178.105.234.52, Nürnberg) — Kostenentscheidung
  Julius. Eigene Docker-Gruppe unter /opt/firmengolf-staging (Postgres 18,
  API, Worker, statische Web-App), harte Speicher-/CPU-Limits, Wirtschaftln
  hat Vorrang und darf nichts merken. Eingang: staging.firmengolf.app über
  den Wirtschaftln-Caddy (edge-Docker-Netz). NUR Testdaten, Stripe-Testmodus.
  HARTE GRENZE: Zum Go-live mit echten Personendaten zieht Firmengolf
  auf einen eigenen Server (~5 €/Monat). Details:
  firmengolf-app/deploy/staging/README.md

## Mail

- Postfächer: **Microsoft 365** (Tenant visionpunch.de). `hallo@firmengolf.app`
  + Aliase (website@, julius@, datenschutz@, partner@, presse@) auf Julius.
- Transaktionsversand: **Brevo** (SMTP-Relay), Domain firmengolf.app
  authentifiziert (DKIM/DMARC = PASS). Eigener SMTP-Key je Projekt!

## Google

- **Maps**: Website-Key (Referrer firmengolf.app) + Map-ID · **App-Key separat**
  (API-beschränkt, Budget-Alarm aktiv) — Keys nie zwischen Projekten teilen.
- **GA4**: Website `G-NBZH1PR8M2` (Consent-gated via Klaro) · Events eigene Property.
- **Search Console**: Domain-Properties für firmengolf.app + firmengolf-events.de.

## Meta (Werbung)

- **Meta Pixel „FGE Web"**: `1378606913654515` auf firmengolf-events.de
  (seit 1.9.126, 20.08.2026). Klaro-Dienst `meta-pixel` in der Kategorie
  Marketing, lädt nur nach Einwilligung; bewusst ohne noscript-Fallback und
  ohne automatischen erweiterten Abgleich (autoConfig false). Events nur
  PageView (nach Einwilligung, alle Seiten) und Lead (abgesendete
  Event-Anfrage, derselbe Auslöser wie die Google-Ads-Conversion).
- Lead trägt eine serverseitige event_id (UUID je Anfrage, Meta
  `_fge_meta_event_id` am Request): Pflicht für die Deduplizierung, wenn die
  **Conversions API** später an dieselbe Datenquelle sendet (geplant, noch
  nicht gebaut).

## Monitoring

- UptimeRobot: firmengolf.app + firmengolf-events.de.

## App: Betriebsregeln Auth/2FA (seit 31.07.2026)

- FG-Admin-Zugänge (support/finance/super_admin) haben TOTP-2FA-Pflicht;
  Einrichtung im Portal unter /admin/sicherheit, Backup-Codes beim Login
  nutzbar. Dev-Ausnahme APP_FG_2FA_PFLICHT=0 wirkt NIE in Produktion.
- ⚠️ AUTH_SECRET verschlüsselt auch die TOTP-Secrets und Backup-Codes:
  eine Rotation des Secrets sperrt ALLE FG-Admins aus (2FA muss danach
  neu eingerichtet werden). Rotation nur geplant, nie nebenbei.
- Notfall-Entsperrung (Handy + Backup-Codes weg): per SQL
  `update "user" set two_factor_enabled=false` + Zeile in two_factor
  löschen — nur durch Julius' Betreiber-Zugang, danach 2FA sofort neu
  einrichten.

## ⚠️ Veraltete Aussagen in älteren Projekt-Dokus (Stand-Hygiene)

- Events-Docs (Stand 02.07.2026) sagen „firmengolf.app reserviert, NICHT verwenden"
  und „firmen.golf nie als Mail-Domain" — **überholt seit 17.07.2026**: Die Website
  lebt auf firmengolf.app, Mail läuft über @firmengolf.app, firmen.golf leitet um.
- Events-Go-Live-Runbooks referenzieren One.com — Hosting ist längst Hetzner.
- Bei Widersprüchen zwischen Projekt-Doku und diesem Repo gilt: **dieses Repo.**

## Google Analytics: Bestandsaufnahme 19.09.2026 (Konten und Properties)

| Konto | Property | Stream(s) | Mess-ID | Status / Plan |
|---|---|---|---|---|
| FairWayGolf 186456140 | Fair-Way-Golf – GA4 (352922895) | www.fair-way-golf.com | G-W3C5ZYZKLL | **aktiv**, seit 19.09. auf der neuen Seite |
| FairWayGolf | fair-way-golf.com/ GA4 - MonsterInsights (360965649) | alt | – | Papierkorb (altes Plugin) |
| Firmengolf 374654288 | Firmengolf-Events (544641045) | firmengolf-events.de | G-17GGY2WEEV | **aktiv** (Events-Seite) |
| Firmengolf | Firmenevents (543051965) | visionpunch.de | – | keine Daten, Karteileiche |
| Firmengolf | www.firmen.golf (512498120) | www.firmen.golf, firmen.golf | – | keine Daten (firmen.golf leitet auf firmengolf.app) |
| Spotee-Golf 218971119 | Firmengolf.app (546099170) | firmengolf.app | G-NBZH1PR8M2 | **aktiv**, gehört ins Konto Firmengolf (verschieben) |
| Spotee-Golf | Spotee-Golf (301738806) | www.spotee-golf.de | – | behalten für den Spotee-Neubau |
| Spotee-Golf | Spotee-Golf – … (301752728) | www.fair-way-golf.de, www.spotee-golf.de, firmen.golf | G-MT7VRFWH8J (fair-way-golf.de-Stream) | Sammelsurium der alten Seiten, nach Spotee-Neubau Papierkorb |

Wunsch Julius: Konto Firmengolf = Events, firmengolf.app, firmen.golf; Konto Spotee-Golf = nur Spotee.
Hinweis: spotee-golf.de war am 19.09.2026 nicht erreichbar (Verbindung abgelehnt).
