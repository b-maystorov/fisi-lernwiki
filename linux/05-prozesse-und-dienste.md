# 5. Prozesse und Dienste

In diesem Kapitel geht es um Prozesse und Dienste unter Linux.

Ein Linux-System führt ständig Programme aus. Manche Programme laufen direkt sichtbar im Terminal oder als Anwendung. Andere laufen im Hintergrund als Dienste und stellen wichtige Funktionen bereit, zum Beispiel SSH, Webserver, Datenbanken, Docker oder Cronjobs.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr wichtig, weil viele Serverprobleme mit Prozessen oder Diensten zusammenhängen. Ein FISI muss prüfen können, ob ein Dienst läuft, warum er nicht startet, welche Logs es gibt, welcher Prozess Ressourcen verbraucht und welche Ports geöffnet sind.

---

## Kurz erklärt

Ein Prozess ist ein laufendes Programm.

Ein Dienst ist ein Programm, das meistens im Hintergrund läuft und eine bestimmte Aufgabe erfüllt.

Wichtige Themen sind:

- Prozesse anzeigen
- Prozess-ID verstehen
- laufende Programme überwachen
- Prozesse beenden
- Ressourcenverbrauch prüfen
- Dienste mit systemd verwalten
- systemctl nutzen
- journalctl nutzen
- Dienste starten, stoppen und neu starten
- Autostart von Diensten verwalten
- offene Ports prüfen
- Fehler bei Diensten analysieren
- Logs auswerten

Prozesse und Dienste gehören zu den wichtigsten Grundlagen der Linux-Administration.

---

## Was ist ein Prozess?

Ein Prozess ist ein Programm, das gerade ausgeführt wird.

Beispiele:

- Terminal
- Browser
- Python-Skript
- SSH-Verbindung
- Webserver
- Datenbank
- Docker-Containerprozess
- Backup-Skript
- Paketmanager

Jeder Prozess hat eine Prozess-ID, kurz PID.

Die PID ist eine eindeutige Nummer für einen laufenden Prozess.

Beispiel:

```bash
ps
```

Mögliche Ausgabe:

```text
PID TTY          TIME CMD
1234 pts/0    00:00:00 bash
1250 pts/0    00:00:00 ps
```

Hier sind `bash` und `ps` laufende Prozesse.

---

## Prozess-ID und Parent-Prozess

Jeder Prozess hat eine PID.

Viele Prozesse haben außerdem einen Parent-Prozess. Das ist der Prozess, der sie gestartet hat.

Wichtige Begriffe:

| Begriff        | Bedeutung                                              |
| -------------- | ------------------------------------------------------ |
| PID            | Prozess-ID                                             |
| PPID           | Parent Process ID                                      |
| Prozess        | laufendes Programm                                     |
| Parent-Prozess | Prozess, der einen anderen Prozess gestartet hat       |
| Child-Prozess  | Prozess, der von einem anderen Prozess gestartet wurde |

Beispiel:

Eine Shell startet den Befehl `ls`.
Dann ist die Shell der Parent-Prozess und `ls` der Child-Prozess.

Prozessbeziehungen helfen zu verstehen, warum bestimmte Prozesse laufen und wodurch sie gestartet wurden.

---

## Prozesse anzeigen mit `ps`

Mit `ps` kann man laufende Prozesse anzeigen.

Einfach:

```bash
ps
```

Alle Prozesse anzeigen:

```bash
ps aux
```

Häufige Bedeutung der Optionen:

| Option | Bedeutung                                     |
| ------ | --------------------------------------------- |
| `a`    | Prozesse aller Benutzer mit Terminal anzeigen |
| `u`    | benutzerfreundliche Ausgabe                   |
| `x`    | auch Prozesse ohne Terminal anzeigen          |

`ps aux` ist einer der wichtigsten Befehle zur Prozessanalyse.

---

## Ausgabe von `ps aux` verstehen

Beispiel:

```text
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1 167000 12000 ?        Ss   09:00   0:02 /sbin/init
bilgin    2450  0.1  0.3  90000 25000 pts/0    S+   10:00   0:00 python3 app.py
```

Wichtige Spalten:

| Spalte  | Bedeutung                             |
| ------- | ------------------------------------- |
| USER    | Benutzer, unter dem der Prozess läuft |
| PID     | Prozess-ID                            |
| %CPU    | CPU-Verbrauch                         |
| %MEM    | RAM-Verbrauch                         |
| TTY     | Terminal                              |
| STAT    | Prozessstatus                         |
| START   | Startzeit                             |
| TIME    | verbrauchte CPU-Zeit                  |
| COMMAND | gestarteter Befehl                    |

Diese Informationen helfen, Prozesse zu erkennen und Probleme einzugrenzen.

---

## Prozessstatus

Prozesse können verschiedene Zustände haben.

Wichtige Statuszeichen:

| Status | Bedeutung                                                      |
| ------ | -------------------------------------------------------------- |
| `R`    | running, Prozess läuft gerade                                  |
| `S`    | sleeping, Prozess wartet                                       |
| `D`    | uninterruptible sleep, wartet auf I/O                          |
| `T`    | stopped, Prozess ist angehalten                                |
| `Z`    | zombie, Prozess ist beendet, aber noch nicht sauber aufgeräumt |
| `s`    | Session Leader                                                 |
| `+`    | Prozess gehört zum Vordergrundprozess im Terminal              |

Ein Prozess im Status `S` ist nicht automatisch problematisch. Viele Dienste warten die meiste Zeit auf Arbeit.

Ein Zombie-Prozess kann auf ein Problem mit dem Parent-Prozess hinweisen.

---

## Prozesse suchen mit `grep`

Wenn viele Prozesse laufen, kann man mit `grep` filtern.

Beispiel:

```bash
ps aux | grep ssh
```

Das zeigt Prozesse, die `ssh` im Namen oder Befehl enthalten.

Beispiel für Python:

```bash
ps aux | grep python
```

Wichtig:

Der `grep`-Befehl selbst erscheint manchmal ebenfalls in der Ausgabe.

Das ist normal, weil auch `grep` ein laufender Prozess ist.

---

## Prozesse mit `pgrep` finden

`pgrep` sucht Prozesse nach Namen und gibt PIDs aus.

Beispiel:

```bash
pgrep ssh
```

Mit Details:

```bash
pgrep -a ssh
```

Beispielausgabe:

```text
920 sshd: /usr/sbin/sshd -D
```

`pgrep -a` ist praktisch, weil es PID und Befehl anzeigt.

---

## Prozesse live anzeigen mit `top`

Mit `top` kann man Prozesse live beobachten.

```bash
top
```

`top` zeigt unter anderem:

- CPU-Auslastung
- RAM-Nutzung
- laufende Prozesse
- Last des Systems
- Prozess-IDs
- Benutzer
- Laufzeit
- Ressourcenverbrauch

Wichtige Tasten in `top`:

| Taste | Bedeutung          |
| ----- | ------------------ |
| `q`   | beenden            |
| `P`   | nach CPU sortieren |
| `M`   | nach RAM sortieren |
| `k`   | Prozess beenden    |
| `h`   | Hilfe anzeigen     |

`top` ist hilfreich, wenn ein System langsam ist oder ein Prozess zu viele Ressourcen nutzt.

---

## htop

`htop` ist eine komfortablere Alternative zu `top`.

Starten:

```bash
htop
```

Falls nicht installiert:

```bash
sudo apt install htop
```

Vorteile:

- übersichtlichere Darstellung
- einfachere Bedienung
- Prozesse leichter sortieren
- Prozesse einfacher beenden
- CPU-Kerne sichtbar
- RAM und Swap gut erkennbar

`htop` ist auf Servern sehr nützlich, aber nicht immer standardmäßig installiert.

---

## Prozesse als Baum anzeigen

Mit `pstree` sieht man Prozesse als Baumstruktur.

```bash
pstree
```

Mit PIDs:

```bash
pstree -p
```

Das zeigt, welche Prozesse andere Prozesse gestartet haben.

Beispiel:

```text
systemd(1)─┬─sshd(920)
           ├─cron(700)
           └─docker(1100)
```

Das hilft zu verstehen, welche Dienste und Prozesse zusammenhängen.

---

## Prozesse beenden mit `kill`

Mit `kill` sendet man ein Signal an einen Prozess.

Normales Beenden:

```bash
kill PID
```

Beispiel:

```bash
kill 2450
```

Wenn ein Prozess nicht reagiert:

```bash
kill -9 PID
```

Wichtig:

`kill -9` erzwingt das Beenden. Das sollte man nicht als erste Lösung nutzen.

Besser zuerst normal beenden und nur bei Bedarf stärker eingreifen.

---

## Signale

`kill` sendet Signale an Prozesse.

Wichtige Signale:

| Signal  | Nummer | Bedeutung                                      |
| ------- | -----: | ---------------------------------------------- |
| SIGTERM |     15 | Prozess soll sich sauber beenden               |
| SIGKILL |      9 | Prozess wird sofort beendet                    |
| SIGHUP  |      1 | Konfiguration neu laden oder Terminal getrennt |
| SIGINT  |      2 | Unterbrechung, ähnlich Ctrl + C                |

Standard bei `kill PID` ist meistens SIGTERM.

SIGTERM gibt dem Prozess die Möglichkeit, sauber aufzuräumen.

SIGKILL beendet sofort und kann zu unsauberen Zuständen führen.

---

## Prozess mit Namen beenden

Mit `pkill` kann man Prozesse nach Namen beenden.

Beispiel:

```bash
pkill python3
```

Vorsicht:

Dieser Befehl kann mehrere Prozesse treffen.

