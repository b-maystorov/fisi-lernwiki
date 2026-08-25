# 3. SQL-Grundlagen

In diesem Kapitel geht es um die Grundlagen von SQL.

SQL wird genutzt, um relationale Datenbanken zu erstellen, abzufragen und zu verwalten. Mit SQL kann man Tabellen anlegen, Daten einfügen, Daten lesen, Daten ändern und Daten löschen.

Für Fachinformatiker für Systemintegration ist SQL wichtig, weil viele IT-Systeme im Hintergrund mit Datenbanken arbeiten. Auch wenn man nicht als Datenbankentwickler arbeitet, sollte man einfache SQL-Befehle lesen, verstehen und anwenden können.

---

## Kurz erklärt

SQL bedeutet:

```text
Structured Query Language
```

SQL ist eine Abfragesprache für relationale Datenbanken.

Mit SQL kann man:

- Tabellen erstellen
- Daten einfügen
- Daten abfragen
- Daten filtern
- Daten sortieren
- Daten ändern
- Daten löschen
- Tabellen verbinden
- Regeln für Daten festlegen
- Benutzerrechte verwalten

Die wichtigsten SQL-Befehle am Anfang sind:

```text
CREATE
INSERT
SELECT
UPDATE
DELETE
WHERE
ORDER BY
LIMIT
JOIN
```

---

## SQL ist keine normale Programmiersprache

SQL funktioniert anders als Python, JavaScript oder Bash.

In einer Programmiersprache beschreibt man meistens Schritt für Schritt, was passieren soll.

In SQL beschreibt man eher, welche Daten man haben möchte.

Beispiel:

```sql
SELECT name, email
FROM users
WHERE id = 1;
```

Das bedeutet:

```text
Zeige mir name und email aus der Tabelle users, aber nur für den Datensatz mit id 1.
```

Man beschreibt also das gewünschte Ergebnis. Die Datenbank entscheidet intern, wie sie die Abfrage ausführt.

---

## Grundstruktur eines SQL-Befehls

Ein SQL-Befehl besteht oft aus mehreren Teilen.

Beispiel:

```sql
SELECT name, email
FROM users
WHERE active = true
ORDER BY name;
```

Bedeutung:

| Teil                  | Bedeutung                            |
| --------------------- | ------------------------------------ |
| `SELECT name, email`  | welche Spalten angezeigt werden      |
| `FROM users`          | aus welcher Tabelle die Daten kommen |
| `WHERE active = true` | welche Zeilen gefiltert werden       |
| `ORDER BY name`       | wie das Ergebnis sortiert wird       |

SQL-Befehle werden oft über mehrere Zeilen geschrieben, damit sie besser lesbar sind.

---

## Groß- und Kleinschreibung

SQL-Schlüsselwörter werden häufig großgeschrieben.

Beispiel:

```sql
SELECT name
FROM users
WHERE id = 1;
```

Das ist besser lesbar als:

```sql
select name from users where id = 1;
```

Viele Datenbanken akzeptieren beides.

Trotzdem ist diese Schreibweise üblich:

```text
SQL-Befehle groß
Tabellen und Spalten klein
```

Beispiel:

```sql
SELECT title, author_id
FROM books
WHERE id = 5;
```

---

## Semikolon

Viele SQL-Befehle enden mit einem Semikolon.

```sql
SELECT *
FROM users;
```

Das Semikolon zeigt:

```text
Dieser SQL-Befehl ist beendet.
```

In manchen Tools funktioniert ein einzelner Befehl auch ohne Semikolon. In Skripten und mehreren Befehlen ist das Semikolon aber wichtig.

Beispiel mit mehreren Befehlen:

```sql
SELECT *
FROM users;

SELECT *
FROM books;
```

---

## Kommentare in SQL

SQL unterstützt Kommentare.

Einzeiliger Kommentar:

```sql
-- Das ist ein Kommentar
SELECT *
FROM users;
```

Mehrzeiliger Kommentar:

```sql
/*
Das ist ein Kommentar
über mehrere Zeilen.
*/
SELECT *
FROM users;
```

Kommentare sind nützlich, um SQL-Skripte verständlicher zu machen.

---

## SQL-Kategorien

SQL-Befehle werden oft in Kategorien eingeteilt.

