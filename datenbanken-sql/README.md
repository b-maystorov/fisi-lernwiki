# Datenbanken & SQL

In diesem Bereich geht es um relationale Datenbanken und SQL.

Datenbanken sind ein wichtiger Teil der IT-Systemintegration, weil viele Anwendungen Daten dauerhaft speichern, verwalten und auswerten müssen. SQL wird genutzt, um Tabellen zu erstellen, Daten einzufügen, zu lesen, zu ändern und zu löschen.

Für Fachinformatiker für Systemintegration ist SQL wichtig, weil man Datenbanken oft nicht nur theoretisch kennen muss. Man muss verstehen, wie Tabellen aufgebaut sind, wie Beziehungen funktionieren, wie Abfragen geschrieben werden und wie man Fehler in Datenbankstrukturen oder SQL-Befehlen erkennt.

---

## Kurz erklärt

Eine relationale Datenbank speichert Daten in Tabellen.

SQL bedeutet:

```text
Structured Query Language
```

SQL ist die Sprache, mit der man relationale Datenbanken abfragt und verwaltet.

Typische Aufgaben mit SQL:

- Datenbanken verstehen
- Tabellen erstellen
- Daten einfügen
- Daten abfragen
- Daten ändern
- Daten löschen
- Tabellen miteinander verbinden
- Beziehungen zwischen Daten modellieren
- Schlüssel und Constraints nutzen
- einfache Auswertungen durchführen

---

## Kapitelübersicht

| Kapitel                                                                           | Thema                                                              |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| [1. Datenbank-Grundlagen](./01-datenbank-grundlagen.md)                           | Grundbegriffe, Tabellen, Datensätze und relationale Datenbanken    |
| [2. Tabellen, Schlüssel und Beziehungen](./02-tabellen-schluessel-beziehungen.md) | Primärschlüssel, Fremdschlüssel, Beziehungen und Datenmodellierung |
| [3. SQL-Grundlagen](./03-sql-grundlagen.md)                                       | Grundstruktur von SQL-Befehlen und wichtige SQL-Kategorien         |
| [4. SELECT, Filter und Sortierung](./04-select-filter-sortierung.md)              | Daten abfragen, filtern, sortieren und begrenzen                   |
| [5. Joins und Beziehungen](./05-joins-und-beziehungen.md)                         | Tabellen verbinden und relationale Daten auswerten                 |
| [6. Daten ändern und verwalten](./06-daten-aendern-und-verwalten.md)              | INSERT, UPDATE, DELETE, Constraints und saubere Datenpflege        |

---

## Warum Datenbanken wichtig sind

Fast jede größere IT-Anwendung arbeitet mit Daten.

Beispiele:

| Anwendung          | Gespeicherte Daten                    |
| ------------------ | ------------------------------------- |
| Onlineshop         | Kunden, Produkte, Bestellungen        |
| Bibliothekssystem  | Bücher, Mitglieder, Ausleihen         |
| Ticketsystem       | Benutzer, Tickets, Status, Kommentare |
| Schulverwaltung    | Schüler, Kurse, Noten, Termine        |
| Netzwerkverwaltung | Geräte, IP-Adressen, Standorte        |
| Monitoring-System  | Messwerte, Logs, Ereignisse           |

Ohne Datenbank müssten diese Informationen unstrukturiert in Dateien oder Listen gespeichert werden. Das wäre schwer zu verwalten, schwer zu durchsuchen und fehleranfällig.

Eine Datenbank sorgt dafür, dass Daten strukturiert, dauerhaft und gezielt abrufbar bleiben.

---

## Wichtige Grundbegriffe

| Begriff         | Bedeutung                                             |
| --------------- | ----------------------------------------------------- |
| Datenbank       | Sammlung strukturierter Daten                         |
| Tabelle         | geordnete Datenstruktur mit Zeilen und Spalten        |
| Spalte          | ein bestimmtes Merkmal, zum Beispiel Name oder E-Mail |
| Zeile           | ein einzelner Datensatz                               |
| Datensatz       | zusammengehörende Informationen in einer Zeile        |
| Primärschlüssel | eindeutige Kennung eines Datensatzes                  |
| Fremdschlüssel  | Verweis auf einen Datensatz in einer anderen Tabelle  |
| Constraint      | Regel für Daten in einer Tabelle                      |
| Query           | SQL-Abfrage                                           |
| Relation        | Beziehung zwischen Tabellen                           |

---

## SQL-Befehlskategorien

SQL-Befehle lassen sich grob in verschiedene Bereiche einteilen.

| Kategorie | Bedeutung                         | Beispiele                    |
| --------- | --------------------------------- | ---------------------------- |
| DDL       | Struktur der Datenbank definieren | `CREATE`, `ALTER`, `DROP`    |
| DML       | Daten bearbeiten                  | `INSERT`, `UPDATE`, `DELETE` |
| DQL       | Daten abfragen                    | `SELECT`                     |
| DCL       | Rechte verwalten                  | `GRANT`, `REVOKE`            |
| TCL       | Transaktionen steuern             | `COMMIT`, `ROLLBACK`         |

Für den Anfang sind besonders wichtig:

```text
CREATE
INSERT
SELECT
UPDATE
DELETE
```

---

## Typischer SQL-Ablauf

Ein einfacher Ablauf mit SQL sieht oft so aus:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT
);

INSERT INTO users (id, name, email)
VALUES (1, 'Max', 'max@example.com');

