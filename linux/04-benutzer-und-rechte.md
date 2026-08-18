# 4. Benutzer, Gruppen und Rechte

In diesem Kapitel geht es um Benutzer, Gruppen und Dateirechte unter Linux.

Linux ist ein Mehrbenutzersystem. Das bedeutet, dass mehrere Benutzer auf einem System existieren können und jeder Benutzer unterschiedliche Rechte haben kann. Rechte steuern, wer Dateien lesen, verändern oder ausführen darf.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr wichtig, weil falsche Rechte eine häufige Ursache für Sicherheitsprobleme, Programmfehler, Zugriffsprobleme und Serverstörungen sind.

---

## Kurz erklärt

Linux nutzt Benutzer, Gruppen und Rechte, um Zugriff auf Dateien, Verzeichnisse und Systemfunktionen zu kontrollieren.

Wichtige Themen sind:

- Benutzerkonten
- Gruppen
- Root-Benutzer
- sudo
- Besitzer von Dateien
- Gruppenbesitz
- Leserechte
- Schreibrechte
- Ausführungsrechte
- Rechte für Dateien
- Rechte für Verzeichnisse
- chmod
- chown
- chgrp
- umask
- Sonderrechte
- typische Rechteprobleme

Rechte sind ein zentrales Sicherheitskonzept unter Linux.

---

## Warum Rechte wichtig sind

Rechte schützen das System und die Daten.

Ohne Rechteverwaltung könnte jeder Benutzer alles lesen, ändern oder löschen.

Mögliche Probleme ohne saubere Rechte:

- Benutzer können fremde Dateien lesen
- wichtige Systemdateien werden verändert
- Dienste können ihre Dateien nicht öffnen
- Skripte sind nicht ausführbar
- SSH-Schlüssel werden unsicher
- Programme laufen mit zu vielen Rechten
- Logs können nicht geschrieben werden
- sensible Daten werden öffentlich lesbar
- normale Benutzer können Admin-Aufgaben ausführen

Gute Rechteverwaltung sorgt dafür, dass Benutzer und Programme nur das dürfen, was sie wirklich brauchen.

---

## Benutzer unter Linux

Ein Benutzer ist ein Konto auf dem System.

Jeder Benutzer hat normalerweise:

- Benutzername
- Benutzer-ID
- Home-Verzeichnis
- Standard-Shell
- Gruppenmitgliedschaften
- Passwort oder andere Anmeldemethode

Beispiel:

```bash
whoami
```

Ausgabe:

```text
bilgin
```

Der Befehl zeigt den aktuell angemeldeten Benutzer.

---

## Benutzerinformationen anzeigen

Mit `id` sieht man Benutzer-ID und Gruppen.

```bash
id
```

Beispielausgabe:

```text
uid=1000(bilgin) gid=1000(bilgin) groups=1000(bilgin),27(sudo),1001(docker)
```

Bedeutung:

| Teil     | Bedeutung               |
| -------- | ----------------------- |
| `uid`    | User ID                 |
| `gid`    | primäre Gruppen-ID      |
| `groups` | Gruppenmitgliedschaften |

Die User ID ist intern wichtig. Linux arbeitet intern stark mit IDs, auch wenn Menschen meistens Benutzernamen sehen.

---

## Gruppen unter Linux

Gruppen fassen Benutzer zusammen.

Dadurch kann man Rechte einfacher verwalten.

Beispiel:

Mehrere Benutzer sollen Zugriff auf einen Projektordner haben. Dann kann man eine Gruppe erstellen und dem Ordner diese Gruppe zuweisen.

Vorteile von Gruppen:

- Rechte müssen nicht einzeln pro Benutzer gesetzt werden
- Teamzugriffe werden einfacher
- Verwaltung wird übersichtlicher
- weniger Fehler bei Berechtigungen
- Benutzer können Rollen bekommen

Typische Gruppen:

| Gruppe     | Bedeutung                                               |
| ---------- | ------------------------------------------------------- |
| `sudo`     | Benutzer darf mit sudo administrative Befehle ausführen |
| `docker`   | Benutzer darf Docker nutzen                             |
| `www-data` | häufig für Webserver                                    |
| `adm`      | Zugriff auf bestimmte Logs                              |
| `users`    | normale Benutzergruppe                                  |