| Kategorie | Bedeutung                    | Beispiele                    |
| --------- | ---------------------------- | ---------------------------- |
| DDL       | Datenbankstruktur definieren | `CREATE`, `ALTER`, `DROP`    |
| DML       | Daten bearbeiten             | `INSERT`, `UPDATE`, `DELETE` |
| DQL       | Daten abfragen               | `SELECT`                     |
| DCL       | Rechte verwalten             | `GRANT`, `REVOKE`            |
| TCL       | Transaktionen steuern        | `COMMIT`, `ROLLBACK`         |

Für den Anfang sind besonders wichtig:

```text
DDL
DML
DQL
```

---

## DDL: Struktur definieren

DDL bedeutet:

```text
Data Definition Language
```

DDL-Befehle verändern die Struktur einer Datenbank.

Beispiele:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT
);
```

```sql
ALTER TABLE users
ADD COLUMN created_at DATE;
```

```sql
DROP TABLE users;
```

Wichtige DDL-Befehle:

| Befehl   | Bedeutung                       |
| -------- | ------------------------------- |
| `CREATE` | erstellt eine Datenbankstruktur |
| `ALTER`  | ändert eine bestehende Struktur |
| `DROP`   | löscht eine Struktur            |

DDL betrifft also Tabellen, Spalten, Datentypen und Regeln.

---

## DML: Daten bearbeiten

DML bedeutet:

```text
Data Manipulation Language
```

DML-Befehle bearbeiten Daten innerhalb der Tabellen.

Beispiele:

```sql
INSERT INTO users (id, name, email)
VALUES (1, 'Max', 'max@example.com');
```

```sql
UPDATE users
SET email = 'max.neu@example.com'
WHERE id = 1;
```

```sql
DELETE FROM users
WHERE id = 1;
```

Wichtige DML-Befehle:

| Befehl   | Bedeutung      |
| -------- | -------------- |
| `INSERT` | Daten einfügen |
| `UPDATE` | Daten ändern   |
| `DELETE` | Daten löschen  |

DML betrifft also die Inhalte der Tabellen.

---

## DQL: Daten abfragen

DQL bedeutet:

```text
Data Query Language
```

Der wichtigste DQL-Befehl ist:

```sql
SELECT
```

Beispiel:

```sql
SELECT name, email
FROM users;
```

Mit `SELECT` liest man Daten aus Tabellen.

`SELECT` wird oft mit weiteren Teilen kombiniert:

```sql
SELECT name, email
FROM users
WHERE active = true
ORDER BY name
LIMIT 10;
```

Das ist einer der wichtigsten SQL-Bereiche im Alltag.

---

## DCL: Rechte verwalten

DCL bedeutet:

```text
Data Control Language
```

DCL-Befehle verwalten Berechtigungen.

Beispiele:

```sql
GRANT SELECT ON users TO report_user;
```

```sql
REVOKE SELECT ON users FROM report_user;
```

Diese Befehle sind eher für Datenbankadministration wichtig.

Für den Einstieg muss man vor allem wissen:

```text
Datenbanken haben Benutzer und Rechte.
Nicht jeder Benutzer darf alles.
```

---

## TCL: Transaktionen steuern

TCL bedeutet:

```text
Transaction Control Language
```

Transaktionen fassen mehrere Datenbankoperationen logisch zusammen.

Beispiel:

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 100
WHERE id = 1;

UPDATE accounts
SET balance = balance + 100
WHERE id = 2;

COMMIT;
```

Wenn etwas schiefgeht:

```sql
ROLLBACK;
```

Wichtige Begriffe:

| Begriff    | Bedeutung                      |
| ---------- | ------------------------------ |
| `BEGIN`    | Transaktion starten            |
| `COMMIT`   | Änderungen dauerhaft speichern |
| `ROLLBACK` | Änderungen zurücknehmen        |

Transaktionen sind wichtig, damit Daten nicht halb geändert bleiben.

---

## SELECT

`SELECT` wird genutzt, um Daten abzufragen.

Alle Spalten:

```sql
SELECT *
FROM users;
```

Bestimmte Spalten:

```sql
SELECT name, email
FROM users;
```

Mit Bedingung:

```sql
SELECT name, email
FROM users
WHERE id = 1;
```

`SELECT` ist wahrscheinlich der wichtigste SQL-Befehl für den Alltag.

