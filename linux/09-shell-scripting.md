# 9. Shell Scripting

In diesem Kapitel geht es um Shell Scripting unter Linux.

Shell-Skripte werden genutzt, um Befehle zu automatisieren. Statt mehrere Befehle immer wieder manuell einzugeben, kann man sie in einer Datei speichern und als Skript ausführen.

Für Fachinformatiker für Systemintegration ist Shell Scripting wichtig, weil viele wiederkehrende Aufgaben im Linux- und Serverbetrieb automatisiert werden können: Systemprüfungen, Backups, Logauswertungen, Benutzerverwaltung, Paketprüfungen, Dienstkontrollen und einfache Wartungsaufgaben.

---

## Kurz erklärt

Ein Shell-Skript ist eine Textdatei mit Linux-Befehlen.

Diese Befehle werden nacheinander ausgeführt.

Ein einfaches Skript:

```bash
#!/bin/bash

echo "Systemstatus"
hostname
uptime
df -h
```

Ein Shell-Skript kann zum Beispiel:

- Systeminformationen anzeigen
- Dateien kopieren
- Backups erstellen
- Logs durchsuchen
- Dienste prüfen
- Benutzerinformationen ausgeben
- Pakete prüfen
- Netzwerk testen
- Aufgaben automatisieren
- Fehlerausgaben speichern
- Reports erzeugen

Shell Scripting ist keine große Anwendung wie Python oder Java. Es ist besonders stark, wenn man Linux-Befehle automatisieren und verbinden möchte.

---

## Was ist eine Shell?

Eine Shell ist ein Programm, das Befehle entgegennimmt und ausführt.

Die Shell ist die Verbindung zwischen Benutzer und Betriebssystem.

Häufige Shells:

| Shell  | Bedeutung                                  |
| ------ | ------------------------------------------ |
| `bash` | sehr verbreitete Standardshell unter Linux |
| `sh`   | klassische einfache Shell                  |
| `zsh`  | moderne Shell mit vielen Komfortfunktionen |
| `fish` | benutzerfreundliche Shell                  |

Auf Ubuntu und Debian ist Bash sehr wichtig.

Prüfen, welche Shell man nutzt:

```bash
echo $SHELL
```

Oder:

```bash
ps -p $$
```

---

## Was ist ein Skript?

Ein Skript ist eine Datei mit Befehlen, die automatisch ausgeführt werden.

Beispiel:

```bash
echo "Hallo"
date
hostname
```

Wenn diese Befehle in einer Datei stehen, kann man sie später wieder ausführen, ohne alles erneut zu tippen.

Typische Dateiendung:

```text
.sh
```

Beispiel:

```text
check-system.sh
backup.sh
install-tools.sh
log-check.sh
```

Die Endung `.sh` ist hilfreich für Menschen, aber technisch nicht allein entscheidend. Wichtig sind Inhalt, Shebang und Ausführungsrechte.

---

## Shebang

Am Anfang eines Shell-Skripts steht oft ein Shebang.

```bash
#!/bin/bash
```

Der Shebang sagt dem System, mit welchem Programm das Skript ausgeführt werden soll.

Beispiele:

```bash
#!/bin/bash
#!/bin/sh
#!/usr/bin/env bash
```

Häufig nutzt man:

```bash
#!/bin/bash
```

oder:

```bash
#!/usr/bin/env bash
```

Der Shebang ist wichtig, wenn man das Skript direkt ausführt:

```bash
./script.sh
```

---

## Skript erstellen

Ein Skript kann man mit einem Editor erstellen.

Beispiel mit `nano`:

```bash
nano check-system.sh
```

Inhalt:

```bash
#!/bin/bash

echo "Systemstatus"
hostname
uptime
df -h
```

Speichern in nano:

```text
Ctrl + O
Enter
Ctrl + X
```

Danach ist die Datei vorhanden, aber noch nicht automatisch ausführbar.

---

## Skript ausführbar machen

Ein Skript braucht Ausführungsrechte.

```bash
chmod +x check-system.sh
```

Danach starten:

```bash
./check-system.sh
```

Das `./` bedeutet:

```text
Starte die Datei aus dem aktuellen Verzeichnis.
```

Ohne `./` sucht die Shell das Programm nur in den Verzeichnissen aus der `PATH`-Variable.

