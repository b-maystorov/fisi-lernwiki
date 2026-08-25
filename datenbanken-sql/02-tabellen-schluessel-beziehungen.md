# 2. Tabellen, Schlüssel und Beziehungen

In diesem Kapitel geht es um Tabellen, Schlüssel und Beziehungen in relationalen Datenbanken.

Relationale Datenbanken bestehen nicht nur aus einzelnen Tabellen. Der wichtige Punkt ist, dass Tabellen sinnvoll miteinander verbunden werden. Dadurch können Daten sauber gespeichert werden, ohne alles mehrfach einzutragen.

Für Fachinformatiker für Systemintegration ist dieses Wissen wichtig, weil viele Anwendungen mit relationalen Datenbanken arbeiten. Man muss Tabellenstrukturen lesen, Primärschlüssel und Fremdschlüssel verstehen und erkennen können, wie Daten zusammenhängen.

---

## Kurz erklärt

Eine Tabelle speichert gleichartige Daten.

Beispiele:

```text
users
books
members
loans
orders
products
departments
employees
```

Schlüssel sorgen dafür, dass Datensätze eindeutig erkannt und miteinander verbunden werden können.

Die wichtigsten Schlüssel sind:

| Schlüssel                   | Bedeutung                                            |
| --------------------------- | ---------------------------------------------------- |
| Primärschlüssel             | eindeutige Kennung eines Datensatzes                 |
| Fremdschlüssel              | Verweis auf einen Datensatz in einer anderen Tabelle |
| zusammengesetzter Schlüssel | Schlüssel aus mehreren Spalten                       |

Beziehungen beschreiben, wie Tabellen miteinander verbunden sind.

Die wichtigsten Beziehungstypen sind:

```text
1:1
1:n
n:m
```

---

## Tabellen sauber aufbauen

Eine Tabelle sollte immer eine klare Aufgabe haben.

Beispiel:

Eine Tabelle `members` speichert Mitglieder.

```sql
CREATE TABLE members (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT UNIQUE
);
```

Diese Tabelle speichert keine Bücher, keine Ausleihen und keine Autoren. Sie speichert nur Mitglieder.

Das ist wichtig, damit Daten logisch getrennt bleiben.

Schlechte Tabelle:

```text
member_name
member_email
book_title
author_name
loan_date
```

Hier werden Mitglied, Buch, Autor und Ausleihe in eine Tabelle gemischt.

Besser:

```text
members
books
authors
loans
```

Jede Tabelle hat eine eigene Aufgabe.

---

## Spalten in Tabellen

Spalten beschreiben Eigenschaften eines Datensatzes.

Beispiel Tabelle `members`:

| Spalte       | Bedeutung                  |
| ------------ | -------------------------- |
| `id`         | eindeutige Mitgliedsnummer |
| `name`       | Name des Mitglieds         |
| `email`      | E-Mail-Adresse             |
| `created_at` | Erstellungsdatum           |

Eine gute Spalte sollte:

- einen klaren Namen haben
- einen passenden Datentyp haben
- nur eine Information speichern
- nicht mehrere Werte in einem Feld mischen

Schlecht:

```text
address = "Musterstraße 5, 20095 Hamburg, Deutschland"
```

Besser, wenn man die Daten einzeln auswerten muss:

```text
street
house_number
postal_code
city
country
```

---

## Zeilen als Datensätze

Eine Zeile ist ein vollständiger Datensatz.

Beispiel:

| id  | name       | email           |
| --- | ---------- | --------------- |
| 1   | Max Müller | max@example.com |

Diese Zeile beschreibt genau ein Mitglied.

Wichtig:

Eine Tabelle sollte nicht mehrere unterschiedliche Dinge in einer Zeile mischen.

Beispiel bei `members`:

```text
Eine Zeile = ein Mitglied
```

Beispiel bei `books`:

```text
Eine Zeile = ein Buch
```

Beispiel bei `loans`:

```text
Eine Zeile = eine Ausleihe
```

---

## Primärschlüssel

Ein Primärschlüssel ist die eindeutige Kennung eines Datensatzes.

Sehr häufig wird dafür eine Spalte `id` verwendet.

```sql
CREATE TABLE members (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL
);
```

Beispiel:

| id  | name |
| --- | ---- |
| 1   | Max  |
| 2   | Lisa |
| 3   | Max  |

Der Name ist nicht eindeutig, weil zwei Personen gleich heißen können.

