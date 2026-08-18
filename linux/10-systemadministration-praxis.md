# 10. Systemadministration in der Praxis

In diesem Kapitel geht es um typische praktische Aufgaben in der Linux-Systemadministration.

Die vorherigen Kapitel erklären einzelne Grundlagen wie Dateien, Rechte, Prozesse, Dienste, Pakete, Netzwerk, Logs und Shell Scripting. In der Praxis kommen diese Themen aber fast immer zusammen vor. Ein Serverproblem besteht selten nur aus einem einzigen Befehl. Man muss den Zustand prüfen, Informationen sammeln, Änderungen verstehen, Fehler eingrenzen und das Ergebnis dokumentieren.

Für Fachinformatiker für Systemintegration ist dieses Kapitel wichtig, weil Linux-Administration nicht nur aus Befehlen besteht, sondern aus sauberem Vorgehen.

---

## Kurz erklärt

Systemadministration bedeutet, IT-Systeme einzurichten, zu betreiben, zu überwachen, abzusichern, zu warten und Fehler zu beheben.

Typische Aufgaben sind:

- Systemstatus prüfen
- Benutzer und Rechte verwalten
- Pakete installieren und aktualisieren
- Dienste prüfen und steuern
- Logs analysieren
- Netzwerkverbindungen testen
- Speicherplatz überwachen
- Backups vorbereiten und prüfen
- Sicherheitsmaßnahmen umsetzen
- Konfigurationen dokumentieren
- Fehler systematisch beheben
- Änderungen nachvollziehbar durchführen

Ein guter Administrator arbeitet nicht blind, sondern prüft zuerst den Zustand und entscheidet dann gezielt.

---

## Grundprinzipien der Administration

Linux-Administration folgt einigen wichtigen Grundprinzipien.

| Prinzip             | Bedeutung                                             |
| ------------------- | ----------------------------------------------------- |
| Prüfen vor Ändern   | erst Zustand verstehen, dann handeln                  |
| Kleine Schritte     | nicht zu viele Änderungen gleichzeitig                |
| Dokumentieren       | Änderungen nachvollziehbar machen                     |
| Backup vor Risiko   | vor wichtigen Änderungen Sicherung erstellen          |
| Least Privilege     | nur notwendige Rechte vergeben                        |
| Logs lesen          | Fehler anhand von Meldungen analysieren               |
| Wiederholbarkeit    | Abläufe so gestalten, dass sie erneut ausführbar sind |
| Sicherheit beachten | keine unnötigen Dienste, Rechte oder offenen Ports    |
| Testen              | nach Änderungen Ergebnis kontrollieren                |

Diese Prinzipien sind wichtiger als einzelne Befehle auswendig zu kennen.

---

## Systeminformationen sammeln

Bei fast jeder Administration ist zuerst wichtig:

```text
Was ist das für ein System?
```

Nützliche Befehle:

```bash
hostnamectl
uname -a
lsb_release -a
whoami
id
uptime
date
```

Bedeutung:

| Befehl           | Aufgabe                                   |
| ---------------- | ----------------------------------------- |
| `hostnamectl`    | Hostname und Systeminformationen anzeigen |
| `uname -a`       | Kernelinformationen anzeigen              |
| `lsb_release -a` | Distributionsinformationen anzeigen       |
| `whoami`         | aktuellen Benutzer anzeigen               |
| `id`             | Benutzer-ID und Gruppen anzeigen          |
| `uptime`         | Laufzeit und Systemlast anzeigen          |
| `date`           | Systemdatum und Uhrzeit anzeigen          |

Diese Informationen helfen, das System einzuordnen und Probleme besser zu verstehen.

---

## Schneller Systemcheck

Ein einfacher Systemcheck kann so aussehen:

```bash
hostnamectl
uptime
df -h
free -h
systemctl --failed
ip a
ip route
```

Damit prüft man:

- Systemname
- Betriebssystem
- Laufzeit
- Systemlast
- Speicherplatz
- Arbeitsspeicher
- fehlgeschlagene Dienste
- IP-Adressen
- Routing

Das ist ein guter Startpunkt bei vielen Problemen.

---

## Speicherplatz prüfen

