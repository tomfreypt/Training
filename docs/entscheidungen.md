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

## E-005: Eigene Angabe „statisch / dynamisch“ statt einer Stufe auf der Skala

- **Datum:** 2026-11-05
- **Status:** entschieden
- **Entscheidung:** Neben der Stufe 0 bis 4 bekommt jede Bewertung die optionale Angabe „statisch“ oder „dynamisch“. Die Skala selbst bleibt unverändert.
- **Begründung:** Eine Stufe „statisch“ am Anfang der Skala würde bedeuten, dass statische Belastung immer leichter ist als dynamische. Bei der Kontrolle trifft das oft zu, bei mechanischer Belastung häufig nicht, zum Beispiel bei einer schweren isometrischen Haltung. Als eigene Angabe bleibt sichtbar, ob ein Klient ein Belastungsniveau nur statisch oder auch dynamisch erreicht. Daraus ergibt sich der Progressionsschritt von statisch zu dynamisch.
- **Nicht gewählt:** „statisch“ als unterste Stufe der Skala, sodass die Skala auf sechs Stufen anwächst.
- **Anstoß:** Vorschlag des Projektinhabers, „statisch“ an den Anfang der Skala zu setzen.
- **Details:** [02-bewertungsmodell.md, Abschnitt 4](02-bewertungsmodell.md#4-angabe-statisch--dynamisch-entschieden-e-005)

---

## E-006: Allgemeine Stufenbeschreibungen und Zuordnung der Referenzsituationen

- **Datum:** 2026-11-05
- **Status:** entschieden
- **Entscheidung:**
  - Die Stufen haben allgemeine Beschreibungen: 0 keine, 1 reduziert, 2 Alltag, 3 sportlich, 4 Spitze.
  - Als Soll bedeutet eine Stufe: Das Ziel verlangt diese Belastung. Als Ist bedeutet sie: Der Klient bewältigt diese Belastung derzeit kontrolliert und verträglich.
  - Es gibt nur ganze Stufen. Unsicherheit wird über die Angabe „Sicherheit der Einschätzung“ ausgedrückt.
  - Es wird nicht gerechnet. Lücken werden als „Ist liegt x Stufen unter Soll“ angezeigt, ohne Summen oder Durchschnitte.
  - Referenzsituationen gehören zu einem Anforderungsbereich in einer Körperregion, zum Beispiel „Exzentrische Belastung, Knie“.
  - Jede Referenzsituation hat eine Angabe zur Beleglage.
  - Wird eine Referenzsituation geändert, bleibt gespeichert, gegen welche Fassung frühere Bewertungen vergeben wurden.
- **Begründung:** Die allgemeinen Beschreibungen machen die Skala sofort nutzbar, auch ohne Referenzsituationen. Die Zuordnung zur Körperregion ist nötig, weil derselbe Anforderungsbereich, etwa exzentrische Belastung, an Knie und Schulter völlig unterschiedlich aussieht.
- **Einordnung:** Die Abstufung von Alltag zu Sport ist eine Arbeitshypothese und kein geprüftes Messinstrument. Sie wird in der Anwendung überprüft, besonders bei den propriozeptiven Bereichen.
- **Nicht Teil der Entscheidung:** Das Kniebeispiel (Treppe mit Geländer bis Landung aus einem Sprung) dient nur zur Veranschaulichung.
- **Details:** [02-bewertungsmodell.md, Abschnitte 2 und 3](02-bewertungsmodell.md)

---

## E-007: Listen A und B vollständig als Anforderungsbereiche übernehmen

- **Datum:** 2026-11-05
- **Status:** entschieden
- **Entscheidung:** Die Listen A (14 neurologische und propriozeptive Bereiche) und B (16 mechanische und strukturelle Bereiche) aus dem Projektauftrag werden vollständig in den Katalog übernommen. Bei jeder Anforderung werden nur die relevanten Bereiche eingeschaltet.
- **Begründung:** Nichts geht verloren, und die Auswahl trifft der Trainer bei jeder Anforderung selbst. Die Bereiche sind Inhalte im Fachwissen und lassen sich jederzeit ausblenden oder umbenennen.
- **Nicht gewählt:** mit einer kleinen Kernauswahl von 8 bis 10 Bereichen zu starten.
- **Details:** [03-anforderungsbereiche.md](03-anforderungsbereiche.md)

---

## E-008: Überlappende Anforderungsbereiche in Gruppen mit Unterbereichen ordnen

- **Datum:** 2026-11-06
- **Status:** entschieden
- **Entscheidung:**
  - Es gibt vier Gruppen: Propriozeption (A01–A03), Sensorik und Gleichgewicht (A04–A06, A13, A14), Antizipation (A09, A10) und Belastungsform (B07–B10).
  - Alle übrigen Bereiche sind Einzelbereiche.
  - Bewertet wird die Gruppe, ein Unterbereich oder beides. Die Gruppe „Belastungsform“ wird nur über ihre Unterbereiche bewertet.
  - Gruppenbewertungen werden nie aus den Unterbereichen errechnet.
  - Lücken werden nur angezeigt, wenn Soll und Ist auf derselben Ebene bewertet sind.
- **Begründung:**
  - Alle Bereiche bleiben erhalten.
  - Doppelte Bewertungen werden vermieden.
  - Die Auswahl auf dem Handy wird kürzer.
  - Feinere Bewertungen sind nur dort nötig, wo sie für den Klienten wichtig sind.
- **Nicht gewählt:**
  - alle Bereiche ungeordnet nebeneinander zu lassen
  - überlappende Bereiche zusammenzulegen
- **Details:** [03-anforderungsbereiche.md, Abschnitt 3](03-anforderungsbereiche.md#3-gruppen-mit-unterbereichen-entschieden-e-008)

---

## E-009: Liste C bei Belastungssituationen bewerten

- **Datum:** 2026-11-06
- **Status:** entschieden
- **Entscheidung:** Die Merkmale aus Liste C (C01–C08, Belastbarkeit und Sicherheit) werden bei Teilaufgaben des Ziels und bei Übungsvarianten bewertet, nicht bei den einzelnen Anforderungen.
- **Begründung:** Fragen wie „Wie leicht kann man abbrechen?“ oder „Was passiert bei Kontrollverlust?“ beschreiben eine konkrete Situation und keine Anforderung. Bewertet man sie bei Übungen und bei Teilaufgaben des Ziels, wird Graded Exposure als Weg sichtbar: von gut kontrollierbaren Übungen hin zu kaum kontrollierbaren Situationen des Ziels.
- **Nicht gewählt:** Liste C wie A und B bei jeder Anforderung zu bewerten.
- **Details:** [03-anforderungsbereiche.md, Abschnitt 4](03-anforderungsbereiche.md#4-liste-c-merkmale-von-belastungssituationen-entschieden-e-009)

---

## Offen

| Thema | Wo beschrieben | Stand |
|---|---|---|
| Konzeptentwurf Phase 1 | [01-konzept.md](01-konzept.md) | Entwurf, noch nicht abgestimmt |
| Kurzbeschreibung je Anforderungsbereich | [03-anforderungsbereiche.md](03-anforderungsbereiche.md) | noch nicht begonnen |
| Skala für die Merkmale aus Liste C | [03-anforderungsbereiche.md, Abschnitt 4](03-anforderungsbereiche.md#4-liste-c-merkmale-von-belastungssituationen-entschieden-e-009) | nächster Schritt |
| Aufteilung nach Gerät (Handy für schnelle Einträge, Laptop für Analyse) | [01-konzept.md, Abschnitt 6](01-konzept.md#6-technische-architektur) | Vorschlag, noch nicht abgestimmt |
| Technik (Programmiersprache, Bildschirme, Datenbank) | [01-konzept.md, Abschnitt 6](01-konzept.md#6-technische-architektur) | Vorschlag liegt vor (TypeScript, React, relationale Datenbank) |
| Anbieter für Server und Datenbank | – | offen, wird vor Beginn von Phase 2 geklärt |
