# 2. Variablen, Datentypen und Operatoren

In diesem Kapitel geht es um Variablen, Datentypen und Operatoren in Python.

Variablen speichern Werte. Datentypen beschreiben, welche Art von Wert gespeichert wird. Operatoren werden genutzt, um mit diesen Werten zu arbeiten.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Skripte mit technischen Daten arbeiten: Dateinamen, IP-Adressen, Ports, Benutzerlisten, Statuswerten, Logzeilen oder Konfigurationswerten.

---

## Kurz erklärt

Eine Variable ist ein Name für einen gespeicherten Wert.

Beispiel:

```python
hostname = "server01"
port = 22
ssh_aktiv = True
```

Hier werden drei Werte gespeichert:

```text
hostname speichert einen Text
port speichert eine Zahl
ssh_aktiv speichert Wahr oder Falsch
```

Mit Variablen kann man Werte später wiederverwenden.

---

## Warum Variablen wichtig sind

Ohne Variablen müsste man Werte ständig direkt in den Code schreiben.

Schlecht:

```python
print("server01")
print("server01")
print("server01")
```

Besser:

```python
hostname = "server01"

print(hostname)
print(hostname)
print(hostname)
```

Wenn sich der Hostname ändert, muss man ihn nur an einer Stelle anpassen.

---

## Variablen erstellen

In Python erstellt man eine Variable mit einem Namen, einem Gleichheitszeichen und einem Wert.

```python
name = "Bilgin"
alter = 25
```

Das Gleichheitszeichen bedeutet hier:

```text
Speichere den Wert rechts in der Variable links.
```

Also:

```text
name bekommt den Wert "Bilgin"
alter bekommt den Wert 25
```

---

## Variablen ausgeben

Variablen kann man mit `print()` ausgeben.

```python
hostname = "server01"
ip_adresse = "192.168.10.20"

print(hostname)
print(ip_adresse)
```

Ausgabe:

```text
server01
192.168.10.20
```

Man kann auch Text und Variablen zusammen ausgeben:

```python
print("Hostname:", hostname)
print("IP-Adresse:", ip_adresse)
```

Ausgabe:

```text
Hostname: server01
IP-Adresse: 192.168.10.20
```

---

## Gute Variablennamen

Gute Variablennamen machen Code verständlicher.

Schlecht:

```python
x = "server01"
y = "192.168.10.20"
z = 22
```

Besser:

```python
hostname = "server01"
ip_adresse = "192.168.10.20"
ssh_port = 22
```

Gute Namen erklären, was gespeichert wird.

---

## Regeln für Variablennamen

Variablennamen dürfen:

```text
Buchstaben enthalten
Zahlen enthalten
Unterstriche enthalten
nicht mit einer Zahl beginnen
keine Leerzeichen enthalten
```

Gültig:

```python
hostname = "server01"
ip_adresse = "192.168.10.20"
server_1 = "web01"
```

Ungültig:

```python
1server = "web01"
ip adresse = "192.168.10.20"
server-name = "web01"
```

In Python nutzt man meistens `snake_case`.

Beispiel:

```python
backup_erfolgreich = True
anzahl_server = 3
```

---

## Datentypen

Ein Datentyp beschreibt, welche Art von Wert eine Variable enthält.

Wichtige Datentypen:

| Datentyp | Bedeutung | Beispiel |
|---|---|---|
| `str` | Text | `"server01"` |
| `int` | ganze Zahl | `22` |
| `float` | Kommazahl | `3.14` |
| `bool` | Wahrheitswert | `True` |
| `list` | Liste mehrerer Werte | `["web01", "db01"]` |
| `dict` | Schlüssel-Wert-Struktur | `{"name": "web01"}` |
| `None` | kein Wert | `None` |

Python erkennt den Datentyp meistens automatisch.

---

## type()

Mit `type()` kann man prüfen, welchen Datentyp ein Wert hat.

```python
hostname = "server01"
port = 22
cpu_last = 15.5
ssh_aktiv = True

print(type(hostname))
print(type(port))
print(type(cpu_last))
print(type(ssh_aktiv))
```

Ausgabe:

```text
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
```

Das ist nützlich, wenn man nicht sicher ist, mit welchem Datentyp man arbeitet.

---

## String

Ein String ist Text.

Strings stehen in Anführungszeichen.

```python
hostname = "server01"
rolle = "Webserver"
```

Man kann doppelte oder einfache Anführungszeichen nutzen:

```python
text1 = "Hallo"
text2 = 'Hallo'
```

Beides funktioniert.

Wichtig ist, dass Anfang und Ende zusammenpassen.

---

## Strings verbinden

Strings kann man mit `+` verbinden.

```python
vorname = "Bilgin"
nachname = "Maystorov"

voller_name = vorname + " " + nachname

print(voller_name)
```