Vorher besser prüfen:

```bash
pgrep -a python3
```

Dann gezielt entscheiden.

Bei produktiven Systemen sollte man sehr vorsichtig sein, bevor man Prozesse beendet.

---

## Prozess im Vordergrund und Hintergrund

Ein Befehl läuft normalerweise im Vordergrund.

Beispiel:

```bash
sleep 60
```

Das Terminal ist blockiert, bis der Befehl fertig ist.

Mit `&` startet man einen Befehl im Hintergrund:

```bash
sleep 60 &
```

Aktuelle Jobs anzeigen:

```bash
jobs
```

Einen Prozess in den Vordergrund holen:

```bash
fg
```

Das ist nützlich bei längeren Befehlen, aber für echte Dienste nutzt man besser systemd.

---

## Ctrl + C und Ctrl + Z

Wichtige Tastenkombinationen:

| Tastenkombination | Bedeutung                                      |
| ----------------- | ---------------------------------------------- |
| Ctrl + C          | laufenden Vordergrundprozess abbrechen         |
| Ctrl + Z          | Prozess anhalten                               |
| `fg`              | angehaltenen Prozess fortsetzen im Vordergrund |
| `bg`              | angehaltenen Prozess im Hintergrund fortsetzen |

Beispiel:

Ein Befehl läuft zu lange.
Mit Ctrl + C kann man ihn abbrechen.

Ctrl + Z stoppt den Prozess nur. Er ist dann nicht sauber beendet.

---

## Ressourcenverbrauch prüfen

Bei Performanceproblemen sollte man CPU, RAM und Speicher prüfen.

Wichtige Befehle:

```bash
top
htop
free -h
df -h
du -sh *
ps aux --sort=-%mem
ps aux --sort=-%cpu
```

Bedeutung:

| Befehl                | Aufgabe                                 |
| --------------------- | --------------------------------------- |
| `free -h`             | Arbeitsspeicher anzeigen                |
| `df -h`               | Speicherplatz der Dateisysteme anzeigen |
| `du -sh *`            | Größe von Dateien und Ordnern anzeigen  |
| `ps aux --sort=-%mem` | Prozesse nach RAM sortieren             |
| `ps aux --sort=-%cpu` | Prozesse nach CPU sortieren             |

Ein langsames System kann viele Ursachen haben: CPU, RAM, volle Festplatte, I/O-Probleme, Netzwerk oder ein fehlerhafter Dienst.

---

## Nice-Wert und Priorität

Linux kann Prozessen unterschiedliche Prioritäten geben.

Der Nice-Wert beeinflusst, wie freundlich ein Prozess gegenüber anderen Prozessen ist.

Bereich:

```text
-20 bis 19
```

Bedeutung:

| Nice-Wert | Bedeutung           |
| --------: | ------------------- |
|       -20 | sehr hohe Priorität |
|         0 | normal              |
|        19 | niedrige Priorität  |

Prozess mit niedriger Priorität starten:

```bash
nice -n 10 command
```

Priorität eines laufenden Prozesses ändern:

```bash
renice 10 -p PID
```

Für normale Administration braucht man das nicht ständig, aber es ist gut zu wissen.

---

## Was ist ein Dienst?

Ein Dienst ist ein Programm, das meist im Hintergrund läuft und eine Aufgabe bereitstellt.

Beispiele:

| Dienst           | Aufgabe                     |
| ---------------- | --------------------------- |
| SSH              | Remote-Zugriff per Terminal |
| Nginx            | Webserver                   |
| Apache           | Webserver                   |
| PostgreSQL       | Datenbankserver             |
| MariaDB          | Datenbankserver             |
| Docker           | Container verwalten         |
| Cron             | zeitgesteuerte Aufgaben     |
| NetworkManager   | Netzwerkverwaltung          |
| systemd-resolved | DNS-Auflösung               |
| rsyslog          | Systemlogging               |

Dienste sind besonders wichtig auf Servern.

Wenn ein Dienst nicht läuft, funktioniert oft eine zentrale Funktion nicht.

---

## systemd

Viele moderne Linux-Distributionen nutzen `systemd`.

`systemd` ist ein System- und Dienstmanager.

Er ist unter anderem verantwortlich für:

- Systemstart
- Dienste starten
- Dienste stoppen
- Dienste überwachen
- Abhängigkeiten zwischen Diensten
- Logs über journald
- Targets
- Timer
- Mounts
- automatische Neustarts

Der erste Prozess auf vielen Linux-Systemen ist `systemd`.

Prüfen:

```bash
ps -p 1 -o comm=
```

Mögliche Ausgabe:

```text
systemd
```

Das bedeutet: systemd läuft als Prozess mit PID 1.

---

## systemctl

`systemctl` ist das wichtigste Werkzeug zur Verwaltung von systemd-Diensten.

Status prüfen:

```bash
systemctl status ssh
```

