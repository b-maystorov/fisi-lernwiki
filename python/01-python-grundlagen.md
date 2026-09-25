# 1. Python Grundlagen

In diesem Kapitel geht es um die Grundlagen von Python.

Python ist eine Programmiersprache, die häufig für Skripte, Automatisierung, kleine Tools, Datenverarbeitung, Tests und einfache technische Aufgaben genutzt wird.

Für Fachinformatiker für Systemintegration ist Python besonders interessant, weil man damit wiederkehrende Aufgaben automatisieren, Dateien auswerten, Logs prüfen und kleine Hilfsprogramme für die tägliche IT-Arbeit schreiben kann.

---

## Kurz erklärt

Python ist eine Programmiersprache.

Mit Python kann man dem Computer Schritt für Schritt Anweisungen geben.

Beispiel:

```python
print("Hallo Welt")
```

Dieses Programm gibt folgenden Text aus:

```text
Hallo Welt
```

Python-Code wird meistens in Dateien mit der Endung `.py` gespeichert.

Beispiel:

```text
script.py
log_check.py
backup_report.py
server_list.py
```

---

## Warum Python genutzt wird

Python ist beliebt, weil die Sprache relativ gut lesbar ist.

Ein einfaches Python-Programm sieht oft klarer aus als Code in vielen anderen Programmiersprachen.

Beispiel:

```python
name = "Bilgin"
print("Hallo", name)
```

Auch ohne viel Erfahrung kann man oft ungefähr erkennen, was passiert.

Python wird genutzt für:

```text
Skripting
Automatisierung
Dateiverarbeitung
Loganalyse
Webentwicklung
Datenanalyse
APIs
Tests
kleine Tools
DevOps-Grundlagen
```

Für FISI ist vor allem der praktische Einsatz interessant.

---

## Python in der FISI-Praxis

Ein FISI muss nicht wie ein Softwareentwickler große Anwendungen bauen.

Aber Python kann helfen, technische Aufgaben besser zu verstehen und zu vereinfachen.

Beispiele:

```text
Logdateien durchsuchen
Dateien automatisch sortieren
JSON-Dateien lesen
Serverlisten verarbeiten
einfache Reports erstellen
Systeminformationen sammeln
kleine Prüfskripte schreiben
wiederkehrende Aufgaben automatisieren
```

Python ist also ein Werkzeug für praktische IT-Aufgaben.

---

## Python-Dateien

Python-Dateien haben meistens die Endung:

```text
.py
```

Beispiele:

```text
main.py
check_logs.py
read_json.py
server_report.py
```

Eine Python-Datei enthält Python-Code.

Beispiel:

```python
print("Python läuft")
```

Wenn die Datei ausgeführt wird, verarbeitet Python den Code von oben nach unten.

---

## Python ausführen

Unter Linux kann man Python im Terminal ausführen.

Version prüfen:

```bash
python3 --version
```

Eine Python-Datei ausführen:

```bash
python3 main.py
```

Beispiel:

```bash
python3 script.py
```

Wenn die Datei gültigen Python-Code enthält, wird das Programm gestartet.

---

## Python im Terminal

Man kann Python auch direkt im Terminal starten.

```bash
python3
```

Dann öffnet sich die interaktive Python-Umgebung.

Dort kann man einzelne Befehle testen.

Beispiel:

```python
2 + 3
```

Ausgabe:

```text
5
```

Diese interaktive Umgebung ist praktisch, um kleine Dinge schnell auszuprobieren.

Beenden kann man sie mit:

```python
exit()
```

oder mit:

```text
Strg + D
```

---

## print()

Die Funktion `print()` gibt etwas auf dem Bildschirm aus.

Beispiel:

```python
print("Hallo")
```

Ausgabe:

```text
Hallo
```

Man kann auch mehrere Werte ausgeben:

```python
name = "Bilgin"
print("Hallo", name)
```

Ausgabe:

```text
Hallo Bilgin
```

