# Mitgliedschafts-Modelle & Spielrechte

Quelle: `Firmengolf_Mitgliedschaftslogik.docx` (Julius) · technisch umgesetzt in
`fg_play_status()` der Website (`inc/partners.php`). Stand: Juli 2026.

## Die 4 Modelle

| Modell | Kern | Spielrechte |
|---|---|---|
| **Discover** | Reine Firmengolf-Mitgliedschaft ohne Clubbindung — der Einstieg | Training/Kurse auf Discover-Plätzen, Range & Kurzplatz übers **Punktekonto** |
| **Discover +** | Echte Clubmitgliedschaft im Heimatclub (DGV-Ausweis, Handicap). **Setzt die Platzreife voraus** — reine Greenfee-Mitgliedschaft mit Trainingspunkten für Golfer; Grundlagen-/Platzreifekurse werden D+ weder angezeigt noch sind sie buchbar (30.07.2026) | Punktekonto wie Discover; Platzrunden ÜBERALL (auch am Heimatclub) nur gegen (oft vergünstigtes) Greenfee — kein Freispielrecht. Präzisiert 30.07.2026 mit der App-Entscheidungsmatrix; der Heimatclub liefert Ausweis/HCP |
| **Access** | Volles Spielrecht im Netzwerk | Unlimitiert auf allen Access-Plätzen |
| **Access +** | Das große Spielrecht | Zusätzlich alle A+-Plätze |

## Regeln

- Ohne Clubmitgliedschaft darf man in Deutschland nicht auf den Platz — deshalb ist
  ab Discover + eine echte Mitgliedschaft im Heimatclub enthalten.
- Welche Modelle auf welchem Platz gelten, definiert der Kooperationsvertrag je Club
  (maschinenlesbar: `membership`-Array je Partner in `inc/partners.php`).
- Einschränkungen möglich, z. B. Gut Kaden „Kaden Woche": Access nur Mo–Fr.
- Greenfee-Sonderkonditionen je Platz: `gf_dplus` / `gf_gast` (ebd.).
- UI-Regel Partnerplätze-Karte: Nutzer wählt Modell → jede Anlage zeigt, was sie
  damit bekommt (inklusive / unlimitiert / gegen Greenfee).

## Preise (Julius, 30.07.2026 — mit App-Matrix abgenommen)

- Discover 49,90 €/Mon · **Discover+ 59,90 €/Mon (10 € Eigenanteil)** ·
  Access 149 €/Mon · Access+ 199 €/Mon. AG-Anteil max. 49,90 €.
- ⚠️ **Website zeigt für Discover+ noch 49 €** (`fg_models()` in
  `inc/partners.php`) — auf 59,90 € korrigieren (Tier-Karten, Vergleichstabelle,
  FAQ prüfen).
- D+-Fixum an den Heimatclub: 10–20 €/Monat je aktivem D+-Mitglied, vertraglich
  individuell je Club-Satzung.
- Verbindliche Regel-Referenz für die App:
  `firmengolf-app/docs/product/entscheidungsmatrix-spielrechte.md`
  (abgenommen 30.07.2026).

## Perspektive

Die App wird die Quelle der Wahrheit für Modelle & Spielrechte (Backend + API);
die Website konsumiert dann von dort. Bis dahin gilt `inc/partners.php`.
