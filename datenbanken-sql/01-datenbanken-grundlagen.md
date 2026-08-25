# 1. Datenbank-Grundlagen

In diesem Kapitel geht es um die Grundlagen von Datenbanken.

Datenbanken werden genutzt, um Informationen strukturiert, dauerhaft und gezielt abrufbar zu speichern. Viele IT-Systeme arbeiten im Hintergrund mit Datenbanken, auch wenn man das als Benutzer nicht direkt sieht.

Für Fachinformatiker für Systemintegration ist es wichtig zu verstehen, wie Datenbanken grundsätzlich aufgebaut sind, warum Tabellen genutzt werden und wie Daten sauber gespeichert werden.

---

## Kurz erklärt

Eine Datenbank ist eine strukturierte Sammlung von Daten.

Beispiele für Daten:

```text
Benutzer
Kunden
Produkte
Bücher
Tickets
Bestellungen
IP-Adressen
Geräte
Log-Einträge
```

Eine Datenbank sorgt dafür, dass diese Daten nicht einfach ungeordnet irgendwo gespeichert werden, sondern nach klaren Regeln.

Dadurch kann man Daten:

- speichern
- suchen
- sortieren
- filtern
- ändern
- löschen
- miteinander verbinden
- auswerten

---

## Warum Datenbanken gebraucht werden

Ohne Datenbank würden viele Anwendungen ihre Daten in einfachen Dateien speichern.

Das wäre bei kleinen Datenmengen möglich, wird aber schnell unübersichtlich.

Beispiel:

```text
kunden.txt
produkte.txt
bestellungen.txt
```

Probleme dabei:

- Daten können doppelt vorkommen
- Suche ist langsam
- Änderungen sind fehleranfällig
- mehrere Benutzer können schwer gleichzeitig arbeiten
- Beziehungen zwischen Daten sind schwer darstellbar
- Sicherheit und Rechte sind schwer zu verwalten
- Backups und Wiederherstellung werden komplizierter

Eine Datenbank löst viele dieser Probleme, weil sie Daten strukturiert verwaltet.

---

## Beispiele aus der Praxis

| System             | Mögliche Daten in der Datenbank            |
| ------------------ | ------------------------------------------ |
| Onlineshop         | Kunden, Produkte, Warenkörbe, Bestellungen |
| Bibliothek         | Bücher, Autoren, Mitglieder, Ausleihen     |
| Ticketsystem       | Benutzer, Tickets, Status, Kommentare      |
| Schule             | Schüler, Kurse, Klassen, Noten             |
| Monitoring         | Server, Messwerte, Ereignisse, Logs        |
| Netzwerkverwaltung | Geräte, IP-Adressen, Standorte, VLANs      |
| Personalverwaltung | Mitarbeiter, Abteilungen, Verträge         |

Fast jede moderne Anwendung arbeitet mit irgendeiner Form von Datenbank.

---

## Datenbank vs Datei

Eine Datei kann Daten speichern. Eine Datenbank kann Daten strukturiert verwalten.

| Bereich             | Datei                    | Datenbank                 |
| ------------------- | ------------------------ | ------------------------- |
| Struktur            | oft einfach oder frei    | klar definiert            |
| Suche               | oft langsam oder manuell | gezielt mit Abfragen      |
| Beziehungen         | schwer darstellbar       | über Schlüssel möglich    |
| Mehrbenutzerbetrieb | schwierig                | dafür ausgelegt           |
| Sicherheit          | eher einfach             | Rechte und Rollen möglich |
| Datenmenge          | eher klein               | auch große Datenmengen    |
| Auswertung          | begrenzt                 | mit SQL möglich           |
| Konsistenz          | schwer zu sichern        | Regeln und Constraints    |

Eine Datei ist nicht automatisch schlecht. Für Konfigurationen oder kleine Daten reicht sie oft aus.

Für strukturierte, verknüpfte und dauerhaft wichtige Daten ist eine Datenbank meistens besser.

---

## Relationale Datenbanken

In diesem Wiki geht es hauptsächlich um relationale Datenbanken.

Relationale Datenbanken speichern Daten in Tabellen.

Beispiele für relationale Datenbanksysteme:

```text
PostgreSQL
MySQL
MariaDB
SQLite
Microsoft SQL Server
Oracle Database
```

Der Begriff „relational“ bedeutet, dass Daten in Tabellen organisiert werden und Tabellen miteinander in Beziehung stehen können.

Beispiel:

```text
members
books
loans
```

Eine Ausleihe kann mit einem Mitglied und einem Buch verbunden sein.

Diese Verbindung entsteht über Schlüssel.

---

## Tabellen

Eine Tabelle ist eine strukturierte Sammlung von Daten.

Man kann sich eine Tabelle ähnlich wie eine Excel-Tabelle vorstellen, aber mit strengeren Regeln.

Beispiel:

| id  | name         | email            |
| --- | ------------ | ---------------- |
| 1   | Max Müller   | max@example.com  |
| 2   | Lisa Schmidt | lisa@example.com |
| 3   | Sara Klein   | sara@example.com |

Diese Tabelle könnte `users` heißen.

Sie besteht aus:

```text
Spalten
Zeilen
Datensätzen
Werten
```

---

## Spalten

Eine Spalte beschreibt ein bestimmtes Merkmal.

Beispiel:

```text
id
name
email
created_at
```

Jede Spalte hat normalerweise einen Datentyp.

Beispiel:

| Spalte       | Bedeutung          | Möglicher Datentyp  |
| ------------ | ------------------ | ------------------- |
| `id`         | eindeutige Nummer  | INTEGER             |
| `name`       | Name des Benutzers | TEXT                |
| `email`      | E-Mail-Adresse     | TEXT                |
| `created_at` | Erstellungsdatum   | DATE oder TIMESTAMP |

Spalten legen fest, welche Art von Information gespeichert werden kann.

---

## Zeilen und Datensätze

Eine Zeile enthält einen vollständigen Datensatz.

Beispiel:

| id  | name       | email           |
| --- | ---------- | --------------- |
| 1   | Max Müller | max@example.com |

Diese Zeile beschreibt einen Benutzer.

Ein Datensatz ist also eine zusammengehörende Gruppe von Werten.

In einer Benutzertabelle entspricht eine Zeile einem Benutzer.  
In einer Büchertabelle entspricht eine Zeile einem Buch.  
In einer Ausleihtabelle entspricht eine Zeile einer Ausleihe.

---

## Werte

Ein Wert ist der konkrete Inhalt einer Zelle.

Beispiel:

```text
Max Müller
max@example.com
1
```

Werte müssen zum Datentyp der Spalte passen.

Eine Zahl gehört zum Beispiel nicht sinnvoll in eine Datumsspalte.

Deshalb sind Datentypen wichtig.

---

## Datentypen

Datentypen legen fest, welche Art von Daten gespeichert werden darf.

Häufige Datentypen:

| Datentyp  | Bedeutung                 | Beispiel              |
| --------- | ------------------------- | --------------------- |
| INTEGER   | ganze Zahl                | `42`                  |
| TEXT      | Text                      | `'Hamburg'`           |
| VARCHAR   | Text mit begrenzter Länge | `'Max'`               |
| BOOLEAN   | wahr oder falsch          | `true`                |
| DATE      | Datum                     | `2026-08-25`          |
| TIMESTAMP | Datum und Uhrzeit         | `2026-08-25 15:30:00` |
| DECIMAL   | genaue Kommazahl          | `19.99`               |

Der richtige Datentyp hilft, Daten sauber und zuverlässig zu speichern.

---

## Beispiel einer Tabelle in SQL

Eine einfache Tabelle kann so erstellt werden:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT
);
```

Bedeutung:

| Teil                 | Erklärung                                   |
| -------------------- | ------------------------------------------- |
| `CREATE TABLE users` | erstellt eine Tabelle mit dem Namen `users` |
| `id INTEGER`         | Spalte `id` als ganze Zahl                  |
| `PRIMARY KEY`        | eindeutige Kennung der Zeile                |
| `name TEXT`          | Spalte `name` als Text                      |
| `NOT NULL`           | Wert darf nicht leer sein                   |
| `email TEXT`         | Spalte `email` als Text                     |

Diese Tabelle kann Benutzer speichern.

---

## Daten einfügen

Daten werden mit `INSERT` eingefügt.

```sql
INSERT INTO users (id, name, email)
VALUES (1, 'Max Müller', 'max@example.com');
```

Danach enthält die Tabelle einen Datensatz.

Mehrere Datensätze:

```sql
INSERT INTO users (id, name, email)
VALUES
  (2, 'Lisa Schmidt', 'lisa@example.com'),
  (3, 'Sara Klein', 'sara@example.com');
