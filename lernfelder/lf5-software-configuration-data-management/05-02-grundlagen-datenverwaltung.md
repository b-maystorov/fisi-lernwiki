# 5.2 Grundlagen der Datenverwaltung

In diesem Kapitel geht es um die Grundlagen der Datenverwaltung.

Daten sind ein zentraler Bestandteil fast jeder IT-Umgebung. Benutzerkonten, Kundendaten, Rechnungen, Logdateien, Konfigurationsdateien, Inventarlisten, Supporttickets und Messwerte müssen gespeichert, verarbeitet, gesichert und wiedergefunden werden können.

Für Fachinformatiker für Systemintegration ist Datenverwaltung wichtig, weil viele Systeme nur dann zuverlässig funktionieren, wenn Daten korrekt strukturiert, geschützt, gesichert und nachvollziehbar verwaltet werden.

---

## Kurz erklärt

Datenverwaltung bedeutet, Daten sinnvoll zu erfassen, zu speichern, zu ändern, zu schützen, zu sichern und wieder bereitzustellen.

Dazu gehören:

- Daten erfassen
- Daten strukturieren
- Daten speichern
- Daten ändern
- Daten suchen
- Daten löschen
- Daten sichern
- Daten wiederherstellen
- Zugriffe kontrollieren
- Datenqualität prüfen
- Datenschutz beachten
- Dokumentation pflegen

Datenverwaltung ist nicht nur ein Datenbankthema. Auch Dateien, Tabellen, Logdateien, Konfigurationsdateien und Backups gehören dazu.

---

## Was sind Daten?

Daten sind gespeicherte Informationen, die von Menschen oder Maschinen verarbeitet werden können.

Beispiele:

- Namen
- Zahlen
- Adressen
- E-Mail-Adressen
- Kundennummern
- Preise
- Rechnungen
- Bestellungen
- Passwörter
- Logeinträge
- IP-Adressen
- Sensordaten
- Konfigurationen
- Dateien

Daten allein sind oft nur einzelne Werte. Erst durch Zusammenhang und Bedeutung werden daraus nutzbare Informationen.

Beispiel:

Der Wert `42` ist nur eine Zahl.
Wenn bekannt ist, dass `42` die Anzahl offener Supporttickets ist, wird daraus eine Information.

---

## Daten und Informationen

Daten und Informationen hängen zusammen, sind aber nicht exakt dasselbe.

| Begriff       | Bedeutung                                                               |
| ------------- | ----------------------------------------------------------------------- |
| Daten         | einzelne Werte oder Fakten                                              |
| Informationen | Daten mit Bedeutung und Zusammenhang                                    |
| Wissen        | verstandene Informationen, die für Entscheidungen genutzt werden können |

Beispiel:

| Ebene       | Beispiel                                                                       |
| ----------- | ------------------------------------------------------------------------------ |
| Daten       | `192.168.10.25`                                                                |
| Information | IP-Adresse eines Arbeitsplatz-PCs                                              |
| Wissen      | dieser Client befindet sich im Clientnetz und nutzt das Gateway `192.168.10.1` |

In der IT werden Daten gesammelt und verarbeitet, damit daraus nutzbare Informationen entstehen.

---

## Warum Datenverwaltung wichtig ist

Ohne gute Datenverwaltung entstehen schnell Probleme.

Typische Probleme:

- Daten sind doppelt vorhanden
- Daten sind veraltet
- Daten sind falsch
- Daten fehlen
- Daten liegen an unsicheren Orten
- niemand weiß, welche Version aktuell ist
- Zugriffsrechte sind unklar
- Backups fehlen
- Daten können nicht wiederhergestellt werden
- personenbezogene Daten werden falsch behandelt
- Dateien werden unstrukturiert gespeichert

Gute Datenverwaltung sorgt dafür, dass Daten zuverlässig, sicher und nachvollziehbar genutzt werden können.

---

## Datenarten

Daten können in verschiedene Arten eingeteilt werden.

