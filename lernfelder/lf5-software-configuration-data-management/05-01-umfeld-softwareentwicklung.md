# 5.1 Umfeld der Softwareentwicklung analysieren

In diesem Kapitel geht es darum, das Umfeld der Softwareentwicklung zu verstehen.

Software entsteht nicht einfach nur dadurch, dass jemand Code schreibt. Vorher müssen Anforderungen geklärt, Benutzer verstanden, technische Rahmenbedingungen geprüft, Daten betrachtet, Werkzeuge ausgewählt und Zuständigkeiten festgelegt werden.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Software in fast jeder IT-Umgebung vorkommt. Auch wenn FISI nicht immer selbst große Programme entwickeln, müssen sie Software installieren, anpassen, betreiben, dokumentieren, Fehler analysieren und mit Entwicklern oder Anwendern zusammenarbeiten.

---

## Kurz erklärt

Das Umfeld der Softwareentwicklung beschreibt alles, was eine Softwarelösung beeinflusst.

Dazu gehören:

- Benutzer
- Kunden
- Anforderungen
- Geschäftsprozesse
- vorhandene IT-Systeme
- Daten
- Schnittstellen
- Betriebssysteme
- Netzwerke
- Sicherheitsanforderungen
- Programmiersprachen
- Entwicklungswerkzeuge
- Datenbanken
- Tests
- Dokumentation
- Wartung
- Betrieb

Softwareentwicklung ist also nicht nur Programmierung. Sie ist ein geplanter Prozess, bei dem technische und organisatorische Faktoren zusammenkommen.

---

## Was bedeutet Softwareentwicklung?

Softwareentwicklung bedeutet, eine Softwarelösung zu planen, umzusetzen, zu testen, bereitzustellen und weiterzuentwickeln.

Eine Software kann viele Formen haben:

- kleines Skript
- Konsolenprogramm
- Webanwendung
- Desktop-Anwendung
- mobile App
- Datenbankanwendung
- Automatisierungstool
- Schnittstelle
- internes Verwaltungstool
- Cloud-Anwendung

Der Umfang kann sehr unterschiedlich sein.

Ein kleines Python-Skript zur Logauswertung ist auch Software. Eine große Webplattform mit Datenbank, Benutzerverwaltung und API ist ebenfalls Software.

---

## Warum Softwareentwicklung geplant werden muss

Ohne Planung entstehen schnell Probleme.

Typische Probleme bei ungeplanter Softwareentwicklung:

- Anforderungen sind unklar
- Benutzer bekommen nicht das, was sie brauchen
- Datenstruktur passt nicht
- Sicherheit wird vergessen
- Code ist schwer wartbar
- Fehler werden spät entdeckt
- Dokumentation fehlt
- Abhängigkeiten sind unklar
- Software läuft nicht in der Zielumgebung
- Änderungen sind schwer nachvollziehbar

Planung bedeutet nicht, dass jedes Detail von Anfang an perfekt sein muss. Planung bedeutet, dass man bewusst arbeitet und Entscheidungen nachvollziehbar trifft.

---

## Beteiligte Personen

Bei Softwareentwicklung sind oft verschiedene Personen beteiligt.

| Rolle                    | Aufgabe                                             |
| ------------------------ | --------------------------------------------------- |
| Kunde                    | beschreibt Bedarf und Ziel                          |
| Benutzer                 | arbeitet später mit der Software                    |
| Entwickler               | setzt die Software technisch um                     |
| Administrator            | betreibt Systeme und Infrastruktur                  |
| Projektleitung           | koordiniert Zeit, Aufgaben und Ressourcen           |
| Tester                   | prüft Funktion und Qualität                         |
| Datenschutz / Sicherheit | bewertet rechtliche und sicherheitsrelevante Themen |
| Support                  | unterstützt Benutzer nach Einführung                |

In kleinen Projekten kann eine Person mehrere Rollen übernehmen.

Wichtig ist, dass klar ist, wer welche Aufgabe hat.