Ausgabe:

```text
Bilgin Maystorov
```

Für einfache Ausgaben ist oft ein f-String besser.

---

## f-Strings

f-Strings sind eine praktische Möglichkeit, Variablen in Text einzubauen.

```python
hostname = "server01"
ip_adresse = "192.168.10.20"

print(f"Der Server {hostname} hat die IP-Adresse {ip_adresse}.")
```

Ausgabe:

```text
Der Server server01 hat die IP-Adresse 192.168.10.20.
```

f-Strings sind sehr gut lesbar und werden in Python häufig genutzt.

---

## Integer

Ein Integer ist eine ganze Zahl.

```python
ssh_port = 22
anzahl_server = 3
fehler_count = 5
```

Mit Integern kann man rechnen.

```python
server_online = 8
server_offline = 2

gesamt = server_online + server_offline

print(gesamt)
```

Ausgabe:

```text
10
```

---

## Float

Ein Float ist eine Kommazahl.

```python
cpu_last = 15.5
temperatur = 42.7
speicher_gb = 3.8
```

Floats nutzt man für Werte mit Nachkommastellen.

Beispiel:

```python
download_gb = 5.5
upload_gb = 2.3

gesamt = download_gb + upload_gb

print(gesamt)
```

Ausgabe:

```text
7.8
```

---

## Boolean

Ein Boolean speichert Wahr oder Falsch.

```python
ssh_aktiv = True
backup_erfolgreich = False
```

Booleans sind wichtig für Bedingungen.

```python
if ssh_aktiv:
    print("SSH ist aktiv")
else:
    print("SSH ist nicht aktiv")
```

Booleans helfen, Zustände im Programm abzubilden.

---

## None

`None` bedeutet:

```text
kein Wert
```

Beispiel:

```python
letzter_fehler = None
```

Das kann sinnvoll sein, wenn ein Wert später gesetzt wird.

Beispiel:

```python
letzter_fehler = None

print(letzter_fehler)
```

Ausgabe:

```text
None
```

`None` ist nicht dasselbe wie `0`, `False` oder ein leerer Text.

---

## Listen

Eine Liste speichert mehrere Werte.

```python
server = ["web01", "db01", "backup01"]
```

Liste ausgeben:

```python
print(server)
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
Python zählt ab 0.
```

Das erste Element hat also den Index `0`.

---

## Liste erweitern

Mit `.append()` kann man einer Liste ein neues Element hinzufügen.

```python
server = ["web01", "db01"]

server.append("backup01")

print(server)
```

Ausgabe:

```text
['web01', 'db01', 'backup01']
```

Listen sind nützlich, wenn man mehrere ähnliche Werte speichern möchte.

---

## Dictionary

Ein Dictionary speichert Werte mit Schlüsseln.

```python
server = {
    "name": "web01",
    "ip": "192.168.10.20",
    "rolle": "Webserver"
}
```

Wert auslesen:

```python
print(server["name"])
print(server["ip"])
```

Ausgabe:

```text
web01
192.168.10.20
```

Dictionaries sind sehr wichtig für strukturierte Daten.

Sie passen gut zu JSON.

---

## Dictionary erweitern

Man kann neue Schlüssel hinzufügen.

```python
server = {
    "name": "web01",
    "ip": "192.168.10.20"
}

server["rolle"] = "Webserver"

print(server)
```

Ausgabe:

```text
{'name': 'web01', 'ip': '192.168.10.20', 'rolle': 'Webserver'}
```

Das ist praktisch, wenn Daten Schritt für Schritt aufgebaut werden.

---

## Datentypen umwandeln

Manchmal muss man Werte umwandeln.

Beispiele:

```python
zahl_text = "22"
port = int(zahl_text)

print(port)
print(type(port))
```

Ausgabe:

```text
22
<class 'int'>
```

Wichtige Umwandlungen:

| Funktion | Bedeutung |
|---|---|
| `str()` | in Text umwandeln |
| `int()` | in ganze Zahl umwandeln |
| `float()` | in Kommazahl umwandeln |
| `bool()` | in Wahrheitswert umwandeln |

---

## input() und Datentypen

`input()` liefert immer Text zurück.

Beispiel:

```python
alter = input("Wie alt bist du? ")

print(type(alter))
```

Auch wenn man `25` eingibt, ist der Wert ein String.

Wenn man rechnen möchte, muss man umwandeln:

```python
alter = int(input("Wie alt bist du? "))

print(alter + 1)
```

Ohne `int()` würde Python den Wert als Text behandeln.

---

## Operatoren

Operatoren werden genutzt, um mit Werten zu arbeiten.

Beispiele:

```text
rechnen
vergleichen
logisch prüfen
Werte verbinden
```

Wichtige Operatorgruppen:

```text
arithmetische Operatoren
Vergleichsoperatoren
logische Operatoren
Zuweisungsoperatoren
```

---

## Arithmetische Operatoren

Arithmetische Operatoren nutzt man zum Rechnen.

| Operator | Bedeutung | Beispiel |
|---|---|---|
| `+` | Addition | `5 + 3` |
| `-` | Subtraktion | `5 - 3` |
| `*` | Multiplikation | `5 * 3` |
| `/` | Division | `5 / 3` |
| `//` | Ganzzahldivision | `5 // 3` |
| `%` | Restwert | `5 % 3` |
| `**` | Potenz | `2 ** 3` |

Beispiel:

```python
a = 5
b = 3

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a // b)
print(a % b)
print(a ** b)
```

Ausgabe:

```text
8
2
15
1.6666666666666667
1
2
125
```

---

## Modulo

Der Modulo-Operator `%` gibt den Rest einer Division zurück.

Beispiel:

```python
print(10 % 3)
```

Ausgabe:

```text
1
```

Denn:

```text
10 geteilt durch 3 = 3 Rest 1
```

Modulo wird oft genutzt, um zu prüfen, ob eine Zahl gerade ist.

```python
zahl = 10

if zahl % 2 == 0:
    print("gerade")
else:
    print("ungerade")
```

---

## Vergleichsoperatoren

Vergleichsoperatoren prüfen Werte.

Das Ergebnis ist immer ein Boolean: `True` oder `False`.

| Operator | Bedeutung |
|---|---|
| `==` | ist gleich |
| `!=` | ist ungleich |
| `>` | größer als |
| `<` | kleiner als |
| `>=` | größer oder gleich |
| `<=` | kleiner oder gleich |

Beispiel:

```python
port = 22

print(port == 22)
print(port != 80)
print(port > 20)
```

Ausgabe:

```text
True
True
True
```

---

## Gleichheitszeichen vs Vergleich

Wichtig:

```text
=  speichert einen Wert
== vergleicht zwei Werte
```

Beispiel:

```python
port = 22
```

Das speichert `22` in der Variable `port`.

Beispiel:

```python
port == 22
```

Das prüft, ob `port` den Wert `22` hat.

Dieser Unterschied ist sehr wichtig.

---

## Logische Operatoren

Logische Operatoren verbinden Bedingungen.

| Operator | Bedeutung |
|---|---|
| `and` | beide Bedingungen müssen wahr sein |
| `or` | mindestens eine Bedingung muss wahr sein |
| `not` | kehrt Wahrheitswert um |

Beispiel:

```python
ssh_aktiv = True
firewall_erlaubt = True

if ssh_aktiv and firewall_erlaubt:
    print("SSH-Zugriff möglich")
```

Nur wenn beide Werte `True` sind, wird die Meldung ausgegeben.

---

## and

`and` bedeutet:

```text
beide Bedingungen müssen wahr sein
```

Beispiel:

```python
ip_vorhanden = True
gateway_vorhanden = True

if ip_vorhanden and gateway_vorhanden:
    print("Netzwerk sieht grundsätzlich gut aus")
```

Wenn eine der beiden Bedingungen `False` ist, wird der Block nicht ausgeführt.

---

## or

`or` bedeutet:

```text
mindestens eine Bedingung muss wahr sein
```

Beispiel:

```python
ssh_erlaubt = False
web_erlaubt = True

if ssh_erlaubt or web_erlaubt:
    print("Mindestens ein Dienst ist erreichbar")
```

Hier wird die Meldung ausgegeben, weil `web_erlaubt` wahr ist.

---

## not

`not` kehrt einen Boolean um.

Beispiel:

```python
backup_erfolgreich = False

if not backup_erfolgreich:
    print("Backup prüfen")
```

Da `backup_erfolgreich` `False` ist, wird durch `not` daraus logisch `True`.

---

## Zuweisungsoperatoren

Zuweisungsoperatoren verändern Werte.

| Operator | Bedeutung | Beispiel |
|---|---|---|
| `=` | Wert zuweisen | `x = 5` |
| `+=` | erhöhen | `x += 1` |
| `-=` | verringern | `x -= 1` |
| `*=` | multiplizieren | `x *= 2` |
| `/=` | teilen | `x /= 2` |

Beispiel:

```python
fehler = 0

fehler += 1
fehler += 1

print(fehler)
```

Ausgabe:

```text
2
```

Das ist praktisch für Zähler.

---

## String-Operatoren

Das `+` kann Strings verbinden.

```python
text = "Hallo" + " " + "Welt"

print(text)
```

Ausgabe:

```text
Hallo Welt
```

Das `*` kann Strings wiederholen.

```python
linie = "-" * 10

print(linie)
```

Ausgabe:

```text
----------
```

