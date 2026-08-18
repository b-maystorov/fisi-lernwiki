# 3. Dateien und Verzeichnisse

In diesem Kapitel geht es um den praktischen Umgang mit Dateien und Verzeichnissen unter Linux.

Dateien und Ordner sind die Grundlage fast jeder Arbeit unter Linux. Konfigurationsdateien, Logdateien, Skripte, Benutzerdateien, Projektordner und Systemdateien werden über das Dateisystem verwaltet.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Aufgaben im Terminal stattfinden: Dateien anzeigen, kopieren, verschieben, löschen, suchen, bearbeiten, vergleichen und sicher verwalten.

---

## Kurz erklärt

Unter Linux arbeitet man sehr häufig direkt mit Dateien und Verzeichnissen.

Typische Aufgaben sind:

- Dateien anzeigen
- Ordner anzeigen
- Dateien erstellen
- Ordner erstellen
- Dateien kopieren
- Dateien verschieben
- Dateien umbenennen
- Dateien löschen
- Ordner löschen
- Inhalte anzeigen
- Dateien bearbeiten
- Dateien suchen
- Dateityp prüfen
- Speicherverbrauch prüfen
- versteckte Dateien anzeigen

Wichtig ist dabei, immer zu wissen, in welchem Verzeichnis man gerade arbeitet und welche Datei wirklich betroffen ist.

---

## Datei und Verzeichnis

Eine Datei speichert Daten.

Beispiele:

- Textdatei
- Konfigurationsdatei
- Logdatei
- Skript
- Bild
- PDF
- Programmdatei
- CSV-Datei
- Markdown-Datei

Ein Verzeichnis ist ein Ordner, der Dateien und weitere Verzeichnisse enthalten kann.

Beispiele:

```text
/home/bilgin
/etc
/var/log
~/github/private/fisi-lernwiki
```

Unter Linux werden Dateien und Verzeichnisse über Pfade angesprochen.

---

## Aktuellen Ordner prüfen

Bevor man Dateien verändert, sollte man oft prüfen, wo man gerade ist.

```bash
pwd
```

Beispielausgabe:

```text
/home/bilgin/github/private/fisi-lernwiki
```

`pwd` bedeutet **print working directory**.

Dieser Befehl ist besonders wichtig, bevor man Befehle wie `rm`, `mv`, `cp`, `chmod` oder `chown` nutzt.

---

## Dateien und Ordner anzeigen

Mit `ls` zeigt man Dateien und Ordner an.

```bash
ls
```

Mit Details:

```bash
ls -l
```

Mit versteckten Dateien:

```bash
ls -a
```

Mit Details und versteckten Dateien:

```bash
ls -la
```

Beispielausgabe:

```text
drwxr-xr-x 2 bilgin bilgin 4096 Aug 18 10:00 linux
-rw-r--r-- 1 bilgin bilgin 1200 Aug 18 10:00 README.md
```

---

## Ausgabe von `ls -l` verstehen

Eine Ausgabe von `ls -l` enthält viele Informationen.

Beispiel:

```text
-rw-r--r-- 1 bilgin bilgin 1200 Aug 18 10:00 README.md
```

Bedeutung:

| Teil           | Bedeutung           |
| -------------- | ------------------- |
| `-rw-r--r--`   | Dateityp und Rechte |
| `1`            | Anzahl Links        |
| `bilgin`       | Besitzer            |
| `bilgin`       | Gruppe              |
| `1200`         | Größe in Byte       |
| `Aug 18 10:00` | Änderungsdatum      |
| `README.md`    | Dateiname           |

Der erste Buchstabe zeigt den Typ:

| Zeichen | Bedeutung         |
| ------- | ----------------- |
| `-`     | normale Datei     |
| `d`     | Verzeichnis       |
| `l`     | symbolischer Link |

Beispiel:

```text
drwxr-xr-x
```

Das `d` am Anfang bedeutet: Es ist ein Verzeichnis.