| Datenart               | Beispiele                                 |
| ---------------------- | ----------------------------------------- |
| Stammdaten             | Kunden, Benutzer, Produkte, Geräte        |
| Bewegungsdaten         | Bestellungen, Buchungen, Tickets, Logins  |
| Bestandsdaten          | Lagerbestand, Inventar, Kontostand        |
| Konfigurationsdaten    | Systemeinstellungen, Netzwerkparameter    |
| Protokolldaten         | Logs, Ereignisse, Fehlermeldungen         |
| Metadaten              | Dateigröße, Erstelldatum, Besitzer        |
| personenbezogene Daten | Name, Adresse, E-Mail, Personalnummer     |
| sensible Daten         | Gesundheitsdaten, Passwörter, Finanzdaten |

Diese Einteilung hilft zu verstehen, wie Daten genutzt und geschützt werden müssen.

---

## Stammdaten

Stammdaten sind grundlegende Daten, die über längere Zeit relativ stabil bleiben.

Beispiele:

- Kundendaten
- Lieferantendaten
- Benutzerdaten
- Produktdaten
- Gerätedaten
- Standortdaten
- Abteilungsdaten

Stammdaten werden oft von vielen Prozessen genutzt.

Wenn Stammdaten falsch sind, können viele andere Abläufe betroffen sein.

Beispiel:

Wenn die Adresse eines Kunden falsch gespeichert ist, können Rechnungen, Lieferungen oder Verträge falsch verarbeitet werden.

---

## Bewegungsdaten

Bewegungsdaten entstehen durch Vorgänge oder Ereignisse.

Beispiele:

- Bestellungen
- Rechnungen
- Zahlungen
- Supporttickets
- Login-Versuche
- Buchungen
- Lagerbewegungen
- Messwerte
- Dateiänderungen

Bewegungsdaten ändern sich häufiger als Stammdaten.

Sie zeigen, was passiert ist oder gerade passiert.

Beispiel:

Ein Benutzerkonto ist Stammdaten.
Ein Login dieses Benutzers ist Bewegungsdaten.

---

## Konfigurationsdaten

Konfigurationsdaten beschreiben, wie Systeme eingestellt sind.

Beispiele:

- IP-Adresse
- DNS-Server
- Firewall-Regeln
- Benutzerrechte
- Softwareeinstellungen
- Datenbankverbindungen
- Serverparameter
- Docker-Compose-Dateien
- YAML-Dateien
- SSH-Konfiguration
- Netzwerkeinstellungen

Konfigurationsdaten sind besonders wichtig im Bereich Systemintegration.

Falsche Konfigurationsdaten können dazu führen, dass Systeme nicht funktionieren oder unsicher werden.

---

## Protokolldaten

Protokolldaten entstehen, wenn Systeme Ereignisse aufzeichnen.

Beispiele:

- Systemlogs
- Anmeldeversuche
- Fehlermeldungen
- Firewall-Logs
- Webserver-Logs
- Backup-Logs
- Datenbank-Logs
- Netzwerkereignisse
- Sicherheitsmeldungen

Logs helfen bei:

- Fehlersuche
- Sicherheitsanalyse
- Nachvollziehbarkeit
- Monitoring
- Audits
- Performanceanalyse

Protokolldaten können sehr wichtig sein, enthalten aber manchmal auch personenbezogene oder sicherheitsrelevante Informationen.

---

## Personenbezogene Daten

Personenbezogene Daten sind Informationen, die sich auf eine bestimmte Person beziehen.

Beispiele:

- Name
- Adresse
- Telefonnummer
- E-Mail-Adresse
- Kundennummer
- Personalnummer
- Benutzername
- IP-Adresse in bestimmten Zusammenhängen
- Bewerbungsdaten
- Gehaltsdaten
- Gesundheitsdaten

Personenbezogene Daten müssen besonders sorgfältig behandelt werden.

Wichtige Punkte:

- nur notwendige Daten speichern
- Zugriffe begrenzen
- Daten schützen
- Löschfristen beachten
- Daten nicht unkontrolliert kopieren
- Datenschutzvorgaben einhalten
- sichere Speicherung und Übertragung nutzen

