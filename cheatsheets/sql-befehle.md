# SQL-Befehle Cheatsheet

Dieses Cheatsheet enthält wichtige SQL-Befehle für Datenbankabfragen, Tabellen, Datensätze, Filter, Joins und einfache Datenverwaltung.

SQL bedeutet **Structured Query Language**. Mit SQL kann man Daten in relationalen Datenbanken abfragen, einfügen, ändern und löschen.

Dieses Cheatsheet passt besonders zu den Themen Datenbanken, LF5 und praktischer Arbeit mit Tabellen.

---

## Grundbegriffe

| Begriff           | Bedeutung                                       |
| ----------------- | ----------------------------------------------- |
| Datenbank         | Sammlung strukturierter Daten                   |
| Tabelle           | Datenstruktur mit Zeilen und Spalten            |
| Zeile / Datensatz | ein einzelner Eintrag in einer Tabelle          |
| Spalte / Attribut | Eigenschaft eines Datensatzes                   |
| Primärschlüssel   | eindeutige ID eines Datensatzes                 |
| Fremdschlüssel    | Verweis auf eine andere Tabelle                 |
| SQL               | Sprache zur Arbeit mit relationalen Datenbanken |

Beispiel:

```text
Tabelle: customers

id | name  | country
---|-------|--------
1  | Ava   | Germany
2  | Ben   | Spain
3  | Cara  | Germany
```

---

## SELECT

`SELECT` wird genutzt, um Daten abzufragen.

Alle Spalten anzeigen:

```sql
SELECT *
FROM customers;
```

Bestimmte Spalten anzeigen:

```sql
SELECT name, country
FROM customers;
```

Bedeutung:

| Teil     | Bedeutung                            |
| -------- | ------------------------------------ |
| `SELECT` | welche Spalten angezeigt werden      |
| `FROM`   | aus welcher Tabelle die Daten kommen |
| `*`      | alle Spalten                         |

---

## WHERE

`WHERE` filtert Datensätze.

```sql
SELECT *
FROM customers
WHERE country = 'Germany';
```

Nur Kunden aus Deutschland werden angezeigt.

Weitere Beispiele:

```sql
SELECT *
FROM customers
WHERE age >= 18;
```

```sql
SELECT *
FROM customers
WHERE name = 'Ava';
```

---

## Vergleichsoperatoren

| Operator | Bedeutung           |
| -------- | ------------------- |
| `=`      | gleich              |
| `!=`     | ungleich            |
| `<>`     | ungleich            |
| `>`      | größer als          |
| `<`      | kleiner als         |
| `>=`     | größer oder gleich  |
| `<=`     | kleiner oder gleich |

Beispiel:

```sql
SELECT *
FROM products
WHERE price > 100;
```

---

## AND, OR, NOT

Mehrere Bedingungen kombinieren:

```sql
SELECT *
FROM customers
WHERE country = 'Germany'
AND age >= 18;
```

Oder-Bedingung:

```sql
SELECT *
FROM customers
WHERE country = 'Germany'
OR country = 'Austria';
```

Negation:

```sql
SELECT *
FROM customers
WHERE NOT country = 'Germany';
```

---

## ORDER BY

`ORDER BY` sortiert Ergebnisse.

Aufsteigend:

```sql
SELECT *
FROM customers
ORDER BY name ASC;
```

Absteigend:

```sql
SELECT *
FROM customers
ORDER BY age DESC;
```

Wenn `ASC` oder `DESC` fehlt, wird meistens aufsteigend sortiert.

---

## LIMIT

`LIMIT` begrenzt die Anzahl der Ergebnisse.

```sql
SELECT *
FROM customers
LIMIT 10;
```

Beispiel mit Sortierung:

```sql
SELECT *
FROM customers
ORDER BY age DESC
LIMIT 5;
```

Das zeigt die fünf ältesten Kunden.

---

## LIKE

`LIKE` sucht nach Mustern.