---

## Skript ohne Ausführungsrecht starten

Man kann ein Skript auch direkt mit Bash starten.

```bash
bash check-system.sh
```

Dann braucht die Datei nicht unbedingt Ausführungsrechte.

Unterschied:

| Startart         | Bedeutung                                                           |
| ---------------- | ------------------------------------------------------------------- |
| `./script.sh`    | Skript direkt starten, braucht Ausführungsrecht und Shebang         |
| `bash script.sh` | Bash führt die Datei aus, Ausführungsrecht ist nicht zwingend nötig |

Für echte Admin-Skripte ist `chmod +x` mit sauberem Shebang meistens besser.

---

## Kommentare

Kommentare erklären den Code.

In Bash beginnt ein Kommentar mit:

```bash
#
```

Beispiel:

```bash
#!/bin/bash

# Hostname anzeigen
hostname

# Speicherplatz anzeigen
df -h
```

Kommentare sind wichtig, damit man später versteht, warum ein Befehl im Skript steht.

Aber Kommentare sollten nicht jeden offensichtlichen Befehl wiederholen.

Gut:

```bash
# Prüft, ob das Root-Dateisystem fast voll ist
df -h /
```

Weniger sinnvoll:

```bash
# echo gibt Text aus
echo "Hallo"
```

---

## echo

Mit `echo` gibt man Text aus.

```bash
echo "Hallo"
```

Beispiel:

```bash
echo "Starte Systemprüfung..."
hostname
echo "Prüfung beendet."
```

`echo` ist nützlich für:

- Statusmeldungen
- einfache Ausgaben
- Debugging
- Reports
- Hinweise für Benutzer

---

## Variablen

Variablen speichern Werte.

Beispiel:

```bash
name="Bilgin"
echo "$name"
```

Wichtig:

Bei der Zuweisung dürfen keine Leerzeichen um `=` stehen.

Richtig:

```bash
name="Bilgin"
```

Falsch:

```bash
name = "Bilgin"
```

Variablen werden mit `$` gelesen:

```bash
echo "$name"
```

---

## Warum Anführungszeichen wichtig sind

Variablen sollten meistens in Anführungszeichen gesetzt werden.

Besser:

```bash
echo "$name"
```

Nicht so gut:

```bash
echo $name
```

Das ist besonders wichtig, wenn Werte Leerzeichen enthalten.

Beispiel:

```bash
file="mein dokument.txt"
cat "$file"
```

Ohne Anführungszeichen würde die Shell den Namen als mehrere Teile interpretieren.

---

## Einfache Systemvariablen

Linux stellt viele Umgebungsvariablen bereit.

Beispiele:

| Variable    | Bedeutung                      |
| ----------- | ------------------------------ |
| `$HOME`     | Home-Verzeichnis des Benutzers |
| `$USER`     | Benutzername                   |
| `$SHELL`    | aktuelle Shell                 |
| `$PATH`     | Suchpfade für Programme        |
| `$PWD`      | aktuelles Verzeichnis          |
| `$HOSTNAME` | Hostname                       |

Beispiele:

```bash
echo "$HOME"
echo "$USER"
echo "$PATH"
echo "$PWD"
```

Diese Variablen sind in Skripten sehr praktisch.

---

## Kommandoausgabe in Variable speichern

Mit `$(...)` kann man die Ausgabe eines Befehls speichern.

Beispiel:

```bash
current_date=$(date)
echo "$current_date"
```

Hostname speichern:

```bash
host=$(hostname)
echo "System: $host"
```

Speicherprüfung:

```bash
disk_usage=$(df -h /)
echo "$disk_usage"
```

Das ist sehr wichtig für Reports und Automatisierung.

---

## Eingaben mit read

Mit `read` kann man Benutzereingaben einlesen.

Beispiel:

```bash
#!/bin/bash

echo "Wie heißt du?"
read name

echo "Hallo $name"
```

Besser mit Prompt:

```bash
read -p "Wie heißt du? " name
echo "Hallo $name"
```

`read` ist nützlich für einfache interaktive Skripte.

Auf Servern und in Automatisierung sind nicht-interaktive Skripte aber oft besser.

---

## Parameter an Skripte übergeben

Ein Skript kann Parameter bekommen.

Beispielstart:

```bash
./backup.sh /home/bilgin
```

Im Skript:

```bash
#!/bin/bash

echo "Erster Parameter: $1"
```

Wichtige Parameter:

| Ausdruck | Bedeutung                     |
| -------- | ----------------------------- |
| `$0`     | Name des Skripts              |
| `$1`     | erster Parameter              |
| `$2`     | zweiter Parameter             |
| `$#`     | Anzahl der Parameter          |
| `$@`     | alle Parameter                |
| `$?`     | Exit-Code des letzten Befehls |

Beispiel:

```bash
#!/bin/bash

echo "Skriptname: $0"
echo "Erster Parameter: $1"
echo "Anzahl Parameter: $#"
```

---

## Prüfen, ob Parameter vorhanden ist

Beispiel:

```bash
#!/bin/bash

if [ -z "$1" ]; then
  echo "Fehler: Bitte einen Pfad angeben."
  echo "Nutzung: $0 /pfad"
  exit 1
fi

echo "Pfad: $1"
```

Bedeutung:

| Teil          | Bedeutung                 |
| ------------- | ------------------------- |
| `if`          | Bedingung beginnt         |
| `[ -z "$1" ]` | prüft, ob `$1` leer ist   |
| `then`        | dann ausführen            |
| `exit 1`      | Skript mit Fehler beenden |
| `fi`          | Ende der if-Bedingung     |

Das ist wichtig, damit Skripte nicht mit fehlenden Werten weiterlaufen.

---

## Exit-Codes

Jeder Befehl gibt einen Exit-Code zurück.

Anzeigen:

```bash
echo $?
```

Bedeutung:

|      Exit-Code | Bedeutung                      |
| -------------: | ------------------------------ |
|            `0` | erfolgreich                    |
| `1` oder höher | Fehler oder besonderer Zustand |

Beispiel:

```bash
ls /etc
echo $?

ls /ordner-gibt-es-nicht
echo $?
```

Exit-Codes sind wichtig für Automatisierung, weil Skripte dadurch erkennen können, ob ein Befehl erfolgreich war.

---

## if-Bedingungen

Mit `if` kann ein Skript Entscheidungen treffen.

Beispiel:

```bash
#!/bin/bash

if [ -f "/etc/hosts" ]; then
  echo "Datei existiert."
else
  echo "Datei existiert nicht."
fi
```

Bedeutung:

| Test | Bedeutung                   |
| ---- | --------------------------- |
| `-f` | normale Datei existiert     |
| `-d` | Verzeichnis existiert       |
| `-e` | Datei oder Ordner existiert |
| `-z` | Zeichenkette ist leer       |
| `-n` | Zeichenkette ist nicht leer |
| `-r` | lesbar                      |
| `-w` | schreibbar                  |
| `-x` | ausführbar                  |

---

## Zahlen vergleichen

Zahlen werden mit speziellen Operatoren verglichen.

| Operator | Bedeutung           |
| -------- | ------------------- |
| `-eq`    | gleich              |
| `-ne`    | nicht gleich        |
| `-gt`    | größer als          |
| `-ge`    | größer oder gleich  |
| `-lt`    | kleiner als         |
| `-le`    | kleiner oder gleich |

Beispiel:

```bash
#!/bin/bash

count=5

if [ "$count" -gt 3 ]; then
  echo "Count ist größer als 3."
fi
```

Wichtig:

Für Zahlen nutzt man nicht einfach `>` in einfachen `[ ]`, weil das sonst als Umleitung interpretiert werden kann.

---

## Strings vergleichen

Strings kann man so vergleichen:

```bash
name="admin"

if [ "$name" = "admin" ]; then
  echo "Admin erkannt."
fi
```

Ungleich:

```bash
if [ "$name" != "admin" ]; then
  echo "Kein Admin."
fi
```

Leer prüfen:

```bash
if [ -z "$name" ]; then
  echo "Name ist leer."
fi
```

Nicht leer prüfen:

```bash
if [ -n "$name" ]; then
  echo "Name ist gesetzt."
fi
```

---

## Schleifen mit for

Eine `for`-Schleife wiederholt Befehle für mehrere Werte.

Beispiel:

```bash
#!/bin/bash

for file in *.md; do
  echo "Datei: $file"
done
```

Beispiel mit festen Werten:

```bash
for service in ssh docker cron; do
  systemctl is-active "$service"
done
```

`for` ist nützlich für:

- mehrere Dateien
- mehrere Dienste
- mehrere Benutzer
- mehrere Servernamen
- mehrere Ordner

---

## Schleifen mit while

Eine `while`-Schleife läuft, solange eine Bedingung wahr ist.

Beispiel:

```bash
#!/bin/bash

count=1

while [ "$count" -le 5 ]; do
  echo "Durchlauf $count"
  count=$((count + 1))
done
```

`while` wird oft genutzt, wenn man nicht vorher genau weiß, wie oft etwas laufen soll.

---

## Rechnen in Bash

Einfache Berechnungen macht man mit `$((...))`.

Beispiel:

```bash
count=1
count=$((count + 1))
echo "$count"
```

Weitere Beispiele:

```bash
a=10
b=5

echo $((a + b))
echo $((a - b))
echo $((a * b))
echo $((a / b))
```

Bash ist aber nicht ideal für komplexe Mathematik. Für größere Logik ist Python oft besser.

---

## Funktionen

Funktionen fassen Befehle zusammen.

Beispiel:

```bash
#!/bin/bash

show_status() {
  echo "Hostname:"
  hostname

  echo "Uptime:"
  uptime
}

show_status
```

Funktionen sind nützlich, wenn man denselben Ablauf mehrfach braucht.

Beispiel mit Parameter:

```bash
check_service() {
  service="$1"
  systemctl is-active "$service"
}

check_service ssh
check_service docker
```

---

## Pipes in Skripten

Pipes verbinden Befehle.

Beispiel:

```bash
grep -i "error" /var/log/syslog | tail -n 20
```

Das bedeutet:

- suche nach `error`
- zeige davon die letzten 20 Treffer

Pipes sind sehr stark für Logauswertung und Textverarbeitung.

Weitere Beispiele:

```bash
ps aux | grep nginx
df -h | grep "/$"
journalctl -p err | tail -n 20
```

---

## Umleitung

Mit Umleitung kann man Ausgaben in Dateien schreiben.

Überschreiben:

```bash
echo "Report" > report.txt
```

Anhängen:

```bash
echo "Neue Zeile" >> report.txt
```

Fehlerausgabe umleiten:

```bash
command 2> error.log
```

Normale Ausgabe und Fehlerausgabe zusammen:

```bash
command > output.log 2>&1
```

Das ist wichtig für Skripte, die automatisch laufen und später geprüft werden sollen.

---

## Logdatei im Skript schreiben

Ein Skript kann eigene Logeinträge schreiben.

Beispiel:

```bash
#!/bin/bash

logfile="script.log"

echo "$(date) - Skript gestartet" >> "$logfile"
hostname >> "$logfile"
df -h >> "$logfile"
echo "$(date) - Skript beendet" >> "$logfile"
```

Das ist besser als nur Ausgaben im Terminal, wenn das Skript automatisch läuft.

---

## set -e

Mit `set -e` beendet sich ein Skript, wenn ein Befehl fehlschlägt.

Beispiel:

```bash
#!/bin/bash
set -e

sudo apt update
sudo apt install nginx
systemctl status nginx
```

Wenn ein Befehl fehlschlägt, läuft das Skript nicht einfach blind weiter.

Das kann sicherer sein, aber man muss verstehen, wann ein Fehler wirklich das Skript stoppen soll.

---

## set -u

Mit `set -u` wird die Nutzung nicht gesetzter Variablen als Fehler behandelt.

Beispiel:

```bash
#!/bin/bash
set -u

echo "$username"
```

Wenn `username` nicht gesetzt ist, bricht das Skript ab.

Das hilft, Tippfehler in Variablennamen zu finden.

---

## set -euo pipefail

In vielen Skripten sieht man:

```bash
set -euo pipefail
```

Bedeutung:

| Option     | Bedeutung                                     |
| ---------- | --------------------------------------------- |
| `-e`       | bei Fehler abbrechen                          |
| `-u`       | nicht gesetzte Variablen als Fehler behandeln |
| `pipefail` | Fehler in Pipes besser erkennen               |

Das ist für robustere Skripte nützlich.

Für Anfänger sollte man aber verstehen, was diese Optionen bewirken, bevor man sie überall nutzt.

