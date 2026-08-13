# 5.6 Programmiersprachen und Werkzeuge

In diesem Kapitel geht es um Programmiersprachen und Werkzeuge, die bei der Softwareentwicklung eingesetzt werden.

Software entsteht nicht nur durch das Schreiben von Code. Man braucht auch passende Werkzeuge, um Code zu schreiben, auszuführen, zu testen, Fehler zu finden, Änderungen zu verwalten, Abhängigkeiten zu installieren und Ergebnisse zu dokumentieren.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Skripte, Automatisierung, Datenbanken, Konfigurationsdateien und Entwicklungswerkzeuge im IT-Betrieb regelmäßig vorkommen.

---

## Kurz erklärt

Eine Programmiersprache wird genutzt, um einem Computer genaue Anweisungen zu geben.

Entwicklungswerkzeuge helfen dabei, Software zu erstellen, zu prüfen und zu verwalten.

Wichtige Themen sind:

- Programmiersprachen
- Skriptsprachen
- Compiler und Interpreter
- Entwicklungsumgebungen
- Code-Editoren
- Terminal
- Versionsverwaltung
- Paketmanager
- virtuelle Umgebungen
- Debugger
- Testwerkzeuge
- Datenbankwerkzeuge
- Container
- Dokumentation
- Automatisierung

Für FISI sind besonders Python, Bash, PowerShell, SQL, Git, Linux-Terminal, Docker und einfache Entwicklungswerkzeuge wichtig.

---

## Was ist eine Programmiersprache?

Eine Programmiersprache ist eine formale Sprache, mit der Menschen Anweisungen für Computer schreiben.

Ein Computer versteht nicht direkt normale menschliche Sprache. Deshalb werden Programmiersprachen genutzt, um Abläufe eindeutig zu beschreiben.

Beispiele für Anweisungen:

- Wert speichern
- Bedingung prüfen
- Schleife ausführen
- Datei öffnen
- Daten verarbeiten
- Ergebnis ausgeben
- Verbindung zu Datenbank herstellen
- Benutzeranfrage bearbeiten

Programmiersprachen müssen präzise sein. Kleine Schreibfehler oder falsche Struktur können dazu führen, dass ein Programm nicht funktioniert.

---

## Warum es verschiedene Programmiersprachen gibt

Es gibt nicht die eine beste Programmiersprache für alles.

Verschiedene Sprachen sind für verschiedene Aufgaben geeignet.

| Sprache    | typische Nutzung                                                  |
| ---------- | ----------------------------------------------------------------- |
| Python     | Skripte, Automatisierung, Datenverarbeitung, einfache Anwendungen |
| Bash       | Linux-Automatisierung und Shell-Skripte                           |
| PowerShell | Windows-Administration und Automatisierung                        |
| SQL        | Datenbankabfragen und Datenverwaltung                             |
| JavaScript | Webseiten und Webanwendungen                                      |
| Java       | Unternehmensanwendungen und Backend-Systeme                       |
| C#         | Windows-Anwendungen und Backend-Systeme                           |
| PHP        | Webanwendungen                                                    |
| C / C++    | systemnahe Entwicklung, Treiber, performante Programme            |

Die Wahl der Sprache hängt von Aufgabe, Umgebung, Team, Betriebssystem, vorhandener Infrastruktur und Anforderungen ab.

---

## Programmiersprache, Skriptsprache und Abfragesprache

Nicht jede Sprache wird gleich verwendet.

| Art                   | Bedeutung                              | Beispiele                |
| --------------------- | -------------------------------------- | ------------------------ |
| Programmiersprache    | allgemeine Entwicklung von Software    | Python, Java, C#         |
| Skriptsprache         | Automatisierung und kleinere Programme | Bash, PowerShell, Python |
| Abfragesprache        | Arbeit mit Datenbanken                 | SQL                      |
| Auszeichnungssprache  | Struktur von Dokumenten oder Webseiten | HTML, Markdown           |
| Konfigurationssprache | Beschreibung von Einstellungen         | YAML, JSON, XML          |

