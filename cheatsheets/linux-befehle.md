# Linux-Befehle Cheatsheet

Dieses Cheatsheet enthält wichtige Linux-Befehle für Alltag, Administration und Fehlersuche.

Die Befehle sind kurz erklärt und nach typischen Aufgaben sortiert. Für ausführliche Erklärungen siehe den Bereich [Linux](../linux/).

---

## Navigation im Dateisystem

| Befehl      | Bedeutung                           |
| ----------- | ----------------------------------- |
| `pwd`       | zeigt den aktuellen Pfad            |
| `ls`        | zeigt Dateien und Ordner            |
| `ls -l`     | zeigt Dateien mit Details           |
| `ls -la`    | zeigt auch versteckte Dateien       |
| `cd ordner` | wechselt in einen Ordner            |
| `cd ..`     | geht eine Ebene nach oben           |
| `cd ~`      | wechselt ins Home-Verzeichnis       |
| `cd -`      | wechselt zum vorherigen Verzeichnis |

Beispiel:

```bash
pwd
ls -la
cd /etc
cd -
```

---

## Dateien und Ordner

| Befehl                     | Bedeutung                       |
| -------------------------- | ------------------------------- |
| `touch datei.txt`          | erstellt eine leere Datei       |
| `mkdir ordner`             | erstellt einen Ordner           |
| `mkdir -p pfad/zum/ordner` | erstellt mehrere Ordnerstufen   |
| `cp quelle ziel`           | kopiert eine Datei              |
| `cp -r quelle ziel`        | kopiert einen Ordner rekursiv   |
| `mv alt neu`               | verschiebt oder benennt um      |
| `rm datei`                 | löscht eine Datei               |
| `rm -r ordner`             | löscht einen Ordner rekursiv    |
| `file datei`               | zeigt den Dateityp              |
| `stat datei`               | zeigt genaue Dateiinformationen |

Vorsicht:

```bash
rm -rf
```

Dieser Befehl kann sehr viele Dateien ohne Rückfrage löschen.

---

## Dateien anzeigen und lesen

| Befehl             | Bedeutung                   |
| ------------------ | --------------------------- |
| `cat datei`        | zeigt komplette Datei       |
| `less datei`       | zeigt Datei seitenweise     |
| `head datei`       | zeigt Anfang einer Datei    |
| `head -n 20 datei` | zeigt die ersten 20 Zeilen  |
| `tail datei`       | zeigt Ende einer Datei      |
| `tail -n 20 datei` | zeigt die letzten 20 Zeilen |
| `tail -f datei`    | verfolgt Datei live         |
| `wc -l datei`      | zählt Zeilen                |

Beispiel:

```bash
less /var/log/syslog
tail -f /var/log/syslog
wc -l datei.txt
```

---

## Suchen und Filtern

| Befehl                     | Bedeutung                         |
| -------------------------- | --------------------------------- |
| `grep "text" datei`        | sucht Text in Datei               |
| `grep -i "text" datei`     | sucht ohne Groß-/Kleinschreibung  |
| `grep -r "text" ordner/`   | sucht rekursiv in Ordner          |
| `grep -n "text" datei`     | zeigt Zeilennummern               |
| `find /pfad -name "datei"` | sucht nach Dateiname              |
| `find . -type f`           | sucht Dateien                     |
| `find . -type d`           | sucht Ordner                      |
| `which befehl`             | zeigt Pfad eines Befehls          |
| `whereis befehl`           | zeigt mögliche Orte eines Befehls |

Beispiel:

```bash
grep -r "error" /var/log/
find . -name "*.md"
which python3
```

---

## Benutzer und Gruppen

