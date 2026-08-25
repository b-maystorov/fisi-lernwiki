# 4. SELECT, Filter und Sortierung

In diesem Kapitel geht es um `SELECT`, Filter und Sortierung in SQL.

`SELECT` ist einer der wichtigsten SQL-Befehle, weil damit Daten aus Tabellen gelesen werden. In der Praxis möchte man aber selten einfach alle Daten sehen. Meistens filtert, sortiert oder begrenzt man Ergebnisse, damit man genau die Informationen bekommt, die man braucht.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil man mit `SELECT` Daten kontrollieren, Fehler prüfen, Testdaten ansehen und Datenbankinhalte nachvollziehen kann.

---

## Kurz erklärt

Mit `SELECT` fragt man Daten aus Tabellen ab.

Einfaches Beispiel:

```sql
SELECT *
FROM users;
```

Das zeigt alle Spalten und alle Datensätze aus der Tabelle `users`.

Häufig kombiniert man `SELECT` mit:

| SQL-Teil   | Bedeutung                             |
| ---------- | ------------------------------------- |
| `FROM`     | aus welcher Tabelle gelesen wird      |
| `WHERE`    | welche Zeilen gefiltert werden        |
| `ORDER BY` | wie das Ergebnis sortiert wird        |
| `LIMIT`    | wie viele Datensätze angezeigt werden |
| `DISTINCT` | doppelte Werte entfernen              |
| `LIKE`     | Textmuster suchen                     |
| `IN`       | mehrere mögliche Werte prüfen         |
| `BETWEEN`  | Wertebereich prüfen                   |
| `IS NULL`  | fehlende Werte prüfen                 |

---

## Grundaufbau von SELECT

Ein typischer `SELECT`-Befehl sieht so aus:

```sql
SELECT spalte1, spalte2
FROM tabelle
WHERE bedingung
ORDER BY spalte
LIMIT anzahl;
```

Beispiel:

```sql
SELECT name, email
FROM users
WHERE city = 'Hamburg'
ORDER BY name
LIMIT 10;
```

Bedeutung:

| Teil                     | Erklärung                      |
| ------------------------ | ------------------------------ |
| `SELECT name, email`     | zeige nur diese Spalten        |
| `FROM users`             | aus der Tabelle `users`        |
| `WHERE city = 'Hamburg'` | nur Benutzer aus Hamburg       |
| `ORDER BY name`          | nach Name sortieren            |
| `LIMIT 10`               | maximal 10 Ergebnisse anzeigen |

---

## SELECT \*

`SELECT *` zeigt alle Spalten einer Tabelle.

```sql
SELECT *
FROM users;
```

Das ist praktisch, wenn man schnell sehen möchte, wie eine Tabelle aussieht.

Bei großen Tabellen ist `SELECT *` aber oft nicht ideal.

Nachteile:

- Ergebnis kann unübersichtlich werden
- unnötige Daten werden geladen
- sensible Spalten können sichtbar werden
- Performance kann schlechter sein
- Abfrage ist weniger sauber dokumentiert

Besser ist oft:

```sql
SELECT id, name, email
FROM users;
```

So sieht man nur die Spalten, die wirklich gebraucht werden.

---

## Bestimmte Spalten auswählen

Man kann gezielt Spalten auswählen.

```sql
SELECT name, email
FROM users;
```

Beispiel mit Produkten:

```sql
SELECT name, price
FROM products;
```

Beispiel mit Tickets:

```sql
SELECT id, title, status
FROM tickets;
```

Das macht Abfragen übersichtlicher und hilft, sich auf die wichtigen Informationen zu konzentrieren.

---

## FROM

`FROM` gibt an, aus welcher Tabelle die Daten gelesen werden.

```sql
SELECT name
FROM users;
```

Hier kommen die Daten aus der Tabelle:

```text
users
```

Jede normale `SELECT`-Abfrage braucht eine Datenquelle.

Bei einfachen Abfragen ist das eine Tabelle.  
Bei komplexeren Abfragen können mehrere Tabellen über `JOIN` verbunden werden.

---

## WHERE

`WHERE` filtert Zeilen.

Beispiel:

```sql
SELECT *
FROM users
WHERE city = 'Hamburg';
```

Nur Zeilen, bei denen `city = 'Hamburg'` gilt, werden angezeigt.

Weitere Beispiele:

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

```sql
SELECT *
FROM books
WHERE title = 'Linux Grundlagen';
```

`WHERE` ist einer der wichtigsten Teile von SQL, weil man damit gezielt Daten auswählt.

---

