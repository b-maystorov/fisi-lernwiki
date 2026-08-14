# 5.7 Einfache Anwendungen in Python implementieren

In diesem Kapitel geht es darum, einfache Anwendungen mit Python zu verstehen und umzusetzen.

Python eignet sich gut für den Einstieg in die Programmierung, weil die Sprache gut lesbar ist und viele typische Aufgaben einfach umgesetzt werden können. Für Fachinformatiker für Systemintegration ist Python besonders nützlich, weil man damit kleine Tools, Automatisierungen, Datenverarbeitungen und Skripte schreiben kann.

---

## Kurz erklärt

Eine Python-Anwendung besteht aus Anweisungen, die Schritt für Schritt ausgeführt werden.

Typische Bestandteile sind:

- Variablen
- Datentypen
- Eingaben
- Ausgaben
- Bedingungen
- Schleifen
- Funktionen
- Listen
- Dictionaries
- Dateien
- Fehlerbehandlung
- Module
- einfache Programmstruktur

Mit diesen Grundlagen kann man bereits kleine Programme schreiben, zum Beispiel Rechner, Textauswertungen, Logprüfungen, Inventarlisten oder kleine Konsolenanwendungen.

---

## Warum Python wichtig ist

Python wird in vielen IT-Bereichen eingesetzt.

Beispiele:

- Automatisierung
- Systemadministration
- Datenverarbeitung
- Logfile-Auswertung
- kleine interne Tools
- Webentwicklung
- Tests
- API-Nutzung
- Datei- und Ordnerverwaltung
- Datenbankzugriffe
- Skripte für wiederkehrende Aufgaben

Für FISI ist Python besonders interessant, weil viele Aufgaben im IT-Betrieb wiederholbar sind.

Wenn man solche Aufgaben automatisiert, spart man Zeit und reduziert Fehler.

---

## Python als interpretierte Sprache

Python wird meistens interpretiert.

Das bedeutet: Der Python-Code wird nicht vorher wie bei manchen anderen Sprachen komplett in eine ausführbare Datei kompiliert, sondern vom Python-Interpreter ausgeführt.

Beispiel:

```bash
python3 main.py
```

Der Interpreter liest die Datei und führt die Anweisungen aus.

Damit ein Python-Programm funktioniert, muss Python auf dem System installiert sein.

---

## Python-Dateien

Python-Dateien haben meistens die Endung `.py`.

Beispiele:

```text
main.py
script.py
inventory.py
log_checker.py
```

Eine Datei `main.py` wird oft als Startpunkt eines kleinen Programms verwendet.

Beispiel:

```python
print("Hallo Welt")
```

Ausführen:

```bash
python3 main.py
```

Ausgabe:

```text
Hallo Welt
```

---

## Kommentare

Kommentare erklären Code für Menschen.

Python ignoriert Kommentare bei der Ausführung.

Beispiel:

```python
# Das ist ein Kommentar
print("Programm startet")
```

Kommentare sind sinnvoll, wenn sie erklären, warum etwas gemacht wird.

Zu viele Kommentare für offensichtliche Dinge können den Code unübersichtlich machen.

---

## Variablen

Eine Variable speichert einen Wert.

Beispiel:

```python
name = "Bilgin"
age = 25

print(name)
print(age)
```

Variablen helfen, Werte wiederzuverwenden.

Der Name einer Variable sollte verständlich sein.

Gut:

```python
username = "admin"
ticket_count = 5
```

Schlecht:

```python
x = "admin"
a = 5
```

Kurze Namen sind manchmal okay, aber in normalen Programmen sind klare Namen besser.

---

## Datentypen

Ein Datentyp beschreibt, welche Art von Wert gespeichert wird.

Wichtige Datentypen in Python:

| Datentyp | Bedeutung               | Beispiel            |
| -------- | ----------------------- | ------------------- |
| `str`    | Text                    | `"Hallo"`           |
| `int`    | ganze Zahl              | `42`                |
| `float`  | Kommazahl               | `3.14`              |
| `bool`   | Wahrheitswert           | `True` oder `False` |
| `list`   | Liste von Werten        | `[1, 2, 3]`         |
| `dict`   | Schlüssel-Wert-Struktur | `{"name": "Ali"}`   |

