# 5. Joins und Beziehungen

In diesem Kapitel geht es um Joins und Beziehungen in SQL.

Relationale Datenbanken bestehen meistens aus mehreren Tabellen. Daten werden bewusst aufgeteilt, damit sie nicht doppelt gespeichert werden. Damit man zusammengehörende Informationen wieder gemeinsam anzeigen kann, nutzt man Joins.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Datenbankabfragen nicht nur eine Tabelle betreffen. In Anwendungen, Ticketsystemen, Inventarsystemen oder Datenbankprojekten müssen Daten oft aus mehreren Tabellen zusammengeführt werden.

---

## Kurz erklärt

Ein Join verbindet Daten aus mehreren Tabellen.

Beispiel:

```text
members
loans
books
```

Eine Tabelle `loans` speichert vielleicht nur IDs:

```text
member_id
book_id
loan_date
```

Damit man den Namen des Mitglieds und den Titel des Buches sieht, muss man die Tabellen verbinden.

Beispiel:

```sql
SELECT members.name, books.title, loans.loan_date
FROM loans
JOIN members
  ON loans.member_id = members.id
JOIN books
  ON loans.book_id = books.id;
```

Wichtig ist immer die Verbindung über passende Schlüssel:

```text
Primary Key -> Foreign Key
```

---

## Warum Joins gebraucht werden

Daten werden in relationalen Datenbanken oft auf mehrere Tabellen verteilt.

Das verhindert doppelte Daten.

Schlechtes Beispiel in einer großen Tabelle:

| loan_id | member_name | member_email    | book_title       | loan_date  |
| ------- | ----------- | --------------- | ---------------- | ---------- |
| 1       | Max         | max@example.com | Linux Grundlagen | 2026-08-01 |
| 2       | Max         | max@example.com | SQL Einstieg     | 2026-08-10 |

Hier werden Name und E-Mail mehrfach gespeichert.

Besser:

```text
members
books
loans
```

Die Tabelle `loans` speichert nur die Verweise.

Joins holen die Informationen später wieder zusammen.

---

## Beispieltabellen

Für die Beispiele nutzen wir drei Tabellen.

### members

| id  | name | email            |
| --- | ---- | ---------------- |
| 1   | Max  | max@example.com  |
| 2   | Lisa | lisa@example.com |
| 3   | Sara | sara@example.com |

### books

| id  | title            |
| --- | ---------------- |
| 1   | Linux Grundlagen |
| 2   | SQL Einstieg     |
| 3   | Docker Praxis    |

### loans

| id  | member_id | book_id | loan_date  |
| --- | --------- | ------- | ---------- |
| 1   | 1         | 2       | 2026-08-01 |
| 2   | 2         | 1       | 2026-08-03 |
| 3   | 1         | 3       | 2026-08-10 |

Die Tabelle `loans` verbindet Mitglieder mit Büchern.

---

## Beziehung erkennen

Die Beziehungen sind:

```text
members.id -> loans.member_id
books.id -> loans.book_id
```

Das bedeutet:

```text
Ein Mitglied kann mehrere Ausleihen haben.
Ein Buch kann in mehreren Ausleih-Datensätzen vorkommen.
Eine Ausleihe gehört zu genau einem Mitglied und einem Buch.
```

In SQL verbindet man diese Beziehungen mit `JOIN ... ON`.

---

## INNER JOIN

Ein `INNER JOIN` zeigt nur Datensätze, bei denen auf beiden Seiten eine passende Verbindung existiert.

Beispiel:

```sql
SELECT members.name, loans.loan_date
FROM members
INNER JOIN loans
  ON members.id = loans.member_id;
```

Das Ergebnis zeigt nur Mitglieder, die eine Ausleihe haben.

Wenn ein Mitglied keine Ausleihe hat, erscheint es nicht im Ergebnis.

---

## JOIN ist meistens INNER JOIN