---

## Prüfen, ob Skript als Root läuft

Manche Skripte brauchen Root-Rechte.

Beispiel:

```bash
#!/bin/bash

if [ "$EUID" -ne 0 ]; then
  echo "Bitte mit sudo ausführen."
  exit 1
fi

echo "Root-Rechte vorhanden."
```

`$EUID` enthält die effektive Benutzer-ID.

Root hat die ID:

```text
0
```

Das ist nützlich bei Installations- oder Admin-Skripten.

---

## Dienste mit Skript prüfen

Beispiel:

```bash
#!/bin/bash

services=("ssh" "docker" "cron")

for service in "${services[@]}"; do
  if systemctl is-active --quiet "$service"; then
    echo "$service läuft."
  else
    echo "$service läuft nicht."
  fi
done
```

Dieses Skript prüft mehrere Dienste.

Das ist eine typische FISI-Aufgabe.

---

## Einfacher Systemreport

Beispiel:

```bash
#!/bin/bash

echo "===== Systemreport ====="
echo "Hostname:"
hostname

echo
echo "Uptime:"
uptime

echo
echo "Speicherplatz:"
df -h

echo
echo "RAM:"
free -h

echo
echo "Fehlgeschlagene Dienste:"
systemctl --failed
```

So ein Skript kann für Lernumgebungen, Serverchecks oder Dokumentation nützlich sein.

---

## Einfaches Backup-Skript

Beispiel:

```bash
#!/bin/bash

source_dir="$HOME/Documents"
backup_dir="$HOME/backups"
date_string=$(date +%Y-%m-%d)

mkdir -p "$backup_dir"

tar -czf "$backup_dir/documents-$date_string.tar.gz" "$source_dir"

echo "Backup erstellt: $backup_dir/documents-$date_string.tar.gz"
```

Dieses Skript:

- setzt Quellordner
- setzt Backupordner
- erzeugt ein Datum
- erstellt den Backupordner
- erstellt ein komprimiertes Archiv

Wichtig:

Ein Backup ist erst wirklich gut, wenn man auch das Wiederherstellen getestet hat.

---

## Logdatei nach Fehlern durchsuchen

Beispiel:

```bash
#!/bin/bash

logfile="/var/log/syslog"

if [ ! -f "$logfile" ]; then
  echo "Logdatei nicht gefunden: $logfile"
  exit 1
fi

grep -Ei "error|failed|denied" "$logfile" | tail -n 20
```

Dieses Skript zeigt die letzten auffälligen Meldungen aus einer Logdatei.

Das kann bei Fehlersuche helfen.

---

## Netzwerkprüfung als Skript

Beispiel:

```bash
#!/bin/bash

echo "IP-Adressen:"
ip a

echo
echo "Routing:"
ip route

echo
echo "Gateway-Test:"
ping -c 3 192.168.178.1

echo
echo "DNS-Test:"
ping -c 3 google.com
```

Wichtig:

Die Gateway-IP muss zum eigenen Netzwerk passen.

In einem anderen Netzwerk wäre `192.168.178.1` vielleicht falsch.

---

## Cronjobs

Ein Shell-Skript kann regelmäßig über Cron gestartet werden.

Crontab bearbeiten:

```bash
crontab -e
```

Beispiel:

```cron
0 8 * * * /home/bilgin/scripts/check-system.sh >> /home/bilgin/scripts/check-system.log 2>&1
```

Das bedeutet:

- jeden Tag um 08:00 Uhr
- Skript ausführen
- Ausgabe in Logdatei schreiben
- Fehlerausgabe ebenfalls in Logdatei schreiben

Cron ist wichtig für regelmäßige Aufgaben.

---

## Cron-Syntax

Cron nutzt fünf Zeitfelder.

```text
Minute Stunde Tag-des-Monats Monat Wochentag Befehl
```

Beispiele:

| Cron-Ausdruck  | Bedeutung              |
| -------------- | ---------------------- |
| `0 8 * * *`    | jeden Tag um 08:00     |
| `*/15 * * * *` | alle 15 Minuten        |
| `0 2 * * 1`    | jeden Montag um 02:00  |
| `30 18 * * 5`  | jeden Freitag um 18:30 |

Cronjobs sollten immer mit vollständigen Pfaden arbeiten, weil die Umgebung anders sein kann als im normalen Terminal.

