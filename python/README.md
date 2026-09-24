# Python

In diesem Bereich geht es um Python-Grundlagen mit Fokus auf Systemintegration, Skripting und Automatisierung.

Python ist eine Programmiersprache, die häufig für kleine Tools, Automatisierung, Datenverarbeitung, Tests, einfache Admin-Skripte und technische Hilfsprogramme genutzt wird.

Für Fachinformatiker für Systemintegration ist Python nicht das Hauptthema wie bei der Anwendungsentwicklung. Trotzdem ist Python sehr nützlich, weil man damit wiederkehrende Aufgaben automatisieren, Dateien auswerten, Logs analysieren und kleine Werkzeuge für die tägliche IT-Arbeit schreiben kann.

---

## Kurz erklärt

Python kann in der FISI-Praxis helfen bei:

```text
kleinen Admin-Skripten
Dateien lesen und schreiben
Logdateien auswerten
JSON-Daten verarbeiten
einfache Automatisierung
Systeminformationen sammeln
wiederkehrende Aufgaben vereinfachen
kleine Tools für eigene Labs schreiben
```

Der Fokus in diesem Bereich liegt nicht auf großer Softwareentwicklung, sondern auf praktischem Verständnis.

---

## Warum Python für FISI sinnvoll ist

Ein FISI muss nicht unbedingt große Anwendungen entwickeln.

Aber es ist hilfreich, Programmierlogik zu verstehen.

Python hilft dabei, technische Abläufe besser zu verstehen:

```text
Was ist eine Variable?
Wie funktionieren Bedingungen?
Wie funktionieren Schleifen?
Wie verarbeitet man Dateien?
Wie behandelt man Fehler?
Wie strukturiert man Code?
Wie automatisiert man einfache Aufgaben?
```

Diese Grundlagen helfen auch bei anderen Themen wie:

```text
Bash-Skripting
PowerShell
Docker
APIs
JSON
Konfigurationsdateien
Automatisierung
Monitoring
DevOps-Grundlagen
```

---

## Kapitelübersicht

| Kapitel | Thema |
|---|---|
| [1. Python Grundlagen](./01-python-grundlagen.md) | Was Python ist, wie Programme aufgebaut sind und wie man sie ausführt |
| [2. Variablen, Datentypen und Operatoren](./02-variablen-datentypen-und-operatoren.md) | Werte speichern, Texte, Zahlen, Listen und einfache Berechnungen |
| [3. Kontrollstrukturen](./03-kontrollstrukturen.md) | Bedingungen, Schleifen und Programmablauf steuern |
| [4. Funktionen und Module](./04-funktionen-und-module.md) | Code strukturieren, wiederverwenden und externe Module nutzen |
| [5. Dateien, Logs und JSON](./05-dateien-logs-und-json.md) | Dateien lesen, schreiben, Logs auswerten und JSON-Daten verarbeiten |
| [6. Fehlerbehandlung und Debugging](./06-fehlerbehandlung-und-debugging.md) | Fehler verstehen, abfangen und systematisch beheben |
| [7. OOP Grundlagen](./07-oop-grundlagen.md) | Klassen, Objekte, Methoden und einfache objektorientierte Struktur |
| [8. Skripting und Automatisierung](./08-skripting-und-automatisierung.md) | kleine praktische Skripte für wiederkehrende Aufgaben |
| [9. Python in der FISI-Praxis](./09-python-in-der-fisi-praxis.md) | typische Anwendungsfälle für Systemintegration und Home-Lab |

---

## Python im Vergleich zu Bash und PowerShell

Python ersetzt Bash oder PowerShell nicht immer.

Jedes Werkzeug hat seinen eigenen Zweck.

| Werkzeug | Typischer Einsatz |
|---|---|
| Bash | Linux-Kommandos, einfache Automatisierung, Terminal-Aufgaben |
| PowerShell | Windows-Administration, Dienste, Benutzer, Systemabfragen |
| Python | strukturierte Skripte, Dateien, Daten, JSON, kleine Tools |
| SQL | Datenbanken abfragen und Daten verwalten |

Beispiel:

```text
Bash ist gut für schnelle Linux-Kommandos.
PowerShell ist stark für Windows-Verwaltung.
Python ist gut, wenn ein Skript etwas mehr Logik oder Datenverarbeitung braucht.
```

---

## Typische Python-Aufgaben für FISI

Python kann in der Systemintegration für viele kleine Aufgaben genutzt werden.

Beispiele:

```text
eine Logdatei nach Fehlern durchsuchen
mehrere Textdateien auswerten
eine JSON-Konfiguration lesen
eine Liste von Servernamen verarbeiten
einfache Reports erstellen
Dateien automatisch umbenennen
Ordner prüfen
IP-Adressen oder Hostnamen aus einer Datei lesen
kleine Hilfstools für eigene Labs bauen
```

