# Phase 1: Produktkonzept und Architektur

> **Status: Entwurf, nicht abgestimmt.**
> Alles in diesem Dokument ist ein Vorschlag. Was davon gilt, steht erst fest, wenn es im [Entscheidungsprotokoll](entscheidungen.md) als Entscheidung eingetragen ist.
>
> Erstellt: 2026-11-01

Fachliche Aussagen sind gekennzeichnet:

- **[belegt]**: wissenschaftlich gut abgesichert
- **[plausibel]**: begründete Annahme, aber nicht direkt belegt
- **[Arbeitshypothese]**: persönliche Annahme aus der Praxis, die sich noch bewähren muss

---

## 1. Produktkonzept

**In einem Satz:** Das Tool unterstützt die fachliche Entscheidungsfindung. Es ist kein Programm, das Trainingspläne erzeugt. Es zeigt zwei Dinge nebeneinander: was das Ziel eines Klienten verlangt und was er aktuell kann. Beides wird getrennt nach Anforderungsbereich und Bewegungsebene dargestellt. Außerdem dokumentiert es, wie diese Lücke Schritt für Schritt durch Belastungssteigerung geschlossen wird.

### Grundidee: zwei getrennte Bereiche

- **Fachwissen** gilt für alle Klienten und wächst mit der Erfahrung. Dazu gehören Anforderungsbereiche, Bausteine wie „einbeinige exzentrische Kniekontrolle“, Vorlagen für typische Ziele, Übungen und Progressionswege.
- **Klientenakte** wird pro Klient geführt. Sie enthält Ziel, Ausgangspunkt, Beobachtungen, Hypothesen, Interventionen, Reaktionen und Entscheidungen.

Wird Fachwissen bei einem Klienten verwendet, wird es **kopiert**, und angepasst wird nur die Kopie. So wird aus einer Vorlage nie ein Standardplan.

### Grundsätze als feste Regeln im Tool

| Grundsatz | Was das im Tool bedeutet |
|---|---|
| Kein Gesamt-Schwierigkeitswert | Jede Bewertung bleibt einzeln stehen. Das Tool bildet keine Summen und keine Durchschnitte. |
| Hypothesen sind keine Fakten | Eine Hypothese hat einen der Zustände „offen“, „gestützt“, „geschwächt“ oder „verworfen“. Den Zustand „bewiesen“ gibt es nicht. |
| Der Trainer entscheidet | Das Tool zeigt Möglichkeiten und Verläufe. Es setzt nie selbst etwas um. |
| Nur Relevantes erfassen | „Nicht bewertet“ ist ein eigener Eintrag und nicht dasselbe wie null. |
| Annahmen sind unterschiedlich gut abgesichert | Jeder Eintrag im Fachwissen bekommt eine Angabe, wie gut er belegt ist. |
| Keine Entscheidung aus einem Einzelwert | Das Monitoring zeigt Verläufe. Ein einzelner Schmerzwert löst keine Warnung aus. |

---

## 2. Module

| # | Modul | Aufgabe | Phase |
|---|---|---|---|
| 1 | Klienten | Profil mit festen Grundfeldern und eigenen Zusatzfeldern | MVP |
| 2 | Ziele und Zerlegung | Hauptziel mit Rahmenbedingungen, Teilaufgaben und Anforderungen als Baum | MVP |
| 3 | Fachwissen | Anforderungsbereiche, Bewertungsskalen, Bausteine, Zielvorlagen, Beleglage | MVP (Grundlage) |
| 4 | Anforderungen und Lücken | Bewertung von Soll und Ist je Anforderungsbereich und Ebene, Lückenanzeige, Priorisierung | MVP |
| 5 | Ausgangspunkt und Tests | Beobachtungen, Tests, Angaben des Klienten, Trainingserfahrung | MVP, Re-Tests in Phase 3 |
| 6 | Klinisches Denken | Verknüpfte Kette von der Beobachtung bis zur Entscheidung | MVP |
| 7 | Interventionsplanung | Übung mit Belastungsangaben, trainierte Anforderung, Begründung | MVP (einfach) |
| 8 | Übungen und Progressionsmatrix | Übungsdatenbank, Varianten, Progressionswege als Netz | Phase 3 |
| 9 | Monitoring und Verlauf | Reaktionen zu vier Zeitpunkten, Verlaufsgrafiken | Phase 3 |
| 10 | Export und Sicherung | Vollständige Sicherungskopie, später Berichte als PDF | MVP (einfach) |
| 11 | KI-Unterstützung | Erzeugt nur Vorschläge, die der Trainer annimmt, ändert oder verwirft | Phase 4 |