Gruppen sind besonders wichtig bei Servern, Projektordnern, Webservern und gemeinsam genutzten Dateien.

---

## Gruppen anzeigen

Gruppen des aktuellen Benutzers anzeigen:

```bash
groups
```

Oder für einen bestimmten Benutzer:

```bash
groups benutzername
```

Detaillierter:

```bash
id benutzername
```

Beispiel:

```bash
id bilgin
```

So sieht man, zu welchen Gruppen ein Benutzer gehört.

---

## Root-Benutzer

`root` ist der administrative Benutzer unter Linux.

Root darf fast alles:

- Systemdateien ändern
- Benutzer erstellen
- Benutzer löschen
- Pakete installieren
- Dienste verwalten
- Rechte ändern
- Netzwerkeinstellungen ändern
- Dateien anderer Benutzer löschen
- Prozesse beenden

Root ist sehr mächtig.

Deshalb sollte man nicht dauerhaft als Root arbeiten.

Ein falscher Befehl als Root kann das System beschädigen oder wichtige Daten löschen.

---

## sudo

`sudo` erlaubt einem berechtigten Benutzer, einzelne Befehle mit administrativen Rechten auszuführen.

Beispiel:

```bash
sudo apt update
```

Das bedeutet:

Der Befehl `apt update` wird mit erhöhten Rechten ausgeführt.

Typische Aufgaben mit `sudo`:

```bash
sudo apt install nginx
sudo systemctl restart ssh
sudo nano /etc/hosts
sudo chown user:group file.txt
```

Wichtig:

`sudo` sollte bewusst genutzt werden.

Nicht jeder Befehl braucht `sudo`. Wenn man immer sofort `sudo` benutzt, versteht man Rechteprobleme schlechter und erhöht das Risiko für Fehler.

---

## su

Mit `su` kann man den Benutzer wechseln.

Beispiel:

```bash
su -
```

Das versucht, zum Root-Benutzer zu wechseln.

Zu einem bestimmten Benutzer wechseln:

```bash
su - benutzername
```

In vielen Ubuntu-Systemen wird statt direktem Root-Login eher `sudo` genutzt.

Für normale Administration ist `sudo` meistens sauberer, weil einzelne Befehle mit erhöhten Rechten ausgeführt werden, statt dauerhaft als Root zu arbeiten.

---

## Wichtige Dateien für Benutzer und Gruppen

Linux speichert Benutzer- und Gruppeninformationen in wichtigen Systemdateien.

| Datei             | Bedeutung                             |
| ----------------- | ------------------------------------- |
| `/etc/passwd`     | Benutzerkonten und Grundinformationen |
| `/etc/shadow`     | verschlüsselte Passwortinformationen  |
| `/etc/group`      | Gruppeninformationen                  |
| `/etc/sudoers`    | sudo-Regeln                           |
| `/etc/sudoers.d/` | zusätzliche sudo-Regeln               |

Diese Dateien sind sehr wichtig.

Man sollte sie nicht unvorsichtig bearbeiten.

Bei sudo-Regeln nutzt man besser:

```bash
sudo visudo
```

`visudo` prüft die Datei auf Syntaxfehler, bevor Änderungen übernommen werden.

---

## `/etc/passwd`

Die Datei `/etc/passwd` enthält Benutzerinformationen.

Anzeigen:

```bash
cat /etc/passwd
```

Beispielzeile:

```text
bilgin:x:1000:1000:Bilgin:/home/bilgin:/bin/bash
```

Bedeutung:

| Feld           | Bedeutung                       |
| -------------- | ------------------------------- |
| `bilgin`       | Benutzername                    |
| `x`            | Passwort liegt in `/etc/shadow` |
| `1000`         | User ID                         |
| `1000`         | primäre Gruppen-ID              |
| `Bilgin`       | Kommentar oder Name             |
| `/home/bilgin` | Home-Verzeichnis                |
| `/bin/bash`    | Standard-Shell                  |

Die Datei heißt zwar `passwd`, enthält aber moderne Passwort-Hashes normalerweise nicht direkt.

---

## `/etc/shadow`

Die Datei `/etc/shadow` enthält Passwortinformationen.

Sie ist nur für Root lesbar.

Prüfen:

```bash
sudo less /etc/shadow
```

Diese Datei ist besonders sensibel.

