# Linux

In diesem Bereich sammle ich Linux-Grundlagen und praxisnahe Linux-Administration für meine Ausbildung zum Fachinformatiker für Systemintegration.

Linux ist in der IT wichtig, weil viele Server, Netzwerkdienste, Container, Cloud-Systeme und Entwicklungsumgebungen auf Linux basieren. Für Systemintegration reicht es nicht, nur einzelne Befehle auswendig zu kennen. Wichtig ist zu verstehen, wie Linux aufgebaut ist, wie Dateien und Rechte funktionieren, wie Dienste verwaltet werden, wie Logs gelesen werden und wie man Fehler systematisch eingrenzt.

---

## Ziel dieses Bereichs

Dieser Linux-Bereich soll eine strukturierte Wissenssammlung für praktische Administration sein.

Die Themen sind so aufgebaut, dass zuerst die Grundlagen kommen und danach immer mehr typische Aufgaben aus dem IT-Betrieb behandelt werden.

Wichtige Ziele sind:

- Linux als Betriebssystem verstehen
- sicher im Terminal arbeiten
- Dateisystem und Pfade einordnen
- Dateien und Verzeichnisse verwalten
- Benutzer, Gruppen und Rechte verstehen
- Prozesse und Dienste analysieren
- Softwarepakete installieren und aktualisieren
- Netzwerk unter Linux prüfen
- Logs lesen und Fehler finden
- einfache Shell-Skripte verstehen
- typische Admin-Aufgaben dokumentieren

---

## Kapitelübersicht

| Kapitel                                   | Thema                              |
| ----------------------------------------- | ---------------------------------- |
| [1](./01-linux-grundlagen.md)             | Linux Grundlagen                   |
| [2](./02-dateisystem-und-pfade.md)        | Dateisystem und Pfade              |
| [3](./03-dateien-und-verzeichnisse.md)    | Dateien und Verzeichnisse          |
| [4](./04-benutzer-und-rechte.md)          | Benutzer, Gruppen und Rechte       |
| [5](./05-prozesse-und-dienste.md)         | Prozesse und Dienste               |
| [6](./06-paketverwaltung.md)              | Paketverwaltung                    |
| [7](./07-netzwerk-linux.md)               | Netzwerk unter Linux               |
| [8](./08-logs-und-fehlersuche.md)         | Logs und Fehlersuche               |
| [9](./09-shell-scripting.md)              | Shell Scripting                    |
| [10](./10-systemadministration-praxis.md) | Systemadministration in der Praxis |

---

## Warum Linux wichtig ist

Linux wird in vielen Bereichen der IT eingesetzt.

Beispiele:

- Serverbetrieb
- Webserver
- Datenbanken
- Container
- Docker
- Kubernetes
- Cloud-Systeme
- Firewalls
- Monitoring
- Automatisierung
- Netzwerkdienste
- Backup-Systeme
- Entwicklungsumgebungen
- Embedded Systeme

Viele Dienste im professionellen IT-Betrieb laufen auf Linux-Servern, weil Linux stabil, flexibel, gut automatisierbar und ressourcenschonend ist.

Für FISI ist Linux besonders wichtig, weil viele Aufgaben im Server- und Netzwerkbereich ohne grafische Oberfläche erledigt werden. Deshalb ist der sichere Umgang mit Terminal, Dateien, Diensten, Logs und Netzwerkbefehlen eine wichtige Grundlage.

---

## Linux und Systemadministration

Linux-Administration bedeutet nicht nur, Befehle auszuführen.

Ein Administrator muss verstehen:

- wo Konfigurationsdateien liegen
- welche Dienste laufen
- welche Benutzer Rechte haben
- welche Prozesse Ressourcen verbrauchen
- welche Logs Fehler zeigen
- welche Netzwerkverbindungen bestehen
- welche Pakete installiert sind
- wie Updates eingespielt werden
- wie Zugriffe abgesichert werden
- wie Fehler systematisch analysiert werden

Linux wird oft über das Terminal verwaltet. Dadurch kann man schnell arbeiten, Aufgaben automatisieren und auch entfernte Server per SSH administrieren.

---

## Terminal und Shell

Das Terminal ist die wichtigste Arbeitsumgebung unter Linux.

Über die Shell werden Befehle eingegeben und ausgeführt. Häufig wird die Bash genutzt.

Typische Aufgaben im Terminal:

- Dateien anzeigen
- Ordner wechseln
- Programme starten
- Benutzer prüfen
- Rechte ändern
- Dienste verwalten
- Logs lesen
- Netzwerk testen
- Prozesse anzeigen
- Pakete installieren
- Skripte ausführen

Ein sicherer Umgang mit dem Terminal ist für FISI sehr wichtig, weil Server oft keine grafische Oberfläche haben.

---

## Wichtige Grundbefehle

