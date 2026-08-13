# 5.3 Software in Projekten entwickeln

In diesem Kapitel geht es darum, wie Software innerhalb eines Projekts geplant, entwickelt und organisiert wird.

Softwareentwicklung ist meistens keine einzelne Aufgabe, sondern ein Projekt mit Ziel, Anforderungen, Zeitrahmen, Beteiligten, Werkzeugen, Aufgaben, Tests und Dokumentation. Auch kleine Programme oder Skripte sollten strukturiert entwickelt werden, damit sie verständlich, wartbar und zuverlässig bleiben.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil auch im IT-Betrieb häufig kleinere Softwarelösungen, Skripte, Automatisierungen oder Anpassungen entstehen.

---

## Kurz erklärt

Software in Projekten zu entwickeln bedeutet, nicht einfach direkt loszuprogrammieren, sondern geplant vorzugehen.

Dazu gehören:

- Ziel klären
- Anforderungen sammeln
- Aufgaben planen
- Rollen festlegen
- Werkzeuge auswählen
- Code schreiben
- Versionierung nutzen
- Tests durchführen
- Fehler beheben
- Dokumentation erstellen
- Ergebnis prüfen
- Software verbessern

Ein Softwareprojekt soll am Ende nicht nur funktionieren, sondern auch nachvollziehbar, wartbar und nutzbar sein.

---

## Was ist ein Softwareprojekt?

Ein Softwareprojekt ist ein zeitlich begrenztes Vorhaben, bei dem eine Softwarelösung erstellt, angepasst oder erweitert wird.

Beispiele:

- kleines Python-Skript zur Logauswertung
- Webanwendung für Supporttickets
- Datenbank für Inventarverwaltung
- Automatisierung für Backups
- Tool zur Auswertung von CSV-Dateien
- Anpassung einer bestehenden Anwendung
- Schnittstelle zwischen zwei Systemen
- internes Verwaltungsprogramm
- Konfigurationsgenerator
- Monitoring-Erweiterung

Nicht jedes Softwareprojekt ist groß. Auch kleine Tools sollten sauber geplant werden, wenn sie später genutzt, erweitert oder dokumentiert werden sollen.

---

## Warum Projektarbeit wichtig ist

Projektarbeit hilft, Softwareentwicklung geordnet durchzuführen.

Ohne Projektstruktur entstehen oft Probleme:

- Ziel ist unklar
- Anforderungen ändern sich unkontrolliert
- Aufgaben werden vergessen
- niemand weiß, wer verantwortlich ist
- Code ist schwer verständlich
- Tests fehlen
- Fehler fallen zu spät auf
- Dokumentation fehlt
- Zeitaufwand wird unterschätzt
- Software passt nicht zum Bedarf

Projektarbeit schafft Übersicht und macht Fortschritt messbar.

---

## Projektziel

Das Projektziel beschreibt, was am Ende erreicht werden soll.

Ein gutes Projektziel sollte klar und verständlich sein.

Beispiele:

| schlechtes Ziel               | besseres Ziel                                                               |
| ----------------------------- | --------------------------------------------------------------------------- |
| Wir bauen ein Tool            | Wir bauen ein Python-Tool, das Logdateien nach Fehlern durchsucht           |
| Daten sollen besser sein      | Inventardaten sollen zentral gespeichert und durchsucht werden können       |
| Support soll einfacher werden | Supporttickets sollen mit Status, Priorität und Bearbeiter verwaltet werden |

Ein klares Ziel hilft, Anforderungen, Aufgaben und Tests daraus abzuleiten.

---

## Projektauftrag

Ein Projektauftrag beschreibt die Grundlage eines Projekts.

Typische Inhalte:

- Projektname
- Ausgangssituation
- Ziel
- Auftraggeber
- Beteiligte
- Rahmenbedingungen
- grober Zeitplan
- erwartetes Ergebnis
- Einschränkungen
- Risiken
- Abnahmekriterien

Ein Projektauftrag muss nicht immer sehr lang sein. Aber er sollte so klar sein, dass alle Beteiligten verstehen, worum es geht.

---

## Anforderungen im Projekt