Die `id` ist eindeutig.

Deshalb sollte man für technische Beziehungen nicht den Namen verwenden, sondern den Primärschlüssel.

---

## Eigenschaften eines Primärschlüssels

Ein Primärschlüssel sollte:

- eindeutig sein
- nicht leer sein
- sich nicht ständig ändern
- jeden Datensatz klar identifizieren
- für Beziehungen nutzbar sein

Beispiele für gute Primärschlüssel:

```text
id
user_id
book_id
member_id
order_id
```

Beispiele für problematische Primärschlüssel:

```text
name
email
phone_number
address
```

Eine E-Mail-Adresse kann zwar eindeutig sein, aber sie kann sich ändern. Deshalb ist eine technische ID oft stabiler.

---

## Fremdschlüssel

Ein Fremdschlüssel verbindet eine Tabelle mit einer anderen Tabelle.

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

| id  | member_id | loan_date  |
| --- | --------- | ---------- |
| 1   | 2         | 2026-08-25 |

Hier bedeutet:

```text
member_id = 2
```

Die Ausleihe gehört zu Lisa.

---

## Fremdschlüssel in SQL

Beispiel:

```sql
CREATE TABLE members (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL
);

CREATE TABLE loans (
  id INTEGER PRIMARY KEY,
  member_id INTEGER NOT NULL,
  loan_date DATE NOT NULL,
  FOREIGN KEY (member_id) REFERENCES members(id)
);
```

Bedeutung:

| Teil                      | Erklärung                                  |
| ------------------------- | ------------------------------------------ |
| `member_id INTEGER`       | Spalte für den Verweis                     |
| `FOREIGN KEY (member_id)` | diese Spalte ist ein Fremdschlüssel        |
| `REFERENCES members(id)`  | verweist auf `id` in der Tabelle `members` |

So weiß die Datenbank, dass eine Ausleihe nur zu einem vorhandenen Mitglied gehören darf.

---

## Warum Fremdschlüssel wichtig sind

Fremdschlüssel schützen die Datenintegrität.

Ohne Fremdschlüssel könnte man zum Beispiel eine Ausleihe für ein Mitglied speichern, das gar nicht existiert.

Problematisch:

| loan_id | member_id |
| ------- | --------- |
| 1       | 999       |

Wenn es kein Mitglied mit `id = 999` gibt, ist die Ausleihe ungültig.

Ein Fremdschlüssel verhindert solche Fehler.

---

## Beziehungen zwischen Tabellen

Beziehungen beschreiben, wie Datensätze aus verschiedenen Tabellen zusammenhängen.

Wichtige Beziehungstypen:

| Beziehung | Bedeutung                                                     |
| --------- | ------------------------------------------------------------- |
| 1:1       | ein Datensatz gehört zu genau einem anderen                   |
| 1:n       | ein Datensatz kann mehrere andere Datensätze haben            |
| n:m       | mehrere Datensätze können mit mehreren anderen verbunden sein |

Diese Beziehungen sind ein Kernpunkt relationaler Datenbanken.

---

## 1:1-Beziehung

Eine 1:1-Beziehung bedeutet:

```text
Ein Datensatz aus Tabelle A gehört zu genau einem Datensatz aus Tabelle B.
```

Beispiel:

```text
users
user_profiles
```

Ein Benutzer hat genau ein Profil.  
Ein Profil gehört genau zu einem Benutzer.

Beispiel:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  username TEXT NOT NULL
);