Dienst starten:

```bash
sudo systemctl start ssh
```

Dienst stoppen:

```bash
sudo systemctl stop ssh
```

Dienst neu starten:

```bash
sudo systemctl restart ssh
```

Dienst beim Booten automatisch starten:

```bash
sudo systemctl enable ssh
```

Autostart deaktivieren:

```bash
sudo systemctl disable ssh
```

`systemctl` gehört zu den wichtigsten Linux-Befehlen für FISI.

---

## Dienststatus verstehen

Beispiel:

```bash
systemctl status ssh
```

Mögliche Ausgabe enthält:

```text
Active: active (running)
Loaded: loaded
Main PID: 920
```

Wichtige Informationen:

| Feld     | Bedeutung                      |
| -------- | ------------------------------ |
| Loaded   | Unit-Datei wurde geladen       |
| Active   | aktueller Zustand              |
| Main PID | Hauptprozess des Dienstes      |
| Docs     | Dokumentation, falls vorhanden |
| Logs     | letzte Logzeilen               |

Wichtige Zustände:

| Zustand          | Bedeutung                 |
| ---------------- | ------------------------- |
| active (running) | Dienst läuft              |
| inactive (dead)  | Dienst läuft nicht        |
| failed           | Dienst ist fehlgeschlagen |
| activating       | Dienst startet gerade     |
| deactivating     | Dienst stoppt gerade      |

Bei `failed` sollte man Logs mit `journalctl` prüfen.

---

## start, stop, restart und reload

Wichtige Unterschiede:

| Befehl    | Bedeutung                                         |
| --------- | ------------------------------------------------- |
| `start`   | Dienst starten                                    |
| `stop`    | Dienst stoppen                                    |
| `restart` | Dienst stoppen und neu starten                    |
| `reload`  | Konfiguration neu laden, ohne kompletten Neustart |
| `status`  | Zustand anzeigen                                  |

Beispiele:

```bash
sudo systemctl restart nginx
sudo systemctl reload nginx
```

`reload` ist oft schonender, wenn ein Dienst es unterstützt.

Nicht jeder Dienst unterstützt `reload`.

Prüfen kann man den Status danach:

```bash
systemctl status nginx
```

---

## enable und disable

`enable` und `disable` steuern den Autostart beim Systemstart.

Autostart aktivieren:

```bash
sudo systemctl enable nginx
```

Autostart deaktivieren:

```bash
sudo systemctl disable nginx
```

Wichtig:

`enable` startet den Dienst nicht sofort.
Es sorgt nur dafür, dass er beim Booten automatisch startet.

Wenn man beides möchte:

```bash
sudo systemctl enable --now nginx
```

Das aktiviert Autostart und startet den Dienst direkt.

---

## is-active und is-enabled

Man kann Dienste auch gezielt abfragen.

Prüfen, ob Dienst läuft:

```bash
systemctl is-active ssh
```

Prüfen, ob Autostart aktiv ist:

```bash
systemctl is-enabled ssh
```

Beispiele für Ausgaben:

```text
active
inactive
enabled
disabled
```

Diese Befehle sind nützlich für Skripte und schnelle Prüfungen.

---

## Alle Dienste anzeigen

Alle geladenen Dienste anzeigen:

```bash
systemctl list-units --type=service
```

Auch inaktive Dienste anzeigen:

```bash
systemctl list-units --type=service --all
```

Fehlgeschlagene Dienste anzeigen:

```bash
systemctl --failed
```

Das ist besonders nützlich nach einem Neustart oder bei Systemproblemen.

Wenn ein Server Fehler hat, ist `systemctl --failed` oft ein guter Startpunkt.

---

## Unit-Dateien

systemd verwaltet sogenannte Units.

Eine Service-Unit beschreibt einen Dienst.

Typische Orte:

```text
/etc/systemd/system
/lib/systemd/system
/usr/lib/systemd/system
```

Wichtiger Unterschied:

| Pfad                      | Bedeutung                                    |
| ------------------------- | -------------------------------------------- |
| `/etc/systemd/system`     | eigene oder angepasste Units                 |
| `/lib/systemd/system`     | Units aus Paketen auf Debian/Ubuntu          |
| `/usr/lib/systemd/system` | Units aus Paketen auf manchen Distributionen |

Eigene Anpassungen gehören meistens nach `/etc/systemd/system`.

---

## Beispiel einer Service-Unit

Eine einfache Service-Datei kann so aussehen:

```ini
[Unit]
Description=Example Service
After=network.target

[Service]
ExecStart=/usr/bin/python3 /opt/example/app.py
Restart=on-failure
User=exampleuser

[Install]
WantedBy=multi-user.target
```

Bedeutung:

| Abschnitt   | Aufgabe                         |
| ----------- | ------------------------------- |
| `[Unit]`    | Beschreibung und Abhängigkeiten |
| `[Service]` | Startbefehl und Verhalten       |
| `[Install]` | Autostart-Ziel                  |