Das kann nützlich sein, um einfache Ausgaben zu formatieren.

---

## Operatoren und Datentypen

Nicht jeder Operator funktioniert mit jedem Datentyp.

Beispiel:

```python
print("Port: " + 22)
```

Das führt zu einem Fehler, weil Text und Zahl nicht direkt mit `+` verbunden werden können.

Besser:

```python
port = 22

print("Port: " + str(port))
```

Oder besser lesbar:

```python
port = 22

print(f"Port: {port}")
```

f-Strings vermeiden viele solche Fehler.

---

## Beispiel 1: Serverdaten speichern

```python
hostname = "web01"
ip_adresse = "192.168.10.20"
ssh_port = 22
ssh_aktiv = True

print(f"Server: {hostname}")
print(f"IP-Adresse: {ip_adresse}")
print(f"SSH-Port: {ssh_port}")
print(f"SSH aktiv: {ssh_aktiv}")
```

Ausgabe:

```text
Server: web01
IP-Adresse: 192.168.10.20
SSH-Port: 22
SSH aktiv: True
```

---

## Beispiel 2: Speicherplatz prüfen

```python
freier_speicher_gb = 12
grenze_gb = 10

if freier_speicher_gb < grenze_gb:
    print("Warnung: wenig Speicherplatz")
else:
    print("Speicherplatz ausreichend")
```

Ausgabe:

```text
Speicherplatz ausreichend
```

Das zeigt, wie Variablen und Vergleiche für einfache Prüfungen genutzt werden können.

---

## Beispiel 3: Liste von Hosts

```python
hosts = ["web01", "db01", "backup01"]

print(f"Erster Host: {hosts[0]}")
print(f"Zweiter Host: {hosts[1]}")
print(f"Dritter Host: {hosts[2]}")
```

Ausgabe:

```text
Erster Host: web01
Zweiter Host: db01
Dritter Host: backup01
```

Listen sind sinnvoll, wenn mehrere Werte zusammengehören.

---

## Beispiel 4: Dictionary für Server

```python
server = {
    "hostname": "web01",
    "ip": "192.168.10.20",
    "port": 22,
    "rolle": "Webserver"
}

print(f"Hostname: {server['hostname']}")
print(f"IP: {server['ip']}")
print(f"Port: {server['port']}")
print(f"Rolle: {server['rolle']}")
```

Ausgabe:

```text
Hostname: web01
IP: 192.168.10.20
Port: 22
Rolle: Webserver
```

Dictionaries sind gut für strukturierte technische Informationen.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| `=` und `==` verwechseln | Zuweisung und Vergleich werden verwechselt |
| Zahl als Text behandeln | Rechnen funktioniert nicht wie erwartet |
| Text und Zahl mit `+` verbinden | TypeError |
| falscher Listenindex | falsches Element oder IndexError |
| Schlüssel im Dictionary falsch schreiben | KeyError |
| Boolean klein schreiben | `true` ist falsch, richtig ist `True` |
| Variable unterschiedlich schreiben | Python erkennt andere Namen |
| input nicht umwandeln | eingegebene Zahlen bleiben Text |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Variablen und Datentypen:

```text
aussagekräftige Namen verwenden
Datentypen bewusst prüfen
f-Strings für Ausgaben nutzen
input-Werte bei Bedarf umwandeln
Listen für mehrere ähnliche Werte nutzen
Dictionaries für strukturierte Daten nutzen
Fehlermeldungen lesen
kleine Beispiele testen
```

Wichtige Regel:

```text
Erst verstehen, welcher Datentyp vorliegt.
Dann entscheiden, was man damit machen kann.
```

---

## FISI-Bezug

Variablen, Datentypen und Operatoren sind für FISI wichtig, weil viele technische Aufgaben mit Daten arbeiten.

Beispiele:

```text
Hostnamen speichern
IP-Adressen verarbeiten
Ports prüfen
Logzeilen durchsuchen
Statuswerte vergleichen
Serverlisten auswerten
JSON-Daten verstehen
Konfigurationswerte nutzen
einfache Reports erstellen
```

Ein FISI muss nicht jede Python-Funktion auswendig kennen.

Aber er sollte verstehen, wie Werte gespeichert, geprüft und verarbeitet werden.

---

## Kurze Zusammenfassung

Variablen speichern Werte unter einem Namen.

Datentypen beschreiben, welche Art von Wert gespeichert wird. Wichtige Datentypen sind `str`, `int`, `float`, `bool`, `list`, `dict` und `None`.

Operatoren werden genutzt, um Werte zu berechnen, zu vergleichen oder logisch zu prüfen.

Für FISI sind diese Grundlagen wichtig, weil viele Skripte mit technischen Daten wie Hostnamen, IP-Adressen, Ports, Logs, Dateien und Statuswerten arbeiten.