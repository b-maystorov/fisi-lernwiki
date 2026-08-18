# 2. Dateisystem und Pfade

In diesem Kapitel geht es um das Linux-Dateisystem und den sicheren Umgang mit Pfaden.

Das Dateisystem ist eine der wichtigsten Grundlagen unter Linux. Fast alles wird über Dateien, Ordner und Pfade organisiert: Programme, Konfigurationen, Logs, Benutzerdateien, Geräte, Prozesse und Systeminformationen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Administrationsaufgaben davon abhängen, Dateien und Verzeichnisse schnell zu finden, Pfade richtig zu verstehen und typische Systemorte zu kennen.

---

## Kurz erklärt

Linux nutzt ein hierarchisches Dateisystem.

Das bedeutet:

- alles beginnt im Wurzelverzeichnis `/`
- darunter liegen alle weiteren Verzeichnisse
- Dateien und Ordner werden über Pfade angesprochen
- Konfigurationen liegen oft unter `/etc`
- Logs liegen oft unter `/var/log`
- Benutzerdateien liegen unter `/home`
- Programme und Bibliotheken liegen häufig unter `/usr`
- temporäre Dateien liegen unter `/tmp`
- Geräte erscheinen unter `/dev`

Im Gegensatz zu Windows gibt es unter Linux keine Laufwerke wie `C:` oder `D:` als Hauptstruktur. Auch zusätzliche Festplatten, USB-Sticks oder Netzlaufwerke werden in die bestehende Verzeichnisstruktur eingehängt.

---

## Das Wurzelverzeichnis `/`

Das Wurzelverzeichnis ist der oberste Punkt im Linux-Dateisystem.

Es wird mit einem einfachen Schrägstrich dargestellt:

```text
/
```

Alle anderen Dateien und Ordner liegen unterhalb davon.

Beispiele:

```text
/home
/etc
/var
/usr
/tmp
/root
```

Das Wurzelverzeichnis ist nicht das gleiche wie der Root-Benutzer.

| Begriff | Bedeutung                           |
| ------- | ----------------------------------- |
| `/`     | Wurzelverzeichnis des Dateisystems  |
| `root`  | administrativer Benutzer            |
| `/root` | Home-Verzeichnis des Root-Benutzers |

Diese Begriffe werden oft verwechselt.

---

## Hierarchische Struktur

Linux organisiert Dateien in einer Baumstruktur.

Beispiel:

```text
/
├── home
│   └── bilgin
│       ├── Documents
│       └── Downloads
├── etc
│   ├── hostname
│   └── ssh
├── var
│   └── log
└── usr
    └── bin
```

Jeder Ordner kann weitere Ordner und Dateien enthalten.

Ein Pfad beschreibt dann den genauen Ort einer Datei oder eines Ordners.

Beispiel:

```text
/home/bilgin/Documents/report.md
```

Dieser Pfad bedeutet:

- beginne bei `/`
- gehe nach `home`
- gehe nach `bilgin`
- gehe nach `Documents`
- dort liegt die Datei `report.md`

---

## Absolute Pfade

Ein absoluter Pfad beginnt immer beim Wurzelverzeichnis `/`.

Beispiele:

```text
/home/bilgin
/etc/ssh/sshd_config
/var/log/syslog
/usr/bin/python3
/tmp/test.txt
```

Absolute Pfade sind eindeutig.

Egal, in welchem Verzeichnis man sich gerade befindet, ein absoluter Pfad zeigt immer auf denselben Ort.

Beispiel:

```bash
cat /etc/hostname
```

Dieser Befehl funktioniert von jedem aktuellen Verzeichnis aus, weil `/etc/hostname` ein absoluter Pfad ist.

---

## Relative Pfade

Ein relativer Pfad beginnt vom aktuellen Verzeichnis aus.

Beispiel:

Aktueller Ordner:

```text
/home/bilgin
```

Relativer Pfad:

```text
Documents/report.md
```

Vollständiger absoluter Pfad wäre:

```text
/home/bilgin/Documents/report.md
```

Relative Pfade sind praktisch, wenn man gerade in einem Projektordner arbeitet.

Beispiel:

```bash
cd ~/github/private/fisi-lernwiki
cat linux/README.md
```

Hier ist `linux/README.md` relativ zum aktuellen Projektordner.