---

## Kunden und Benutzer

Kunden und Benutzer sind nicht immer die gleiche Person.

Der Kunde beauftragt oder bezahlt eine Lösung.  
Der Benutzer arbeitet später mit der Software.

Beispiel:

Ein Unternehmen möchte ein internes Ticketsystem. Die Geschäftsführung oder IT-Leitung beauftragt die Einführung. Die Benutzer sind später Support-Mitarbeiter und normale Mitarbeitende, die Tickets erstellen.

Software muss die Anforderungen des Kunden erfüllen, aber auch für die Benutzer verständlich und praktisch sein.

---

## Anforderungen

Anforderungen beschreiben, was eine Software leisten soll.

Man unterscheidet häufig zwischen funktionalen und nicht-funktionalen Anforderungen.

| Art                             | Bedeutung                                              |
| ------------------------------- | ------------------------------------------------------ |
| funktionale Anforderungen       | was die Software tun soll                              |
| nicht-funktionale Anforderungen | wie gut oder unter welchen Bedingungen sie es tun soll |

Beispiele für funktionale Anforderungen:

- Benutzer kann sich anmelden
- Daten können gespeichert werden
- Bericht kann exportiert werden
- Suchfunktion ist vorhanden
- Admin kann Benutzer verwalten

Beispiele für nicht-funktionale Anforderungen:

- Software soll schnell reagieren
- Daten müssen verschlüsselt sein
- Anwendung soll im Browser laufen
- System soll 100 Benutzer gleichzeitig unterstützen
- Bedienung soll einfach sein
- Software soll gut dokumentiert sein

Beide Arten sind wichtig.

---

## Geschäftsprozesse verstehen

Software unterstützt oft einen Geschäftsprozess.

Ein Geschäftsprozess beschreibt, wie eine Aufgabe im Unternehmen abläuft.

Beispiele:

- Bestellung bearbeiten
- Rechnung erstellen
- Benutzerkonto anlegen
- Supportticket lösen
- Kundendaten pflegen
- Lagerbestand aktualisieren
- Bericht erzeugen

Damit Software sinnvoll entwickelt werden kann, muss verstanden werden, wie der Prozess wirklich abläuft.

Wenn der Prozess nicht verstanden wird, kann die Software zwar technisch funktionieren, aber im Alltag unpraktisch sein.

---

## Ist-Zustand und Soll-Zustand

Bei der Analyse wird oft zwischen Ist-Zustand und Soll-Zustand unterschieden.

| Zustand      | Bedeutung                       |
| ------------ | ------------------------------- |
| Ist-Zustand  | aktuelle Situation              |
| Soll-Zustand | gewünschte zukünftige Situation |

Beispiel:

Ist-Zustand:

- Benutzer tragen Daten manuell in Excel ein.
- Dateien werden per E-Mail verschickt.
- Fehler entstehen durch doppelte Eingaben.
- Niemand sieht den aktuellen Stand zentral.

Soll-Zustand:

- Daten werden zentral in einer Anwendung erfasst.
- Benutzer haben passende Rechte.
- Änderungen sind nachvollziehbar.
- Berichte können automatisch erzeugt werden.

Diese Unterscheidung hilft, das eigentliche Ziel der Software zu verstehen.

---

## Technische Rahmenbedingungen

Software muss zur vorhandenen IT-Umgebung passen.

Wichtige technische Fragen:

- Welches Betriebssystem wird genutzt?
- Gibt es Windows, Linux oder beides?
- Soll die Software lokal oder im Browser laufen?
- Gibt es eine Datenbank?
- Gibt es vorhandene Server?
- Wird Cloud genutzt?
- Welche Programmiersprache passt?
- Welche Schnittstellen werden benötigt?
- Welche Benutzerverwaltung wird genutzt?
- Gibt es Netzwerkbeschränkungen?
- Welche Sicherheitsrichtlinien gelten?
- Wie wird die Software installiert und aktualisiert?