SELECT *
FROM users;

UPDATE users
SET email = 'max.neu@example.com'
WHERE id = 1;

DELETE FROM users
WHERE id = 1;
```

Dieser Ablauf zeigt die wichtigsten Grundaktionen:

```text
Tabelle erstellen
Daten einfügen
Daten lesen
Daten ändern
Daten löschen
```

---

## Relationale Daten verstehen

Relationale Datenbanken speichern Daten nicht einfach in einer großen Tabelle.

Stattdessen werden Daten auf mehrere Tabellen verteilt.

Beispiel Bibliothek:

```text
books
authors
members
loans
```

Dadurch vermeidet man viele doppelte Daten.

Ein Buch kann zum Beispiel mit einem Autor verbunden sein. Eine Ausleihe kann mit einem Mitglied und einem Buch-Exemplar verbunden sein.

Diese Verbindungen entstehen über Schlüssel:

```text
Primary Key
Foreign Key
```

Das ist wichtig, damit die Datenbank weiß, welche Datensätze zusammengehören.

---

## SQL und FISI-Praxis

Für FISI ist SQL aus mehreren Gründen wichtig.

In der Praxis kann man SQL brauchen für:

- Datenbankgrundlagen verstehen
- Anwendungen mit Datenbankanbindung betreuen
- einfache Datenbankabfragen schreiben
- Fehler in Tabellen oder Beziehungen erkennen
- Daten kontrollieren
- Testdaten einfügen
- Admin-Tools wie Adminer oder phpMyAdmin nutzen
- Docker-Datenbankprojekte verstehen
- Ticketsysteme oder Monitoring-Systeme nachvollziehen
- mit Entwicklern über Datenstrukturen sprechen

Man muss als FISI nicht direkt Datenbankentwickler sein, aber man sollte die Grundlagen sicher verstehen.

---

## Verbindung zu Docker

Datenbanken werden in Lern- und Testprojekten oft mit Docker gestartet.

Beispiel:

```text
PostgreSQL + Adminer
```

Docker Compose kann eine Datenbank und eine Weboberfläche gemeinsam starten.

Beispiel:

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_PASSWORD: example
    volumes:
      - db_data:/var/lib/postgresql/data

  adminer:
    image: adminer
    ports:
      - "8080:8080"

volumes:
  db_data:
```

Dadurch kann man SQL praktisch üben, ohne die Datenbank direkt auf dem Host-System zu installieren.

---

## Typische Fehler

| Fehler                         | Problem                                             |
| ------------------------------ | --------------------------------------------------- |
| `SELECT *` immer nutzen        | oft unübersichtlich bei großen Tabellen             |
| `WHERE` bei `UPDATE` vergessen | zu viele Datensätze werden geändert                 |
| `WHERE` bei `DELETE` vergessen | zu viele Datensätze werden gelöscht                 |
| Primärschlüssel vergessen      | Datensätze sind nicht eindeutig identifizierbar     |
| Fremdschlüssel falsch setzen   | Beziehungen funktionieren nicht sauber              |
| `NULL` falsch verstehen        | `NULL` bedeutet kein Wert, nicht 0 oder leerer Text |
| Datentypen falsch wählen       | Daten werden unpassend gespeichert                  |
| Joins ohne Beziehung schreiben | Ergebnisse werden falsch oder zu groß               |
| Tabellen zu groß planen        | viele doppelte Daten entstehen                      |
| Datenbank nicht dokumentieren  | Struktur ist später schwer verständlich             |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise mit SQL:

1. Tabellenstruktur verstehen
2. Primärschlüssel und Fremdschlüssel prüfen
3. kleine Testdaten einfügen
4. einfache `SELECT`-Abfragen schreiben
5. Filter mit `WHERE` nutzen
6. Sortierung mit `ORDER BY` prüfen
7. Joins langsam aufbauen
8. Datenänderungen immer mit `WHERE` absichern
9. Struktur dokumentieren
10. Fehler anhand der Meldung lesen

Wichtig ist:

```text
Erst verstehen, dann ändern.
```

Besonders bei `UPDATE` und `DELETE` sollte man vorsichtig arbeiten.

---

## Praktische Lernziele

Nach diesem Bereich sollte man erklären können:

- was eine relationale Datenbank ist
- wofür Tabellen, Zeilen und Spalten genutzt werden
- was Primärschlüssel und Fremdschlüssel sind
- wie einfache SQL-Abfragen aufgebaut sind
- wie `SELECT`, `WHERE`, `ORDER BY` und `LIMIT` funktionieren
- wie man Daten mit `INSERT`, `UPDATE` und `DELETE` verändert
- warum Joins wichtig sind
- wie Tabellen miteinander verbunden werden
- welche Fehler bei SQL häufig passieren
- warum SQL auch für FISI relevant ist

---

## Kurze Zusammenfassung

Datenbanken speichern Daten strukturiert und dauerhaft.

SQL ist die Sprache, mit der relationale Datenbanken abgefragt und verwaltet werden.

Die wichtigsten SQL-Grundlagen sind Tabellen, Datensätze, Spalten, Primärschlüssel, Fremdschlüssel, `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `WHERE`, `ORDER BY`, `LIMIT` und Joins.

Für FISI ist SQL wichtig, weil viele IT-Systeme im Hintergrund Datenbanken nutzen. Wer SQL-Grundlagen versteht, kann Anwendungen, Datenbankprojekte und Fehlersuche besser nachvollziehen.
