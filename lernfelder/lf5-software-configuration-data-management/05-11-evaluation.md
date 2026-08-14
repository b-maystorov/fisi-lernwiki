# 5.11 Softwareentwicklung evaluieren

In diesem Kapitel geht es darum, Softwareentwicklung nach der Umsetzung zu bewerten.

Evaluation bedeutet, ein Ergebnis systematisch zu prüfen und daraus Verbesserungen abzuleiten. Bei Software wird dabei betrachtet, ob die Anwendung die Anforderungen erfüllt, ob sie zuverlässig funktioniert, ob sie sicher ist, ob sie gut dokumentiert wurde und ob sie im Betrieb sinnvoll nutzbar ist.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Software nicht nur entwickelt, sondern auch betrieben, gewartet, überwacht und verbessert werden muss.

---

## Kurz erklärt

Softwareentwicklung evaluieren bedeutet, das Ergebnis und den Entwicklungsprozess kritisch zu prüfen.

Dabei geht es um Fragen wie:

- Wurde das Projektziel erreicht?
- Sind die Anforderungen erfüllt?
- Funktioniert die Software zuverlässig?
- Wurden Tests durchgeführt?
- Ist die Dokumentation verständlich?
- Ist die Software sicher genug?
- Sind Daten geschützt?
- Kann die Software betrieben und gewartet werden?
- Gab es Probleme im Projekt?
- Was kann beim nächsten Mal verbessert werden?

Evaluation ist also nicht nur Kritik.  
Sie hilft, aus einem Projekt zu lernen und die Qualität zukünftiger Projekte zu verbessern.

---

## Warum Evaluation wichtig ist

Ohne Evaluation weiß man oft nicht, ob ein Projekt wirklich erfolgreich war.

Eine Software kann auf den ersten Blick funktionieren, aber trotzdem Probleme haben:

- Anforderungen wurden nur teilweise erfüllt
- Benutzer kommen mit der Bedienung nicht gut klar
- Dokumentation fehlt
- Tests wurden nicht vollständig durchgeführt
- Sicherheit wurde zu wenig beachtet
- Installation ist zu kompliziert
- Betrieb ist nicht vorbereitet
- Fehler treten erst später auf
- Code ist schwer wartbar
- Datenstruktur ist unpraktisch

Evaluation hilft, solche Punkte sichtbar zu machen.

Dadurch kann man entscheiden, ob die Software verbessert, erweitert, anders betrieben oder neu geplant werden muss.

---

## Was wird evaluiert?

Bei der Evaluation kann man verschiedene Bereiche betrachten.

| Bereich                | Fragestellung                                     |
| ---------------------- | ------------------------------------------------- |
| Anforderungen          | Wurde umgesetzt, was gefordert war?               |
| Funktion               | Arbeitet die Software korrekt?                    |
| Qualität               | Ist die Software stabil, sicher und wartbar?      |
| Benutzerfreundlichkeit | Können Benutzer sinnvoll damit arbeiten?          |
| Sicherheit             | Sind Daten, Zugriffe und Systeme geschützt?       |
| Datenschutz            | Werden personenbezogene Daten korrekt behandelt?  |
| Tests                  | Wurden wichtige Testfälle durchgeführt?           |
| Dokumentation          | Ist Nutzung, Betrieb und Wartung nachvollziehbar? |
| Betrieb                | Kann die Software zuverlässig betrieben werden?   |
| Projektverlauf         | Was lief gut und was lief schlecht?               |
| Wartbarkeit            | Kann die Software später geändert werden?         |

Eine gute Evaluation betrachtet nicht nur den Code, sondern die gesamte Lösung.

---

## Evaluation des Projektergebnisses

Zuerst wird geprüft, ob das Projektergebnis zum Ziel passt.

Wichtige Fragen:

- Was war das ursprüngliche Ziel?
- Wurde dieses Ziel erreicht?
- Welche Funktionen wurden umgesetzt?
- Welche Funktionen fehlen?
- Welche Anforderungen wurden erfüllt?
- Welche Anforderungen wurden nicht erfüllt?
- Gibt es offene Fehler?
- Gibt es bekannte Einschränkungen?
- Ist das Ergebnis nutzbar?
- Wurde das Ergebnis dokumentiert?

Eine ehrliche Bewertung ist wichtig.

Es ist besser, offene Punkte klar zu nennen, als ein Projekt besser darzustellen, als es wirklich ist.