Ein FISI arbeitet häufig mit mehreren Arten gleichzeitig.

Beispiel:

Eine Docker-Umgebung kann aus Python-Code, einer YAML-Datei, SQL-Datenbankbefehlen und Bash-Kommandos bestehen.

---

## Python

Python ist eine weit verbreitete Programmiersprache.

Python wird häufig genutzt für:

- Automatisierung
- Skripte
- Datenverarbeitung
- einfache Tools
- Webentwicklung
- Tests
- Systemadministration
- Auswertung von Logdateien
- Arbeiten mit APIs
- Lernprojekte

Vorteile von Python:

- gut lesbar
- einfacher Einstieg
- viele Bibliotheken
- plattformübergreifend
- gut für Automatisierung
- stark in Datenverarbeitung
- große Community

Für FISI ist Python besonders nützlich, weil man damit wiederkehrende Aufgaben automatisieren und Daten einfach verarbeiten kann.

---

## Bash

Bash ist eine Shell und Skriptsprache auf Linux- und Unix-Systemen.

Bash wird genutzt für:

- Dateien verwalten
- Programme starten
- Systeminformationen abfragen
- Logs durchsuchen
- Backups automatisieren
- Dienste prüfen
- Befehle kombinieren
- einfache Automatisierung

Typische Werkzeuge in Bash-Umgebungen:

- `cd`
- `ls`
- `cat`
- `grep`
- `awk`
- `sed`
- `find`
- `chmod`
- `systemctl`
- `journalctl`
- `ssh`
- `scp`

Für FISI ist Bash wichtig, weil viele Server mit Linux betrieben werden.

---

## PowerShell

PowerShell ist eine Skript- und Automatisierungsumgebung, die besonders in Windows-Umgebungen wichtig ist.

PowerShell wird genutzt für:

- Windows-Systemadministration
- Benutzerverwaltung
- Dienste verwalten
- Dateien bearbeiten
- Systeme auslesen
- Active Directory verwalten
- Microsoft-Cloud-Dienste administrieren
- Automatisierung von Routineaufgaben

PowerShell arbeitet stark mit Objekten. Dadurch können Informationen aus Befehlen gut weiterverarbeitet werden.

Für FISI ist PowerShell besonders wichtig, wenn Windows-Server, Microsoft 365 oder Active Directory eingesetzt werden.

---

## SQL

SQL bedeutet **Structured Query Language**.

SQL ist keine klassische Programmiersprache für allgemeine Anwendungen, sondern eine Sprache für relationale Datenbanken.

SQL wird genutzt, um:

- Daten abzufragen
- Daten einzufügen
- Daten zu ändern
- Daten zu löschen
- Tabellen zu erstellen
- Datenstrukturen zu ändern
- Rechte zu verwalten

Wichtige SQL-Befehle:

| Befehl       | Aufgabe                 |
| ------------ | ----------------------- |
| SELECT       | Daten abfragen          |
| INSERT       | neue Daten einfügen     |
| UPDATE       | vorhandene Daten ändern |
| DELETE       | Daten löschen           |
| CREATE TABLE | Tabelle erstellen       |
| ALTER TABLE  | Tabelle ändern          |
| DROP TABLE   | Tabelle löschen         |

Für FISI ist SQL wichtig, weil viele Anwendungen ihre Daten in Datenbanken speichern.

---

## JavaScript

JavaScript wird vor allem für Webentwicklung genutzt.

Typische Einsatzbereiche:

- Webseiten
- Webanwendungen
- Benutzeroberflächen im Browser
- Backend-Entwicklung mit Node.js
- APIs
- dynamische Inhalte
- Formularprüfung

JavaScript läuft im Browser und kann Webseiten interaktiv machen.

Für FISI ist JavaScript meistens nicht so zentral wie Python, Bash oder SQL, aber ein Grundverständnis hilft beim Verstehen von Webanwendungen.

