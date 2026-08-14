# 1. Linux Grundlagen

In diesem Kapitel geht es um die wichtigsten Grundlagen von Linux.

Linux ist ein Betriebssystem, das besonders häufig auf Servern, in Cloud-Umgebungen, bei Containern, in Netzwerken und in der Softwareentwicklung eingesetzt wird. Für Fachinformatiker für Systemintegration ist Linux wichtig, weil viele professionelle IT-Systeme ohne grafische Oberfläche betrieben werden und über das Terminal administriert werden.

Dieses Kapitel erklärt die Grundidee von Linux, den Aufbau des Systems, wichtige Begriffe und die ersten Konzepte, die man für die spätere Administration verstehen muss.

---

## Kurz erklärt

Linux ist ein Betriebssystemkern, der zusammen mit vielen Programmen und Werkzeugen ein vollständiges Betriebssystem bildet.

Im Alltag sagt man meistens einfach „Linux“, obwohl damit oft eine komplette Linux-Distribution gemeint ist.

Beispiele für Linux-Distributionen:

- Ubuntu
- Debian
- Fedora
- Arch Linux
- openSUSE
- Red Hat Enterprise Linux
- Rocky Linux
- Kali Linux

Linux wird besonders häufig genutzt für:

- Server
- Webdienste
- Datenbanken
- Docker
- Cloud-Systeme
- Netzwerkdienste
- Firewalls
- Automatisierung
- Entwicklungsumgebungen
- Embedded Systeme

---

## Was ist ein Betriebssystem?

Ein Betriebssystem ist die grundlegende Software, die zwischen Hardware und Anwendungen steht.

Es verwaltet zum Beispiel:

- Prozessor
- Arbeitsspeicher
- Festplatten
- Dateien
- Benutzer
- Rechte
- Prozesse
- Netzwerk
- Geräte
- Dienste

Ohne Betriebssystem könnten Programme nicht sinnvoll mit der Hardware arbeiten.

Beispiele für Betriebssysteme:

| Betriebssystem | typische Nutzung                           |
| -------------- | ------------------------------------------ |
| Linux          | Server, Cloud, Container, Entwicklung      |
| Windows        | Clients, Büros, Windows-Server             |
| macOS          | Apple-Geräte, Entwicklung, kreative Arbeit |
| Android        | Smartphones und Tablets                    |
| iOS            | iPhones und iPads                          |

Linux ist besonders stark im Serverbereich, weil es stabil, flexibel, gut automatisierbar und ressourcenschonend ist.

---

## Kernel

Der Kernel ist der Kern eines Betriebssystems.

Er ist die zentrale Schicht zwischen Hardware und Software.

Aufgaben des Kernels:

- Prozesse verwalten
- Speicher verwalten
- Dateisysteme verwalten
- Gerätetreiber bereitstellen
- Netzwerkfunktionen ermöglichen
- Zugriffe auf Hardware kontrollieren
- Systemressourcen verteilen

Wenn ein Programm zum Beispiel eine Datei lesen will, spricht es nicht direkt mit der Festplatte. Es nutzt Systemfunktionen, die über den Kernel laufen.

Der Linux-Kernel ist also die technische Grundlage des Systems.

---

## Linux-Distribution

Eine Linux-Distribution ist ein vollständiges Betriebssystem auf Basis des Linux-Kernels.

Eine Distribution enthält zusätzlich zum Kernel viele weitere Bestandteile:

- Paketmanager
- Systemwerkzeuge
- Shell
- Standardprogramme
- Installationssystem
- Desktop-Umgebung, wenn gewünscht
- Konfigurationsdateien
- Dienste
- Sicherheitsupdates
- Dokumentation

Beispiel:

Ubuntu ist eine Distribution.
Debian ist eine Distribution.
Fedora ist eine Distribution.

Der Kernel ist nur ein Teil davon.

---

## Warum es viele Distributionen gibt

Es gibt viele Linux-Distributionen, weil unterschiedliche Einsatzzwecke verschiedene Schwerpunkte haben.

| Distribution             | typischer Schwerpunkt                                |
| ------------------------ | ---------------------------------------------------- |
| Ubuntu                   | einfacher Einstieg, Desktop, Server, große Community |
| Debian                   | Stabilität, Server, freie Software                   |
| Fedora                   | moderne Pakete, neue Technologien                    |
| Arch Linux               | hohe Kontrolle, Rolling Release                      |
| Red Hat Enterprise Linux | Unternehmensumgebungen, Support                      |
| Rocky Linux              | Enterprise-Server, RHEL-kompatibel                   |
| Kali Linux               | Security-Testing und Forensik                        |