---

## Absolute Pfade in Skripten

In Skripten sind absolute Pfade oft sicherer.

Beispiel:

```bash
/home/bilgin/scripts/check-system.sh
```

Statt nur:

```bash
check-system.sh
```

Besonders bei Cron ist das wichtig.

Auch Programme können mit vollem Pfad genutzt werden.

Pfad herausfinden:

```bash
which bash
which tar
which python3
```

Beispiel:

```bash
/usr/bin/tar
/usr/bin/python3
```

---

## Fehler in Skripten finden

Skript mit Bash ausführen:

```bash
bash script.sh
```

Syntax prüfen, ohne auszuführen:

```bash
bash -n script.sh
```

Debug-Modus:

```bash
bash -x script.sh
```

`bash -x` zeigt, welche Befehle ausgeführt werden.

Das ist sehr hilfreich, wenn ein Skript nicht macht, was man erwartet.

---

## shellcheck

`shellcheck` ist ein Werkzeug zur Prüfung von Shell-Skripten.

Installation:

```bash
sudo apt install shellcheck
```

Prüfen:

```bash
shellcheck script.sh
```

`shellcheck` findet viele typische Fehler:

- fehlende Anführungszeichen
- unsichere Variablen
- falsche Syntax
- mögliche Probleme bei Schleifen
- unklare Umleitungen

Für bessere Skripte ist `shellcheck` sehr hilfreich.

---

## Skripte sicher schreiben

Wichtige Regeln:

- Variablen meistens in Anführungszeichen setzen
- Eingaben prüfen
- Pfade genau kontrollieren
- nicht blind `sudo` nutzen
- nicht blind `rm -rf` nutzen
- Backups vor Änderungen erstellen
- Fehlerausgaben speichern
- Exit-Codes beachten
- Skripte mit Testdaten ausprobieren
- gefährliche Befehle erst mit `echo` testen
- keine Passwörter im Skript speichern

Beispiel für gefährliches Muster:

```bash
rm -rf "$target"
```

Wenn `$target` leer oder falsch ist, kann das sehr gefährlich werden.

Besser vorher prüfen:

```bash
if [ -z "$target" ]; then
  echo "Fehler: target ist leer."
  exit 1
fi
```

---

## Keine Passwörter im Skript speichern

Passwörter oder geheime Tokens sollten nicht direkt im Skript stehen.

Schlecht:

```bash
password="meinpasswort123"
```

Probleme:

- Skript kann in Git landen
- andere Benutzer können Datei lesen
- Passwort bleibt in Backups
- Passwort kann versehentlich veröffentlicht werden

Besser:

- Umgebungsvariablen nutzen
- Secret-Management nutzen
- Rechte der Datei stark einschränken
- keine geheimen Daten in GitHub hochladen

Für öffentliche Repositories sollten keine echten Zugangsdaten enthalten sein.

---

## Skripte und GitHub

Wenn Skripte in GitHub veröffentlicht werden, sollten sie sauber und ungefährlich sein.

Nicht veröffentlichen:

- Passwörter
- private SSH-Schlüssel
- interne IP-Adressen, wenn sie sensibel sind
- Kundendaten
- echte Tokens
- private Hostnamen
- produktive Zugangsdaten
- geheime Konfigurationen

Gut veröffentlichen:

- Beispielskripte
- Platzhalterwerte
- klare README-Erklärung
- sichere Standardwerte
- Kommentare
- Hinweise zur Nutzung
- keine echten privaten Daten

---

## Typische Fehler

| Fehler                             | Problem                                                |
| ---------------------------------- | ------------------------------------------------------ |
| Leerzeichen bei Variablenzuweisung | Bash interpretiert es falsch                           |
| Variablen ohne Anführungszeichen   | Probleme bei Leerzeichen und Sonderzeichen             |
| fehlendes `chmod +x`               | Skript startet nicht direkt                            |
| fehlender Shebang                  | System weiß nicht sicher, womit es starten soll        |
| relative Pfade in Cronjobs         | Skript findet Dateien nicht                            |
| Exit-Codes ignorieren              | Skript läuft trotz Fehler weiter                       |
| `rm -rf` ohne Prüfung              | hohes Risiko für Datenverlust                          |
| Passwörter im Skript               | Sicherheitsproblem                                     |
| keine Logs schreiben               | Fehler bei automatischen Läufen schwer nachvollziehbar |
| Skript nicht mit ShellCheck prüfen | typische Fehler bleiben unentdeckt                     |