Für FISI ist wichtig, personenbezogene Daten nicht einfach in Testdateien, Screenshots, Logs oder öffentliche Repositories zu übernehmen.

---

## Datenstrukturen

Daten müssen strukturiert werden, damit sie sinnvoll verarbeitet werden können.

Beispiele für Datenstrukturen:

| Struktur       | Beispiel                                       |
| -------------- | ---------------------------------------------- |
| einfache Datei | Textdatei mit Notizen                          |
| Tabelle        | Excel-Liste oder Datenbanktabelle              |
| Ordnerstruktur | Projektordner mit Dokumenten                   |
| JSON           | strukturierte Daten für Anwendungen            |
| YAML           | Konfigurationen                                |
| XML            | strukturierter Datenaustausch                  |
| Datenbank      | relationale oder nicht-relationale Speicherung |

Die passende Struktur hängt davon ab, wie die Daten genutzt werden sollen.

Eine kleine Liste kann in einer Tabelle reichen. Für viele Benutzer, große Datenmengen und gleichzeitige Zugriffe ist eine Datenbank oft besser.

---

## Dateien als Datenspeicher

Dateien sind eine einfache Form der Datenspeicherung.

Beispiele:

- `.txt`
- `.csv`
- `.json`
- `.yaml`
- `.xml`
- `.log`
- `.md`
- `.xlsx`
- `.pdf`

Dateien sind einfach zu erstellen und zu lesen, haben aber Grenzen.

Vorteile:

- einfach
- schnell nutzbar
- gut für kleine Datenmengen
- gut für Konfigurationen oder Exporte
- leicht zu sichern

Nachteile:

- gleichzeitige Bearbeitung schwierig
- Rechteverwaltung manchmal unklar
- Suche kann aufwendig sein
- Datenqualität schwer kontrollierbar
- keine starken Beziehungen zwischen Daten
- bei großen Datenmengen unpraktisch

---

## CSV-Dateien

CSV bedeutet **Comma-Separated Values**.

Eine CSV-Datei speichert tabellarische Daten als Text.

Beispiel:

```csv
id,name,email
1,Ali,ali@example.com
2,Maria,maria@example.com
```

CSV-Dateien werden häufig genutzt für:

- Datenexport
- Datenimport
- einfache Tabellen
- Austausch zwischen Systemen
- Logauswertungen
- Listen und Berichte

Vorteile:

- einfaches Format
- mit vielen Programmen lesbar
- gut für Import und Export
- kann mit Skripten verarbeitet werden

Nachteile:

- keine festen Datentypen
- keine eingebauten Beziehungen
- keine Benutzerrechte
- Trennzeichen können Probleme machen
- große Dateien werden unübersichtlich

CSV ist praktisch, aber keine vollständige Datenbank.

---

## JSON

JSON bedeutet **JavaScript Object Notation**.

JSON wird häufig für strukturierte Daten und Schnittstellen genutzt.

Beispiel:

```json
{
  "id": 1,
  "name": "Ali",
  "email": "ali@example.com",
  "active": true
}
```

JSON wird oft genutzt bei:

- APIs
- Webanwendungen
- Konfigurationsdateien
- Datenaustausch
- Automatisierung
- modernen Softwareprojekten

Vorteile:

- gut lesbar
- strukturiert
- unterstützt Listen und Objekte
- weit verbreitet
- gut für Programmiersprachen geeignet

JSON ist besonders wichtig, wenn Systeme Daten über Schnittstellen austauschen.

---

## YAML

YAML wird häufig für Konfigurationen genutzt.

Beispiel:

```yaml
server:
  host: localhost
  port: 8080
  debug: true
```

YAML wird oft verwendet bei:

- Docker Compose
- Kubernetes
- CI/CD-Pipelines
- Ansible
- Cloud-Konfigurationen
- Autoinstall-Dateien
- Projektkonfigurationen

Vorteile:

- gut lesbar
- übersichtlich
- beliebt für Konfigurationen

Wichtig:

YAML ist empfindlich bei Einrückungen. Leerzeichen und Struktur müssen korrekt sein.

Ein kleiner Einrückungsfehler kann dazu führen, dass eine Konfiguration nicht funktioniert.

---

## Tabellen

Tabellen ordnen Daten in Zeilen und Spalten.

Beispiel:

|  id | name  | rolle    |
| --: | ----- | -------- |
|   1 | Ali   | Admin    |
|   2 | Maria | Benutzer |

Tabellen sind leicht verständlich und werden häufig genutzt.

Beispiele:

- Excel-Listen
- Inventarlisten
- Datenbanktabellen
- Benutzerlisten
- Gerätelisten
- Berichte

Tabellen sind gut, wenn Daten regelmäßig die gleiche Struktur haben.

Wenn Daten aber stark miteinander verknüpft sind oder von vielen Benutzern gleichzeitig genutzt werden, ist eine Datenbank meistens besser geeignet.

---

## Datenbanken

Eine Datenbank ist ein System zur strukturierten Speicherung und Verwaltung von Daten.

Datenbanken ermöglichen:

- Daten speichern
- Daten suchen
- Daten ändern
- Daten löschen
- Zugriffe kontrollieren
- Beziehungen abbilden
- mehrere Benutzer gleichzeitig unterstützen
- Daten konsistent halten
- Abfragen durchführen
- Backups erstellen

Datenbanken sind besonders wichtig, wenn Daten dauerhaft, strukturiert und zuverlässig gespeichert werden müssen.

---

## Datenbankmanagementsystem

Ein Datenbankmanagementsystem, kurz DBMS, ist die Software, die Datenbanken verwaltet.

Beispiele:

- PostgreSQL
- MySQL
- MariaDB
- SQLite
- Microsoft SQL Server
- Oracle Database

Ein DBMS übernimmt Aufgaben wie:

- Daten speichern
- Abfragen verarbeiten
- Benutzerrechte verwalten
- Transaktionen steuern
- Datenintegrität sichern
- Backups ermöglichen
- gleichzeitige Zugriffe verwalten

Die Datenbank ist der gespeicherte Datenbestand.
Das DBMS ist die Software, die diesen Datenbestand verwaltet.

---

## Relationale Datenbanken

Relationale Datenbanken speichern Daten in Tabellen.

Die Tabellen können über Schlüssel miteinander verbunden sein.

Wichtige Begriffe:

| Begriff         | Bedeutung                                |
| --------------- | ---------------------------------------- |
| Tabelle         | Sammlung gleichartiger Datensätze        |
| Zeile           | einzelner Datensatz                      |
| Spalte          | Eigenschaft eines Datensatzes            |
| Primärschlüssel | eindeutige Kennung eines Datensatzes     |
| Fremdschlüssel  | Verweis auf Datensatz in anderer Tabelle |
| Beziehung       | Verbindung zwischen Tabellen             |

Relationale Datenbanken sind sehr verbreitet und werden häufig mit SQL genutzt.

---

## Beispiel einer relationalen Struktur

Eine einfache Inventarverwaltung könnte zwei Tabellen haben.

Tabelle `geraete`:

|  id | hostname | typ     |
| --: | -------- | ------- |
|   1 | pc-001   | Laptop  |
|   2 | pc-002   | Desktop |

Tabelle `benutzer`:

|  id | name  | geraet_id |
| --: | ----- | --------: |
|   1 | Ali   |         1 |
|   2 | Maria |         2 |

Die Spalte `geraet_id` verweist auf ein Gerät.

Dadurch kann gespeichert werden, welcher Benutzer welches Gerät nutzt.

---

## SQL

SQL bedeutet **Structured Query Language**.

SQL wird genutzt, um mit relationalen Datenbanken zu arbeiten.

Typische SQL-Aufgaben:

- Daten abfragen
- Daten einfügen
- Daten ändern
- Daten löschen
- Tabellen erstellen
- Beziehungen definieren
- Benutzerrechte setzen