---

## SELECT \*

`SELECT *` bedeutet:

```text
Zeige alle Spalten.
```

Beispiel:

```sql
SELECT *
FROM users;
```

Das ist praktisch zum schnellen Testen.

In größeren Datenbanken sollte man aber oft gezielt Spalten auswählen:

```sql
SELECT name, email
FROM users;
```

Warum?

- Ergebnis ist übersichtlicher
- weniger unnötige Daten
- bessere Performance
- weniger Risiko bei sensiblen Spalten
- Abfrage ist klarer dokumentiert

Für Lernen und schnelle Prüfung ist `SELECT *` okay. Für saubere Abfragen sind konkrete Spalten besser.

---

## FROM

`FROM` gibt an, aus welcher Tabelle die Daten kommen.

Beispiel:

```sql
SELECT name
FROM users;
```

Hier kommen die Daten aus der Tabelle:

```text
users
```

Bei Joins können mehrere Tabellen beteiligt sein.

Beispiel:

```sql
SELECT users.name, orders.id
FROM users
JOIN orders
  ON users.id = orders.user_id;
```

---

## WHERE

`WHERE` filtert Zeilen.

Beispiel:

```sql
SELECT *
FROM users
WHERE id = 1;
```

Nur Datensätze mit `id = 1` werden angezeigt.

Weitere Beispiele:

```sql
SELECT *
FROM users
WHERE name = 'Max';
```

```sql
SELECT *
FROM products
WHERE price > 100;
```

```sql
SELECT *
FROM tickets
WHERE status = 'open';
```

`WHERE` ist auch bei `UPDATE` und `DELETE` sehr wichtig.

---

## Vergleichsoperatoren

In `WHERE`-Bedingungen nutzt man Vergleichsoperatoren.

| Operator | Bedeutung                       |
| -------- | ------------------------------- |
| `=`      | ist gleich                      |
| `<>`     | ist ungleich                    |
| `!=`     | ist ungleich, je nach Datenbank |
| `>`      | größer als                      |
| `<`      | kleiner als                     |
| `>=`     | größer oder gleich              |
| `<=`     | kleiner oder gleich             |

Beispiel:

```sql
SELECT *
FROM products
WHERE price >= 50;
```

---

## Logische Operatoren

Mehrere Bedingungen können kombiniert werden.

| Operator | Bedeutung                                |
| -------- | ---------------------------------------- |
| `AND`    | beide Bedingungen müssen wahr sein       |
| `OR`     | mindestens eine Bedingung muss wahr sein |
| `NOT`    | Bedingung wird umgedreht                 |

Beispiel mit `AND`:

```sql
SELECT *
FROM users
WHERE active = true
  AND city = 'Hamburg';
```

Beispiel mit `OR`:

```sql
SELECT *
FROM tickets
WHERE status = 'open'
   OR status = 'pending';
```

Beispiel mit `NOT`:

```sql
SELECT *
FROM users
WHERE NOT active = true;
```

---

## ORDER BY

`ORDER BY` sortiert das Ergebnis.

Aufsteigend:

```sql
SELECT *
FROM users
ORDER BY name;
```

Explizit aufsteigend:

```sql
SELECT *
FROM users
ORDER BY name ASC;
```

Absteigend:

```sql
SELECT *
FROM users
ORDER BY name DESC;
```

Beispiele:

```sql
SELECT *
FROM products
ORDER BY price DESC;
```

```sql
SELECT *
FROM tickets
ORDER BY created_at DESC;
```

---

## LIMIT

`LIMIT` begrenzt die Anzahl der Ergebnisse.

Beispiel:

```sql
SELECT *
FROM users
LIMIT 10;
```

Das zeigt nur 10 Datensätze.

Mit Sortierung:

```sql
SELECT *
FROM tickets
ORDER BY created_at DESC
LIMIT 5;
```

Das zeigt die 5 neuesten Tickets, wenn `created_at` korrekt gepflegt wird.

`LIMIT` ist besonders nützlich, wenn Tabellen groß sind.

---

## INSERT

`INSERT` fügt neue Daten ein.

Beispiel:

```sql
INSERT INTO users (id, name, email)
VALUES (1, 'Max', 'max@example.com');
```

Mehrere Zeilen:

```sql
INSERT INTO users (id, name, email)
VALUES
  (2, 'Lisa', 'lisa@example.com'),
  (3, 'Sara', 'sara@example.com');
```

Wichtig:

Die Werte müssen zu den Spalten passen.

---

## UPDATE

`UPDATE` ändert bestehende Daten.

Beispiel:

```sql
UPDATE users
SET email = 'max.neu@example.com'
WHERE id = 1;
```

Wichtig:

Bei `UPDATE` sollte fast immer ein `WHERE` genutzt werden.

Gefährlich:

```sql
UPDATE users
SET email = 'test@example.com';
```

Ohne `WHERE` würden alle Datensätze geändert.

---

## DELETE

`DELETE` löscht Daten.

Beispiel:

```sql
DELETE FROM users
WHERE id = 1;
```

Gefährlich:

```sql
DELETE FROM users;
```

Ohne `WHERE` werden alle Datensätze aus der Tabelle gelöscht.

Vor `DELETE` ist oft sinnvoll:

```sql
SELECT *
FROM users
WHERE id = 1;
```

Erst prüfen, dann löschen.

---

## CREATE TABLE

`CREATE TABLE` erstellt eine neue Tabelle.

Beispiel:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT UNIQUE
);
```

Wichtige Teile:

| Teil                 | Bedeutung                           |
| -------------------- | ----------------------------------- |
| `CREATE TABLE users` | Tabelle `users` erstellen           |
| `id INTEGER`         | Spalte `id` als Zahl                |
| `PRIMARY KEY`        | eindeutige Kennung                  |
| `name TEXT`          | Spalte `name` als Text              |
| `NOT NULL`           | Wert darf nicht fehlen              |
| `email TEXT UNIQUE`  | E-Mail darf nicht doppelt vorkommen |

---

## ALTER TABLE

`ALTER TABLE` ändert eine bestehende Tabelle.

Beispiel:

```sql
ALTER TABLE users
ADD COLUMN created_at DATE;
```

Das fügt eine neue Spalte hinzu.

Weitere mögliche Änderungen:

```text
Spalte hinzufügen
Spalte ändern
Spalte löschen
Constraint hinzufügen
Constraint entfernen
```

Je nach Datenbanksystem unterscheiden sich manche Details.

---

## DROP TABLE

`DROP TABLE` löscht eine Tabelle.

Beispiel:

```sql
DROP TABLE users;
```

Das ist gefährlich, weil die Tabellenstruktur und die enthaltenen Daten gelöscht werden.

Für Lernprojekte okay, aber in echten Systemen sehr vorsichtig nutzen.

Vorher prüfen:

```sql
SELECT *
FROM users
LIMIT 10;
```

Und bei echten Daten:

```text
Backup prüfen.
Rechte prüfen.
Auswirkungen prüfen.
```

---

## NULL in SQL

`NULL` bedeutet:

```text
kein Wert vorhanden
```

Das ist nicht dasselbe wie:

```text
0
false
leerer Text
```

Falsch:

```sql
SELECT *
FROM users
WHERE phone = NULL;
```

Richtig:

```sql
SELECT *
FROM users
WHERE phone IS NULL;
```

Nicht NULL:

```sql
SELECT *
FROM users
WHERE phone IS NOT NULL;
```

`NULL` muss in SQL besonders behandelt werden.

---

## IN

`IN` prüft, ob ein Wert in einer Liste enthalten ist.

Beispiel:

```sql
SELECT *
FROM users
WHERE city IN ('Hamburg', 'Berlin', 'Kiel');
```

Das ist kürzer als:

```sql
SELECT *
FROM users
WHERE city = 'Hamburg'
   OR city = 'Berlin'
   OR city = 'Kiel';