```

---

## Daten abfragen

Daten werden mit `SELECT` abgefragt.

```sql
SELECT *
FROM users;
```

Das bedeutet:

```text
Zeige alle Spalten aus der Tabelle users.
```

Bestimmte Spalten abfragen:

```sql
SELECT name, email
FROM users;
```

Mit Filter:

```sql
SELECT name, email
FROM users
WHERE id = 1;
```

---

## Daten ändern

Daten werden mit `UPDATE` geändert.

```sql
UPDATE users
SET email = 'max.neu@example.com'
WHERE id = 1;
```

Wichtig:

Bei `UPDATE` sollte fast immer ein `WHERE` genutzt werden.

Ohne `WHERE` werden alle passenden Zeilen geändert.

Gefährlich:

```sql
UPDATE users
SET email = 'test@example.com';
```

Das würde bei vielen Datenbanken alle E-Mail-Adressen ändern.

---

## Daten löschen

Daten werden mit `DELETE` gelöscht.

```sql
DELETE FROM users
WHERE id = 1;
```

Auch hier ist `WHERE` sehr wichtig.

Gefährlich:

```sql
DELETE FROM users;
```

Das löscht alle Datensätze aus der Tabelle.

---

## Primärschlüssel

Ein Primärschlüssel ist eine eindeutige Kennung für einen Datensatz.

Beispiel:

```text
id
```

In einer Tabelle sollte jeder Datensatz eindeutig identifizierbar sein.

Beispiel:

| id  | name |
| --- | ---- |
| 1   | Max  |
| 2   | Lisa |
| 3   | Max  |

Der Name ist nicht eindeutig, weil zwei Personen gleich heißen können.

Die `id` ist eindeutig.

Deshalb wird meistens eine ID als Primärschlüssel genutzt.

---

## Warum Primärschlüssel wichtig sind

Primärschlüssel helfen bei:

- eindeutiger Identifikation
- Datenänderungen
- Datenlöschung
- Beziehungen zwischen Tabellen
- Joins
- Datenintegrität

Beispiel:

```sql
SELECT *
FROM users
WHERE id = 2;
```

Das ist sauberer als:

```sql
SELECT *
FROM users
WHERE name = 'Lisa';
```

Denn Namen können doppelt vorkommen.

---

## Fremdschlüssel

Ein Fremdschlüssel ist ein Verweis auf eine andere Tabelle.

Beispiel:

```text
loans.member_id verweist auf members.id
```

Tabelle `members`:

| id  | name |
| --- | ---- |
| 1   | Max  |
| 2   | Lisa |

Tabelle `loans`:

| id  | member_id | book_title       |
| --- | --------- | ---------------- |
| 1   | 2         | Linux Grundlagen |

Hier bedeutet `member_id = 2`, dass Lisa das Buch ausgeliehen hat.

Der Fremdschlüssel verbindet also Datensätze aus verschiedenen Tabellen.

---

## Beziehungen zwischen Tabellen

Relationale Datenbanken arbeiten viel mit Beziehungen.

Häufige Beziehungstypen:

| Beziehung | Bedeutung                                                     | Beispiel                    |
| --------- | ------------------------------------------------------------- | --------------------------- |
| 1:1       | ein Datensatz gehört genau zu einem anderen                   | Benutzer und Benutzerprofil |
| 1:n       | ein Datensatz kann mehrere andere Datensätze haben            | Kunde und Bestellungen      |
| n:m       | mehrere Datensätze können mit mehreren anderen verbunden sein | Bücher und Autoren          |

Die wichtigste Beziehung am Anfang ist meistens:

```text
1:n
```

Beispiel:

Ein Mitglied kann mehrere Ausleihen haben.  
Eine Ausleihe gehört aber zu genau einem Mitglied.

---

## Beispiel: Bibliothek

Eine einfache Bibliotheksdatenbank könnte so aussehen:

```text
members
books
loans
```

`members` speichert Mitglieder.

| id  | name |
| --- | ---- |
| 1   | Max  |
| 2   | Lisa |

`books` speichert Bücher.

| id  | title            |
| --- | ---------------- |
| 1   | Linux Grundlagen |
| 2   | SQL Einstieg     |

`loans` speichert Ausleihen.

| id  | member_id | book_id |
| --- | --------- | ------- |
| 1   | 1         | 2       |
| 2   | 2         | 1       |

Dadurch sieht man:

```text
Max hat SQL Einstieg ausgeliehen.
Lisa hat Linux Grundlagen ausgeliehen.
```

Die Tabelle `loans` verbindet Mitglieder und Bücher.

---

## Datenintegrität

Datenintegrität bedeutet, dass Daten korrekt, vollständig und widerspruchsfrei bleiben.

Beispiele:

```text
Eine Ausleihe soll nicht auf ein nicht vorhandenes Mitglied zeigen.
Eine E-Mail-Adresse soll nicht doppelt vergeben sein.
Ein Name darf nicht leer sein.
Eine ID muss eindeutig sein.
```

Datenbanken nutzen Regeln, um solche Fehler zu vermeiden.

Diese Regeln heißen Constraints.

---

## Constraints

Constraints sind Regeln für Tabellen und Spalten.

Häufige Constraints:

| Constraint    | Bedeutung                                |
| ------------- | ---------------------------------------- |
| `PRIMARY KEY` | eindeutige Kennung                       |
| `FOREIGN KEY` | Verweis auf andere Tabelle               |
| `NOT NULL`    | Wert darf nicht fehlen                   |
| `UNIQUE`      | Wert muss eindeutig sein                 |
| `CHECK`       | Wert muss bestimmte Bedingung erfüllen   |
| `DEFAULT`     | Standardwert, wenn nichts angegeben wird |

Beispiel:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT UNIQUE
);
```