In vielen Datenbanken bedeutet `JOIN` ohne Zusatz dasselbe wie `INNER JOIN`.

Diese beiden Abfragen sind meistens gleich:

```sql
SELECT members.name, loans.loan_date
FROM members
JOIN loans
  ON members.id = loans.member_id;
```

und:

```sql
SELECT members.name, loans.loan_date
FROM members
INNER JOIN loans
  ON members.id = loans.member_id;
```

Für Anfänger ist es oft gut, `INNER JOIN` bewusst auszuschreiben, damit klar ist, welcher Join-Typ gemeint ist.

---

## INNER JOIN Beispiel

```sql
SELECT members.name, books.title, loans.loan_date
FROM loans
INNER JOIN members
  ON loans.member_id = members.id
INNER JOIN books
  ON loans.book_id = books.id;
```

Das Ergebnis könnte so aussehen:

| name | title            | loan_date  |
| ---- | ---------------- | ---------- |
| Max  | SQL Einstieg     | 2026-08-01 |
| Lisa | Linux Grundlagen | 2026-08-03 |
| Max  | Docker Praxis    | 2026-08-10 |

Die IDs werden genutzt, um die richtigen Namen und Titel anzuzeigen.

---

## LEFT JOIN

Ein `LEFT JOIN` zeigt alle Datensätze aus der linken Tabelle.

Wenn es rechts keine passende Verbindung gibt, werden rechts `NULL`-Werte angezeigt.

Beispiel:

```sql
SELECT members.name, loans.loan_date
FROM members
LEFT JOIN loans
  ON members.id = loans.member_id;
```

Das bedeutet:

```text
Zeige alle Mitglieder.
Wenn sie Ausleihen haben, zeige die Ausleihen dazu.
Wenn nicht, zeige trotzdem das Mitglied.
```

---

## LEFT JOIN Beispiel

Tabelle `members`:

| id  | name |
| --- | ---- |
| 1   | Max  |
| 2   | Lisa |
| 3   | Sara |

Tabelle `loans`:

| id  | member_id | loan_date  |
| --- | --------- | ---------- |
| 1   | 1         | 2026-08-01 |
| 2   | 2         | 2026-08-03 |

Abfrage:

```sql
SELECT members.name, loans.loan_date
FROM members
LEFT JOIN loans
  ON members.id = loans.member_id;
```

Ergebnis:

| name | loan_date  |
| ---- | ---------- |
| Max  | 2026-08-01 |
| Lisa | 2026-08-03 |
| Sara | NULL       |

Sara erscheint, obwohl sie keine Ausleihe hat.

---

## Welche Tabelle ist links?

Die linke Tabelle ist die Tabelle direkt nach `FROM`.

Beispiel:

```sql
SELECT members.name, loans.loan_date
FROM members
LEFT JOIN loans
  ON members.id = loans.member_id;
```

Hier ist `members` links.

```text
FROM members = linke Tabelle
LEFT JOIN loans = rechte Tabelle
```

Deshalb zeigt der `LEFT JOIN` alle Datensätze aus `members`.

---

## LEFT JOIN andersherum

Wenn man die Reihenfolge ändert, ändert sich die Bedeutung.

```sql
SELECT members.name, loans.loan_date
FROM loans
LEFT JOIN members
  ON loans.member_id = members.id;
```

Jetzt ist `loans` die linke Tabelle.

Das bedeutet:

```text
Zeige alle Ausleihen.
Wenn ein Mitglied dazu existiert, zeige den Namen.
```

Die linke Tabelle ist immer entscheidend.

---

## RIGHT JOIN

Ein `RIGHT JOIN` zeigt alle Datensätze aus der rechten Tabelle.

Beispiel:

```sql
SELECT members.name, loans.loan_date
FROM loans
RIGHT JOIN members
  ON loans.member_id = members.id;
```

Das zeigt alle Mitglieder, auch wenn sie keine Ausleihe haben.