---

## Aktuelles Verzeichnis anzeigen

Mit `pwd` sieht man, in welchem Verzeichnis man sich gerade befindet.

```bash
pwd
```

Beispielausgabe:

```text
/home/bilgin/github/private/fisi-lernwiki
```

`pwd` bedeutet **print working directory**.

Das ist einer der wichtigsten Befehle, wenn man unsicher ist, wo man gerade arbeitet.

Vor gefährlichen Befehlen wie `rm`, `mv`, `chmod` oder `chown` sollte man oft zuerst mit `pwd` prüfen, ob man im richtigen Ordner ist.

---

## Verzeichnis wechseln

Mit `cd` wechselt man das Verzeichnis.

Beispiele:

```bash
cd /etc
cd /var/log
cd ~/Downloads
cd ..
cd -
```

Wichtige Varianten:

| Befehl    | Bedeutung                             |
| --------- | ------------------------------------- |
| `cd /etc` | in `/etc` wechseln                    |
| `cd ..`   | ein Verzeichnis nach oben             |
| `cd ~`    | ins eigene Home-Verzeichnis           |
| `cd`      | ebenfalls ins eigene Home-Verzeichnis |
| `cd -`    | zurück ins vorherige Verzeichnis      |

`cd` ist ein Shell-Befehl. Deshalb gibt es dafür oft Hilfe mit:

```bash
help cd
```

---

## Wichtige Pfadzeichen

Linux nutzt einige besondere Zeichen für Pfade.

| Zeichen | Bedeutung                                            |
| ------- | ---------------------------------------------------- |
| `/`     | Wurzelverzeichnis oder Trennzeichen zwischen Ordnern |
| `.`     | aktuelles Verzeichnis                                |
| `..`    | übergeordnetes Verzeichnis                           |
| `~`     | Home-Verzeichnis des aktuellen Benutzers             |
| `-`     | bei `cd -`: vorheriges Verzeichnis                   |

Beispiele:

```bash
cd .
cd ..
cd ~
cd -
```

In normalen Pfaden trennt `/` die Verzeichnisse.

Beispiel:

```text
/home/bilgin/Documents
```

Windows nutzt oft `\`, Linux nutzt `/`.

---

## Das Home-Verzeichnis

Das Home-Verzeichnis ist der persönliche Bereich eines Benutzers.

Normale Benutzer haben ihr Home-Verzeichnis meistens unter:

```text
/home/benutzername
```

Beispiel:

```text
/home/bilgin
```

Die Kurzform dafür ist:

```text
~
```

Beispiele:

```bash
cd ~
cd ~/Downloads
touch ~/test.txt
```

Das Home-Verzeichnis enthält oft:

- persönliche Dateien
- Downloads
- Dokumente
- Benutzerkonfigurationen
- SSH-Schlüssel
- Git-Projekte
- versteckte Konfigurationsordner

---

## Das Root-Home `/root`

Der Root-Benutzer hat ein eigenes Home-Verzeichnis:

```text
/root
```

Das ist nicht dasselbe wie `/`.

| Pfad           | Bedeutung                              |
| -------------- | -------------------------------------- |
| `/`            | Wurzelverzeichnis des gesamten Systems |
| `/root`        | Home-Verzeichnis des Root-Benutzers    |
| `/home/bilgin` | Home-Verzeichnis des Benutzers Bilgin  |

Normale Benutzer haben meistens keinen Zugriff auf `/root`.

Das ist aus Sicherheitsgründen sinnvoll.

---

## Wichtige Systemverzeichnisse

Linux hat typische Standardverzeichnisse.

| Verzeichnis | Bedeutung                                    |
| ----------- | -------------------------------------------- |
| `/home`     | Home-Verzeichnisse normaler Benutzer         |
| `/root`     | Home-Verzeichnis des Root-Benutzers          |
| `/etc`      | Konfigurationsdateien                        |
| `/var`      | veränderliche Daten                          |
| `/var/log`  | Logdateien                                   |
| `/tmp`      | temporäre Dateien                            |
| `/usr`      | Programme, Bibliotheken und gemeinsame Daten |
| `/usr/bin`  | viele normale Programme                      |
| `/bin`      | grundlegende Programme                       |
| `/sbin`     | Systemprogramme                              |
| `/opt`      | optionale zusätzliche Software               |
| `/dev`      | Gerätedateien                                |
| `/proc`     | Kernel- und Prozessinformationen             |
| `/sys`      | System- und Hardwareinformationen            |
| `/mnt`      | manuelle Einhängepunkte                      |
| `/media`    | automatisch eingebundene Medien              |

Diese Struktur muss man nicht sofort komplett auswendig können. Wichtig ist, die wichtigsten Orte einordnen zu können.

---

## `/etc`

Unter `/etc` liegen viele Konfigurationsdateien.

Beispiele:

```text
/etc/hostname
/etc/hosts
/etc/passwd
/etc/group
/etc/ssh/sshd_config
/etc/fstab
```

Typische Aufgaben:

- Hostname prüfen
- SSH-Konfiguration bearbeiten
- Benutzer- und Gruppendateien verstehen
- Netzwerkkonfiguration finden
- Dienste konfigurieren
- Systemweite Einstellungen prüfen

Wichtig:

Vor Änderungen an Konfigurationsdateien sollte man ein Backup erstellen.

Beispiel:

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
```

