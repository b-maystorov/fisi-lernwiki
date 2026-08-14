# 5.10 Softwareentwicklung dokumentieren

In diesem Kapitel geht es darum, Softwareentwicklung verständlich und nachvollziehbar zu dokumentieren.

Dokumentation ist ein wichtiger Teil der Softwareentwicklung. Sie erklärt, was eine Software macht, wie sie genutzt wird, wie sie installiert wird, welche Entscheidungen getroffen wurden und wie die Software später betrieben oder erweitert werden kann.

Für Fachinformatiker für Systemintegration ist Dokumentation besonders wichtig, weil Software im Betrieb nicht nur funktionieren muss. Andere Personen müssen verstehen können, wie die Software aufgebaut ist, welche Systeme beteiligt sind, wie Fehler analysiert werden und wie Änderungen durchgeführt werden.

---

## Kurz erklärt

Softwaredokumentation beschreibt eine Softwarelösung so, dass andere Personen sie verstehen, nutzen, betreiben, testen oder weiterentwickeln können.

Dazu gehören:

- Projektbeschreibung
- Anforderungen
- Installationsanleitung
- Bedienungsanleitung
- technische Dokumentation
- Projektstruktur
- Datenmodell
- Schnittstellen
- Konfiguration
- Testdokumentation
- Fehlerdokumentation
- Änderungsdokumentation
- Betriebsdokumentation
- Sicherheits- und Datenschutzinformationen

Gute Dokumentation spart Zeit, verhindert Missverständnisse und macht Software wartbarer.

---

## Warum Dokumentation wichtig ist

Ohne Dokumentation entstehen schnell Probleme.

Typische Folgen schlechter Dokumentation:

- niemand weiß, wie die Software installiert wird
- Funktionen sind unklar
- Benutzer machen Fehler
- Entwickler verstehen alten Code nicht
- Betrieb kann Fehler schwer analysieren
- Updates werden riskant
- Abhängigkeiten sind unbekannt
- Konfigurationen werden falsch gesetzt
- Wissen hängt nur an einzelnen Personen
- Übergaben dauern lange
- Sicherheitsmaßnahmen werden vergessen

Dokumentation ist deshalb nicht nur Zusatzarbeit.

Sie ist ein Teil der Qualität einer Softwarelösung.

---

## Ziel der Dokumentation

Dokumentation soll Wissen festhalten.

Eine gute Dokumentation beantwortet wichtige Fragen:

- Was macht die Software?
- Warum wurde sie erstellt?
- Wer nutzt sie?
- Welche Anforderungen erfüllt sie?
- Wie wird sie installiert?
- Wie wird sie gestartet?
- Welche Daten werden verarbeitet?
- Welche Systeme sind beteiligt?
- Welche Konfiguration ist nötig?
- Wie wird getestet?
- Wie wird ein Fehler analysiert?
- Wie wird die Software betrieben?
- Wie wird sie aktualisiert?
- Welche Einschränkungen gibt es?

Je besser diese Fragen beantwortet sind, desto einfacher ist die spätere Nutzung und Wartung.

---

## Arten von Dokumentation

Softwaredokumentation kann verschiedene Formen haben.

| Art                         | Zweck                                       |
| --------------------------- | ------------------------------------------- |
| Projektdokumentation        | beschreibt Ziel, Verlauf und Entscheidungen |
| Benutzerdokumentation       | erklärt Nutzung für Anwender                |
| technische Dokumentation    | erklärt Aufbau und Technik                  |
| Installationsanleitung      | erklärt Einrichtung und Start               |
| Betriebsdokumentation       | erklärt Betrieb, Wartung und Fehleranalyse  |
| Testdokumentation           | beschreibt Tests und Ergebnisse             |
| Schnittstellendokumentation | beschreibt Verbindungen zu anderen Systemen |
| Datenbankdokumentation      | beschreibt Tabellen, Felder und Beziehungen |
| Änderungsdokumentation      | beschreibt Änderungen an der Software       |
| Sicherheitsdokumentation    | beschreibt Schutzmaßnahmen und Risiken      |

Nicht jedes Projekt braucht jede Dokumentationsart gleich ausführlich.

Ein kleines Skript braucht vielleicht README, Nutzungshinweise und Beispiele. Eine produktive Anwendung braucht deutlich mehr.