Voller Speicherplatz ist eine sehr häufige Fehlerursache.

Prüfen:

```bash
df -h
```

Große Ordner finden:

```bash
du -sh *
```

Für Systembereiche:

```bash
sudo du -sh /var/*
sudo du -sh /var/log/*
```

Typische Probleme bei vollem Speicher:

- Dienste starten nicht
- Logs können nicht geschrieben werden
- Datenbanken stoppen
- Updates schlagen fehl
- Benutzer können keine Dateien speichern
- System wird langsam

Wichtig:

Nicht blind Dateien löschen. Erst prüfen, was groß ist und ob es sicher entfernt werden darf.

---

## Arbeitsspeicher prüfen

RAM prüfen:

```bash
free -h
```

Prozesse nach RAM-Verbrauch sortieren:

```bash
ps aux --sort=-%mem | head
```

Live prüfen:

```bash
top
```

Oder mit `htop`:

```bash
htop
```

Wichtig:

Linux nutzt freien RAM oft für Cache. Das ist normal und nicht automatisch ein Problem.

Problematisch wird es eher, wenn:

- Swap stark genutzt wird
- Prozesse sehr viel RAM verbrauchen
- das System langsam reagiert
- Dienste wegen Speicherproblemen beendet werden

---

## CPU und Systemlast prüfen

CPU-Last prüfen:

```bash
top
```

Prozesse nach CPU sortieren:

```bash
ps aux --sort=-%cpu | head
```

Systemlast anzeigen:

```bash
uptime
```

Beispiel:

```text
load average: 0.35, 0.42, 0.50
```

Die Load Average zeigt die durchschnittliche Last über 1, 5 und 15 Minuten.

Eine hohe Last kann entstehen durch:

- CPU-intensive Prozesse
- viele gleichzeitige Prozesse
- I/O-Probleme
- hängende Dienste
- zu wenig RAM
- starke Logausgaben
- Datenbanklast

---

## Dienste prüfen

Fehlgeschlagene Dienste anzeigen:

```bash
systemctl --failed
```

Status eines Dienstes prüfen:

```bash
systemctl status dienstname
```

Beispiel:

```bash
systemctl status ssh
systemctl status docker
```

Logs eines Dienstes prüfen:

```bash
journalctl -u dienstname -n 100
```

Dienst neu starten:

```bash
sudo systemctl restart dienstname
```

Wichtig:

Nicht sofort neu starten, ohne vorher Status und Logs zu lesen. Sonst verliert man manchmal wichtige Hinweise.

---

## Dienst nach Änderung neu laden

Nach Konfigurationsänderungen muss ein Dienst oft neu geladen oder neu gestartet werden.

Beispiel:

```bash
sudo systemctl reload nginx
```

Oder:

```bash
sudo systemctl restart nginx
```

Unterschied:

| Befehl    | Bedeutung                                    |
| --------- | -------------------------------------------- |
| `reload`  | Konfiguration neu laden, Dienst läuft weiter |
| `restart` | Dienst stoppen und neu starten               |

Wenn ein Dienst `reload` unterstützt, ist das oft schonender.

Nach jeder Änderung prüfen:

```bash
systemctl status dienstname
journalctl -u dienstname -n 50
```

---

## Paketpflege

Ein Linux-System muss regelmäßig aktualisiert werden.

Typischer Ablauf auf Ubuntu/Debian:

```bash
sudo apt update
apt list --upgradable
sudo apt upgrade
sudo apt autoremove
```

Wichtig:

`apt update` aktualisiert nur die Paketlisten.  
`apt upgrade` installiert Updates.

Bei Servern sollte man Updates planen und dokumentieren, besonders wenn Dienste betroffen sind.

Nach Updates prüfen:

```bash
systemctl --failed
journalctl -b -p err
```

---

## Paketlogs prüfen

Wenn nach einem Update Probleme auftreten, sind Paketlogs wichtig.

```bash
less /var/log/apt/history.log
less /var/log/dpkg.log
```

Damit kann man prüfen:

- welche Pakete installiert wurden
- welche Pakete aktualisiert wurden
- wann Änderungen passiert sind
- ob Installationen fehlgeschlagen sind

