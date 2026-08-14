# 5.9 Software testen und debuggen

In diesem Kapitel geht es darum, Software zu testen und Fehler systematisch zu finden.

Software funktioniert selten sofort perfekt. Fehler können durch falsche Logik, falsche Eingaben, fehlende Dateien, ungültige Daten, falsche Konfigurationen, Netzwerkprobleme, Rechteprobleme oder unerwartete Benutzeraktionen entstehen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Software im Betrieb zuverlässig laufen muss. Ein FISI muss Fehler erkennen, Fehlermeldungen verstehen, Logs auswerten, Tests durchführen und Probleme nachvollziehbar eingrenzen können.

---

## Kurz erklärt

Testen bedeutet, zu prüfen, ob eine Software korrekt funktioniert.

Debuggen bedeutet, Fehler im Code oder Ablauf zu suchen und zu beheben.

Wichtige Themen sind:

- Testziele
- Testfälle
- Testdaten
- erwartetes Ergebnis
- tatsächliches Ergebnis
- manuelle Tests
- automatische Tests
- Unit-Tests
- Integrationstests
- Systemtests
- Abnahmetests
- Regressionstests
- Fehlermeldungen
- Logs
- Debugger
- Breakpoints
- Fehleranalyse
- Fehlerdokumentation
- Fehlerbehebung

Tests und Debugging helfen, Software stabiler, sicherer und wartbarer zu machen.

---

## Warum Testen wichtig ist

Tests sollen Fehler finden, bevor Benutzer oder produktive Systeme betroffen sind.

Ohne Tests können Probleme entstehen:

- Funktionen arbeiten falsch
- Daten werden falsch gespeichert
- Benutzer bekommen falsche Ergebnisse
- Software stürzt ab
- Sicherheitslücken bleiben unentdeckt
- Fehler treten erst im Produktivbetrieb auf
- Änderungen beschädigen alte Funktionen
- Dokumentation und Realität passen nicht zusammen
- Vertrauen in die Software sinkt

Testen bedeutet nicht, dass eine Software garantiert fehlerfrei ist.

Testen reduziert aber das Risiko und macht Probleme früher sichtbar.

---

## Warum Debugging wichtig ist

Debugging ist die gezielte Fehlersuche.

Wenn ein Programm nicht funktioniert, reicht es nicht zu sagen:

> Es geht nicht.

Man muss herausfinden:

- was genau passiert
- wann es passiert
- welche Eingabe betroffen ist
- welche Fehlermeldung erscheint
- welcher Programmteil beteiligt ist
- ob Daten korrekt sind
- ob die Umgebung korrekt ist
- ob Rechte oder Konfigurationen fehlen
- welche Änderung den Fehler verursacht hat

Debugging hilft, nicht nur Symptome zu behandeln, sondern die Ursache zu verstehen.

---

## Unterschied zwischen Testen und Debuggen

| Begriff  | Bedeutung                                     |
| -------- | --------------------------------------------- |
| Testen   | prüfen, ob Software wie erwartet funktioniert |
| Debuggen | Ursache eines Fehlers suchen und beheben      |

Beispiel:

Ein Test zeigt, dass eine Suchfunktion keine Ergebnisse liefert.

Beim Debugging wird dann untersucht, warum das passiert:

- falsche SQL-Abfrage
- leerer Suchbegriff
- falscher Tabellenname
- keine Daten in der Datenbank
- Rechteproblem
- Fehler in der Programmlogik

Testen findet das Problem.
Debugging erklärt und behebt das Problem.

---

## Fehlerarten

Softwarefehler können verschiedene Ursachen haben.

| Fehlerart            | Beispiel                                         |
| -------------------- | ------------------------------------------------ |
| Syntaxfehler         | Code ist formal falsch geschrieben               |
| Logikfehler          | Code läuft, aber Ergebnis ist falsch             |
| Laufzeitfehler       | Fehler entsteht während der Ausführung           |
| Eingabefehler        | Benutzer gibt ungültige Daten ein                |
| Datenfehler          | Daten sind unvollständig oder widersprüchlich    |
| Konfigurationsfehler | falscher Pfad, Port oder Servername              |
| Rechtefehler         | Benutzer darf Datei oder Datenbank nicht nutzen  |
| Netzwerkfehler       | Zielsystem ist nicht erreichbar                  |
| Schnittstellenfehler | API oder Datenbank antwortet anders als erwartet |
| Sicherheitsfehler    | Eingaben oder Rechte werden nicht sauber geprüft |

Ein Fehler kann auch mehrere Ursachen gleichzeitig haben.

---

## Syntaxfehler