`print()` ist besonders am Anfang sehr wichtig, weil man damit prüfen kann, was im Programm passiert.

---

## Kommentare

Kommentare sind Notizen im Code.

Python ignoriert Kommentare beim Ausführen.

Ein Kommentar beginnt mit:

```python
#
```

Beispiel:

```python
# Das ist ein Kommentar
print("Hallo")
```

Kommentare helfen dabei, Code verständlicher zu machen.

Gute Kommentare erklären nicht jeden einzelnen Befehl, sondern den Zweck.

Schlecht:

```python
# print gibt Text aus
print("Hallo")
```

Besser:

```python
# Kurzer Test, ob das Skript startet
print("Hallo")
```

---

## Code wird von oben nach unten ausgeführt

Python führt Code normalerweise Zeile für Zeile von oben nach unten aus.

Beispiel:

```python
print("Start")
print("Verarbeitung")
print("Ende")
```

Ausgabe:

```text
Start
Verarbeitung
Ende
```

Die Reihenfolge ist wichtig.

Wenn ein Wert später gebraucht wird, muss er vorher erstellt werden.

---

## Einrückung

Python nutzt Einrückung, um Codeblöcke zu erkennen.

Das ist sehr wichtig.

Beispiel:

```python
if True:
    print("Das gehört zum if-Block")
```

Die eingerückte Zeile gehört zur Bedingung.

Falsch wäre:

```python
if True:
print("Das ist falsch eingerückt")
```

Dann gibt Python einen Fehler aus.

Einrückung gehört zu den wichtigsten Grundlagen in Python.

---

## Variablen

Eine Variable speichert einen Wert.

Beispiel:

```python
name = "Bilgin"
alter = 25
```

Danach kann man die Werte benutzen:

```python
print(name)
print(alter)
```

Ausgabe:

```text
Bilgin
25
```

Variablen helfen, Informationen im Programm zu speichern und wiederzuverwenden.

---

## Einfache Datentypen

Python kennt verschiedene Datentypen.

| Datentyp | Bedeutung | Beispiel |
|---|---|---|
| `str` | Text | `"Hallo"` |
| `int` | ganze Zahl | `25` |
| `float` | Kommazahl | `3.14` |
| `bool` | Wahrheitswert | `True` oder `False` |
| `list` | Liste von Werten | `["server1", "server2"]` |
| `dict` | Schlüssel-Wert-Struktur | `{"name": "server1"}` |

Diese Datentypen werden später genauer behandelt.

---

## Strings

Ein String ist Text.

Beispiel:

```python
hostname = "server01"
print(hostname)
```

Ausgabe:

```text
server01
```

Strings stehen in Anführungszeichen.

Möglich sind:

```python
"Text"
'Text'
```

Beides funktioniert.

Wichtig ist nur, dass Anfang und Ende zusammenpassen.

---

## Zahlen

Python kann mit Zahlen rechnen.

Beispiel:

```python
a = 5
b = 3

print(a + b)
print(a - b)
print(a * b)
print(a / b)
```

Ausgabe:

```text
8
2
15
1.6666666666666667
```

Zahlen sind wichtig für Berechnungen, Zähler, Größen, Ports oder einfache Prüfungen.

---

## Boolean

Ein Boolean ist ein Wahrheitswert.

Es gibt nur zwei Werte:

```python
True
False
```

Beispiel:

```python
ssh_aktiv = True
backup_erfolgreich = False
```

Booleans werden häufig für Bedingungen genutzt.

Beispiel:

```python
if ssh_aktiv:
    print("SSH ist aktiv")
```

---

## Listen

Eine Liste speichert mehrere Werte.

Beispiel:

```python
server = ["web01", "db01", "backup01"]

print(server)
```

Ausgabe:

```text
['web01', 'db01', 'backup01']
```

Ein einzelnes Element ausgeben:

```python
print(server[0])
```

Ausgabe:

```text
web01
```