Das hilft, einen Fehler zeitlich mit einer Änderung zu verbinden.

---

## Benutzerverwaltung

Benutzer anzeigen:

```bash
getent passwd
```

Bestimmten Benutzer prüfen:

```bash
id username
getent passwd username
```

Benutzer erstellen:

```bash
sudo adduser username
```

Benutzer löschen:

```bash
sudo deluser username
```

Benutzer zu Gruppe hinzufügen:

```bash
sudo usermod -aG gruppe username
```

Wichtig:

Nach Gruppenänderungen muss sich der Benutzer oft neu anmelden.

Benutzerverwaltung sollte dokumentiert werden, besonders auf Servern.

---

## Rechteprobleme prüfen

Typische Fehlermeldung:

```text
Permission denied
```

Dann nicht sofort blind `sudo` nutzen.

Besser prüfen:

```bash
whoami
id
ls -l datei
ls -ld ordner
groups
```

Bei Pfadproblemen auch Elternordner prüfen:

```bash
ls -ld /pfad
ls -ld /pfad/zum
ls -ld /pfad/zum/ordner
```

Wichtig:

Bei Verzeichnissen braucht man `x`, um sie betreten zu können.

---

## Rechte sauber korrigieren

Besitzer ändern:

```bash
sudo chown user:group datei
```

Rechte ändern:

```bash
chmod 644 datei
chmod 755 script.sh
chmod 700 private-folder
```

Vorsicht mit:

```bash
chmod -R
chown -R
chmod 777
```

`chmod 777` ist fast nie eine saubere Lösung.

Besser ist zu prüfen:

- welcher Benutzer braucht Zugriff?
- welche Gruppe braucht Zugriff?
- muss gelesen, geschrieben oder ausgeführt werden?
- betrifft es Datei oder Ordner?
- muss es rekursiv sein?

---

## Netzwerkstatus prüfen

Netzwerk prüfen:

```bash
ip a
ip route
resolvectl status
```

Erreichbarkeit testen:

```bash
ping gateway-ip
ping 8.8.8.8
ping google.com
```

Offene Ports prüfen:

```bash
ss -tulpen
```

HTTP-Dienst testen:

```bash
curl http://localhost
curl -I https://example.com
```

Firewall prüfen:

```bash
sudo ufw status
```

Bei Netzwerkproblemen trennt man sauber zwischen:

- IP-Adresse
- Gateway
- Routing
- DNS
- Dienst
- Port
- Firewall
- externer Erreichbarkeit

---

## SSH-Administration

SSH ist eine der wichtigsten Grundlagen für Linux-Server.

Dienst prüfen:

```bash
systemctl status ssh
```

Port prüfen:

```bash
ss -tulpen | grep :22
```

Logs prüfen:

```bash
journalctl -u ssh -n 100
sudo less /var/log/auth.log
```

Firewall prüfen:

```bash
sudo ufw status
```

Typische Fehler:

| Fehler                         | Mögliche Ursache                        |
| ------------------------------ | --------------------------------------- |
| `Connection refused`           | SSH-Dienst läuft nicht oder Port falsch |
| `Connection timed out`         | Firewall, Routing oder Netzwerkproblem  |
| `Permission denied`            | Benutzer, Passwort oder SSH-Key falsch  |
| `Host key verification failed` | Host-Key hat sich geändert              |
| keine DNS-Auflösung            | Hostname kann nicht aufgelöst werden    |

Bei SSH-Konfigurationsänderungen vorsichtig sein, damit man sich nicht aussperrt.

---

## Konfigurationsdateien bearbeiten

Viele Linux-Einstellungen liegen in Textdateien.

Typische Orte:

```text
/etc
/etc/ssh/sshd_config
/etc/hosts
/etc/fstab
/etc/netplan/
```

Vor Änderungen Backup erstellen:

```bash
sudo cp /etc/hosts /etc/hosts.backup
```

Datei bearbeiten:

```bash
sudo nano /etc/hosts
```

Nach Änderung prüfen:

```bash
diff /etc/hosts.backup /etc/hosts
```

Wichtig:

Bei Konfigurationsdateien sollte man immer wissen, welcher Dienst danach neu geladen oder neu gestartet werden muss.

---

## Logs in der Praxis nutzen

Allgemeine Fehler seit Boot:

```bash
journalctl -b -p err
```

Dienstlogs:

```bash
journalctl -u dienstname -n 100
```

Live beobachten:

```bash
journalctl -u dienstname -f
```

Klassische Logs:

```bash
less /var/log/syslog
sudo less /var/log/auth.log
```

Nach Fehlern suchen:

```bash
grep -Ei "error|failed|denied" datei.log
```

Logs sind oft der Unterschied zwischen Raten und echter Analyse.

---

## Backup-Grundlagen

Backups schützen vor Datenverlust.

Ein Backup sollte nicht nur erstellt, sondern auch getestet werden.

Wichtige Fragen:

- Was wird gesichert?
- Wohin wird gesichert?
- Wie oft wird gesichert?
- Wie lange wird es aufbewahrt?
- Wer darf auf das Backup zugreifen?
- Wie wird das Backup wiederhergestellt?
- Wurde Restore getestet?

Ein einfaches Archiv:

```bash
tar -czf backup.tar.gz /pfad/zum/ordner
```

Entpacken:

```bash
tar -xzf backup.tar.gz
```

Wichtig:

Ein Backup ohne getestete Wiederherstellung ist unsicher.

---

## Automatisierung mit Skripten

Wiederkehrende Aufgaben können mit Shell-Skripten automatisiert werden.

Beispiel Systemcheck:

```bash
#!/bin/bash

echo "Hostname:"
hostname

echo
echo "Uptime:"
uptime

echo
echo "Speicherplatz:"
df -h

echo
echo "Fehlgeschlagene Dienste:"
systemctl --failed
```

Skript ausführbar machen:

```bash
chmod +x check-system.sh
```

Starten:

```bash
./check-system.sh
```

Automatisierung spart Zeit und reduziert Fehler, wenn Skripte sauber geschrieben und getestet sind.

---

## Cronjobs prüfen

Cronjobs anzeigen:

```bash
crontab -l
```

Cronjobs bearbeiten:

```bash
crontab -e
```

Systemweite Cron-Orte:

```text
/etc/crontab
/etc/cron.daily/
/etc/cron.hourly/
/etc/cron.weekly/
/etc/cron.monthly/
```

Cron-Dienst prüfen:

```bash
systemctl status cron
```

Wichtig:

Cronjobs sollten mit vollständigen Pfaden arbeiten und ihre Ausgabe in Logs schreiben.

Beispiel:

```cron
0 8 * * * /home/bilgin/scripts/check-system.sh >> /home/bilgin/scripts/check-system.log 2>&1
```

---

## Sicherheit im Alltag

Linux-Sicherheit besteht aus vielen kleinen Maßnahmen.

Wichtige Punkte:

- Updates regelmäßig einspielen
- unnötige Dienste deaktivieren
- offene Ports prüfen
- starke Passwörter oder SSH-Keys nutzen
- Root-Login vermeiden
- sudo bewusst verwenden
- Rechte minimal vergeben
- Firewall passend konfigurieren
- Logs prüfen
- keine geheimen Daten in Git speichern
- keine unbekannten Skripte mit sudo ausführen
- Backups schützen
- Benutzerkonten regelmäßig prüfen

Sicherheit ist kein einzelner Befehl, sondern ein dauerhaftes Vorgehen.

---

## Offene Ports und Dienste reduzieren

Offene Ports prüfen:

```bash
ss -tulpen
```

Dienste prüfen:

```bash
systemctl list-units --type=service --all
```

Nicht benötigten Dienst stoppen:

```bash
sudo systemctl stop dienstname
```

Autostart deaktivieren:

```bash
sudo systemctl disable dienstname
```

Wichtig:

Nur Dienste deaktivieren, deren Zweck man versteht.

Bei Servern gilt:

```text
Was nicht benötigt wird, sollte nicht laufen.
```

---

## Dokumentation von Änderungen

Jede wichtige Änderung sollte dokumentiert werden.

Dokumentation kann enthalten:

- Datum
- Systemname
- Ausgangszustand
- durchgeführte Änderung
- verwendete Befehle
- betroffene Dateien
- Ergebnis
- offene Punkte
- Rollback-Möglichkeit

Beispiel:

```text
Datum: 18.08.2026
System: ubuntu-server-01
Änderung: SSH-Dienst aktiviert
Befehl: sudo systemctl enable --now ssh
Prüfung: systemctl status ssh -> active (running)
Ergebnis: SSH erreichbar auf Port 22
```

Gute Dokumentation hilft später bei Fehlersuche, Übergabe und Teamarbeit.

---

## Change Management

Change Management bedeutet, Änderungen geplant und kontrolliert durchzuführen.

Vor einer Änderung:

- Ziel klären
- Risiko einschätzen
- Backup erstellen
- betroffene Dienste prüfen
- Wartungsfenster beachten
- Rollback planen

Während der Änderung:

- nur notwendige Schritte durchführen
- Ausgaben beachten
- Fehlermeldungen notieren

Nach der Änderung:

- Dienststatus prüfen
- Logs prüfen
- Funktion testen
- Dokumentation aktualisieren

Das ist besonders wichtig bei produktiven Systemen.

---

## Rollback

Rollback bedeutet, eine Änderung rückgängig zu machen.

Beispiele:

- Konfigurationsbackup zurückkopieren
- Dienst wieder auf alte Version setzen
- Paketänderung rückgängig machen
- Firewallregel entfernen
- alten Containerstand starten
- Snapshot einer VM wiederherstellen

