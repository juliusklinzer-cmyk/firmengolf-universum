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