Eine gute Lösung muss nicht nur programmiert werden, sondern auch in der Zielumgebung zuverlässig laufen.

---

## Daten im Umfeld der Softwareentwicklung

Viele Softwarelösungen arbeiten mit Daten.

Wichtige Fragen zu Daten:

- Welche Daten werden erfasst?
- Wo werden Daten gespeichert?
- Wer darf Daten lesen?
- Wer darf Daten ändern?
- Wie lange werden Daten gespeichert?
- Müssen Daten gelöscht werden?
- Gibt es personenbezogene Daten?
- Müssen Daten gesichert werden?
- Müssen Daten exportiert werden?
- Gibt es Schnittstellen zu anderen Systemen?
- Wie wird Datenqualität sichergestellt?

Daten sind oft der wichtigste Teil einer Softwarelösung.

Wenn Daten falsch gespeichert, ungeschützt oder schlecht strukturiert sind, kann die ganze Anwendung problematisch werden.

---

## Datenquellen

Daten können aus verschiedenen Quellen kommen.

Beispiele:

- manuelle Eingabe durch Benutzer
- CSV-Dateien
- Excel-Dateien
- Datenbanken
- APIs
- Logdateien
- Sensoren
- Webformulare
- andere Anwendungen
- Cloud-Dienste

Die Datenquelle beeinflusst, wie die Software aufgebaut wird.

Eine Anwendung, die Daten aus einer CSV-Datei liest, ist anders aufgebaut als eine Anwendung, die dauerhaft mit einer SQL-Datenbank arbeitet.

---

## Datenqualität

Datenqualität beschreibt, wie gut Daten für ihren Zweck geeignet sind.

Wichtige Merkmale:

| Merkmal      | Bedeutung                                     |
| ------------ | --------------------------------------------- |
| korrekt      | Daten stimmen fachlich                        |
| vollständig  | wichtige Angaben fehlen nicht                 |
| aktuell      | Daten sind nicht veraltet                     |
| eindeutig    | Daten sind nicht doppelt oder widersprüchlich |
| konsistent   | Daten passen zusammen                         |
| verständlich | Daten sind klar interpretierbar               |

Schlechte Datenqualität führt zu Fehlern in Berichten, falschen Entscheidungen und zusätzlicher Arbeit.

Software sollte deshalb Eingaben prüfen und klare Datenstrukturen nutzen.

---

## Schnittstellen

Schnittstellen verbinden Software mit anderen Systemen.

Beispiele:

- Web-API
- Datenbankverbindung
- Dateiimport
- Dateiexport
- E-Mail-Schnittstelle
- Authentifizierungssystem
- Cloud-Dienst
- Drucker
- Monitoring-System

Schnittstellen sind wichtig, weil Software selten komplett allein arbeitet.

Typische Fragen:

- Welche Daten werden übertragen?
- In welchem Format?
- Wie wird die Verbindung geschützt?
- Wer darf die Schnittstelle nutzen?
- Was passiert bei Fehlern?
- Wird der Austausch protokolliert?

Schnittstellen müssen besonders sorgfältig geplant werden, weil Fehler dort oft mehrere Systeme betreffen.

---

## Entwicklungsumgebung

Eine Entwicklungsumgebung ist die Umgebung, in der Software geschrieben und getestet wird.

Dazu gehören:

- Code-Editor oder IDE
- Programmiersprache
- Compiler oder Interpreter
- Paketmanager
- Bibliotheken
- lokale Testdaten
- Versionsverwaltung
- Terminal
- Debugger
- Dokumentation

Beispiele für Werkzeuge:

- VS Code
- PyCharm
- Git
- Python
- pip
- Docker
- SQLite
- PostgreSQL
- Browser-Entwicklertools

Eine gute Entwicklungsumgebung erleichtert das Schreiben, Testen und Verstehen von Software.

---

## Programmiersprachen

Eine Programmiersprache wird genutzt, um Anweisungen für einen Computer zu schreiben.