| Befehl       | Bedeutung                                     |
| ------------ | --------------------------------------------- |
| `pwd`        | aktuellen Pfad anzeigen                       |
| `ls`         | Dateien und Ordner anzeigen                   |
| `cd`         | Verzeichnis wechseln                          |
| `mkdir`      | Verzeichnis erstellen                         |
| `touch`      | Datei erstellen                               |
| `cp`         | Datei oder Ordner kopieren                    |
| `mv`         | Datei oder Ordner verschieben oder umbenennen |
| `rm`         | Datei oder Ordner löschen                     |
| `cat`        | Datei ausgeben                                |
| `less`       | Datei seitenweise anzeigen                    |
| `grep`       | Text suchen                                   |
| `find`       | Dateien suchen                                |
| `chmod`      | Rechte ändern                                 |
| `chown`      | Besitzer ändern                               |
| `ps`         | Prozesse anzeigen                             |
| `systemctl`  | Dienste verwalten                             |
| `journalctl` | Systemlogs anzeigen                           |
| `ip`         | Netzwerk prüfen                               |
| `df`         | Speicherplatz anzeigen                        |
| `top`        | Prozesse und Ressourcen anzeigen              |

Diese Befehle sind die Grundlage für viele spätere Admin-Aufgaben.

---

## Linux-Dateisystem

Linux nutzt eine klare Verzeichnisstruktur.

Wichtige Verzeichnisse:

| Verzeichnis | Bedeutung                              |
| ----------- | -------------------------------------- |
| `/`         | Wurzelverzeichnis des Systems          |
| `/home`     | Benutzerverzeichnisse                  |
| `/etc`      | Konfigurationsdateien                  |
| `/var`      | veränderliche Daten, Logs, Spools      |
| `/var/log`  | Logdateien                             |
| `/usr`      | Programme und Bibliotheken             |
| `/bin`      | wichtige Benutzerbefehle               |
| `/sbin`     | wichtige Systembefehle                 |
| `/tmp`      | temporäre Dateien                      |
| `/opt`      | optionale Software                     |
| `/root`     | Home-Verzeichnis des Root-Benutzers    |
| `/dev`      | Gerätedateien                          |
| `/proc`     | Informationen über Prozesse und Kernel |
| `/mnt`      | temporäre Einhängepunkte               |
| `/media`    | automatisch eingehängte Medien         |

Diese Struktur ist wichtig, weil viele Dateien unter Linux feste typische Orte haben.

---

## Benutzer, Gruppen und Rechte

Linux ist ein Mehrbenutzersystem.

Das bedeutet, dass mehrere Benutzer auf einem System existieren können und jeder Benutzer unterschiedliche Rechte haben kann.

Wichtige Begriffe:

| Begriff  | Bedeutung                                   |
| -------- | ------------------------------------------- |
| Benutzer | Konto auf dem System                        |
| Gruppe   | Zusammenfassung mehrerer Benutzer           |
| Root     | administrativer Benutzer mit vollen Rechten |
| sudo     | temporäre Ausführung mit erhöhten Rechten   |
| Besitzer | Benutzer, dem eine Datei gehört             |
| Rechte   | steuern Lesen, Schreiben und Ausführen      |

Dateirechte sind ein zentrales Sicherheitskonzept unter Linux.

Beispiel:

```text
-rw-r--r--
```

Das zeigt, welche Rechte Besitzer, Gruppe und andere Benutzer auf eine Datei haben.

---

## Prozesse und Dienste

Ein Prozess ist ein laufendes Programm.

Ein Dienst ist ein Programm, das im Hintergrund läuft und eine Aufgabe erfüllt.

Beispiele für Dienste:

- SSH-Server
- Webserver
- Datenbankserver
- DNS-Dienst
- DHCP-Dienst
- Docker-Dienst
- Cron-Dienst

Mit `systemctl` werden Dienste verwaltet.

Beispiele:

```bash
systemctl status ssh
systemctl start ssh
systemctl stop ssh
systemctl restart ssh
systemctl enable ssh
```

Für FISI ist das wichtig, weil viele Serverdienste geprüft, gestartet, gestoppt oder neu geladen werden müssen.

---

## Paketverwaltung

Linux-Systeme installieren Software meistens über Paketmanager.

Bei Debian und Ubuntu wird häufig `apt` verwendet.

Typische Befehle:

```bash
sudo apt update
sudo apt upgrade
sudo apt install paketname
sudo apt remove paketname
apt search paketname
apt show paketname
```

Paketverwaltung ist wichtig für:

- Software installieren
- Updates einspielen
- Sicherheitsupdates durchführen
- Abhängigkeiten verwalten
- Pakete entfernen
- System aktuell halten

Ein nicht aktualisiertes System kann Sicherheitsrisiken enthalten.

---

## Netzwerk unter Linux

Linux bietet viele Werkzeuge zur Netzwerkanalyse.

Wichtige Befehle:

| Befehl              | Aufgabe                                |
| ------------------- | -------------------------------------- |
| `ip a`              | IP-Adressen anzeigen                   |
| `ip route`          | Routingtabelle anzeigen                |
| `ping`              | Erreichbarkeit testen                  |
| `traceroute`        | Weg zu einem Ziel prüfen               |
| `ss -tulpen`        | offene Ports und Verbindungen anzeigen |
| `resolvectl status` | DNS-Konfiguration anzeigen             |
| `hostname`          | Hostname anzeigen                      |
| `nmcli`             | NetworkManager verwalten               |
| `curl`              | HTTP-Verbindungen testen               |