So kann man bei Fehlern zur alten Version zurückkehren.

---

## `/var`

Unter `/var` liegen Daten, die sich während des Betriebs häufig ändern.

Beispiele:

```text
/var/log
/var/cache
/var/spool
/var/lib
```

Typische Inhalte:

- Logs
- Cache-Dateien
- Paketinformationen
- Daten von Diensten
- Warteschlangen
- Datenbanken oder Anwendungsdaten

Für Server ist `/var` besonders wichtig, weil dort viele laufende Dienste Daten speichern.

Wenn `/var` voll ist, können Dienste Probleme bekommen.

---

## `/var/log`

Unter `/var/log` liegen viele Logdateien.

Beispiele:

```text
/var/log/syslog
/var/log/auth.log
/var/log/kern.log
/var/log/apt
```

Logs helfen bei der Fehlersuche.

Beispiele:

```bash
ls /var/log
less /var/log/syslog
sudo less /var/log/auth.log
```

Auf Systemen mit systemd ist zusätzlich `journalctl` sehr wichtig.

```bash
journalctl
journalctl -u ssh
journalctl -f
```

Ein guter FISI prüft bei Fehlern oft zuerst Dienste, Logs und Konfiguration.

---

## `/tmp`

`/tmp` ist für temporäre Dateien gedacht.

Beispiele:

```text
/tmp/test.txt
/tmp/script-output.log
```

Viele Programme nutzen `/tmp`, um vorübergehend Daten zu speichern.

Wichtig:

- Dateien in `/tmp` sind nicht für dauerhafte Speicherung gedacht.
- Das System kann `/tmp` beim Neustart oder regelmäßig leeren.
- Sensible Daten sollten dort nicht ungeschützt liegen.

Für Tests ist `/tmp` praktisch, aber nicht für wichtige Dokumente oder dauerhafte Konfigurationen.

---

## `/usr`

Unter `/usr` liegen viele Programme, Bibliotheken und gemeinsame Dateien.

Wichtige Unterordner:

| Pfad         | Bedeutung                              |
| ------------ | -------------------------------------- |
| `/usr/bin`   | viele ausführbare Programme            |
| `/usr/sbin`  | Systemprogramme                        |
| `/usr/lib`   | Bibliotheken                           |
| `/usr/share` | gemeinsame Daten, Dokumentation, Icons |

Beispiel:

```bash
which python3
```

Mögliche Ausgabe:

```text
/usr/bin/python3
```

Das zeigt, wo das Programm `python3` liegt.

---

## `/bin` und `/sbin`

Unter `/bin` liegen wichtige Programme für normale Benutzer.

Beispiele:

```text
/bin/ls
/bin/cp
/bin/mv
/bin/bash
```

Unter `/sbin` liegen oft Systemprogramme.

Beispiele:

```text
/sbin/reboot
/sbin/shutdown
```

Auf modernen Linux-Systemen sind `/bin` und `/sbin` manchmal symbolische Links auf Verzeichnisse unter `/usr`.

Trotzdem sind diese Pfade wichtig, weil sie in vielen Dokumentationen und Skripten vorkommen.

---

## `/opt`

Unter `/opt` wird häufig optionale Software installiert.

Beispiele:

```text
/opt/programname
/opt/vendorname
```

Dieser Ordner wird oft genutzt, wenn Software nicht direkt über den Paketmanager installiert wird.

Beispiele:

- zusätzliche Tools
- Herstellersoftware
- manuell installierte Anwendungen

Für FISI ist wichtig, zwischen Paketmanager-Software und manuell installierter Software zu unterscheiden.

Manuell installierte Software muss oft gesondert dokumentiert und aktualisiert werden.

---

## `/dev`

Unter `/dev` erscheinen Gerätedateien.

Beispiele:

```text
/dev/sda
/dev/sdb
/dev/null
/dev/tty
```

Linux behandelt viele Geräte wie Dateien.

Beispiele für Geräte:

- Festplatten
- Partitionen
- Terminals
- virtuelle Geräte

Wichtig:

Man sollte nicht blind Befehle auf Gerätedateien ausführen.

Ein Befehl wie `dd` auf das falsche Gerät kann Daten zerstören.

---

## `/proc`

`/proc` ist ein virtuelles Dateisystem.

Es enthält Informationen über laufende Prozesse und den Kernel.

Beispiele:

```text
/proc/cpuinfo
/proc/meminfo
/proc/uptime
```

Man kann Informationen mit `cat` anzeigen:

```bash
cat /proc/cpuinfo
cat /proc/meminfo
```

Diese Dateien liegen nicht wie normale Dateien dauerhaft auf der Festplatte.

Sie werden vom Kernel bereitgestellt.

---

## `/mnt` und `/media`

Diese Verzeichnisse werden für eingehängte Dateisysteme genutzt.

| Pfad     | typische Nutzung               |
| -------- | ------------------------------ |
| `/mnt`   | manuelle Mountpoints           |
| `/media` | automatisch eingehängte Medien |

Beispiele:

```text
/mnt/backup
/media/bilgin/USB-STICK
```

Ein Mountpoint ist ein Ordner, an dem ein anderes Dateisystem sichtbar wird.

Zum Beispiel kann ein USB-Stick unter `/media/...` erscheinen.

---

## Mountpoints

Unter Linux werden zusätzliche Datenträger in die Verzeichnisstruktur eingehängt.

Das nennt man **mounten**.

Beispiele für Datenträger:

- zweite Festplatte
- USB-Stick
- externe SSD
- Netzlaufwerk
- ISO-Datei
- Docker-Volume

Befehle zum Prüfen:

```bash
lsblk
df -h
mount
findmnt
```

Bedeutung:

| Befehl    | Aufgabe                                             |
| --------- | --------------------------------------------------- |
| `lsblk`   | Blockgeräte und Partitionen anzeigen                |
| `df -h`   | eingehängte Dateisysteme und Speicherplatz anzeigen |
| `mount`   | aktuell eingehängte Dateisysteme anzeigen           |
| `findmnt` | Mountpoints übersichtlich anzeigen                  |

Mountpoints sind wichtig, weil Speicher nicht immer direkt dort liegt, wo der Pfad aussieht.

---

## Speicherplatz prüfen

Mit `df -h` prüft man belegten Speicherplatz.

```bash
df -h
```

Beispielausgabe:

```text
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        50G   20G   28G  42% /
/dev/sdb1       200G   80G  120G  40% /mnt/data
```

Wichtig ist die Spalte `Mounted on`.

Sie zeigt, wo ein Dateisystem eingehängt ist.

Wenn ein Server Probleme hat, ist voller Speicherplatz eine häufige Ursache.

---

## Verzeichnisgröße prüfen

Mit `du` prüft man, wie viel Speicher Ordner oder Dateien belegen.

Beispiele:

```bash
du -sh /var/log
du -sh *
```

Bedeutung:

| Option | Bedeutung                             |
| ------ | ------------------------------------- |
| `-s`   | zusammengefasste Ausgabe              |
| `-h`   | menschenlesbare Größen wie MB oder GB |

Beispiel:

```bash
du -sh ~/Downloads
```

Das zeigt, wie viel Speicher der Downloads-Ordner belegt.

---

## Versteckte Dateien

Unter Linux sind Dateien und Ordner versteckt, wenn ihr Name mit einem Punkt beginnt.

Beispiele:

```text
.bashrc
.profile
.ssh
.git
.config
```