Service-Dateien sind wichtig, wenn eigene Skripte oder Anwendungen als Dienst laufen sollen.

---

## daemon-reload

Wenn man systemd-Unit-Dateien ändert oder neu erstellt, muss systemd die Dateien neu einlesen.

```bash
sudo systemctl daemon-reload
```

Danach kann man den Dienst starten oder neu starten.

Beispiel:

```bash
sudo systemctl daemon-reload
sudo systemctl restart example.service
```

Ohne `daemon-reload` erkennt systemd Änderungen an Unit-Dateien möglicherweise nicht.

---

## journalctl

`journalctl` zeigt Logs aus dem systemd-Journal.

Alle Logs anzeigen:

```bash
journalctl
```

Live mitlesen:

```bash
journalctl -f
```

Logs eines Dienstes anzeigen:

```bash
journalctl -u ssh
```

Logs seit dem letzten Boot:

```bash
journalctl -b
```

Fehler mit mehr Kontext anzeigen:

```bash
journalctl -xe
```

`journalctl` ist eines der wichtigsten Werkzeuge bei der Fehlersuche unter systemd.

---

## Logs eines Dienstes prüfen

Wenn ein Dienst nicht startet:

```bash
systemctl status dienstname
journalctl -u dienstname
```

Beispiel:

```bash
systemctl status ssh
journalctl -u ssh
```

Nur aktuelle Logs:

```bash
journalctl -u ssh -n 50
```

Live beobachten:

```bash
journalctl -u ssh -f
```

Damit sieht man direkt, was passiert, wenn ein Dienst startet, stoppt oder Fehler schreibt.

---

## Logs nach Zeit filtern

`journalctl` kann nach Zeit filtern.

Beispiele:

```bash
journalctl --since "today"
journalctl --since "1 hour ago"
journalctl --since "2026-08-18 10:00"
journalctl --until "2026-08-18 12:00"
```

Für einen Dienst:

```bash
journalctl -u nginx --since "30 minutes ago"
```

Das ist sehr nützlich, wenn ein Fehler zu einem bestimmten Zeitpunkt aufgetreten ist.

---

## Dienste und offene Ports

Viele Dienste öffnen Netzwerkports.

Beispiele:

| Dienst          | typischer Port |
| --------------- | -------------: |
| SSH             |             22 |
| HTTP            |             80 |
| HTTPS           |            443 |
| PostgreSQL      |           5432 |
| MySQL / MariaDB |           3306 |
| DNS             |             53 |

Offene Ports anzeigen:

```bash
ss -tulpen
```

Bedeutung der Optionen:

| Option | Bedeutung                |
| ------ | ------------------------ |
| `-t`   | TCP                      |
| `-u`   | UDP                      |
| `-l`   | listening                |
| `-p`   | Prozess anzeigen         |
| `-e`   | erweiterte Informationen |
| `-n`   | numerische Ausgabe       |

Wenn ein Dienst nicht erreichbar ist, sollte man prüfen, ob er überhaupt auf einem Port lauscht.

---

## Dienst läuft, aber ist nicht erreichbar

Wenn ein Dienst läuft, aber nicht erreichbar ist, kann es mehrere Ursachen geben.

Mögliche Ursachen:

- Dienst lauscht nur auf localhost
- falscher Port
- Firewall blockiert Verbindung
- Dienst läuft auf anderer IP-Adresse
- DNS zeigt auf falsche Adresse
- Netzwerkroute fehlt
- Container-Port ist nicht gemappt
- Anwendung hat interne Fehler
- Zertifikatproblem bei HTTPS

Prüfen:

```bash
systemctl status dienstname
ss -tulpen
ip a
ip route
ping ziel
curl http://localhost:port
journalctl -u dienstname
```

Man sollte nicht nur prüfen, ob der Dienst läuft, sondern auch, ob er erreichbar ist.

---

## Prozesse und Ports verbinden

Mit `ss -tulpen` sieht man, welcher Prozess auf welchem Port lauscht.

Beispiel:

```text
tcp LISTEN 0 128 0.0.0.0:22 0.0.0.0:* users:(("sshd",pid=920,fd=3))
```

Bedeutung:

| Teil         | Bedeutung                               |
| ------------ | --------------------------------------- |
| `tcp`        | Protokoll                               |
| `LISTEN`     | wartet auf Verbindungen                 |
| `0.0.0.0:22` | lauscht auf allen IPv4-Adressen Port 22 |
| `sshd`       | Prozessname                             |
| `pid=920`    | Prozess-ID                              |

Das ist wichtig, um Dienste und Netzwerkverhalten zu verbinden.

---

## Cron-Dienst

Cron führt Aufgaben zeitgesteuert aus.

Der Dienst heißt oft:

```text
cron
```

Status prüfen:

```bash
systemctl status cron
```