---

## README

Eine README-Datei ist oft die erste Dokumentation in einem Repository.

Sie erklärt kurz und verständlich, worum es im Projekt geht.

Typische Inhalte einer README:

- Projektname
- kurze Beschreibung
- Ziel des Projekts
- Funktionen
- Voraussetzungen
- Installation
- Nutzung
- Beispiele
- Projektstruktur
- Konfiguration
- bekannte Einschränkungen
- Lizenz oder Hinweis
- Autor oder Kontext

Eine README sollte so geschrieben sein, dass jemand das Projekt schnell einordnen kann.

Besonders bei GitHub-Projekten ist die README sehr wichtig, weil sie direkt auf der Projektseite angezeigt wird.

---

## Beispielstruktur für eine README

Eine einfache README kann so aufgebaut sein:

```md
# Projektname

Kurze Beschreibung des Projekts.

## Ziel

Was soll das Projekt lösen?

## Funktionen

- Funktion 1
- Funktion 2
- Funktion 3

## Voraussetzungen

Welche Software wird benötigt?

## Installation

Wie wird das Projekt eingerichtet?

## Nutzung

Wie wird das Projekt gestartet oder benutzt?

## Projektstruktur

Welche Dateien und Ordner sind wichtig?

## Hinweise

Bekannte Einschränkungen oder offene Punkte.
```

Diese Struktur reicht für viele kleine Lern- oder Portfolio-Projekte aus.

---

## Projektdokumentation

Die Projektdokumentation beschreibt das Projekt als Ganzes.

Wichtige Inhalte:

- Ausgangssituation
- Problemstellung
- Zielsetzung
- Anforderungen
- Planung
- Umsetzung
- verwendete Werkzeuge
- Testdurchführung
- Ergebnis
- Probleme und Lösungen
- Bewertung
- mögliche Verbesserungen

Die Projektdokumentation ist besonders wichtig, wenn ein Projekt bewertet, übergeben oder später weitergeführt wird.

Sie zeigt nicht nur das Ergebnis, sondern auch den Weg dorthin.

---

## Technische Dokumentation

Technische Dokumentation richtet sich eher an IT-Personal, Entwickler oder Administratoren.

Sie beschreibt, wie die Software technisch aufgebaut ist.

Typische Inhalte:

- Architektur
- Projektstruktur
- verwendete Programmiersprache
- verwendete Bibliotheken
- Datenbankstruktur
- Schnittstellen
- Konfigurationsdateien
- Umgebungsvariablen
- Dienste
- Ports
- Logs
- Backup
- Deployment
- Sicherheitsmaßnahmen

Technische Dokumentation hilft besonders im Betrieb und bei der Wartung.

---

## Benutzerdokumentation

Benutzerdokumentation erklärt, wie Anwender mit der Software arbeiten.

Sie sollte einfach und praxisnah geschrieben sein.

Typische Inhalte:

- Anmeldung
- wichtige Funktionen
- Schritt-für-Schritt-Anleitungen
- Screenshots, wenn sinnvoll
- häufige Fehler
- Hinweise zur Bedienung
- Kontakt oder Supportweg

Benutzerdokumentation sollte nicht zu technisch sein.

Ein normaler Benutzer muss nicht wissen, wie die Datenbank aufgebaut ist. Er muss wissen, wie er seine Aufgabe mit der Software erledigt.

---

## Installationsanleitung

Eine Installationsanleitung beschreibt, wie die Software eingerichtet wird.

Wichtige Inhalte:

- Voraussetzungen
- benötigte Programme
- Betriebssystem
- Abhängigkeiten
- Installationsbefehle
- Konfiguration
- Datenbankeinrichtung
- Startbefehl
- Test nach Installation
- typische Fehler