Beispiele für SQL-Befehle:

| Befehl       | Aufgabe                 |
| ------------ | ----------------------- |
| SELECT       | Daten abfragen          |
| INSERT       | neue Daten einfügen     |
| UPDATE       | vorhandene Daten ändern |
| DELETE       | Daten löschen           |
| CREATE TABLE | Tabelle erstellen       |
| ALTER TABLE  | Tabelle ändern          |
| DROP TABLE   | Tabelle löschen         |

SQL ist wichtig, weil viele Anwendungen ihre Daten in relationalen Datenbanken speichern.

---

## CRUD-Prinzip

CRUD beschreibt die vier Grundoperationen der Datenverwaltung.

| Buchstabe | Bedeutung | SQL-Beispiel |
| --------- | --------- | ------------ |
| C         | Create    | INSERT       |
| R         | Read      | SELECT       |
| U         | Update    | UPDATE       |
| D         | Delete    | DELETE       |

Fast jede Anwendung mit Daten nutzt diese Grundoperationen.

Beispiel:

Ein Ticketsystem muss Tickets erstellen, anzeigen, ändern und löschen oder schließen können.

---

## Datenqualität

Datenqualität beschreibt, ob Daten für ihren Zweck geeignet sind.

Wichtige Kriterien:

| Kriterium    | Bedeutung                                 |
| ------------ | ----------------------------------------- |
| korrekt      | Daten stimmen fachlich                    |
| vollständig  | wichtige Werte fehlen nicht               |
| aktuell      | Daten sind nicht veraltet                 |
| eindeutig    | keine unnötigen Dubletten                 |
| konsistent   | Daten widersprechen sich nicht            |
| gültig       | Daten erfüllen Regeln und Formate         |
| verständlich | Daten können richtig interpretiert werden |

Schlechte Datenqualität kann technische und organisatorische Probleme verursachen.

Beispiel:

Wenn Geräte im Inventar doppelt oder falsch erfasst sind, wird Support, Einkauf und Wartung schwieriger.

---

## Datenvalidierung

Datenvalidierung bedeutet, Eingaben zu prüfen.

Beispiele:

- E-Mail-Adresse muss ein gültiges Format haben
- Pflichtfelder dürfen nicht leer sein
- Alter darf keine negative Zahl sein
- Preis muss eine Zahl sein
- Datum muss gültig sein
- Benutzername darf nicht doppelt existieren
- Passwort muss Mindestanforderungen erfüllen

Validierung verhindert viele Fehler schon bei der Eingabe.

Sie verbessert Datenqualität und reduziert spätere Korrekturen.

---

## Redundanz

Redundanz bedeutet, dass Daten mehrfach vorhanden sind.

Redundanz kann problematisch sein, wenn Daten dadurch widersprüchlich werden.

Beispiel:

Eine Kundenadresse steht in drei verschiedenen Listen. Wenn sie nur in einer Liste geändert wird, entstehen unterschiedliche Versionen.

Nachteile unnötiger Redundanz:

- mehr Speicherbedarf
- mehr Pflegeaufwand
- Fehler durch unterschiedliche Versionen
- unklare Datenquelle
- schwierigere Auswertungen

In Datenbanken versucht man oft, unnötige Redundanz durch gute Struktur zu reduzieren.

---

## Konsistenz

Konsistenz bedeutet, dass Daten logisch zusammenpassen und sich nicht widersprechen.

Beispiele:

- Eine Bestellung verweist auf einen existierenden Kunden.
- Eine Rechnung hat ein gültiges Datum.
- Ein Benutzer gehört zu einer vorhandenen Abteilung.
- Ein Gerät ist nicht gleichzeitig zwei verschiedenen Personen fest zugeordnet, wenn das fachlich nicht erlaubt ist.

Datenbanken können Konsistenz durch Regeln unterstützen.

Beispiele:

- Primärschlüssel
- Fremdschlüssel
- NOT NULL
- UNIQUE
- CHECK
- Transaktionen