---

## Compiler und Interpreter

Programmiersprachen werden unterschiedlich ausgeführt.

Ein Compiler übersetzt Programmcode vor der Ausführung in eine ausführbare Form.

Ein Interpreter führt Code Schritt für Schritt aus.

| Begriff          | Erklärung                               | Beispiele                    |
| ---------------- | --------------------------------------- | ---------------------------- |
| Compiler         | übersetzt Code vor der Ausführung       | C, C++, Go                   |
| Interpreter      | führt Code direkt oder schrittweise aus | Python, Bash                 |
| Laufzeitumgebung | Umgebung, die Programme ausführt        | Python Runtime, Java Runtime |

Python wird typischerweise interpretiert.  
C oder C++ werden typischerweise kompiliert.

Für die Praxis bedeutet das: Manche Programme müssen zuerst gebaut werden, andere können direkt mit dem passenden Interpreter gestartet werden.

---

## Syntax

Syntax beschreibt die Regeln einer Programmiersprache.

Beispiele für Syntaxregeln:

- Klammern richtig setzen
- Anführungszeichen korrekt verwenden
- Einrückungen beachten
- Schlüsselwörter richtig schreiben
- Doppelpunkte an passenden Stellen setzen
- Dateiendungen beachten

Wenn die Syntax falsch ist, kann das Programm meistens nicht ausgeführt werden.

Beispiel:

In Python sind Einrückungen besonders wichtig. Eine falsche Einrückung kann die Logik verändern oder einen Fehler auslösen.

---

## Semantik

Semantik beschreibt die Bedeutung des Codes.

Ein Programm kann syntaktisch korrekt sein, aber trotzdem fachlich falsch arbeiten.

Beispiel:

Der Code läuft ohne Fehlermeldung, berechnet aber einen falschen Preis oder löscht den falschen Datensatz.

Syntax beantwortet:

> Ist der Code formal richtig geschrieben?

Semantik beantwortet:

> Macht der Code fachlich das Richtige?

Beides ist wichtig.

---

## Entwicklungsumgebung

Eine Entwicklungsumgebung ist die Umgebung, in der Software erstellt wird.

Dazu gehören:

- Betriebssystem
- Programmiersprache
- Editor oder IDE
- Terminal
- Interpreter oder Compiler
- Paketmanager
- Bibliotheken
- Git
- Debugger
- Testdaten
- Dokumentation
- lokale Konfiguration

Eine gute Entwicklungsumgebung macht Entwicklung einfacher, schneller und nachvollziehbarer.

---

## Editor und IDE

Ein Editor oder eine IDE wird genutzt, um Code zu schreiben.

| Werkzeug | Bedeutung                                                    |
| -------- | ------------------------------------------------------------ |
| Editor   | Programm zum Schreiben von Code und Text                     |
| IDE      | integrierte Entwicklungsumgebung mit vielen Zusatzfunktionen |

Beispiele:

- VS Code
- PyCharm
- IntelliJ IDEA
- Eclipse
- Visual Studio
- nano
- vim

VS Code ist ein beliebter Editor, weil er viele Sprachen unterstützt und durch Erweiterungen angepasst werden kann.

Eine IDE bietet oft zusätzliche Funktionen wie Debugger, Projektverwaltung, Autovervollständigung und Testintegration.

---

## Terminal

Das Terminal ist ein wichtiges Werkzeug für Entwickler und Administratoren.

Über das Terminal können Befehle ausgeführt werden.

Typische Aufgaben:

- Dateien erstellen
- Programme starten
- Git verwenden
- Pakete installieren
- Tests ausführen
- Logs anzeigen
- Server verwalten
- Docker nutzen
- Skripte ausführen
- Prozesse prüfen

Für FISI ist das Terminal besonders wichtig, weil viele Aufgaben auf Servern ohne grafische Oberfläche durchgeführt werden.

