# 5.8 Datenverwaltung mit Datenbanken

In diesem Kapitel geht es darum, wie Daten mit Datenbanken strukturiert gespeichert, verwaltet und abgefragt werden.

Datenbanken werden in vielen IT-Systemen genutzt. Anwendungen speichern dort zum Beispiel Benutzer, Kunden, Produkte, Rechnungen, Tickets, Logeinträge oder Konfigurationsdaten. Ohne Datenbanken wären viele moderne Anwendungen schwer wartbar, langsam oder unübersichtlich.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Datenbanken installiert, angebunden, gesichert, überwacht und bei Fehlern analysiert werden müssen.

---

## Kurz erklärt

Eine Datenbank speichert Daten strukturiert und dauerhaft.

Ein Datenbankmanagementsystem verwaltet diese Daten und ermöglicht kontrollierten Zugriff.

Wichtige Themen sind:

- Datenbanken
- Datenbankmanagementsysteme
- Tabellen
- Datensätze
- Spalten
- Primärschlüssel
- Fremdschlüssel
- Beziehungen
- relationale Datenbanken
- SQL
- Abfragen
- Daten ändern
- Constraints
- Transaktionen
- Benutzerrechte
- Backup und Restore
- Sicherheit
- Dokumentation

Datenbanken helfen, Daten zuverlässig, geordnet und nachvollziehbar zu verwalten.

---

## Was ist eine Datenbank?

Eine Datenbank ist eine strukturierte Sammlung von Daten.

Daten werden so gespeichert, dass sie später gezielt gesucht, verändert, gelöscht oder ausgewertet werden können.

Beispiele für Daten in einer Datenbank:

- Benutzerkonten
- Kundendaten
- Gerätedaten
- Rechnungen
- Bestellungen
- Supporttickets
- Logdaten
- Produktlisten
- Lagerbestände
- Buchungen
- Rollen und Rechte

Eine Datenbank ist besonders nützlich, wenn viele Daten dauerhaft gespeichert und von mehreren Benutzern oder Anwendungen genutzt werden.

---

## Datenbankmanagementsystem

Ein Datenbankmanagementsystem, kurz DBMS, ist die Software, die Datenbanken verwaltet.

Beispiele:

| DBMS                 | typische Nutzung                          |
| -------------------- | ----------------------------------------- |
| PostgreSQL           | professionelle relationale Datenbanken    |
| MySQL                | Webanwendungen und klassische Datenbanken |
| MariaDB              | freie Alternative zu MySQL                |
| SQLite               | kleine lokale Datenbanken                 |
| Microsoft SQL Server | Windows- und Unternehmensumgebungen       |
| Oracle Database      | große Unternehmenssysteme                 |

Das DBMS übernimmt wichtige Aufgaben:

- Daten speichern
- Daten abfragen
- Daten ändern
- Tabellen verwalten
- Benutzerrechte verwalten
- gleichzeitige Zugriffe kontrollieren
- Transaktionen ausführen
- Datenintegrität sichern
- Backups unterstützen
- Sicherheit ermöglichen

Die Datenbank ist der Datenbestand.  
Das DBMS ist die Software, die diesen Datenbestand verwaltet.

---

## Warum Datenbanken genutzt werden

Datenbanken bieten viele Vorteile gegenüber einfachen Dateien oder Tabellen.

Vorteile:

- strukturierte Speicherung
- schnelle Suche
- kontrollierte Änderungen
- mehrere Benutzer gleichzeitig
- Rechteverwaltung
- Datenintegrität
- Beziehungen zwischen Daten
- Abfragen mit SQL
- Backup und Wiederherstellung
- bessere Skalierbarkeit
- zentrale Datenhaltung

Eine einfache CSV-Datei reicht für kleine Listen.

Wenn aber mehrere Benutzer, Beziehungen, Rechte, Auswertungen und dauerhafte Speicherung nötig sind, ist eine Datenbank meistens besser geeignet.