## Vergleichsoperatoren

In `WHERE`-Bedingungen werden Vergleichsoperatoren genutzt.

| Operator | Bedeutung                       |
| -------- | ------------------------------- |
| `=`      | ist gleich                      |
| `<>`     | ist ungleich                    |
| `!=`     | ist ungleich, je nach Datenbank |
| `>`      | größer als                      |
| `<`      | kleiner als                     |
| `>=`     | größer oder gleich              |
| `<=`     | kleiner oder gleich             |

Beispiele:

```sql
SELECT *
FROM products
WHERE price >= 50;
```

```sql
SELECT *
FROM users
WHERE age < 18;
```

```sql
SELECT *
FROM tickets
WHERE status <> 'closed';
```

---

## Textwerte in SQL

Textwerte werden in SQL meistens mit einfachen Anführungszeichen geschrieben.

Richtig:

```sql
SELECT *
FROM users
WHERE city = 'Hamburg';
```

Falsch:

```sql
SELECT *
FROM users
WHERE city = Hamburg;
```

Ohne Anführungszeichen denkt die Datenbank, dass `Hamburg` ein Spaltenname oder Objektname ist.

Bei Texten also:

```text
'Text'
```

---

## Zahlen in SQL

Zahlen brauchen keine Anführungszeichen.

```sql
SELECT *
FROM products
WHERE price > 100;
```

Auch IDs werden meistens ohne Anführungszeichen genutzt:

```sql
SELECT *
FROM users
WHERE id = 5;
```

Wichtig ist, dass der Datentyp passt.

Eine Zahlenspalte sollte mit Zahlen verglichen werden.  
Eine Textspalte sollte mit Text verglichen werden.

---

## AND

Mit `AND` müssen mehrere Bedingungen gleichzeitig wahr sein.

```sql
SELECT *
FROM users
WHERE city = 'Hamburg'
  AND active = true;
```

Das bedeutet:

```text
Nur Benutzer aus Hamburg, die aktiv sind.
```

Weiteres Beispiel:

```sql
SELECT *
FROM products
WHERE price >= 10
  AND price <= 50;
```

Beide Bedingungen müssen stimmen.

---

## OR

Mit `OR` reicht es, wenn eine Bedingung wahr ist.

```sql
SELECT *
FROM tickets
WHERE status = 'open'
   OR status = 'pending';
```

Das bedeutet:

```text
Zeige Tickets, die offen oder ausstehend sind.
```

Weiteres Beispiel:

```sql
SELECT *
FROM users
WHERE city = 'Hamburg'
   OR city = 'Berlin';
```

---

## AND und OR kombinieren

Wenn `AND` und `OR` zusammen genutzt werden, sollte man Klammern verwenden.

Beispiel:

```sql
SELECT *
FROM tickets
WHERE status = 'open'
  AND (priority = 'high' OR priority = 'critical');
```

Ohne Klammern können Ergebnisse anders sein als erwartet.

Klammern machen die Logik klarer.

Gute Regel:

```text
Wenn AND und OR zusammen vorkommen, lieber Klammern setzen.
```

---

## NOT

`NOT` dreht eine Bedingung um.

```sql
SELECT *
FROM users
WHERE NOT city = 'Hamburg';
```

Das bedeutet:

```text
Zeige Benutzer, die nicht aus Hamburg sind.
```

Häufiger schreibt man aber:

```sql
SELECT *
FROM users
WHERE city <> 'Hamburg';
```

Beide Varianten können funktionieren.

---

## IN

`IN` prüft, ob ein Wert in einer Liste enthalten ist.

```sql
SELECT *
FROM users
WHERE city IN ('Hamburg', 'Berlin', 'Kiel');
```

Das ist kürzer und sauberer als:

```sql
SELECT *
FROM users
WHERE city = 'Hamburg'
   OR city = 'Berlin'
   OR city = 'Kiel';
```

`IN` ist besonders praktisch, wenn mehrere Werte erlaubt sind.

---

## NOT IN

`NOT IN` prüft, ob ein Wert nicht in einer Liste enthalten ist.

```sql
SELECT *
FROM users
WHERE city NOT IN ('Hamburg', 'Berlin');
```

Das bedeutet:

```text
Zeige Benutzer, die nicht aus Hamburg oder Berlin sind.
```

Wichtig:

Bei `NULL`-Werten kann `NOT IN` je nach Situation unerwartete Ergebnisse liefern. Deshalb sollte man bei fehlenden Werten sauber mit `IS NULL` oder `IS NOT NULL` arbeiten.

---