CREATE TABLE user_profiles (
  id INTEGER PRIMARY KEY,
  user_id INTEGER UNIQUE NOT NULL,
  bio TEXT,
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```

Das `UNIQUE` bei `user_id` sorgt dafür, dass ein Benutzer nicht mehrere Profile bekommt.

1:1-Beziehungen kommen vor, sind aber seltener als 1:n-Beziehungen.

---

## 1:n-Beziehung

Eine 1:n-Beziehung bedeutet:

```text
Ein Datensatz aus Tabelle A kann mehrere Datensätze aus Tabelle B haben.
```

Beispiel:

```text
Ein Mitglied kann mehrere Ausleihen haben.
Eine Ausleihe gehört aber zu genau einem Mitglied.
```

Tabelle `members`:

| id  | name |
| --- | ---- |
| 1   | Max  |
| 2   | Lisa |

Tabelle `loans`:

| id  | member_id | loan_date  |
| --- | --------- | ---------- |
| 1   | 1         | 2026-08-01 |
| 2   | 1         | 2026-08-10 |
| 3   | 2         | 2026-08-12 |

Hier hat Max zwei Ausleihen und Lisa eine Ausleihe.

Die Fremdschlüssel-Spalte steht meistens auf der n-Seite.

In diesem Beispiel:

```text
loans.member_id
```

---

## n:m-Beziehung

Eine n:m-Beziehung bedeutet:

```text
Mehrere Datensätze aus Tabelle A können mit mehreren Datensätzen aus Tabelle B verbunden sein.
```

Beispiel:

```text
Ein Buch kann mehrere Autoren haben.
Ein Autor kann mehrere Bücher schreiben.
```

Das kann man nicht sauber mit nur einem Fremdschlüssel lösen.

Dafür nutzt man eine Zwischentabelle.

Beispiel:

```text
books
authors
book_authors
```

---

## Zwischentabelle bei n:m

Beispiel:

```sql
CREATE TABLE books (
  id INTEGER PRIMARY KEY,
  title TEXT NOT NULL
);

CREATE TABLE authors (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL
);

CREATE TABLE book_authors (
  book_id INTEGER NOT NULL,
  author_id INTEGER NOT NULL,
  PRIMARY KEY (book_id, author_id),
  FOREIGN KEY (book_id) REFERENCES books(id),
  FOREIGN KEY (author_id) REFERENCES authors(id)
);
```

Die Tabelle `book_authors` verbindet Bücher und Autoren.

Beispiel Inhalt:

| book_id | author_id |
| ------- | --------- |
| 1       | 1         |
| 1       | 2         |
| 2       | 1         |

Das bedeutet:

```text
Buch 1 hat Autor 1 und Autor 2.
Buch 2 hat Autor 1.
```

---

## Zusammengesetzter Primärschlüssel

Ein zusammengesetzter Primärschlüssel besteht aus mehreren Spalten.

Beispiel:

```sql
PRIMARY KEY (book_id, author_id)
```

Das bedeutet:

Die Kombination aus `book_id` und `author_id` muss eindeutig sein.

Dadurch kann dieselbe Kombination nicht doppelt gespeichert werden.

Erlaubt:

| book_id | author_id |
| ------- | --------- |
| 1       | 1         |
| 1       | 2         |

Nicht sinnvoll doppelt:

| book_id | author_id |
| ------- | --------- |
| 1       | 1         |
| 1       | 1         |

Der zusammengesetzte Schlüssel verhindert solche doppelten Verknüpfungen.

---

## Join-Tabellen

Zwischentabellen werden auch Join-Tabellen genannt.

Typische Namen:

```text
book_authors
user_roles
order_products
student_courses
project_members
```

Eine Join-Tabelle enthält meistens:

- Fremdschlüssel auf Tabelle A
- Fremdschlüssel auf Tabelle B
- optional zusätzliche Informationen

Beispiel `order_products`:

```text
order_id
product_id
quantity
price_at_order_time
```

Hier speichert die Join-Tabelle nicht nur die Verbindung, sondern auch die Menge und den Preis zum Zeitpunkt der Bestellung.

---

## Beziehung lesen können

Man sollte Beziehungen in beide Richtungen lesen können.

Beispiel:

```text
members 1:n loans
```

Bedeutung:

```text
Ein Mitglied kann mehrere Ausleihen haben.
Eine Ausleihe gehört zu genau einem Mitglied.
```

Beispiel:

```text
books n:m authors
```

Bedeutung:

```text
Ein Buch kann mehrere Autoren haben.
Ein Autor kann mehrere Bücher haben.
```

Das ist wichtig beim Zeichnen von ERM-Diagrammen und beim Schreiben von Joins.

---

## ERM kurz erklärt

ERM bedeutet:

```text
Entity Relationship Model
```

Ein ERM beschreibt Tabellen und Beziehungen grafisch.

Typische Bestandteile:

| Begriff      | Bedeutung                           |
| ------------ | ----------------------------------- |
| Entity       | Objekt oder Tabelle                 |
| Attribut     | Eigenschaft oder Spalte             |
| Beziehung    | Verbindung zwischen Tabellen        |
| Kardinalität | Art der Beziehung, zum Beispiel 1:n |

Beispiel:

```text
Member 1:n Loan
Book 1:n Loan
Book n:m Author
```

Ein ERM hilft, die Datenbank vor dem Erstellen der Tabellen zu planen.

---

## Kardinalität

Kardinalität beschreibt, wie viele Datensätze miteinander verbunden sein können.

Beispiele:

| Kardinalität | Bedeutung                |
| ------------ | ------------------------ |
| 1:1          | genau eins zu genau eins |
| 1:n          | eins zu vielen           |
| n:m          | viele zu vielen          |

Beispiel Bibliothek:

| Beziehung            | Kardinalität |
| -------------------- | ------------ |
| Mitglied zu Ausleihe | 1:n          |
| Buch zu Exemplar     | 1:n          |
| Buch zu Autor        | n:m          |
| Ausleihe zu Mitglied | n:1          |

Wichtig:

Ob man von links nach rechts oder rechts nach links liest, ändert die Formulierung.

```text
Mitglied 1:n Ausleihe
Ausleihe n:1 Mitglied
```

Beides beschreibt dieselbe Beziehung aus unterschiedlicher Richtung.

---

## Tabellenbenennung

Tabellen sollten klare Namen haben.

Beispiele:

```text
users
members
books
authors
loans
orders
products
```

Wichtig ist, dass die Benennung im Projekt einheitlich bleibt.

Nicht gut gemischt:

```text
User
members
BookTable
tbl_loans
```

Besser einheitlich:

```text
users
members
books
loans
```

Für Lernprojekte ist eine einfache englische Benennung oft sinnvoll, weil viele SQL-Beispiele und Frameworks englische Namen nutzen.

---

## Spaltenbenennung

Spaltennamen sollten verständlich und eindeutig sein.

Gute Beispiele:

```text
id
name
email
created_at
member_id
book_id
loan_date
return_date
```

Weniger gut:

```text
n
mail1
xid
datum2
wert
```

Bei Fremdschlüsseln ist diese Form sehr üblich:

```text
tabelle_id
```

Beispiele:

```text
member_id
book_id
author_id
department_id
```

Dadurch erkennt man direkt, worauf die Spalte verweist.

---

## Constraints und Beziehungen

Constraints helfen, Beziehungen und Regeln abzusichern.

Wichtige Constraints:

| Constraint    | Bedeutung                         |
| ------------- | --------------------------------- |
| `PRIMARY KEY` | eindeutige Kennung                |
| `FOREIGN KEY` | Verweis auf andere Tabelle        |
| `NOT NULL`    | Wert darf nicht fehlen            |
| `UNIQUE`      | Wert darf nicht doppelt vorkommen |
| `CHECK`       | Wert muss eine Bedingung erfüllen |
| `DEFAULT`     | Standardwert                      |

Beispiel:

```sql
CREATE TABLE members (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT UNIQUE
);
```

Hier gilt:

```text
id ist eindeutig
name darf nicht fehlen
email darf nicht doppelt vorkommen
```

---

## NOT NULL

`NOT NULL` bedeutet, dass ein Wert eingetragen werden muss.

Beispiel:

```sql
name TEXT NOT NULL
```

Das ist sinnvoll bei Pflichtfeldern.

Beispiele:

```text
Name eines Mitglieds
Titel eines Buches
Datum einer Ausleihe
Fremdschlüssel bei Pflichtbeziehungen
```

Ohne `NOT NULL` könnte ein Datensatz unvollständig sein.

---

## UNIQUE

`UNIQUE` bedeutet, dass ein Wert nicht doppelt vorkommen darf.

Beispiel:

```sql
email TEXT UNIQUE
```

Das ist sinnvoll, wenn jede E-Mail-Adresse nur einmal vorkommen soll.

Beispiele:

```text
Benutzername
E-Mail-Adresse
Inventarnummer
ISBN
Seriennummer
```

Wichtig:

Nicht alles, was eindeutig aussieht, bleibt dauerhaft eindeutig. Deshalb ist eine technische ID als Primärschlüssel oft trotzdem sinnvoll.

---

## CHECK

`CHECK` prüft eine Bedingung.

Beispiel:

```sql
CREATE TABLE products (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  price DECIMAL CHECK (price >= 0)
);
```

Dadurch darf `price` nicht negativ sein.

Weitere Beispiele:

```sql
CHECK (age >= 0)
CHECK (stock >= 0)
CHECK (status IN ('open', 'closed', 'pending'))
```

`CHECK` hilft, falsche Daten direkt in der Datenbank zu verhindern.

---

## DEFAULT

`DEFAULT` setzt einen Standardwert.

Beispiel:

```sql
CREATE TABLE tickets (
  id INTEGER PRIMARY KEY,
  title TEXT NOT NULL,
  status TEXT DEFAULT 'open'
);
```

Wenn kein Status angegeben wird, setzt die Datenbank automatisch:

```text
open
```

Das ist praktisch für Felder, die meistens denselben Startwert haben.

---

## ON DELETE kurz erklärt

Bei Fremdschlüsseln stellt sich die Frage:

```text
Was passiert, wenn der verknüpfte Datensatz gelöscht wird?
```

Beispiel:

```text
Ein Mitglied hat Ausleihen.
Was passiert mit den Ausleihen, wenn das Mitglied gelöscht wird?
```

Mögliche Regeln:

| Regel      | Bedeutung                               |
| ---------- | --------------------------------------- |
| `RESTRICT` | Löschen wird verhindert                 |
| `CASCADE`  | abhängige Datensätze werden mitgelöscht |
| `SET NULL` | Fremdschlüssel wird auf NULL gesetzt    |

Beispiel:

```sql
FOREIGN KEY (member_id) REFERENCES members(id)
ON DELETE RESTRICT
```

Für Lernprojekte ist es wichtig zu verstehen:

```text
CASCADE kann praktisch sein, aber auch gefährlich.
```

Wenn man einen Datensatz löscht, können dadurch viele abhängige Daten verschwinden.

---

## Beispiel: einfache Bibliotheksstruktur

Eine einfache Bibliotheksdatenbank:

```sql
CREATE TABLE members (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT UNIQUE
);

CREATE TABLE books (
  id INTEGER PRIMARY KEY,
  title TEXT NOT NULL,
  isbn TEXT UNIQUE
);

CREATE TABLE loans (
  id INTEGER PRIMARY KEY,
  member_id INTEGER NOT NULL,
  book_id INTEGER NOT NULL,
  loan_date DATE NOT NULL,
  return_date DATE,
  FOREIGN KEY (member_id) REFERENCES members(id),
  FOREIGN KEY (book_id) REFERENCES books(id)
);
```

Beziehungen:

```text
members 1:n loans
books 1:n loans
```

Ein Mitglied kann mehrere Ausleihen haben.  
Ein Buch kann mehrfach ausgeliehen werden, wenn man Ausleihen historisch speichert.

---

## Beispiel: Bücher und Autoren

Ein Buch kann mehrere Autoren haben. Ein Autor kann mehrere Bücher schreiben.

Dafür braucht man eine n:m-Beziehung.

```sql
CREATE TABLE authors (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL
);

CREATE TABLE book_authors (
  book_id INTEGER NOT NULL,
  author_id INTEGER NOT NULL,
  PRIMARY KEY (book_id, author_id),
  FOREIGN KEY (book_id) REFERENCES books(id),
  FOREIGN KEY (author_id) REFERENCES authors(id)
);
```

Die Tabelle `book_authors` ist die Verbindungstabelle.

---

## Daten doppelt speichern vermeiden

Ein wichtiges Ziel ist, doppelte Daten zu vermeiden.

Schlechtes Beispiel:

| loan_id | member_name | member_email    | book_title |
| ------- | ----------- | --------------- | ---------- |
| 1       | Max         | max@example.com | Linux      |
| 2       | Max         | max@example.com | SQL        |

Hier werden Name und E-Mail mehrfach gespeichert.

Besser:

```text
members
books
loans
```

Dann steht Max nur einmal in `members`. Die Ausleihen verweisen über `member_id` auf Max.

Vorteile:

- weniger Speicherverbrauch
- weniger Tippfehler
- einfachere Änderungen
- bessere Datenqualität
- klare Beziehungen

---

## Normalisierung und Beziehungen

Normalisierung bedeutet, Daten sauber auf mehrere Tabellen aufzuteilen.

Ziel:

```text
Daten sollen möglichst nicht unnötig doppelt gespeichert werden.
```

Beispiel:

Statt alles in eine große Tabelle zu schreiben, trennt man:

```text
members
books
authors
loans
categories
```

Dann verbindet man die Tabellen mit Schlüsseln.

Normalisierung ist am Anfang manchmal schwer, aber sie macht Datenbanken langfristig sauberer.

---

## Wann eine neue Tabelle sinnvoll ist

Eine neue Tabelle ist oft sinnvoll, wenn:

- dieselben Informationen mehrfach vorkommen
- ein Objekt eigene Eigenschaften hat
- Daten unabhängig verwaltet werden sollen
- mehrere Datensätze miteinander verbunden werden
- eine n:m-Beziehung entsteht
- Werte später erweitert werden sollen

Beispiel:

Statt Kategorie als Text in jedem Buch zu speichern:

```text
category = "IT"
category = "IT"
category = "IT"
```

kann man eine eigene Tabelle nutzen:

```text
categories
book_categories
```

Das ist besonders sinnvoll, wenn Bücher mehrere Kategorien haben können.

---

## Typische Modellierungsfehler

| Fehler                                  | Problem                                     |
| --------------------------------------- | ------------------------------------------- |
| alles in eine Tabelle schreiben         | viele doppelte Daten                        |
| Primärschlüssel vergessen               | Datensätze nicht eindeutig                  |
| Namen als Schlüssel nutzen              | Namen können doppelt vorkommen              |
| n:m ohne Zwischentabelle modellieren    | Datenstruktur wird unsauber                 |
| Fremdschlüssel nicht setzen             | Beziehungen bleiben nur theoretisch         |
| `NULL` überall erlauben                 | viele unvollständige Daten                  |
| zu viele Daten in eine Spalte schreiben | schwer filterbar                            |
| uneinheitliche Namen nutzen             | Struktur wird schwer lesbar                 |
| `CASCADE` unüberlegt nutzen             | Daten können unbeabsichtigt gelöscht werden |
| Tabellen ohne Zweck erstellen           | Modell wird unnötig kompliziert             |

---

## Praktisches Lesen einer Datenbankstruktur

Wenn man eine fremde Datenbankstruktur sieht, sollte man zuerst diese Fragen stellen:

```text
Welche Tabellen gibt es?
Was ist die Aufgabe jeder Tabelle?
Welche Primärschlüssel gibt es?
Welche Fremdschlüssel gibt es?
Welche Tabellen sind miteinander verbunden?
Gibt es 1:n- oder n:m-Beziehungen?
Wo sind Join-Tabellen?
Welche Constraints sichern die Daten?
Welche Spalten dürfen NULL sein?
```

Ein guter erster Befehl ist oft:

```sql
SELECT *
FROM table_name
LIMIT 10;
```

So bekommt man einen ersten Eindruck von den Daten.

---

## Verbindung zu Joins

Beziehungen werden besonders wichtig bei Joins.

Beispiel:

```sql
SELECT members.name, loans.loan_date
FROM members
JOIN loans
  ON members.id = loans.member_id;
```

Hier nutzt der Join die Beziehung:

```text
members.id = loans.member_id
```

Ohne saubere Schlüssel und Beziehungen werden Joins schnell falsch oder unübersichtlich.

Deshalb ist Datenmodellierung eine wichtige Grundlage für SQL-Abfragen.

---

## FISI-Bezug

Für FISI ist das Verständnis von Tabellen, Schlüsseln und Beziehungen sehr wichtig.

In der Praxis hilft es bei:

- Datenbankprojekte verstehen
- Adminer oder andere Datenbanktools nutzen
- Tabellenstrukturen lesen
- einfache SQL-Abfragen schreiben
- Joins nachvollziehen
- Datenbankfehler analysieren
- Docker-Datenbankprojekte betreiben
- mit Entwicklern über Datenstrukturen sprechen
- technische Dokumentationen verstehen
- Datenintegrität einschätzen

Ein FISI muss nicht jede Datenbank perfekt modellieren können, aber die Grundlogik von Tabellen, Primärschlüsseln, Fremdschlüsseln und Beziehungen sollte klar sein.

---

## Kurze Zusammenfassung

Tabellen speichern Daten in Zeilen und Spalten.

Primärschlüssel identifizieren Datensätze eindeutig. Fremdschlüssel verbinden Tabellen miteinander.

Die wichtigsten Beziehungstypen sind 1:1, 1:n und n:m. Bei n:m-Beziehungen wird eine Zwischentabelle genutzt.

Constraints wie `PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL`, `UNIQUE`, `CHECK` und `DEFAULT` helfen, Daten korrekt und zuverlässig zu speichern.

Für FISI ist dieses Wissen wichtig, weil viele Anwendungen, Datenbankprojekte und IT-Systeme auf relationalen Datenbanken basieren.