Normale Benutzer dürfen sie nicht lesen, weil dort Passwort-Hashes und Passwortregeln gespeichert sind.

Wichtig:

Man sollte keine Inhalte aus `/etc/shadow` veröffentlichen, kopieren oder in GitHub hochladen.

---

## `/etc/group`

Die Datei `/etc/group` enthält Gruppeninformationen.

Anzeigen:

```bash
cat /etc/group
```

Beispielzeile:

```text
docker:x:1001:bilgin
```

Bedeutung:

| Feld     | Bedeutung                                        |
| -------- | ------------------------------------------------ |
| `docker` | Gruppenname                                      |
| `x`      | Gruppenpasswort wird normalerweise nicht genutzt |
| `1001`   | Gruppen-ID                                       |
| `bilgin` | Mitglieder der Gruppe                            |

Diese Datei hilft zu verstehen, welche Gruppen existieren und welche Benutzer Mitglied sind.

---

## Benutzer erstellen

Auf Ubuntu und Debian wird häufig `adduser` genutzt.

```bash
sudo adduser username
```

Dieser Befehl erstellt:

- Benutzerkonto
- Home-Verzeichnis
- Passwortabfrage
- Grundkonfiguration

Beispiel:

```bash
sudo adduser testuser
```

Es gibt auch `useradd`, das technischer und weniger komfortabel ist.

Für einfache Administration ist `adduser` oft angenehmer.

---

## Benutzer löschen

Benutzer löschen:

```bash
sudo deluser username
```

Benutzer inklusive Home-Verzeichnis löschen:

```bash
sudo deluser --remove-home username
```

Wichtig:

Vor dem Löschen sollte geprüft werden, ob der Benutzer noch Dateien, Prozesse oder Dienste besitzt.

Prüfen:

```bash
id username
ps -u username
ls -la /home/username
```

Ein Benutzerkonto einfach zu löschen, ohne Daten und Zuständigkeiten zu prüfen, kann Probleme verursachen.

---

## Passwort ändern

Eigenes Passwort ändern:

```bash
passwd
```

Passwort eines anderen Benutzers ändern:

```bash
sudo passwd username
```

Beispiel:

```bash
sudo passwd testuser
```

Starke Passwörter und sichere Anmeldemethoden sind wichtig, besonders bei Servern mit SSH-Zugriff.

---

## Gruppen erstellen und löschen

Gruppe erstellen:

```bash
sudo addgroup projektteam
```

Gruppe löschen:

```bash
sudo delgroup projektteam
```

Gruppe anzeigen:

```bash
getent group projektteam
```

`getent` liest Informationen aus den systemweiten Datenbanken, zum Beispiel Benutzer und Gruppen.

---

## Benutzer zu Gruppe hinzufügen

Benutzer zu einer Gruppe hinzufügen:

```bash
sudo usermod -aG gruppenname benutzername
```

Beispiel:

```bash
sudo usermod -aG docker bilgin
```

Wichtig ist die Option `-aG`.

| Option | Bedeutung                              |
| ------ | -------------------------------------- |
| `-G`   | setzt zusätzliche Gruppen              |
| `-a`   | append, also hinzufügen statt ersetzen |

Ohne `-a` kann man versehentlich bestehende Gruppenmitgliedschaften entfernen.

Nach einer Gruppenänderung muss sich der Benutzer oft neu anmelden, damit die Änderung aktiv wird.

---

## Dateien und Besitzer

Jede Datei hat einen Besitzer und eine Gruppe.

Anzeigen:

```bash
ls -l
```

Beispiel:

```text
-rw-r--r-- 1 bilgin bilgin 1200 Aug 18 10:00 README.md
```

Hier ist:

| Teil             | Bedeutung |
| ---------------- | --------- |
| erster `bilgin`  | Besitzer  |
| zweiter `bilgin` | Gruppe    |
| `-rw-r--r--`     | Rechte    |

Der Besitzer ist der Benutzer, dem die Datei gehört.

Die Gruppe ist die Gruppe, für die Gruppenrechte gelten.

---

## Rechte-Grundlagen

Linux nutzt drei Grundrechte.

| Recht     | Zeichen | Bedeutung bei Dateien                  |
| --------- | ------- | -------------------------------------- |
| Lesen     | `r`     | Dateiinhalt anzeigen                   |
| Schreiben | `w`     | Datei ändern                           |
| Ausführen | `x`     | Datei als Programm oder Skript starten |