Anforderungen beschreiben, was die Software leisten soll.

Man unterscheidet:

| Art                             | Bedeutung                                                     |
| ------------------------------- | ------------------------------------------------------------- |
| funktionale Anforderungen       | was die Software tun soll                                     |
| nicht-funktionale Anforderungen | wie gut oder unter welchen Bedingungen sie funktionieren soll |

Beispiele für funktionale Anforderungen:

- Benutzer kann Daten eingeben
- Daten werden gespeichert
- Liste kann gefiltert werden
- Fehler werden angezeigt
- Bericht kann exportiert werden

Beispiele für nicht-funktionale Anforderungen:

- Software soll einfach bedienbar sein
- Daten müssen geschützt werden
- Anwendung soll schnell reagieren
- Lösung soll dokumentiert sein
- Software soll unter Linux laufen
- Code soll wartbar sein

Anforderungen sind wichtig, damit später geprüft werden kann, ob die Software das Ziel erfüllt.

---

## Beteiligte im Softwareprojekt

In Softwareprojekten gibt es verschiedene Beteiligte.

| Rolle                    | Aufgabe                                          |
| ------------------------ | ------------------------------------------------ |
| Auftraggeber             | beauftragt oder genehmigt das Projekt            |
| Benutzer                 | arbeitet später mit der Software                 |
| Entwickler               | schreibt oder ändert Code                        |
| Administrator            | stellt Umgebung und Betrieb sicher               |
| Tester                   | prüft Funktion und Fehler                        |
| Projektleitung           | koordiniert Aufgaben, Zeit und Kommunikation     |
| Datenschutz / Sicherheit | prüft rechtliche und sicherheitsrelevante Punkte |
| Support                  | hilft nach Einführung der Software               |

In kleinen Projekten übernimmt eine Person oft mehrere Rollen.

Wichtig ist, dass Zuständigkeiten klar sind.

---

## Projektplanung

Projektplanung bedeutet, das Vorgehen vor der Umsetzung zu strukturieren.

Wichtige Fragen:

- Was soll erreicht werden?
- Welche Anforderungen gibt es?
- Welche Aufgaben müssen erledigt werden?
- Wer übernimmt welche Aufgabe?
- Welche Werkzeuge werden genutzt?
- Welche Daten werden verarbeitet?
- Welche Risiken gibt es?
- Wie wird getestet?
- Wie wird dokumentiert?
- Wann ist das Projekt fertig?

Projektplanung verhindert nicht alle Probleme, aber sie hilft, Probleme früher zu erkennen.

---

## Arbeitspakete

Ein Arbeitspaket ist eine klar abgegrenzte Aufgabe innerhalb eines Projekts.

Beispiele:

- Anforderungen sammeln
- Datenmodell erstellen
- Benutzeroberfläche planen
- Datenbanktabelle erstellen
- Python-Funktion schreiben
- Eingabevalidierung einbauen
- Testdaten erstellen
- Fehlerbehandlung ergänzen
- README schreiben
- Anwendung testen

Arbeitspakete helfen, ein großes Projekt in kleinere, verständliche Aufgaben zu zerlegen.

---

## Meilensteine

Ein Meilenstein ist ein wichtiger Zwischenpunkt im Projekt.

Beispiele:

- Anforderungen sind fertig
- Datenmodell ist erstellt
- erste Programmversion läuft
- Datenbank ist angebunden
- Tests sind durchgeführt
- Dokumentation ist fertig
- Software ist abgenommen

Meilensteine helfen, Fortschritt zu kontrollieren.

Sie zeigen, ob ein Projekt noch im Plan liegt oder ob angepasst werden muss.

---

## Zeitplanung

Softwareprojekte brauchen eine realistische Zeitplanung.

Typische Projektphasen:

| Phase         | Inhalt                                |
| ------------- | ------------------------------------- |
| Analyse       | Problem und Anforderungen verstehen   |
| Planung       | Lösung, Daten und Aufgaben planen     |
| Umsetzung     | Code schreiben und konfigurieren      |
| Test          | Funktion und Fehler prüfen            |
| Dokumentation | Nutzung und Technik beschreiben       |
| Übergabe      | Ergebnis vorstellen und bereitstellen |
| Wartung       | Fehler beheben und verbessern         |