Beispiele:

| Sprache    | typische Nutzung                                                  |
| ---------- | ----------------------------------------------------------------- |
| Python     | Skripte, Automatisierung, Datenverarbeitung, einfache Anwendungen |
| JavaScript | Webseiten und Webanwendungen                                      |
| Java       | Unternehmensanwendungen, Backend, Android                         |
| C#         | Windows-Anwendungen, Unternehmenssoftware                         |
| PHP        | Webanwendungen                                                    |
| SQL        | Datenbankabfragen                                                 |
| Bash       | Linux-Skripte und Automatisierung                                 |
| PowerShell | Windows-Administration und Automatisierung                        |

Die Wahl der Sprache hängt vom Projekt, der Umgebung, den Anforderungen und dem Team ab.

Für FISI sind Python, Bash, PowerShell und SQL besonders nützlich.

---

## Entwicklungswerkzeuge

Entwicklungswerkzeuge unterstützen den Entwicklungsprozess.

Wichtige Werkzeuge:

| Werkzeug           | Aufgabe                             |
| ------------------ | ----------------------------------- |
| Editor / IDE       | Code schreiben                      |
| Terminal           | Befehle ausführen                   |
| Git                | Versionierung                       |
| Debugger           | Fehler im Code untersuchen          |
| Testwerkzeug       | automatische Tests durchführen      |
| Datenbanktool      | Daten ansehen und bearbeiten        |
| Paketmanager       | Bibliotheken installieren           |
| Dokumentationstool | technische Informationen festhalten |
| Container          | Umgebung reproduzierbar machen      |

Werkzeuge helfen, Software kontrolliert und nachvollziehbar zu entwickeln.

---

## Versionsverwaltung

Versionsverwaltung speichert Änderungen am Code nachvollziehbar.

Git ist ein sehr verbreitetes Werkzeug dafür.

Vorteile:

- Änderungen nachvollziehen
- alte Versionen wiederherstellen
- im Team zusammenarbeiten
- Branches nutzen
- Code sichern
- Fehler leichter finden
- Projektstand dokumentieren

Ohne Versionsverwaltung ist es schwer zu erkennen, wer was geändert hat und wann ein Fehler entstanden ist.

Für professionelle Softwareentwicklung ist Versionsverwaltung fast immer notwendig.

---

## Entwicklungs-, Test- und Produktivumgebung

In der Softwareentwicklung werden Umgebungen häufig getrennt.

| Umgebung             | Zweck                                         |
| -------------------- | --------------------------------------------- |
| Entwicklungsumgebung | hier wird Software geschrieben                |
| Testumgebung         | hier wird Software geprüft                    |
| Produktivumgebung    | hier arbeiten echte Benutzer mit echten Daten |

Diese Trennung ist wichtig.

Man sollte neue Funktionen oder riskante Änderungen nicht direkt mit echten Benutzern und echten Daten testen.

Eine klare Trennung reduziert Risiken und erleichtert Fehlersuche.

---

## Betrieb der Software

Software muss nach der Entwicklung betrieben werden.

Betrieb bedeutet:

- Software installieren
- Server bereitstellen
- Datenbank betreiben
- Updates einspielen
- Zugriffe verwalten
- Backups durchführen
- Monitoring einrichten
- Logs prüfen
- Fehler beheben
- Benutzer unterstützen
- Dokumentation pflegen

Hier ist der FISI-Bezug besonders stark.

Systemintegration bedeutet oft, Software nicht selbst komplett zu entwickeln, aber zuverlässig bereitzustellen und zu betreiben.

---

## Sicherheit im Softwareumfeld

Sicherheit muss von Anfang an berücksichtigt werden.

Wichtige Sicherheitsfragen:

- Welche Daten werden verarbeitet?
- Gibt es personenbezogene Daten?
- Wie erfolgt Anmeldung?
- Welche Rechte gibt es?
- Werden Daten verschlüsselt?
- Gibt es sichere Passwörter und MFA?
- Wie werden Eingaben geprüft?
- Werden Logs geschrieben?
- Gibt es Backups?
- Wie werden Updates eingespielt?
- Gibt es offene Schnittstellen?
- Wer darf administrieren?

Sicherheit nachträglich einzubauen ist oft schwieriger als sie direkt mitzudenken.

---

## Datenschutz

Datenschutz ist wichtig, wenn personenbezogene Daten verarbeitet werden.

Personenbezogene Daten können sein:

- Name
- Adresse
- E-Mail-Adresse
- Telefonnummer
- Kundennummer
- Personalnummer
- IP-Adresse in bestimmten Zusammenhängen
- Bewerbungsdaten
- Gesundheitsdaten

Bei Softwareprojekten muss geprüft werden:

- Welche personenbezogenen Daten werden gespeichert?
- Warum werden sie gespeichert?
- Wer darf darauf zugreifen?
- Wie lange werden sie gespeichert?
- Wie werden sie gelöscht?
- Wie werden sie geschützt?

Für FISI ist wichtig, solche Daten nicht unkontrolliert zu kopieren oder unsicher zu speichern.

---

## Qualität von Software

Softwarequalität bedeutet, dass eine Software zuverlässig, verständlich und passend zum Zweck ist.

Wichtige Qualitätsmerkmale:

| Merkmal         | Bedeutung                             |
| --------------- | ------------------------------------- |
| Funktionalität  | Software erfüllt die Anforderungen    |
| Zuverlässigkeit | Software läuft stabil                 |
| Benutzbarkeit   | Benutzer können sie sinnvoll bedienen |
| Wartbarkeit     | Software kann später geändert werden  |
| Sicherheit      | Daten und Zugriffe sind geschützt     |
| Leistung        | Software reagiert schnell genug       |
| Kompatibilität  | Software passt zur Umgebung           |
| Dokumentation   | Aufbau und Nutzung sind verständlich  |

Gute Software ist nicht nur Code, der irgendwie läuft.

Gute Software ist verständlich, testbar, sicher und wartbar.

---

## Wartung und Weiterentwicklung

Software ist nach der ersten Version nicht fertig.

Typische Gründe für Änderungen:

- Fehler werden gefunden
- Anforderungen ändern sich
- neue Benutzerwünsche entstehen
- Betriebssysteme ändern sich
- Sicherheitsupdates sind nötig
- Datenbankstruktur muss angepasst werden
- Schnittstellen ändern sich
- Performance muss verbessert werden
- Dokumentation muss aktualisiert werden

Deshalb sollte Software so entwickelt werden, dass sie später gewartet und erweitert werden kann.

---

## Dokumentation im Softwareumfeld

Dokumentation ist wichtig für Entwicklung, Betrieb und Support.

Wichtige Dokumente:

- Anforderungen
- Installationsanleitung
- Benutzeranleitung
- technische Dokumentation
- Datenbankbeschreibung
- Schnittstellenbeschreibung
- Testprotokolle
- Änderungsprotokoll
- Fehlerbeschreibung
- Betriebsdokumentation
- Backup- und Restore-Anleitung

Ohne Dokumentation wird eine Software schwer verständlich und schwer wartbar.

Das betrifft besonders den Betrieb, wenn andere Personen später die Software übernehmen müssen.

---

## Projektarbeit

Softwareentwicklung findet häufig in Projekten statt.

Ein Projekt hat normalerweise:

- Ziel
- Zeitraum
- Aufgaben
- Rollen
- Ressourcen
- Anforderungen
- Risiken
- Ergebnis
- Dokumentation

Auch kleine Softwareprojekte sollten strukturiert geplant werden.

Beispiel:

Ein kleines Python-Tool zur Auswertung von Logdateien braucht trotzdem Ziel, Eingabedaten, Ausgabeformat, Testfälle und Dokumentation.

---

## Vorgehen bei der Umfeldanalyse