Diese Rechte gelten für drei Bereiche:

| Bereich | Bedeutung             |
| ------- | --------------------- |
| User    | Besitzer der Datei    |
| Group   | zugeordnete Gruppe    |
| Others  | alle anderen Benutzer |

Deshalb sieht man Rechte oft als neun Zeichen.

Beispiel:

```text
rw-r--r--
```

Aufgeteilt:

```text
rw- r-- r--
```

Bedeutung:

| Bereich  | Rechte              |
| -------- | ------------------- |
| Besitzer | lesen und schreiben |
| Gruppe   | lesen               |
| Andere   | lesen               |

---

## Dateityp in der Rechteanzeige

Bei `ls -l` steht ganz vorne ein Zeichen für den Dateityp.

Beispiel:

```text
-rw-r--r--
```

Das erste Zeichen ist hier `-`.

Wichtige Zeichen:

| Zeichen | Bedeutung         |
| ------- | ----------------- |
| `-`     | normale Datei     |
| `d`     | Verzeichnis       |
| `l`     | symbolischer Link |
| `c`     | Character Device  |
| `b`     | Block Device      |
| `s`     | Socket            |
| `p`     | Pipe              |

Beispiel für ein Verzeichnis:

```text
drwxr-xr-x
```

Das `d` zeigt: Es ist ein Verzeichnis.

---

## Rechte bei Verzeichnissen

Rechte bei Verzeichnissen haben eine etwas andere Bedeutung als bei Dateien.

| Recht | Bedeutung bei Verzeichnissen                              |
| ----- | --------------------------------------------------------- |
| `r`   | Inhalt des Verzeichnisses auflisten                       |
| `w`   | Dateien im Verzeichnis erstellen, löschen oder umbenennen |
| `x`   | Verzeichnis betreten und Pfade darin nutzen               |

Das Ausführungsrecht `x` ist bei Verzeichnissen besonders wichtig.

Ohne `x` kann man ein Verzeichnis nicht sinnvoll betreten, auch wenn `r` gesetzt ist.

Beispiel:

```bash
cd ordner
```

funktioniert nur, wenn man für den Ordner Ausführungsrecht hat.

---

## Rechte anzeigen

Rechte anzeigen:

```bash
ls -l
```

Für versteckte Dateien:

```bash
ls -la
```

Für einen bestimmten Pfad:

```bash
ls -ld /etc
```

Wichtig:

`ls -l /etc` zeigt den Inhalt von `/etc`.

`ls -ld /etc` zeigt die Rechte des Ordners `/etc` selbst.

Das ist ein wichtiger Unterschied.

---

## chmod

Mit `chmod` ändert man Rechte.

Es gibt zwei häufige Schreibweisen:

- symbolisch
- numerisch

Symbolisch:

```bash
chmod u+x script.sh
```

Numerisch:

```bash
chmod 755 script.sh
```

`chmod` bedeutet **change mode**.

Damit wird festgelegt, wer lesen, schreiben oder ausführen darf.

---

## Symbolische Rechte mit chmod

Symbolische Schreibweise nutzt Buchstaben.

Bereiche:

| Zeichen | Bedeutung      |
| ------- | -------------- |
| `u`     | user, Besitzer |
| `g`     | group, Gruppe  |
| `o`     | others, andere |
| `a`     | all, alle      |

Aktionen:

| Zeichen | Bedeutung           |
| ------- | ------------------- |
| `+`     | Recht hinzufügen    |
| `-`     | Recht entfernen     |
| `=`     | Rechte exakt setzen |

Rechte:

| Zeichen | Bedeutung |
| ------- | --------- |
| `r`     | lesen     |
| `w`     | schreiben |
| `x`     | ausführen |

Beispiele:

```bash
chmod u+x script.sh
chmod g+w projekt.txt
chmod o-r geheim.txt
chmod a+r README.md
```

---

## Numerische Rechte mit chmod

Bei der numerischen Schreibweise haben Rechte Zahlenwerte.

| Recht | Wert |
| ----- | ---: |
| `r`   |    4 |
| `w`   |    2 |
| `x`   |    1 |

Die Werte werden addiert.