Diese Dateien sieht man nicht mit einfachem `ls`.

Man nutzt:

```bash
ls -a
ls -la
```

Versteckte Dateien enthalten oft Benutzerkonfigurationen.

Beispiele:

| Datei / Ordner | Bedeutung                           |
| -------------- | ----------------------------------- |
| `.bashrc`      | Bash-Konfiguration                  |
| `.ssh`         | SSH-Schlüssel und SSH-Konfiguration |
| `.git`         | Git-Repositorydaten                 |
| `.config`      | Benutzerkonfigurationen             |
| `.profile`     | Login-Konfiguration                 |

Versteckt bedeutet nicht geheim oder sicher. Es bedeutet nur, dass die Datei in normalen Listen ausgeblendet wird.

---

## Groß- und Kleinschreibung

Linux unterscheidet Groß- und Kleinschreibung.

Diese Namen sind verschieden:

```text
README.md
readme.md
Readme.md
```

Auch diese Ordner wären unterschiedlich:

```text
Downloads
downloads
```

Das ist eine häufige Fehlerquelle, besonders wenn man von Windows kommt.

Beispiel:

```bash
cd downloads
```

funktioniert nicht, wenn der Ordner eigentlich `Downloads` heißt.

---

## Leerzeichen in Dateinamen

Dateinamen können Leerzeichen enthalten, aber im Terminal ist das oft unpraktisch.

Beispiel:

```text
mein dokument.txt
```

Wenn man den Namen im Terminal nutzt, muss man ihn schützen.

Variante mit Anführungszeichen:

```bash
cat "mein dokument.txt"
```

Variante mit Backslash:

```bash
cat mein\ dokument.txt
```

Für IT-Projekte sind Namen ohne Leerzeichen oft einfacher.

Besser:

```text
mein-dokument.txt
mein_dokument.txt
```

---

## Sonderzeichen in Dateinamen

In Dateinamen sollte man Sonderzeichen möglichst vermeiden, besonders in Projekten, Skripten und Serverumgebungen.

Problematisch können sein:

```text
Leerzeichen
Umlaute
*
?
:
;
&
$
"
'
\
```

Besser sind einfache Namen mit:

- Kleinbuchstaben
- Zahlen
- Bindestrich
- Unterstrich
- Punkt für Endungen

Beispiele:

```text
linux-grundlagen.md
backup-script.sh
server-log.txt
inventory_data.csv
```

Klare Dateinamen reduzieren Fehler in Skripten, Git, Docker und Dokumentation.

---

## Dateiendungen

Linux benötigt Dateiendungen nicht immer zwingend.

Eine Datei kann auch ohne Endung ausführbar sein, wenn sie passende Rechte hat.

Trotzdem sind Endungen nützlich für Menschen und Programme.

| Endung  | Bedeutung           |
| ------- | ------------------- |
| `.txt`  | Textdatei           |
| `.md`   | Markdown            |
| `.sh`   | Shell-Skript        |
| `.py`   | Python-Datei        |
| `.conf` | Konfigurationsdatei |
| `.log`  | Logdatei            |
| `.json` | JSON-Datei          |
| `.yaml` | YAML-Datei          |
| `.csv`  | CSV-Datei           |

Wichtig:

Die Endung allein garantiert nicht den echten Inhalt.

Mit `file` kann man den Dateityp prüfen:

```bash
file script.sh
file image.png
file README.md
```

---

## Der Befehl `file`

Der Befehl `file` erkennt den Typ einer Datei anhand des Inhalts.

Beispiel:

```bash
file README.md
```

Mögliche Ausgabe:

```text
README.md: ASCII text
```

Beispiel:

```bash
file /bin/ls
```

Mögliche Ausgabe:

```text
/bin/ls: ELF 64-bit executable
```

Das ist nützlich, wenn eine Datei keine Endung hat oder die Endung nicht eindeutig ist.

---

## Programme im Pfad finden

Mit `which` findet man heraus, wo ein Befehl liegt.

Beispiel:

```bash
which python3
which bash
which git
```

Mögliche Ausgabe:

```text
/usr/bin/python3
/usr/bin/bash
/usr/bin/git
```

Das zeigt, welche ausführbare Datei gestartet wird, wenn man den Befehl eingibt.

---

## Die PATH-Variable