Beispiel für ein Python-Projekt:

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python3 main.py
```

Eine gute Installationsanleitung verhindert, dass andere Personen lange raten müssen, wie das Projekt gestartet wird.

---

## Betriebsdokumentation

Betriebsdokumentation beschreibt, wie eine Software im laufenden Betrieb verwaltet wird.

Wichtige Inhalte:

- wo läuft die Software?
- welcher Dienstname wird genutzt?
- welche Ports werden verwendet?
- wo liegen Konfigurationsdateien?
- wo liegen Logs?
- wie wird die Software gestartet?
- wie wird sie gestoppt?
- wie werden Updates eingespielt?
- wie werden Backups erstellt?
- wie wird ein Restore durchgeführt?
- wie wird Monitoring geprüft?
- wer ist verantwortlich?

Diese Dokumentation ist besonders wichtig für FISI, weil Betrieb, Wartung und Fehleranalyse typische Aufgaben in der Systemintegration sind.

---

## Dokumentation der Projektstruktur

Eine Projektstruktur zeigt, welche Dateien und Ordner wofür genutzt werden.

Beispiel:

```text
python-project/
├── README.md
├── main.py
├── requirements.txt
├── .gitignore
├── src/
│   └── helper.py
├── tests/
│   └── test_helper.py
└── docs/
    └── installation.md