Viele Entwickler nutzen lieber `LEFT JOIN`, weil man die Tabellen einfach andersherum schreiben kann.

Diese Abfrage ist oft leichter lesbar:

```sql
SELECT members.name, loans.loan_date
FROM members
LEFT JOIN loans
  ON members.id = loans.member_id;
```

---

## FULL OUTER JOIN

Ein `FULL OUTER JOIN` zeigt alle Datensätze aus beiden Tabellen.

Wenn links oder rechts keine passende Verbindung existiert, werden fehlende Werte als `NULL` angezeigt.

Beispiel:

```sql
SELECT members.name, loans.loan_date
FROM members
FULL OUTER JOIN loans
  ON members.id = loans.member_id;
```

Das ist nützlich, wenn man sehen möchte:

```text
alle Mitglieder
alle Ausleihen
auch unverbundene Datensätze
```

Nicht jedes Datenbanksystem unterstützt `FULL OUTER JOIN` gleich.

---

## CROSS JOIN

Ein `CROSS JOIN` kombiniert jede Zeile der ersten Tabelle mit jeder Zeile der zweiten Tabelle.

Beispiel:

```sql
SELECT members.name, books.title
FROM members
CROSS JOIN books;
```

Wenn es 3 Mitglieder und 3 Bücher gibt, entstehen:

```text
3 × 3 = 9 Zeilen
```

`CROSS JOIN` braucht man seltener.

Vorsicht:

Bei großen Tabellen kann die Ergebnismenge extrem groß werden.

---

## Join-Bedingung mit ON

Die Join-Bedingung steht meistens nach `ON`.

Beispiel:

```sql
ON loans.member_id = members.id
```

Das bedeutet:

```text
Verbinde eine Ausleihe mit dem Mitglied, dessen id zur member_id passt.
```

Ohne passende Join-Bedingung entstehen falsche oder zu große Ergebnisse.

Die wichtigste Regel:

```text
JOIN immer über sinnvolle Schlüssel verbinden.
```

---

## Primärschlüssel und Fremdschlüssel beim Join

Joins nutzen meistens diese Struktur:

```text
tabelle_a.id = tabelle_b.tabelle_a_id
```

Beispiel:

```sql
ON members.id = loans.member_id
```

Hier ist:

| Teil              | Bedeutung       |
| ----------------- | --------------- |
| `members.id`      | Primärschlüssel |
| `loans.member_id` | Fremdschlüssel  |

Das ist eine typische 1:n-Beziehung.

---

## Aliase bei Joins

Bei Joins werden Tabellenaliase sehr häufig genutzt.

Ohne Alias:

```sql
SELECT members.name, loans.loan_date
FROM members
JOIN loans
  ON members.id = loans.member_id;
```

Mit Alias:

```sql
SELECT m.name, l.loan_date
FROM members AS m
JOIN loans AS l
  ON m.id = l.member_id;
```

Das ist kürzer und bei mehreren Tabellen besser lesbar.

---

## Mehrere Joins

Man kann mehr als zwei Tabellen verbinden.

Beispiel:

```sql
SELECT m.name, b.title, l.loan_date
FROM loans AS l
JOIN members AS m
  ON l.member_id = m.id
JOIN books AS b
  ON l.book_id = b.id;
```

Bedeutung:

```text
loans wird mit members verbunden.
loans wird mit books verbunden.
```

So entsteht eine lesbare Ausleihliste mit Namen und Buchtiteln.

---

## Join-Reihenfolge verstehen

Bei mehreren Joins sollte man Schritt für Schritt denken.

Ausgangspunkt:

```sql
FROM loans AS l
```

Dann:

```sql
JOIN members AS m
  ON l.member_id = m.id
```

Dann:

```sql
JOIN books AS b
  ON l.book_id = b.id
```

Die Tabelle `loans` ist hier die Verbindung zwischen Mitgliedern und Büchern.

Das ist oft bei Beziehungstabellen oder Ereignistabellen so.

---