```sql
SELECT *
FROM customers
WHERE name LIKE 'A%';
```

Bedeutung:

| Muster   | Bedeutung     |
| -------- | ------------- |
| `'A%'`   | beginnt mit A |
| `'%a'`   | endet mit a   |
| `'%ar%'` | enthält ar    |

Beispiel:

```sql
SELECT *
FROM customers
WHERE email LIKE '%gmail.com';
```

---

## IN

`IN` prüft, ob ein Wert in einer Liste enthalten ist.

```sql
SELECT *
FROM customers
WHERE country IN ('Germany', 'Austria', 'Switzerland');
```

Das ist kürzer als viele `OR`-Bedingungen.

Vergleich:

```sql
WHERE country = 'Germany'
OR country = 'Austria'
OR country = 'Switzerland'
```

---

## BETWEEN

`BETWEEN` prüft einen Bereich.

```sql
SELECT *
FROM products
WHERE price BETWEEN 50 AND 100;
```

Das bedeutet:

```text
Preis zwischen 50 und 100
```

Auch mit Datum möglich:

```sql
SELECT *
FROM orders
WHERE order_date BETWEEN '2026-01-01' AND '2026-12-31';
```

---

## NULL

`NULL` bedeutet: kein Wert vorhanden.

Wichtig:

Für `NULL` nutzt man nicht `=`, sondern `IS`.

Richtig:

```sql
SELECT *
FROM customers
WHERE phone IS NULL;
```

Richtig:

```sql
SELECT *
FROM customers
WHERE phone IS NOT NULL;
```

Falsch:

```sql
SELECT *
FROM customers
WHERE phone = NULL;
```

---

## INSERT

`INSERT` fügt neue Datensätze ein.

```sql
INSERT INTO customers (name, country, age)
VALUES ('Ava', 'Germany', 25);
```

Mehrere Datensätze:

```sql
INSERT INTO customers (name, country, age)
VALUES
('Ben', 'Spain', 30),
('Cara', 'Germany', 22);
```

Wichtig:

Die Reihenfolge der Spalten muss zur Reihenfolge der Werte passen.

---

## UPDATE

`UPDATE` ändert bestehende Datensätze.

```sql
UPDATE customers
SET country = 'Austria'
WHERE id = 1;
```

Wichtig:

Bei `UPDATE` fast immer `WHERE` nutzen.

Gefährlich:

```sql
UPDATE customers
SET country = 'Austria';
```

Ohne `WHERE` werden alle Zeilen geändert.

---

## DELETE

`DELETE` löscht Datensätze.

```sql
DELETE FROM customers
WHERE id = 1;
```

Wichtig:

Bei `DELETE` fast immer `WHERE` nutzen.

Gefährlich:

```sql
DELETE FROM customers;
```

Das löscht alle Datensätze aus der Tabelle.

---

## CREATE TABLE

`CREATE TABLE` erstellt eine neue Tabelle.

```sql
CREATE TABLE customers (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  country TEXT,
  age INTEGER
);
```

Bedeutung:

| Teil          | Bedeutung                 |
| ------------- | ------------------------- |
| `id`          | Spaltenname               |
| `INTEGER`     | Datentyp                  |
| `PRIMARY KEY` | eindeutiger Schlüssel     |
| `TEXT`        | Textwert                  |
| `NOT NULL`    | Wert darf nicht leer sein |

---

## Datentypen

Häufige Datentypen:

| Datentyp     | Bedeutung                 |
| ------------ | ------------------------- |
| `INTEGER`    | ganze Zahl                |
| `TEXT`       | Text                      |
| `VARCHAR(n)` | Text mit maximaler Länge  |
| `DECIMAL`    | genaue Zahl, oft für Geld |
| `REAL`       | Kommazahl                 |
| `DATE`       | Datum                     |
| `TIMESTAMP`  | Datum und Uhrzeit         |
| `BOOLEAN`    | wahr/falsch               |

Beispiel:

```sql
CREATE TABLE products (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  price DECIMAL,
  active BOOLEAN
);
```

---

## PRIMARY KEY

Ein Primärschlüssel identifiziert jeden Datensatz eindeutig.

```sql
CREATE TABLE customers (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL
);
```

Typisch ist eine Spalte wie:

```text
id
```

Der Primärschlüssel darf nicht doppelt vorkommen.

---

## FOREIGN KEY

Ein Fremdschlüssel verweist auf eine andere Tabelle.

Beispiel:

```sql
CREATE TABLE orders (
  id INTEGER PRIMARY KEY,
  customer_id INTEGER NOT NULL,
  order_date DATE,
  FOREIGN KEY (customer_id) REFERENCES customers(id)
);
```

Bedeutung:

```text
orders.customer_id verweist auf customers.id
```

So werden Tabellen miteinander verbunden.

---

## JOIN

`JOIN` verbindet Daten aus mehreren Tabellen.

Beispiel:

```sql
SELECT orders.id, customers.name, orders.order_date
FROM orders
JOIN customers
ON orders.customer_id = customers.id;
```

Bedeutung:

| Teil                                | Bedeutung                             |
| ----------------------------------- | ------------------------------------- |
| `JOIN customers`                    | Tabelle customers verbinden           |
| `ON`                                | Verbindungsbedingung                  |
| `orders.customer_id = customers.id` | Fremdschlüssel trifft Primärschlüssel |

---

## INNER JOIN

`INNER JOIN` zeigt nur passende Datensätze aus beiden Tabellen.

```sql
SELECT customers.name, orders.order_date
FROM customers
INNER JOIN orders
ON customers.id = orders.customer_id;
```

Nur Kunden mit passenden Bestellungen werden angezeigt.

---

## LEFT JOIN

`LEFT JOIN` zeigt alle Datensätze aus der linken Tabelle, auch wenn rechts nichts passt.

```sql
SELECT customers.name, orders.order_date
FROM customers
LEFT JOIN orders
ON customers.id = orders.customer_id;
```

Damit sieht man auch Kunden ohne Bestellung.

---

## GROUP BY

`GROUP BY` gruppiert Datensätze.

Beispiel:

```sql
SELECT country, COUNT(*) AS customer_count
FROM customers
GROUP BY country;
```

Das zählt Kunden pro Land.

Ergebnis-Idee:

```text
Germany | 5
Spain   | 2
Austria | 3
```

---

## Aggregatfunktionen

| Funktion      | Bedeutung      |
| ------------- | -------------- |
| `COUNT(*)`    | zählt Zeilen   |
| `SUM(spalte)` | summiert Werte |
| `AVG(spalte)` | Durchschnitt   |
| `MIN(spalte)` | kleinster Wert |
| `MAX(spalte)` | größter Wert   |

Beispiele:

```sql
SELECT COUNT(*)
FROM customers;
```

```sql
SELECT AVG(price)
FROM products;
```

```sql
SELECT MAX(age)
FROM customers;
```

---

## HAVING

`HAVING` filtert Gruppen.

```sql
SELECT country, COUNT(*) AS customer_count
FROM customers
GROUP BY country
HAVING COUNT(*) > 2;
```

Wichtig:

| Befehl   | Nutzung                              |
| -------- | ------------------------------------ |
| `WHERE`  | filtert Zeilen vor der Gruppierung   |
| `HAVING` | filtert Gruppen nach der Gruppierung |

---

## Aliase mit AS

`AS` gibt Spalten oder Tabellen einen Alias.

```sql
SELECT name AS customer_name
FROM customers;
```

Bei Aggregaten:

```sql
SELECT country, COUNT(*) AS customer_count
FROM customers
GROUP BY country;
```

Aliase machen Ergebnisse lesbarer.

---

## DISTINCT

`DISTINCT` entfernt doppelte Werte aus dem Ergebnis.

```sql
SELECT DISTINCT country
FROM customers;
```