Die Module bauen nur in eine Richtung aufeinander auf. Das Monitoring kennt zum Beispiel die Interventionen, die Interventionen brauchen das Monitoring aber nicht. Dadurch lässt sich ein Modul erweitern, ohne andere umzubauen.

---

## 3. Grundlegende Datenstruktur

**Kernidee:** In denselben Anforderungsbereichen werden drei Dinge bewertet:

- was das Ziel verlangt (Soll),
- was der Klient kann (Ist),
- was eine Übung fordert.

Dadurch werden Lücken sichtbar, und später lassen sich Übungen finden, die genau diese Lücke ansprechen. Ein Gesamtwert entsteht dabei nirgends.

```
FACHWISSEN (für alle Klienten)
  Anforderungsbereich (z. B. „Exzentrische Belastung“, „Gleichgewicht“) mit Bewertungsskala
  Baustein (z. B. „Einbeinige exzentrische Kniekontrolle“)
  Zielvorlage „Treppensteigen“ → Teilaufgaben → Bausteine
  Übung → Varianten → Progressionsweg („Variable X verändern → steigert Bereich Y“)

KLIENTENAKTE (pro Klient)
  Klient
   └─ Ziel (+ Rahmenbedingungen: Umfang, Tempo, Untergrund, Umgebung …)
       └─ Teilaufgabe (z. B. „Treppe absteigen“)
           └─ Anforderung (Kopie eines Bausteins, mit Priorität)
               ├─ Soll-Bewertungen
               ├─ Ist-Bewertungen (mit Datum und Herkunft)
               └─ Einträge aus der Denk-Kette
   └─ Intervention (Übungsvariante + Belastungsangaben → für welche Anforderungen)
       └─ Trainingseinheit → Reaktionen (während / direkt danach / nach Stunden / Folgetag)
```

### Der wichtigste Datensatz: eine einzelne Bewertung

| Angabe | Beispiel |
|---|---|
| Was wird bewertet | Anforderung „Treppe absteigen, einbeinige exzentrische Kontrolle“ |
| Anforderungsbereich | Exzentrische Belastung |
| Bewegungsebene *(optional)* | Frontal |
| Art der Kontrolle *(optional)* | mechanisch oder propriozeptiv |
| Wert | Stufe auf einer Skala (z. B. 0 bis 4) oder „nicht bewertet“ |
| Sicherheit der Einschätzung | gering / mittel / hoch |
| Herkunft | Beobachtung / Test / Trainingserfahrung / Angabe des Klienten |
| Datum, Notiz | … |

### Weitere Grundsätze