---

## Relationale Datenbanken

Relationale Datenbanken speichern Daten in Tabellen.

Tabellen bestehen aus Zeilen und Spalten.

Beispiel Tabelle `users`:

|  id | username | email             | active |
| --: | -------- | ----------------- | ------ |
|   1 | ali      | ali@example.com   | true   |
|   2 | maria    | maria@example.com | true   |
|   3 | sam      | sam@example.com   | false  |

Jede Zeile ist ein Datensatz.  
Jede Spalte beschreibt eine Eigenschaft.

Relationale Datenbanken sind sehr verbreitet und werden meistens mit SQL genutzt.

---

## Tabellen, Zeilen und Spalten

Eine Tabelle speichert gleichartige Daten.

| Begriff   | Bedeutung                                    |
| --------- | -------------------------------------------- |
| Tabelle   | Sammlung von Datensätzen                     |
| Zeile     | ein einzelner Datensatz                      |
| Spalte    | Eigenschaft eines Datensatzes                |
| Feld      | einzelner Wert in einer Zeile                |
| Datensatz | komplette Zeile mit zusammengehörigen Werten |

Beispiel:

In einer Inventartabelle ist ein Laptop ein Datensatz.

Spalten könnten sein:

- Inventarnummer
- Hostname
- Gerätetyp
- Seriennummer
- Standort
- Benutzer
- Status

---

## Datentypen in Datenbanken

Spalten haben Datentypen.

Der Datentyp legt fest, welche Werte gespeichert werden dürfen.

Typische Datentypen:

| Datentyp       | Bedeutung         | Beispiel           |
| -------------- | ----------------- | ------------------ |
| INTEGER        | ganze Zahl        | `42`               |
| TEXT / VARCHAR | Text              | `pc-001`           |
| BOOLEAN        | wahr/falsch       | `true`             |
| DATE           | Datum             | `2026-08-14`       |
| TIMESTAMP      | Datum und Uhrzeit | `2026-08-14 10:30` |
| DECIMAL        | genaue Kommazahl  | `19.99`            |
| FLOAT          | Kommazahl         | `3.14`             |

Datentypen verbessern Datenqualität.

Eine Spalte für Preise sollte zum Beispiel keine normalen Texte speichern.

---

## Primärschlüssel

Ein Primärschlüssel identifiziert jeden Datensatz eindeutig.

Beispiel:

|  id | username |
| --: | -------- |
|   1 | ali      |
|   2 | maria    |
|   3 | sam      |

Die Spalte `id` kann hier Primärschlüssel sein.

Eigenschaften eines Primärschlüssels:

- eindeutig
- nicht leer
- stabil
- identifiziert genau einen Datensatz

Primärschlüssel sind wichtig, damit Datensätze eindeutig angesprochen werden können.

Ohne Primärschlüssel wird es schwieriger, Daten zuverlässig zu ändern oder Beziehungen zu erstellen.

---

## Fremdschlüssel

Ein Fremdschlüssel verweist auf einen Datensatz in einer anderen Tabelle.

Beispiel Tabelle `devices`:

|  id | hostname | user_id |
| --: | -------- | ------: |
|   1 | pc-001   |       1 |
|   2 | pc-002   |       2 |

Beispiel Tabelle `users`:

|  id | username |
| --: | -------- |
|   1 | ali      |
|   2 | maria    |

Die Spalte `user_id` in `devices` verweist auf die Spalte `id` in `users`.

Dadurch wird gespeichert, welcher Benutzer welchem Gerät zugeordnet ist.

Fremdschlüssel helfen, Beziehungen zwischen Tabellen sauber abzubilden.

---

## Beziehungen zwischen Tabellen

In relationalen Datenbanken gibt es verschiedene Beziehungstypen.

