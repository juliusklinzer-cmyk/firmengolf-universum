# Infrastruktur-Überblick

Stand: 19.07.2026. Zugangsdaten liegen NICHT hier, sondern je Projekt
(Website: `.deploy-creds.txt`) bzw. im Passwortmanager.

## Domains

| Domain | Zweck | Status |
|---|---|---|
| **firmengolf.app** | Website (live seit 17.07.2026) + künftig App/Benefit | Hetzner, DNS dort |
| **firmengolf-events.de** | Events-Plattform (live) | Hetzner |
| firmen.golf | Alt-Domain, 301 → firmengolf.app | ⚠️ Hosting beim Ex-Partner, Redirect via Plugin — Transfer anstreben |
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