---

## Git

Git ist ein Werkzeug zur Versionsverwaltung.

Git speichert Änderungen am Code und an Projektdateien.

Vorteile:

- Änderungen nachvollziehen
- alte Stände wiederherstellen
- Branches nutzen
- im Team arbeiten
- Fehler leichter finden
- Projektstände dokumentieren
- Code sicher in einem Repository speichern

Wichtige Git-Befehle:

| Befehl     | Aufgabe                          |
| ---------- | -------------------------------- |
| git status | aktuellen Zustand anzeigen       |
| git add    | Änderungen vormerken             |
| git commit | Änderungen speichern             |
| git push   | Änderungen hochladen             |
| git pull   | Änderungen herunterladen         |
| git log    | Verlauf anzeigen                 |
| git branch | Branches anzeigen oder erstellen |
| git switch | Branch wechseln                  |
| git clone  | Repository kopieren              |

Git ist in professionellen Projekten fast unverzichtbar.

---

## Repository

Ein Repository ist ein Projektordner mit Versionsgeschichte.

Ein gutes Repository enthält meistens:

- Quellcode
- README
- Dokumentation
- Tests
- Konfigurationsdateien
- `.gitignore`
- Beispieldaten
- Installationshinweise

Ein Repository sollte keine sensiblen Daten enthalten.

Nicht in öffentliche Repositories gehören:

- Passwörter
- API-Schlüssel
- private SSH-Schlüssel
- echte Kundendaten
- interne IP-Pläne
- private Screenshots
- Zugangsdaten
- vertrauliche Dokumente

Für Portfolio-Projekte ist ein sauberes Repository sehr wichtig.

---

## Paketmanager

Ein Paketmanager installiert und verwaltet Softwarepakete oder Bibliotheken.

Beispiele:

| Umgebung            | Paketmanager |
| ------------------- | ------------ |
| Python              | pip          |
| Node.js             | npm          |
| Linux Debian/Ubuntu | apt          |
| Red Hat/Fedora      | dnf          |
| Windows             | winget       |
| macOS               | brew         |

Paketmanager helfen, benötigte Software kontrolliert zu installieren.

Bei Projekten ist wichtig, Abhängigkeiten zu dokumentieren, damit andere Personen das Projekt ebenfalls ausführen können.

---

## Bibliotheken und Abhängigkeiten

Eine Bibliothek ist fertiger Code, der in einem Projekt genutzt werden kann.

Beispiele:

- Bibliothek für Datenbankzugriff
- Bibliothek für Webserver
- Bibliothek für CSV-Verarbeitung
- Bibliothek für Tests
- Bibliothek für HTTP-Anfragen

Abhängigkeiten sparen Zeit, können aber auch Risiken bringen.

Wichtige Punkte:

- nur notwendige Bibliotheken nutzen
- Versionen dokumentieren
- Sicherheitsupdates beachten
- ungenutzte Abhängigkeiten entfernen
- vertrauenswürdige Quellen nutzen

Eine externe Bibliothek kann Sicherheitslücken enthalten oder später nicht mehr gepflegt werden.

---

## Virtuelle Umgebungen

Virtuelle Umgebungen trennen Projektabhängigkeiten voneinander.

In Python wird häufig eine virtuelle Umgebung genutzt.

Vorteile:

- jedes Projekt hat eigene Abhängigkeiten
- weniger Konflikte zwischen Projekten
- System-Python bleibt sauberer
- Projekt ist besser reproduzierbar
- Installation wird übersichtlicher

Typischer Ablauf bei Python:

```bash
python3 -m venv venv
source venv/bin/activate
pip install paketname
```

Eine virtuelle Umgebung gehört normalerweise nicht ins Git-Repository.

Deshalb steht `venv/` oft in der `.gitignore`.

---

## Debugger

Ein Debugger hilft bei der Fehlersuche im Code.

Mit einem Debugger kann man:

- Programm Schritt für Schritt ausführen
- Variablenwerte ansehen
- Haltepunkte setzen
- Abläufe nachvollziehen
- Fehlerstellen genauer finden

Debugging ist ein normaler Teil der Entwicklung.

Auch erfahrener Code funktioniert nicht immer sofort korrekt.

Ein Debugger hilft, nicht nur zu raten, sondern den Programmablauf genau zu untersuchen.

---

## Logging

Logging bedeutet, dass ein Programm Ereignisse protokolliert.

Logs können enthalten:

- Start und Ende eines Programms
- Fehlermeldungen
- Warnungen
- Benutzeraktionen
- technische Zustände
- Verbindungsprobleme
- Datenbankfehler

Logs helfen später bei:

- Fehlersuche
- Betrieb
- Monitoring
- Sicherheitsanalyse
- Nachvollziehbarkeit

Wichtig ist, dass Logs keine sensiblen Daten unnötig speichern.

Passwörter oder geheime Tokens dürfen nicht in Logs stehen.

---

## Testwerkzeuge

Testwerkzeuge helfen zu prüfen, ob Software korrekt funktioniert.

Tests können manuell oder automatisch sein.

Arten von Tests:

| Testart          | Bedeutung                                 |
| ---------------- | ----------------------------------------- |
| manueller Test   | Benutzer oder Entwickler prüft per Hand   |
| Unit-Test        | einzelne Funktion wird geprüft            |
| Integrationstest | mehrere Teile werden zusammen geprüft     |
| Systemtest       | gesamte Anwendung wird geprüft            |
| Abnahmetest      | Ergebnis wird gegen Anforderungen geprüft |

Automatische Tests sind besonders nützlich, wenn Software regelmäßig geändert wird.

Sie helfen, alte Funktionen nach Änderungen erneut zu prüfen.

---

## Linter und Formatter

Ein Linter prüft Code auf mögliche Probleme.

Ein Formatter formatiert Code automatisch nach bestimmten Regeln.

Vorteile:

- einheitlicher Code-Stil
- bessere Lesbarkeit
- weniger einfache Fehler
- bessere Teamarbeit
- schnelleres Review

Beispiele für Prüfungen:

- ungenutzte Variablen
- falsche Einrückung
- zu lange Zeilen
- unsaubere Struktur
- mögliche Fehlerquellen

Solche Werkzeuge verbessern Codequalität, ersetzen aber keine Tests und kein Verständnis.

---

## Datenbankwerkzeuge

Datenbankwerkzeuge helfen, Datenbanken zu verwalten und zu prüfen.

Beispiele:

- Adminer
- pgAdmin
- DBeaver
- MySQL Workbench
- SQLite Browser
- psql
- mysql CLI

Mit Datenbankwerkzeugen kann man:

- Tabellen ansehen
- SQL-Abfragen ausführen
- Daten prüfen
- Datenstrukturen betrachten
- Benutzerrechte verwalten
- Daten exportieren
- Fehler analysieren

Für FISI ist wichtig, Datenbanken nicht nur als Blackbox zu sehen, sondern grundlegende Struktur und Abfragen zu verstehen.

---

## Container als Entwicklungswerkzeug

Container können helfen, Entwicklungs- und Testumgebungen reproduzierbar aufzubauen.

Docker wird häufig genutzt, um Anwendungen oder Dienste isoliert auszuführen.

Beispiele:

- Datenbank als Container starten
- Webserver testen
- Anwendung mit Abhängigkeiten ausführen
- gleiche Umgebung auf mehreren Systemen nutzen
- lokale Testumgebung aufbauen

Vorteile:

- reproduzierbare Umgebung
- weniger Konflikte mit lokalem System
- einfache Bereitstellung
- gut für Tests
- nützlich für Teamarbeit

Für FISI ist Docker wichtig, weil moderne Anwendungen oft containerisiert betrieben werden.

---

## CI/CD-Werkzeuge