```

`IN` wird auch oft mit Subqueries genutzt.

---

## LIKE

`LIKE` wird für einfache Textsuche genutzt.

Beispiel:

```sql
SELECT *
FROM users
WHERE name LIKE 'Ma%';
```

Bedeutung:

```text
Name beginnt mit Ma
```

Häufige Muster:

| Muster      | Bedeutung      |
| ----------- | -------------- |
| `'Ma%'`     | beginnt mit Ma |
| `'%son'`    | endet mit son  |
| `'%admin%'` | enthält admin  |

Je nach Datenbank kann Groß-/Kleinschreibung unterschiedlich behandelt werden.

---

## BETWEEN

`BETWEEN` prüft einen Bereich.

Beispiel:

```sql
SELECT *
FROM products
WHERE price BETWEEN 10 AND 50;
```

Das bedeutet:

```text
price ist zwischen 10 und 50
```

Auch mit Datum:

```sql
SELECT *
FROM loans
WHERE loan_date BETWEEN '2026-08-01' AND '2026-08-31';
```

---

## Aliase

Aliase geben Tabellen oder Spalten einen kürzeren Namen.

Spaltenalias:

```sql
SELECT name AS username
FROM users;
```

Tabellenalias:

```sql
SELECT u.name
FROM users AS u;
```

Bei Joins sind Aliase besonders praktisch:

```sql
SELECT u.name, o.id
FROM users AS u
JOIN orders AS o
  ON u.id = o.user_id;
```

Dadurch wird die Abfrage kürzer und lesbarer.

---

## Funktionen

SQL hat viele eingebaute Funktionen.

Beispiele:

| Funktion  | Bedeutung        |
| --------- | ---------------- |
| `COUNT()` | zählt Datensätze |
| `MIN()`   | kleinster Wert   |
| `MAX()`   | größter Wert     |
| `AVG()`   | Durchschnitt     |
| `SUM()`   | Summe            |

Beispiel:

```sql
SELECT COUNT(*)
FROM users;
```

Beispiel:

```sql
SELECT MAX(price)
FROM products;
```

Diese Funktionen werden oft mit `GROUP BY` kombiniert.

---

## GROUP BY kurz erklärt

`GROUP BY` gruppiert Daten.

Beispiel:

```sql
SELECT city, COUNT(*)
FROM users
GROUP BY city;
```

Das Ergebnis könnte zeigen:

| city    | count |
| ------- | ----- |
| Hamburg | 12    |
| Berlin  | 8     |
| Kiel    | 3     |

`GROUP BY` ist nützlich für Auswertungen.

---

## JOIN kurz erklärt

`JOIN` verbindet Tabellen.

Beispiel:

```sql
SELECT members.name, loans.loan_date
FROM members
JOIN loans
  ON members.id = loans.member_id;
```

Hier werden Mitglieder mit ihren Ausleihen verbunden.

Wichtig:

Joins funktionieren sauber, wenn die Tabellen gute Schlüssel und Beziehungen haben.

---

## Subquery kurz erklärt

Eine Subquery ist eine Abfrage innerhalb einer anderen Abfrage.

Beispiel:

```sql
SELECT *
FROM users
WHERE id IN (
  SELECT user_id
  FROM orders
);
```

Das bedeutet:

```text
Zeige Benutzer, deren id in der Bestell-Tabelle vorkommt.
```

Subqueries sind nützlich, wenn man Ergebnisse einer Abfrage als Bedingung für eine andere Abfrage nutzt.

---

## CRUD noch einmal

CRUD ist ein wichtiges Grundkonzept.

| CRUD   | Bedeutung       | SQL      |
| ------ | --------------- | -------- |
| Create | Daten erstellen | `INSERT` |
| Read   | Daten lesen     | `SELECT` |
| Update | Daten ändern    | `UPDATE` |
| Delete | Daten löschen   | `DELETE` |

Beispiel:

```sql
INSERT INTO users (id, name)
VALUES (1, 'Max');

SELECT *
FROM users;

UPDATE users
SET name = 'Max Müller'
WHERE id = 1;