Ein Syntaxfehler bedeutet, dass der Code formal falsch geschrieben ist.

Beispiel in Python:

```python
if age >= 18
    print("Volljährig")
```

Hier fehlt der Doppelpunkt nach der Bedingung.

Korrekt:

```python
if age >= 18:
    print("Volljährig")
```

Syntaxfehler werden oft direkt beim Start des Programms angezeigt.

Sie sind meistens leichter zu finden als Logikfehler, weil der Interpreter oder Compiler eine konkrete Stelle meldet.

---

## Logikfehler

Ein Logikfehler bedeutet, dass der Code ausgeführt wird, aber fachlich falsch arbeitet.

Beispiel:

```python
price = 100
discount = 20

final_price = price + discount
print(final_price)
```

Der Code läuft, aber das Ergebnis ist falsch, wenn der Rabatt eigentlich abgezogen werden sollte.

Korrekt:

```python
price = 100
discount = 20

final_price = price - discount
print(final_price)
```

Logikfehler sind oft schwieriger zu finden, weil keine Fehlermeldung erscheint.

Das Programm macht einfach das Falsche.

---

## Laufzeitfehler

Ein Laufzeitfehler entsteht während das Programm läuft.

Beispiele:

```python
number = int("abc")
```

Dieser Code erzeugt einen Fehler, weil `"abc"` nicht in eine Zahl umgewandelt werden kann.

Ein anderes Beispiel:

```python
with open("server.log", "r") as file:
    content = file.read()
```

Wenn die Datei `server.log` nicht existiert, entsteht ein Fehler.

Laufzeitfehler müssen durch gute Fehlerbehandlung und Tests berücksichtigt werden.

---

## Testziele

Vor dem Testen sollte klar sein, was geprüft werden soll.

Mögliche Testziele:

- Funktion arbeitet korrekt
- Eingaben werden geprüft
- Fehlerfälle werden abgefangen
- Daten werden korrekt gespeichert
- Benutzerrechte funktionieren
- Ausgabe ist verständlich
- Software läuft in der Zielumgebung
- Schnittstellen funktionieren
- Performance ist ausreichend
- Sicherheitsanforderungen sind erfüllt

Ohne Testziel werden Tests zufällig und unvollständig.

---

## Testfall

Ein Testfall beschreibt, was genau getestet wird.

Ein guter Testfall enthält:

- Testfall-ID
- Beschreibung
- Voraussetzung
- Eingabedaten
- Testschritte
- erwartetes Ergebnis
- tatsächliches Ergebnis
- Status
- Bemerkungen

Beispiel:

| Feld                   | Inhalt                                |
| ---------------------- | ------------------------------------- |
| Testfall-ID            | T-001                                 |
| Beschreibung           | Benutzer erstellt ein Ticket          |
| Voraussetzung          | Benutzer ist angemeldet               |
| Eingabe                | Titel und Beschreibung                |
| Erwartetes Ergebnis    | Ticket wird gespeichert und angezeigt |
| Tatsächliches Ergebnis | Ticket wird gespeichert               |
| Status                 | bestanden                             |

Testfälle machen Tests nachvollziehbar.

---

## Erwartetes und tatsächliches Ergebnis

Beim Testen ist der Unterschied zwischen erwartetem und tatsächlichem Ergebnis wichtig.

| Begriff                | Bedeutung                           |
| ---------------------- | ----------------------------------- |
| erwartetes Ergebnis    | was laut Anforderung passieren soll |
| tatsächliches Ergebnis | was beim Test wirklich passiert     |

Wenn beide übereinstimmen, ist der Test bestanden.

Wenn sie nicht übereinstimmen, liegt ein Fehler oder eine unklare Anforderung vor.

Beispiel:

Erwartet:

- Benutzer ohne Adminrechte darf keinen Datensatz löschen.

Tatsächlich:

- Benutzer ohne Adminrechte kann Datensatz löschen.

Das ist ein Sicherheitsfehler.

---

## Testdaten

Testdaten sind Daten, mit denen eine Software geprüft wird.

Beispiele:

- gültige Benutzerdaten
- ungültige Eingaben
- leere Felder
- sehr lange Texte
- Sonderzeichen
- doppelte Einträge
- falsche Datentypen
- Beispielkunden
- Testtickets
- Testgeräte
- Testdateien

Gute Tests nutzen nicht nur perfekte Eingaben.

Sie prüfen auch, was bei falschen oder ungewöhnlichen Eingaben passiert.

---

## Keine echten sensiblen Daten in Tests

In Tests sollten keine echten sensiblen Daten verwendet werden.

Nicht geeignet:

- echte Kundendaten
- echte Personaldaten
- echte Passwörter
- echte Rechnungen
- echte medizinische Daten
- echte interne Zugangsdaten
- produktive Datenbankkopien ohne Schutz

Besser:

- künstliche Testdaten
- anonymisierte Daten
- kleine Beispieldatensätze
- Testkonten
- lokale Testdateien

Das ist besonders wichtig bei öffentlichen Repositories, Schulprojekten und Lernumgebungen.

---

## Manuelle Tests

Manuelle Tests werden von Menschen durchgeführt.

Beispiel:

Ein Benutzer klickt durch eine Anwendung und prüft, ob alles funktioniert.

Vorteile:

- leicht durchzuführen
- gut für Bedienung und Oberfläche
- gut für erste Prüfung
- Benutzerfeedback möglich

Nachteile:

- zeitaufwendig
- nicht immer gleich wiederholbar
- Fehler können übersehen werden
- bei vielen Änderungen unpraktisch

Manuelle Tests sind sinnvoll, ersetzen aber bei größeren Projekten keine automatischen Tests.

---

## Automatische Tests

Automatische Tests werden durch Code oder Testwerkzeuge ausgeführt.

Vorteile:

- schnell wiederholbar
- gleiche Prüfung bei jeder Ausführung
- gut für häufige Änderungen
- Fehler werden früher erkannt
- gut für CI/CD
- alte Funktionen können erneut geprüft werden

Nachteile:

- müssen erst geschrieben werden
- prüfen nur das, was definiert wurde
- brauchen Pflege
- können bei schlechten Tests falsche Sicherheit geben

Automatische Tests sind besonders hilfreich, wenn Software regelmäßig erweitert wird.

---

## Unit-Test

Ein Unit-Test prüft einen kleinen, einzelnen Programmteil.

Meistens wird eine einzelne Funktion getestet.

Beispiel:

```python
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
```

Unit-Tests sind gut, weil sie Fehler in kleinen Bereichen sichtbar machen.

Wenn eine Funktion einzeln korrekt arbeitet, ist das eine gute Grundlage für größere Tests.

---

## Integrationstest

Ein Integrationstest prüft, ob mehrere Teile zusammen funktionieren.

Beispiele:

- Anwendung verbindet sich mit Datenbank
- Backend verarbeitet Daten aus Formular
- API liefert Daten an Frontend
- Python-Skript liest CSV-Datei und schreibt Ergebnis
- Login nutzt Benutzerverwaltung und Rechteprüfung

Integrationstests sind wichtig, weil einzelne Teile für sich funktionieren können, aber im Zusammenspiel trotzdem Fehler entstehen können.

---

## Systemtest

Ein Systemtest prüft die gesamte Software als vollständiges System.

Dabei wird getestet, ob die Anwendung insgesamt funktioniert.

Beispiele:

- Benutzer meldet sich an
- Benutzer erstellt Datensatz
- Datensatz wird gespeichert
- Datensatz erscheint in Übersicht
- Benutzer meldet sich ab

Systemtests prüfen die Software aus einer größeren Sicht.

Sie sind näher an der echten Nutzung als Unit-Tests.

---

## Abnahmetest

Ein Abnahmetest prüft, ob die Software die vereinbarten Anforderungen erfüllt.

Dabei wird häufig aus Sicht des Kunden oder Benutzers getestet.

Beispiel:

Anforderung:

- Ein Support-Mitarbeiter kann ein Ticket erstellen, bearbeiten und schließen.

Abnahmetest:

- Support-Mitarbeiter erstellt Testticket
- ändert Priorität
- weist Bearbeiter zu
- schließt Ticket
- prüft Anzeige in der Übersicht

Der Abnahmetest entscheidet oft, ob ein Projektergebnis akzeptiert wird.

---

## Regressionstest

Ein Regressionstest prüft, ob alte Funktionen nach einer Änderung weiterhin funktionieren.

Beispiel:

Eine neue Exportfunktion wird eingebaut.

Danach muss geprüft werden, ob alte Funktionen wie Login, Suche und Speichern weiterhin funktionieren.

Regressionstests sind wichtig, weil Änderungen manchmal bestehende Funktionen beschädigen.

Automatische Tests sind für Regressionstests besonders hilfreich.

---

## Smoke-Test

Ein Smoke-Test ist ein kurzer Grundtest.

Er prüft, ob die wichtigsten Funktionen grundsätzlich laufen.

Beispiele:

- Anwendung startet
- Login-Seite ist erreichbar
- Datenbankverbindung funktioniert
- Hauptseite lädt
- wichtigste Funktion reagiert

Smoke-Tests werden oft nach Updates oder Deployments genutzt.