Für FISI ist Netzwerkdiagnose unter Linux besonders wichtig, weil viele Serverprobleme durch DNS, Routing, Firewall, Dienste oder falsche IP-Konfiguration entstehen.

---

## Logs und Fehlersuche

Logs sind eine der wichtigsten Informationsquellen bei Fehlern.

Unter Linux liegen viele Logs unter:

```text
/var/log
```

Bei systemd-Systemen ist außerdem `journalctl` sehr wichtig.

Beispiele:

```bash
journalctl
journalctl -f
journalctl -u ssh
journalctl -xe
```

Logs helfen bei:

- Dienstfehlern
- fehlgeschlagenen Anmeldungen
- Netzwerkproblemen
- Systemstarts
- Paketproblemen
- Hardwaremeldungen
- Sicherheitsereignissen

Ein guter FISI schaut bei Fehlern nicht nur auf die Oberfläche, sondern prüft Logs, Dienste, Konfiguration und Systemzustand.

---

## Shell Scripting

Shell-Skripte automatisieren Befehle.

Ein Shell-Skript kann zum Beispiel:

- Dateien sichern
- Logs durchsuchen
- Dienste prüfen
- Reports erstellen
- Benutzerinformationen ausgeben
- Systeme vorbereiten
- wiederkehrende Befehle zusammenfassen

Ein einfaches Skript:

```bash
#!/bin/bash

echo "Systemstatus"
hostname
uptime
df -h
```

Shell Scripting ist wichtig, weil viele Admin-Aufgaben wiederkehrend sind. Automatisierung spart Zeit und reduziert Fehler.

---

## Linux im Zusammenhang mit Docker

Docker nutzt Linux-Konzepte sehr stark.

Wichtige Zusammenhänge:

- Container laufen auf Linux-Kernel-Funktionen
- Images enthalten Linux-Dateisysteme
- Prozesse im Container sind Linux-Prozesse
- Volumes hängen mit Dateisystemen zusammen
- Netzwerke in Docker basieren auf Linux-Netzwerkfunktionen
- Rechte und Benutzer spielen auch in Containern eine Rolle
- Logs und Prozesse müssen analysiert werden

Wer Linux besser versteht, versteht auch Docker, Serverbetrieb und DevOps-Grundlagen besser.

---

## Linux im FISI-Alltag

Typische FISI-Aufgaben mit Linux:

- SSH-Zugriff prüfen
- Dienste starten oder neu starten
- Logdateien analysieren
- Benutzer und Rechte prüfen
- Software installieren
- Updates durchführen
- Speicherplatz prüfen
- Netzwerkverbindung testen
- Firewall- oder Portprobleme eingrenzen
- Backups prüfen
- Skripte ausführen
- Docker-Container analysieren
- Serverdokumentation schreiben

Linux ist deshalb nicht nur ein einzelnes Thema, sondern eine Grundlage für viele andere IT-Bereiche.

---

## Typische Fehler beim Lernen von Linux

| Fehler                          | Problem                                                  |
| ------------------------------- | -------------------------------------------------------- |
| Befehle nur auswendig lernen    | ohne Verständnis schwer auf neue Situationen übertragbar |
| Pfade nicht verstehen           | Konfigurationsdateien und Logs werden schwer gefunden    |
| Rechte ignorieren               | viele Probleme entstehen durch falsche Berechtigungen    |
| immer sofort `sudo` nutzen      | Sicherheitsrisiko und schlechtes Verständnis             |
| Logs nicht lesen                | Fehlerursachen bleiben unklar                            |
| Befehle blind kopieren          | Gefahr von Datenverlust oder falscher Konfiguration      |
| Netzwerkgrundlagen überspringen | Serverprobleme werden schwer analysierbar                |
| Dokumentation weglassen         | spätere Fehlersuche wird schwieriger                     |

---

## Lernansatz

Dieser Bereich soll nicht nur Befehle sammeln.

Der Fokus liegt auf Verständnis und Praxis:

1. Was ist das Konzept?
2. Warum ist es wichtig?
3. Welche Dateien oder Dienste sind beteiligt?
4. Welche Befehle helfen?
5. Welche Fehler sind typisch?
6. Wie prüft man das in der Praxis?
7. Wie dokumentiert man das Ergebnis?

So entsteht Linux-Wissen, das man in echten Admin-Situationen verwenden kann.

---

## Kurze Zusammenfassung

Linux ist eine zentrale Grundlage für Systemadministration, Serverbetrieb, Container, Cloud und Automatisierung.

Wichtige Themen sind Terminal, Dateisystem, Rechte, Prozesse, Dienste, Paketverwaltung, Netzwerk, Logs, Fehlersuche und Shell Scripting.

Für Fachinformatiker für Systemintegration ist Linux besonders wichtig, weil viele produktive Systeme auf Linux laufen und viele Aufgaben im IT-Betrieb über das Terminal erledigt werden.