```

Dazu sollte erklärt werden:

| Datei / Ordner     | Zweck                            |
| ------------------ | -------------------------------- |
| `README.md`        | Projektüberblick                 |
| `main.py`          | Startpunkt des Programms         |
| `requirements.txt` | Python-Abhängigkeiten            |
| `.gitignore`       | Dateien, die Git ignorieren soll |
| `src/`             | Programmlogik                    |
| `tests/`           | Tests                            |
| `docs/`            | zusätzliche Dokumentation        |

Eine klare Struktur macht ein Projekt leichter verständlich.

---

## Anforderungen dokumentieren

Anforderungen sollten schriftlich festgehalten werden.

Wichtige Punkte:

- funktionale Anforderungen
- nicht-funktionale Anforderungen
- Muss-Anforderungen
- Soll-Anforderungen
- Kann-Anforderungen
- Benutzerrollen
- Akzeptanzkriterien
- offene Fragen
- Änderungen an Anforderungen

Beispiel:

| ID    | Anforderung                           | Kategorie        | Priorität |
| ----- | ------------------------------------- | ---------------- | --------- |
| A-001 | Benutzer kann Ticket erstellen        | funktional       | Muss      |
| A-002 | Ticket erhält eindeutige Nummer       | funktional       | Muss      |
| A-003 | Anwendung lädt in unter zwei Sekunden | nicht-funktional | Soll      |
| A-004 | Admin kann Benutzer verwalten         | funktional       | Kann      |

Dokumentierte Anforderungen helfen später beim Testen und bei der Abnahme.

---

## Entscheidungen dokumentieren

In Projekten werden viele Entscheidungen getroffen.

Beispiele:

- Warum wurde Python genutzt?
- Warum wird SQLite statt PostgreSQL verwendet?
- Warum läuft die Anwendung als Container?
- Warum wurde eine bestimmte Projektstruktur gewählt?
- Warum wird eine bestimmte Schnittstelle genutzt?
- Warum wird eine Funktion erst später umgesetzt?

Solche Entscheidungen sollten kurz dokumentiert werden.

Das hilft später, weil man nicht erneut überlegen muss, warum etwas so gebaut wurde.

---

## Datenbankdokumentation

Wenn eine Software eine Datenbank nutzt, sollte die Datenbank dokumentiert werden.

Wichtige Inhalte:

- Zweck der Datenbank
- Tabellen
- Spalten
- Datentypen
- Primärschlüssel
- Fremdschlüssel
- Beziehungen
- Constraints
- wichtige SQL-Abfragen
- Benutzerrechte
- Backup und Restore
- besondere Regeln

Beispiel:

| Tabelle     | Zweck                    |
| ----------- | ------------------------ |
| `users`     | speichert Benutzer       |
| `tickets`   | speichert Supporttickets |
| `devices`   | speichert Geräte         |
| `locations` | speichert Standorte      |

Ohne Datenbankdokumentation wird es später schwer, Datenstruktur und Zusammenhänge zu verstehen.

---

## Schnittstellendokumentation

Schnittstellen verbinden Software mit anderen Systemen.

Eine Schnittstellendokumentation sollte beschreiben:

- beteiligte Systeme
- Zweck der Schnittstelle
- Datenformat
- Authentifizierung
- Endpunkte oder Pfade
- Eingabedaten
- Ausgabedaten
- Fehlermeldungen
- Sicherheitsmaßnahmen
- Verantwortlichkeiten

Beispiele für Schnittstellen:

- REST-API
- Datenbankverbindung
- CSV-Import
- JSON-Export
- E-Mail-Versand
- LDAP-Anbindung
- Cloud-Dienst

Schnittstellen müssen gut dokumentiert sein, weil Fehler dort oft mehrere Systeme betreffen.

---

## Konfiguration dokumentieren

Viele Anwendungen benötigen Konfiguration.

Beispiele:

- Port
- Datenbankadresse
- Dateipfade
- API-URL
- Log-Level
- Benutzerrollen
- Umgebungsvariablen
- Speicherorte
- Backup-Pfade

Wichtig:

Geheime Werte dürfen nicht direkt in öffentlicher Dokumentation stehen.

Nicht dokumentieren:

- echte Passwörter
- echte API-Schlüssel
- private Tokens
- private SSH-Schlüssel

Besser:

```text
DB_HOST=localhost
DB_PORT=5432
DB_USER=example_user
DB_PASSWORD=<hier-passwort-eintragen>
```

So sieht man, welche Werte benötigt werden, ohne echte Geheimnisse zu veröffentlichen.

---

## Testdokumentation

Testdokumentation beschreibt, welche Tests durchgeführt wurden.

Typische Inhalte:

- Testfall-ID
- Beschreibung
- Voraussetzung
- Eingabe
- erwartetes Ergebnis
- tatsächliches Ergebnis
- Status
- Tester
- Datum
- Bemerkungen

Beispiel:

| ID    | Testfall                    | Erwartet           | Ergebnis           | Status         |
| ----- | --------------------------- | ------------------ | ------------------ | -------------- |
| T-001 | Login mit gültigen Daten    | Login erfolgreich  | Login erfolgreich  | bestanden      |
| T-002 | Login mit falschem Passwort | Zugriff verweigert | Zugriff verweigert | bestanden      |
| T-003 | Ticket ohne Titel speichern | Fehlermeldung      | Ticket gespeichert | fehlgeschlagen |

Testdokumentation zeigt, ob Anforderungen wirklich geprüft wurden.

---

## Fehlerdokumentation

Fehler sollten nachvollziehbar dokumentiert werden.

Eine gute Fehlerdokumentation enthält:

- kurze Beschreibung
- Schritte zur Reproduktion
- erwartetes Ergebnis
- tatsächliches Ergebnis
- Fehlermeldung
- betroffene Version
- betroffene Umgebung
- Schweregrad
- Status
- Lösung
- Testergebnis nach der Behebung

Schlecht:

> Speichern geht nicht.

Besser:

> Beim Speichern eines Tickets ohne Titel wird kein Fehler angezeigt. Das Ticket wird trotzdem gespeichert. Erwartet wäre eine Fehlermeldung, weil der Titel ein Pflichtfeld ist.

Gute Fehlerdokumentation spart viel Zeit bei Analyse und Behebung.

---

## Änderungsdokumentation

Änderungsdokumentation beschreibt, was sich an einer Software geändert hat.

Das kann über Git-Commits, Changelog oder Release Notes passieren.

Beispiele:

```text
Add ticket search function
Fix login validation
Update database schema
Improve error messages
Add installation guide
```

Eine gute Änderungsdokumentation hilft zu verstehen:

- was geändert wurde
- wann es geändert wurde
- warum es geändert wurde
- welche Version betroffen ist
- ob besondere Hinweise nötig sind

Git ist dafür sehr wichtig, ersetzt aber nicht immer eine verständliche Zusammenfassung für Benutzer oder Betrieb.

---

## Changelog

Ein Changelog beschreibt Änderungen zwischen Versionen.

Beispiel:

```md
# Changelog

## Version 1.1.0

- Suchfunktion für Tickets ergänzt
- Fehlermeldungen verbessert
- README aktualisiert

## Version 1.0.0