Hier muss `id` eindeutig sein, `name` darf nicht fehlen und `email` darf nicht doppelt vorkommen.

---

## NULL

`NULL` bedeutet: kein Wert vorhanden.

Das ist nicht dasselbe wie:

```text
0
leerer Text
false
```

Beispiel:

| id  | name | phone     |
| --- | ---- | --------- |
| 1   | Max  | NULL      |
| 2   | Lisa | 040123456 |

Bei Max ist keine Telefonnummer gespeichert.

Das bedeutet nicht, dass seine Telefonnummer `0` ist.  
Es bedeutet, dass kein Wert eingetragen wurde.

---

## Datenbankmanagementsystem

Eine Datenbank allein ist nicht nur eine Datei oder Tabelle.

Man braucht ein Datenbankmanagementsystem.

Abkürzung:

```text
DBMS
```

Ein DBMS verwaltet Datenbanken.

Beispiele:

```text
PostgreSQL
MySQL
MariaDB
SQLite
Microsoft SQL Server
Oracle Database
```

Aufgaben eines DBMS:

- Tabellen verwalten
- SQL-Abfragen ausführen
- Daten speichern
- Benutzerrechte verwalten
- Verbindungen annehmen
- Transaktionen steuern
- Backups ermöglichen
- Datenintegrität sichern

---

## Datenbankserver

Viele Datenbanken laufen als Serverdienst.

Beispiel PostgreSQL:

```text
Client -> PostgreSQL-Server -> Datenbank
```

Ein Client kann sein:

```text
Adminer
psql
eine Webanwendung
ein Backend
ein SQL-Tool
```

Der Server verarbeitet die Anfrage und gibt das Ergebnis zurück.

Bei Docker läuft PostgreSQL oft als Container.

Adminer kann dann als zweiter Container darauf zugreifen.

---

## Client und Server

Bei Datenbanken gibt es oft eine Client-Server-Struktur.

| Teil      | Aufgabe                           |
| --------- | --------------------------------- |
| Client    | sendet SQL-Abfragen               |
| Server    | verarbeitet Abfragen              |
| Datenbank | speichert die Daten               |
| Benutzer  | arbeitet über Tool oder Anwendung |

Beispiel:

```text
Browser -> Adminer -> PostgreSQL -> Datenbank
```

Adminer ist dabei die Weboberfläche. PostgreSQL ist das Datenbanksystem.

---

## SQL als Sprache

SQL ist die Sprache für relationale Datenbanken.

SQL wird genutzt für:

```text
Tabellen erstellen
Daten einfügen
Daten abfragen
Daten ändern
Daten löschen
Rechte verwalten
Transaktionen steuern
```

SQL ist keine normale Programmiersprache wie Python.

SQL beschreibt eher, welche Daten man haben möchte oder welche Daten geändert werden sollen.

Beispiel:

```sql
SELECT name
FROM users
WHERE id = 1;
```

Man beschreibt das gewünschte Ergebnis. Die Datenbank entscheidet, wie sie es ausführt.

---

## CRUD

CRUD beschreibt die vier Grundoperationen für Daten.

| Buchstabe | Bedeutung | SQL-Befehl |
| --------- | --------- | ---------- |
| C         | Create    | `INSERT`   |
| R         | Read      | `SELECT`   |
| U         | Update    | `UPDATE`   |
| D         | Delete    | `DELETE`   |