---

## Versteckte Dateien

Unter Linux sind Dateien versteckt, wenn ihr Name mit einem Punkt beginnt.

Beispiele:

```text
.bashrc
.profile
.ssh
.git
.config
```

Anzeigen:

```bash
ls -a
ls -la
```

Versteckte Dateien sind nicht automatisch sicher oder verschlüsselt. Sie werden nur bei normalem `ls` nicht angezeigt.

Viele Benutzer- und Programmkonfigurationen liegen in versteckten Dateien oder Ordnern.

---

## Datei erstellen mit `touch`

Mit `touch` kann man eine leere Datei erstellen.

```bash
touch notes.txt
```

Mehrere Dateien erstellen:

```bash
touch file1.txt file2.txt file3.txt
```

Wenn die Datei bereits existiert, wird der Zeitstempel aktualisiert.

`touch` wird oft genutzt, um schnell eine neue Datei anzulegen.

---

## Verzeichnis erstellen mit `mkdir`

Mit `mkdir` erstellt man ein Verzeichnis.

```bash
mkdir docs
```

Mehrere Verzeichnisse erstellen:

```bash
mkdir docs scripts data
```

Verschachtelte Verzeichnisse erstellen:

```bash
mkdir -p project/docs/linux
```

Die Option `-p` sorgt dafür, dass fehlende Zwischenordner automatisch erstellt werden.

Ohne `-p` würde der Befehl fehlschlagen, wenn ein Zwischenordner noch nicht existiert.

---

## Dateien anzeigen mit `cat`

Mit `cat` kann man den Inhalt einer Datei direkt ausgeben.

```bash
cat README.md
```

`cat` ist gut für kurze Dateien.

Für lange Dateien ist `cat` oft unpraktisch, weil der ganze Inhalt sofort durchläuft.

Dann ist `less` besser.

---

## Dateien anzeigen mit `less`

Mit `less` kann man eine Datei seitenweise lesen.

```bash
less README.md
```

Wichtige Tasten in `less`:

| Taste       | Bedeutung         |
| ----------- | ----------------- |
| `Space`     | eine Seite weiter |
| `b`         | eine Seite zurück |
| `/suchwort` | im Text suchen    |
| `n`         | nächster Treffer  |
| `q`         | beenden           |

`less` ist sehr wichtig für Logdateien, Konfigurationen und längere Dokumente.

---

## Anfang und Ende einer Datei anzeigen

Mit `head` zeigt man den Anfang einer Datei.

```bash
head file.txt
```

Mit `tail` zeigt man das Ende einer Datei.

```bash
tail file.txt
```

Mehr Zeilen anzeigen:

```bash
head -n 20 file.txt
tail -n 20 file.txt
```

Das ist besonders nützlich bei Logdateien.

---

## Logdatei live verfolgen

Mit `tail -f` kann man eine Datei live verfolgen.

```bash
tail -f /var/log/syslog
```

Das bedeutet:

Neue Zeilen werden direkt angezeigt, sobald sie in die Datei geschrieben werden.

Das ist nützlich bei:

- Logs
- Dienstfehlern
- Webservern
- Anwendungen
- Docker-Logs als Datei
- Debugging

Beenden mit:

```text
Ctrl + C
```

---

## Datei kopieren mit `cp`

Mit `cp` kopiert man Dateien.

```bash
cp quelle ziel
```

Beispiel:

```bash
cp README.md README-backup.md
```

In einen Ordner kopieren:

```bash
cp README.md docs/
```

Mit anderem Namen kopieren:

```bash
cp README.md docs/linux-readme.md
```

Vor Änderungen an wichtigen Dateien ist eine Kopie oft sinnvoll.

