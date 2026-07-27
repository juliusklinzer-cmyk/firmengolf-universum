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

## Status-Update 27.07. (nachts, ~23:45)

- **erwincklinzer.at GEKLAERT + LIVE**: Kuenstler-Nebenprojekt (Erwin C. Klinzer,
  Elementor-Seite). one.com-Backup (Files 99MB + DB-Dump, Stand 18.06.) auf www733
  wiederhergestellt: Ordner public_html/erwincklinzer.at, EIGENE DB c5wkuy_db1 auf
  lx55.your-database.de (nichts mit Firmengolf vermischt), onecom-Plugins vorab
  deaktiviert, frische wp-config, Zone A/AAAA auf www733 korrigiert (AAAA zeigte
  auf www4!), Addon-Domain + SSL durch Julius, extern verifiziert (Titel, Login,
  0 one.com-Reste, 301 apex→www). OFFEN: MX zeigt auf www4 (ins Leere) — nur
  relevant, falls der Kuenstler je eine @erwincklinzer.at-Mail braucht.
- **Events-Ausfall 22:09–22:51 aufgeklaert**: DB-Server lqxc (=sql792) war nicht
  erreichbar (vermutl. Wartungsserie wie sql812/sql815 laut konsoleH-Status).
  Tracker-Historie zeigt: 25.07. = DENIC-Vorfall, 23.07. = Webserver-Schluckauf
  (events+app zeitgleich, verschiedene DB-Hosts) → KEIN chronisches lqxc-Problem,
  kein DB-Umzug noetig. Lehre offen: automatische DB-Backups einrichten.

## Status-Update 27.07. (spaet abends)

- **spotee-golf.de: Umzug KOMPLETT** (Duplicator 1,4 GB, DB lx4c/c5wkuy_db1, NS
  geschwenkt, SSL aktiv, Installer-Dateien entfernt, one.com-Plugins deaktiviert
  [onecom-themes-plugins, onecom-spam-protection], Mail auf M365 umgestellt
  [MX spoteegolf-de01e...outlook, Aliase in M365 angelegt], Plugins/Core nach
  Umzug aktualisiert [Health-Monitor-Luecken], extern voll verifiziert).
- Verbleibend: benko-NS-Schwenk (Koch-Termin; Zone verifiziert schwenk-bereit),
  erwincklinzer.at-Klaerung, dann Kuendigungsfreigabe. Julius-PC: hosts-Zeilen
  (spotee IPv4+IPv6, ggf. fair-way) wieder entfernen.

## Status-Update 27.07. (abends)

- **fair-way-golf.com: Umzug KOMPLETT** (Duplicator auf Hetzner, DB lx2m, NS
  geschwenkt, SSL aktiv, Installer-Dateien entfernt, one.com-Plugins deaktiviert,
  M365-Mail unterbrechungsfrei, extern voll verifiziert). Einordnung von Julius:
  Ueberbleibsel eines inzwischen insolventen Projekts, wird spaeter eh neu
  gebaut → KEINE weitere Pflege/Optimierung investieren (PHP memory_limit 128M
  reicht knapp; Elementor-Editor kann Memory-Fatals werfen — bewusst ignoriert,
  bei Bedarf Serverkonfiguration → memory_limit 512M).
- Verbleibend vor one.com-Kuendigung: spotee (DB + Duplicator + Weiterleitungs-
  Frage), benko-NS-Schwenk (Koch-Termin), erwincklinzer.at-Klaerung (404, Zweck
  unklar), finale Freigabe durch Claude.

## Status-Update 27.07.

- Phase 1 (visionpunch) ERLEDIGT: NS auf Hetzner, extern verifiziert.
- benko: neues WordPress liegt auf dem Hetzner-Server (public_html/benko.restaurant),
  Vhost liefert es bereits aus; hallo@ als Hetzner-Postfach angelegt + Mailimport
  gelaufen. OFFEN: fistion@ anlegen+importieren, Koch-Termin, NS-Schwenk, SSL,
  Delta-Mailimport, Koch-Handy (IMAP/SMTP www733.your-server.de, 993/587).
- NEU: fair-way-golf.com gehoert ebenfalls dazu. Registrierung ist SCHON bei
  Hetzner (kein Transfer noetig), NS noch one.com, Website = WordPress bei
  one.com, Mail = direkt Microsoft 365 (MX fairwaygolf-com01bb...).
- spotee + fair-way: Julius will beide Websites 1:1 zu Hetzner umziehen
  (Duplicator-Weg wie beim Go-Live), Mails unveraendert weiterlaufen lassen.

### Zonen-Soll vor dem NS-Schwenk (in konsoleH DNS-Verwaltung anpassen!)

fair-way-golf.com — vorbereitete Hetzner-Zone zeigt auf FALSCHEN Server (www4):
| Typ | Name | Soll |
|---|---|---|
| A | @ und www | 167.235.121.129 (statt 88.198.219.246) |
| MX | @ | 0 fairwaygolf-com01bb.mail.protection.outlook.com. (statt www4) |
| TXT | @ | "v=spf1 include:_spf.mlsend.com include:spf.protection.outlook.com -all" |
(_custspf.one.com aus dem alten SPF entfaellt nach dem Wegzug; MailerLite bleibt.)

spotee-golf.de — A stimmt schon (167.235.121.129); MX haengt an der Mail-Klaerung
(one.com-Weiterleitungen fuer spotee pruefen: existieren welche, wohin?).

### Cutover-Ablauf je Domain (Duplicator)
1. Duplicator-Paket auf dem one.com-WP bauen (Julius, wp-admin), Download-Links an
   Claude → Claude laedt Pakete und legt sie per SFTP in den Ziel-Ordner.
2. konsoleH: neue DB je Domain (Host lqxc.your-database.de), Web-Bereich/Ordner
   wie bei benko anlegen, Zone nach Solltabelle.
3. NS-Schwenk → Installer im Browser am echten Domainnamen (kurzes Fenster,
   Seiten sind wartungsarm) → SSL Manager → Permalinks speichern.
4. Claude verifiziert extern (Seite, Blogartikel, MX/M365, SSL).

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