## BETWEEN

`BETWEEN` prüft, ob ein Wert in einem Bereich liegt.

```sql
SELECT *
FROM products
WHERE price BETWEEN 10 AND 50;
```

Das bedeutet:

```text
Preis zwischen 10 und 50.
```

Auch bei Datum:

```sql
SELECT *
FROM loans
WHERE loan_date BETWEEN '2026-08-01' AND '2026-08-31';
```

`BETWEEN` schließt die Grenzwerte meistens mit ein.

Das bedeutet:

```text
10 und 50 zählen mit.
```

---

## LIKE

`LIKE` wird für einfache Textsuche genutzt.

```sql
SELECT *
FROM users
WHERE name LIKE 'Ma%';
```

Bedeutung:

```text
Name beginnt mit Ma.
```

Häufige Muster:

| Muster      | Bedeutung                               |
| ----------- | --------------------------------------- |
| `'Ma%'`     | beginnt mit Ma                          |
| `'%son'`    | endet mit son                           |
| `'%admin%'` | enthält admin                           |
| `'M_x'`     | ein beliebiges Zeichen zwischen M und x |

Beispiel:

```sql
SELECT *
FROM books
WHERE title LIKE '%Linux%';
```

Das findet Titel, die `Linux` enthalten.

---

## Groß- und Kleinschreibung bei LIKE

Je nach Datenbank wird Groß- und Kleinschreibung unterschiedlich behandelt.

Beispiel:

```sql
SELECT *
FROM books
WHERE title LIKE '%linux%';
```

Manche Datenbanken finden damit auch `Linux`, andere nicht.

Bei PostgreSQL gibt es zusätzlich:

```sql
ILIKE
```

Beispiel:

```sql
SELECT *
FROM books
WHERE title ILIKE '%linux%';
```

`ILIKE` sucht in PostgreSQL ohne Beachtung der Groß- und Kleinschreibung.

---

## NULL filtern

`NULL` bedeutet:

```text
kein Wert vorhanden
```

Man darf `NULL` nicht mit `=` vergleichen.

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

Nicht leer:

```sql
SELECT *
FROM users
WHERE phone IS NOT NULL;
```

Wichtig:

`NULL` ist nicht dasselbe wie `0`, `false` oder leerer Text.

---

## DISTINCT

`DISTINCT` entfernt doppelte Werte aus dem Ergebnis.

Beispiel:

```sql
SELECT DISTINCT city
FROM users;
```

Wenn mehrere Benutzer aus Hamburg kommen, wird `Hamburg` nur einmal angezeigt.

Ohne `DISTINCT`:

| city    |
| ------- |
| Hamburg |
| Hamburg |
| Berlin  |

Mit `DISTINCT`:

| city    |
| ------- |
| Hamburg |
| Berlin  |

`DISTINCT` ist nützlich, wenn man wissen möchte, welche Werte überhaupt vorkommen.

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

## Nach mehreren Spalten sortieren

Man kann nach mehreren Spalten sortieren.

```sql
SELECT *
FROM users
ORDER BY city ASC, name ASC;
```

Das bedeutet:

```text
Erst nach Stadt sortieren.
Innerhalb derselben Stadt nach Name sortieren.
```

Weiteres Beispiel:

```sql
SELECT *
FROM tickets
ORDER BY priority DESC, created_at ASC;
```

Mehrere Sortierungen helfen, Ergebnisse besser zu strukturieren.

---

## LIMIT

`LIMIT` begrenzt die Anzahl der Ergebnisse.

```sql
SELECT *
FROM users
LIMIT 10;
```

Das zeigt maximal 10 Datensätze.

Sehr praktisch bei großen Tabellen:

```sql
SELECT *
FROM logs
LIMIT 20;
```

Ohne `LIMIT` kann eine große Tabelle sehr viele Ergebnisse liefern.

Für erste Prüfungen ist `LIMIT` deshalb sehr sinnvoll.

---

## LIMIT mit ORDER BY

`LIMIT` ist besonders sinnvoll zusammen mit `ORDER BY`.

Beispiel:

```sql
SELECT *
FROM tickets
ORDER BY created_at DESC
LIMIT 5;
```

Das zeigt die 5 neuesten Tickets.

Ohne `ORDER BY` ist nicht garantiert, welche 5 Datensätze angezeigt werden.

Gute Regel:

```text
LIMIT ohne ORDER BY ist oft nur für schnelle Tests sinnvoll.
```

---

## OFFSET

`OFFSET` überspringt eine bestimmte Anzahl von Datensätzen.