Eine einfache Reihenfolge:

1. Ziel der Software klären
2. Benutzer und Kunden identifizieren
3. Ist-Zustand beschreiben
4. Soll-Zustand beschreiben
5. Anforderungen sammeln
6. Daten und Datenquellen betrachten
7. vorhandene IT-Systeme prüfen
8. Schnittstellen erkennen
9. Sicherheitsanforderungen klären
10. technische Rahmenbedingungen prüfen
11. Werkzeuge auswählen
12. Betrieb und Wartung mitdenken
13. Ergebnis dokumentieren

Diese Analyse hilft, bevor mit der eigentlichen Umsetzung begonnen wird.

---

## Praxisbeispiele

### Beispiel 1: Python-Tool für Logdateien

Ein FISI möchte ein kleines Python-Tool schreiben, das Logdateien nach Fehlern durchsucht. Vorher muss geklärt werden, wo die Logs liegen, welches Format sie haben, welche Fehler gesucht werden, wie das Ergebnis ausgegeben wird und wer das Tool nutzt.

### Beispiel 2: Datenbank für Inventar

Ein Unternehmen möchte Geräte wie PCs, Monitore und Drucker besser verwalten. Dafür wird eine kleine Datenbank geplant. Wichtig sind Datenfelder, Benutzerrechte, Suchfunktionen, Backup und spätere Erweiterbarkeit.

### Beispiel 3: Webanwendung für Supporttickets

Eine Supportabteilung möchte Tickets zentral erfassen. Vor der Entwicklung müssen Benutzerrollen, Statuswerte, Benachrichtigungen, Datenschutz, Datenbank, Anmeldung und Auswertungen geklärt werden.

---

## Typische Fehler

| Fehler                          | Problem                                 |
| ------------------------------- | --------------------------------------- |
| direkt mit Code anfangen        | Anforderungen und Ziel sind unklar      |
| Benutzer nicht einbeziehen      | Software passt nicht zum Alltag         |
| Datenstruktur nicht planen      | spätere Änderungen werden schwierig     |
| Sicherheit zu spät beachten     | Risiken entstehen schon im Design       |
| keine Versionsverwaltung nutzen | Änderungen sind nicht nachvollziehbar   |
| keine Testumgebung verwenden    | Fehler landen direkt bei Benutzern      |
| Dokumentation weglassen         | Wartung wird schwierig                  |
| Betrieb nicht mitdenken         | Software läuft später nicht zuverlässig |
| Schnittstellen unterschätzen    | Fehler betreffen mehrere Systeme        |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist das Umfeld der Softwareentwicklung wichtig, weil Software in der Praxis immer mit Infrastruktur zusammenhängt.

Ein FISI muss verstehen:

- auf welchem System Software läuft
- welche Daten verarbeitet werden
- welche Benutzer Zugriff brauchen
- welche Netzwerke und Dienste benötigt werden
- wie Software installiert wird
- wie Updates eingespielt werden
- wie Logs und Fehler analysiert werden
- wie Backups funktionieren
- wie Sicherheit umgesetzt wird
- wie Software dokumentiert wird

Ein guter FISI denkt bei Software nicht nur an den Code, sondern auch an Betriebssystem, Netzwerk, Datenbank, Benutzerrechte, Sicherheit, Backup und Wartung.

---

## Kurze Zusammenfassung

Das Umfeld der Softwareentwicklung umfasst alle technischen, organisatorischen und fachlichen Faktoren, die eine Softwarelösung beeinflussen.

Dazu gehören Benutzer, Kunden, Anforderungen, Geschäftsprozesse, Daten, Schnittstellen, Entwicklungswerkzeuge, Programmiersprachen, Sicherheit, Datenschutz, Betrieb, Wartung und Dokumentation.

Für FISI ist dieses Thema wichtig, weil Software im IT-Betrieb nicht isoliert existiert, sondern immer Teil einer größeren Infrastruktur ist.
