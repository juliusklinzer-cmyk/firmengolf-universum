# Firmengolf-Universum — das zentrale Gehirn

Ein Repository für alles, was **mehr als ein Projekt betrifft**. Die drei Projekte
(Website `Firmengolf Webseite`, `firmengolf-events`, `firmengolf-app`) lesen hier,
bevor sie arbeiten — und schreiben hierher, wenn eine Änderung Auswirkungen über
das eigene Projekt hinaus hat.

## Regeln

1. **Hier liegt die Wahrheit über das Geschäft**, nicht über Code: Mitgliedschaften,
   Punktesystem, Partner-Status, Marke & Ton, Infrastruktur, Entscheidungen.
   Projektspezifisches (Templates, Deploy-Details) bleibt im jeweiligen Projekt.
2. **Jede Änderung = ein Git-Commit** mit sprechender Message. Die Historie IST das
   Gedächtnis („was hat sich wann geändert und warum").
3. Änderungen mit Auswirkung auf andere Projekte bekommen zusätzlich eine Zeile in
   `CHANGELOG.md` (menschenlesbar, neueste oben).
4. **Sync-Mechanik für Claude-Sessions:** Jedes Projekt hat eine Datei
   `.universum-stand` mit dem zuletzt gelesenen Commit-Hash. Bei Sessionstart:
   `git -C ~/projects/firmengolf-universum log --oneline <hash>..HEAD` zeigt, was
   seitdem neu ist → relevante Dateien lesen → Marker auf HEAD setzen.
5. Kein Detail-Duplikat: Wenn eine Info woanders maschinenlesbar lebt (z. B.
   Partnerkonditionen in `inc/partners.php` der Website), verweist die Datei hier
   dorthin, statt die Werte zu kopieren.

## Dateien

| Datei | Inhalt |
|---|---|
| `mitgliedschaften.md` | Die 4 Modelle + Spielrechte-Logik |
| `punktesystem.md` | Punktekonto: Stand + offene Fragen |
| `partner-status.md` | Verträge, offene Klärungen je Club |
| `marke-und-ton.md` | Sprache, Design-Grundwerte, Social Accounts |
| `vertrieb.md` | Funnel, Preise, Argumente, Lead-Kanäle |
| `infrastruktur.md` | Domains, Hosting, Mail, Keys, Accounts |
| `entscheidungen.md` | Datierte Grundsatz-Entscheidungen |
| `kunden-updates.md` | Kundenfertige Update-Texte für Julius' Update-Mails (nach jedem kundenrelevanten Release ergänzen) |
| `CHANGELOG.md` | Was ist neu — für Menschen und Sessions |