## Joins und WHERE

Man kann Joins mit `WHERE` kombinieren.

Beispiel:

```sql
SELECT m.name, b.title, l.loan_date
FROM loans AS l
JOIN members AS m
  ON l.member_id = m.id
JOIN books AS b
  ON l.book_id = b.id
WHERE m.name = 'Max';
```

Das zeigt nur Ausleihen von Max.

Weiteres Beispiel:

```sql
SELECT m.name, b.title, l.loan_date
FROM loans AS l
JOIN members AS m
  ON l.member_id = m.id
JOIN books AS b
  ON l.book_id = b.id
WHERE l.loan_date >= '2026-08-01';
```

---

## LEFT JOIN und WHERE vorsichtig nutzen

Bei `LEFT JOIN` kann ein falsches `WHERE` den Effekt zerstören.

Beispiel:

```sql
SELECT m.name, l.loan_date
FROM members AS m
LEFT JOIN loans AS l
  ON m.id = l.member_id
WHERE l.loan_date >= '2026-08-01';
```

Problem:

Mit `WHERE l.loan_date >= ...` verschwinden Mitglieder ohne Ausleihe, weil `loan_date` bei ihnen `NULL` ist.

Dadurch verhält sich die Abfrage fast wie ein `INNER JOIN`.

Man muss bei `LEFT JOIN` bewusst prüfen, ob `NULL`-Zeilen erhalten bleiben sollen.

---

## Datensätze ohne Beziehung finden

Ein häufiger Anwendungsfall für `LEFT JOIN` ist:

```text
Zeige Datensätze ohne passende Verbindung.
```

Beispiel:

```sql
SELECT m.name
FROM members AS m
LEFT JOIN loans AS l
  ON m.id = l.member_id
WHERE l.id IS NULL;
```

Das zeigt Mitglieder ohne Ausleihen.

Die Logik:

```text
LEFT JOIN zeigt alle Mitglieder.
Bei Mitgliedern ohne Ausleihe ist l.id NULL.
WHERE l.id IS NULL filtert genau diese Fälle.
```

---

## Doppelte Zeilen durch Joins

Joins können mehrere Ergebniszeilen pro Datensatz erzeugen.

Beispiel:

Ein Mitglied hat drei Ausleihen.

Dann erscheint dieses Mitglied im Join-Ergebnis drei Mal.

```text
Max - SQL Einstieg
Max - Docker Praxis
Max - Linux Grundlagen
```

Das ist kein Fehler. Es zeigt die Beziehung korrekt.

Wenn man nur zählen möchte, nutzt man Aggregatfunktionen:

```sql
SELECT m.name, COUNT(l.id) AS loan_count
FROM members AS m
LEFT JOIN loans AS l
  ON m.id = l.member_id
GROUP BY m.name;
```

---

## n:m-Beziehung mit Join-Tabelle

Bei n:m-Beziehungen braucht man eine Zwischentabelle.

Beispiel:

```text
books
authors
book_authors
```

Ein Buch kann mehrere Autoren haben.  
Ein Autor kann mehrere Bücher schreiben.

Abfrage:

```sql
SELECT b.title, a.name
FROM books AS b
JOIN book_authors AS ba
  ON b.id = ba.book_id
JOIN authors AS a
  ON ba.author_id = a.id;
```

Die Join-Tabelle `book_authors` verbindet Bücher und Autoren.

---

## Beispiel n:m Ergebnis

Ergebnis:

| title            | name    |
| ---------------- | ------- |
| Linux Grundlagen | Müller  |
| Linux Grundlagen | Schmidt |
| SQL Einstieg     | Schmidt |

Das bedeutet:

```text
Linux Grundlagen hat zwei Autoren.
Schmidt ist Autor von mehreren Büchern.
```

Ohne Join-Tabelle wäre diese Beziehung schwer sauber abzubilden.

---

## Self Join

Ein Self Join verbindet eine Tabelle mit sich selbst.