Wichtig:

```text
Python zählt bei Listen ab 0.
```

Das erste Element hat also die Nummer `0`.

---

## Dictionaries

Ein Dictionary speichert Werte mit Schlüsseln.

Beispiel:

```python
server = {
    "name": "web01",
    "ip": "192.168.10.20",
    "rolle": "Webserver"
}

print(server["name"])
print(server["ip"])
```

Ausgabe:

```text
web01
192.168.10.20
```

Dictionaries sind sehr nützlich für strukturierte Daten.

Sie passen gut zu JSON und Konfigurationsdaten.

---

## input()

Mit `input()` kann man Benutzereingaben einlesen.

Beispiel:

```python
name = input("Wie heißt du? ")
print("Hallo", name)
```

Ablauf:

```text
Programm fragt nach Name.
Benutzer gibt Text ein.
Programm gibt Begrüßung aus.
```

Wichtig:

```text
input() liefert immer Text zurück.
```

Wenn man eine Zahl braucht, muss man umwandeln.

Beispiel:

```python
alter = int(input("Wie alt bist du? "))
print(alter)
```

---

## Fehler und Fehlermeldungen

Fehler gehören zum Programmieren dazu.

Python zeigt meistens eine Fehlermeldung.

Beispiel:

```python
print(name)
```

Wenn `name` vorher nicht definiert wurde, kommt ein Fehler.

Typischer Fehler:

```text
NameError
```

Das bedeutet:

```text
Python kennt diesen Namen nicht.
```

Fehlermeldungen sind wichtig. Man sollte sie nicht ignorieren, sondern lesen.

---

## Häufige Anfängerfehler

| Fehler | Erklärung |
|---|---|
| falsche Einrückung | Python erkennt Codeblock nicht |
| Anführungszeichen vergessen | String ist nicht korrekt |
| Variable falsch geschrieben | Python findet den Namen nicht |
| Klammer vergessen | Syntaxfehler |
| Zahl und Text falsch kombiniert | Datentypen passen nicht |
| Datei falsch gestartet | falscher Dateiname oder Pfad |
| Python 2 statt Python 3 genutzt | Befehle verhalten sich anders |

Viele Fehler sind am Anfang normal.

Wichtig ist, sie ruhig zu lesen und Schritt für Schritt zu beheben.

---

## Python und Terminal

Python wird oft zusammen mit dem Terminal genutzt.

Typischer Ablauf:

```text
Datei in VS Code schreiben
Terminal öffnen
Skript mit python3 ausführen
Ausgabe prüfen
Fehler lesen
Code anpassen
erneut ausführen
```

Beispiel:

```bash
python3 main.py
```

Das ist ähnlich wie bei anderen IT-Aufgaben:

```text
ändern
testen
prüfen
dokumentieren
```

---

## Python und Dateien

Python kann Dateien lesen und schreiben.

Das ist für FISI sehr nützlich.

Beispiele:

```text
Logdatei lesen
Serverliste verarbeiten
Konfigurationsdatei prüfen
Report schreiben
Textdatei automatisch erzeugen
```

Ein einfaches Beispiel wird später genauer behandelt:

```python
with open("server.txt", "r") as file:
    content = file.read()

print(content)
```

Hier wird eine Datei gelesen und ausgegeben.

---

## Python und JSON

JSON ist ein wichtiges Datenformat in der IT.

Viele Tools und APIs nutzen JSON.

Beispiel:

```json
{
  "hostname": "server01",
  "ip": "192.168.10.20",
  "rolle": "webserver"
}
```

Python kann JSON-Daten lesen und verarbeiten.

Das ist nützlich für:

```text
APIs
Docker
Konfigurationsdateien
Monitoring
Automatisierung
Cloud-Dienste
```

---

## Python und Automatisierung

Automatisierung bedeutet:

```text
wiederkehrende Aufgaben durch Skripte erledigen lassen
```

Beispiele:

```text
Dateien automatisch prüfen
Logs durchsuchen
Reports erstellen
Serverlisten auswerten
Ordnerstrukturen erzeugen
Konfigurationsdateien vorbereiten
```

Python eignet sich gut, wenn eine Aufgabe mehr Logik braucht als ein einfacher Terminal-Befehl.

---

## Gute Arbeitsweise beim Lernen

Eine gute Arbeitsweise mit Python:

```text
klein anfangen
Code selbst schreiben
nicht nur kopieren
Fehlermeldungen lesen
print() zum Prüfen nutzen
eine Änderung nach der anderen machen
Dateien sauber benennen
Code regelmäßig speichern
kleine Projekte dokumentieren
```

Am Anfang ist es wichtiger, die Logik zu verstehen, als perfekten Code zu schreiben.

---

## Beispiel 1: Erstes Python-Skript

Datei:

```text
main.py
```

Inhalt:

```python
print("Hallo Welt")
print("Python läuft")
```

Ausführen:

```bash
python3 main.py
```

Ausgabe:

```text
Hallo Welt
Python läuft
```

Dieses Beispiel zeigt, ob Python grundsätzlich funktioniert.

---

## Beispiel 2: Einfache Variablen

```python
hostname = "server01"
ip_adresse = "192.168.10.20"

print("Hostname:", hostname)
print("IP-Adresse:", ip_adresse)
```

Ausgabe:

```text
Hostname: server01
IP-Adresse: 192.168.10.20
```

Das ist ein einfaches Beispiel für technische Daten.

---

## Beispiel 3: Liste von Servern

```python
server = ["web01", "db01", "backup01"]

print(server[0])
print(server[1])
print(server[2])
```

Ausgabe:

```text
web01
db01
backup01
```

Listen sind nützlich, wenn man mehrere ähnliche Werte speichern möchte.

---

## Beispiel 4: Einfacher Status

```python
dienst_laeuft = True

if dienst_laeuft:
    print("Dienst läuft")
else:
    print("Dienst läuft nicht")
```

Ausgabe:

```text
Dienst läuft
```

Dieses Beispiel zeigt eine einfache Bedingung.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| Datei nicht gespeichert | alte Version wird ausgeführt |
| falscher Dateiname | Terminal findet Datei nicht |
| falscher Ordner | Skript wird nicht gefunden |
| Einrückung falsch | Python versteht Codeblock nicht |
| Variable nicht definiert | NameError |
| Text ohne Anführungszeichen | Syntaxfehler |
| Klammer fehlt | Syntaxfehler |
| `python` statt `python3` verwechselt | falsche Python-Version möglich |

---

## FISI-Bezug

Python-Grundlagen sind für FISI sinnvoll, weil viele technische Aufgaben mit Logik, Daten und Wiederholung zu tun haben.

Man braucht Python nicht für jede Aufgabe.

Aber Python hilft bei:

```text
Skripting
Automatisierung
Loganalyse
Dateiverarbeitung
JSON-Verarbeitung
kleinen Admin-Tools
DevOps-Grundlagen
technischem Verständnis
```

Ein FISI sollte einfache Skripte lesen und anpassen können.

Das hilft auch beim Verständnis anderer Werkzeuge wie Bash, PowerShell, Docker, APIs und Konfigurationsdateien.

---

## Kurze Zusammenfassung

Python ist eine gut lesbare Programmiersprache, die für Skripting, Automatisierung, Dateien, Logs, JSON und kleine technische Tools genutzt werden kann.

Python-Dateien haben meistens die Endung `.py` und werden zum Beispiel mit `python3 datei.py` ausgeführt.

Wichtige Grundlagen sind `print()`, Variablen, Datentypen, Listen, Dictionaries, Bedingungen, Einrückung und Fehlermeldungen.

Für FISI ist Python eine praktische Ergänzung, um technische Aufgaben besser zu verstehen und einfache Automatisierung umzusetzen.