- erste Version der Anwendung
- Tickets erstellen und anzeigen
- einfache Benutzerverwaltung
```

Ein Changelog ist besonders nützlich, wenn eine Software mehrere Versionen hat.

Benutzer und Administratoren können sehen, was sich geändert hat.

---

## Kommentare im Code

Kommentare erklären Code direkt an der Stelle, an der er steht.

Gute Kommentare erklären nicht jeden einzelnen Befehl, sondern wichtige Entscheidungen.

Schlecht:

```python
# Zahl wird um 1 erhöht
counter = counter + 1
```

Besser:

```python
# Nach drei fehlgeschlagenen Versuchen wird der Login blockiert
failed_attempts = failed_attempts + 1
```

Kommentare sollten helfen, die Absicht zu verstehen.

Zu viele unnötige Kommentare können Code unübersichtlich machen.

---

## Selbsterklärender Code

Gute Namen reduzieren den Bedarf an Kommentaren.

Schlecht:

```python
x = 5
y = 10
z = x + y
```

Besser:

```python
ticket_count = 5
new_tickets = 10
total_tickets = ticket_count + new_tickets
```

Selbsterklärender Code ist leichter zu lesen und zu warten.

Dokumentation beginnt also schon bei guten Namen und klarer Struktur.

---

## Dokumentation mit Markdown

Markdown ist ein einfaches Format für Dokumentation.

Es wird häufig genutzt für:

- README-Dateien
- GitHub-Dokumentation
- Wikis
- Notizen
- technische Anleitungen
- Projektbeschreibungen

Wichtige Markdown-Elemente:

````md
# Überschrift 1

## Überschrift 2

Normaler Text

- Liste
- Liste

```bash
echo "Beispiel"
```
````

| Spalte 1 | Spalte 2 |
| -------- | -------- |
| Wert     | Wert     |

````

Markdown ist gut lesbar und funktioniert direkt in GitHub.

---

## Dokumentation in GitHub

GitHub eignet sich gut für Projektdokumentation.

Möglichkeiten:

- README im Repository
- Markdown-Dateien im Ordner `docs/`
- Wiki-Bereich
- Issues für Aufgaben und Fehler
- Pull Requests für Änderungen
- Releases für Versionen
- Commit-Verlauf für Änderungen

Für Portfolio-Projekte ist GitHub-Dokumentation besonders wichtig.

Sie zeigt nicht nur Code, sondern auch Arbeitsweise, Struktur und Verständnis.

---

## Dokumentation aktuell halten

Dokumentation muss zur Software passen.

Veraltete Dokumentation kann schlimmer sein als gar keine Dokumentation, weil sie falsche Informationen liefert.

Typische Situationen, in denen Dokumentation angepasst werden muss:

- neue Funktion wurde ergänzt
- Funktion wurde entfernt
- Installationsschritte ändern sich
- neue Abhängigkeit wurde hinzugefügt
- Datenbankstruktur wurde geändert
- Konfiguration wurde angepasst
- neuer Port wird genutzt
- neues Deployment-Verfahren wird verwendet
- bekannte Fehler wurden behoben

Dokumentation sollte Teil der Änderung sein, nicht eine Aufgabe irgendwann später.

---

## Zielgruppe beachten

Dokumentation muss zur Zielgruppe passen.

| Zielgruppe | braucht eher |
|---|---|
| Benutzer | einfache Bedienungsanleitung |
| Entwickler | Codeaufbau, Module, Tests |
| Administratoren | Installation, Betrieb, Logs, Backup |
| Projektleitung | Ziel, Status, Risiken |
| Prüfer | Anforderungen, Umsetzung, Ergebnis |
| Support | Fehlerbilder, Lösungen, bekannte Probleme |

Eine technische Anleitung für Administratoren sieht anders aus als eine Bedienungsanleitung für normale Benutzer.

Gute Dokumentation erklärt genau das, was die Zielgruppe braucht.

---

## Gute Dokumentation schreiben

Gute Dokumentation sollte:

- klar sein
- aktuell sein
- vollständig genug sein
- nicht unnötig kompliziert sein
- praktische Beispiele enthalten
- wichtige Befehle zeigen
- Voraussetzungen nennen
- Fehlerquellen erwähnen
- verständliche Überschriften nutzen
- private Daten vermeiden
- nachvollziehbar strukturiert sein

Dokumentation muss nicht perfekt klingen.

Sie muss nützlich sein.

---

## Was nicht in öffentliche Dokumentation gehört

In öffentliche Repositories oder Dokumentationen gehören keine sensiblen Daten.

Nicht veröffentlichen:

- Passwörter
- API-Schlüssel
- private SSH-Schlüssel
- echte Kundendaten
- echte Personaldaten
- interne IP-Pläne
- interne Tickets
- private Screenshots
- vertrauliche Projektinformationen
- geheime URLs
- Zugangsdaten
- Datenbankdumps mit echten Daten

Für öffentliche Beispiele sollten Platzhalter oder künstliche Daten genutzt werden.

Beispiel:

```text
username: example_user
password: <password-placeholder>
server: example.local
````