Das zeigt jedes Land nur einmal.

---

## ALTER TABLE

`ALTER TABLE` ändert eine bestehende Tabelle.

Spalte hinzufügen:

```sql
ALTER TABLE customers
ADD COLUMN email TEXT;
```

Je nach Datenbank sind weitere Änderungen unterschiedlich unterstützt.

Beispiel:

```sql
ALTER TABLE products
ADD COLUMN created_at DATE;
```

---

## DROP TABLE

`DROP TABLE` löscht eine Tabelle.

```sql
DROP TABLE customers;
```

Vorsicht:

Die Tabelle und ihre Daten werden gelöscht.

Oft sicherer:

```sql
DROP TABLE IF EXISTS customers;
```

Trotzdem nur nutzen, wenn klar ist, dass die Tabelle wirklich gelöscht werden soll.

---

## Constraints

Constraints sind Regeln für Daten.

| Constraint    | Bedeutung                         |
| ------------- | --------------------------------- |
| `PRIMARY KEY` | eindeutiger Primärschlüssel       |
| `FOREIGN KEY` | Verweis auf andere Tabelle        |
| `NOT NULL`    | Wert muss vorhanden sein          |
| `UNIQUE`      | Wert darf nicht doppelt vorkommen |
| `CHECK`       | prüft Bedingung                   |
| `DEFAULT`     | Standardwert                      |