Gerade Anfänger unterschätzen oft Test, Fehlersuche und Dokumentation.

Diese Teile gehören aber zum Projekt dazu.

---

## Vorgehensmodelle

Ein Vorgehensmodell beschreibt, wie ein Softwareprojekt organisiert wird.

Wichtige Beispiele:

- Wasserfallmodell
- iteratives Vorgehen
- agiles Vorgehen
- Scrum
- Kanban

Nicht jedes Projekt braucht ein komplexes Modell.

Für kleine Projekte reicht oft ein einfaches, klares Vorgehen. Für größere Projekte braucht man mehr Struktur.

---

## Wasserfallmodell

Beim Wasserfallmodell laufen Projektphasen nacheinander ab.

Typische Reihenfolge:

1. Anforderungen
2. Planung
3. Umsetzung
4. Test
5. Einführung
6. Wartung

Vorteile:

- klare Struktur
- gut dokumentierbar
- gut bei stabilen Anforderungen
- einfache Planung

Nachteile:

- Änderungen sind später schwierig
- Fehler werden manchmal spät entdeckt
- Benutzerfeedback kommt oft spät

Das Wasserfallmodell passt eher, wenn Anforderungen früh klar und stabil sind.

---

## Iteratives Vorgehen

Beim iterativen Vorgehen wird die Software Schritt für Schritt verbessert.

Es entsteht nicht sofort die perfekte Endversion.

Stattdessen wird eine erste Version gebaut, getestet, verbessert und erweitert.

Vorteile:

- frühes Feedback
- Fehler werden schneller sichtbar
- Änderungen sind leichter möglich
- Benutzer sehen früh erste Ergebnisse

Beispiel:

Ein Inventartool startet mit Geräteerfassung. Danach kommen Suche, Bearbeitung, Export und Benutzerrechte dazu.

---

## Agiles Vorgehen

Agiles Vorgehen bedeutet, flexibel auf Änderungen zu reagieren und regelmäßig kleine Ergebnisse zu liefern.

Typische Merkmale:

- kurze Entwicklungsabschnitte
- regelmäßiges Feedback
- enge Zusammenarbeit
- Priorisierung von Aufgaben
- Anpassung an neue Erkenntnisse
- funktionierende Zwischenergebnisse

Agil bedeutet nicht, ohne Plan zu arbeiten.

Agil bedeutet, geplant flexibel zu bleiben.

---

## Scrum

Scrum ist ein bekanntes agiles Vorgehensmodell.

Wichtige Begriffe:

| Begriff          | Bedeutung                          |
| ---------------- | ---------------------------------- |
| Product Owner    | priorisiert Anforderungen          |
| Scrum Master     | unterstützt den Prozess            |
| Entwicklungsteam | setzt Aufgaben um                  |
| Product Backlog  | Liste aller Anforderungen          |
| Sprint           | kurzer Arbeitsabschnitt            |
| Sprint Review    | Ergebnis wird vorgestellt          |
| Retrospektive    | Team verbessert die Zusammenarbeit |

Scrum wird häufig in größeren Softwareteams genutzt.

Für kleine Lern- oder Praxisprojekte reicht oft eine vereinfachte Form mit Aufgabenliste und kurzen Arbeitsphasen.

---

## Kanban

Kanban ist eine Methode zur Visualisierung von Aufgaben.

Ein einfaches Kanban-Board hat Spalten wie:

| Spalte      | Bedeutung                      |
| ----------- | ------------------------------ |
| To Do       | Aufgabe ist noch offen         |
| In Progress | Aufgabe wird gerade bearbeitet |
| Review      | Aufgabe wird geprüft           |
| Done        | Aufgabe ist erledigt           |

Kanban hilft, den Überblick zu behalten.

Es eignet sich gut für kleinere Teams, Supportaufgaben oder laufende Verbesserungen.

---

## Versionsverwaltung im Projekt

Versionsverwaltung ist ein wichtiger Bestandteil moderner Softwareprojekte.