Sie zeigen schnell, ob etwas grundsätzlich kaputt ist.

---

## Black-Box-Test

Beim Black-Box-Test wird die Software von außen getestet.

Der Tester kennt den inneren Code nicht.

Er prüft nur:

- Eingabe
- Verhalten
- Ausgabe
- Fehlermeldungen
- Benutzeroberfläche

Beispiel:

Ein Benutzer gibt ein falsches Passwort ein und prüft, ob die Anmeldung abgelehnt wird.

Black-Box-Tests sind gut, um aus Benutzersicht zu testen.

---

## White-Box-Test

Beim White-Box-Test kennt der Tester den Code oder die interne Struktur.

Dabei wird gezielt geprüft:

- Funktionen
- Bedingungen
- Schleifen
- Codepfade
- Datenflüsse
- Fehlerbehandlung

White-Box-Tests sind gut, um die technische Logik zu prüfen.

Entwickler nutzen diese Form oft bei Unit-Tests.

---

## Grenzwerttests

Grenzwerttests prüfen Werte an Grenzen.

Beispiel:

Eine Eingabe erlaubt Zahlen von 1 bis 100.

Wichtige Testwerte:

- 0
- 1
- 2
- 99
- 100
- 101

Fehler treten oft an Grenzen auf.

Deshalb sind Grenzwerttests sehr wichtig.

---

## Negativtests

Negativtests prüfen, ob Software mit falschen Eingaben korrekt umgeht.

Beispiele:

- Pflichtfeld leer lassen
- falsches Passwort eingeben
- Text statt Zahl eingeben
- sehr lange Eingabe nutzen
- ungültige Datei hochladen
- Sonderzeichen eingeben
- doppelten Benutzernamen erstellen
- Zugriff ohne Rechte versuchen

Negativtests sind wichtig, weil Benutzer und Angreifer nicht immer perfekte Eingaben liefern.

---

## Testprotokoll

Ein Testprotokoll dokumentiert durchgeführte Tests.

Typische Inhalte:

- Testdatum
- Tester
- Softwareversion
- Umgebung
- Testfall
- Eingaben
- erwartetes Ergebnis
- tatsächliches Ergebnis
- bestanden oder fehlgeschlagen
- Bemerkungen
- gefundene Fehler

Ein Testprotokoll ist wichtig für Nachvollziehbarkeit.

Gerade bei Projekten, Abnahmen und Fehlersuche hilft es zu wissen, was bereits geprüft wurde.

---

## Fehlerdokumentation

Wenn ein Fehler gefunden wird, sollte er sauber dokumentiert werden.

Eine gute Fehlerbeschreibung enthält:

- kurze Fehlerbeschreibung
- Schritte zur Reproduktion
- erwartetes Ergebnis
- tatsächliches Ergebnis
- Fehlermeldung
- Screenshot oder Logauszug, wenn sinnvoll
- betroffene Version
- betroffene Umgebung
- Schweregrad
- Status
- Bearbeiter

Schlecht:

> Geht nicht.

Besser:

> Beim Speichern eines Tickets ohne Titel erscheint keine Fehlermeldung. Das Ticket wird trotzdem gespeichert. Erwartet wäre, dass der Titel als Pflichtfeld geprüft wird.

Eine gute Fehlerbeschreibung spart viel Zeit.

---

## Fehler reproduzieren

Ein Fehler ist besser analysierbar, wenn man ihn reproduzieren kann.

Reproduzieren bedeutet:

> Man kann den Fehler mit klaren Schritten erneut auslösen.

Beispiel:

1. Anwendung starten.
2. Als normaler Benutzer anmelden.
3. Neues Ticket öffnen.
4. Titel leer lassen.
5. Auf Speichern klicken.
6. Ticket wird ohne Titel gespeichert.

Wenn ein Fehler nicht reproduzierbar ist, wird die Analyse schwieriger.

Dann helfen Logs, Zeitpunkte, Systemzustand und Benutzerinformationen.

---

## Debugging-Vorgehen

Ein sinnvolles Debugging-Vorgehen:

1. Fehler genau lesen
2. Fehler reproduzieren
3. letzte Änderungen prüfen
4. Eingaben kontrollieren
5. Daten und Variablen prüfen
6. Logs ansehen
7. betroffenen Programmteil eingrenzen
8. kleine Änderung durchführen
9. erneut testen
10. Lösung dokumentieren

Wichtig ist, nicht wild viele Dinge gleichzeitig zu ändern.

Sonst weiß man später nicht, welche Änderung den Fehler wirklich behoben hat.

---

## Fehlermeldungen lesen

Fehlermeldungen enthalten oft wichtige Hinweise.