Python erkennt Datentypen oft automatisch.

Beispiel:

```python
name = "Ali"
age = 30
active = True
```

---

## Ausgabe mit print

Mit `print()` kann ein Programm etwas im Terminal ausgeben.

Beispiel:

```python
name = "Ali"

print("Hallo")
print(name)
```

Ausgabe:

```text
Hallo
Ali
```

Man kann Werte auch zusammen ausgeben.

```python
name = "Ali"
age = 30

print("Name:", name)
print("Alter:", age)
```

---

## Eingabe mit input

Mit `input()` kann der Benutzer etwas eingeben.

Beispiel:

```python
name = input("Wie heißt du? ")

print("Hallo", name)
```

Wichtig:

`input()` liefert immer Text zurück.

Wenn man eine Zahl braucht, muss man den Wert umwandeln.

Beispiel:

```python
age_text = input("Wie alt bist du? ")
age = int(age_text)

print(age)
```

Wenn der Benutzer keine gültige Zahl eingibt, entsteht ein Fehler. Deshalb ist Fehlerbehandlung später wichtig.

---

## Bedingungen

Bedingungen steuern, welche Teile eines Programms ausgeführt werden.

Beispiel:

```python
age = 18

if age >= 18:
    print("Volljährig")
else:
    print("Nicht volljährig")
```

Python nutzt Einrückungen, um Blöcke zu erkennen.

Falsche Einrückung kann zu Fehlern führen oder die Logik verändern.

---

## Vergleichsoperatoren

Vergleichsoperatoren prüfen Werte.

| Operator | Bedeutung           |
| -------- | ------------------- |
| `==`     | ist gleich          |
| `!=`     | ist ungleich        |
| `>`      | größer als          |
| `<`      | kleiner als         |
| `>=`     | größer oder gleich  |
| `<=`     | kleiner oder gleich |

Beispiel:

```python
password = "secret"

if password == "secret":
    print("Zugriff erlaubt")
else:
    print("Zugriff verweigert")
```

Wichtig:

`=` weist einen Wert zu.
`==` vergleicht zwei Werte.

---

## Logische Operatoren

Mit logischen Operatoren können Bedingungen kombiniert werden.

| Operator | Bedeutung                                |
| -------- | ---------------------------------------- |
| `and`    | beide Bedingungen müssen wahr sein       |
| `or`     | mindestens eine Bedingung muss wahr sein |
| `not`    | kehrt einen Wahrheitswert um             |

Beispiel:

```python
username = "admin"
password = "secret"

if username == "admin" and password == "secret":
    print("Login erfolgreich")
else:
    print("Login fehlgeschlagen")
```

Diese Operatoren sind wichtig für Entscheidungen im Programm.

---

## Schleifen

Schleifen wiederholen Code.

Python hat zwei wichtige Schleifenarten:

- `for`
- `while`

Eine `for`-Schleife wird oft genutzt, wenn man über eine Liste geht.

Beispiel:

```python
names = ["Ali", "Maria", "Sam"]

for name in names:
    print(name)
```

Ausgabe:

```text
Ali
Maria
Sam
```

---

## while-Schleife

Eine `while`-Schleife läuft, solange eine Bedingung wahr ist.

Beispiel:

```python
counter = 1

while counter <= 3:
    print(counter)
    counter = counter + 1
```

Ausgabe:

```text
1
2
3
```

Wichtig:

Bei `while`-Schleifen muss man darauf achten, dass die Bedingung irgendwann falsch wird.

Sonst entsteht eine Endlosschleife.

---

## Listen

Eine Liste speichert mehrere Werte.

Beispiel:

```python
devices = ["Laptop", "Monitor", "Drucker"]

print(devices)
print(devices[0])
```

Ausgabe:

```text
['Laptop', 'Monitor', 'Drucker']
Laptop
```

Listen beginnen bei Index `0`.

Das erste Element hat also den Index `0`, nicht `1`.

---

## Mit Listen arbeiten

Wichtige Listenoperationen:

```python
devices = ["Laptop", "Monitor"]

devices.append("Drucker")
devices.remove("Monitor")

print(devices)
```