| Befehl                         | Bedeutung                          |
| ------------------------------ | ---------------------------------- |
| `whoami`                       | zeigt aktuellen Benutzer           |
| `id`                           | zeigt Benutzer-ID und Gruppen      |
| `groups`                       | zeigt Gruppen des Benutzers        |
| `sudo befehl`                  | führt Befehl mit Admin-Rechten aus |
| `su - benutzer`                | wechselt Benutzer                  |
| `passwd`                       | ändert eigenes Passwort            |
| `sudo passwd benutzer`         | ändert Passwort eines Benutzers    |
| `sudo adduser name`            | erstellt Benutzer                  |
| `sudo deluser name`            | entfernt Benutzer                  |
| `sudo usermod -aG gruppe user` | fügt Benutzer zu Gruppe hinzu      |

Beispiel:

```bash
whoami
id
groups
sudo adduser testuser
```

---

## Rechte und Besitzer

| Befehl                    | Bedeutung                         |
| ------------------------- | --------------------------------- |
| `ls -l`                   | zeigt Rechte und Besitzer         |
| `chmod +x script.sh`      | macht Skript ausführbar           |
| `chmod 644 datei`         | typische Rechte für Datei         |
| `chmod 755 ordner`        | typische Rechte für Ordner/Skript |
| `chown user:gruppe datei` | ändert Besitzer und Gruppe        |
| `chgrp gruppe datei`      | ändert Gruppe                     |
| `umask`                   | zeigt Standard-Rechtemaske        |

Beispiel:

```bash
ls -l script.sh
chmod +x script.sh
sudo chown root:root config.conf
```

Typische Rechte:

| Rechte | Bedeutung                              |
| ------ | -------------------------------------- |
| `600`  | nur Besitzer lesen/schreiben           |
| `644`  | Besitzer schreiben, alle lesen         |
| `700`  | nur Besitzer alles                     |
| `755`  | Besitzer alles, andere lesen/ausführen |

---

## Prozesse

| Befehl        | Bedeutung                                   |
| ------------- | ------------------------------------------- |
| `ps aux`      | zeigt laufende Prozesse                     |
| `top`         | zeigt Prozesse live                         |
| `htop`        | bessere Prozessübersicht, falls installiert |
| `pgrep name`  | sucht Prozess-ID nach Name                  |
| `kill PID`    | beendet Prozess normal                      |
| `kill -9 PID` | beendet Prozess hart                        |
| `pkill name`  | beendet Prozesse nach Name                  |
| `jobs`        | zeigt Hintergrundjobs                       |
| `Ctrl + C`    | bricht laufenden Prozess ab                 |
| `Ctrl + Z`    | pausiert Prozess                            |

Beispiel:

```bash
ps aux | grep nginx
pgrep ssh
kill 1234
```

---

## Dienste mit systemd

| Befehl                          | Bedeutung                     |
| ------------------------------- | ----------------------------- |
| `systemctl status dienst`       | zeigt Dienststatus            |
| `sudo systemctl start dienst`   | startet Dienst                |
| `sudo systemctl stop dienst`    | stoppt Dienst                 |
| `sudo systemctl restart dienst` | startet Dienst neu            |
| `sudo systemctl reload dienst`  | lädt Konfiguration neu        |
| `sudo systemctl enable dienst`  | aktiviert Autostart           |
| `sudo systemctl disable dienst` | deaktiviert Autostart         |
| `systemctl is-active dienst`    | prüft, ob Dienst aktiv ist    |
| `systemctl is-enabled dienst`   | prüft Autostart               |
| `systemctl --failed`            | zeigt fehlgeschlagene Dienste |

Beispiel:

```bash
systemctl status ssh
sudo systemctl restart ssh
systemctl --failed
```

---

## Logs und Fehlersuche

| Befehl                            | Bedeutung                         |
| --------------------------------- | --------------------------------- |
| `journalctl`                      | zeigt systemd-Logs                |
| `journalctl -xe`                  | zeigt wichtige aktuelle Meldungen |
| `journalctl -u dienst`            | zeigt Logs eines Dienstes         |
| `journalctl -u dienst -f`         | verfolgt Dienstlogs live          |
| `journalctl --since "1 hour ago"` | zeigt Logs der letzten Stunde     |
| `dmesg`                           | zeigt Kernel-Meldungen            |
| `dmesg -T`                        | Kernel-Meldungen mit Zeit         |
| `tail -f /var/log/syslog`         | verfolgt Systemlog live           |