| Zahl | Rechte                        |
| ---: | ----------------------------- |
|    0 | keine Rechte                  |
|    1 | ausführen                     |
|    2 | schreiben                     |
|    3 | schreiben + ausführen         |
|    4 | lesen                         |
|    5 | lesen + ausführen             |
|    6 | lesen + schreiben             |
|    7 | lesen + schreiben + ausführen |

Beispiele:

| Zahl  | Bedeutung                                                      |
| ----- | -------------------------------------------------------------- |
| `644` | Besitzer lesen/schreiben, Gruppe lesen, andere lesen           |
| `600` | nur Besitzer lesen/schreiben                                   |
| `755` | Besitzer alles, Gruppe lesen/ausführen, andere lesen/ausführen |
| `700` | nur Besitzer alles                                             |
| `777` | alle dürfen alles                                              |

---

## Beispiele für chmod

Normale Textdatei:

```bash
chmod 644 file.txt
```

Privater SSH-Schlüssel:

```bash
chmod 600 ~/.ssh/id_ed25519
```

Skript ausführbar machen:

```bash
chmod +x script.sh
```

Oder:

```bash
chmod 755 script.sh
```

Privater Ordner:

```bash
chmod 700 private-folder
```

Gefährlich:

```bash
chmod 777 file.txt
```

`777` bedeutet: Jeder darf lesen, schreiben und ausführen.

Das ist fast nie eine gute Lösung.

---

## chown

Mit `chown` ändert man den Besitzer einer Datei oder eines Ordners.

Beispiel:

```bash
sudo chown bilgin file.txt
```

Besitzer und Gruppe ändern:

```bash
sudo chown bilgin:bilgin file.txt
```

Für Ordner rekursiv:

```bash
sudo chown -R bilgin:bilgin projektordner
```

Vorsicht mit `-R`.

Rekursive Änderungen können sehr viele Dateien betreffen.

Vorher prüfen:

```bash
pwd
ls -la
```

---

## chgrp

Mit `chgrp` ändert man nur die Gruppe.

Beispiel:

```bash
sudo chgrp projektteam file.txt
```

Für einen Ordner:

```bash
sudo chgrp -R projektteam projektordner
```

Das ist nützlich bei gemeinsamen Projektordnern.

Beispiel:

Mehrere Benutzer sind in der Gruppe `projektteam`. Der Ordner gehört dieser Gruppe, und Gruppenmitglieder dürfen darin arbeiten.

---

## Gemeinsamer Projektordner

Beispiel für einen gemeinsamen Ordner:

```bash
sudo mkdir /srv/projekt
sudo chgrp projektteam /srv/projekt
sudo chmod 2775 /srv/projekt
```

Bedeutung:

| Befehl       | Wirkung                             |
| ------------ | ----------------------------------- |
| `mkdir`      | Ordner erstellen                    |
| `chgrp`      | Gruppe setzen                       |
| `chmod 2775` | Rechte setzen und setgid aktivieren |

Das `2` vorne aktiviert setgid auf dem Ordner.

Dadurch bekommen neue Dateien im Ordner automatisch die Gruppe des Ordners.

Das ist bei Teamordnern praktisch.

---

## umask

`umask` legt fest, welche Rechte bei neuen Dateien und Ordnern standardmäßig entfernt werden.

Anzeigen:

```bash
umask
```

Beispiel:

```text
0022
```

Typische Wirkung:

| Objekt       | Standard mit umask 022 |
| ------------ | ---------------------- |
| neue Datei   | `644`                  |
| neuer Ordner | `755`                  |

Das bedeutet:

- Dateien sind für Besitzer schreibbar
- Gruppe und andere dürfen lesen
- Ordner sind für andere betretbar und lesbar

Eine strengere umask kann zum Beispiel sein:

```bash
umask 077
```

Dann sind neue Dateien und Ordner nur für den Besitzer zugänglich.

---

## Sonderrechte

Neben `r`, `w` und `x` gibt es Sonderrechte.

Wichtige Sonderrechte:

| Sonderrecht | Bedeutung                                                          |
| ----------- | ------------------------------------------------------------------ |
| setuid      | Programm läuft mit Rechten des Besitzers                           |
| setgid      | Datei/Programm läuft mit Gruppenrechten oder Ordner vererbt Gruppe |
| sticky bit  | Benutzer dürfen in gemeinsamem Ordner nur eigene Dateien löschen   |