---

## Evaluation der Anforderungen

Anforderungen sind die Grundlage für die Bewertung.

Wenn Anforderungen vorher sauber dokumentiert wurden, kann später geprüft werden, ob sie erfüllt sind.

Beispiel:

| Anforderung                     | erfüllt   | Bemerkung                                            |
| ------------------------------- | --------- | ---------------------------------------------------- |
| Benutzer kann Ticket erstellen  | ja        | funktioniert im Test                                 |
| Ticket erhält eindeutige Nummer | ja        | automatisch generiert                                |
| Benutzer kann Datei anhängen    | nein      | für spätere Version geplant                          |
| Admin kann Benutzer verwalten   | teilweise | Benutzer können angelegt, aber nicht gelöscht werden |
| Anwendung ist dokumentiert      | ja        | README vorhanden                                     |

Diese Bewertung zeigt deutlich, was erreicht wurde und was noch offen ist.

---

## Muss-, Soll- und Kann-Anforderungen prüfen

Bei der Evaluation ist die Priorität der Anforderungen wichtig.

| Kategorie | Bedeutung bei Evaluation                                            |
| --------- | ------------------------------------------------------------------- |
| Muss      | muss erfüllt sein, sonst ist das Ziel meist nicht erreicht          |
| Soll      | sollte erfüllt sein, kann bei Zeitproblemen begründet offen bleiben |
| Kann      | optional, gut für spätere Erweiterungen                             |

Wenn eine Muss-Anforderung fehlt, ist das deutlich kritischer als eine fehlende Kann-Anforderung.

Beispiel:

Bei einer Inventarverwaltung ist „Gerät speichern“ eine Muss-Anforderung.  
Ein Statistik-Dashboard ist vielleicht nur eine Kann-Anforderung.

---

## Funktionale Bewertung

Die funktionale Bewertung prüft, ob die Software fachlich das Richtige tut.

Wichtige Fragen:

- Funktionieren die Hauptfunktionen?
- Werden Daten korrekt gespeichert?
- Werden Daten korrekt angezeigt?
- Werden Eingaben geprüft?
- Funktionieren Such- und Filterfunktionen?
- Werden Fehler sinnvoll behandelt?
- Funktionieren Benutzerrollen?
- Funktionieren Schnittstellen?
- Werden Ergebnisse korrekt berechnet?
- Sind alle wichtigen Abläufe nutzbar?

Eine Software ist funktional gut, wenn sie die vereinbarten Aufgaben zuverlässig erfüllt.

---

## Nicht-funktionale Bewertung

Nicht-funktionale Anforderungen beschreiben Qualitätsmerkmale.

Dazu gehören:

| Merkmal        | Fragestellung                               |
| -------------- | ------------------------------------------- |
| Leistung       | Reagiert die Software schnell genug?        |
| Stabilität     | Läuft die Software zuverlässig?             |
| Sicherheit     | Sind Daten und Zugriffe geschützt?          |
| Bedienbarkeit  | Ist die Nutzung verständlich?               |
| Wartbarkeit    | Kann die Software später geändert werden?   |
| Kompatibilität | Läuft die Software in der Zielumgebung?     |
| Skalierbarkeit | Kann die Software wachsen?                  |
| Dokumentation  | Ist die Lösung nachvollziehbar beschrieben? |

Eine Software kann funktional richtig sein, aber trotzdem schlecht bewertet werden, wenn sie langsam, unsicher oder schwer wartbar ist.

---

## Bewertung der Benutzerfreundlichkeit

Benutzerfreundlichkeit beschreibt, wie gut Anwender mit der Software arbeiten können.

Wichtige Fragen:

- Ist die Bedienung verständlich?
- Sind Eingabefelder klar beschriftet?
- Sind Fehlermeldungen hilfreich?
- Sind wichtige Funktionen leicht erreichbar?
- Ist die Ausgabe verständlich?
- Müssen Benutzer unnötig viele Schritte machen?
- Können typische Aufgaben schnell erledigt werden?
- Gibt es eine Anleitung?
- Gibt es unnötige Komplexität?

Eine technische Lösung ist nur dann wirklich gut, wenn Benutzer damit sinnvoll arbeiten können.

---

## Bewertung der Sicherheit

Sicherheit muss bei der Evaluation ausdrücklich betrachtet werden.

Wichtige Fragen:

- Gibt es eine Anmeldung?
- Sind Rollen und Rechte sinnvoll umgesetzt?
- Haben Benutzer nur notwendige Rechte?
- Werden Passwörter sicher behandelt?
- Werden sensible Daten geschützt?
- Werden Daten verschlüsselt übertragen?
- Werden Eingaben validiert?
- Werden Fehler sicher behandelt?
- Gibt es Logs?
- Gibt es Backups?
- Sind geheime Daten aus dem Repository entfernt?
- Gibt es bekannte Sicherheitsrisiken?

Sicherheit darf nicht nur als Zusatz betrachtet werden.

Gerade wenn personenbezogene oder geschäftskritische Daten verarbeitet werden, ist sie ein zentraler Qualitätsfaktor.

---

## Bewertung des Datenschutzes

Wenn personenbezogene Daten verarbeitet werden, muss Datenschutz geprüft werden.

Wichtige Fragen:

- Welche personenbezogenen Daten werden gespeichert?
- Ist klar, warum diese Daten benötigt werden?
- Haben nur berechtigte Personen Zugriff?
- Werden Daten nur so lange gespeichert wie nötig?
- Gibt es Löschmöglichkeiten?
- Werden echte Daten in Tests vermieden?
- Sind Screenshots anonymisiert?
- Werden personenbezogene Daten in Logs vermieden?
- Werden Daten sicher übertragen und gespeichert?
- Gibt es Dokumentation zur Datenverarbeitung?

Für Lernprojekte und öffentliche Repositories sollten keine echten personenbezogenen Daten verwendet werden.

---

## Bewertung der Tests

Tests zeigen, ob die Software geprüft wurde.

Wichtige Fragen:

- Welche Testfälle wurden durchgeführt?
- Wurden Muss-Anforderungen getestet?
- Wurden Fehlerfälle getestet?
- Wurden ungültige Eingaben getestet?
- Wurden Benutzerrechte getestet?
- Wurden Schnittstellen getestet?
- Wurde nach Änderungen erneut getestet?
- Gibt es ein Testprotokoll?
- Welche Tests sind fehlgeschlagen?
- Welche Fehler sind noch offen?

Tests sollten nicht nur den perfekten Normalfall prüfen.

Eine gute Evaluation betrachtet auch, ob mit Fehlern und Grenzfällen sinnvoll umgegangen wurde.

---

## Bewertung der Dokumentation

Dokumentation ist ein wichtiger Teil der Softwarequalität.

Wichtige Fragen:

- Gibt es eine README?
- Ist das Ziel des Projekts erklärt?
- Sind Installation und Start beschrieben?
- Sind Voraussetzungen genannt?
- Ist die Projektstruktur erklärt?
- Sind wichtige Funktionen beschrieben?
- Sind Konfigurationen dokumentiert?
- Sind Tests dokumentiert?
- Sind bekannte Fehler oder Grenzen genannt?
- Gibt es Hinweise zum Betrieb?
- Sind sensible Daten entfernt?

Eine Software ohne Dokumentation ist schwer zu nutzen, zu betreiben und weiterzuentwickeln.

---

## Bewertung der Wartbarkeit

Wartbarkeit beschreibt, wie gut eine Software später geändert oder erweitert werden kann.

Wichtige Fragen:

- Ist der Code verständlich?
- Sind Dateien sinnvoll strukturiert?
- Haben Variablen und Funktionen klare Namen?
- Gibt es unnötige Wiederholungen?
- Sind Funktionen nicht zu groß?
- Gibt es Tests?
- Gibt es Dokumentation?
- Sind Abhängigkeiten dokumentiert?
- Ist die Konfiguration vom Code getrennt?
- Werden Änderungen mit Git nachvollziehbar gespeichert?

Wartbare Software spart später viel Zeit.

Unwartbare Software funktioniert vielleicht heute, wird aber bei Änderungen schnell problematisch.

---

## Bewertung des Betriebs

Für FISI ist besonders wichtig, ob Software zuverlässig betrieben werden kann.

Wichtige Fragen:

- Wo läuft die Software?
- Wie wird sie installiert?
- Wie wird sie gestartet und gestoppt?
- Gibt es einen Dienst oder Container?
- Welche Ports werden genutzt?
- Wo liegen Logs?
- Wie werden Fehler geprüft?
- Wie werden Backups erstellt?
- Wie wird ein Restore durchgeführt?
- Wie werden Updates eingespielt?
- Wer ist verantwortlich?
- Gibt es Monitoring?
- Gibt es einen Rückfallplan?