Für FISI sind Ubuntu und Debian besonders gute Grundlagen, weil sie häufig in Lernumgebungen, Servern und Dokumentationen vorkommen.

---

## Open Source

Linux ist Open Source.

Das bedeutet, dass der Quellcode öffentlich einsehbar ist und von vielen Personen und Organisationen weiterentwickelt werden kann.

Vorteile von Open Source:

- Code kann geprüft werden
- große Community
- viele kostenlose Werkzeuge
- schnelle Fehlerbehebung durch viele Beteiligte
- hohe Anpassbarkeit
- keine Bindung an einen einzigen Hersteller
- gut für Lernen und Verständnis

Open Source bedeutet aber nicht automatisch, dass alles immer kostenlos, sicher oder professionell gepflegt ist.

Auch Open-Source-Software muss aktualisiert, geprüft und sinnvoll eingesetzt werden.

---

## Linux im Serverbereich

Linux wird sehr häufig auf Servern eingesetzt.

Gründe dafür:

- stabiler Betrieb
- gute Netzwerkfunktionen
- geringer Ressourcenverbrauch
- starke Automatisierung
- gute Rechteverwaltung
- viele Serverdienste verfügbar
- Paketverwaltung
- gute Fernadministration per SSH
- breite Nutzung in Cloud und Containern

Typische Linux-Serverdienste:

- Webserver
- Datenbankserver
- SSH-Server
- DNS-Server
- DHCP-Server
- Dateiserver
- Monitoring-Systeme
- Backup-Systeme
- Containerplattformen

Viele Server laufen ohne grafische Oberfläche. Deshalb ist das Terminal so wichtig.

---

## Linux und das Terminal

Das Terminal ist eine textbasierte Oberfläche, über die Befehle eingegeben werden.

Eine Shell verarbeitet diese Befehle.

Häufige Shells:

| Shell | Beschreibung                               |
| ----- | ------------------------------------------ |
| Bash  | sehr verbreitet unter Linux                |
| Zsh   | moderne Shell mit vielen Komfortfunktionen |
| Fish  | benutzerfreundliche Shell                  |
| Sh    | einfache klassische Shell                  |

Im FISI-Alltag ist Bash besonders wichtig.

Typische Aufgaben im Terminal:

- Dateien verwalten
- Dienste prüfen
- Logs anzeigen
- Pakete installieren
- Netzwerk testen
- Benutzer verwalten
- Rechte prüfen
- Prozesse anzeigen
- Skripte starten
- Server per SSH verwalten

Das Terminal wirkt am Anfang schwerer als eine grafische Oberfläche, ist aber sehr mächtig und schnell.

---

## Shell, Terminal und Konsole

Diese Begriffe werden oft ähnlich benutzt, bedeuten aber nicht exakt dasselbe.

| Begriff  | Bedeutung                                       |
| -------- | ----------------------------------------------- |
| Terminal | Programm oder Umgebung zur Texteingabe          |
| Shell    | Programm, das Befehle interpretiert             |
| Konsole  | direkte textbasierte Systemoberfläche           |
| Prompt   | Eingabezeile, an der Befehle geschrieben werden |

Beispiel für einen Prompt:

```text
bilgin@ubuntu:~$
```

Das bedeutet meistens:

- Benutzer: `bilgin`
- Hostname: `ubuntu`
- aktueller Ordner: `~`
- normaler Benutzer: `$`

Bei Root sieht man oft:

```text
root@ubuntu:~#
```

Das `#` zeigt häufig an, dass man mit administrativen Rechten arbeitet.

---

## Grundidee von Befehlen

Linux-Befehle folgen oft einem ähnlichen Aufbau.

Allgemeines Muster:

```bash
befehl optionen argumente
```

Beispiel:

```bash
ls -la /home
```

Bedeutung:

| Teil    | Erklärung                       |
| ------- | ------------------------------- |
| `ls`    | Befehl zum Anzeigen von Dateien |
| `-la`   | Optionen                        |
| `/home` | Argument, hier der Pfad         |

Viele Befehle haben Optionen, mit denen das Verhalten verändert wird.

Beispiel:

```bash
ls
ls -l
ls -a
ls -la
```

Der gleiche Befehl kann dadurch unterschiedliche Informationen anzeigen.

---

## Hilfe zu Befehlen