Ausgabe:

```text
['Laptop', 'Drucker']
```

Listen sind praktisch, wenn mehrere Werte gesammelt, durchsucht oder verarbeitet werden sollen.

Beispiele:

- Geräteliste
- Benutzernamen
- Fehlermeldungen
- Dateinamen
- offene Tickets

---

## Dictionaries

Ein Dictionary speichert Daten als Schlüssel-Wert-Paare.

Beispiel:

```python
user = {
    "name": "Ali",
    "role": "admin",
    "active": True
}

print(user["name"])
print(user["role"])
```

Ausgabe:

```text
Ali
admin
```

Dictionaries sind nützlich, wenn Daten Eigenschaften haben.

Beispiel:

Ein Benutzer hat Name, Rolle und Status.
Ein Gerät hat Hostname, IP-Adresse und Standort.

---

## Beispiel Dictionary für ein Gerät

```python
device = {
    "hostname": "pc-001",
    "ip": "192.168.10.25",
    "location": "Office 1",
    "active": True
}

print(device["hostname"])
print(device["ip"])
```

Dictionaries sind sehr wichtig in Python, weil viele strukturierte Daten so dargestellt werden können.

Auch JSON-Daten ähneln oft Python-Dictionaries.

---

## Funktionen

Eine Funktion ist ein wiederverwendbarer Codeblock.

Beispiel:

```python
def greet_user(name):
    print("Hallo", name)

greet_user("Ali")
greet_user("Maria")
```

Funktionen helfen, Code zu strukturieren.

Vorteile:

- weniger Wiederholung
- bessere Übersicht
- Funktionen können getestet werden
- Code wird wiederverwendbar
- Programme werden leichter wartbar

---

## return

Eine Funktion kann mit `return` einen Wert zurückgeben.

Beispiel:

```python
def add_numbers(a, b):
    return a + b

result = add_numbers(5, 3)

print(result)
```

Ausgabe:

```text
8
```

`print()` zeigt etwas an.
`return` gibt einen Wert an den aufrufenden Code zurück.

Das ist ein wichtiger Unterschied.

---

## Module

Ein Modul ist eine Python-Datei, die Code enthält.

Man kann Code aus einer Datei in einer anderen Datei verwenden.

Beispiel:

Datei `calculator.py`:

```python
def add(a, b):
    return a + b
```

Datei `main.py`:

```python
from calculator import add

result = add(5, 3)
print(result)
```

Module helfen, größere Programme in mehrere Dateien aufzuteilen.

---

## Standardbibliothek

Python bringt viele fertige Module mit.

Beispiele:

| Modul        | Zweck                             |
| ------------ | --------------------------------- |
| `os`         | Betriebssystemfunktionen          |
| `pathlib`    | Arbeiten mit Dateipfaden          |
| `datetime`   | Datum und Uhrzeit                 |
| `random`     | Zufallszahlen                     |
| `csv`        | CSV-Dateien lesen und schreiben   |
| `json`       | JSON-Daten verarbeiten            |
| `sys`        | Informationen zum Python-Programm |
| `subprocess` | externe Befehle starten           |

Die Standardbibliothek ist sehr nützlich, weil man nicht alles selbst programmieren muss.

---

## Dateien lesen

Python kann Dateien lesen.

Beispiel:

```python
with open("example.txt", "r", encoding="utf-8") as file:
    content = file.read()

print(content)
```

`with open(...)` sorgt dafür, dass die Datei nach der Nutzung wieder sauber geschlossen wird.

Dateien lesen ist wichtig für viele FISI-Aufgaben, zum Beispiel Logdateien, CSV-Dateien oder Konfigurationsdateien.

---

## Dateien zeilenweise lesen

Bei großen Dateien liest man oft zeilenweise.

Beispiel:

```python
with open("server.log", "r", encoding="utf-8") as file:
    for line in file:
        if "ERROR" in line:
            print(line)
```

Dieses Beispiel durchsucht eine Logdatei nach dem Wort `ERROR`.

Das ist ein typisches Beispiel für praktische Automatisierung.

---

## Dateien schreiben

Python kann auch Dateien schreiben.

Beispiel:

```python
with open("result.txt", "w", encoding="utf-8") as file:
    file.write("Analyse abgeschlossen\n")
```

Der Modus `"w"` überschreibt die Datei.

Der Modus `"a"` hängt neue Inhalte an die Datei an.

Beispiel:

```python
with open("result.txt", "a", encoding="utf-8") as file:
    file.write("Neuer Eintrag\n")
```

---

## CSV-Dateien verarbeiten

CSV-Dateien enthalten tabellarische Daten.

Beispiel:

```python
import csv

with open("users.csv", "r", encoding="utf-8") as file:
    reader = csv.DictReader(file)

    for row in reader:
        print(row["name"], row["email"])
```

CSV-Dateien werden häufig für Import, Export und einfache Datenverarbeitung genutzt.

Für FISI kann das nützlich sein, zum Beispiel bei Benutzerlisten, Inventardaten oder Auswertungen.

---

## Fehlerbehandlung

Fehler können während der Programmausführung entstehen.

Beispiele:

- Datei existiert nicht
- Benutzer gibt falschen Wert ein
- Netzwerk ist nicht erreichbar
- Datenbank antwortet nicht
- Zahl kann nicht umgewandelt werden
- Rechte fehlen

Mit `try` und `except` kann man Fehler abfangen.

Beispiel:

```python
try:
    age = int(input("Alter: "))
    print(age)
except ValueError:
    print("Bitte eine gültige Zahl eingeben.")
```

Fehlerbehandlung macht Programme stabiler und benutzerfreundlicher.

---

## Häufige Fehlertypen

| Fehler              | Bedeutung                                  |
| ------------------- | ------------------------------------------ |
| `SyntaxError`       | Code ist formal falsch geschrieben         |
| `NameError`         | Name oder Variable existiert nicht         |
| `TypeError`         | falscher Datentyp wird verwendet           |
| `ValueError`        | Wert passt nicht zur erwarteten Umwandlung |
| `FileNotFoundError` | Datei wurde nicht gefunden                 |
| `KeyError`          | Schlüssel in Dictionary existiert nicht    |
| `IndexError`        | Listenindex existiert nicht                |

Fehlermeldungen sind nicht nur Probleme, sondern Hinweise.

Sie zeigen oft ziemlich genau, wo und warum etwas nicht funktioniert.

---

## Eingabe, Verarbeitung, Ausgabe

Viele einfache Programme folgen dem EVA-Prinzip.

| Teil         | Bedeutung                                |
| ------------ | ---------------------------------------- |
| Eingabe      | Daten kommen in das Programm             |
| Verarbeitung | Daten werden geprüft oder verändert      |
| Ausgabe      | Ergebnis wird angezeigt oder gespeichert |

Beispiel:

```python
number_text = input("Zahl eingeben: ")
number = int(number_text)

double = number * 2

print("Ergebnis:", double)
```

Hier ist:

- Eingabe: Benutzer gibt Zahl ein
- Verarbeitung: Zahl wird verdoppelt
- Ausgabe: Ergebnis wird angezeigt

Dieses Prinzip hilft beim Planen kleiner Programme.

---

## Einfache Programmstruktur

Ein kleines Python-Programm sollte übersichtlich aufgebaut sein.

Beispiel:

```python
def get_username():
    return input("Benutzername: ")

def greet_user(name):
    print("Hallo", name)

def main():
    username = get_username()
    greet_user(username)

main()
```

Der Vorteil:

- Eingabe ist getrennt
- Verarbeitung ist getrennt
- Hauptablauf ist klar
- Funktionen können später erweitert werden

---

## main-Funktion

In Python wird häufig eine `main()`-Funktion genutzt.

Beispiel:

```python
def main():
    print("Programm startet")

if __name__ == "__main__":
    main()
```

Diese Struktur sorgt dafür, dass `main()` nur ausgeführt wird, wenn die Datei direkt gestartet wird.

Das ist besonders nützlich, wenn Dateien auch als Module importiert werden.

Für Anfänger wirkt diese Zeile zuerst komisch, aber sie ist eine professionelle und häufige Struktur.

---

## Virtuelle Umgebung

Eine virtuelle Umgebung trennt Python-Abhängigkeiten pro Projekt.