Beispiel:

Eine Tabelle `employees` enthält Mitarbeiter und deren Vorgesetzte.

| id  | name | manager_id |
| --- | ---- | ---------- |
| 1   | Anna | NULL       |
| 2   | Max  | 1          |
| 3   | Lisa | 1          |

Abfrage:

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees AS e
LEFT JOIN employees AS m
  ON e.manager_id = m.id;
```

Hier wird `employees` zweimal verwendet:

```text
e = employee
m = manager
```

Self Joins sind am Anfang etwas schwerer, aber sehr nützlich bei Hierarchien.

---

## JOIN vs Subquery

Manchmal kann man ein Problem mit Join oder Subquery lösen.

Beispiel mit Join:

```sql
SELECT DISTINCT m.name
FROM members AS m
JOIN loans AS l
  ON m.id = l.member_id;
```

Beispiel mit Subquery:

```sql
SELECT name
FROM members
WHERE id IN (
  SELECT member_id
  FROM loans
);
```

Beide können ähnliche Ergebnisse liefern.

Joins sind oft besser, wenn man Daten aus mehreren Tabellen gleichzeitig anzeigen möchte.

Subqueries sind oft praktisch, wenn man eine Bedingung aus einer anderen Abfrage ableitet.

---

## Join mit Aggregatfunktionen

Joins werden oft mit `COUNT`, `SUM`, `MIN`, `MAX` oder `AVG` kombiniert.

Beispiel:

```sql
SELECT m.name, COUNT(l.id) AS loan_count
FROM members AS m
LEFT JOIN loans AS l
  ON m.id = l.member_id
GROUP BY m.name
ORDER BY loan_count DESC;
```

Das zeigt, wie viele Ausleihen jedes Mitglied hat.

Mit `LEFT JOIN` erscheinen auch Mitglieder mit 0 Ausleihen.

---

## GROUP BY bei Joins

Wenn man Aggregatfunktionen mit normalen Spalten kombiniert, braucht man meistens `GROUP BY`.

Beispiel:

```sql
SELECT m.name, COUNT(l.id)
FROM members AS m
LEFT JOIN loans AS l
  ON m.id = l.member_id
GROUP BY m.name;
```

Hier wird nach Mitglied gruppiert.

Ohne `GROUP BY` weiß die Datenbank nicht sauber, wie die normalen Spalten mit den gezählten Werten kombiniert werden sollen.

---

## Join-Ergebnis sortieren

Join-Ergebnisse können mit `ORDER BY` sortiert werden.

Beispiel:

```sql
SELECT m.name, b.title, l.loan_date
FROM loans AS l
JOIN members AS m
  ON l.member_id = m.id
JOIN books AS b
  ON l.book_id = b.id
ORDER BY l.loan_date DESC;
```

Das zeigt die neuesten Ausleihen zuerst.

---

## Join-Ergebnis begrenzen

Bei großen Tabellen kann man `LIMIT` nutzen.

```sql
SELECT m.name, b.title, l.loan_date
FROM loans AS l
JOIN members AS m
  ON l.member_id = m.id
JOIN books AS b
  ON l.book_id = b.id