Unter Linux kann man Hilfe direkt im System abrufen.

Wichtige Möglichkeiten:

```bash
man ls
ls --help
help cd
```

Bedeutung:

| Befehl   | Aufgabe                         |
| -------- | ------------------------------- |
| `man`    | Handbuchseite anzeigen          |
| `--help` | kurze Hilfe zu einem Befehl     |
| `help`   | Hilfe für Shell-interne Befehle |

Beispiel:

```bash
man systemctl
```

Damit kann man die Dokumentation zu `systemctl` lesen.

Das ist wichtig, weil man nicht jeden Befehl auswendig wissen muss. Man muss wissen, wie man Informationen findet.

---

## Root und normale Benutzer

Linux unterscheidet normale Benutzer und administrative Rechte.

Der Benutzer `root` hat volle Kontrolle über das System.

Root kann:

- Systemdateien ändern
- Programme installieren
- Benutzer verwalten
- Dienste starten und stoppen
- Rechte verändern
- Dateien anderer Benutzer löschen
- Netzwerkkonfiguration ändern

Deshalb sollte man nicht dauerhaft als Root arbeiten.

Ein Fehler als Root kann das ganze System beschädigen.

---

## sudo

`sudo` erlaubt einem berechtigten Benutzer, einzelne Befehle mit administrativen Rechten auszuführen.

Beispiel:

```bash
sudo apt update
```

Das bedeutet:

Der Befehl `apt update` wird mit erhöhten Rechten ausgeführt.

`sudo` ist wichtig, weil man normalerweise als normaler Benutzer arbeitet und nur bei Bedarf Adminrechte nutzt.

Typische Aufgaben mit `sudo`:

- Pakete installieren
- Dienste verwalten
- Systemdateien bearbeiten
- Rechte ändern
- Netzwerkdienste konfigurieren

Wichtig:

Man sollte `sudo` bewusst verwenden und nicht einfach vor jeden Befehl schreiben.

---

## Dateisystem-Grundidee

Linux hat ein hierarchisches Dateisystem.

Alles beginnt bei:

```text
/
```

Dieses Verzeichnis nennt man Wurzelverzeichnis oder Root-Verzeichnis.

Darunter liegen alle anderen Verzeichnisse.

Beispiele:

```text
/home
/etc
/var
/usr
/tmp
/root
```

Anders als bei Windows gibt es keine Laufwerke wie `C:` oder `D:` als Hauptstruktur.

Auch Festplatten, USB-Sticks und Netzlaufwerke werden in die Verzeichnisstruktur eingehängt.

---

## Wichtige Verzeichnisse

| Verzeichnis | Bedeutung                            |
| ----------- | ------------------------------------ |
| `/`         | Wurzel des gesamten Dateisystems     |
| `/home`     | persönliche Ordner normaler Benutzer |
| `/root`     | Home-Verzeichnis des Root-Benutzers  |
| `/etc`      | Konfigurationsdateien                |
| `/var`      | veränderliche Daten                  |
| `/var/log`  | Logdateien                           |
| `/tmp`      | temporäre Dateien                    |
| `/usr`      | Programme und Bibliotheken           |
| `/bin`      | wichtige Benutzerprogramme           |
| `/sbin`     | wichtige Systemprogramme             |
| `/opt`      | zusätzliche Software                 |
| `/dev`      | Gerätedateien                        |
| `/proc`     | Kernel- und Prozessinformationen     |
| `/mnt`      | manuelle Einhängepunkte              |
| `/media`    | automatisch eingebundene Medien      |

Diese Struktur ist eine Grundlage für Linux-Administration.

Viele Probleme löst man schneller, wenn man weiß, wo man suchen muss.

---

## Pfade

Ein Pfad beschreibt den Ort einer Datei oder eines Ordners.

Es gibt absolute und relative Pfade.

Absoluter Pfad:

```text
/home/bilgin/documents/file.txt
```

Ein absoluter Pfad beginnt immer bei `/`.

Relativer Pfad:

```text
documents/file.txt
```

Ein relativer Pfad beginnt vom aktuellen Verzeichnis aus.

Wichtige Kurzformen:

| Zeichen | Bedeutung                                |
| ------- | ---------------------------------------- |
| `.`     | aktuelles Verzeichnis                    |
| `..`    | übergeordnetes Verzeichnis               |
| `~`     | Home-Verzeichnis des aktuellen Benutzers |
| `/`     | Wurzelverzeichnis                        |

Beispiel:

```bash
cd ~
cd ..
cd /etc
```

---

## Groß- und Kleinschreibung

Linux unterscheidet zwischen Groß- und Kleinschreibung.

Diese Dateien wären unterschiedliche Dateien:

```text
README.md
readme.md
Readme.md
```

Das ist wichtig, weil Fehler durch falsche Schreibweise entstehen können.

Beispiel:

```bash
cd Downloads
```

ist nicht dasselbe wie:

```bash
cd downloads
```

Wenn ein Ordner `Downloads` heißt, funktioniert `downloads` nicht.

---

## Dateien unter Linux

Unter Linux ist fast alles als Datei sichtbar.

Dazu gehören:

- normale Dateien
- Verzeichnisse
- Geräte
- Prozesse
- Systeminformationen
- Konfigurationen
- Logs

Diese Idee ist wichtig, weil viele Systeminformationen über Dateien gelesen werden können.

Beispiele:

```text
/etc/hostname
/etc/passwd
/var/log/syslog
/proc/cpuinfo
```

Auch Hardwaregeräte erscheinen als Dateien unter `/dev`.

---

## Dateiendungen

Linux braucht Dateiendungen technisch nicht immer so stark wie Windows.

Eine Datei kann auch ohne Endung ausführbar sein.

Trotzdem werden Endungen häufig genutzt, damit Menschen und Programme den Typ besser erkennen.

Beispiele:

| Endung  | Bedeutung           |
| ------- | ------------------- |
| `.txt`  | Textdatei           |
| `.log`  | Logdatei            |
| `.conf` | Konfigurationsdatei |
| `.sh`   | Shell-Skript        |
| `.py`   | Python-Datei        |
| `.md`   | Markdown-Datei      |
| `.yaml` | YAML-Konfiguration  |
| `.json` | JSON-Datei          |

Wichtiger als die Endung sind unter Linux oft Rechte und Inhalt der Datei.

---

## Rechte-Grundidee

Linux nutzt Rechte, um Zugriff auf Dateien und Ordner zu steuern.

Drei Grundrechte:

| Recht | Bedeutung          |
| ----- | ------------------ |
| `r`   | read, lesen        |
| `w`   | write, schreiben   |
| `x`   | execute, ausführen |

Diese Rechte gelten für:

| Bereich  | Bedeutung                  |
| -------- | -------------------------- |
| Besitzer | Eigentümer der Datei       |
| Gruppe   | zugeordnete Benutzergruppe |
| Andere   | alle anderen Benutzer      |

Beispiel:

```text
-rw-r--r--
```

Das bedeutet:

- Besitzer darf lesen und schreiben
- Gruppe darf lesen
- andere dürfen lesen
- niemand darf ausführen

Dateirechte sind ein zentrales Sicherheitskonzept unter Linux.

---

## Prozesse

Ein Prozess ist ein laufendes Programm.

Beispiele:

- Terminal
- Webserver
- SSH-Dienst
- Datenbank
- Browser
- Python-Skript
- Docker-Containerprozess

Prozesse haben eine Prozess-ID, kurz PID.

Wichtige Befehle:

```bash
ps aux
top
htop
kill PID
```

Prozesse sind wichtig, weil man im Betrieb oft prüfen muss, ob ein Programm läuft, wie viele Ressourcen es nutzt oder ob es beendet werden muss.

---

## Dienste

Ein Dienst ist ein Programm, das meist im Hintergrund läuft.

Beispiele:

- SSH
- Apache
- Nginx
- Docker
- PostgreSQL
- MariaDB
- Cron

Viele moderne Linux-Systeme verwenden `systemd` zur Verwaltung von Diensten.

Wichtige Befehle:

```bash
systemctl status ssh
sudo systemctl start ssh
sudo systemctl stop ssh
sudo systemctl restart ssh
sudo systemctl enable ssh
```

Dienste sind besonders wichtig im Serverbetrieb.

Ein Webserver, der nicht läuft, kann keine Webseite ausliefern.
Ein SSH-Dienst, der nicht läuft, erlaubt keine Remote-Anmeldung.

---

## Logs

Logs sind Protokolle über Ereignisse im System.

Sie helfen bei der Fehlersuche.

Wichtige Orte und Befehle:

```bash
ls /var/log
journalctl
journalctl -f
journalctl -u ssh
```

Logs können zeigen:

- Dienst startet nicht
- Anmeldung fehlgeschlagen
- Netzwerkproblem
- Festplatte voll
- Paketinstallation fehlgeschlagen
- System wurde neu gestartet
- Sicherheitsereignisse