Crontab des aktuellen Benutzers bearbeiten:

```bash
crontab -e
```

Crontab anzeigen:

```bash
crontab -l
```

Cron wird genutzt für:

- regelmäßige Skripte
- Backups
- Reports
- Wartungsaufgaben
- Logverarbeitung
- automatische Prüfungen

Cronjobs sind Prozesse, die zu bestimmten Zeiten gestartet werden.

---

## systemd Timer

Neben Cron gibt es systemd Timer.

Timer sind systemd-Units für zeitgesteuerte Aufgaben.

Timer anzeigen:

```bash
systemctl list-timers
```

Timer können Cron ersetzen oder ergänzen.

Sie sind besonders gut integriert mit systemd und journalctl.

Für den Anfang ist Cron oft einfacher, aber systemd Timer sind in modernen Linux-Systemen sehr relevant.

---

## Dienste nach Paketinstallation

Viele Pakete installieren automatisch Dienste.

Beispiel:

```bash
sudo apt install nginx
```

Danach kann man prüfen:

```bash
systemctl status nginx
systemctl is-enabled nginx
ss -tulpen
```

Nicht jede Software startet automatisch nach Installation.

Deshalb sollte man nach Paketinstallationen prüfen:

- ist der Dienst vorhanden?
- läuft er?
- startet er automatisch?
- gibt es offene Ports?
- gibt es Fehlermeldungen?

---

## Dienst startet nicht

Wenn ein Dienst nicht startet, systematisch prüfen:

1. Status prüfen:

```bash
systemctl status dienstname
```

2. Logs prüfen:

```bash
journalctl -u dienstname
```

3. Konfiguration prüfen:

```bash
sudo less /etc/dienstname/config
```

4. Syntax-Test nutzen, wenn verfügbar:

```bash
sudo nginx -t
```

5. Portkonflikt prüfen:

```bash
ss -tulpen
```

6. Rechte prüfen:

```bash
ls -la /pfad/zur/datei
```

7. Speicher prüfen:

```bash
df -h
free -h
```

So findet man die Ursache schneller als durch blindes Neustarten.

---

## Typische Ursachen für Dienstfehler

| Ursache                    | Beispiel                                        |
| -------------------------- | ----------------------------------------------- |
| falsche Konfiguration      | Syntaxfehler in Config-Datei                    |
| Port bereits belegt        | zwei Webserver wollen Port 80 nutzen            |
| fehlende Rechte            | Dienst darf Datei nicht lesen                   |
| fehlender Benutzer         | Service-Unit nutzt nicht existierenden User     |
| fehlende Datei             | Pfad in Konfiguration ist falsch                |
| Datenbank nicht erreichbar | Anwendung startet nicht                         |
| Netzwerkproblem            | Dienst kann externes Ziel nicht erreichen       |
| Speicher voll              | Logs oder Daten können nicht geschrieben werden |
| Paket fehlt                | benötigtes Programm ist nicht installiert       |
| falsche Umgebungsvariable  | Anwendung bekommt keine DB-Adresse              |

Die Fehlermeldung im Journal ist meistens der beste Hinweis.

---

## Dienst neu starten nach Konfigurationsänderung

Nach einer Konfigurationsänderung muss ein Dienst oft neu geladen oder neu gestartet werden.

Beispiel für SSH:

```bash
sudo systemctl restart ssh
```

Beispiel für Nginx mit Syntax-Test:

```bash
sudo nginx -t
sudo systemctl reload nginx
```

Wichtig:

Bei kritischen Diensten wie SSH sollte man vorsichtig sein.

Wenn man SSH falsch konfiguriert und den Dienst neu startet, kann man sich aussperren.

Besser:

- bestehende SSH-Sitzung offen lassen
- Konfiguration testen, wenn möglich
- Backup der Config erstellen
- erst dann neu starten

---

## Dienst deaktivieren oder maskieren

Autostart deaktivieren:

```bash
sudo systemctl disable dienstname
```

Dienst sofort stoppen:

```bash
sudo systemctl stop dienstname
```

Dienst komplett blockieren:

```bash
sudo systemctl mask dienstname
```

Maskierten Dienst wieder freigeben:

```bash
sudo systemctl unmask dienstname
```

`mask` verhindert, dass ein Dienst gestartet wird, auch nicht durch Abhängigkeiten.

Das sollte man bewusst und vorsichtig einsetzen.

---

## Targets

systemd nutzt Targets, um Systemzustände zu beschreiben.

Wichtige Targets:

| Target              | Bedeutung                                     |
| ------------------- | --------------------------------------------- |
| `multi-user.target` | Mehrbenutzerbetrieb ohne grafische Oberfläche |
| `graphical.target`  | Mehrbenutzerbetrieb mit grafischer Oberfläche |
| `rescue.target`     | Rettungsmodus                                 |
| `emergency.target`  | sehr minimaler Notfallmodus                   |

