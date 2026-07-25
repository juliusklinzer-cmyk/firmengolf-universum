# one.com-Ablöse — Runbook

Ziel (Julius, 2026-07-25): Alles von one.com wegziehen und danach dort kündigen.
Auslöser: DENIC-Vorfall vom 25.07. (alle 5 .de-Domains der VisionPunch UG waren
offline, Ursache verpasste Inhaberdaten-Verifizierung über das outlook.de-Postfach).

**Wichtig:** Die 5 .de-Domains (firmengolf-events, visionpunch, benko-restaurant,
spotee-golf, wirtschaftln) sind als REGISTRIERUNG bereits bei Hetzner. Bei one.com
liegen nur noch: DNS-Zonen (visionpunch, benko, spotee), Webspace + Postfächer
(benko, spotee). wirtschaftln.de und firmengolf-events.de sind schon one.com-frei.

## Ist-Zustand (extern verifiziert, 25.07.)

| Domain | NS (Zone) | Website | Mail |
|---|---|---|---|
| firmengolf-events.de | Hetzner | Hetzner | M365 ✓ fertig |
| wirtschaftln.de | Hetzner | 178.105.234.52 | Hetzner-Mail ✓ fertig |
| visionpunch.de | **one.com** | 301→events (Hetzner-IP) | M365 (MX outlook) |
| benko-restaurant.de | **one.com** | one.com-Webspace | **one.com-Postfächer** |
| spotee-golf.de | **one.com** | one.com-Webspace | **one.com-Postfächer** |

## Phase 1 — visionpunch.de-Zone zu Hetzner (SEO-kritisch, zuerst)

In konsoleH neue DNS-Zone `visionpunch.de` anlegen, exakt diese Einträge
(vollständig aus der one.com-Zone ausgelesen):

| Typ | Name | Wert |
|---|---|---|
| A | @ | 167.235.121.129 |
| A | www | 167.235.121.129 |
| MX | @ | 0 visionpunch-de.mail.protection.outlook.com. |
| CNAME | autodiscover | autodiscover.outlook.com. |
| TXT | @ | "v=spf1 include:spf.protection.outlook.com -all" |
| TXT | @ | "MS=ms75629099" |
| TXT | @ | "google-site-verification=RUIurW4eSC7qMkfeFYQkOrJV5F9Xa2gEJdRPRUVbavQ" |
| TXT | @ | "brevo-code:05ad041addbe789bc1847836389ad299" |
| TXT | _dmarc | "v=DMARC1; p=none; rua=mailto:rua@dmarc.brevo.com" |

Danach in der Hetzner-Domainverwaltung die Nameserver der Domain auf
ns1.your-server.de / ns3.second-ns.de / ns.second-ns.com stellen.
Claude verifiziert anschließend extern (Zone, 301, MX-Auflösung), erst dann gilt
Phase 1 als abgeschlossen.

## Phase 2 — benko-restaurant.de + spotee-golf.de (werden neu aufgesetzt)

1. **Postfächer sichern** (nur Julius kann das): one.com-Webmail prüfen, welche
   Adressen aktiv sind; aufbewahrenswerte Mails per IMAP-Export sichern
   (z. B. Thunderbird: Konto einrichten, Ordner lokal kopieren). OFFEN: welche
   Adressen existieren, wohin künftig (M365 / Weiterleitung / entfällt)?
2. **Webspace:** Wird neu aufgesetzt, kein Migrationsbedarf. Falls alte Inhalte
   als Referenz gebraucht werden: vorher per FTP/Backup ziehen.
3. **DNS-Zonen bei Hetzner anlegen:** minimal A @ + www auf 167.235.121.129
   (Platzhalter/Baustellenseite auf dem Hetzner-Server, analog firmengolf.app
   als eigener vhost-Ordner). MX ERST setzen, wenn die neue Mail-Lösung steht,
   sonst bouncen Mails kommentarlos.
4. Nameserver beider Domains auf Hetzner umstellen, extern verifizieren.

## Phase 3 — restliche Domains im one.com-Konto

OFFEN: Julius prüft die Domain-Liste im one.com-Konto. Nicht-.de-Domains
(z. B. firmen.golf, firmengolf.app, falls dort registriert) brauchen echte
Registrar-Transfers: Auth-Code bei one.com holen, Transfer bei Hetzner (oder
Wunsch-Registrar) einleiten. .de-Domains sind schon weg von one.com.

## Phase 4 — Kündigung

Erst wenn Phase 1 bis 3 extern verifiziert sind: one.com-Abo kündigen
(Kündigungsfrist im Konto prüfen). Vorher NICHTS bei one.com löschen.

## Lehren aus dem 25.07. (parallel umsetzen)

- Domain-Inhaber-Kontakt bei Hetzner von julius.klinzer@outlook.de auf das
  täglich gelesene Postfach umstellen (JULIUS, in konsoleH/Robot).
- Domain-Wächter: täglicher Cron-Check aller 5 Domains gegen die DENIC-Zone
  plus HTTP-Check, Alarm-Mail an Gmail (CLAUDE, auf Go).