ORDER BY l.loan_date DESC
LIMIT 20;
```

Das zeigt die 20 neuesten Ausleihen.

---

## Typische Join-Fehler

| Fehler                                             | Problem                                  |
| -------------------------------------------------- | ---------------------------------------- |
| Join-Bedingung vergessen                           | extrem große falsche Ergebnismenge       |
| falsche Spalten verbunden                          | falsche Daten werden kombiniert          |
| INNER JOIN statt LEFT JOIN                         | Datensätze ohne Beziehung verschwinden   |
| LEFT JOIN mit falschem WHERE                       | verhält sich plötzlich wie INNER JOIN    |
| Tabellenreihenfolge bei LEFT JOIN nicht verstanden | falsche Datensätze bleiben erhalten      |
| n:m ohne Zwischentabelle                           | unsaubere Datenstruktur                  |
| Aliase unklar benannt                              | Abfrage wird schwer lesbar               |
| `SELECT *` bei Joins                               | Spaltennamen doppelt und unübersichtlich |
| Duplikate nicht verstanden                         | 1:n erzeugt mehrere Ergebniszeilen       |
| fehlende Fremdschlüssel                            | Beziehungen sind nicht abgesichert       |

---

## Gute Arbeitsweise bei Joins

Eine gute Arbeitsweise:

1. Tabellen einzeln anschauen
2. Primärschlüssel und Fremdschlüssel erkennen
3. Beziehung in Worten formulieren
4. erste Tabelle bewusst wählen
5. Join-Bedingung mit `ON` sauber schreiben
6. zuerst nur wenige Spalten auswählen
7. Ergebnis mit `LIMIT` prüfen
8. erst danach Filter und Sortierung ergänzen
9. bei `LEFT JOIN` auf `NULL` achten
10. bei mehreren Joins Schritt für Schritt erweitern

Guter Start:

```sql
SELECT *
FROM members
LIMIT 10;
```

Dann:

```sql
SELECT *
FROM loans
LIMIT 10;
```

Dann Join:

```sql
SELECT m.name, l.loan_date
FROM members AS m
JOIN loans AS l
  ON m.id = l.member_id
LIMIT 10;
```

---

## Praktische Beispiele

### Beispiel 1: Mitglieder mit Ausleihen

```sql
SELECT m.name, l.loan_date
FROM members AS m
JOIN loans AS l
  ON m.id = l.member_id;
```

### Beispiel 2: Alle Mitglieder anzeigen, auch ohne Ausleihe

```sql
SELECT m.name, l.loan_date
FROM members AS m
LEFT JOIN loans AS l
  ON m.id = l.member_id;
```

### Beispiel 3: Mitglieder ohne Ausleihe finden

```sql
SELECT m.name
FROM members AS m
LEFT JOIN loans AS l
  ON m.id = l.member_id
WHERE l.id IS NULL;
```

### Beispiel 4: Bücher mit Autoren anzeigen

```sql
SELECT b.title, a.name
FROM books AS b
JOIN book_authors AS ba
  ON b.id = ba.book_id
JOIN authors AS a
  ON ba.author_id = a.id;
```

---

## FISI-Bezug

Für FISI sind Joins wichtig, weil Daten in echten IT-Systemen selten nur in einer Tabelle liegen.

In der Praxis helfen Joins bei:

- Datenbankstrukturen verstehen
- Ticketsystemdaten auswerten
- Benutzer und Rollen verbinden
- Geräte und Standorte verbinden
- Bücher, Mitglieder und Ausleihen verbinden
- SQL-Projekte dokumentieren
- Adminer oder psql sinnvoll nutzen
- Fehler in Datenbeziehungen erkennen
- Docker-Datenbankprojekte testen
- mit Entwicklern über Datenmodelle sprechen

Ein FISI muss Joins nicht sofort perfekt optimieren können. Aber `INNER JOIN`, `LEFT JOIN`, Primärschlüssel, Fremdschlüssel und Join-Bedingungen sollten verstanden werden.

---

## Kurze Zusammenfassung

Joins verbinden Daten aus mehreren Tabellen.

Ein `INNER JOIN` zeigt nur passende Datensätze auf beiden Seiten. Ein `LEFT JOIN` zeigt alle Datensätze aus der linken Tabelle und passende Daten aus der rechten Tabelle.

Die linke Tabelle ist die Tabelle direkt nach `FROM`.

Joins werden meistens über Primärschlüssel und Fremdschlüssel geschrieben, zum Beispiel `members.id = loans.member_id`.

Für n:m-Beziehungen braucht man eine Zwischentabelle. Joins sind für relationale Datenbanken sehr wichtig, weil Daten bewusst auf mehrere Tabellen verteilt werden.