Git ist dafür sehr verbreitet.

Vorteile von Git:

- Änderungen nachvollziehen
- alte Versionen wiederherstellen
- Branches nutzen
- Zusammenarbeit im Team
- Code sichern
- Fehler leichter finden
- Entwicklungsstände dokumentieren

In Projekten sollte Code nicht nur lokal auf einem Gerät liegen. Ein Repository sorgt für bessere Nachvollziehbarkeit und Zusammenarbeit.

---

## Repository

Ein Repository ist ein Speicherort für ein Projekt mit Versionsgeschichte.

Typische Inhalte:

- Quellcode
- README
- Dokumentation
- Konfigurationsdateien
- Tests
- Beispiele
- Skripte
- Lizenzinformationen

Ein gutes Repository sollte übersichtlich aufgebaut sein.

Andere Personen sollten verstehen können, was das Projekt macht, wie es gestartet wird und welche Dateien wichtig sind.

---

## Branches

Branches ermöglichen parallele Arbeit an verschiedenen Änderungen.

Beispiele:

- `main`
- `dev`
- `feature-login`
- `bugfix-validation`
- `documentation`

Ein Branch kann genutzt werden, um eine neue Funktion zu entwickeln, ohne direkt den stabilen Hauptstand zu verändern.

Nach Prüfung kann der Branch wieder zusammengeführt werden.

---

## Commit

Ein Commit speichert einen Projektstand in Git.

Ein guter Commit sollte:

- eine klare Änderung enthalten
- verständliche Nachricht haben
- nicht zu groß sein
- zusammengehörige Änderungen bündeln

Beispielhafte Commit-Nachrichten:

- `Add user input validation`
- `Fix CSV import error`
- `Update project documentation`
- `Create database schema`
- `Add basic logging`

Commits helfen, die Entwicklung später nachzuvollziehen.

---

## Zusammenarbeit im Team

Softwareprojekte werden oft im Team umgesetzt.

Wichtige Punkte:

- klare Aufgabenverteilung
- gemeinsame Regeln
- einheitlicher Code-Stil
- regelmäßige Abstimmung
- Versionsverwaltung nutzen
- Änderungen prüfen
- Dokumentation aktuell halten
- Konflikte früh klären

Teamarbeit funktioniert besser, wenn nicht jeder einfach irgendwo im Code Änderungen macht.

Struktur, Kommunikation und Reviews sind wichtig.

---

## Code Reviews

Ein Code Review bedeutet, dass eine andere Person den Code prüft.

Dabei wird nicht nur gesucht, ob der Code läuft.

Geprüft werden kann:

- Verständlichkeit
- Fehler
- Sicherheit
- Code-Stil
- Wartbarkeit
- Tests
- Dokumentation
- unnötige Komplexität

Code Reviews verbessern Qualität und helfen beim Lernen.

Auch Anfänger profitieren davon, weil sie Feedback zu Denkweise und Struktur bekommen.

---

## Entwicklungswerkzeuge im Projekt

Ein Softwareprojekt nutzt verschiedene Werkzeuge.

| Werkzeug      | Zweck                                   |
| ------------- | --------------------------------------- |
| Editor / IDE  | Code schreiben                          |
| Git           | Versionierung                           |
| Terminal      | Befehle ausführen                       |
| Debugger      | Fehler untersuchen                      |
| Datenbanktool | Daten prüfen                            |
| Testwerkzeug  | Tests ausführen                         |
| Issue-Tracker | Aufgaben verwalten                      |
| Dokumentation | Wissen festhalten                       |
| CI/CD         | automatische Prüfungen und Auslieferung |
| Container     | Umgebung reproduzierbar machen          |

Die Werkzeuge sollten zum Projekt passen und nicht unnötig kompliziert sein.

---

## Entwicklungsumgebung

Die Entwicklungsumgebung ist die Umgebung, in der Code geschrieben und getestet wird.

Sie kann enthalten:

- Betriebssystem
- Programmiersprache
- Abhängigkeiten
- Editor
- Terminal
- lokale Datenbank
- Testdaten
- Konfigurationsdateien
- virtuelle Umgebung
- Docker-Container