| Beziehung | Bedeutung                                   | Beispiel                    |
| --------- | ------------------------------------------- | --------------------------- |
| 1:1       | ein Datensatz gehört genau zu einem anderen | Benutzer und Benutzerprofil |
| 1:n       | ein Datensatz kann mehrere andere haben     | Kunde und Bestellungen      |
| n:m       | viele Datensätze gehören zu vielen anderen  | Benutzer und Projekte       |

Die 1:n-Beziehung ist sehr häufig.

Beispiel:

Ein Kunde kann viele Bestellungen haben.  
Eine Bestellung gehört aber zu genau einem Kunden.

---

## n:m-Beziehung

Eine n:m-Beziehung kann nicht direkt sauber in zwei Tabellen gespeichert werden.

Dafür nutzt man meistens eine Zwischentabelle.

Beispiel:

Ein Benutzer kann in mehreren Projekten arbeiten.  
Ein Projekt kann mehrere Benutzer haben.

Tabelle `users`:

|  id | username |
| --: | -------- |
|   1 | ali      |
|   2 | maria    |

Tabelle `projects`:

|  id | name     |
| --: | -------- |
|   1 | Website  |
|   2 | Netzwerk |

Zwischentabelle `user_projects`:

| user_id | project_id |
| ------: | ---------: |
|       1 |          1 |
|       1 |          2 |
|       2 |          1 |

So kann eine n:m-Beziehung sauber abgebildet werden.

---

## ER-Modell

Ein Entity-Relationship-Modell, kurz ER-Modell, hilft beim Planen einer Datenbank.

Es zeigt:

- Entitäten
- Attribute
- Beziehungen

Beispiele:

| Begriff   | Bedeutung                                            |
| --------- | ---------------------------------------------------- |
| Entität   | Objekt oder Sache, über die Daten gespeichert werden |
| Attribut  | Eigenschaft einer Entität                            |
| Beziehung | Verbindung zwischen Entitäten                        |

Beispiel:

Entität: Benutzer  
Attribute: id, name, email

Entität: Gerät  
Attribute: id, hostname, seriennummer

Beziehung: Benutzer besitzt Gerät

Ein ER-Modell hilft, die Datenstruktur vor dem Erstellen der Tabellen zu verstehen.

---

## Normalisierung

Normalisierung bedeutet, Daten sinnvoll auf Tabellen aufzuteilen.

Ziele:

- doppelte Daten vermeiden
- Widersprüche verhindern
- Daten leichter ändern
- Datenstruktur sauber halten
- Beziehungen klar darstellen

Beispiel schlecht:

| gerät  | benutzer | email           | abteilung |
| ------ | -------- | --------------- | --------- |
| pc-001 | Ali      | ali@example.com | IT        |
| pc-002 | Ali      | ali@example.com | IT        |

Die Benutzerdaten stehen mehrfach.

Besser:

Tabelle `users`:

|  id | name | email           | abteilung |
| --: | ---- | --------------- | --------- |
|   1 | Ali  | ali@example.com | IT        |

Tabelle `devices`:

|  id | hostname | user_id |
| --: | -------- | ------: |
|   1 | pc-001   |       1 |
|   2 | pc-002   |       1 |

So müssen Benutzerdaten nur an einer Stelle gepflegt werden.

---

## SQL

SQL bedeutet **Structured Query Language**.

SQL wird genutzt, um mit relationalen Datenbanken zu arbeiten.

Mit SQL kann man:

- Daten abfragen
- Daten einfügen
- Daten ändern
- Daten löschen
- Tabellen erstellen
- Tabellen ändern
- Beziehungen definieren
- Rechte verwalten

Wichtige SQL-Befehle:

| Befehl       | Aufgabe           |
| ------------ | ----------------- |
| SELECT       | Daten abfragen    |
| INSERT       | Daten einfügen    |
| UPDATE       | Daten ändern      |
| DELETE       | Daten löschen     |
| CREATE TABLE | Tabelle erstellen |
| ALTER TABLE  | Tabelle ändern    |
| DROP TABLE   | Tabelle löschen   |