Wichtig ist nicht, direkt perfekte Programme zu schreiben.

Wichtig ist, die Denkweise zu verstehen.

---

## Beispiel: Logdatei prüfen

Ein einfaches Python-Skript könnte später zum Beispiel prüfen, ob eine Logdatei Fehler enthält.

Beispiel-Idee:

```text
Datei öffnen
jede Zeile lesen
nach "error" suchen
Treffer anzeigen
```

Das ist für FISI interessant, weil Logs bei Fehlersuche sehr wichtig sind.

---

## Beispiel: JSON verarbeiten

Viele moderne Tools verwenden JSON.

Beispiele:

```text
APIs
Docker
Cloud-Dienste
Konfigurationsdateien
Monitoring-Systeme
Automatisierungswerkzeuge
```

Python kann JSON-Dateien lesen und verarbeiten.

Beispiel-Idee:

```text
JSON-Datei öffnen
Werte auslesen
bestimmte Informationen anzeigen
```

Das hilft, technische Daten besser zu verstehen.

---

## Beispiel: Dateien automatisch prüfen

Python kann Dateien und Ordner auswerten.

Beispiel-Idee:

```text
Ordner öffnen
alle Dateien auflisten
Dateigrößen prüfen
Dateien nach Endung filtern
Ergebnis anzeigen
```

Solche kleinen Skripte sind gute Übungen für Administration und Automatisierung.

---

## Lernziel dieses Bereichs

Nach diesem Bereich sollte man nicht unbedingt großer Python-Entwickler sein.

Das Ziel ist eher:

```text
Python-Code lesen können
kleine Skripte selbst schreiben können
Fehler grob verstehen können
Dateien verarbeiten können
JSON verstehen können
Funktionen nutzen können
einfache Automatisierungsideen umsetzen können
Python sinnvoll in FISI-Kontext einordnen können
```

---

## Arbeitsweise

Die Kapitel sind bewusst praxisnah aufgebaut.

Typischer Aufbau:

```text
kurze Erklärung
wichtige Begriffe
einfache Beispiele
typische Fehler
FISI-Bezug
kurze Zusammenfassung
```

Der Fokus liegt auf Verständnis und Anwendung.

Nicht auf komplizierter Theorie.

---

## Wichtig für öffentliche Repositories

Bei Python-Projekten auf GitHub muss man aufpassen, keine privaten Daten zu veröffentlichen.

Nicht veröffentlichen:

```text
Passwörter
API-Tokens
private SSH-Keys
echte Kundendaten
interne IP-Pläne
private Logdateien
echte .env-Dateien
```

Besser:

```text
Beispieldaten nutzen
.env.example verwenden
Secrets nicht committen
private Logs anonymisieren
README sauber dokumentieren
```

Das passt auch zu IT-Sicherheit und Datenschutz.

---

## Typische Fehler beim Python-Lernen

| Fehler | Problem |
|---|---|
| nur Code kopieren | man versteht die Logik nicht |
| zu große Projekte starten | man wird schnell überfordert |
| Fehlermeldungen ignorieren | Fehler werden nicht verstanden |
| keine kleinen Schritte machen | Debugging wird schwer |
| Dateien ohne Plan bearbeiten | Daten können überschrieben werden |
| keine Dokumentation schreiben | später schwer nachvollziehbar |
| Secrets in Git speichern | Sicherheitsrisiko |
| zu früh zu komplex werden | Grundlagen fehlen |

Besser ist:

```text
kleine Skripte schreiben
Fehler bewusst lesen
Code selbst tippen
Schritt für Schritt erweitern
Ergebnisse dokumentieren
```

---

## FISI-Bezug

Python ist für FISI besonders interessant als Ergänzung zu:

```text
Linux
Windows
Netzwerke
Docker
Logs
Dateien
JSON
Automatisierung
Monitoring
Home-Lab
DevOps-Grundlagen
```

Python hilft, wiederkehrende technische Aufgaben besser zu verstehen und teilweise zu automatisieren.

Ein FISI muss nicht alles selbst programmieren.

Aber ein FISI sollte verstehen, wie einfache Skripte funktionieren und wann sie sinnvoll eingesetzt werden können.

---

## Kurze Zusammenfassung

Python ist eine vielseitige Programmiersprache, die auch für Fachinformatiker für Systemintegration nützlich ist.

Der Fokus liegt in diesem Wiki auf Grundlagen, Skripting, Dateien, Logs, JSON, Fehlerbehandlung, Automatisierung und praktischen IT-Aufgaben.

Python ergänzt Linux, Windows, Docker, Git, Netzwerke und Systemadministration.

Dieser Bereich soll helfen, kleine technische Skripte zu verstehen, selbst zu schreiben und sinnvoll in der FISI-Praxis einzuordnen.