Man sollte prüfen:

- welche Datei betroffen ist
- welche Zeile genannt wird
- welcher Fehlertyp angezeigt wird
- welche Funktion beteiligt ist
- welche Eingabe den Fehler ausgelöst hat
- ob ein Pfad, Port oder Name falsch ist
- ob Rechte fehlen
- ob eine Abhängigkeit fehlt

Fehlermeldungen wirken am Anfang oft kompliziert.

Trotzdem sind sie meistens der beste Startpunkt für die Fehlersuche.

---

## Python-Fehlermeldungen

Python zeigt bei Fehlern oft einen Traceback.

Beispiel:

```text
Traceback (most recent call last):
  File "main.py", line 3, in <module>
    age = int("abc")
ValueError: invalid literal for int() with base 10: 'abc'
```

Wichtige Informationen:

| Teil              | Bedeutung              |
| ----------------- | ---------------------- |
| `main.py`         | Datei mit Fehler       |
| `line 3`          | Zeile mit Fehler       |
| `int("abc")`      | problematische Stelle  |
| `ValueError`      | Fehlertyp              |
| `invalid literal` | Erklärung des Problems |

Hier ist das Problem, dass `"abc"` keine gültige Zahl ist.

---

## Häufige Python-Fehler

| Fehler                | Bedeutung                                   |
| --------------------- | ------------------------------------------- |
| `SyntaxError`         | Code ist formal falsch                      |
| `IndentationError`    | Einrückung ist falsch                       |
| `NameError`           | Variable oder Funktion existiert nicht      |
| `TypeError`           | falscher Datentyp                           |
| `ValueError`          | Wert passt nicht zur Umwandlung             |
| `FileNotFoundError`   | Datei wurde nicht gefunden                  |
| `KeyError`            | Dictionary-Schlüssel existiert nicht        |
| `IndexError`          | Listenindex existiert nicht                 |
| `ModuleNotFoundError` | Modul oder Paket fehlt                      |
| `PermissionError`     | Zugriff auf Datei oder Ordner nicht erlaubt |

Diese Fehler sollte man nicht auswendig lernen müssen, aber man sollte sie lesen und einordnen können.

---

## Debugging mit print

Eine einfache Debugging-Methode ist `print()`.

Beispiel:

```python
username = input("Username: ")

print("DEBUG username:", username)

if username == "admin":
    print("Admin login")
```

Mit Debug-Ausgaben kann man prüfen:

- Welche Werte haben Variablen?
- Wird ein Codeblock erreicht?
- Welche Eingabe kommt wirklich an?
- Welche Zwischenergebnisse entstehen?

Für kleine Programme ist das sehr hilfreich.

Für größere Programme sollte man eher Logging oder einen Debugger nutzen.

---

## Debugger

Ein Debugger ist ein Werkzeug zur gezielten Fehlersuche.

Mit einem Debugger kann man:

- Haltepunkte setzen
- Programm Schritt für Schritt ausführen
- Variablen ansehen
- Funktionsaufrufe verfolgen
- Bedingungen prüfen
- Fehlerstellen genauer analysieren

In VS Code kann man Python-Programme mit einem Debugger starten und Schritt für Schritt untersuchen.

Das ist besonders nützlich, wenn ein Fehler nicht sofort sichtbar ist.

---

## Breakpoints

Ein Breakpoint ist ein Haltepunkt im Code.

Wenn das Programm diese Stelle erreicht, stoppt es dort.

Dann kann man prüfen:

- welche Variablenwerte vorhanden sind
- welche Funktion gerade läuft
- welche Bedingung wahr oder falsch ist
- welcher Code als Nächstes ausgeführt wird

Breakpoints helfen, den Programmablauf zu verstehen.

Sie sind oft besser als viele `print()`-Ausgaben.

---

## Logging beim Debugging

Logging ist professioneller als reine `print()`-Ausgaben.

Logs können unterschiedliche Stufen haben:

| Log-Level | Bedeutung                       |
| --------- | ------------------------------- |
| DEBUG     | sehr detaillierte Informationen |
| INFO      | normale Ereignisse              |
| WARNING   | Warnungen                       |
| ERROR     | Fehler                          |
| CRITICAL  | kritische Fehler                |

Beispiel:

```python
import logging

logging.basicConfig(level=logging.INFO)

logging.info("Programm gestartet")
logging.warning("Datei ist leer")
logging.error("Datenbank nicht erreichbar")
```

Logs helfen besonders im Betrieb, weil man später nachvollziehen kann, was passiert ist.

---

## Debugging mit Logs im Betrieb

Im Produktivbetrieb kann man nicht immer einfach den Code stoppen.