Eine Software ist erst dann wirklich einsatzbereit, wenn auch der Betrieb geklärt ist.

---

## Bewertung der Performance

Performance beschreibt, wie schnell und ressourcenschonend eine Software arbeitet.

Wichtige Fragen:

- Startet die Software schnell genug?
- Reagiert die Anwendung ausreichend schnell?
- Dauern Datenbankabfragen zu lange?
- Wird zu viel Arbeitsspeicher genutzt?
- Wird die CPU stark belastet?
- Werden große Dateien effizient verarbeitet?
- Gibt es unnötige Wiederholungen?
- Werden Daten sinnvoll gefiltert?
- Gibt es Performanceprobleme bei mehreren Benutzern?

Für kleine Lernprojekte ist Performance oft nicht das wichtigste Thema.

Trotzdem sollte man erkennen, wenn eine Lösung unnötig langsam oder ineffizient ist.

---

## Bewertung der Zuverlässigkeit

Zuverlässigkeit bedeutet, dass Software stabil und vorhersehbar funktioniert.

Wichtige Fragen:

- Stürzt die Software häufig ab?
- Werden Fehler abgefangen?
- Gibt es verständliche Fehlermeldungen?
- Funktioniert die Software auch bei falschen Eingaben?
- Werden Daten korrekt gespeichert?
- Gibt es Probleme nach Neustart?
- Funktioniert die Software in der Zielumgebung?
- Gibt es Tests für wichtige Funktionen?

Zuverlässige Software reagiert kontrolliert, auch wenn nicht alles perfekt läuft.

---

## Bewertung der Projektstruktur

Eine klare Projektstruktur erleichtert Wartung und Verständnis.

Wichtige Fragen:

- Sind Dateien sinnvoll benannt?
- Ist der Startpunkt der Anwendung klar?
- Gibt es getrennte Ordner für Code, Tests und Dokumentation?
- Sind Beispieldaten getrennt von echten Daten?
- Ist `.gitignore` sinnvoll gepflegt?
- Sind unnötige Dateien entfernt?
- Gibt es klare README-Hinweise?
- Sind Konfigurationsdateien verständlich?

Eine gute Struktur zeigt, dass das Projekt nicht zufällig zusammengebaut wurde.

---

## Bewertung mit Kriterien

Eine Evaluation sollte möglichst nicht nur aus Gefühl bestehen.

Besser ist eine Bewertung anhand klarer Kriterien.

Beispiel:

| Kriterium              | Bewertung | Begründung                                         |
| ---------------------- | --------- | -------------------------------------------------- |
| Funktionalität         | gut       | Hauptfunktionen arbeiten korrekt                   |
| Tests                  | mittel    | Normalfälle getestet, Fehlerfälle fehlen teilweise |
| Dokumentation          | gut       | README und Installationshinweise vorhanden         |
| Sicherheit             | mittel    | keine echten Daten, aber Rollen noch einfach       |
| Wartbarkeit            | gut       | Code ist in Funktionen aufgeteilt                  |
| Betrieb                | mittel    | Start beschrieben, Monitoring fehlt                |
| Benutzerfreundlichkeit | gut       | Konsolenausgabe ist verständlich                   |

So wird die Bewertung nachvollziehbar.

---

## Bewertungsskala

Man kann einfache Bewertungsskalen nutzen.

Beispiel:

| Bewertung   | Bedeutung                                         |
| ----------- | ------------------------------------------------- |
| sehr gut    | erfüllt Anforderungen vollständig und sauber      |
| gut         | erfüllt Anforderungen mit kleinen offenen Punkten |
| ausreichend | Kernfunktion vorhanden, aber Verbesserungen nötig |
| mangelhaft  | wichtige Anforderungen fehlen                     |
| kritisch    | nicht sinnvoll nutzbar oder unsicher              |

Wichtig ist, die Bewertung zu begründen.

Eine Note oder Bewertung ohne Begründung ist wenig hilfreich.

---

## Soll-Ist-Vergleich

Ein Soll-Ist-Vergleich zeigt, was geplant war und was tatsächlich umgesetzt wurde.

| Soll                         | Ist                 | Bewertung          |
| ---------------------------- | ------------------- | ------------------ |
| CSV-Datei einlesen           | umgesetzt           | erfüllt            |
| Fehlerhafte Datei erkennen   | umgesetzt           | erfüllt            |
| Ergebnis als Datei speichern | nicht umgesetzt     | offen              |
| README schreiben             | umgesetzt           | erfüllt            |
| automatische Tests           | teilweise umgesetzt | Verbesserung nötig |