Ein guter Admin liest Logs, statt nur zu raten.

---

## Paketverwaltung

Software wird unter Linux meistens über Paketmanager installiert.

Bei Ubuntu und Debian ist `apt` sehr wichtig.

Beispiele:

```bash
sudo apt update
sudo apt upgrade
sudo apt install nginx
sudo apt remove nginx
apt search nginx
apt show nginx
```

Bedeutung:

| Befehl        | Aufgabe                           |
| ------------- | --------------------------------- |
| `apt update`  | Paketlisten aktualisieren         |
| `apt upgrade` | installierte Pakete aktualisieren |
| `apt install` | Paket installieren                |
| `apt remove`  | Paket entfernen                   |
| `apt search`  | Paket suchen                      |
| `apt show`    | Paketinformationen anzeigen       |

Paketmanager lösen auch Abhängigkeiten.

Das bedeutet: Wenn ein Programm andere Pakete braucht, werden diese oft automatisch mitinstalliert.

---

## Netzwerk-Grundlagen unter Linux

Linux-Systeme sind oft Teil eines Netzwerks.

Wichtige Informationen:

- IP-Adresse
- Subnetz
- Gateway
- DNS
- Routingtabelle
- offene Ports
- aktive Verbindungen
- Hostname

Wichtige Befehle:

```bash
ip a
ip route
ping 8.8.8.8
traceroute 8.8.8.8
ss -tulpen
resolvectl status
hostname
```

Diese Befehle helfen, Netzwerkprobleme einzugrenzen.

Beispiel:

Wenn `ping 8.8.8.8` funktioniert, aber `ping google.com` nicht, könnte DNS das Problem sein.

---

## SSH

SSH bedeutet Secure Shell.

SSH wird genutzt, um sich sicher auf entfernte Systeme zu verbinden.

Beispiel:

```bash
ssh user@server
```

SSH ist sehr wichtig für Serveradministration.

Mit SSH kann man:

- entfernte Server verwalten
- Befehle ausführen
- Dateien übertragen
- Dienste prüfen
- Logs lesen
- Konfigurationen bearbeiten

Der SSH-Dienst auf dem Server muss laufen, damit eine Verbindung möglich ist.

Prüfen:

```bash
systemctl status ssh
```

---

## Konfigurationsdateien

Linux speichert viele Einstellungen in Textdateien.

Typische Orte:

```text
/etc
/etc/ssh/sshd_config
/etc/hosts
/etc/fstab
/etc/netplan
```

Vorteile:

- gut lesbar
- versionierbar
- per SSH bearbeitbar
- automatisierbar
- dokumentierbar

Wichtig:

Vor Änderungen an wichtigen Konfigurationsdateien sollte man ein Backup erstellen.