Eine saubere Entwicklungsumgebung reduziert Fehler.

Wenn jeder Entwickler eine komplett andere Umgebung hat, können Probleme entstehen, die schwer nachvollziehbar sind.

---

## Abhängigkeiten

Software nutzt oft externe Bibliotheken, Frameworks oder Pakete.

Beispiele:

- Python-Pakete über `pip`
- JavaScript-Pakete über `npm`
- Datenbanktreiber
- Webframeworks
- Testbibliotheken
- Systempakete

Abhängigkeiten müssen dokumentiert werden.

Sonst läuft die Software vielleicht nur auf dem Rechner des Entwicklers, aber nicht auf einem anderen System.

---

## Konfiguration

Software benötigt oft Konfigurationsdaten.

Beispiele:

- Datenbankadresse
- Portnummer
- API-Schlüssel
- Dateipfade
- Log-Level
- Benutzerrollen
- Servername
- Umgebungseinstellungen

Konfiguration sollte nicht fest im Code versteckt sein, wenn sie sich je nach Umgebung ändert.

Wichtig:

Passwörter, API-Schlüssel und geheime Zugangsdaten gehören nicht in öffentliche Repositories.

---

## Anforderungen an Sicherheit

Sicherheit muss im Projekt von Anfang an berücksichtigt werden.

Wichtige Fragen:

- Welche Daten werden verarbeitet?
- Gibt es personenbezogene Daten?
- Wer darf welche Funktionen nutzen?
- Wie erfolgt Anmeldung?
- Werden Passwörter sicher behandelt?
- Werden Daten verschlüsselt übertragen?
- Werden Eingaben geprüft?
- Gibt es Logs?
- Gibt es Backups?
- Werden Fehler sicher behandelt?
- Gibt es administrative Funktionen?

Sicherheit nachträglich einzubauen ist oft schwieriger als sie direkt mitzudenken.

---

## Datenschutz im Projekt

Wenn personenbezogene Daten verarbeitet werden, muss Datenschutz beachtet werden.

Wichtige Fragen:

- Welche personenbezogenen Daten werden gespeichert?
- Warum werden sie gespeichert?
- Wer darf darauf zugreifen?
- Wie lange werden sie gespeichert?
- Wie werden sie gelöscht?
- Werden Daten in die Cloud übertragen?
- Werden Daten verschlüsselt?
- Gibt es Testdaten ohne echte Personen?
- Werden Daten in Logs geschrieben?

In Lernprojekten und öffentlichen Repositories sollten keine echten personenbezogenen Daten verwendet werden.

Besser sind künstliche Beispieldaten.

---

## Testen im Projekt

Tests prüfen, ob Software korrekt funktioniert.

Arten von Tests:

| Testart          | Bedeutung                                  |
| ---------------- | ------------------------------------------ |
| manueller Test   | Benutzer oder Entwickler prüft selbst      |
| Unit-Test        | einzelne Funktion wird getestet            |
| Integrationstest | Zusammenspiel mehrerer Teile wird getestet |
| Systemtest       | gesamtes System wird geprüft               |
| Abnahmetest      | Kunde oder Benutzer prüft Ergebnis         |

Tests sollten nicht erst ganz am Ende stattfinden.

Je früher Fehler gefunden werden, desto leichter sind sie meistens zu beheben.

---

## Fehlerverwaltung

Fehler sollten dokumentiert und nachvollziehbar bearbeitet werden.

Wichtige Informationen bei Fehlern:

- was ist passiert?
- wann ist es passiert?
- bei welchem Benutzer oder System?
- welche Schritte führen zum Fehler?
- welche Fehlermeldung erscheint?
- welche Version ist betroffen?
- wie kritisch ist der Fehler?
- wurde der Fehler behoben?
- wurde die Lösung getestet?

Eine gute Fehlerbeschreibung spart viel Zeit bei der Analyse.

---

## Dokumentation im Projekt

Dokumentation gehört zum Softwareprojekt dazu.

Wichtige Dokumente:

- README
- Installationsanleitung
- Benutzeranleitung
- technische Dokumentation
- Datenmodell
- Schnittstellenbeschreibung
- Testprotokoll
- Änderungsprotokoll
- Betriebsanleitung
- bekannte Fehler
- Entscheidungen und Begründungen

Dokumentation muss nicht perfekt sein, aber sie muss nutzbar sein.

Eine Software ohne Dokumentation ist schwer zu betreiben, zu erweitern oder zu übergeben.

---

## README

Eine README-Datei erklärt ein Projekt direkt im Repository.

Typische Inhalte:

- Projektname
- kurze Beschreibung
- Ziel
- Funktionen
- Voraussetzungen
- Installation
- Nutzung
- Beispiel
- Projektstruktur
- bekannte Einschränkungen
- Autor oder Kontext

Eine gute README hilft anderen Personen, das Projekt schnell zu verstehen.

Für Portfolio-Projekte ist eine gute README besonders wichtig.

---

## Projektstruktur

Eine klare Projektstruktur hilft bei Übersicht und Wartung.

Beispiel für ein kleines Python-Projekt:

| Datei / Ordner     | Zweck                            |
| ------------------ | -------------------------------- |
| `main.py`          | Startpunkt des Programms         |
| `src/`             | Programmlogik                    |
| `tests/`           | Tests                            |
| `docs/`            | Dokumentation                    |
| `data/`            | Beispieldaten                    |
| `README.md`        | Projektbeschreibung              |
| `.gitignore`       | Dateien, die Git ignorieren soll |
| `requirements.txt` | Python-Abhängigkeiten            |

Nicht jedes Projekt braucht genau diese Struktur. Wichtig ist, dass die Struktur verständlich ist.

---

## Qualität im Softwareprojekt

Softwarequalität bedeutet, dass die Lösung fachlich, technisch und organisatorisch brauchbar ist.

Wichtige Qualitätsmerkmale:

| Merkmal          | Bedeutung                                   |
| ---------------- | ------------------------------------------- |
| Funktionalität   | Software erfüllt Anforderungen              |
| Zuverlässigkeit  | Software läuft stabil                       |
| Wartbarkeit      | Software kann später geändert werden        |
| Verständlichkeit | Code und Dokumentation sind nachvollziehbar |
| Sicherheit       | Daten und Zugriffe sind geschützt           |
| Benutzbarkeit    | Benutzer können sinnvoll damit arbeiten     |
| Leistung         | Software reagiert schnell genug             |
| Testbarkeit      | Funktionen können geprüft werden            |

Qualität entsteht nicht zufällig. Sie entsteht durch Planung, sauberen Code, Tests, Reviews und Dokumentation.

---

## Übergabe und Abnahme

Am Ende eines Projekts wird das Ergebnis übergeben oder abgenommen.

Dabei wird geprüft:

- erfüllt die Software die Anforderungen?
- funktioniert sie in der Zielumgebung?
- sind Tests durchgeführt?
- ist die Dokumentation vorhanden?
- sind bekannte Fehler dokumentiert?
- wurde die Installation beschrieben?
- sind Benutzer informiert?
- ist der Betrieb geklärt?
- sind Backups oder Wiederherstellung bedacht?

Eine Abnahme bedeutet nicht immer, dass alles perfekt ist. Sie bedeutet, dass das vereinbarte Ergebnis geprüft und akzeptiert wurde.

---

## Wartung nach dem Projekt

Nach der ersten Version beginnt oft die Wartung.

Typische Wartungsaufgaben:

- Fehler beheben
- Sicherheitsupdates einspielen
- Abhängigkeiten aktualisieren
- Anforderungen ergänzen
- Dokumentation aktualisieren
- Datenbank anpassen
- Logs prüfen
- Performance verbessern
- Benutzer unterstützen

Software ist selten komplett fertig.

Sie muss gepflegt werden, solange sie genutzt wird.

---

## Risiken in Softwareprojekten

Softwareprojekte können verschiedene Risiken haben.