Der Soll-Ist-Vergleich ist eine einfache und sehr praktische Methode zur Evaluation.

---

## Lessons Learned

Lessons Learned bedeutet, aus einem Projekt zu lernen.

Dabei wird festgehalten:

- Was lief gut?
- Was lief schlecht?
- Was war schwieriger als erwartet?
- Was war einfacher als erwartet?
- Welche Fehler wurden gemacht?
- Welche Werkzeuge haben geholfen?
- Was sollte beim nächsten Projekt anders gemacht werden?
- Welche Themen müssen noch gelernt werden?

Lessons Learned sind besonders wertvoll für Lernprojekte und Ausbildung.

Sie zeigen, dass man nicht nur ein Ergebnis erstellt, sondern auch den eigenen Lernprozess reflektiert.

---

## Retrospektive

Eine Retrospektive ist eine strukturierte Rückschau auf die Zusammenarbeit und den Projektverlauf.

Typische Fragen:

- Was hat gut funktioniert?
- Was hat uns aufgehalten?
- Was sollten wir beibehalten?
- Was sollten wir verbessern?
- Welche Probleme kamen mehrfach vor?
- Welche konkrete Maßnahme nehmen wir uns vor?

In Teams ist eine Retrospektive besonders hilfreich.

Aber auch allein kann man am Ende eines Projekts kurz reflektieren.

---

## Feedback einholen

Feedback von anderen Personen ist wichtig.

Mögliche Feedbackquellen:

- Benutzer
- Mitschüler
- Ausbilder
- Kollegen
- Administratoren
- Tester
- Support
- Projektleitung

Feedback kann zeigen, was man selbst übersieht.

Ein Entwickler schaut oft auf Code und Technik.  
Ein Benutzer achtet eher auf Bedienung und Verständlichkeit.  
Ein Administrator achtet auf Betrieb, Logs, Sicherheit und Wartbarkeit.

---

## Verbesserungsmaßnahmen ableiten

Evaluation ist nur nützlich, wenn daraus Verbesserungen entstehen.

Beispiele:

| Feststellung                             | Verbesserungsmaßnahme                |
| ---------------------------------------- | ------------------------------------ |
| README ist unvollständig                 | Installationsschritte ergänzen       |
| Fehlerfälle wurden nicht getestet        | Negativtests hinzufügen              |
| Code ist zu groß in einer Datei          | Funktionen oder Module aufteilen     |
| Passwörter stehen in Konfiguration       | Umgebungsvariablen nutzen            |
| keine Backups geplant                    | Backup- und Restore-Konzept ergänzen |
| Benutzer verstehen Fehlermeldungen nicht | Fehlermeldungen klarer formulieren   |
| Datenbankstruktur ist unübersichtlich    | ER-Modell und Tabellen dokumentieren |

Eine gute Evaluation endet also nicht bei „gut“ oder „schlecht“, sondern mit konkreten nächsten Schritten.

---

## Offene Punkte dokumentieren

Nicht jedes Projekt ist nach der ersten Version komplett fertig.

Offene Punkte sollten ehrlich dokumentiert werden.

Beispiele:

- automatische Tests fehlen noch
- Benutzerverwaltung ist noch einfach
- Exportfunktion ist geplant
- Datenbankstruktur kann verbessert werden
- Dockerisierung ist noch offen
- README braucht mehr Beispiele
- Fehlerbehandlung ist noch nicht vollständig
- Sicherheitsprüfung muss erweitert werden

Offene Punkte sind nicht automatisch schlecht.

Sie zeigen, was in einer späteren Version verbessert werden kann.

---

## Evaluation bei kleinen Lernprojekten

Auch kleine Lernprojekte können evaluiert werden.

Beispiel Python-Skript:

- Funktioniert das Skript?
- Sind Eingaben geprüft?
- Gibt es verständliche Ausgaben?
- Ist der Code lesbar?
- Gibt es Funktionen statt nur langen Code?
- Gibt es eine README?
- Sind Testdaten künstlich?
- Gibt es bekannte Grenzen?
- Wurde Git genutzt?
- Gibt es sinnvolle Commit-Nachrichten?