Beispiel:

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
```

So kann man bei Fehlern zur alten Version zurückkehren.

---

## Linux und Sicherheit

Linux bietet viele Sicherheitsmechanismen.

Wichtige Grundlagen:

- Benutzer und Gruppen
- Dateirechte
- sudo
- Dienste nur bei Bedarf aktivieren
- Updates einspielen
- Firewall nutzen
- SSH absichern
- Logs prüfen
- starke Passwörter oder SSH-Keys
- keine unnötigen Root-Sitzungen
- sensible Dateien schützen

Sicherheit bedeutet nicht nur ein Tool zu installieren.

Sicherheit entsteht durch saubere Konfiguration, Updates, Rechte, Monitoring und bewusstes Arbeiten.

---

## Linux und Automatisierung

Linux eignet sich sehr gut für Automatisierung.

Gründe:

- viele Aufgaben über Befehle steuerbar
- Shell-Skripte möglich
- Konfigurationsdateien sind Text
- Remote-Administration per SSH
- Cronjobs für regelmäßige Aufgaben
- viele Tools lassen sich kombinieren

Beispiel:

```bash
grep "ERROR" /var/log/syslog
```

Dieser Befehl sucht nach Fehlern in einer Logdatei.

Mehrere Befehle können später in Skripten kombiniert werden.

---

## Linux und Docker

Docker nutzt viele Linux-Grundlagen.

Wichtige Zusammenhänge:

- Container sind Prozesse
- Images enthalten Dateisysteme
- Volumes nutzen Speicherbereiche
- Netzwerke basieren auf Linux-Netzwerkfunktionen
- Logs können über Docker und Linux geprüft werden
- Rechte und Benutzer spielen auch in Containern eine Rolle

Wer Linux versteht, versteht Docker schneller.

Viele Docker-Probleme sind eigentlich Linux-Probleme:

- Port belegt
- Datei nicht gefunden
- falsche Rechte
- Volume falsch eingebunden
- Prozess beendet
- DNS funktioniert nicht
- Netzwerk nicht erreichbar

---

## Typische erste Befehle

Diese Befehle gehören zu den wichtigsten Grundlagen:

| Befehl             | Bedeutung                                            |
| ------------------ | ---------------------------------------------------- |
| `pwd`              | aktuellen Ordner anzeigen                            |
| `ls`               | Dateien anzeigen                                     |
| `ls -la`           | Dateien mit Details und versteckten Dateien anzeigen |
| `cd`               | Ordner wechseln                                      |
| `mkdir`            | Ordner erstellen                                     |
| `touch`            | Datei erstellen                                      |
| `cat`              | Datei ausgeben                                       |
| `less`             | Datei seitenweise anzeigen                           |
| `cp`               | kopieren                                             |
| `mv`               | verschieben oder umbenennen                          |
| `rm`               | löschen                                              |
| `whoami`           | aktuellen Benutzer anzeigen                          |
| `hostname`         | Hostnamen anzeigen                                   |
| `uptime`           | Laufzeit des Systems anzeigen                        |
| `df -h`            | Speicherplatz anzeigen                               |
| `free -h`          | Arbeitsspeicher anzeigen                             |
| `ip a`             | IP-Adressen anzeigen                                 |
| `systemctl status` | Dienststatus prüfen                                  |

Diese Befehle sind die Grundlage für spätere Kapitel.

---

## Arbeiten mit Vorsicht

Einige Befehle können gefährlich sein, wenn man sie falsch nutzt.

Beispiele:

```bash
rm -rf
sudo
chmod -R
chown -R
dd
mkfs
```

Diese Befehle können Dateien löschen, Rechte falsch setzen oder Datenträger überschreiben.

Deshalb gilt:

- Befehl verstehen, bevor man ihn ausführt
- Pfad genau prüfen
- bei Unsicherheit erst mit ungefährlichen Befehlen prüfen
- Backups machen
- nicht blind kopieren
- vorsichtig mit `sudo` sein

Linux gibt viel Kontrolle.
Mit viel Kontrolle kommt auch Verantwortung.

---

## Typische Fehler am Anfang

| Fehler                               | Problem                                   |
| ------------------------------------ | ----------------------------------------- |
| Groß- und Kleinschreibung ignorieren | Dateien oder Ordner werden nicht gefunden |
| falschen Pfad nutzen                 | Befehl wirkt an falscher Stelle           |
| immer `sudo` verwenden               | Rechteverständnis bleibt schwach          |
| Logs nicht prüfen                    | Fehlerursache bleibt unklar               |
| `rm` unvorsichtig nutzen             | Datenverlust möglich                      |
| Rechte falsch setzen                 | Sicherheits- oder Funktionsprobleme       |
| Paketlisten nicht aktualisieren      | Pakete werden nicht gefunden              |
| Netzwerk nur mit Browser prüfen      | DNS, Gateway oder Routing bleiben unklar  |
| Terminalausgaben nicht lesen         | wichtige Hinweise werden übersehen        |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Linux eine wichtige Grundlage.

In der Praxis bedeutet das:

- Server per SSH verwalten
- Dienste prüfen und neu starten
- Logs lesen
- Benutzer und Rechte verstehen
- Pakete installieren
- Updates durchführen
- Netzwerk prüfen
- Speicherplatz überwachen
- Fehler systematisch eingrenzen
- Konfigurationsdateien bearbeiten
- einfache Skripte schreiben
- Docker besser verstehen
- Systeme dokumentieren

Ein guter FISI kennt nicht nur Befehle, sondern versteht, warum ein Befehl genutzt wird und welche Information er liefert.

---

## Kurze Zusammenfassung

Linux ist ein wichtiges Betriebssystem für Server, Cloud, Container, Netzwerke und Automatisierung.

Die wichtigsten Grundlagen sind Kernel, Distributionen, Terminal, Shell, Benutzer, Rechte, Dateisystem, Prozesse, Dienste, Logs, Paketverwaltung, Netzwerk und SSH.

Für FISI ist Linux besonders wichtig, weil viele produktive Systeme auf Linux laufen und viele Administrationsaufgaben über das Terminal erledigt werden.