Diese Rechte sind fortgeschrittener, aber wichtig zu kennen.

---

## Sticky Bit

Das Sticky Bit wird häufig bei gemeinsam beschreibbaren Ordnern genutzt.

Beispiel:

```bash
ls -ld /tmp
```

Typische Ausgabe:

```text
drwxrwxrwt 10 root root 4096 Aug 18 10:00 /tmp
```

Das `t` am Ende zeigt das Sticky Bit.

Bedeutung:

In `/tmp` dürfen viele Benutzer Dateien erstellen.
Aber Benutzer dürfen normalerweise nur eigene Dateien löschen, nicht die Dateien anderer Benutzer.

Das schützt gemeinsam genutzte Ordner vor fremdem Löschen.

---

## setgid bei Ordnern

setgid auf einem Ordner sorgt dafür, dass neue Dateien die Gruppe des Ordners übernehmen.

Beispiel:

```bash
sudo chmod g+s projektordner
```

Oder numerisch:

```bash
sudo chmod 2775 projektordner
```

Das ist nützlich für Teamordner.

Wenn mehrere Benutzer in einem gemeinsamen Ordner arbeiten, bleiben neue Dateien automatisch in der richtigen Gruppe.

---

## ACLs

ACL bedeutet **Access Control List**.

ACLs erlauben feinere Rechte als klassische Linux-Rechte.

Beispiel:

```bash
getfacl file.txt
```

Recht für einen bestimmten Benutzer setzen:

```bash
setfacl -m u:username:r file.txt
```

ACLs sind nützlich, wenn klassische Besitzer-Gruppe-Andere-Rechte nicht ausreichen.

Für den Anfang sind klassische Rechte aber wichtiger.

---

## Rechte und SSH

SSH ist besonders empfindlich bei Rechten.

Private Schlüssel dürfen nicht für andere Benutzer lesbar sein.