Die Variable `PATH` enthält Verzeichnisse, in denen die Shell nach Programmen sucht.

Anzeigen:

```bash
echo $PATH
```

Beispielausgabe:

```text
/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin
```

Die Verzeichnisse sind durch `:` getrennt.

Wenn man einen Befehl eingibt, sucht die Shell in diesen Verzeichnissen nach einem passenden Programm.

Wenn ein Programm nicht im `PATH` liegt, muss man es mit Pfad starten.

Beispiel:

```bash
./script.sh
```

Das bedeutet: Starte `script.sh` aus dem aktuellen Verzeichnis.

---

## Aktuelles Verzeichnis und `./`

Wenn eine ausführbare Datei im aktuellen Ordner liegt, startet man sie oft mit:

```bash
./script.sh
```

Das `./` bedeutet:

- `.` = aktuelles Verzeichnis
- `/` = Pfadtrennung
- `script.sh` = Datei

Linux startet Programme im aktuellen Verzeichnis nicht automatisch nur durch den Dateinamen, wenn der aktuelle Ordner nicht im `PATH` steht.

Das ist ein Sicherheitsmechanismus.

---

## Symbolische Links

Ein symbolischer Link ist eine Art Verweis auf eine andere Datei oder einen anderen Ordner.

Erstellen:

```bash
ln -s ziel linkname
```

Beispiel:

```bash
ln -s /var/log/syslog ~/syslog-link
```

Dann verweist `~/syslog-link` auf `/var/log/syslog`.

Symbolische Links erkennt man bei `ls -l` an einem Pfeil:

```text
syslog-link -> /var/log/syslog
```

Symbolische Links sind nützlich, können aber auch verwirren, wenn man nicht erkennt, dass eine Datei nur ein Verweis ist.

---

## Pfade in Skripten

In Skripten sind Pfade besonders wichtig.

Problem:

Ein Skript funktioniert vielleicht nur, wenn man es aus einem bestimmten Ordner startet.

Beispiel:

```bash
cat data/input.txt
```

Dieser relative Pfad funktioniert nur, wenn der aktuelle Ordner stimmt.

Sicherer kann ein absoluter Pfad sein:

```bash
cat /home/bilgin/project/data/input.txt
```

Oder das Skript bestimmt seinen eigenen Ordner.

Für einfache Skripte reicht oft eine klare Dokumentation:

```text
Dieses Skript muss aus dem Projektordner gestartet werden.
```

---

## Pfade mit `sudo`

Bei `sudo` muss man besonders auf Pfade achten.

Beispiel:

```bash
sudo nano /etc/hosts
```

Das öffnet eine Systemdatei mit erhöhten Rechten.

Wenn man versehentlich die falsche Datei bearbeitet, kann das Systemverhalten beeinflusst werden.

Vor Änderungen prüfen:

```bash
ls -l /etc/hosts
sudo cp /etc/hosts /etc/hosts.backup
```

Dann erst bearbeiten.

Bei Systemdateien ist ein Backup vor Änderungen eine gute Gewohnheit.

---

## Dateien und Ordner suchen

Für Pfade ist Suchen sehr wichtig.

Wichtige Befehle:

```bash
find /etc -name "sshd_config"
find ~ -name "*.md"
locate sshd_config
```

`find` sucht direkt im Dateisystem.

Beispiel:

```bash
find ~/github -name "README.md"
```

Das sucht alle README-Dateien unter `~/github`.

`locate` kann schneller sein, nutzt aber eine Datenbank, die vorher aktualisiert werden muss.

---

## Typische Admin-Orte

Für FISI sind bestimmte Pfade besonders wichtig.

| Aufgabe                | typischer Ort           |
| ---------------------- | ----------------------- |
| Benutzerdateien        | `/home`                 |
| Systemkonfiguration    | `/etc`                  |
| SSH-Konfiguration      | `/etc/ssh`              |
| Logs                   | `/var/log`              |
| temporäre Tests        | `/tmp`                  |
| installierte Programme | `/usr/bin`, `/usr/sbin` |
| manuelle Software      | `/opt`                  |
| Mountpoints            | `/mnt`, `/media`        |
| Systeminformationen    | `/proc`, `/sys`         |
| Gerätedateien          | `/dev`                  |

Diese Orte helfen bei Fehlersuche und Dokumentation.