- **Die Anforderungsbereiche sind Inhalte, kein fester Programmcode.** Sie lassen sich ohne Programmierung ergänzen, umbenennen oder ausblenden.
- **Die Denk-Kette** besteht aus eigenen Eintragsarten: Beobachtung, Klientenfeedback, Hypothese, Manipulation, Reaktion, Intervention, Re-Test und Entscheidung. Die Einträge sind miteinander verknüpft. Eine Hypothese verweist zum Beispiel auf die Beobachtungen, aus denen sie entstanden ist, und eine Manipulation auf die Hypothese, die sie überprüfen soll.
- **Die Belastungsform** wird bei jeder Übungsvariante und Intervention festgehalten: passiv, assistiert, aktiv, konzentrisch, exzentrisch, isometrisch, reaktiv oder plyometrisch.
- **Bei Isometrie** wird zusätzlich gespeichert, wie die Position erreicht wurde: konzentrisch, exzentrisch oder passiv/assistiert. Daran ist bewusst **keine Sicherheitsregel** geknüpft (siehe [Fachliche Einordnung](#fachliche-einordnung)).

---

## 4. Arbeitsablauf vom Klientenprofil bis zur Progression

```
Klient anlegen → Ziel + Rahmen → Zerlegung → Anforderungsprofil → Ausgangspunkt → Lückenübersicht + Priorisierung
                                                                                         │
   ┌─────────────────────────────────────────────────────────────────────────────────────┘
   ▼
   Beobachtung → Hypothese → Manipulation → Reaktion → Intervention → Monitoring → Re-Test → Entscheidung
   ▲                                                                                         │
   └──────────────── beibehalten / anpassen / steigern / zurückgehen ─────────────────────────┘
```

1. **Klient anlegen.** Zu Beginn reichen ein Kürzel und das Ziel. Alles Weitere wird erst eingetragen, wenn es relevant wird.
2. **Ziel und Rahmenbedingungen festlegen.** „Joggen“ allein lässt sich kaum analysieren. Zwei Beispiele für Rahmenbedingungen:
   - „30 Minuten auf Waldboden, lockeres Tempo, dreimal pro Woche“
   - „10-km-Wettkampf auf Asphalt“

   Beide verlangen Unterschiedliches, denn Belastungsdauer, Zahl der Bodenkontakte und Unebenheit des Untergrunds verändern die mechanischen und propriozeptiven Anforderungen.
3. **Ziel zerlegen.** Der Baum aus Teilaufgaben und Anforderungen wird leer begonnen oder aus einer kopierten Vorlage aufgebaut.
4. **Anforderungsprofil (Soll) erstellen.** Pro Anforderung werden nur die relevanten Bereiche und Ebenen bewertet.
5. **Ausgangspunkt (Ist) erfassen.** Dazu zählen Ergebnisse aus Tests, Beobachtungen und Angaben des Klienten. Zu jedem Eintrag werden die Herkunft und die Sicherheit der Einschätzung festgehalten.
6. **Lücken anzeigen.** Soll und Ist stehen nebeneinander. Die Reihenfolge der Bearbeitung legt der Trainer selbst fest.
7. **Denk-Kette bis zur Entscheidung durchlaufen.** Bei einer Steigerung wählt der Trainer selbst, welche Variable verändert wird. Das Tool zeigt dafür, welche Variable welchen Anforderungsbereich beeinflusst.

---

## 5. Mechanische, neurologische und propriozeptive Anforderungen und die drei Bewegungsebenen

Jede Anforderung wird in drei Blöcken bewertet:

- **A: Neurologisch und propriozeptiv.** Dazu gehören zum Beispiel Propriozeption, Gelenkpositionswahrnehmung, Gleichgewicht, intersegmentale Koordination, Reaktionsfähigkeit, Antizipation, Automatisierung und Kontrolle unter veränderten sensorischen Bedingungen.
- **B: Mechanisch und strukturell.** Dazu gehören zum Beispiel Kraftentwicklung und Kraftaufnahme, Drehmomente, Kompression, Scherkräfte, Rotationsbelastung, Belastungsform, Geschwindigkeit, Bewegungsumfang, Dauer, Wiederholungszahl, externe Last und Belastung unter Ermüdung.
- **Ebenen-Tabelle:** Sie hat 3 Ebenen und für jede zwei Arten von Kontrolle (mechanisch, propriozeptiv). Ein zusätzliches Feld hält fest, welche Ebenen gleichzeitig gefordert sind, zum Beispiel sagittal und transversal bei einer Landung.

### Vorschlag zu C (Belastbarkeit und Sicherheit)

Die Fragen aus Bereich C, etwa „Wie leicht kann man abbrechen?“ oder „Was passiert bei Kontrollverlust?“, beschreiben keine Anforderung, sondern eine **Belastungssituation**.

C wird deshalb nicht bei den Anforderungen bewertet, sondern an zwei anderen Stellen:

- bei den **Teilaufgaben des Ziels**,
- bei den **Übungsvarianten**.

So wird Graded Exposure als Weg sichtbar: von gut kontrollierbaren Situationen wie einem Split Squat mit Handstütze zu kaum kontrollierbaren wie einem Zweikampf im Fußball.

### Beispiel für die Ebenen-Tabelle

Treppe absteigen, einbeinige exzentrische Kontrolle:

| Ebene | Mechanisch Soll | Mechanisch Ist | Propriozeptiv Soll | Propriozeptiv Ist |
|---|---|---|---|---|
| Sagittal | hoch | mittel | mittel | mittel |
| Frontal | mittel | **gering** | mittel | **gering** |
| Transversal | gering | gering | gering | nicht bewertet |

Lücken werden markiert, aber nicht zu einer Zahl verrechnet.

### Darstellung

- **Zielzerlegung:** als Baum
- **Anforderungen und Bereiche:** als farbige Matrix
- **Übungen, Anforderungen und Progressionen:** später als Netz, das sie miteinander verbindet

### Progression

Jeder Progressionsweg hält zwei Dinge fest:

- *welche Variable* verändert wird,
- *welche Anforderungsbereiche* dadurch steigen.

Damit kann das Tool zum Beispiel diese Frage beantworten: „Welche Variante des Front Foot Elevated Split Squat erhöht die mechanische Anforderung in der Frontalebene, ohne die Spitzenbelastung stark zu steigern?“ Eine feste Reihenfolge der Progressionen gibt es nicht.

---

## 6. Technische Architektur

Das Programm ist in Schichten aufgebaut:

```
[Bildschirme]       ein Bereich pro Modul
      ↓
[Fachlogik]         die Regeln, z. B. „eine Hypothese hat immer einen Status“
      ↓
[Datenzugriff]
      ↓
[Datenbank]         wo die Daten gespeichert sind
      ↑
[KI-Unterstützung]  (Phase 4) schreibt nur in einen Bereich für Vorschläge, nie direkt in die Klientenakte
```

Die Fachlogik ist von Bildschirmen und Datenbank getrennt. Deshalb kann der Speicherort später wechseln (eigenes Gerät oder Server), ohne dass die Logik neu geschrieben werden muss.

### Vorschlag für die Technik

| Baustein | Vorschlag | Vorteil | Nachteil |
|---|---|---|---|
| Programmiersprache | **TypeScript** | Eine Sprache für alle Teile. Fehler im Datenmodell fallen früh auf. | Etwas mehr Schreibaufwand als einfaches JavaScript |
| Bildschirme | **React** | Sehr verbreitet, viele fertige Bausteine für Tabellen, Matrizen und Grafiken | Entwickelt sich schnell, Updates brauchen Pflege |
| Datenbank | **Relationale Datenbank** (SQLite auf dem eigenen Gerät oder PostgreSQL auf einem Server) | Die Daten sind stark miteinander verknüpft, und diese Art Datenbank hält sie zuverlässig zusammen. | Änderungen an der Struktur brauchen kleine Umbau-Skripte. Dafür ist jede Änderung nachvollziehbar dokumentiert. |
| Grafiken | Bausteine für Bäume, Netze, farbige Matrizen und Verläufe | Bewährt | – |
| Tests | Automatische Prüfungen für Logik und Abläufe | Jede neue Funktion wird geprüft, bevor sie genutzt wird | – |
| KI (Phase 4) | Claude über eine eigene Schnittstelle | Strukturierte, begründete Vorschläge | Daten verlassen das Gerät. Deshalb werden nur Kürzel statt Namen übermittelt. |

### Offene Entscheidung: Wo werden die Daten gespeichert?

| | A: Auf dem eigenen Gerät | B: Web-App mit Server |
|---|---|---|
| Daten liegen | lokal beim Trainer | bei einem Anbieter in der EU |
| Datenschutz | einfach, nichts wird weitergegeben | Vertrag mit dem Anbieter, Anmeldung und Verschlüsselung nötig |
| Mehrere Geräte | nur über Abgleich oder Export | ja |
| Klienten tragen selbst ein | nein | möglich |
| Aufwand und Kosten | gering | höher (Server, Sicherheit) |

### Datenschutz

Gesundheitsdaten sind besonders geschützt (Art. 9 DSGVO). In beiden Varianten braucht das Tool deshalb:

- dokumentierte Einwilligung,
- Verschlüsselung,
- Sicherungskopien,
- die Möglichkeit, Daten zu löschen und herauszugeben,
- Kürzel statt Namen bei Auswertungen und KI-Anfragen.

Das ist keine Rechtsberatung. Die Architektur muss diese Anforderungen aber von Anfang an erfüllen können.

---

## 7. Entwicklungsfahrplan

**Schritt 0 (erledigt):** GitHub-Repository als dauerhafter Speicher für Code und Dokumentation.

### Phase 1 (aktuell)

- 1a: Dieses Konzept gemeinsam abstimmen.
- 1b: Klären, wie das Tool genutzt wird, und die Technik festlegen.
- 1c: Datenmodell im Detail ausarbeiten, also die erste Liste der Anforderungsbereiche und die Bewertungsskala.
- 1d: Einfache Skizzen der wichtigsten Bildschirme erstellen, bevor Code entsteht.

### Phase 2: MVP in kleinen, testbaren Schritten

1. Grundgerüst und Klientenprofil
2. Ziel mit Rahmenbedingungen und Zerlegungsbaum, Vorlagen zum Kopieren
3. Anforderungsbereiche und Soll-Bewertung
4. Ausgangspunkt, Lückenübersicht und Priorisierung. Ab diesem Schritt ist das Tool mit echten Fällen nutzbar, wenn Klienten unter Kürzeln geführt werden.
5. Dokumentation der Denk-Kette
6. Einfache Interventionsplanung und Sicherungskopie

### Phase 3

Die Module kommen in dieser Reihenfolge:

1. Übungsdatenbank
2. Progressionsmatrix
3. Monitoring zu den vier Zeitpunkten
4. Re-Tests und Verläufe
5. Vollständige Ansicht der Bewegungsebenen

### Phase 4

KI-Vorschläge werden Schritt für Schritt eingeführt, beginnend mit der Zielzerlegung.

### Vorgeschlagene Änderungen am ursprünglichen Phasenplan

- Die Bewegungsebenen stehen **schon im MVP im Datenmodell**, weil ein späterer Umbau aufwendig wäre. Nur die ausgebaute Ansicht kommt in Phase 3.
- **Sicherungskopien gibt es schon im MVP.** Sobald echte Klientendaten im Tool sind, müssen sie gesichert sein.

### Größte Risiken

- **Zu viel Eingabeaufwand:** Verlangt jede Anforderung 40 Bewertungen, wird das Tool im Alltag nicht genutzt. Gegenmittel sind: nur Relevantes bewerten, Vorlagen nutzen und eine schnelle Eingabe ermöglichen.
- **Scheingenauigkeit:** Stufen wie 0 bis 4 wirken genauer, als sie sind. Deshalb wird immer angezeigt, wie sicher die Einschätzung ist und woher sie stammt. Mit den Werten wird nicht gerechnet.
- **Vorlagen werden zu Standardplänen:** Vorlagen werden immer nur kopiert, und die Herkunft bleibt sichtbar.
- **Medizinprodukte-Recht:** Software, die individuelle Therapieempfehlungen gibt, kann in der EU als Medizinprodukt gelten. Für die eigene Nutzung als Werkzeug zum Dokumentieren und Nachdenken spielt das kaum eine Rolle. Vor einer Weitergabe oder einem Verkauf, besonders mit KI-Empfehlungen, sollte es geprüft werden.

---

## Fachliche Einordnung

### 1. „Graded Exposure“ ist in der Fachliteratur enger gefasst [belegt]

Der Begriff (Vlaeyen u. a.) meint die schrittweise Konfrontation mit *gefürchteten* Bewegungen, um die Angst davor abzubauen.

Die schrittweise Steigerung der Belastbarkeit von Gewebe und Leistung heißt eher progressive Belastungssteuerung. Das Konzept des Tools umfasst beides. Deshalb sollen pro Teilaufgabe zwei Dinge getrennt erfasst werden:

- die **Belastbarkeit**,
- das **Vertrauen in die Bewegung**.

Ein Klient kann mechanisch belastbar sein und trotzdem Angst vor einer Bewegung haben, und umgekehrt.

### 2. Isometrie: konzentrisch eingeleitet als besser kontrollierbar [Arbeitshypothese, der Mechanismus ist plausibel]

Exzentrisch lässt sich mehr Kraft aufbringen als konzentrisch. Wer eine Position exzentrisch erreicht, hält deshalb unter Umständen eine Last, die er konzentrisch nicht mehr bewegen könnte. Ein Abbruch bedeutet dann, der Last nachzugeben. Das spricht für die Arbeitshypothese, beweist sie aber nicht.

Zusätzlich sollten zwei Formen unterschieden werden:

- **Überwindende Isometrie:** gegen einen festen Widerstand drücken. Der Klient bestimmt die Kraft selbst und kann sofort loslassen.
- **Haltende Isometrie:** eine Last halten.

In Laborstudien (u. a. Hunter, Enoka) ermüdeten diese beiden Formen bei gleicher Kraft unterschiedlich schnell [belegt, unter Laborbedingungen].

Das Tool speichert deshalb zwei Angaben: wie die Position erreicht wurde und welche Form der Isometrie vorlag. So lassen sich mit der Zeit eigene Beobachtungen zur Arbeitshypothese sammeln.

### 3. Propriozeption lässt sich kaum direkt messen [plausibel]

Praxistests zur Wahrnehmung der Gelenkposition liefern oft wenig verlässliche Ergebnisse, die stark von der Testmethode abhängen. Wie sie mit der tatsächlichen Funktion zusammenhängen, ist unklar.

Im Tool beruht die propriozeptive Kontrolle deshalb meist auf Beobachtung, zusammen mit der Angabe, wie sicher die Einschätzung ist. Gezielte Veränderungen der Sinneseindrücke passen gut in den Schritt „Manipulation“, zum Beispiel:

- Augen schließen,
- instabile Unterlage,
- eine zweite Aufgabe gleichzeitig.

### 4. Kontrolle in jeder Ebene getrennt betrachten [plausibel]

Dass Training vor allem das verbessert, was geübt wird, ist allgemein gut belegt. Dass sich Kontrolle nicht automatisch von einer Ebene auf eine andere überträgt, ist plausibel, aber kaum direkt untersucht. Die getrennte Bewertung pro Ebene ist deshalb die vorsichtige Wahl.

Die Reihenfolge sagittal → frontal → transversal ist eine Faustregel aus der Praxis und keine feste Abfolge.

---

## Offene Fragen

1. **Nutzung:** Wer nutzt das Tool auf welchen Geräten? Arbeitet nur der Trainer damit, am Laptop und auf Tablet oder Handy während der Einheit? Oder sollen Klienten auch selbst etwas eintragen, etwa ihre Reaktion am Folgetag? Davon hängt ab, ob Speichervariante A (eigenes Gerät) oder B (Server mit Anmeldung) gewählt wird.
