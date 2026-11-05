# Entscheidungsprotokoll

Hier wird jede abgestimmte Entscheidung mit Datum und Begründung festgehalten. Was hier nicht steht, ist noch nicht entschieden.

Ändert sich eine Entscheidung später, wird der alte Eintrag nicht gelöscht. Er wird als „ersetzt durch E-xxx“ markiert, damit nachvollziehbar bleibt, warum sich etwas geändert hat.

---

## E-001: GitHub-Repository als zentraler Projektspeicher

- **Datum:** 2026-11-01
- **Status:** entschieden
- **Entscheidung:** Code und Projektdokumentation liegen im Repository `tomfreypt/training`.
- **Begründung:** Die Entwicklungsumgebung ist nur vorübergehend. Alles, was erhalten bleiben soll, muss im Repository gespeichert sein.

---

## E-002: Nutzung nur durch den Trainer, auf Handy und Laptop

- **Datum:** 2026-11-01
- **Status:** entschieden
- **Entscheidung:** Nur der Trainer nutzt das Tool, und zwar auf dem Handy und dem Laptop. Klienten haben keinen Zugang und tragen nichts selbst ein.
- **Begründung:** Das ist die Antwort auf die Frage nach dem Nutzungskontext.
- **Folge:** Auf beiden Geräten müssen dieselben Daten verfügbar sein. Die Oberfläche muss auch auf dem Handy bedienbar sein.

---

## E-003: Web-App mit Datenspeicherung auf einem Server in der EU

- **Datum:** 2026-11-01
- **Status:** entschieden
- **Entscheidung:** Das Tool wird als Web-App gebaut (Variante B). Die Daten liegen bei einem Anbieter in der EU, und nur der Trainer hat ein Konto, abgesichert mit Zwei-Faktor-Anmeldung. Auf dem Handy wird die Web-App als Symbol auf den Startbildschirm gelegt, ohne App Store.
- **Begründung:**
  - Daten nur auf dem jeweiligen Gerät zu speichern (Variante A) würde Handy und Laptop trennen.
  - Ein eigener Abgleich zwischen den Geräten wäre aufwendig und fehleranfällig.
  - Ein Server löst den Zugriff von mehreren Geräten am einfachsten.
  - Ein fertiger Dienst ist sicherer als ein eigener Server, weil Sicherheitsupdates, Sicherungskopien und Anmeldung beim Anbieter liegen.
- **In Kauf genommen:**
  - laufende Kosten, grob 5–25 € pro Monat je nach Anbieter
  - ein Vertrag zur Auftragsverarbeitung nach DSGVO mit dem Anbieter
  - eine Internetverbindung ist nötig, ein Offline-Modus kann später ergänzt werden
- **Nicht gewählt:** Variante A (Speicherung auf dem eigenen Gerät), auch nicht mit eigenem Abgleich zwischen den Geräten.

---

## E-004: Bewertungsskala mit fünf Stufen und Referenzsituationen

- **Datum:** 2026-11-05
- **Status:** entschieden
- **Entscheidung:**
  - Soll, Ist und später Übungen werden auf derselben Skala mit fünf Stufen von 0 bis 4 bewertet.
  - Zusätzlich gibt es „nicht bewertet“, und das ist nicht dasselbe wie 0.
  - Die Stufen können pro Anforderungsbereich an Referenzsituationen festgemacht werden.
  - Begonnen wird ohne Vorarbeit mit allgemeinen Stufenbeschreibungen. Referenzsituationen werden nach und nach für häufig genutzte Bereiche ergänzt.
- **Begründung:** Nur wenn Soll und Ist an denselben realen Situationen festgemacht sind, sind sie wirklich vergleichbar und bleiben über Wochen einheitlich.
- **Nicht gewählt:**
  - drei Stufen (zu grob, Fortschritte innerhalb einer Stufe bleiben unsichtbar)
  - fünf Stufen ohne Referenzsituationen (wirkt genauer, als es ist)
- **Details:** [02-bewertungsmodell.md](02-bewertungsmodell.md)

---

## Offen

| Thema | Wo beschrieben | Stand |
|---|---|---|
| Konzeptentwurf Phase 1 | [01-konzept.md](01-konzept.md) | Entwurf, noch nicht abgestimmt |
| Stufenbeschreibungen und Zuordnung der Referenzsituationen (Bereich × Körperregion) | [02-bewertungsmodell.md](02-bewertungsmodell.md) | Vorschlag liegt vor |
| Erste Liste der Anforderungsbereiche | [01-konzept.md, Abschnitt 3](01-konzept.md#3-grundlegende-datenstruktur) | nächster Schritt danach |
| Aufteilung nach Gerät (Handy für schnelle Einträge, Laptop für Analyse) | [01-konzept.md, Abschnitt 6](01-konzept.md#6-technische-architektur) | Vorschlag, noch nicht abgestimmt |
| Technik (Programmiersprache, Bildschirme, Datenbank) | [01-konzept.md, Abschnitt 6](01-konzept.md#6-technische-architektur) | Vorschlag liegt vor (TypeScript, React, relationale Datenbank) |
| Anbieter für Server und Datenbank | – | offen, wird vor Beginn von Phase 2 geklärt |