---

## Integrität von Daten

Datenintegrität bedeutet, dass Daten korrekt und unverändert bleiben.

Datenintegrität wird geschützt durch:

- Berechtigungen
- Validierung
- Datenbankregeln
- Backups
- Transaktionen
- Logs
- Versionsverwaltung
- Schutz vor Schadsoftware
- kontrollierte Änderungen

Integrität ist besonders wichtig bei Daten, die Grundlage für Entscheidungen oder Prozesse sind.

Falsche Daten können große Folgen haben.

---

## Verfügbarkeit von Daten

Daten müssen verfügbar sein, wenn sie gebraucht werden.

Maßnahmen für Verfügbarkeit:

- Backups
- redundante Systeme
- Monitoring
- USV
- Datenbankwartung
- klare Wiederherstellungsprozesse
- Hochverfügbarkeit bei kritischen Systemen
- Schutz vor Ransomware
- regelmäßige Tests

Ein System kann technisch laufen, aber für Benutzer wertlos sein, wenn wichtige Daten fehlen oder nicht erreichbar sind.

---

## Vertraulichkeit von Daten

Vertraulichkeit bedeutet, dass Daten nur von berechtigten Personen gelesen werden dürfen.

Maßnahmen:

- Benutzerkonten
- Rollen und Rechte
- Verschlüsselung
- MFA
- sichere Dateiablagen
- Zugriffskontrolle
- Protokollierung
- getrennte Datenbereiche
- sichere Übertragung
- Datenschutzrichtlinien

Je sensibler die Daten, desto stärker müssen Zugriffe kontrolliert werden.

---

## Speicherorte

Daten können an verschiedenen Orten gespeichert werden.

| Speicherort    | Beispiel                           |
| -------------- | ---------------------------------- |
| lokal          | Datei auf einem Client             |
| Server         | Netzlaufwerk oder Dateiserver      |
| Datenbank      | SQL-Datenbank                      |
| Cloud          | Cloud-Speicher oder SaaS-Anwendung |
| Backup         | Sicherungssystem                   |
| Archiv         | langfristige Aufbewahrung          |
| mobiles Medium | USB-Stick oder externe Festplatte  |

Der Speicherort beeinflusst Sicherheit, Verfügbarkeit, Zugriff und Backup.

Sensible Unternehmensdaten sollten nicht unkontrolliert lokal oder auf privaten Datenträgern liegen.

---

## Lokale Speicherung

Lokale Speicherung bedeutet, dass Daten direkt auf einem Client liegen.

Vorteile:

- schneller Zugriff
- unabhängig vom Netzwerk
- einfach für einzelne Benutzer

Nachteile:

- höheres Risiko bei Verlust
- Backup oft schwieriger
- Daten liegen verteilt
- Zusammenarbeit erschwert
- Versionen können auseinanderlaufen
- Datenschutzrisiken bei mobilen Geräten

Lokale Speicherung sollte bewusst genutzt und abgesichert werden, besonders bei Laptops.

---

## Zentrale Speicherung

Zentrale Speicherung bedeutet, dass Daten auf Servern, NAS-Systemen, Datenbanken oder Cloud-Diensten gespeichert werden.

Vorteile:

- bessere Zugriffskontrolle
- einfachere Sicherung
- gemeinsame Nutzung
- zentrale Verwaltung
- bessere Nachvollziehbarkeit
- weniger verteilte Kopien

Nachteile:

- abhängig von Netzwerk und Servern
- zentrale Systeme müssen gut geschützt werden
- Ausfall kann viele Benutzer betreffen
- Berechtigungen müssen sauber gepflegt werden

In Unternehmen ist zentrale Speicherung oft besser kontrollierbar als viele lokale Kopien.

---

## Backup und Restore

Backup bedeutet Datensicherung.

Restore bedeutet Wiederherstellung.

Backups schützen vor:

- versehentlichem Löschen
- Hardwaredefekt
- Ransomware
- beschädigten Dateien
- Fehlkonfiguration
- Diebstahl
- Brand oder Wasserschaden