Das wirkt professioneller und schützt private Informationen.

---

## Dokumentation und Datenschutz

Bei Dokumentation muss Datenschutz beachtet werden.

Besonders kritisch sind:

- Screenshots mit echten Namen
- Logauszüge mit IP-Adressen oder Benutzernamen
- Datenbankbeispiele mit echten Personen
- Supportfälle mit Kundendaten
- E-Mails oder Chatverläufe
- Bewerbungsdaten
- Personaldaten

Wenn Beispiele nötig sind, sollten sie anonymisiert oder künstlich erstellt werden.

Für Lern- und Portfolio-Projekte sind Beispieldaten meistens völlig ausreichend.

---

## Dokumentation und Sicherheit

Dokumentation kann selbst sicherheitsrelevant sein.

Beispiele:

- Netzpläne zeigen Angriffsflächen
- Admin-Anleitungen zeigen kritische Systeme
- Konfigurationsbeispiele enthalten Zugangsdaten
- Logs zeigen interne Strukturen
- Fehlermeldungen verraten technische Details

Deshalb muss entschieden werden, welche Dokumentation öffentlich ist und welche intern bleibt.

Öffentliche Dokumentation sollte fachlich gut sein, aber keine vertraulichen Details verraten.

---

## Dokumentation im Projektverlauf

Dokumentation sollte während des Projekts entstehen.

Sinnvolle Reihenfolge:

1. Ziel und Ausgangssituation dokumentieren
2. Anforderungen festhalten
3. Planung dokumentieren
4. Umsetzungsschritte notieren
5. Tests dokumentieren
6. Fehler und Lösungen festhalten
7. Installation und Nutzung beschreiben
8. Ergebnis bewerten
9. offene Punkte notieren

Wer alles erst am Ende schreibt, vergisst oft wichtige Entscheidungen.

---

## Dokumentation für Übergabe

Bei einer Übergabe muss eine andere Person das Projekt übernehmen können.

Wichtige Inhalte:

- Zweck der Software
- aktueller Stand
- Installation
- Start und Stopp
- Konfiguration
- Benutzerrechte
- Datenbank
- Backup und Restore
- Logs
- typische Fehler
- offene Punkte
- Ansprechpartner
- wichtige Dateien
- bekannte Risiken

Eine gute Übergabedokumentation reduziert Abhängigkeit von einzelnen Personen.

---

## Dokumentation für Fehleranalyse

Für Fehleranalyse sind bestimmte Informationen besonders hilfreich.

Dazu gehören:

- Dienstname
- Logpfade
- Konfigurationsdateien
- Ports
- Datenbankverbindung
- Abhängigkeiten
- Startbefehl
- Neustartbefehl
- letzte Änderungen
- bekannte Fehler
- Prüfkommandos

Beispiel:

```bash
systemctl status app.service
journalctl -u app.service
docker logs app-container
docker compose ps
```

Solche Hinweise helfen dem Betrieb, Fehler schneller zu finden.

---

## Dokumentation von Befehlen

Wenn Befehle dokumentiert werden, sollten sie korrekt und vollständig sein.

Schlecht:

```text
Projekt starten
```

Besser:

```bash
cd ~/project
source venv/bin/activate
python3 main.py
```

Noch besser ist eine kurze Erklärung dazu:

| Befehl                     | Bedeutung                     |
| -------------------------- | ----------------------------- |
| `cd ~/project`             | in den Projektordner wechseln |
| `source venv/bin/activate` | virtuelle Umgebung aktivieren |
| `python3 main.py`          | Programm starten              |

Gerade bei Lernprojekten ist das sehr hilfreich.

---

## Dokumentation von Grenzen

Eine gute Dokumentation sagt auch, was eine Software nicht kann.

Beispiele:

- aktuell nur lokale Nutzung
- keine Benutzerverwaltung vorhanden
- keine Datenbankanbindung
- nur Testdaten enthalten
- keine produktive Sicherheitsprüfung
- keine automatische Installation
- keine Weboberfläche
- keine Mehrbenutzerfunktion

Das ist nicht schlecht.

Es zeigt ehrlich, welchen Stand das Projekt hat und was später verbessert werden könnte.

---

## Versionierung der Dokumentation

Dokumentation sollte zusammen mit dem Projekt versioniert werden.

Wenn Code in Git liegt, sollte wichtige Dokumentation ebenfalls im Repository liegen.

Vorteile:

- Änderungen sind nachvollziehbar
- Dokumentation passt zum Projektstand
- alte Versionen bleiben sichtbar
- Team kann gemeinsam bearbeiten
- Dokumentation kann reviewed werden

Wenn Code und Dokumentation getrennt gepflegt werden, entstehen leichter Widersprüche.

---

## Praxisbeispiele

### Beispiel 1: README für Python-Skript

Ein Python-Skript wertet Logdateien aus. Die README erklärt, was das Skript macht, welche Python-Version nötig ist, wie es gestartet wird und welche Datei als Eingabe erwartet wird.

### Beispiel 2: Installationsanleitung für Docker-Projekt

Ein kleines Webprojekt nutzt Docker Compose. Die Dokumentation zeigt, wie Container gestartet werden, welche Ports verwendet werden und wo Daten gespeichert werden.

### Beispiel 3: Fehlerdokumentation

Eine Anwendung startet nicht, weil eine Umgebungsvariable fehlt. In der Fehlerdokumentation stehen Fehlermeldung, Ursache, Lösung und Test nach der Änderung.

---

## Typische Fehler

| Fehler                                             | Problem                                              |
| -------------------------------------------------- | ---------------------------------------------------- |
| keine README schreiben                             | Projekt ist schwer verständlich                      |
| Dokumentation erst am Ende schreiben               | wichtige Entscheidungen werden vergessen             |
| Installationsschritte unvollständig                | andere können Projekt nicht starten                  |
| echte Daten in Beispielen nutzen                   | Datenschutz- und Sicherheitsrisiko                   |
| Passwörter dokumentieren                           | hohes Sicherheitsrisiko                              |
| Dokumentation nicht aktualisieren                  | falsche Informationen entstehen                      |
| Zielgruppe ignorieren                              | Dokumentation ist zu technisch oder zu oberflächlich |
| nur Code kommentieren, aber keine Nutzung erklären | Anwender und Betrieb verstehen das Projekt nicht     |
| Fehler nicht dokumentieren                         | gleiche Probleme werden wiederholt                   |
| keine Grenzen des Projekts nennen                  | falsche Erwartungen entstehen                        |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Dokumentation ein zentraler Bestandteil der Arbeit.

In der Praxis bedeutet das:

- Installationsschritte dokumentieren
- Konfigurationen erklären
- Betriebsinformationen festhalten
- Logs und Fehleranalyse beschreiben
- Backup- und Restore-Abläufe dokumentieren
- Schnittstellen und Datenbanken beschreiben
- Änderungen nachvollziehbar machen
- sensible Daten aus Dokumentation entfernen
- Übergaben vorbereiten
- GitHub-Projekte verständlich darstellen

Ein guter FISI baut nicht nur Systeme, sondern dokumentiert sie so, dass andere sie verstehen, betreiben und sicher weiterführen können.

---

## Kurze Zusammenfassung

Softwaredokumentation beschreibt, wie eine Software genutzt, installiert, betrieben, getestet, gewartet und weiterentwickelt wird.

Wichtige Dokumentationsarten sind README, Projektdokumentation, technische Dokumentation, Benutzerdokumentation, Installationsanleitung, Betriebsdokumentation, Testdokumentation, Fehlerdokumentation, Änderungsdokumentation, Datenbankdokumentation und Schnittstellendokumentation.

Gute Dokumentation ist klar, aktuell, zielgruppengerecht und frei von sensiblen Daten.

Für FISI ist dieses Kapitel wichtig, weil Software im Betrieb nur zuverlässig betreut werden kann, wenn Aufbau, Konfiguration, Fehleranalyse, Sicherheit und Wartung nachvollziehbar dokumentiert sind.