Aktuelles Standard-Target anzeigen:

```bash
systemctl get-default
```

Standard-Target setzen:

```bash
sudo systemctl set-default multi-user.target
```

Targets sind besonders wichtig für Server und Boot-Verhalten.

---

## Dienste beim Bootvorgang analysieren

Bootzeit anzeigen:

```bash
systemd-analyze
```

Langsame Dienste anzeigen:

```bash
systemd-analyze blame
```

Kritische Kette anzeigen:

```bash
systemd-analyze critical-chain
```

Diese Befehle helfen, wenn ein System langsam startet.

Man sieht, welche Dienste besonders viel Zeit benötigen.

---

## Eigene Skripte als Dienst

Man kann eigene Skripte als systemd-Dienst einrichten.

Beispiel:

Ein Skript liegt unter:

```text
/opt/check-system/check-system.sh
```

Service-Datei:

```ini
[Unit]
Description=Check System Script
After=network.target

[Service]
ExecStart=/opt/check-system/check-system.sh
User=bilgin
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Danach:

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now check-system.service
systemctl status check-system.service
```

Das ist praktisch, wenn ein Skript automatisch als Hintergrunddienst laufen soll.

---

## Logs für eigene Dienste

Wenn ein eigener Dienst über systemd läuft, sieht man seine Ausgabe mit:

```bash
journalctl -u check-system.service
```

Live:

```bash
journalctl -u check-system.service -f
```

Das ist ein großer Vorteil von systemd.

Man muss nicht immer selbst Logdateien bauen, weil Standardausgabe und Fehlerausgabe im Journal landen können.

---

## Dienste und Benutzerrechte

Dienste sollten nicht unnötig als Root laufen.

Besser ist oft ein eigener Benutzer für einen Dienst.

Beispiel:

```ini
[Service]
User=appuser
Group=appuser
```

Vorteile:

- weniger Schaden bei Fehlern
- bessere Trennung
- klarere Rechte
- sicherer Betrieb
- bessere Nachvollziehbarkeit

Das Prinzip der minimalen Rechte gilt auch für Dienste.

Ein Webserver oder Skript sollte nur auf die Dateien zugreifen dürfen, die es wirklich braucht.

---

## Dienste und Docker

Docker selbst läuft als Dienst.

Prüfen:

```bash
systemctl status docker
```

Docker-Container sind ebenfalls Prozesse auf dem Host.

Container anzeigen:

```bash
docker ps
```

Prozesse im Container anzeigen:

```bash
docker exec -it containername ps aux
```

Logs anzeigen:

```bash
docker logs containername
```

Bei Docker-Problemen muss man oft beides prüfen:

- Docker-Dienst auf dem Host
- Container selbst
- Containerlogs
- Ports
- Volumes
- Rechte

---

## Prozess oder Dienst?

Nicht jeder Prozess ist ein systemd-Dienst.

Beispiel:

```bash
python3 script.py
```

Das ist ein Prozess, aber nicht automatisch ein Dienst.

Ein Dienst ist meistens über systemd verwaltet.

Prüfen:

```bash
systemctl status dienstname
```

Wenn das nicht existiert, kann der Prozess trotzdem laufen.

Prüfen:

```bash
ps aux | grep script.py
```

Unterschied:

| Prozess                        | Dienst                               |
| ------------------------------ | ------------------------------------ |
| laufendes Programm             | verwalteter Hintergrundprozess       |
| kann manuell gestartet sein    | meist durch systemd gestartet        |
| keine automatische Verwaltung  | start, stop, restart, enable möglich |
| Logs eventuell nur im Terminal | Logs oft über journalctl             |

---

## Systematisch prüfen: Dienstproblem

Ein praktisches Vorgehen:

1. Dienststatus prüfen:

```bash
systemctl status dienstname
```

2. Fehlgeschlagene Dienste anzeigen:

```bash
systemctl --failed
```

3. Logs prüfen:

```bash
journalctl -u dienstname -n 100
```

4. Offene Ports prüfen:

```bash
ss -tulpen
```

5. Prozesse prüfen:

```bash
ps aux | grep dienstname
```

6. Konfiguration prüfen.

7. Rechte prüfen.

8. Speicher und Ressourcen prüfen:

```bash
df -h
free -h
top
```

Dieses Vorgehen ist besser als nur mehrfach `restart` auszuführen.

---

## Praktische Beispiele

### Beispiel 1: SSH-Dienst prüfen

```bash
systemctl status ssh
journalctl -u ssh -n 50
ss -tulpen | grep :22
```

Damit prüft man:

- läuft SSH?
- gibt es Fehlermeldungen?
- lauscht SSH auf Port 22?

### Beispiel 2: Webserver startet nicht

```bash
systemctl status nginx
journalctl -u nginx
sudo nginx -t
ss -tulpen | grep :80
```

Mögliche Ursachen:

- Fehler in Nginx-Konfiguration
- Port 80 ist bereits belegt
- Datei oder Zertifikat fehlt
- Rechteproblem

### Beispiel 3: System ist langsam

```bash
top
free -h
df -h
ps aux --sort=-%cpu | head
ps aux --sort=-%mem | head
```

Damit prüft man:

- CPU-Verbrauch
- RAM-Verbrauch
- Speicherplatz
- auffällige Prozesse

### Beispiel 4: Docker läuft nicht

```bash
systemctl status docker
journalctl -u docker -n 100
docker ps
```

Damit prüft man:

- läuft der Docker-Dienst?
- gibt es Docker-Fehler?
- laufen Container?

---

## Typische Fehler

| Fehler                                       | Problem                              |
| -------------------------------------------- | ------------------------------------ |
| nur `restart` ausführen                      | Ursache wird nicht verstanden        |
| Logs nicht prüfen                            | wichtigste Hinweise werden ignoriert |
| Dienst läuft, aber Port nicht prüfen         | Erreichbarkeit bleibt unklar         |
| `kill -9` zu früh nutzen                     | Prozess wird unsauber beendet        |
| `enable` mit `start` verwechseln             | Dienst startet nicht sofort          |
| `daemon-reload` nach Unit-Änderung vergessen | systemd kennt Änderung nicht         |
| falschen Dienstnamen verwenden               | Statusprüfung schlägt fehl           |
| Konfiguration ändern ohne Backup             | Rückweg fehlt                        |
| SSH neu starten ohne Test                    | Risiko, sich auszusperren            |
| Dienste als Root laufen lassen ohne Grund    | Sicherheitsrisiko                    |

---

## Nützliche Befehle

| Befehl                     | Bedeutung                          |
| -------------------------- | ---------------------------------- |
| `ps aux`                   | alle Prozesse anzeigen             |
| `pgrep -a name`            | Prozesse nach Name suchen          |
| `top`                      | Prozesse live anzeigen             |
| `htop`                     | komfortable Prozessanzeige         |
| `pstree -p`                | Prozessbaum mit PIDs               |
| `kill PID`                 | Prozess sauber beenden             |
| `kill -9 PID`              | Prozess erzwingen beenden          |
| `pkill name`               | Prozesse nach Namen beenden        |
| `jobs`                     | Shell-Jobs anzeigen                |
| `fg`                       | Job in Vordergrund holen           |
| `free -h`                  | RAM anzeigen                       |
| `df -h`                    | Speicherplatz anzeigen             |
| `systemctl status dienst`  | Dienststatus anzeigen              |
| `systemctl start dienst`   | Dienst starten                     |
| `systemctl stop dienst`    | Dienst stoppen                     |
| `systemctl restart dienst` | Dienst neu starten                 |
| `systemctl reload dienst`  | Konfiguration neu laden            |
| `systemctl enable dienst`  | Autostart aktivieren               |
| `systemctl disable dienst` | Autostart deaktivieren             |
| `systemctl --failed`       | fehlgeschlagene Dienste anzeigen   |
| `journalctl -u dienst`     | Logs eines Dienstes anzeigen       |
| `ss -tulpen`               | offene Ports und Prozesse anzeigen |
| `systemd-analyze blame`    | langsame Boot-Dienste anzeigen     |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Prozesse und Dienste ein zentrales Thema im Linux-Betrieb.

In der Praxis bedeutet das:

- prüfen, ob Dienste laufen
- Dienste starten, stoppen und neu starten
- Autostart von Diensten verwalten
- Logs mit journalctl lesen
- Prozess- und Ressourcenverbrauch prüfen
- offene Ports analysieren
- Dienstfehler systematisch eingrenzen
- Konfigurationen nach Änderungen neu laden
- eigene Skripte als Dienste betreiben
- Docker-Dienst und Containerprozesse verstehen
- Serverprobleme nachvollziehbar dokumentieren

Ein guter FISI fragt bei einem Problem nicht nur „läuft der Server?“, sondern prüft gezielt Dienststatus, Logs, Prozesse, Ports, Ressourcen, Konfiguration und Rechte.

---

## Kurze Zusammenfassung

Ein Prozess ist ein laufendes Programm. Ein Dienst ist ein Hintergrundprogramm, das meist über systemd verwaltet wird.

Wichtige Prozessbefehle sind `ps aux`, `pgrep`, `top`, `htop`, `pstree`, `kill`, `pkill`, `free` und `df`.

Wichtige Dienstbefehle sind `systemctl status`, `start`, `stop`, `restart`, `reload`, `enable`, `disable`, `systemctl --failed` und `journalctl`.

Für FISI ist dieses Kapitel wichtig, weil viele Serverprobleme durch nicht laufende Dienste, fehlerhafte Konfigurationen, blockierte Ports, Rechteprobleme oder zu hohen Ressourcenverbrauch entstehen.