Wichtig:

Ein Backup ist nur dann wertvoll, wenn ein Restore funktioniert.

Deshalb müssen Backups regelmäßig getestet und dokumentiert werden.

---

## Archivierung

Archivierung bedeutet, Daten langfristig aufzubewahren.

Archivierung ist nicht das Gleiche wie Backup.

| Begriff | Zweck                                      |
| ------- | ------------------------------------------ |
| Backup  | Wiederherstellung nach Verlust oder Fehler |
| Archiv  | langfristige Aufbewahrung von Daten        |

Archive werden genutzt für:

- gesetzliche Aufbewahrung
- Nachweise
- alte Projekte
- abgeschlossene Vorgänge
- historische Daten

Archivdaten müssen ebenfalls geschützt werden, besonders wenn sie personenbezogene oder geschäftskritische Informationen enthalten.

---

## Löschung von Daten

Daten müssen nicht unbegrenzt gespeichert werden.

Bei der Löschung sind mehrere Punkte wichtig:

- gesetzliche Aufbewahrungsfristen
- Löschfristen
- Datenschutz
- technische Löschung
- sichere Löschung von Datenträgern
- Löschprotokoll bei sensiblen Daten
- Löschung aus Backups beachten
- Zuständigkeiten klären

Daten einfach nur „liegen zu lassen“ ist keine gute Datenverwaltung.

Besonders personenbezogene Daten dürfen nicht ohne Grund dauerhaft gespeichert werden.

---

## Zugriff auf Daten

Zugriffe müssen kontrolliert werden.

Wichtige Fragen:

- Wer darf Daten lesen?
- Wer darf Daten ändern?
- Wer darf Daten löschen?
- Wer darf Daten exportieren?
- Wer darf Berechtigungen vergeben?
- Werden Zugriffe protokolliert?
- Werden Rechte regelmäßig geprüft?

Berechtigungen sollten möglichst über Rollen und Gruppen vergeben werden.

Das macht Verwaltung einfacher und reduziert Fehler.

---

## Rollen und Rechte

Ein Rollen- und Rechtekonzept beschreibt, welche Benutzergruppen welche Zugriffe haben.

Beispiel:

| Rolle             | Zugriff                                |
| ----------------- | -------------------------------------- |
| normaler Benutzer | eigene Daten und freigegebene Bereiche |
| Teamleitung       | Teamdaten und Berichte                 |
| Buchhaltung       | Finanzdaten                            |
| Personalabteilung | Personaldaten                          |
| Administrator     | technische Verwaltung                  |
| Gast              | kein Zugriff auf interne Daten         |

Das Prinzip der minimalen Rechte sollte immer beachtet werden.

Benutzer erhalten nur die Rechte, die sie wirklich brauchen.

---

## Datenlebenszyklus

Der Datenlebenszyklus beschreibt die Stationen von Daten.

Typischer Ablauf:

1. Daten entstehen
2. Daten werden erfasst
3. Daten werden gespeichert
4. Daten werden verarbeitet
5. Daten werden genutzt
6. Daten werden gesichert
7. Daten werden archiviert
8. Daten werden gelöscht

Nicht jede Information durchläuft alle Schritte gleich.

Wichtig ist, dass für jede Phase klar ist, wie die Daten geschützt und verwaltet werden.

---

## Datenverwaltung und Datenschutz

Datenschutz spielt bei personenbezogenen Daten eine wichtige Rolle.

Wichtige Grundsätze:

- nur notwendige Daten speichern
- Zweck der Verarbeitung kennen
- Zugriff beschränken
- Daten sicher speichern
- Daten sicher übertragen
- Löschfristen beachten
- Daten nicht unkontrolliert kopieren
- Betroffenenrechte beachten
- Sicherheitsmaßnahmen dokumentieren

Für FISI ist Datenschutz besonders relevant bei Benutzerkonten, Logs, Backups, Cloud-Diensten und Supportfällen.

---

## Datenverwaltung in der Praxis