Beispiel:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  age INTEGER CHECK (age >= 0),
  active BOOLEAN DEFAULT true
);
```

---

## Transaktionen

Eine Transaktion fasst mehrere Befehle zusammen.

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

Wenn etwas falsch läuft:

```sql
ROLLBACK;
```

Bedeutung:

| Befehl     | Bedeutung               |
| ---------- | ----------------------- |
| `BEGIN`    | Transaktion starten     |
| `COMMIT`   | Änderungen speichern    |
| `ROLLBACK` | Änderungen zurücknehmen |

---

## Reihenfolge einer SELECT-Abfrage

Typische Reihenfolge:

```sql
SELECT spalten
FROM tabelle
JOIN andere_tabelle
ON bedingung
WHERE filter
GROUP BY spalten
HAVING gruppenfilter
ORDER BY spalten
LIMIT anzahl;
```

Beispiel:

```sql
SELECT country, COUNT(*) AS customer_count
FROM customers
WHERE age >= 18
GROUP BY country
HAVING COUNT(*) >= 2
ORDER BY customer_count DESC
LIMIT 5;
```

---

## CRUD

CRUD beschreibt die vier Grundoperationen.

| Buchstabe | Bedeutung | SQL      |
| --------- | --------- | -------- |
| C         | Create    | `INSERT` |
| R         | Read      | `SELECT` |
| U         | Update    | `UPDATE` |
| D         | Delete    | `DELETE` |

Beispiele:

```sql
INSERT INTO customers (name) VALUES ('Ava');
```

```sql
SELECT * FROM customers;
```

```sql
UPDATE customers SET name = 'Eva' WHERE id = 1;
```

```sql
DELETE FROM customers WHERE id = 1;
```

---

## Sichere Arbeitsweise

Vor `UPDATE` oder `DELETE` zuerst mit `SELECT` prüfen.

Beispiel:

```sql
SELECT *
FROM customers
WHERE id = 1;
```

Dann erst:

```sql
UPDATE customers
SET country = 'Germany'
WHERE id = 1;
```

Oder:

```sql
DELETE FROM customers
WHERE id = 1;
```

Wichtige Regel:

```text
Erst prüfen, dann ändern oder löschen.
```

---

## Häufige Fehler

| Fehler                                  | Problem                     |
| --------------------------------------- | --------------------------- |
| `WHERE` bei `UPDATE` vergessen          | alle Zeilen werden geändert |
| `WHERE` bei `DELETE` vergessen          | alle Zeilen werden gelöscht |
| `NULL` mit `=` vergleichen              | funktioniert nicht korrekt  |
| Spaltennamen falsch schreiben           | SQL-Fehler                  |
| Komma vergessen                         | Syntaxfehler                |
| Text ohne Anführungszeichen             | Syntaxfehler                |
| falsche JOIN-Bedingung                  | falsche Ergebnisse          |
| `GROUP BY` nicht verstanden             | Aggregatfehler              |
| Primärschlüssel doppelt vergeben        | Constraint-Fehler           |
| Fremdschlüssel ohne passenden Datensatz | Integritätsfehler           |

---

## Praktische Beispiele

### Beispiel 1: Kunden anzeigen

```sql
SELECT id, name, country
FROM customers
ORDER BY name;
```

### Beispiel 2: Kunden aus Deutschland

```sql
SELECT *
FROM customers
WHERE country = 'Germany';
```

### Beispiel 3: Anzahl Kunden pro Land

```sql
SELECT country, COUNT(*) AS customer_count
FROM customers
GROUP BY country
ORDER BY customer_count DESC;
```

### Beispiel 4: Bestellungen mit Kundennamen

```sql
SELECT orders.id, customers.name, orders.order_date
FROM orders
JOIN customers
ON orders.customer_id = customers.id;
```

---

## Gefährliche Befehle

| Befehl                             | Risiko                                        |
| ---------------------------------- | --------------------------------------------- |
| `DELETE FROM table;`               | löscht alle Datensätze                        |
| `UPDATE table SET column = value;` | ändert alle Datensätze                        |
| `DROP TABLE table;`                | löscht komplette Tabelle                      |
| `DROP DATABASE database;`          | löscht komplette Datenbank                    |
| `TRUNCATE TABLE table;`            | leert Tabelle sehr schnell                    |
| falscher `JOIN`                    | erzeugt falsche oder viel zu große Ergebnisse |

Vor gefährlichen Befehlen immer prüfen:

```sql
SELECT *
FROM table
WHERE bedingung;
```

---

## Nützliche Befehle kompakt

| Befehl                      | Bedeutung                 |
| --------------------------- | ------------------------- |
| `SELECT * FROM table;`      | alle Daten anzeigen       |
| `SELECT column FROM table;` | bestimmte Spalte anzeigen |
| `WHERE`                     | filtern                   |
| `ORDER BY`                  | sortieren                 |
| `LIMIT`                     | Ergebnis begrenzen        |
| `INSERT INTO`               | Daten einfügen            |
| `UPDATE`                    | Daten ändern              |
| `DELETE FROM`               | Daten löschen             |
| `CREATE TABLE`              | Tabelle erstellen         |
| `ALTER TABLE`               | Tabelle ändern            |
| `DROP TABLE`                | Tabelle löschen           |
| `JOIN`                      | Tabellen verbinden        |
| `GROUP BY`                  | gruppieren                |
| `COUNT(*)`                  | Zeilen zählen             |
| `SUM()`                     | Werte summieren           |
| `AVG()`                     | Durchschnitt berechnen    |
| `MIN()`                     | kleinsten Wert finden     |
| `MAX()`                     | größten Wert finden       |
| `IS NULL`                   | NULL-Werte finden         |
| `IS NOT NULL`               | nicht leere Werte finden  |

---

## Kurze Zusammenfassung

Dieses Cheatsheet enthält wichtige SQL-Befehle für relationale Datenbanken.

Die wichtigsten Befehle für den Anfang sind:

```sql
SELECT
FROM
WHERE
ORDER BY
LIMIT
INSERT INTO
UPDATE
DELETE FROM
CREATE TABLE
JOIN
GROUP BY
COUNT
```

Für FISI ist SQL wichtig, weil viele Anwendungen und IT-Systeme Datenbanken nutzen. Auch wenn man nicht als Entwickler arbeitet, sollte man Tabellen, Schlüssel, Abfragen und einfache Datenänderungen verstehen.