Deshalb sind Logs wichtig.

Typische Fragen bei Betriebsfehlern:

- Wann ist der Fehler aufgetreten?
- Welcher Benutzer war betroffen?
- Welche Aktion wurde ausgeführt?
- Welche Fehlermeldung steht im Log?
- Gibt es Verbindungsprobleme?
- Ist der Dienst gestartet?
- Ist Speicherplatz voll?
- Gibt es Rechteprobleme?
- Gab es kurz vorher ein Update?

Für FISI sind Logs eines der wichtigsten Werkzeuge bei der Fehleranalyse.

---

## Testumgebung

Eine Testumgebung ist eine Umgebung, in der Software ohne Gefahr für echte Benutzer geprüft wird.

Vorteile:

- keine echten produktiven Daten gefährdet
- Fehler haben weniger Auswirkungen
- neue Versionen können geprüft werden
- Tests sind kontrollierter
- Updates können vorher ausprobiert werden

Eine Testumgebung sollte möglichst ähnlich zur Produktivumgebung sein.

Wenn Test und Produktion komplett unterschiedlich sind, können Fehler unentdeckt bleiben.

---

## Entwicklungs-, Test- und Produktivumgebung

| Umgebung    | Zweck                              |
| ----------- | ---------------------------------- |
| Entwicklung | Code schreiben und ausprobieren    |
| Test        | Funktionen und Änderungen prüfen   |
| Produktion  | echte Nutzung mit echten Benutzern |

Diese Trennung ist wichtig.

Neue Funktionen sollten nicht direkt in Produktion getestet werden.

Besonders Datenbanken, Benutzerrechte, Schnittstellen und Konfigurationen müssen kontrolliert geprüft werden.

---

## Testen von Datenbanken

Bei Datenbanken müssen Datenstruktur, Abfragen und Regeln geprüft werden.

Wichtige Tests:

- Tabellen existieren
- Datentypen passen
- Pflichtfelder funktionieren
- Primärschlüssel sind eindeutig
- Fremdschlüssel funktionieren
- `SELECT` liefert korrekte Daten
- `INSERT` speichert gültige Daten
- ungültige Daten werden abgelehnt
- `UPDATE` ändert nur gewünschte Datensätze
- `DELETE` löscht nur gewünschte Datensätze
- Backups können wiederhergestellt werden

Gerade bei `UPDATE` und `DELETE` ist Vorsicht wichtig.

Vorher sollte oft mit `SELECT` geprüft werden, welche Datensätze betroffen sind.

---

## Testen von Schnittstellen

Schnittstellen verbinden Systeme.

Tests sollten prüfen:

- Verbindung funktioniert
- Authentifizierung funktioniert
- Datenformat stimmt
- Fehler werden korrekt behandelt
- Antwortzeiten sind akzeptabel
- ungültige Anfragen werden abgelehnt
- Logs werden geschrieben
- Berechtigungen werden eingehalten

Beispiele für Schnittstellen:

- API
- Datenbankverbindung
- Dateiimport
- E-Mail-Versand
- LDAP oder Active Directory
- Cloud-Dienst
- Monitoring-System

Schnittstellenfehler können mehrere Systeme betreffen und müssen deshalb sorgfältig getestet werden.

---

## Testen von Sicherheit

Sicherheitstests prüfen, ob Schutzmaßnahmen funktionieren.

Beispiele:

- Benutzer ohne Rechte kann keine Adminfunktion nutzen
- falsches Passwort wird abgelehnt
- MFA funktioniert
- direkte URL zu geschützter Seite wird blockiert
- Eingaben werden validiert
- SQL-Injection wird verhindert
- sensible Daten werden nicht in Logs geschrieben
- Session läuft nach Inaktivität ab
- Rollen und Rechte greifen korrekt

Sicherheit sollte nicht erst am Ende geprüft werden.

Sie muss bei Anforderungen, Entwicklung und Tests berücksichtigt werden.

---

## Testen von Fehlerfällen

Fehlerfälle sind besonders wichtig.

Beispiele:

- Datei fehlt
- Datenbank ist nicht erreichbar
- Netzwerk ist getrennt
- Benutzer hat keine Rechte
- Eingabe ist leer
- Eingabe ist zu lang
- Speicherplatz ist voll
- API antwortet nicht
- falsches Passwort
- ungültiges Dateiformat
- doppelter Datensatz

Gute Software reagiert kontrolliert auf Fehler.

Sie sollte nicht einfach abstürzen oder sensible Informationen anzeigen.

---

## Testen nach Änderungen

Nach einer Änderung sollte geprüft werden:

- funktioniert die neue Änderung?
- funktionieren alte Funktionen weiterhin?
- wurden neue Fehler erzeugt?
- muss Dokumentation angepasst werden?
- müssen Tests angepasst werden?
- sind Konfigurationen betroffen?
- sind Datenbankänderungen nötig?
- ist ein Rollback möglich?

Viele Fehler entstehen nicht beim ersten Schreiben von Software, sondern bei späteren Änderungen.

Deshalb sind Regressionstests wichtig.

---

## CI/CD und automatische Tests

In modernen Projekten werden Tests oft automatisch ausgeführt.

Beispiel:

1. Entwickler pusht Code zu GitHub.
2. GitHub Actions startet automatisch.
3. Tests werden ausgeführt.
4. Ergebnis wird angezeigt.
5. Bei Fehlern wird der Code nicht ausgeliefert.

Vorteile:

- Fehler werden früh gefunden
- Tests werden nicht vergessen
- Team arbeitet sicherer
- Qualität wird besser kontrolliert
- Deployment wird zuverlässiger

Für FISI ist das wichtig, weil CI/CD oft mit Infrastruktur, Containern und Deployment zusammenhängt.

---

## Debugging in Infrastruktur und Betrieb

Nicht jeder Fehler liegt im Code.

Viele Probleme entstehen durch Umgebung oder Betrieb.

Beispiele:

- Dienst läuft nicht
- Port ist blockiert
- Firewall-Regel fehlt
- DNS löst falsch auf
- Datenbank ist nicht erreichbar
- Zertifikat ist abgelaufen
- Speicherplatz ist voll
- falsche Umgebungsvariable
- falsche Datei-Rechte
- falsche Netzwerkverbindung
- Container startet nicht
- Volume fehlt

FISI muss deshalb nicht nur Code prüfen, sondern auch Systemumgebung, Logs, Netzwerk und Konfiguration.

---

## Typische Linux-Befehle bei Fehlersuche

Nützliche Befehle:

```bash
systemctl status dienstname
journalctl -u dienstname
journalctl -f
ss -tulpen
ip a
ip route
ping ziel
traceroute ziel
df -h
free -h
ps aux
top
```

Diese Befehle helfen bei Fragen wie:

- läuft der Dienst?
- gibt es Fehlermeldungen?
- ist der Port offen?
- hat das System eine IP-Adresse?
- ist das Gateway erreichbar?
- ist Speicherplatz voll?
- läuft der Prozess?

Für FISI sind solche Prüfungen sehr wichtig.

---

## Typische Docker-Befehle bei Fehlersuche

Bei Containern sind diese Befehle hilfreich:

```bash
docker ps
docker ps -a
docker logs containername
docker exec -it containername bash
docker inspect containername
docker stats
docker compose ps
docker compose logs
```

Damit kann man prüfen:

- läuft der Container?
- wurde er beendet?
- welche Logs gibt es?
- kann man in den Container hinein?
- welche Ports und Volumes sind gesetzt?
- wie hoch ist die Ressourcennutzung?

Docker-Fehler liegen oft an Ports, Volumes, Umgebungsvariablen, Images oder Netzwerken.

---

## Fehler eingrenzen

Fehleranalyse bedeutet oft, den Fehlerbereich zu verkleinern.

Man fragt:

- liegt es am Code?
- liegt es an der Eingabe?
- liegt es an der Datenbank?
- liegt es an der Datei?
- liegt es am Netzwerk?
- liegt es an Rechten?
- liegt es an der Konfiguration?
- liegt es an der Umgebung?
- liegt es an einer neuen Änderung?

Je genauer man den Fehler eingrenzt, desto schneller findet man die Ursache.

---

## Kleine Änderungen testen

Beim Debugging sollte man möglichst kleine Änderungen machen.

Schlecht:

- fünf Dinge gleichzeitig ändern
- danach testen
- nicht wissen, was geholfen hat

Besser:

- eine Vermutung aufstellen
- eine kleine Änderung durchführen
- testen
- Ergebnis bewerten
- nächste Vermutung prüfen

So bleibt die Fehlersuche nachvollziehbar.

---

## Versionierung beim Debugging

Git hilft bei der Fehlersuche.

Nützliche Fragen:

- Welche Datei wurde zuletzt geändert?
- Seit welchem Commit tritt der Fehler auf?
- Funktionierte es in einer alten Version?
- Welche Änderung könnte die Ursache sein?
- Kann man eine Änderung testweise rückgängig machen?

Nützliche Git-Befehle:

```bash
git status
git log
git diff
git show
```

Versionierung macht Fehleranalyse deutlich einfacher.

Ohne Git ist schwer nachvollziehbar, wann ein Fehler entstanden ist.