In der Praxis begegnet Datenverwaltung in vielen IT-Aufgaben.

Beispiele:

- Benutzerliste pflegen
- Inventar erfassen
- Netzwerkdokumentation aktualisieren
- Logdateien auswerten
- Backupstatus prüfen
- Datenbank prüfen
- CSV-Datei importieren
- Konfigurationsdatei bearbeiten
- Ticketsystem nutzen
- Cloud-Speicher verwalten
- Berechtigungen setzen
- alte Daten archivieren

Datenverwaltung ist deshalb nicht nur ein Thema für Entwickler oder Datenbankadministratoren.

Auch Systemadministratoren arbeiten täglich mit Daten.

---

## Praxisbeispiele

### Beispiel 1: Inventarliste

Ein Unternehmen verwaltet Geräte in einer Tabelle. Dort stehen Hostname, Seriennummer, Benutzer, Standort und Gerätetyp. Wenn diese Daten aktuell und eindeutig sind, kann der IT-Support schneller arbeiten.

### Beispiel 2: Logdateien

Ein Server schreibt Logdateien. Ein FISI durchsucht diese Logs nach Fehlermeldungen, Anmeldeversuchen oder Dienstproblemen. Logs helfen bei Fehlersuche und Sicherheitsanalyse.

### Beispiel 3: Datenbank für Supporttickets

Ein Ticketsystem speichert Anfragen in einer Datenbank. Jedes Ticket hat Status, Priorität, Benutzer, Beschreibung und Bearbeiter. Dadurch können Supportfälle nachvollziehbar bearbeitet werden.

---

## Typische Fehler

| Fehler                                       | Problem                                        |
| -------------------------------------------- | ---------------------------------------------- |
| Daten doppelt pflegen                        | widersprüchliche Versionen entstehen           |
| keine klare Datenstruktur nutzen             | Suche und Auswertung werden schwierig          |
| lokale Dateien unkontrolliert speichern      | Backup und Zugriffsschutz fehlen               |
| personenbezogene Daten in Testdateien nutzen | Datenschutzrisiko                              |
| Backups nicht testen                         | Wiederherstellung kann scheitern               |
| Rechte nicht prüfen                          | Benutzer behalten unnötige Zugriffe            |
| Logs ignorieren                              | Fehler und Angriffe bleiben unbemerkt          |
| Daten nie löschen                            | Speicher, Datenschutz und Übersicht leiden     |
| CSV-Dateien als Datenbankersatz missbrauchen | Skalierung und Konsistenz werden problematisch |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Datenverwaltung ein wichtiges Grundthema.

Ein FISI muss verstehen, wo Daten liegen, wie sie geschützt werden, wer darauf zugreifen darf und wie sie gesichert werden.

In der Praxis bedeutet das:

- Dateien und Ordnerstrukturen verwalten
- Datenbanken grundlegend verstehen
- SQL-Abfragen einordnen
- Logdateien analysieren
- Backups prüfen
- Zugriffsrechte setzen
- Datenschutz beachten
- Konfigurationsdaten pflegen
- Datenqualität erkennen
- zentrale Speicherung planen
- Wiederherstellung berücksichtigen

Ein guter FISI denkt bei Daten nicht nur an Speicherung, sondern auch an Struktur, Sicherheit, Verfügbarkeit, Backup, Zugriff und Lebenszyklus.

---

## Kurze Zusammenfassung

Datenverwaltung bedeutet, Daten sinnvoll zu erfassen, zu strukturieren, zu speichern, zu schützen, zu sichern, zu nutzen und bei Bedarf zu löschen.

Wichtige Themen sind Datenarten, Datenqualität, Dateien, CSV, JSON, YAML, Tabellen, Datenbanken, SQL, CRUD, Backup, Archivierung, Zugriffskontrolle, Datenschutz und Datenlebenszyklus.

Für FISI ist dieses Kapitel wichtig, weil fast alle IT-Systeme mit Daten arbeiten und Daten zuverlässig, sicher und nachvollziehbar verwaltet werden müssen.