CRUD ist ein sehr wichtiges Grundkonzept.

Fast jede Anwendung macht im Hintergrund CRUD-Operationen.

Beispiel Ticketsystem:

```text
Ticket erstellen -> INSERT
Ticket anzeigen -> SELECT
Ticketstatus ändern -> UPDATE
Ticket löschen -> DELETE
```

---

## Datenbankentwurf

Bevor man Tabellen erstellt, sollte man überlegen, welche Daten gebraucht werden.

Fragen:

```text
Welche Objekte gibt es?
Welche Eigenschaften haben diese Objekte?
Welche Beziehungen gibt es?
Welche Daten müssen eindeutig sein?
Welche Daten dürfen fehlen?
Welche Daten sollen nicht doppelt gespeichert werden?
```

Beispiel Bibliothek:

```text
Objekte:
- Bücher
- Autoren
- Mitglieder
- Ausleihen

Beziehungen:
- ein Mitglied kann mehrere Ausleihen haben
- ein Buch kann mehrere Exemplare haben
- ein Buch kann mehrere Autoren haben
```

Ein sauberer Datenbankentwurf verhindert viele spätere Probleme.

---

## Normalisierung kurz erklärt

Normalisierung bedeutet, Daten sinnvoll auf mehrere Tabellen aufzuteilen.

Ziel:

- weniger doppelte Daten
- weniger Fehler
- bessere Struktur
- klarere Beziehungen
- einfachere Pflege

Schlechtes Beispiel:

| loan_id | member_name | member_email    | book_title       | author  |
| ------- | ----------- | --------------- | ---------------- | ------- |
| 1       | Max         | max@example.com | Linux Grundlagen | Müller  |
| 2       | Max         | max@example.com | SQL Einstieg     | Schmidt |

Hier werden Max und seine E-Mail mehrfach gespeichert.

Besser:

```text
members
books
authors
loans
```

Dann wird Max nur einmal in `members` gespeichert.

---

## Typische Fehler

| Fehler                            | Problem                                  |
| --------------------------------- | ---------------------------------------- |
| alles in eine Tabelle schreiben   | viele doppelte Daten                     |
| keine Primärschlüssel nutzen      | Datensätze schwer eindeutig erkennbar    |
| falsche Datentypen wählen         | Daten passen nicht sauber                |
| `NULL` falsch verstehen           | fehlender Wert wird falsch interpretiert |
| Fremdschlüssel ignorieren         | Beziehungen bleiben unklar               |
| Tabellen nicht dokumentieren      | Struktur ist später schwer verständlich  |
| Namen als eindeutige Werte nutzen | Namen können doppelt vorkommen           |
| `DELETE` ohne `WHERE` nutzen      | zu viele Daten werden gelöscht           |
| `UPDATE` ohne `WHERE` nutzen      | zu viele Daten werden geändert           |
| Datenbank nur über GUI verstehen  | SQL-Grundlagen bleiben schwach           |

---

## FISI-Bezug

Für FISI ist Datenbankgrundwissen sehr nützlich.

In der Praxis kann man damit:

- Anwendungen mit Datenbankanbindung besser verstehen
- Datenbankcontainer mit Docker betreiben
- einfache SQL-Abfragen schreiben
- Adminer oder andere Datenbanktools nutzen
- Fehler in Datenbankverbindungen erkennen
- Tabellenstrukturen lesen
- Primärschlüssel und Fremdschlüssel verstehen
- Datenbankdokumentationen nachvollziehen
- mit Entwicklern besser kommunizieren
- Testdaten kontrollieren oder einfügen

Man muss nicht sofort komplexe Datenbankentwicklung beherrschen. Aber die Grundlagen sollten sitzen.

---

## Kurze Zusammenfassung

Eine Datenbank speichert Daten strukturiert und dauerhaft.

Relationale Datenbanken arbeiten mit Tabellen, Zeilen, Spalten und Beziehungen.

Wichtige Begriffe sind Tabelle, Datensatz, Spalte, Wert, Datentyp, Primärschlüssel, Fremdschlüssel, Constraint, NULL und SQL.

Für FISI ist dieses Wissen wichtig, weil viele IT-Systeme im Hintergrund Datenbanken verwenden. Wer die Grundlagen versteht, kann Anwendungen, Datenbankprojekte und Fehler besser nachvollziehen.