---

## Fehlerbehebung dokumentieren

Nach der Fehlerbehebung sollte dokumentiert werden:

- was war das Problem?
- was war die Ursache?
- welche Änderung wurde gemacht?
- wie wurde getestet?
- welche Version ist behoben?
- gibt es offene Risiken?
- muss Dokumentation angepasst werden?

Eine gute Commit-Nachricht kann ebenfalls helfen.

Beispiel:

```text
Fix ticket validation for empty title
```

Das ist besser als:

```text
fix
```

---

## Qualität durch Tests verbessern

Tests verbessern Softwarequalität.

Sie helfen bei:

- weniger Fehlern
- sichereren Änderungen
- besserer Wartbarkeit
- klareren Anforderungen
- schnellerer Fehlersuche
- besserer Dokumentation
- mehr Vertrauen in die Software

Tests ersetzen nicht gutes Design, aber sie unterstützen saubere Entwicklung.

Besonders bei Projekten, die wachsen, werden Tests immer wichtiger.

---

## Praxisbeispiele

### Beispiel 1: Python-Eingabefehler

Ein Python-Programm fragt nach einer Zahl. Wenn der Benutzer Text eingibt, stürzt das Programm ab. Durch einen Test mit ungültiger Eingabe wird der Fehler gefunden. Mit `try` und `except` wird eine verständliche Fehlermeldung eingebaut.

### Beispiel 2: Datenbankfehler

Eine Anwendung speichert neue Benutzer. Beim Test fällt auf, dass doppelte E-Mail-Adressen möglich sind. Die Lösung ist ein `UNIQUE`-Constraint in der Datenbank und eine passende Fehlermeldung in der Anwendung.

### Beispiel 3: Docker-Container startet nicht

Ein Container beendet sich direkt nach dem Start. Mit `docker ps -a` sieht man den beendeten Container. Mit `docker logs containername` wird die Fehlermeldung geprüft. Ursache ist eine fehlende Umgebungsvariable für die Datenbankverbindung.

---

## Typische Fehler

| Fehler                             | Problem                                 |
| ---------------------------------- | --------------------------------------- |
| nur den Normalfall testen          | Fehlerfälle bleiben unentdeckt          |
| keine Testdaten planen             | Tests sind unvollständig                |
| echte Daten in Tests verwenden     | Datenschutzrisiko                       |
| Fehlerbeschreibung zu ungenau      | Analyse dauert länger                   |
| Fehlermeldungen nicht lesen        | wichtige Hinweise werden ignoriert      |
| zu viele Dinge gleichzeitig ändern | Ursache bleibt unklar                   |
| Tests nach Änderungen vergessen    | alte Funktionen können kaputtgehen      |
| keine Logs prüfen                  | Betriebsfehler bleiben unklar           |
| keine Testumgebung nutzen          | Produktivsystem wird gefährdet          |
| keine Dokumentation der Lösung     | gleicher Fehler tritt später erneut auf |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Testen und Debugging sehr praxisnah.

Ein FISI muss häufig herausfinden, warum ein System oder eine Anwendung nicht funktioniert.

In der Praxis bedeutet das:

- Fehlermeldungen lesen
- Logs analysieren
- Dienste prüfen
- Netzwerkverbindungen testen
- Datenbankverbindungen prüfen
- Containerlogs auswerten
- Konfigurationen kontrollieren
- Rechteprobleme erkennen
- Tests durchführen
- Fehler dokumentieren
- Änderungen mit Git nachvollziehen
- Test- und Produktivumgebung unterscheiden
- nach Updates Smoke-Tests durchführen

Ein guter FISI sagt nicht nur „geht nicht“, sondern beschreibt sauber, was passiert, wann es passiert, welche Systeme betroffen sind und welche Hinweise aus Logs oder Tests erkennbar sind.

---

## Kurze Zusammenfassung

Testen bedeutet, Software systematisch zu prüfen.

Debuggen bedeutet, Fehler gezielt zu suchen, zu verstehen und zu beheben.

Wichtige Testarten sind manuelle Tests, automatische Tests, Unit-Tests, Integrationstests, Systemtests, Abnahmetests, Regressionstests und Smoke-Tests.

Wichtige Debugging-Werkzeuge sind Fehlermeldungen, Logs, `print()`-Ausgaben, Debugger, Breakpoints, Git, Systembefehle und Docker-Befehle.

Für FISI ist dieses Kapitel wichtig, weil Software im Betrieb zuverlässig funktionieren muss und Fehler oft aus Code, Konfiguration, Netzwerk, Datenbank, Rechten oder Umgebung entstehen können.