CI/CD-Werkzeuge automatisieren Schritte im Entwicklungsprozess.

CI bedeutet Continuous Integration.  
CD bedeutet Continuous Delivery oder Continuous Deployment.

Typische Aufgaben:

- Code automatisch testen
- Codequalität prüfen
- Anwendung bauen
- Container-Image erstellen
- Dokumentation prüfen
- Deployment vorbereiten
- neue Version veröffentlichen

Beispiele für CI/CD-Werkzeuge:

- GitHub Actions
- GitLab CI
- Jenkins
- Azure DevOps

Für FISI ist CI/CD wichtig, weil Entwicklung und Betrieb in modernen Umgebungen enger zusammenarbeiten.

---

## Dokumentationswerkzeuge

Dokumentation ist ein wichtiger Teil der Softwareentwicklung.

Typische Dokumentationsformen:

- README
- Markdown-Dateien
- Wiki
- technische Dokumentation
- Installationsanleitung
- Benutzeranleitung
- API-Dokumentation
- Kommentare im Code
- Changelog

Markdown ist besonders beliebt für README-Dateien und GitHub-Dokumentation.

Gute Dokumentation erklärt nicht nur, was gemacht wurde, sondern auch warum bestimmte Entscheidungen getroffen wurden.

---

## Konfigurationsdateien

Viele Werkzeuge und Anwendungen nutzen Konfigurationsdateien.

Häufige Formate:

| Format | Nutzung                                    |
| ------ | ------------------------------------------ |
| YAML   | Docker Compose, Kubernetes, CI/CD, Ansible |
| JSON   | APIs, Webprojekte, Konfigurationen         |
| XML    | ältere Systeme, Datenaustausch             |
| INI    | einfache Konfigurationen                   |
| ENV    | Umgebungsvariablen                         |
| TOML   | moderne Projektkonfigurationen             |

Konfigurationsdateien sind wichtig, weil viele Programme damit an verschiedene Umgebungen angepasst werden.

Wichtig:

Geheime Daten wie Passwörter oder Tokens gehören nicht ungeschützt in Konfigurationsdateien im Repository.

---

## Umgebungsvariablen

Umgebungsvariablen speichern Einstellungen außerhalb des Codes.

Beispiele:

- Datenbankadresse
- Port
- Benutzername
- API-URL
- Umgebung
- Log-Level

Vorteile:

- Code bleibt gleich
- Einstellungen können je Umgebung anders sein
- sensible Werte müssen nicht direkt im Code stehen
- gut für Container und Serverumgebungen

Beispiel:

Entwicklung und Produktion können dieselbe Anwendung nutzen, aber unterschiedliche Datenbankadressen verwenden.

---

## Auswahl passender Werkzeuge

Nicht jedes Projekt braucht alle Werkzeuge.

Bei der Auswahl sollte man fragen:

- Welche Aufgabe soll gelöst werden?
- Welche Sprache passt?
- Welche Umgebung wird genutzt?
- Welche Daten werden verarbeitet?
- Welche Personen arbeiten mit?
- Muss das Projekt später betrieben werden?
- Gibt es Sicherheitsanforderungen?
- Gibt es vorhandene Standards im Unternehmen?
- Wie komplex ist das Projekt?
- Wie gut ist das Werkzeug dokumentiert?

Ein kleines Skript braucht vielleicht nur Python, VS Code, Git und README.

Eine größere Anwendung braucht zusätzlich Tests, Datenbank, CI/CD, Deployment, Monitoring und Betriebsdokumentation.

---

## Sicherheit bei Entwicklungswerkzeugen

Auch Entwicklungswerkzeuge müssen sicher genutzt werden.

Wichtige Punkte:

- keine Passwörter ins Repository schreiben
- private SSH-Schlüssel schützen
- nur vertrauenswürdige Erweiterungen installieren
- Abhängigkeiten prüfen
- Sicherheitsupdates einspielen
- Zugriffsrechte auf Repositories kontrollieren
- keine echten Kundendaten in Testprojekten nutzen
- Logs auf sensible Daten prüfen
- lokale Entwicklungsumgebung aktuell halten