Typische Rechte:

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
chmod 600 ~/.ssh/config
```

Wenn private SSH-Schlüssel zu offene Rechte haben, verweigert SSH oft die Nutzung.

Das ist ein Schutzmechanismus.

---

## Rechte und Webserver

Webserver nutzen oft eigene Benutzer.

Beispiele:

- `www-data`
- `nginx`
- `apache`

Ein Webserver muss Dateien lesen können, aber nicht immer schreiben dürfen.

Typische Fragen:

- Wem gehören die Webdateien?
- Welche Gruppe hat Zugriff?
- Darf der Webserver schreiben?
- Sind Upload-Ordner extra abgesichert?
- Sind Konfigurationsdateien geschützt?
- Sind geheime Dateien öffentlich erreichbar?

Zu offene Rechte bei Webservern sind ein Sicherheitsrisiko.

---

## Rechte und Docker

Auch Docker hängt mit Linux-Rechten zusammen.

Wichtige Punkte:

- Dateien in Volumes haben Besitzer und Rechte
- Containerprozesse laufen als Benutzer
- der Docker-Daemon läuft mit hohen Rechten
- Mitglieder der Gruppe `docker` haben sehr mächtige Rechte
- falsche Volume-Rechte können Anwendungen stoppen
- Container können Dateien als Root erstellen

Beispielproblem:

Ein Container schreibt Dateien als Root in einen Volume-Ordner. Danach kann der normale Benutzer diese Dateien nicht mehr bearbeiten.

Prüfen:

```bash
ls -la
id
docker exec -it containername id
```

---

## Rechteprobleme erkennen

Typische Fehlermeldungen:

```text
Permission denied
Access denied
Operation not permitted
Read-only file system
cannot open file
permission denied while trying to connect to Docker daemon
```

Diese Meldungen deuten oft auf Rechteprobleme hin.

Wichtig ist, nicht sofort blind `sudo` zu nutzen.

Besser prüfen:

```bash
whoami
id
ls -la datei
ls -ld ordner
groups
```

Dann entscheiden, ob Besitzer, Gruppe oder Rechte angepasst werden müssen.

---

## Systematisch Rechte prüfen

Bei einem Rechteproblem kann man so vorgehen:

1. Aktuellen Benutzer prüfen:

```bash
whoami
id
```

2. Datei oder Ordner prüfen:

```bash
ls -l datei
ls -ld ordner
```

3. Gruppen prüfen:

```bash
groups
```

4. Pfadbestandteile prüfen:

```bash
ls -ld /pfad
ls -ld /pfad/zum
ls -ld /pfad/zum/ordner
```

5. Rechte gezielt ändern:

```bash
chmod
chown
chgrp
```

Wichtig:

Bei Verzeichnissen müssen auch übergeordnete Ordner betretbar sein. Wenn ein Elternordner kein `x`-Recht hat, kann der Zugriff auf Dateien darunter scheitern.

---

## chmod -R vorsichtig nutzen

`chmod -R` ändert Rechte rekursiv.

Beispiel:

```bash
chmod -R 755 ordner
```

Das betrifft den Ordner und alle Inhalte.

Problem:

Dateien und Ordner brauchen oft unterschiedliche Rechte.

Beispiel:

- Ordner brauchen oft `x`, damit man sie betreten kann
- normale Dateien brauchen meistens kein `x`
- private Dateien sollten nicht für alle lesbar sein

Deshalb sollte man `chmod -R` nur verwenden, wenn man genau weiß, was betroffen ist.

---

## chown -R vorsichtig nutzen

Auch `chown -R` kann gefährlich sein.

Beispiel:

```bash
sudo chown -R bilgin:bilgin /
```

So ein Befehl wäre katastrophal, weil er Besitzer im ganzen System ändern würde.

Vor rekursiven Befehlen immer prüfen:

```bash
pwd
ls -la
```

Und den Pfad genau angeben.

Besser:

```bash
sudo chown -R bilgin:bilgin /home/bilgin/projekt
```

Nicht blind kopieren.

---

## Rechte für typische Dateien

| Datei / Ordner      | typische Rechte | Bedeutung                                         |
| ------------------- | --------------- | ------------------------------------------------- |
| normale Textdatei   | `644`           | Besitzer schreibt, andere lesen                   |
| privater Schlüssel  | `600`           | nur Besitzer liest und schreibt                   |
| privater Ordner     | `700`           | nur Besitzer hat Zugriff                          |
| Skript              | `755`           | Besitzer schreibt, alle können ausführen          |
| öffentlicher Ordner | `755`           | alle können lesen/betreten, nur Besitzer schreibt |
| `/tmp`              | `1777`          | alle schreiben, Sticky Bit schützt Löschen        |
| Projektordner Team  | `2775`          | Gruppe arbeitet gemeinsam, setgid aktiv           |

Diese Werte sind keine festen Regeln für jede Situation, aber gute Orientierung.

---

## Prinzip der minimalen Rechte

Das Prinzip der minimalen Rechte bedeutet:

> Benutzer und Programme bekommen nur die Rechte, die sie wirklich benötigen.

Beispiele:

- normale Benutzer bekommen keine Root-Rechte
- Anwendung bekommt keinen Datenbank-Adminzugang
- Webserver darf nicht alle Systemdateien lesen
- Skript bekommt nur Zugriff auf benötigte Ordner
- Teamordner ist nur für die Projektgruppe zugänglich
- private Schlüssel sind nur für den Besitzer lesbar

Dieses Prinzip reduziert Schäden, wenn ein Konto oder Programm kompromittiert wird.

---

## Typische Fehler

| Fehler                                  | Problem                                                   |
| --------------------------------------- | --------------------------------------------------------- |
| immer `sudo` benutzen                   | eigentliches Rechteproblem wird nicht verstanden          |
| `chmod 777` als schnelle Lösung         | hohes Sicherheitsrisiko                                   |
| private SSH-Schlüssel zu offen          | SSH verweigert Nutzung oder Schlüssel sind gefährdet      |
| falscher Besitzer nach Docker-Nutzung   | normaler Benutzer kann Dateien nicht bearbeiten           |
| `chmod -R` blind verwenden              | Rechte vieler Dateien werden falsch gesetzt               |
| `chown -R` mit falschem Pfad            | System kann beschädigt werden                             |
| Gruppenmitgliedschaft vergessen         | Benutzer hat keinen Zugriff trotz richtiger Gruppenrechte |
| nach Gruppenänderung nicht neu anmelden | neue Gruppe ist noch nicht aktiv                          |
| Verzeichnisrechte nicht verstehen       | Datei ist da, aber Zugriff scheitert wegen fehlendem `x`  |
| `/etc/sudoers` falsch bearbeiten        | sudo kann kaputtgehen                                     |

---

## Praktische Beispiele

### Beispiel 1: Skript ausführbar machen

Ein Shell-Skript soll gestartet werden.

```bash
ls -l backup.sh
chmod +x backup.sh
./backup.sh
```

Wenn vorher kein `x`-Recht vorhanden war, konnte das Skript nicht direkt ausgeführt werden.

### Beispiel 2: Besitzer eines Projektordners reparieren

Ein Ordner gehört versehentlich Root.

```bash
ls -ld projekt
sudo chown -R bilgin:bilgin projekt
```

Danach kann der Benutzer wieder normal im Projekt arbeiten.

### Beispiel 3: SSH-Rechte korrigieren

SSH beschwert sich über zu offene Rechte.

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
```