Beispiel:

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
```

---

## Ordner kopieren mit `cp -r`

Verzeichnisse kopiert man rekursiv mit `-r`.

```bash
cp -r docs docs-backup
```

`-r` bedeutet: kopiere den Ordner inklusive Inhalt.

Ohne `-r` kann `cp` normale Verzeichnisse nicht kopieren.

Vorsicht:

Bei großen Ordnern oder falschem Ziel kann schnell viel Speicher belegt werden.

---

## Dateien verschieben mit `mv`

Mit `mv` verschiebt man Dateien.

```bash
mv file.txt docs/
```

Das verschiebt `file.txt` in den Ordner `docs`.

---

## Dateien umbenennen mit `mv`

`mv` wird auch zum Umbenennen genutzt.

```bash
mv old-name.txt new-name.txt
```

Das wirkt am Anfang komisch, aber Umbenennen ist technisch eine Art Verschieben im gleichen Verzeichnis.

Beispiel:

```bash
mv linux-notes.txt 03-dateien-und-verzeichnisse.md
```

---

## Ordner verschieben oder umbenennen

Auch Verzeichnisse können mit `mv` verschoben oder umbenannt werden.

Ordner umbenennen:

```bash
mv old-folder new-folder
```

Ordner verschieben:

```bash
mv docs archive/
```

Wichtig:

Wenn das Ziel existiert und ein Ordner ist, wird die Quelle dort hineingeschoben.

Wenn das Ziel nicht existiert, wird umbenannt.

---

## Dateien löschen mit `rm`

Mit `rm` löscht man Dateien.

```bash
rm file.txt
```

Mehrere Dateien löschen:

```bash
rm file1.txt file2.txt
```

Wichtig:

Unter Linux gibt es im Terminal normalerweise keinen Papierkorb für `rm`.

Gelöschte Dateien sind oft wirklich gelöscht.

Deshalb vorsichtig verwenden.

---

## Ordner löschen

Leeren Ordner löschen:

```bash
rmdir empty-folder
```

Ordner mit Inhalt löschen:

```bash
rm -r foldername
```

Gefährlicher Befehl:

```bash
rm -rf foldername
```

Bedeutung:

| Option | Bedeutung                 |
| ------ | ------------------------- |
| `-r`   | rekursiv, also mit Inhalt |
| `-f`   | force, keine Rückfragen   |

`rm -rf` sollte man nur nutzen, wenn man wirklich sicher ist.

Vorher prüfen:

```bash
pwd
ls -la
```

---

## Sicherer löschen

Wenn man unsicher ist, kann man zuerst anzeigen, was betroffen ist.

Beispiel:

```bash
ls foldername
```

Dann löschen:

```bash
rm -r foldername
```

Oder interaktiv löschen:

```bash
rm -i file.txt
```

Bei `-i` fragt `rm` vor dem Löschen nach.

Für Anfänger ist das bei wichtigen Dateien sicherer.

---

## Datei bearbeiten mit nano

`nano` ist ein einfacher Terminal-Editor.

Datei öffnen:

```bash
nano notes.txt
```

Speichern:

```text
Ctrl + O
```

Bestätigen mit Enter.

Beenden:

```text
Ctrl + X
```

`nano` ist gut für einfache Änderungen an Textdateien und Konfigurationen.

Bei wichtigen Systemdateien vorher Backup machen.

---

## Datei bearbeiten mit VS Code

Bei lokalen Projekten kann man Dateien auch mit VS Code bearbeiten.

Im Projektordner:

```bash
code .
```

Oder einzelne Datei:

```bash
code README.md
```

VS Code ist gut für:

- Markdown
- Python
- Bash-Skripte
- Git-Projekte
- Projektstruktur
- längere Dokumentation

Für Server ohne grafische Oberfläche nutzt man meistens Terminal-Editoren wie `nano` oder `vim`.

---

## Dateiinhalt suchen mit `grep`

Mit `grep` sucht man Text in Dateien.

```bash
grep "ERROR" server.log
```

Groß- und Kleinschreibung ignorieren:

```bash
grep -i "error" server.log
```

Zeilennummer anzeigen:

```bash
grep -n "ERROR" server.log
```

Rekursiv in Ordnern suchen:

```bash
grep -r "TODO" .
```

`grep` ist sehr wichtig für Logs, Konfigurationsdateien und Code.

---

## Dateien suchen mit `find`

Mit `find` sucht man Dateien und Ordner im Dateisystem.

Nach Name suchen:

```bash
find . -name "README.md"
```

Unter Home suchen:

```bash
find ~ -name "*.md"
```

Unter `/etc` suchen:

```bash
sudo find /etc -name "sshd_config"
```

Nach Ordner suchen:

```bash
find . -type d -name "linux"
```

Nach Dateien suchen:

```bash
find . -type f -name "*.md"
```

`find` ist sehr mächtig und im Admin-Alltag sehr nützlich.

---

## Wildcards

Wildcards sind Platzhalter.

| Zeichen | Bedeutung                     |
| ------- | ----------------------------- |
| `*`     | beliebig viele Zeichen        |
| `?`     | genau ein beliebiges Zeichen  |
| `[abc]` | eines der Zeichen a, b oder c |

Beispiele:

```bash
ls *.md
ls file?.txt
rm *.tmp
```

Wichtig:

Vor gefährlichen Befehlen mit Wildcards sollte man zuerst mit `ls` prüfen.

Beispiel:

```bash
ls *.tmp
rm *.tmp
```

Nicht direkt blind löschen.

---

## Dateien zählen mit `wc`

Mit `wc` kann man Zeilen, Wörter und Zeichen zählen.

```bash
wc file.txt
```

Nur Zeilen zählen:

```bash
wc -l file.txt
```

Beispiel mit Logs:

```bash
grep "ERROR" server.log | wc -l
```

Das zählt, wie viele Zeilen mit `ERROR` in der Datei vorkommen.

---

## Pipes

Eine Pipe leitet die Ausgabe eines Befehls an den nächsten Befehl weiter.

Symbol:

```text
|
```

Beispiel:

```bash
cat server.log | grep "ERROR"
```

Besser direkt:

```bash
grep "ERROR" server.log
```

Praktisch bei Kombinationen:

```bash
grep "ERROR" server.log | wc -l
```

Pipes sind eine starke Linux-Idee: kleine Werkzeuge werden kombiniert.

---

## Umleitung in Dateien

Mit `>` und `>>` kann man Ausgaben in Dateien schreiben.

Ausgabe überschreiben:

```bash
echo "Hallo" > test.txt
```

Ausgabe anhängen:

```bash
echo "Neue Zeile" >> test.txt
```

Wichtig:

`>` überschreibt die Datei.

`>>` hängt an die Datei an.

Beispiel:

```bash
date >> system-report.txt
hostname >> system-report.txt
uptime >> system-report.txt
```

---

## Dateien vergleichen mit `diff`

Mit `diff` vergleicht man zwei Dateien.

```bash
diff old.txt new.txt
```

Das zeigt Unterschiede zwischen beiden Dateien.

Nützlich bei:

- Konfigurationsdateien
- Skripten
- Dokumentation
- Backups
- Änderungen vor und nach Bearbeitung

Beispiel:

```bash
diff sshd_config.backup sshd_config
```

So sieht man, was geändert wurde.

---

## Dateityp prüfen mit `file`

Mit `file` prüft man den Dateityp.

```bash
file README.md
file script.sh
file /bin/ls
```

Beispielausgabe:

```text
README.md: Unicode text, UTF-8 text
/bin/ls: ELF 64-bit executable
```

Das ist nützlich, wenn eine Datei keine Endung hat oder die Endung nicht eindeutig ist.

---

## Dateiinformationen mit `stat`

Mit `stat` sieht man genaue Informationen zu einer Datei.

```bash
stat README.md
```

Typische Informationen:

- Größe
- Rechte
- Besitzer
- Gruppe
- Zugriffszeit
- Änderungszeit
- Inode-Nummer

`stat` ist detaillierter als `ls -l`.

---

## Leere und nicht leere Dateien

Eine leere Datei hat Größe 0 Byte.

Erstellen:

```bash
touch empty.txt
```

Prüfen:

```bash
ls -l empty.txt
stat empty.txt
```

Eine Datei kann existieren, auch wenn sie keinen Inhalt hat.

Das ist wichtig bei:

- Platzhalterdateien
- Lockfiles
- Testdateien
- Konfigurationen, die später gefüllt werden

---

## Dateien ausführbar machen

Eine Datei ist nicht automatisch ausführbar.

Bei Skripten braucht man Ausführungsrechte.

Beispiel:

```bash
chmod +x script.sh
```

Danach starten:

```bash
./script.sh
```

Wichtig:

Eine `.sh`-Endung allein reicht nicht.

Entscheidend ist das Ausführungsrecht.

Mehr zu Rechten kommt im Kapitel Benutzer, Gruppen und Rechte.

---

## Shebang bei Skripten

Ein Shell-Skript beginnt oft mit einem Shebang.

Beispiel:

```bash
#!/bin/bash