Erstellen:

```bash
python3 -m venv venv
```

Aktivieren unter Linux:

```bash
source venv/bin/activate
```

Danach können Pakete installiert werden:

```bash
pip install paketname
```

Die virtuelle Umgebung sollte nicht ins Git-Repository.

Deshalb steht meistens in `.gitignore`:

```text
venv/
```

---

## Pakete installieren

Python kann externe Pakete nutzen.

Pakete werden häufig mit `pip` installiert.

Beispiel:

```bash
pip install requests
```

Pakete sollten dokumentiert werden.

Eine häufige Datei dafür ist:

```text
requirements.txt
```

Darin stehen die benötigten Pakete.

Beispiel:

```text
requests
pytest
```

Andere Personen können die Pakete dann installieren:

```bash
pip install -r requirements.txt
```

---

## Debugging in Python

Debugging bedeutet Fehlersuche.

Einfache Methoden:

- Fehlermeldung genau lesen
- `print()` zur Kontrolle nutzen
- Variablenwerte anzeigen
- Code Schritt für Schritt testen
- kleine Funktionen schreiben
- nur eine Änderung auf einmal machen
- Eingabedaten prüfen

Beispiel:

```python
number = 5
print("DEBUG number:", number)
```

Für größere Projekte kann ein Debugger in VS Code genutzt werden.

---

## Tests

Tests prüfen, ob Code funktioniert.

Ein einfacher Test kann so aussehen:

```python
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
```

Tests helfen, Fehler schneller zu finden.

Wenn später Code geändert wird, kann geprüft werden, ob alte Funktionen weiterhin funktionieren.

---

## Kleine Konsolenanwendung

Eine Konsolenanwendung läuft im Terminal.

Beispiel:

```python
def main():
    name = input("Name: ")
    print("Hallo", name)

main()
```

Konsolenanwendungen sind gut für den Einstieg, weil keine grafische Oberfläche nötig ist.

Viele Admin-Tools sind ebenfalls Konsolenprogramme.

---

## Beispiel: kleiner Rechner

```python
def add(a, b):
    return a + b

def main():
    first = int(input("Erste Zahl: "))
    second = int(input("Zweite Zahl: "))

    result = add(first, second)

    print("Ergebnis:", result)

main()
```

Dieses Beispiel zeigt:

- Eingabe
- Umwandlung von Text zu Zahl
- Funktion
- Rückgabewert
- Ausgabe

---

## Beispiel: einfache Inventarliste

```python
devices = []

def add_device(hostname):
    devices.append(hostname)

def show_devices():
    for device in devices:
        print(device)

def main():
    add_device("pc-001")
    add_device("pc-002")
    show_devices()

main()
```

Dieses Beispiel zeigt, wie Listen und Funktionen zusammen genutzt werden können.

Für eine echte Anwendung müsste man später Speicherung, Eingabeprüfung und Fehlerbehandlung ergänzen.

---

## Beispiel: Logdatei prüfen

```python
def show_errors(filename):
    with open(filename, "r", encoding="utf-8") as file:
        for line in file:
            if "ERROR" in line:
                print(line.strip())

def main():
    show_errors("server.log")

main()
```

Dieses Beispiel ist besonders praxisnah für FISI.

Logs auszuwerten ist eine typische Aufgabe im IT-Betrieb.

---

## Objektorientierung kurz erklärt

Python unterstützt objektorientierte Programmierung.

Dabei werden Daten und Funktionen in Klassen zusammengefasst.

Beispiel:

```python
class Device:
    def __init__(self, hostname, ip):
        self.hostname = hostname
        self.ip = ip

    def show_info(self):
        print(self.hostname, self.ip)

device = Device("pc-001", "192.168.10.25")
device.show_info()
```

Eine Klasse beschreibt eine Art Bauplan.

Ein Objekt ist eine konkrete Instanz davon.

Objektorientierung ist nützlich, wenn Daten und Verhalten zusammengehören.

---

## Code lesbar schreiben

Lesbarer Code ist wichtig.

Gute Regeln:

- klare Namen nutzen
- Funktionen klein halten
- nicht alles in eine Datei schreiben
- Wiederholungen vermeiden
- Einrückung sauber halten
- Kommentare sinnvoll einsetzen
- Fehlerfälle beachten
- Code regelmäßig testen

Code wird nicht nur für den Computer geschrieben.

Code wird auch für Menschen geschrieben, die ihn später verstehen müssen.

---

## Sicherheit bei Python-Anwendungen

Auch kleine Python-Programme können Sicherheitsprobleme verursachen.

Wichtige Punkte:

- keine Passwörter direkt im Code speichern
- Eingaben prüfen
- Fehlermeldungen nicht zu viele interne Details zeigen
- Dateien nicht unkontrolliert überschreiben
- Pfade sorgfältig behandeln
- keine echten personenbezogenen Daten in Testprojekten nutzen
- externe Pakete bewusst auswählen
- sensible Daten nicht in Logs schreiben

Gerade bei öffentlichen GitHub-Projekten ist wichtig, keine privaten Daten zu veröffentlichen.

---

## Dokumentation

Auch kleine Python-Projekte brauchen Dokumentation.

Wichtige Inhalte einer README:

- Was macht das Programm?
- Welche Voraussetzungen gibt es?
- Wie wird es gestartet?
- Welche Dateien sind wichtig?
- Welche Eingaben erwartet das Programm?
- Welche Ausgabe entsteht?
- Gibt es Beispiele?
- Welche Grenzen hat die aktuelle Version?

Dokumentation macht ein Projekt verständlicher und professioneller.

---

## Typische Projektstruktur

Eine einfache Python-Projektstruktur kann so aussehen:

```text
python-project/
├── README.md
├── main.py
├── requirements.txt
├── .gitignore
├── src/
│   └── helper.py
├── tests/
│   └── test_helper.py
└── data/
    └── example.csv
```

Nicht jedes kleine Projekt braucht sofort alle Ordner.

Wichtig ist, dass die Struktur verständlich und erweiterbar bleibt.

---

## Typische Fehler

| Fehler                                | Problem                                  |
| ------------------------------------- | ---------------------------------------- |
| alles in eine riesige Datei schreiben | Code wird unübersichtlich                |
| Variablen schlecht benennen           | Code ist schwer verständlich             |
| Eingaben nicht prüfen                 | Programm stürzt leichter ab              |
| Fehlerbehandlung vergessen            | Benutzer bekommt unklare Fehlermeldungen |
| `print()` und `return` verwechseln    | Funktionen sind schwer wiederverwendbar  |
| virtuelle Umgebung nicht nutzen       | Paketkonflikte entstehen                 |
| Passwörter im Code speichern          | Sicherheitsrisiko                        |
| keine README schreiben                | Projekt ist schwer nachvollziehbar       |
| keine Tests machen                    | Fehler bleiben länger unbemerkt          |
| echte Daten in GitHub hochladen       | Datenschutz- und Sicherheitsproblem      |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Python besonders nützlich, weil viele Aufgaben im IT-Betrieb automatisiert werden können.

In der Praxis bedeutet das:

- Logdateien auswerten
- CSV-Dateien verarbeiten
- einfache Reports erzeugen
- Benutzerlisten prüfen
- Dateien und Ordner analysieren
- Systeminformationen sammeln
- kleine Tools schreiben
- API-Daten abrufen
- Konfigurationen prüfen
- wiederkehrende Aufgaben automatisieren
- Fehler schneller analysieren

Ein guter FISI muss nicht sofort große Software entwickeln, sollte aber einfache Programme verstehen und kleine Skripte sauber schreiben können.

---

## Kurze Zusammenfassung

Python ist eine gut lesbare Programmiersprache, die sich besonders für Automatisierung, Datenverarbeitung, kleine Tools und Lernprojekte eignet.

Wichtige Grundlagen sind Variablen, Datentypen, Eingabe, Ausgabe, Bedingungen, Schleifen, Listen, Dictionaries, Funktionen, Module, Dateien, Fehlerbehandlung, Tests und einfache Programmstruktur.

Für FISI ist Python wichtig, weil viele praktische Aufgaben im IT-Betrieb mit kleinen Skripten schneller, sicherer und nachvollziehbarer gelöst werden können.