Gerade für Portfolio-Projekte ist eine kurze Evaluation hilfreich, weil sie zeigt, dass man bewusst gearbeitet hat.

---

## Evaluation bei Datenbankprojekten

Bei Datenbankprojekten werden zusätzlich Datenstruktur und Datenqualität betrachtet.

Wichtige Fragen:

- Sind Tabellen sinnvoll aufgebaut?
- Gibt es Primärschlüssel?
- Gibt es Fremdschlüssel?
- Werden Pflichtfelder geprüft?
- Gibt es Constraints?
- Werden doppelte Daten vermieden?
- Sind Beziehungen nachvollziehbar?
- Funktionieren SQL-Abfragen?
- Gibt es Testdaten?
- Gibt es Backup-Überlegungen?
- Ist das Datenmodell dokumentiert?

Eine Datenbank sollte nicht nur irgendwie Daten speichern.

Sie sollte Daten sinnvoll, konsistent und nachvollziehbar verwalten.

---

## Evaluation bei Docker- oder Serverprojekten

Bei Projekten mit Docker oder Serverbetrieb sind andere Punkte wichtig.

Wichtige Fragen:

- Startet der Container zuverlässig?
- Sind Ports dokumentiert?
- Sind Volumes korrekt genutzt?
- Sind Umgebungsvariablen beschrieben?
- Gibt es Logs?
- Gibt es ein Backup für persistente Daten?
- Ist klar, wie man Container stoppt und startet?
- Sind Images und Versionen nachvollziehbar?
- Gibt es Sicherheitsrisiken?
- Ist die Dokumentation verständlich?

Für FISI ist dieser Bereich besonders praxisnah, weil Software oft in Infrastruktur eingebunden wird.

---

## Abnahme und Evaluation

Abnahme und Evaluation hängen zusammen, sind aber nicht identisch.

| Begriff    | Bedeutung                                                    |
| ---------- | ------------------------------------------------------------ |
| Abnahme    | Prüfen, ob das vereinbarte Ergebnis akzeptiert wird          |
| Evaluation | Bewertung von Ergebnis, Qualität, Prozess und Verbesserungen |

Eine Abnahme kann sagen:

> Das Projekt erfüllt die Mindestanforderungen.

Eine Evaluation kann zusätzlich sagen:

> Das Projekt funktioniert, aber Tests, Dokumentation und Fehlerbehandlung sollten verbessert werden.

---

## Evaluation dokumentieren

Eine Evaluation sollte schriftlich festgehalten werden.

Mögliche Struktur:

```md
# Evaluation

## Ziel

Was sollte erreicht werden?

## Ergebnis

Was wurde umgesetzt?

## Soll-Ist-Vergleich

Welche Anforderungen wurden erfüllt?

## Tests

Was wurde geprüft?

## Qualität

Wie wird die Lösung bewertet?

## Probleme

Welche Schwierigkeiten gab es?

## Verbesserungen

Was sollte später verbessert werden?

## Fazit

Kurze Gesamtbewertung.
```

Diese Struktur ist einfach und für viele Lern- und Praxisprojekte geeignet.

---

## Qualitätskriterien für Software

Softwarequalität kann anhand verschiedener Kriterien bewertet werden.

| Kriterium       | Bedeutung                                |
| --------------- | ---------------------------------------- |
| Funktionalität  | Software erfüllt ihre Aufgaben           |
| Zuverlässigkeit | Software läuft stabil                    |
| Benutzbarkeit   | Software ist verständlich nutzbar        |
| Effizienz       | Software nutzt Ressourcen sinnvoll       |
| Wartbarkeit     | Software kann geändert werden            |
| Übertragbarkeit | Software kann in anderer Umgebung laufen |
| Sicherheit      | Daten und Zugriffe sind geschützt        |
| Dokumentation   | Nutzung und Betrieb sind nachvollziehbar |

Nicht jedes Projekt muss in jedem Bereich perfekt sein.

Aber wichtige Schwächen sollten erkannt und dokumentiert werden.

---

## Erfolgskriterien

Erfolgskriterien beschreiben, woran der Projekterfolg gemessen wird.

Beispiele:

- alle Muss-Anforderungen erfüllt
- keine kritischen Fehler offen
- README vollständig
- Installation nachvollziehbar
- Tests durchgeführt
- Benutzer kann Hauptaufgabe erledigen
- keine sensiblen Daten im Repository
- Anwendung startet zuverlässig
- Daten werden korrekt gespeichert
- Dokumentation ist aktuell