SQL ist eine zentrale Grundlage für Datenverwaltung.

---

## SELECT

Mit `SELECT` werden Daten abgefragt.

Beispiel:

```sql
SELECT * FROM users;
```

Das `*` bedeutet: alle Spalten anzeigen.

Besser ist oft, konkrete Spalten anzugeben:

```sql
SELECT username, email FROM users;
```

Das ist übersichtlicher und vermeidet unnötige Datenabfragen.

---

## WHERE

Mit `WHERE` werden Ergebnisse gefiltert.

Beispiel:

```sql
SELECT username, email
FROM users
WHERE active = true;
```

Diese Abfrage zeigt nur aktive Benutzer.

Weitere Beispiele:

```sql
SELECT *
FROM devices
WHERE status = 'active';
```

```sql
SELECT *
FROM tickets
WHERE priority = 'high';
```

`WHERE` ist wichtig, damit nicht immer alle Daten abgefragt werden.

---

## ORDER BY

Mit `ORDER BY` werden Ergebnisse sortiert.

Beispiel:

```sql
SELECT username, email
FROM users
ORDER BY username;
```

Absteigend sortieren:

```sql
SELECT username, email
FROM users
ORDER BY username DESC;
```

Sortierung hilft, Ergebnisse lesbarer zu machen.

---

## INSERT

Mit `INSERT` werden neue Datensätze eingefügt.

Beispiel:

```sql
INSERT INTO users (username, email, active)
VALUES ('ali', 'ali@example.com', true);
```

Wichtig ist, dass die Werte zu den Spalten und Datentypen passen.

Wenn Pflichtfelder fehlen, kann die Datenbank den Eintrag ablehnen.

---

## UPDATE

Mit `UPDATE` werden vorhandene Datensätze geändert.

Beispiel:

```sql
UPDATE users
SET active = false
WHERE id = 1;
```

Wichtig:

Bei `UPDATE` sollte fast immer eine `WHERE`-Bedingung genutzt werden.

Ohne `WHERE` werden alle passenden Datensätze geändert.

Gefährlich:

```sql
UPDATE users
SET active = false;
```

Dieser Befehl würde alle Benutzer deaktivieren.

---

## DELETE

Mit `DELETE` werden Datensätze gelöscht.

Beispiel:

```sql
DELETE FROM users
WHERE id = 1;
```

Auch bei `DELETE` ist `WHERE` sehr wichtig.

Gefährlich:

```sql
DELETE FROM users;
```

Dieser Befehl würde alle Datensätze aus der Tabelle löschen.

Vor `UPDATE` und `DELETE` ist es oft sinnvoll, zuerst mit `SELECT` zu prüfen, welche Datensätze betroffen sind.

---

## CREATE TABLE

Mit `CREATE TABLE` wird eine neue Tabelle erstellt.

Beispiel:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    username TEXT NOT NULL,
    email TEXT NOT NULL,
    active BOOLEAN NOT NULL
);
```

Hier werden Spalten, Datentypen und Regeln festgelegt.

Eine gute Tabellenstruktur ist wichtig für Datenqualität und Wartbarkeit.

---

## Constraints

Constraints sind Regeln für Daten in einer Tabelle.

Wichtige Constraints:

| Constraint  | Bedeutung                                |
| ----------- | ---------------------------------------- |
| PRIMARY KEY | eindeutige Kennung eines Datensatzes     |
| FOREIGN KEY | Verweis auf andere Tabelle               |
| NOT NULL    | Wert darf nicht leer sein                |
| UNIQUE      | Wert muss eindeutig sein                 |
| CHECK       | Wert muss eine Bedingung erfüllen        |
| DEFAULT     | Standardwert, wenn nichts angegeben wird |

Constraints schützen Daten vor falschen oder unvollständigen Eingaben.

---

## NULL

`NULL` bedeutet, dass kein Wert vorhanden ist.

`NULL` ist nicht das Gleiche wie:

- `0`
- leerer Text
- `false`

Beispiel:

Eine Spalte `phone_number` kann `NULL` sein, wenn keine Telefonnummer bekannt ist.

Wenn ein Wert immer vorhanden sein muss, nutzt man `NOT NULL`.

Beispiel:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    username TEXT NOT NULL
);
```