echo "Hallo"
```

Der Shebang sagt dem System, mit welchem Interpreter das Skript ausgeführt werden soll.

Beispiele:

```bash
#!/bin/bash
#!/usr/bin/env python3
```

Danach kann das Skript mit Ausführungsrechten direkt gestartet werden.

---

## Ordnerstruktur für Projekte

Eine klare Ordnerstruktur macht Projekte verständlicher.

Beispiel:

```text
project/
├── README.md
├── docs/
├── scripts/
├── data/
├── configs/
└── tests/
```

Mögliche Bedeutung:

| Ordner     | Zweck                 |
| ---------- | --------------------- |
| `docs/`    | Dokumentation         |
| `scripts/` | Skripte               |
| `data/`    | Beispieldaten         |
| `configs/` | Konfigurationsdateien |
| `tests/`   | Tests                 |

Eine gute Struktur hilft besonders bei GitHub-Projekten und bei späterer Wartung.

---

## Namen für Dateien und Ordner

Gute Dateinamen sind klar, kurz und ohne unnötige Sonderzeichen.

Gut:

```text
linux-grundlagen.md
backup-script.sh
server-report.txt
inventory_data.csv
```

Ungünstig:

```text
mein Dokument final wirklich neu!!.txt
test 123 neu alt.txt
Änderung für Prüfung.docx
```

Für IT-Projekte sind einfache Namen besser:

- Kleinbuchstaben
- Bindestrich
- Unterstrich
- keine Leerzeichen
- keine unnötigen Sonderzeichen

Das reduziert Probleme in Terminal, Skripten, Git und Docker.

---

## Dateien archivieren

Mehrere Dateien oder Ordner können mit `tar` archiviert werden.

Archiv erstellen:

```bash
tar -cf backup.tar docs/
```

Archiv anzeigen:

```bash
tar -tf backup.tar
```

Archiv entpacken:

```bash
tar -xf backup.tar
```

Komprimiertes Archiv mit gzip:

```bash
tar -czf backup.tar.gz docs/
```

Entpacken:

```bash
tar -xzf backup.tar.gz
```

Archive sind nützlich für Backups, Übertragungen und Projektstände.

---

## Sicherungskopien erstellen

Vor Änderungen an wichtigen Dateien sollte man eine Sicherungskopie erstellen.

Beispiel:

```bash
cp config.conf config.conf.backup
```

Bei Systemdateien:

```bash
sudo cp /etc/hosts /etc/hosts.backup
```

Danach kann man Änderungen vergleichen:

```bash
diff /etc/hosts.backup /etc/hosts
```

Das ist eine einfache, aber sehr wichtige Admin-Gewohnheit.

---

## Typische Fehler

| Fehler                                     | Problem                                               |
| ------------------------------------------ | ----------------------------------------------------- |
| im falschen Ordner arbeiten                | Dateien werden am falschen Ort erstellt oder gelöscht |
| `rm` unvorsichtig nutzen                   | Datenverlust möglich                                  |
| `cp` ohne `-r` bei Ordnern nutzen          | Ordner wird nicht kopiert                             |
| `mv` falsch verstehen                      | Datei wird verschoben statt nur umbenannt             |
| versteckte Dateien übersehen               | wichtige Konfiguration fehlt                          |
| `>` statt `>>` nutzen                      | Datei wird überschrieben                              |
| Wildcards blind verwenden                  | zu viele Dateien werden betroffen                     |
| Leerzeichen in Namen nicht schützen        | Befehl interpretiert Namen falsch                     |
| keine Backups vor Konfigurationsänderungen | Rückweg fehlt                                         |
| Dateiendung mit Dateityp verwechseln       | falsche Annahmen über Dateiinhalt                     |

---

## Praktisches Vorgehen bei Datei-Aufgaben

Vor Änderungen:

```bash
pwd
ls -la
```

Bei wichtigen Dateien:

```bash
cp datei datei.backup
```

Bei Suche:

```bash
find . -name "dateiname"
grep -r "suchwort" .
```

Bei Löschen:

```bash
ls ziel
rm ziel
```

Bei Ordnern:

```bash
rm -r ordner
```

Bei Unsicherheit:

- erst anzeigen
- dann ändern
- keine gefährlichen Befehle blind kopieren
- Pfad genau prüfen
- Backup erstellen

---

## Praxisbeispiele

### Beispiel 1: README kopieren

Ein Projekt hat eine README-Datei. Vor einer größeren Änderung wird eine Sicherung erstellt.

```bash
cp README.md README.md.backup
nano README.md
diff README.md.backup README.md
```

So kann man später sehen, was geändert wurde.

### Beispiel 2: Logdatei durchsuchen

Eine Anwendung schreibt Fehler in eine Logdatei.

```bash
grep -i "error" app.log
grep -i "error" app.log | wc -l
```

Damit findet man Fehler und zählt sie.

### Beispiel 3: Projektordner erstellen

Für ein neues Skriptprojekt wird eine einfache Struktur angelegt.

```bash
mkdir -p linux-tool/scripts linux-tool/docs linux-tool/data
touch linux-tool/README.md
touch linux-tool/scripts/check-system.sh
```

Danach kann das Projekt sauber dokumentiert und versioniert werden.

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist der sichere Umgang mit Dateien und Verzeichnissen eine tägliche Grundlage.

In der Praxis bedeutet das:

- Konfigurationsdateien sichern und bearbeiten
- Logs anzeigen und durchsuchen
- Projektordner strukturieren
- Skripte erstellen
- Dateien auf Servern prüfen
- Backups vorbereiten
- Dateien vergleichen
- Speicherorte verstehen
- Fehler durch falsche Pfade vermeiden
- sicher mit Löschbefehlen umgehen

Ein guter FISI arbeitet im Terminal nicht blind, sondern prüft Pfad, Ziel, Inhalt und Auswirkungen eines Befehls.

---

## Kurze Zusammenfassung

Dateien und Verzeichnisse werden unter Linux häufig direkt im Terminal verwaltet.

Wichtige Befehle sind `ls`, `pwd`, `touch`, `mkdir`, `cat`, `less`, `head`, `tail`, `cp`, `mv`, `rm`, `nano`, `grep`, `find`, `wc`, `diff`, `file`, `stat` und `tar`.

Besonders wichtig sind vorsichtiger Umgang mit `rm`, sinnvolle Dateinamen, Backups vor Änderungen, korrektes Arbeiten mit Pfaden und das Verständnis von versteckten Dateien.

Für FISI ist dieses Kapitel wichtig, weil fast jede Linux-Administration mit Dateien, Ordnern, Konfigurationen, Logs oder Skripten zu tun hat.