Beispiel:

```bash
journalctl -u ssh -f
journalctl --since "today"
dmesg -T | tail
```

---

## Paketverwaltung mit APT

| Befehl                   | Bedeutung                                      |
| ------------------------ | ---------------------------------------------- |
| `sudo apt update`        | aktualisiert Paketlisten                       |
| `sudo apt upgrade`       | installiert Updates                            |
| `sudo apt install paket` | installiert Paket                              |
| `sudo apt remove paket`  | entfernt Paket                                 |
| `sudo apt purge paket`   | entfernt Paket inklusive Konfigurationsdateien |
| `sudo apt autoremove`    | entfernt nicht mehr benötigte Pakete           |
| `apt search paket`       | sucht Paket                                    |
| `apt show paket`         | zeigt Paketinformationen                       |
| `apt list --installed`   | zeigt installierte Pakete                      |
| `dpkg -l`                | zeigt installierte Pakete über dpkg            |

Beispiel:

```bash
sudo apt update
sudo apt install curl
apt show nginx
```

---

## Speicherplatz und Systemressourcen

| Befehl          | Bedeutung                            |
| --------------- | ------------------------------------ |
| `df -h`         | zeigt Speicherplatz der Dateisysteme |
| `du -sh ordner` | zeigt Größe eines Ordners            |
| `free -h`       | zeigt RAM-Nutzung                    |
| `uptime`        | zeigt Laufzeit und Load Average      |
| `hostnamectl`   | zeigt Systeminformationen            |
| `uname -a`      | zeigt Kernelinformationen            |
| `lsblk`         | zeigt Datenträger und Partitionen    |
| `mount`         | zeigt eingehängte Dateisysteme       |
| `findmnt`       | zeigt Mountpoints übersichtlich      |

Beispiel:

```bash
df -h
du -sh ~/Downloads
free -h
lsblk
```

---

## Netzwerk

| Befehl              | Bedeutung                            |
| ------------------- | ------------------------------------ |
| `ip a`              | zeigt IP-Adressen                    |
| `ip route`          | zeigt Routing-Tabelle                |
| `ping ziel`         | prüft Erreichbarkeit                 |
| `ping -c 4 ziel`    | sendet 4 Ping-Pakete                 |
| `ss -tulpen`        | zeigt offene Ports                   |
| `hostname`          | zeigt Hostname                       |
| `hostname -I`       | zeigt eigene IP-Adressen             |
| `resolvectl status` | zeigt DNS-Informationen              |
| `dig domain`        | fragt DNS ab                         |
| `curl url`          | ruft URL im Terminal ab              |
| `wget url`          | lädt Datei herunter                  |
| `traceroute ziel`   | zeigt Netzwerkweg, falls installiert |

Beispiel:

```bash
ip a
ip route
ping -c 4 8.8.8.8
ss -tulpen
```

---

## SSH

| Befehl                        | Bedeutung                          |
| ----------------------------- | ---------------------------------- |
| `ssh user@host`               | verbindet zu Server                |
| `ssh -p port user@host`       | verbindet über bestimmten Port     |
| `scp datei user@host:/pfad`   | kopiert Datei auf Server           |
| `scp user@host:/pfad/datei .` | kopiert Datei vom Server           |
| `ssh-keygen -t ed25519`       | erstellt SSH-Schlüssel             |
| `ssh-add key`                 | fügt Schlüssel zum SSH-Agent hinzu |
| `ssh -T git@github.com`       | testet GitHub-SSH                  |

Beispiel:

```bash
ssh admin@192.168.1.10
scp backup.tar admin@server:/home/admin/
ssh -T git@github.com
```

---

## Archive und Komprimierung