Beispiel mit Konfiguration:

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
sudo nano /etc/ssh/sshd_config
sudo systemctl restart ssh
```

Wenn Fehler auftreten:

```bash
sudo cp /etc/ssh/sshd_config.backup /etc/ssh/sshd_config
sudo systemctl restart ssh
```

Ein Rollback-Plan ist wichtig, bevor man riskante Änderungen macht.

---

## Incident-Grundablauf

Ein Incident ist eine Störung oder ein Sicherheitsereignis.

Ein einfacher Ablauf:

1. Problem aufnehmen
2. betroffene Systeme identifizieren
3. Auswirkungen einschätzen
4. Logs und Status prüfen
5. Ursache eingrenzen
6. Maßnahme durchführen
7. Funktion testen
8. Ergebnis dokumentieren
9. Ursache langfristig beheben
10. Lessons Learned notieren

Wichtig:

Bei kritischen Problemen nicht hektisch viele Änderungen machen. Sonst wird die Ursache schwerer nachvollziehbar.

---

## Beispiel: Dienst ist nicht erreichbar

Problem:

```text
Webseite ist nicht erreichbar.
```

Prüfung:

```bash
systemctl status nginx
journalctl -u nginx -n 100
ss -tulpen | grep :80
curl http://localhost
sudo ufw status
ip a
ip route
```

Mögliche Ursachen:

- Nginx läuft nicht
- Port 80 ist nicht offen
- Firewall blockiert
- Konfiguration ist fehlerhaft
- Dienst lauscht nur lokal
- DNS zeigt falsch
- Server hat Netzwerkproblem

Saubere Analyse trennt diese Ursachen Schritt für Schritt.

---

## Beispiel: Speicherplatz ist voll

Problem:

```text
No space left on device
```

Prüfung:

```bash
df -h
sudo du -sh /var/*
sudo du -sh /var/log/*
journalctl --disk-usage
```

Mögliche Maßnahmen:

```bash
sudo apt clean
sudo apt autoremove
sudo journalctl --vacuum-time=7d
```

Wichtig:

Vor dem Löschen prüfen, was entfernt wird.

Nicht blind Logs oder Datenbanken löschen.

---

## Beispiel: Permission denied

Problem:

```text
Permission denied
```

Prüfung:

```bash
whoami
id
ls -l datei
ls -ld ordner
groups
```

Mögliche Ursachen:

- falscher Besitzer
- falsche Gruppe
- fehlendes Leserecht
- fehlendes Schreibrecht
- fehlendes Ausführungsrecht
- übergeordneter Ordner nicht betretbar
- Dienst läuft unter anderem Benutzer

Mögliche Korrektur:

```bash
sudo chown user:group datei
chmod 640 datei
```

Nicht einfach:

```bash
chmod 777 datei
```

---

## Beispiel: DNS funktioniert nicht

Problem:

```text
IP ist erreichbar, Domainname nicht.
```

Prüfung:

```bash
ping 8.8.8.8
ping google.com
resolvectl status
resolvectl query google.com
cat /etc/resolv.conf
```

Mögliche Ursachen:

- kein DNS-Server eingetragen
- DNS-Server nicht erreichbar
- systemd-resolved Problem
- falsche Netzwerkkonfiguration
- VPN oder Firewall beeinflusst DNS
- interne Domain falsch konfiguriert

DNS-Probleme sind sehr häufig und sollten getrennt von reinen IP-Problemen betrachtet werden.

---

## Beispiel: Docker-Container funktioniert nicht

Prüfung:

```bash
systemctl status docker
docker ps
docker logs containername
docker exec -it containername sh
ss -tulpen
```

Typische Ursachen:

- Docker-Dienst läuft nicht
- Container ist gestoppt
- Anwendung im Container startet nicht
- Portmapping fehlt
- Volume-Rechte falsch
- Umgebungsvariable fehlt
- Netzwerkproblem zwischen Containern
- Host-Port ist bereits belegt

Docker-Probleme sind oft Kombinationen aus Linux-Rechten, Netzwerk, Prozessen, Ports und Logs.

---

## Admin-Checkliste nach Installation

Nach einer neuen Linux-Installation kann man prüfen:

```bash
hostnamectl
ip a
ip route
sudo apt update
sudo apt upgrade
systemctl --failed
df -h
free -h
sudo ufw status
```

Zusätzlich sinnvoll:

- Hostname setzen
- Benutzer prüfen
- SSH einrichten
- Updates installieren
- benötigte Pakete installieren
- unnötige Dienste deaktivieren
- Firewall prüfen
- Zeitzone prüfen
- Dokumentation erstellen

Zeitzone prüfen:

```bash
timedatectl
```

---

## Admin-Checkliste für Serverprobleme

Bei einem unbekannten Serverproblem:

```bash
hostnamectl
uptime
df -h
free -h
top
systemctl --failed
journalctl -b -p err
ip a
ip route
ss -tulpen
```

Dann gezielt je nach Symptom weiterprüfen:

- Dienstproblem: `systemctl status`, `journalctl -u`
- Netzwerkproblem: `ping`, `resolvectl`, `ss`, `ufw`
- Speicherproblem: `df`, `du`
- Rechteproblem: `ls -l`, `id`, `groups`
- Paketproblem: `apt`, Paketlogs
- Dockerproblem: `docker ps`, `docker logs`, `systemctl status docker`

---

## Admin-Checkliste vor Änderungen

Vor wichtigen Änderungen:

```bash
pwd
whoami
id
systemctl status dienstname
sudo cp config config.backup
```

Zusätzlich überlegen:

- Was genau soll geändert werden?
- Welche Datei ist betroffen?
- Welcher Dienst nutzt diese Datei?
- Wie teste ich die Änderung?
- Wie mache ich die Änderung rückgängig?
- Muss ein Dienst neu geladen werden?
- Ist ein Wartungsfenster nötig?
- Sind Benutzer betroffen?

Diese Fragen verhindern viele Fehler.

---

## Admin-Checkliste nach Änderungen

Nach Änderungen:

```bash
systemctl status dienstname
journalctl -u dienstname -n 50
ss -tulpen
```

Zusätzlich testen:

```bash
curl http://localhost
ping ziel
ssh user@server
```

Je nach Änderung:

- Dienststatus prüfen
- Logs prüfen
- Funktion testen
- Netzwerk prüfen
- Rechte prüfen
- Dokumentation aktualisieren
- Backup behalten oder sauber archivieren

Eine Änderung ist erst fertig, wenn die Funktion geprüft wurde.

---

## Typische Fehler in der Praxis

| Fehler                                 | Problem                                          |
| -------------------------------------- | ------------------------------------------------ |
| ohne Prüfung direkt ändern             | Ursache bleibt unklar                            |
| keine Backups vor Konfigänderungen     | Rückweg fehlt                                    |
| zu viele Änderungen gleichzeitig       | Fehlerquelle schwer auffindbar                   |
| Logs ignorieren                        | wichtigste Hinweise fehlen                       |
| `sudo` als Standardlösung nutzen       | Rechteproblem wird nicht verstanden              |
| `chmod 777` verwenden                  | Sicherheitsrisiko                                |
| Dienste neu starten ohne Statusprüfung | Hinweise können verloren gehen                   |
| Firewall vergessen                     | Dienst läuft, ist aber nicht erreichbar          |
| DNS und Internet verwechseln           | falsche Diagnose                                 |
| Dokumentation weglassen                | später nicht nachvollziehbar                     |
| Tests nach Änderung vergessen          | Änderung ist nicht sicher bestätigt              |
| fremde Befehle blind kopieren          | Risiko für Datenverlust oder Sicherheitsprobleme |

---

## Nützliche Befehle

| Befehl                          | Bedeutung                        |
| ------------------------------- | -------------------------------- |
| `hostnamectl`                   | Systeminformationen anzeigen     |
| `uname -a`                      | Kernelinformationen anzeigen     |
| `uptime`                        | Laufzeit und Last anzeigen       |
| `df -h`                         | Speicherplatz prüfen             |
| `du -sh *`                      | Ordnergrößen prüfen              |
| `free -h`                       | RAM prüfen                       |
| `top`                           | Prozesse live prüfen             |
| `ps aux`                        | Prozesse anzeigen                |
| `systemctl --failed`            | fehlgeschlagene Dienste anzeigen |
| `systemctl status dienst`       | Dienststatus prüfen              |
| `journalctl -u dienst`          | Dienstlogs anzeigen              |
| `journalctl -b -p err`          | Fehler seit Boot anzeigen        |
| `ip a`                          | IP-Adressen anzeigen             |
| `ip route`                      | Routing prüfen                   |
| `resolvectl status`             | DNS prüfen                       |
| `ss -tulpen`                    | offene Ports prüfen              |
| `sudo ufw status`               | Firewall prüfen                  |
| `apt list --upgradable`         | verfügbare Updates anzeigen      |
| `less /var/log/apt/history.log` | Paketänderungen prüfen           |
| `whoami`                        | aktuellen Benutzer anzeigen      |
| `id`                            | Benutzer und Gruppen prüfen      |
| `ls -l`                         | Rechte anzeigen                  |
| `chmod`                         | Rechte ändern                    |
| `chown`                         | Besitzer ändern                  |
| `tar`                           | Archive erstellen                |
| `crontab -l`                    | Cronjobs anzeigen                |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist praktische Linux-Administration ein Kernbereich.

In der Praxis bedeutet das:

- Linux-Systeme installieren und vorbereiten
- Benutzer und Rechte verwalten
- Dienste betreiben und prüfen
- Updates durchführen
- Logs analysieren
- Netzwerkprobleme eingrenzen
- Backups planen und testen
- Sicherheitsgrundlagen anwenden
- Fehler strukturiert beheben
- Änderungen dokumentieren
- Systeme wartbar halten
- Automatisierung mit Skripten nutzen
- Server und Container besser verstehen

Ein guter FISI kennt nicht nur Befehle, sondern arbeitet mit Methode: Zustand prüfen, Ursache eingrenzen, Änderung planen, Ergebnis testen und alles nachvollziehbar dokumentieren.

---

## Kurze Zusammenfassung

Linux-Systemadministration verbindet viele einzelne Themen: Dateien, Rechte, Prozesse, Dienste, Pakete, Netzwerk, Logs, Sicherheit, Backups und Automatisierung.

Wichtig ist ein strukturiertes Vorgehen. Vor Änderungen sollte man prüfen, sichern und planen. Nach Änderungen sollte man testen und dokumentieren.

Für FISI ist dieses Kapitel wichtig, weil reale IT-Probleme selten nur mit einem einzelnen Befehl gelöst werden. Entscheidend ist, Zusammenhänge zu verstehen und sauber zu arbeiten.