DELETE FROM users
WHERE id = 1;
```

Fast jede Anwendung nutzt diese vier Grundoperationen.

---

## SQL in Dateien

SQL-Befehle können in Dateien gespeichert werden.

Beispiel:

```text
schema.sql
sample_data.sql
queries.sql
```

Typische Nutzung:

| Datei             | Inhalt           |
| ----------------- | ---------------- |
| `schema.sql`      | Tabellenstruktur |
| `sample_data.sql` | Beispieldaten    |
| `queries.sql`     | Beispielabfragen |

Das ist besonders praktisch bei Projekten mit Git und Docker.

Beispiel:

```text
schema.sql erstellt Tabellen.
sample_data.sql fügt Testdaten ein.
README.md erklärt die Nutzung.
```

---

## SQL und Docker

Datenbanken können mit Docker gestartet werden.

Beispiel:

```bash
docker compose up -d
```

Danach kann man SQL ausführen, zum Beispiel in PostgreSQL:

```bash
docker compose exec db psql -U postgres -d app
```

Oder eine SQL-Datei ausführen:

```bash
docker compose exec db psql -U postgres -d app -f /schema.sql
```

Docker hilft, Datenbankumgebungen reproduzierbar aufzubauen.

---

## Typische Fehler

| Fehler                              | Problem                                       |
| ----------------------------------- | --------------------------------------------- |
| `WHERE` bei `UPDATE` vergessen      | alle Datensätze werden geändert               |
| `WHERE` bei `DELETE` vergessen      | alle Datensätze werden gelöscht               |
| `SELECT *` immer nutzen             | unübersichtlich und oft unnötig               |
| `NULL` mit `=` vergleichen          | funktioniert nicht wie erwartet               |
| falsche Datentypen nutzen           | Daten werden unsauber gespeichert             |
| Semikolon vergessen                 | besonders bei mehreren Befehlen problematisch |
| falsche Tabellen- oder Spaltennamen | SQL-Fehler                                    |
| Strings ohne Anführungszeichen      | Syntaxfehler                                  |
| `AND` und `OR` falsch kombinieren   | falsche Ergebnisse                            |
| Joins ohne klare Beziehung          | falsche oder zu große Ergebnisse              |

---

## Gute SQL-Arbeitsweise

Eine saubere Arbeitsweise:

1. Tabellenstruktur prüfen
2. mit `SELECT` Daten anschauen
3. Filter mit `WHERE` testen
4. bei Änderungen zuerst mit `SELECT` prüfen
5. `UPDATE` und `DELETE` immer vorsichtig nutzen
6. kleine Abfragen schreiben und testen
7. Joins Schritt für Schritt aufbauen
8. Fehlermeldungen genau lesen
9. SQL-Dateien sauber dokumentieren
10. keine echten Passwörter oder sensiblen Daten veröffentlichen

Wichtiger Merksatz:

```text
Erst SELECT, dann UPDATE oder DELETE.
```

---

## Praktische Beispiele

### Beispiel 1: Tabelle ansehen

```sql
SELECT *
FROM users
LIMIT 10;
```

### Beispiel 2: Benutzer filtern

```sql
SELECT name, email
FROM users
WHERE city = 'Hamburg';
```

### Beispiel 3: Datensatz ändern

```sql
UPDATE users
SET email = 'neu@example.com'
WHERE id = 1;
```

### Beispiel 4: Datensatz löschen

```sql
DELETE FROM users
WHERE id = 1;
```

---

## FISI-Bezug

Für FISI ist SQL-Grundwissen wichtig, weil viele IT-Systeme Datenbanken nutzen.

In der Praxis hilft SQL bei:

- Datenbankprojekte verstehen
- einfache Abfragen schreiben
- Daten kontrollieren
- Fehler in Anwendungen besser einordnen
- Datenbankcontainer mit Docker nutzen
- Adminer, psql oder andere Tools verwenden
- Tabellenstrukturen lesen
- technische Dokumentation schreiben
- mit Entwicklern und Administratoren kommunizieren

Ein FISI muss nicht sofort komplexe Datenbankoptimierung beherrschen. Aber einfache SQL-Befehle, Tabellen, Schlüssel, Filter und Datenänderungen sollten verstanden werden.

---

## Kurze Zusammenfassung

SQL ist die Sprache für relationale Datenbanken.

Wichtige Befehle sind `CREATE`, `INSERT`, `SELECT`, `UPDATE`, `DELETE`, `WHERE`, `ORDER BY`, `LIMIT` und `JOIN`.

SQL-Befehle lassen sich in Kategorien wie DDL, DML, DQL, DCL und TCL einteilen.

Für die Praxis sind besonders `SELECT`, `INSERT`, `UPDATE` und `DELETE` wichtig. Bei Änderungen und Löschungen sollte man immer vorsichtig mit `WHERE` arbeiten.

Für FISI ist SQL wichtig, weil viele Anwendungen, Datenbankprojekte und IT-Systeme im Hintergrund mit relationalen Datenbanken arbeiten.