| Befehl                           | Bedeutung                          |
| -------------------------------- | ---------------------------------- |
| `tar -cf archiv.tar ordner/`     | erstellt tar-Archiv                |
| `tar -xf archiv.tar`             | entpackt tar-Archiv                |
| `tar -czf archiv.tar.gz ordner/` | erstellt gzip-komprimiertes Archiv |
| `tar -xzf archiv.tar.gz`         | entpackt gzip-komprimiertes Archiv |
| `zip -r archiv.zip ordner/`      | erstellt ZIP-Archiv                |
| `unzip archiv.zip`               | entpackt ZIP-Archiv                |

Beispiel:

```bash
tar -czf backup.tar.gz projekt/
tar -xzf backup.tar.gz
```

---

## Shell und Variablen

| Befehl               | Bedeutung                |
| -------------------- | ------------------------ |
| `echo text`          | gibt Text aus            |
| `echo $PATH`         | zeigt PATH-Variable      |
| `export NAME=wert`   | setzt Umgebungsvariable  |
| `env`                | zeigt Umgebungsvariablen |
| `history`            | zeigt Befehlshistorie    |
| `alias ll='ls -la'`  | erstellt Alias           |
| `source datei`       | lädt Shell-Datei neu     |
| `chmod +x script.sh` | macht Skript ausführbar  |
| `./script.sh`        | führt Skript aus         |

Beispiel:

```bash
echo $PATH
history
alias ll='ls -la'
```

---

## Ein- und Ausgabe

| Zeichen / Befehl | Bedeutung                                 |
| ---------------- | ----------------------------------------- | -------------------------------------- |
| `>`              | Ausgabe in Datei schreiben, überschreibt  |
| `>>`             | Ausgabe an Datei anhängen                 |
| `<`              | Eingabe aus Datei lesen                   |
| `                | `                                         | Ausgabe an nächsten Befehl weitergeben |
| `2>`             | Fehlermeldungen umleiten                  |
| `2>&1`           | Fehler und normale Ausgabe zusammenführen |

Beispiel:

```bash
ls -la > liste.txt
echo "neue Zeile" >> liste.txt
ps aux | grep ssh
```

---

## Praktische Admin-Abläufe

### System kurz prüfen

```bash
hostnamectl
uptime
df -h
free -h
systemctl --failed
```

### Dienst prüfen

```bash
systemctl status ssh
journalctl -u ssh --since "1 hour ago"
ss -tulpen | grep ssh
```

### Netzwerk prüfen

```bash
ip a
ip route
ping -c 4 8.8.8.8
ping -c 4 google.com
resolvectl status
```

### Speicherplatzproblem prüfen

```bash
df -h
du -sh /*
du -sh /var/log/*
journalctl --disk-usage
```

---

## Gefährliche Befehle

Diese Befehle können Daten löschen oder Systeme stark verändern.

| Befehl                   | Risiko                              |
| ------------------------ | ----------------------------------- |
| `rm -rf pfad`            | löscht rekursiv ohne Rückfrage      |
| `chmod -R 777 /pfad`     | setzt unsichere Rechte              |
| `chown -R user:gruppe /` | kann Systemrechte zerstören         |
| `mkfs`                   | formatiert Dateisystem              |
| `dd`                     | kann Datenträger überschreiben      |
| `git reset --hard`       | verwirft Git-Änderungen             |
| `docker system prune -a` | löscht Docker-Daten                 |
| `sudo`                   | führt Befehle mit Admin-Rechten aus |

Vor gefährlichen Befehlen immer prüfen:

```bash
pwd
ls -la
git status
df -h
lsblk
```

---

## Kurze Zusammenfassung

Dieses Cheatsheet enthält wichtige Linux-Befehle für Navigation, Dateien, Rechte, Prozesse, Dienste, Logs, Pakete, Speicherplatz, Netzwerk und SSH.

Wichtige Grundbefehle für den Alltag sind:

```bash
pwd
ls -la
cd
cat
less
grep
find
chmod
chown
ps aux
systemctl status
journalctl
apt
df -h
free -h
ip a
ip route
ping
ss -tulpen
```

Für FISI ist Linux-Befehlssicherheit wichtig, weil viele Admin-Aufgaben direkt im Terminal stattfinden.