```sql
SELECT *
FROM users
ORDER BY id
LIMIT 10 OFFSET 20;
```

Das bedeutet:

```text
Überspringe die ersten 20 Datensätze und zeige dann 10.
```

Das wird oft für Seitenanzeige verwendet.

Beispiel:

```text
Seite 1: LIMIT 10 OFFSET 0
Seite 2: LIMIT 10 OFFSET 10
Seite 3: LIMIT 10 OFFSET 20
```

---

## Aliase für Spalten

Mit `AS` kann man Spalten im Ergebnis umbenennen.

```sql
SELECT name AS username
FROM users;
```

Das Ergebnis zeigt dann die Spalte als `username`.

Beispiel:

```sql
SELECT price AS product_price
FROM products;
```

Aliase ändern nicht die echte Tabellenstruktur. Sie ändern nur die Anzeige im Ergebnis.

---

## Aliase für Tabellen

Tabellen können ebenfalls Aliase bekommen.

```sql
SELECT u.name, u.email
FROM users AS u;
```

Hier steht `u` kurz für `users`.

Bei einfachen Abfragen ist das nicht unbedingt nötig.

Bei Joins ist es aber sehr praktisch:

```sql
SELECT u.name, o.id
FROM users AS u
JOIN orders AS o
  ON u.id = o.user_id;
```

---

## Rechnen in SELECT

In `SELECT` kann man auch einfache Berechnungen machen.

```sql
SELECT name, price, price * 1.19 AS price_with_tax
FROM products;
```

Das kann nützlich sein für:

- Preise
- Summen
- Rabatte
- Mengen
- berechnete Anzeigen

Die berechnete Spalte wird nicht automatisch gespeichert. Sie erscheint nur im Ergebnis der Abfrage.

---

## COUNT

`COUNT()` zählt Datensätze.

```sql
SELECT COUNT(*)
FROM users;
```

Das zählt alle Zeilen.

Mit Filter:

```sql
SELECT COUNT(*)
FROM users
WHERE city = 'Hamburg';
```

Das zählt nur Benutzer aus Hamburg.

`COUNT()` ist eine Aggregatfunktion und wird oft für einfache Auswertungen genutzt.

---

## MIN und MAX

`MIN()` gibt den kleinsten Wert zurück.

```sql
SELECT MIN(price)
FROM products;
```

`MAX()` gibt den größten Wert zurück.

```sql
SELECT MAX(price)
FROM products;
```

Beispiele:

```sql
SELECT MAX(created_at)
FROM tickets;
```

```sql
SELECT MIN(age)
FROM users;
```

---

## AVG und SUM

`AVG()` berechnet den Durchschnitt.

```sql
SELECT AVG(price)
FROM products;
```

`SUM()` berechnet die Summe.

```sql
SELECT SUM(price)
FROM orders;
```

Diese Funktionen sind besonders nützlich für Auswertungen.

Beispiele:

```text
durchschnittlicher Preis
Summe aller Bestellungen
Anzahl aller Tickets
ältester oder neuester Eintrag
```

---

## GROUP BY kurz

`GROUP BY` gruppiert Ergebnisse.

Beispiel:

```sql
SELECT city, COUNT(*)
FROM users
GROUP BY city;
```

Das Ergebnis zeigt, wie viele Benutzer pro Stadt vorhanden sind.

Beispiel:

| city    | count |
| ------- | ----- |
| Hamburg | 12    |
| Berlin  | 8     |
| Kiel    | 3     |

`GROUP BY` wird später oft zusammen mit Aggregatfunktionen genutzt.

---

## HAVING kurz

`HAVING` filtert gruppierte Ergebnisse.

Beispiel:

```sql
SELECT city, COUNT(*)
FROM users
GROUP BY city
HAVING COUNT(*) > 5;
```

Das bedeutet:

```text
Zeige nur Städte mit mehr als 5 Benutzern.
```

Unterschied:

| Befehl   | Filtert                             |
| -------- | ----------------------------------- |
| `WHERE`  | einzelne Zeilen vor der Gruppierung |
| `HAVING` | Gruppen nach der Gruppierung        |

---

## Reihenfolge der SQL-Bestandteile

Eine typische Schreibreihenfolge:

```sql
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

Beispiel:

```sql
SELECT city, COUNT(*)
FROM users
WHERE active = true
GROUP BY city
HAVING COUNT(*) > 2
ORDER BY city
LIMIT 10;
```

Nicht jede Abfrage braucht alle Teile.

Aber die Reihenfolge ist wichtig.

---

## Beispiel: Benutzer anzeigen

```sql
SELECT id, name, email
FROM users
ORDER BY name;
```

Diese Abfrage zeigt Benutzer mit ID, Name und E-Mail und sortiert sie nach Namen.

---

## Beispiel: Produkte filtern

```sql
SELECT id, name, price
FROM products
WHERE price BETWEEN 10 AND 50
ORDER BY price DESC;
```

Diese Abfrage zeigt Produkte zwischen 10 und 50 Euro und sortiert sie vom teuersten zum günstigsten.

---

## Beispiel: Tickets prüfen

```sql
SELECT id, title, status, created_at
FROM tickets
WHERE status IN ('open', 'pending')
ORDER BY created_at DESC
LIMIT 20;
```

Diese Abfrage zeigt die letzten 20 offenen oder ausstehenden Tickets.

---

## Beispiel: Fehlende Telefonnummern finden

```sql
SELECT id, name, email
FROM users
WHERE phone IS NULL
ORDER BY name;
```

Diese Abfrage findet Benutzer, bei denen keine Telefonnummer eingetragen wurde.

---

## Typische Fehler

| Fehler                                   | Problem                                    |
| ---------------------------------------- | ------------------------------------------ |
| `SELECT *` immer nutzen                  | Ergebnis wird schnell unübersichtlich      |
| `WHERE` vergessen                        | zu viele Datensätze werden angezeigt       |
| Text ohne Anführungszeichen              | Syntaxfehler                               |
| `NULL` mit `=` vergleichen               | Ergebnis ist falsch                        |
| `AND` und `OR` ohne Klammern mischen     | Logik wird unklar                          |
| `LIMIT` ohne `ORDER BY` falsch verstehen | Ergebnisreihenfolge ist nicht garantiert   |
| falsche Spaltennamen nutzen              | SQL-Fehler                                 |
| `LIKE` als exakte Suche erwarten         | Mustervergleich, keine normale Gleichheit  |
| `DISTINCT` falsch einsetzen              | kann Daten scheinbar „verschwinden“ lassen |
| große Tabellen ohne Filter abfragen      | unübersichtlich oder langsam               |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei `SELECT`-Abfragen:

1. zuerst Tabelle und Spalten prüfen
2. mit `LIMIT` kleine Ergebnisse anzeigen
3. gezielt Spalten statt `*` auswählen
4. Filter mit `WHERE` Schritt für Schritt aufbauen
5. bei `AND` und `OR` Klammern nutzen
6. Sortierung mit `ORDER BY` bewusst setzen
7. bei `NULL` immer `IS NULL` oder `IS NOT NULL` nutzen
8. Abfragen lesbar über mehrere Zeilen schreiben
9. Ergebnisse prüfen, bevor man sie weiterverwendet
10. große Datenmengen nicht unnötig laden

Guter Start:

```sql
SELECT *
FROM table_name
LIMIT 10;
```

Danach sauberer machen:

```sql
SELECT id, name, email
FROM table_name
WHERE condition
ORDER BY id
LIMIT 10;
```

---

## FISI-Bezug

Für FISI ist `SELECT` sehr wichtig, weil man damit Daten lesen und prüfen kann.

In der Praxis hilft das bei:

- Datenbankinhalte kontrollieren
- Testdaten prüfen
- Fehler in Anwendungen nachvollziehen
- Ticketsystemdaten verstehen
- Monitoring- oder Logdaten auswerten
- Benutzer- oder Gerätedaten suchen
- Docker-Datenbankprojekte testen
- Adminer oder psql sinnvoll nutzen
- mit Entwicklern über Daten sprechen

Ein FISI muss nicht jede komplexe SQL-Abfrage perfekt schreiben können, aber einfache `SELECT`-Abfragen mit `WHERE`, `ORDER BY`, `LIMIT`, `LIKE`, `IN` und `IS NULL` sollten sicher verstanden werden.

---

## Kurze Zusammenfassung

`SELECT` wird genutzt, um Daten aus Tabellen zu lesen.

Mit `WHERE` filtert man Zeilen. Mit `ORDER BY` sortiert man Ergebnisse. Mit `LIMIT` begrenzt man die Anzahl der angezeigten Datensätze.

Wichtige Ergänzungen sind `DISTINCT`, `LIKE`, `IN`, `BETWEEN`, `IS NULL`, `AND`, `OR`, `NOT` und Aliase.

Für FISI ist dieses Wissen wichtig, weil man damit Datenbankinhalte prüfen, Fehler analysieren und einfache Auswertungen durchführen kann.