Entwicklungsumgebungen können sensible Informationen enthalten.

Deshalb müssen sie genauso bewusst geschützt werden wie andere IT-Systeme.

---

## Praxisbeispiele

### Beispiel 1: Python-Skript mit Git

Ein FISI schreibt ein Python-Skript zur Logauswertung. VS Code wird als Editor genutzt, Git speichert Änderungen, eine README erklärt die Nutzung und eine virtuelle Umgebung trennt die Python-Pakete vom System.

### Beispiel 2: Datenbanktest mit Docker

Für eine Übung wird eine PostgreSQL-Datenbank als Docker-Container gestartet. Dadurch muss die Datenbank nicht direkt auf dem System installiert werden. SQL-Abfragen können in einer isolierten Testumgebung ausprobiert werden.

### Beispiel 3: Bash-Skript für Wartung

Ein Linux-Server soll regelmäßig bestimmte Logdateien prüfen. Ein Bash-Skript kombiniert Befehle wie `grep`, `find` und `journalctl`, um Fehler schneller zu erkennen.

---

## Typische Fehler

| Fehler                              | Problem                                 |
| ----------------------------------- | --------------------------------------- |
| falsche Sprache für Aufgabe wählen  | Umsetzung wird unnötig kompliziert      |
| Abhängigkeiten nicht dokumentieren  | Projekt läuft auf anderem System nicht  |
| virtuelle Umgebung vergessen        | Paketkonflikte entstehen                |
| Passwörter ins Repository schreiben | Sicherheitsrisiko                       |
| keine Versionsverwaltung nutzen     | Änderungen sind nicht nachvollziehbar   |
| Werkzeuge nicht verstehen           | Fehler werden falsch interpretiert      |
| keine Tests nutzen                  | Fehler fallen spät auf                  |
| Logs mit sensiblen Daten schreiben  | Datenschutz- und Sicherheitsrisiko      |
| alles manuell machen                | wiederkehrende Fehler und hoher Aufwand |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Programmiersprachen und Werkzeuge wichtig, weil viele Aufgaben im Betrieb automatisiert oder technisch analysiert werden müssen.

In der Praxis bedeutet das:

- Python für kleine Tools und Datenverarbeitung nutzen
- Bash für Linux-Automatisierung verwenden
- PowerShell in Windows-Umgebungen einsetzen
- SQL für Datenbankabfragen verstehen
- Git zur Versionsverwaltung nutzen
- Docker für Testumgebungen verwenden
- Logs und Konfigurationsdateien auswerten
- Entwicklungs- und Produktivumgebung unterscheiden
- sichere Repository-Nutzung beachten
- Dokumentation schreiben und pflegen

Ein guter FISI muss kein reiner Softwareentwickler sein, sollte aber genug Programmier- und Werkzeugverständnis besitzen, um Systeme automatisieren, Fehler analysieren und Softwareumgebungen betreiben zu können.

---

## Kurze Zusammenfassung

Programmiersprachen dienen dazu, Computeranweisungen genau zu beschreiben.

Wichtige Sprachen für FISI sind Python, Bash, PowerShell und SQL. Zusätzlich ist Grundwissen zu JavaScript, Java oder C# hilfreich, wenn man mit Anwendungen und Entwicklern zusammenarbeitet.

Entwicklungswerkzeuge wie VS Code, Terminal, Git, Paketmanager, virtuelle Umgebungen, Debugger, Testwerkzeuge, Datenbanktools, Docker, CI/CD und Dokumentation unterstützen den gesamten Entwicklungsprozess.

Für FISI ist dieses Kapitel wichtig, weil moderne Systemintegration ohne Skripte, Automatisierung, Datenbanken, Konfigurationsdateien und Werkzeugverständnis kaum möglich ist.