Erfolgskriterien sollten möglichst früh festgelegt werden.

Dann ist die Evaluation später einfacher.

---

## Typische Fragen für eine Evaluation

Eine einfache Evaluation kann mit diesen Fragen starten:

- Was war das Ziel?
- Was wurde umgesetzt?
- Was funktioniert gut?
- Was funktioniert noch nicht?
- Welche Anforderungen wurden erfüllt?
- Welche Anforderungen fehlen?
- Welche Fehler wurden gefunden?
- Wie wurde getestet?
- Wie ist die Dokumentation?
- Wie sicher ist die Lösung?
- Wie gut kann die Software betrieben werden?
- Was würde ich beim nächsten Mal anders machen?
- Was ist der nächste sinnvolle Schritt?

Diese Fragen helfen, eine ehrliche und nützliche Bewertung zu schreiben.

---

## Praxisbeispiele

### Beispiel 1: Python-Logchecker

Ein Python-Skript durchsucht Logdateien nach Fehlermeldungen. Die Evaluation zeigt, dass die Kernfunktion funktioniert. Offen bleibt eine bessere Fehlerbehandlung, wenn die Logdatei nicht existiert. Als Verbesserung wird geplant, `try` und `except` einzubauen und die README zu erweitern.

### Beispiel 2: Inventardatenbank

Eine kleine Inventardatenbank speichert Geräte, Benutzer und Standorte. Die Evaluation zeigt, dass die Tabellenstruktur grundsätzlich passt. Verbesserungspotenzial gibt es bei Fremdschlüsseln, Testdaten und einer besseren Dokumentation der Beziehungen.

### Beispiel 3: Docker-Testumgebung

Eine Datenbank läuft in einem Docker-Container. Die Evaluation zeigt, dass der Container startet und erreichbar ist. Offen bleibt ein klares Backup-Konzept für das Volume und eine bessere Beschreibung der Umgebungsvariablen.

---

## Typische Fehler

| Fehler                          | Problem                                         |
| ------------------------------- | ----------------------------------------------- |
| Evaluation weglassen            | man lernt wenig aus dem Projekt                 |
| nur sagen „alles gut“           | Schwächen und Verbesserungen bleiben unsichtbar |
| Anforderungen nicht vergleichen | Zielerreichung ist unklar                       |
| Tests nicht bewerten            | Qualität bleibt unsicher                        |
| Dokumentation ignorieren        | Betrieb und Wartung werden schwierig            |
| Sicherheit nicht prüfen         | Risiken bleiben bestehen                        |
| Benutzerfeedback nicht einholen | Alltagstauglichkeit bleibt unklar               |
| offene Punkte verschweigen      | falscher Eindruck vom Projektstand entsteht     |
| keine Verbesserungen ableiten   | Evaluation hat keinen praktischen Nutzen        |
| nur Fehler suchen               | positive Ergebnisse werden nicht erkannt        |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Evaluation wichtig, weil Systeme und Software im Betrieb zuverlässig funktionieren müssen.

In der Praxis bedeutet das:

- Anforderungen mit Ergebnis vergleichen
- Tests und Fehlermeldungen bewerten
- Dokumentation prüfen
- Betrieb und Wartung betrachten
- Sicherheit und Datenschutz einordnen
- Backup und Restore mitdenken
- Benutzerfeedback berücksichtigen
- offene Punkte dokumentieren
- Verbesserungsmaßnahmen ableiten
- aus Projekten lernen

Ein guter FISI beendet ein Projekt nicht einfach mit „läuft“, sondern prüft, ob die Lösung sicher, dokumentiert, wartbar und im Betrieb sinnvoll nutzbar ist.

---

## Kurze Zusammenfassung

Softwareentwicklung evaluieren bedeutet, Ergebnis, Qualität, Tests, Dokumentation, Sicherheit, Betrieb und Projektverlauf systematisch zu bewerten.

Wichtige Methoden sind Soll-Ist-Vergleich, Anforderungsprüfung, Testauswertung, Feedback, Lessons Learned und Ableitung konkreter Verbesserungen.

Evaluation hilft, Softwareprojekte ehrlicher zu bewerten und zukünftige Projekte besser zu planen.

Für FISI ist dieses Kapitel wichtig, weil Software im Betrieb nicht nur funktionieren, sondern auch sicher, wartbar, dokumentiert und zuverlässig betreibbar sein muss.