---

## Praktische Beispiele

### Beispiel 1: Systemstatus speichern

```bash
#!/bin/bash

report="$HOME/system-report.txt"

echo "Systemreport" > "$report"
date >> "$report"
hostname >> "$report"
uptime >> "$report"
df -h >> "$report"
free -h >> "$report"

echo "Report gespeichert unter: $report"
```

### Beispiel 2: Dienst prüfen

```bash
#!/bin/bash

service="$1"

if [ -z "$service" ]; then
  echo "Nutzung: $0 dienstname"
  exit 1
fi

if systemctl is-active --quiet "$service"; then
  echo "$service läuft."
else
  echo "$service läuft nicht."
  exit 1
fi
```

Start:

```bash
./check-service.sh ssh
```

### Beispiel 3: Backup erstellen

```bash
#!/bin/bash

source_dir="$1"
backup_dir="$HOME/backups"
date_string=$(date +%Y-%m-%d_%H-%M-%S)

if [ -z "$source_dir" ]; then
  echo "Nutzung: $0 /pfad/zum/ordner"
  exit 1
fi

if [ ! -d "$source_dir" ]; then
  echo "Fehler: Ordner existiert nicht: $source_dir"
  exit 1
fi

mkdir -p "$backup_dir"

tar -czf "$backup_dir/backup-$date_string.tar.gz" "$source_dir"

echo "Backup erstellt."
```

### Beispiel 4: Logs nach Fehlern prüfen

```bash
#!/bin/bash

journalctl -b -p err -n 50
```

Dieses Skript zeigt die letzten 50 Fehlermeldungen seit dem aktuellen Boot.

---

## Nützliche Befehle

| Befehl                 | Bedeutung                           |
| ---------------------- | ----------------------------------- |
| `nano script.sh`       | Skript bearbeiten                   |
| `chmod +x script.sh`   | Skript ausführbar machen            |
| `./script.sh`          | Skript aus aktuellem Ordner starten |
| `bash script.sh`       | Skript mit Bash starten             |
| `bash -n script.sh`    | Syntax prüfen                       |
| `bash -x script.sh`    | Debug-Ausgabe aktivieren            |
| `echo`                 | Text ausgeben                       |
| `read`                 | Eingabe lesen                       |
| `exit`                 | Skript beenden                      |
| `test` oder `[ ]`      | Bedingungen prüfen                  |
| `grep`                 | Text suchen                         |
| `find`                 | Dateien suchen                      |
| `tar`                  | Archive erstellen                   |
| `date`                 | Datum ausgeben                      |
| `hostname`             | Hostname anzeigen                   |
| `systemctl`            | Dienste prüfen                      |
| `journalctl`           | Logs lesen                          |
| `crontab -e`           | Cronjobs bearbeiten                 |
| `shellcheck script.sh` | Skript prüfen                       |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Shell Scripting eine wichtige Fähigkeit im Linux-Alltag.

In der Praxis bedeutet das:

- wiederkehrende Aufgaben automatisieren
- Systeminformationen sammeln
- einfache Reports erstellen
- Backups vorbereiten
- Logs auswerten
- Dienste prüfen
- Paketinstallationen automatisieren
- Netzwerkchecks durchführen
- Cronjobs einrichten
- Fehlerausgaben dokumentieren
- sichere Skripte schreiben
- Skripte in Git verwalten

Ein guter FISI nutzt Shell-Skripte nicht blind, sondern schreibt sie nachvollziehbar, testbar und sicher.

---

## Kurze Zusammenfassung

Shell Scripting bedeutet, Linux-Befehle in Skripten zu automatisieren.

Wichtige Grundlagen sind Shebang, Ausführungsrechte, Variablen, Anführungszeichen, Parameter, if-Bedingungen, Schleifen, Funktionen, Exit-Codes, Pipes, Umleitungen, Cronjobs und Logging.

Für FISI ist Shell Scripting wichtig, weil viele Aufgaben im Linux- und Serverbetrieb wiederkehrend sind und mit Skripten sauber automatisiert werden können.