Dann darf `username` nicht leer bleiben.

---

## UNIQUE

`UNIQUE` sorgt dafür, dass ein Wert nur einmal vorkommen darf.

Beispiel:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    email TEXT UNIQUE
);
```

Dadurch kann dieselbe E-Mail-Adresse nicht mehrfach gespeichert werden.

Das ist nützlich für:

- Benutzernamen
- E-Mail-Adressen
- Inventarnummern
- Seriennummern
- eindeutige Ticketnummern

---

## JOIN

Mit `JOIN` werden Daten aus mehreren Tabellen verbunden.

Beispiel:

Tabelle `users`:

|  id | username |
| --: | -------- |
|   1 | ali      |
|   2 | maria    |

Tabelle `devices`:

|  id | hostname | user_id |
| --: | -------- | ------: |
|   1 | pc-001   |       1 |
|   2 | pc-002   |       2 |

Abfrage:

```sql
SELECT devices.hostname, users.username
FROM devices
JOIN users ON devices.user_id = users.id;
```

Ergebnis:

| hostname | username |
| -------- | -------- |
| pc-001   | ali      |
| pc-002   | maria    |

`JOIN` ist wichtig, weil relationale Datenbanken Daten auf mehrere Tabellen verteilen.

---

## Aggregatfunktionen

Aggregatfunktionen berechnen Werte über mehrere Datensätze.

Wichtige Funktionen:

| Funktion | Bedeutung              |
| -------- | ---------------------- |
| COUNT    | zählt Datensätze       |
| SUM      | summiert Werte         |
| AVG      | berechnet Durchschnitt |
| MIN      | kleinster Wert         |
| MAX      | größter Wert           |

Beispiel:

```sql
SELECT COUNT(*)
FROM users;
```

Diese Abfrage zählt alle Benutzer.

Beispiel:

```sql
SELECT status, COUNT(*)
FROM tickets
GROUP BY status;
```

Diese Abfrage zählt Tickets pro Status.

---

## GROUP BY

Mit `GROUP BY` werden Daten gruppiert.

Beispiel:

```sql
SELECT status, COUNT(*)
FROM tickets
GROUP BY status;
```

Ergebnis:

| status      | count |
| ----------- | ----: |
| open        |    12 |
| in_progress |     5 |
| closed      |    30 |

Das ist nützlich für Auswertungen und Berichte.

---

## Transaktionen

Eine Transaktion fasst mehrere Datenbankoperationen zu einer Einheit zusammen.

Eine Transaktion soll entweder vollständig ausgeführt oder vollständig zurückgenommen werden.

Beispiel:

Bei einer Überweisung müssen zwei Dinge passieren:

1. Geld wird von Konto A abgezogen.
2. Geld wird Konto B gutgeschrieben.

Es wäre falsch, wenn nur einer der beiden Schritte passiert.

Transaktionen schützen vor unvollständigen oder widersprüchlichen Daten.

---

## ACID-Prinzip

Das ACID-Prinzip beschreibt wichtige Eigenschaften von Transaktionen.

| Buchstabe       | Bedeutung                                |
| --------------- | ---------------------------------------- |
| A - Atomicity   | alles oder nichts                        |
| C - Consistency | Daten bleiben gültig                     |
| I - Isolation   | gleichzeitige Vorgänge stören sich nicht |
| D - Durability  | gespeicherte Änderungen bleiben erhalten |

ACID ist wichtig für zuverlässige Datenbanken.

Besonders bei Finanzdaten, Bestellungen oder kritischen Geschäftsprozessen sind Transaktionen sehr wichtig.

---

## Indizes

Ein Index hilft der Datenbank, Daten schneller zu finden.

Beispiel:

Wenn häufig nach `email` gesucht wird, kann ein Index auf dieser Spalte sinnvoll sein.

```sql
CREATE INDEX idx_users_email
ON users (email);
```

Vorteile:

- schnellere Suche
- bessere Performance bei großen Tabellen

Nachteile:

- braucht Speicherplatz
- kann Einfügen und Ändern etwas langsamer machen
- zu viele Indizes machen Verwaltung komplexer

Indizes sollten bewusst gesetzt werden.

---

## Views

Eine View ist eine gespeicherte Abfrage.

Beispiel:

```sql
CREATE VIEW active_users AS
SELECT username, email
FROM users
WHERE active = true;
```

Danach kann man die View wie eine Tabelle abfragen:

```sql
SELECT *
FROM active_users;
```

Views können helfen, häufige Abfragen zu vereinfachen oder bestimmte Daten gezielt bereitzustellen.

---

## Benutzer und Rechte

Datenbanken haben oft eigene Benutzer und Rechte.

Wichtige Fragen:

- Wer darf sich verbinden?
- Wer darf Daten lesen?
- Wer darf Daten ändern?
- Wer darf Daten löschen?
- Wer darf Tabellen erstellen?
- Wer darf Benutzer verwalten?
- Welche Anwendung nutzt welchen Datenbankbenutzer?

Das Prinzip der minimalen Rechte ist wichtig.

Eine Anwendung sollte nur die Rechte bekommen, die sie wirklich braucht.

---

## Sicherheit bei Datenbanken

Datenbanken enthalten oft wichtige oder sensible Daten.

Wichtige Schutzmaßnahmen:

- starke Passwörter
- getrennte Benutzerkonten
- Rechte nach Rollen vergeben
- keine Adminrechte für normale Anwendungen
- verschlüsselte Verbindungen nutzen
- Zugriff auf Netzwerkebene begrenzen
- Datenbank nicht unnötig öffentlich erreichbar machen
- regelmäßige Updates
- Backups schützen
- Logs prüfen
- sensible Daten nicht in Testsysteme kopieren
- SQL-Injection vermeiden

Datenbanken sind oft ein besonders wertvolles Ziel für Angreifer.

---

## SQL-Injection

SQL-Injection ist ein Angriff, bei dem schädliche Eingaben in SQL-Abfragen eingeschleust werden.

Problematisch ist es, wenn Benutzereingaben unsicher direkt in SQL eingebaut werden.

Beispiel gefährliche Idee:

```text
SELECT * FROM users WHERE username = 'EINGABE';
```

Wenn Eingaben nicht sicher verarbeitet werden, kann ein Angreifer die Abfrage manipulieren.

Schutzmaßnahmen:

- vorbereitete Statements nutzen
- Eingaben validieren
- keine SQL-Abfragen durch einfache Textverkettung bauen
- Rechte der Datenbankbenutzer begrenzen
- Fehlermeldungen nicht zu viele interne Details zeigen

SQL-Injection ist einer der bekanntesten Angriffe auf Datenbankanwendungen.

---

## Backup und Restore

Datenbanken müssen regelmäßig gesichert werden.

Backup bedeutet Sicherung.  
Restore bedeutet Wiederherstellung.

Wichtige Fragen:

- Wie oft wird gesichert?
- Wo liegen Backups?
- Sind Backups verschlüsselt?
- Wer darf auf Backups zugreifen?
- Wie lange werden Backups aufbewahrt?
- Wird die Wiederherstellung getestet?
- Wie schnell muss Restore möglich sein?
- Gibt es ein Notfallkonzept?

Ein Backup ist nur wertvoll, wenn der Restore funktioniert.

Deshalb müssen Wiederherstellungen regelmäßig getestet werden.

---

## Datenbanklogs

Datenbanken schreiben oft Logs.

Logs helfen bei:

- Fehlersuche
- Sicherheitsanalyse
- Performanceproblemen
- Verbindungsproblemen
- fehlgeschlagenen Anmeldungen
- Transaktionsproblemen
- Abstürzen

Logs können aber auch sensible Informationen enthalten.

Deshalb müssen Datenbanklogs geschützt und sinnvoll aufbewahrt werden.

---

## Performance

Performance beschreibt, wie schnell und zuverlässig eine Datenbank arbeitet.

Einflussfaktoren:

- Datenmenge
- Tabellenstruktur
- Indizes
- Abfragen
- Hardware
- Arbeitsspeicher
- Festplatte
- Netzwerk
- gleichzeitige Benutzer
- Datenbankkonfiguration

Langsame Datenbanken können Anwendungen stark beeinträchtigen.

Für FISI ist wichtig, einfache Ursachen erkennen zu können, zum Beispiel volle Festplatten, schlechte Netzwerkverbindung, fehlende Ressourcen oder fehlerhafte Dienste.

---

## Datenbank im Betrieb

Im Betrieb müssen Datenbanken gepflegt und überwacht werden.

Typische Aufgaben:

- Dienststatus prüfen
- Speicherplatz überwachen
- Backups kontrollieren
- Logs prüfen
- Updates planen
- Benutzerrechte verwalten
- Performance beobachten
- Verbindungen prüfen
- Sicherheitsupdates einspielen
- Wiederherstellung testen
- Dokumentation pflegen

Datenbanken sind nicht nur Entwicklungsthema.

Sie sind ein wichtiger Bestandteil produktiver IT-Systeme.

---

## Datenbank und Anwendung

Viele Anwendungen nutzen eine Datenbank im Hintergrund.

Beispiel:

Eine Webanwendung besteht oft aus:

- Frontend
- Backend
- Datenbank
- Benutzerverwaltung
- Netzwerkverbindung
- Server oder Container
- Backup
- Monitoring

Wenn die Datenbank ausfällt, funktioniert die Anwendung oft nicht mehr richtig.

Deshalb muss der FISI verstehen, welche Anwendung welche Datenbank nutzt und welche Abhängigkeiten bestehen.

---

## SQLite, PostgreSQL und MySQL

Datenbanksysteme unterscheiden sich je nach Einsatzbereich.

| System     | typische Nutzung                                                |
| ---------- | --------------------------------------------------------------- |
| SQLite     | kleine lokale Anwendungen, Lernprojekte, eingebettete Datenbank |
| PostgreSQL | professionelle Anwendungen, starke Datenintegrität              |
| MySQL      | Webanwendungen, klassische Serveranwendungen                    |
| MariaDB    | freie MySQL-kompatible Alternative                              |

SQLite ist einfach, weil keine separate Serverinstallation nötig ist.

PostgreSQL und MySQL laufen meistens als eigener Datenbankdienst und sind besser für mehrere Benutzer und produktive Anwendungen geeignet.

---

## Datenbanken mit Docker

Datenbanken können auch in Containern laufen.

Beispiel:

```bash
docker run --name test-db -e POSTGRES_PASSWORD=secret -p 5432:5432 -d postgres
```

Das ist praktisch für:

- Lernumgebungen
- Tests
- Entwicklung
- lokale Datenbankprojekte
- reproduzierbare Umgebungen

Wichtig:

Für produktive Datenbanken muss besonders auf Volumes, Backups, Updates, Sicherheit und Zugriffsschutz geachtet werden.

Ein Container allein ist kein Backup.

---

## Dokumentation von Datenbanken

Eine Datenbank sollte dokumentiert werden.

Wichtige Inhalte:

- Zweck der Datenbank
- Tabellenübersicht
- Spalten und Datentypen
- Primärschlüssel
- Fremdschlüssel
- Beziehungen
- Benutzerrechte
- Backup-Konzept
- Restore-Anleitung
- Schnittstellen
- wichtige Abfragen
- Besonderheiten
- Verantwortlichkeiten

Ohne Dokumentation ist eine Datenbank später schwer zu verstehen und zu warten.

---

## Praxisbeispiele

### Beispiel 1: Inventardatenbank

Eine IT-Abteilung speichert Geräte in einer Datenbank. Tabellen können `devices`, `users` und `locations` sein. Über Fremdschlüssel wird gespeichert, welches Gerät welchem Benutzer oder Standort zugeordnet ist.

### Beispiel 2: Ticketsystem

Ein Ticketsystem speichert Supportfälle. Tabellen können `tickets`, `users`, `priorities` und `status` sein. SQL-Abfragen helfen, offene Tickets oder dringende Fälle zu finden.

### Beispiel 3: Datenbank im Docker-Container

Für eine Schulung wird eine PostgreSQL-Datenbank als Container gestartet. Die Datenbank wird mit einem Volume verbunden, damit Daten auch nach dem Stoppen des Containers erhalten bleiben.

---

## Typische Fehler

| Fehler                                 | Problem                                        |
| -------------------------------------- | ---------------------------------------------- |
| keine Primärschlüssel nutzen           | Datensätze sind schwer eindeutig zu erkennen   |
| Daten doppelt speichern                | Widersprüche entstehen                         |
| keine Fremdschlüssel verwenden         | Beziehungen werden unsauber                    |
| `UPDATE` ohne `WHERE`                  | viele Datensätze werden versehentlich geändert |
| `DELETE` ohne `WHERE`                  | Daten können massenhaft gelöscht werden        |
| Backups nicht testen                   | Wiederherstellung kann scheitern               |
| Datenbank öffentlich erreichbar machen | hohes Sicherheitsrisiko                        |
| Anwendung mit Adminrechten verbinden   | unnötig großes Schadenspotenzial               |
| echte Daten in Testsystem kopieren     | Datenschutzproblem                             |
| keine Dokumentation schreiben          | Wartung wird schwierig                         |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Datenbanken wichtig, weil viele Anwendungen im Unternehmen auf Datenbanken angewiesen sind.

In der Praxis bedeutet das:

- Datenbanksysteme grundlegend verstehen
- Datenbankdienste installieren und prüfen
- Verbindungen zwischen Anwendung und Datenbank analysieren
- einfache SQL-Abfragen ausführen
- Tabellen und Beziehungen verstehen
- Benutzerrechte einordnen
- Backups und Restore prüfen
- Logs analysieren
- Performanceprobleme erkennen
- Datenbanken in Docker-Testumgebungen nutzen
- Sicherheit und Datenschutz beachten
- Datenbankdokumentation pflegen

Ein guter FISI muss nicht jede Datenbank tief wie ein Datenbankentwickler optimieren, sollte aber verstehen, wie Datenbanken aufgebaut sind und wie sie sicher betrieben werden.

---

## Kurze Zusammenfassung

Datenbanken speichern Daten strukturiert, dauerhaft und nachvollziehbar.

Relationale Datenbanken arbeiten mit Tabellen, Zeilen, Spalten, Primärschlüsseln, Fremdschlüsseln und Beziehungen.

SQL wird genutzt, um Daten abzufragen, einzufügen, zu ändern, zu löschen und Tabellen zu verwalten.

Wichtige Themen sind Constraints, NULL, JOINs, Transaktionen, Indizes, Benutzerrechte, Sicherheit, Backup, Restore, Performance und Dokumentation.

Für FISI ist dieses Kapitel wichtig, weil viele produktive Anwendungen Datenbanken nutzen und diese zuverlässig, sicher und nachvollziehbar betrieben werden müssen.