---

## Typische Fehler mit Pfaden

| Fehler                                | Problem                                   |
| ------------------------------------- | ----------------------------------------- |
| relativen Pfad falsch verstehen       | Datei wird nicht gefunden                 |
| im falschen Ordner arbeiten           | Befehle wirken an falscher Stelle         |
| Groß- und Kleinschreibung verwechseln | Datei oder Ordner wird nicht gefunden     |
| Leerzeichen nicht schützen            | Befehl interpretiert Namen falsch         |
| `/` und `/root` verwechseln           | falsches Verständnis von Root             |
| `/tmp` für wichtige Daten nutzen      | Daten können verschwinden                 |
| Mountpoint nicht prüfen               | Daten liegen auf anderem Dateisystem      |
| versteckte Dateien übersehen          | wichtige Konfiguration wird nicht gesehen |
| `sudo` mit falschem Pfad nutzen       | Systemdateien können beschädigt werden    |
| Symlink nicht erkennen                | man bearbeitet indirekt eine andere Datei |

---

## Praktisches Vorgehen bei Pfadproblemen

Wenn eine Datei nicht gefunden wird, kann man systematisch prüfen.

1. Aktuellen Ordner anzeigen:

```bash
pwd
```

2. Inhalt anzeigen:

```bash
ls
ls -la
```

3. Absoluten Pfad nutzen:

```bash
cat /voller/pfad/zur/datei
```

4. Datei suchen:

```bash
find ~ -name "dateiname"
```

5. Groß- und Kleinschreibung prüfen.

6. Bei Leerzeichen Anführungszeichen nutzen:

```bash
cat "mein dokument.txt"
```

Dieses Vorgehen ist besser als blind Befehle zu wiederholen.

---

## Praxisbeispiele

### Beispiel 1: Konfigurationsdatei prüfen

Ein SSH-Dienst funktioniert nicht wie erwartet. Zuerst wird geprüft, ob die Konfigurationsdatei vorhanden ist:

```bash
ls -l /etc/ssh/sshd_config
```

Danach kann man sie anzeigen:

```bash
sudo less /etc/ssh/sshd_config
```

Vor Änderungen wird ein Backup erstellt:

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
```

### Beispiel 2: Logdatei finden

Ein Dienst startet nicht. Man prüft zuerst Logs:

```bash
ls /var/log
journalctl -u dienstname
```

Wenn man eine bestimmte Logdatei sucht:

```bash
find /var/log -name "*.log"
```

### Beispiel 3: USB-Stick prüfen

Ein USB-Stick wurde eingesteckt. Man prüft Blockgeräte und Mountpoints:

```bash
lsblk
df -h
findmnt
```

Danach sieht man, ob und wo der USB-Stick eingehängt wurde.

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist das Verständnis von Dateisystem und Pfaden sehr wichtig.

In der Praxis bedeutet das:

- Konfigurationsdateien finden
- Logdateien auswerten
- Benutzerverzeichnisse prüfen
- Speicherplatz analysieren
- Mountpoints verstehen
- Pfade in Skripten korrekt nutzen
- versteckte Dateien erkennen
- Systemdateien vorsichtig bearbeiten
- Fehler durch falsche Pfade vermeiden
- Dokumentation mit korrekten Pfaden schreiben

Ein guter FISI weiß nicht nur, welchen Befehl er ausführt, sondern auch, in welchem Pfad er arbeitet und welche Datei wirklich betroffen ist.

---

## Kurze Zusammenfassung

Linux nutzt ein hierarchisches Dateisystem mit dem Wurzelverzeichnis `/`.

Pfade können absolut oder relativ sein. Wichtige Kurzformen sind `.`, `..` und `~`.

Typische Systemorte sind `/home`, `/etc`, `/var`, `/var/log`, `/tmp`, `/usr`, `/opt`, `/dev`, `/proc`, `/mnt` und `/media`.

Für die Praxis sind Befehle wie `pwd`, `cd`, `ls`, `df -h`, `du -sh`, `lsblk`, `findmnt`, `find`, `which` und `file` wichtig.

Für FISI ist dieses Kapitel eine Grundlage, weil viele Aufgaben in Linux-Administration, Fehlersuche, Skripten, Docker und Serverbetrieb vom sicheren Umgang mit Pfaden abhängen.