| Risiko                 | Beispiel                                       |
| ---------------------- | ---------------------------------------------- |
| unklare Anforderungen  | Kunde weiß nicht genau, was gebraucht wird     |
| Zeitdruck              | Tests und Dokumentation werden weggelassen     |
| technische Probleme    | Schnittstelle funktioniert anders als erwartet |
| Sicherheitsrisiken     | Zugriffsschutz wird vergessen                  |
| Datenschutzrisiken     | echte Personendaten werden falsch verwendet    |
| Abhängigkeiten         | externe Bibliothek wird nicht mehr gepflegt    |
| fehlende Dokumentation | Betrieb wird später schwierig                  |
| fehlende Tests         | Fehler bleiben unentdeckt                      |
| Wissensverlust         | nur eine Person versteht das Projekt           |

Risiken sollten früh erkannt und regelmäßig geprüft werden.

---

## Praxisbeispiele

### Beispiel 1: Log-Auswertung mit Python

Ein kleines Projekt soll Serverlogs nach Fehlermeldungen durchsuchen. Das Projekt wird in Aufgaben zerlegt: Eingabedatei lesen, Suchbegriffe definieren, Treffer zählen, Ergebnis ausgeben, Fehlerbehandlung ergänzen und README schreiben.

### Beispiel 2: Inventarverwaltung

Ein Unternehmen möchte Geräte wie Laptops und Monitore verwalten. Das Projekt benötigt Anforderungen, Datenfelder, Benutzerrollen, Speicherung, Suchfunktion, Backup und Dokumentation.

### Beispiel 3: Webformular für Supportanfragen

Ein Supportformular soll Anfragen erfassen. Wichtig sind Eingabevalidierung, Datenschutz, Speicherung in einer Datenbank, Benachrichtigung, Statusverwaltung und Schutz vor Missbrauch.

---

## Typische Fehler

| Fehler                                | Problem                                 |
| ------------------------------------- | --------------------------------------- |
| direkt mit Code beginnen              | Ziel und Anforderungen bleiben unklar   |
| keine Aufgabenplanung                 | wichtige Schritte werden vergessen      |
| keine Versionsverwaltung              | Änderungen sind nicht nachvollziehbar   |
| alles in einer großen Datei schreiben | Wartung wird schwierig                  |
| keine Tests durchführen               | Fehler fallen spät auf                  |
| Dokumentation erst am Ende anfangen   | wichtige Entscheidungen gehen verloren  |
| echte Daten im Test nutzen            | Datenschutzrisiko                       |
| Passwörter ins Repository schreiben   | Sicherheitsrisiko                       |
| Betrieb nicht mitdenken               | Software läuft später nicht zuverlässig |
| Feedback der Benutzer ignorieren      | Software passt nicht zum Alltag         |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Softwareentwicklung in Projekten wichtig, weil auch Systemintegration oft projektorientiert arbeitet.

Ein FISI muss nicht jede Software komplett selbst entwickeln, aber er muss verstehen, wie Softwareprojekte aufgebaut sind und wie Software später betrieben wird.

In der Praxis bedeutet das:

- Anforderungen mit Benutzern klären
- kleine Skripte strukturiert entwickeln
- Git zur Versionierung nutzen
- Konfigurationsdaten sicher behandeln
- Test- und Produktivumgebungen unterscheiden
- Datenbanken und Schnittstellen einordnen
- Dokumentation schreiben
- Betrieb und Wartung mitdenken
- Sicherheits- und Datenschutzanforderungen beachten
- Fehler nachvollziehbar beschreiben

Ein guter FISI denkt bei Softwareprojekten nicht nur an Code, sondern auch an Ziel, Daten, Umgebung, Sicherheit, Tests, Dokumentation und Betrieb.

---

## Kurze Zusammenfassung

Software in Projekten zu entwickeln bedeutet, eine Softwarelösung geplant und nachvollziehbar umzusetzen.

Wichtige Bestandteile sind Projektziel, Anforderungen, Rollen, Aufgaben, Zeitplanung, Vorgehensmodell, Versionsverwaltung, Tests, Dokumentation, Sicherheit, Datenschutz, Übergabe und Wartung.

Für FISI ist dieses Kapitel wichtig, weil viele praktische IT-Aufgaben durch Skripte, Automatisierung, Datenbanken oder kleine Softwarelösungen unterstützt werden.