Danach akzeptiert SSH den privaten Schlüssel wieder.

### Beispiel 4: Gruppe für Docker prüfen

Docker kann ohne sudo nicht genutzt werden.

```bash
groups
sudo usermod -aG docker bilgin
```

Danach abmelden und neu anmelden.

Wichtig:

Mitgliedschaft in der Gruppe `docker` ist sicherheitsrelevant, weil Docker sehr mächtige Rechte auf dem System ermöglicht.

---

## Nützliche Befehle

| Befehl                         | Bedeutung                            |
| ------------------------------ | ------------------------------------ |
| `whoami`                       | aktuellen Benutzer anzeigen          |
| `id`                           | Benutzer-ID und Gruppen anzeigen     |
| `groups`                       | Gruppen anzeigen                     |
| `ls -l`                        | Rechte, Besitzer und Gruppe anzeigen |
| `ls -ld ordner`                | Rechte eines Ordners selbst anzeigen |
| `chmod`                        | Rechte ändern                        |
| `chown`                        | Besitzer ändern                      |
| `chgrp`                        | Gruppe ändern                        |
| `passwd`                       | Passwort ändern                      |
| `sudo passwd user`             | Passwort eines Benutzers ändern      |
| `sudo adduser user`            | Benutzer erstellen                   |
| `sudo deluser user`            | Benutzer löschen                     |
| `sudo addgroup gruppe`         | Gruppe erstellen                     |
| `sudo usermod -aG gruppe user` | Benutzer zu Gruppe hinzufügen        |
| `getent passwd user`           | Benutzerinformationen anzeigen       |
| `getent group gruppe`          | Gruppeninformationen anzeigen        |
| `umask`                        | Standardrechte anzeigen              |
| `getfacl`                      | ACL-Rechte anzeigen                  |
| `setfacl`                      | ACL-Rechte setzen                    |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Benutzer, Gruppen und Rechte ein zentrales Thema.

In der Praxis bedeutet das:

- Benutzerkonten verwalten
- Gruppenmitgliedschaften prüfen
- Zugriffe auf Projektordner einrichten
- Rechteprobleme analysieren
- Dienste mit passenden Benutzern betreiben
- SSH-Schlüssel korrekt absichern
- sudo bewusst nutzen
- Dateibesitzer korrigieren
- Webserver- und Docker-Rechte verstehen
- Sicherheitsprinzipien anwenden
- Berechtigungen dokumentieren

Ein guter FISI löst Rechteprobleme nicht einfach mit `chmod 777`, sondern prüft Benutzer, Gruppe, Besitzer, Verzeichnisrechte und den tatsächlichen Zweck des Zugriffs.

---

## Kurze Zusammenfassung

Linux verwendet Benutzer, Gruppen und Rechte, um Zugriffe zu kontrollieren.

Dateien und Verzeichnisse haben Besitzer, Gruppe und Rechte für Besitzer, Gruppe und andere Benutzer.

Wichtige Rechte sind `r`, `w` und `x`. Bei Dateien bedeutet `x` ausführen, bei Verzeichnissen bedeutet `x` betreten.

Wichtige Befehle sind `whoami`, `id`, `groups`, `ls -l`, `chmod`, `chown`, `chgrp`, `passwd`, `adduser`, `deluser`, `usermod`, `umask`, `getfacl` und `setfacl`.

Für FISI ist dieses Kapitel wichtig, weil Rechteprobleme im Alltag sehr häufig sind und saubere Berechtigungen eine Grundlage für Sicherheit und stabilen Betrieb bilden.
