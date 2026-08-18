# 6. Paketverwaltung

In diesem Kapitel geht es um Paketverwaltung unter Linux.

Paketverwaltung bedeutet, Software sauber zu installieren, zu aktualisieren, zu entfernen und Informationen über installierte Programme zu prüfen. Unter Linux wird Software meistens nicht von irgendeiner Webseite heruntergeladen, sondern über Paketquellen und Paketmanager installiert.

Für Fachinformatiker für Systemintegration ist Paketverwaltung wichtig, weil Server und Clients aktuell, sicher und nachvollziehbar verwaltet werden müssen.

---

## Kurz erklärt

Ein Paket ist eine vorbereitete Softwareeinheit.

Ein Paket kann enthalten:

- Programme
- Bibliotheken
- Konfigurationsdateien
- Dienste
- Dokumentation
- Abhängigkeiten
- Installationsskripte

Ein Paketmanager kümmert sich darum, Pakete zu installieren, zu aktualisieren und zu entfernen.

Bei Debian und Ubuntu sind besonders wichtig:

- `apt`
- `dpkg`

`apt` arbeitet mit Paketquellen und löst Abhängigkeiten automatisch auf.

`dpkg` arbeitet direkter mit einzelnen `.deb`-Paketen.

---

## Warum Paketverwaltung wichtig ist

Paketverwaltung sorgt dafür, dass Software kontrolliert installiert wird.

Ohne Paketmanager müsste man viele Programme manuell herunterladen, entpacken, kompilieren und aktualisieren.

Das wäre fehleranfällig und schwer wartbar.

Vorteile von Paketverwaltung:

- einfache Installation
- einfache Updates
- automatische Abhängigkeiten
- Sicherheitsupdates
- saubere Entfernung
- Versionsverwaltung
- zentrale Paketquellen
- weniger manuelle Fehler
- bessere Nachvollziehbarkeit
- Integration in das System

Für Server ist das besonders wichtig, weil unkontrollierte Softwareinstallationen Sicherheitsrisiken erzeugen können.

---

## Paketquellen

Paketquellen sind Server, von denen Linux Pakete herunterlädt.

Bei Ubuntu und Debian werden diese Quellen in Konfigurationsdateien verwaltet.

Typische Orte:

```text
/etc/apt/sources.list
/etc/apt/sources.list.d/
```

Die Paketquellen enthalten Informationen darüber, welche Pakete verfügbar sind und aus welchen Repositories sie kommen.

Beispielhafte Bereiche bei Ubuntu:

| Bereich      | Bedeutung                                            |
| ------------ | ---------------------------------------------------- |
| `main`       | offiziell unterstützte freie Software                |
| `universe`   | Community-gepflegte freie Software                   |
| `restricted` | proprietäre Treiber oder eingeschränkte Software     |
| `multiverse` | Software mit rechtlichen oder Lizenz-Einschränkungen |

Nicht jede Softwarequelle ist automatisch vertrauenswürdig.

---

## apt

`apt` ist ein Paketmanager für Debian-basierte Systeme wie Ubuntu und Debian.

Mit `apt` kann man:

- Paketlisten aktualisieren
- Pakete installieren
- Pakete entfernen
- Pakete suchen
- Paketinformationen anzeigen
- System aktualisieren
- Abhängigkeiten verwalten

Typische Befehle:

```bash
sudo apt update
sudo apt upgrade
sudo apt install paketname
sudo apt remove paketname
apt search paketname
apt show paketname
```

`apt` ist im Alltag meistens der wichtigste Befehl für Paketverwaltung auf Ubuntu.

---

## Paketlisten aktualisieren

Mit `apt update` werden die Paketlisten aktualisiert.

```bash
sudo apt update
```

Wichtig:

`apt update` installiert noch keine Updates.

Der Befehl lädt nur aktuelle Informationen aus den Paketquellen.

Das System weiß danach:

- welche Pakete verfügbar sind
- welche Versionen verfügbar sind
- welche Updates existieren
- welche Abhängigkeiten gebraucht werden

Man sollte `apt update` ausführen, bevor man Pakete installiert oder aktualisiert.

---

## Pakete aktualisieren

Mit `apt upgrade` werden installierte Pakete aktualisiert.

```bash
sudo apt upgrade
```

Dieser Befehl installiert verfügbare Updates für bereits installierte Pakete.

Vorher sollte man meistens ausführen:

```bash
sudo apt update
sudo apt upgrade
```

Bedeutung:

| Befehl        | Aufgabe                           |
| ------------- | --------------------------------- |
| `apt update`  | Paketlisten aktualisieren         |
| `apt upgrade` | installierte Pakete aktualisieren |

Das ist ein häufiger Ablauf auf Ubuntu-Servern und Clients.

---

## Unterschied zwischen update und upgrade

`update` und `upgrade` werden oft verwechselt.

| Befehl             | Bedeutung                                     |
| ------------------ | --------------------------------------------- |
| `sudo apt update`  | aktualisiert Paketinformationen               |
| `sudo apt upgrade` | installiert neue Versionen vorhandener Pakete |

Merksatz:

`update` aktualisiert die Liste.  
`upgrade` aktualisiert die installierte Software.

Beispiel:

```bash
sudo apt update
sudo apt upgrade
```

Das ist nicht doppelt. Beide Befehle machen unterschiedliche Dinge.

---

## Paket installieren

Ein Paket installiert man mit:

```bash
sudo apt install paketname
```

Beispiel:

```bash
sudo apt install nginx
```

Dabei prüft `apt`, ob zusätzliche Pakete benötigt werden.

Diese zusätzlichen Pakete heißen Abhängigkeiten.

Beispiel:

Ein Webserver braucht eventuell Bibliotheken oder Hilfsprogramme.  
`apt` installiert diese automatisch mit.

---

## Mehrere Pakete installieren

Man kann mehrere Pakete gleichzeitig installieren.

```bash
sudo apt install git curl htop tree
```

Das ist praktisch, wenn man ein System vorbereitet.

Beispiel für ein neues Testsystem:

```bash
sudo apt update
sudo apt install git curl htop tree net-tools
```

Trotzdem sollte man nur Pakete installieren, die man wirklich braucht.

Jedes zusätzliche Paket kann später Updates, Pflege und mögliche Sicherheitsrisiken bedeuten.

---

## Paket entfernen

Ein Paket entfernt man mit:

```bash
sudo apt remove paketname
```

Beispiel:

```bash
sudo apt remove nginx
```

`remove` entfernt das Programm, lässt aber Konfigurationsdateien oft auf dem System.

Das kann nützlich sein, wenn man das Paket später erneut installieren möchte und die alte Konfiguration behalten will.

---

## Paket vollständig entfernen mit purge

Mit `purge` entfernt man Paket und Konfigurationsdateien.

```bash
sudo apt purge paketname
```

Beispiel:

```bash
sudo apt purge nginx
```

Unterschied:

| Befehl       | Wirkung                                                |
| ------------ | ------------------------------------------------------ |
| `apt remove` | entfernt Paket, lässt Konfigurationsreste oft bestehen |
| `apt purge`  | entfernt Paket und Konfigurationsdateien               |

`purge` ist stärker als `remove`.

Man sollte vorher überlegen, ob man die Konfiguration noch braucht.

---

## Nicht mehr benötigte Pakete entfernen

Mit `autoremove` entfernt man Pakete, die automatisch installiert wurden und nicht mehr gebraucht werden.

```bash
sudo apt autoremove
```

Beispiel:

Ein Paket wird installiert und bringt Abhängigkeiten mit.  
Später wird das Hauptpaket entfernt.  
Dann können manche Abhängigkeiten überflüssig sein.

`autoremove` räumt solche Pakete auf.

Wichtig:

Vor dem Bestätigen lesen, welche Pakete entfernt werden.

---

## Paket suchen

Mit `apt search` sucht man nach Paketen.

```bash
apt search nginx
```

Beispiel:

```bash
apt search python
```

Die Ausgabe kann sehr lang sein.

Man kann auch mit `grep` filtern:

```bash
apt search python | grep venv
```

Suchen ist nützlich, wenn man den genauen Paketnamen nicht kennt.

---

## Paketinformationen anzeigen

Mit `apt show` zeigt man Details zu einem Paket.

```bash
apt show paketname
```

Beispiel:

```bash
apt show nginx
```

Typische Informationen:

- Paketname
- Version
- Beschreibung
- Abhängigkeiten
- Installationsgröße
- Quelle
- Maintainer
- Homepage

Vor der Installation kann man so prüfen, ob das Paket das richtige ist.

---

## Installierte Pakete anzeigen

Installierte Pakete anzeigen:

```bash
apt list --installed
```

Nach einem bestimmten Paket suchen:

```bash
apt list --installed | grep nginx
```

Alternative mit `dpkg`:

```bash
dpkg -l
dpkg -l | grep nginx
```

Das ist hilfreich, wenn man prüfen möchte, ob Software bereits installiert ist.

---

## Paketversion prüfen

Version eines installierten Pakets prüfen:

```bash
apt list --installed | grep paketname
```

Beispiel:

```bash
apt list --installed | grep openssh
```

Oder mit `apt show`:

```bash
apt show openssh-server
```

Bei Fehlern ist die Paketversion wichtig, weil manche Probleme nur bestimmte Versionen betreffen.

---

## Paketdateien anzeigen

Mit `dpkg -L` sieht man, welche Dateien ein Paket installiert hat.

```bash
dpkg -L paketname
```

Beispiel:

```bash
dpkg -L openssh-server
```

Das kann zeigen:

- Programmdateien
- Konfigurationsdateien
- systemd-Unit-Dateien
- Dokumentation
- Hilfsdateien

Nützlich, wenn man wissen möchte, wo Dateien eines Pakets liegen.

---

## Herausfinden, zu welchem Paket eine Datei gehört

Mit `dpkg -S` kann man herausfinden, welches Paket eine Datei installiert hat.

```bash
dpkg -S /pfad/zur/datei
```

Beispiel:

```bash
dpkg -S /usr/bin/ssh
```

Mögliche Ausgabe:

```text
openssh-client: /usr/bin/ssh
```

Das ist sehr nützlich bei Fehlersuche und Dokumentation.

---

## dpkg

`dpkg` ist ein niedrigeres Werkzeug zur Paketverwaltung auf Debian-basierten Systemen.

`apt` nutzt im Hintergrund auch `dpkg`.

Wichtige Befehle:

```bash
dpkg -l
dpkg -L paketname
dpkg -S /pfad/zur/datei
sudo dpkg -i paket.deb
```

Unterschied:

| Werkzeug | Aufgabe                                                     |
| -------- | ----------------------------------------------------------- |
| `apt`    | komfortable Paketverwaltung mit Quellen und Abhängigkeiten  |
| `dpkg`   | direkte Arbeit mit installierten Paketen und `.deb`-Dateien |

Im Alltag nutzt man meistens `apt`.

`dpkg` ist nützlich für Details und lokale `.deb`-Pakete.

---

## Lokale .deb-Pakete installieren

Manchmal lädt man ein `.deb`-Paket manuell herunter.

Installation mit `apt`:

```bash
sudo apt install ./paket.deb
```

Oder mit `dpkg`:

```bash
sudo dpkg -i paket.deb
```

Wenn bei `dpkg` Abhängigkeiten fehlen:

```bash
sudo apt install -f
```

Besser ist oft:

```bash
sudo apt install ./paket.deb
```

Weil `apt` Abhängigkeiten besser auflösen kann.

---

## Abhängigkeiten

Viele Programme brauchen andere Pakete, um zu funktionieren.

Diese benötigten Pakete heißen Abhängigkeiten.

Beispiel:

Ein Programm braucht:

- Bibliotheken
- Laufzeitumgebungen
- Systemwerkzeuge
- andere Dienste

`apt` erkennt Abhängigkeiten und installiert sie automatisch mit.

Problematisch kann es werden, wenn:

- Paketquellen fehlen
- Versionen nicht zusammenpassen
- manuell installierte Pakete stören
- alte Paketstände existieren
- Fremdquellen benutzt wurden

Darum sollte man Paketquellen sauber halten.

---

## Paketkonflikte

Ein Paketkonflikt entsteht, wenn Pakete nicht zusammenpassen.

Mögliche Ursachen:

- zwei Pakete wollen dieselbe Datei bereitstellen
- Versionen passen nicht zusammen
- Abhängigkeiten können nicht erfüllt werden
- Paketquelle ist falsch
- fremde Paketquelle liefert inkompatible Version
- manuelle Installation stört Paketmanager

Typische Fehlermeldungen:

```text
held broken packages
unmet dependencies
package conflicts with
dependency problems
```

Bei solchen Fehlern sollte man die Meldung genau lesen und nicht blind Befehle kopieren.

---

## Beschädigte Paketinstallation reparieren

Wenn eine Paketinstallation unterbrochen wurde, kann man versuchen:

```bash
sudo apt install -f
```

Oder:

```bash
sudo dpkg --configure -a
```

Bedeutung:

| Befehl                | Aufgabe                                        |
| --------------------- | ---------------------------------------------- |
| `apt install -f`      | versucht fehlende Abhängigkeiten zu reparieren |
| `dpkg --configure -a` | konfiguriert unvollständig installierte Pakete |

Diese Befehle sind hilfreich, wenn eine Installation abgebrochen wurde oder Abhängigkeiten fehlen.

---

## Paketmanager-Lock

Manchmal erscheint eine Meldung, dass `apt` gesperrt ist.

Beispiel:

```text
Could not get lock /var/lib/dpkg/lock-frontend
```

Das bedeutet meistens:

Ein anderer Paketprozess läuft gerade.

Mögliche Ursachen:

- automatische Updates laufen
- anderes Terminal nutzt apt
- Software Center ist offen
- vorheriger Paketprozess hängt noch

Prüfen:

```bash
ps aux | grep apt
ps aux | grep dpkg
```

Wichtig:

Lock-Dateien nicht einfach löschen, ohne zu verstehen, ob noch ein Paketprozess läuft.

Ein abgebrochener Paketprozess kann das System beschädigen.

---

## Paketquellen prüfen

Paketquellen liegen häufig hier:

```text
/etc/apt/sources.list
/etc/apt/sources.list.d/
```

Anzeigen:

```bash
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

Bei Problemen kann man prüfen:

```bash
sudo apt update
```

Wenn eine Quelle nicht erreichbar ist oder Fehler liefert, zeigt `apt update` meistens eine Meldung.

Paketquellen sollten nur aus vertrauenswürdigen Quellen stammen.

---

## Fremdquellen und PPAs

Ein PPA ist eine zusätzliche Paketquelle, häufig für Ubuntu.

PPA bedeutet:

```text
Personal Package Archive
```

PPAs können nützlich sein, aber auch Risiken haben.

Mögliche Probleme:

- Pakete sind nicht offiziell geprüft
- Versionen können Konflikte verursachen
- Updates können Systempakete überschreiben
- Quelle kann später nicht mehr gepflegt werden
- Sicherheitsrisiko durch fremde Maintainer

Für Server sollte man zusätzliche Paketquellen sehr vorsichtig verwenden und dokumentieren.

---

## GPG-Schlüssel und Vertrauen

Paketquellen nutzen Signaturen, damit Pakete überprüft werden können.

Dafür werden GPG-Schlüssel verwendet.

Die Grundidee:

- Paketquelle signiert Pakete oder Paketlisten
- System prüft Signatur
- dadurch erkennt man Manipulationen besser

Fehler bei `apt update` können auftreten, wenn ein Schlüssel fehlt oder abgelaufen ist.

Wichtig:

Man sollte Schlüssel nur aus vertrauenswürdigen Quellen hinzufügen.

---

## Sicherheitsupdates

Sicherheitsupdates schließen bekannte Schwachstellen.

Regelmäßige Updates sind wichtig für:

- Server
- Clients
- Datenbanken
- Webserver
- SSH
- Browser
- Programmbibliotheken
- Container-Hosts

Typischer Ablauf:

```bash
sudo apt update
sudo apt upgrade
```

Auf Servern sollte man Updates planen, testen und dokumentieren.

Nicht jedes Update ist risikofrei. Bei produktiven Systemen können Dienste neu gestartet werden müssen.

---

## Upgrade, full-upgrade und dist-upgrade

Neben `upgrade` gibt es auch stärkere Upgrade-Befehle.

```bash
sudo apt full-upgrade
```

Oder älter:

```bash
sudo apt dist-upgrade
```

Diese Befehle können Pakete installieren oder entfernen, wenn das für ein Upgrade nötig ist.

Unterschied grob:

| Befehl         | Verhalten                                           |
| -------------- | --------------------------------------------------- |
| `upgrade`      | aktualisiert Pakete möglichst ohne Entfernen        |
| `full-upgrade` | darf Pakete installieren oder entfernen, wenn nötig |
| `dist-upgrade` | ältere Bezeichnung mit ähnlicher Bedeutung          |

Auf Servern sollte man vor `full-upgrade` genau lesen, was geändert wird.

---

## Distribution-Upgrade

Ein Distribution-Upgrade ist ein Upgrade auf eine neue Version der Distribution.

Beispiel:

Ubuntu 24.04 auf eine spätere Ubuntu-Version.

Das ist nicht dasselbe wie normale Paketupdates.

Ein Distribution-Upgrade kann ändern:

- Kernel
- Systembibliotheken
- Dienste
- Konfigurationsdateien
- Paketquellen
- Standardversionen von Programmen
- Abhängigkeiten

Vor einem Distribution-Upgrade braucht man:

- Backup
- Wartungsfenster
- Dokumentation
- Kompatibilitätsprüfung
- Rollback-Plan
- Testumgebung, wenn möglich

---

## Paket zurückhalten

Manchmal soll ein Paket nicht automatisch aktualisiert werden.

Paket halten:

```bash
sudo apt-mark hold paketname
```

Hold entfernen:

```bash
sudo apt-mark unhold paketname
```

Gehaltene Pakete anzeigen:

```bash
apt-mark showhold
```

Das kann bei produktiven Systemen nötig sein, wenn eine bestimmte Version gebraucht wird.

Aber gehaltene Pakete können Sicherheitsupdates verhindern.

Deshalb muss man solche Entscheidungen dokumentieren.

---

## Paket neu installieren

Ein Paket kann neu installiert werden.

```bash
sudo apt reinstall paketname
```

Beispiel:

```bash
sudo apt reinstall openssh-server
```

Das kann helfen, wenn Dateien eines Pakets beschädigt oder gelöscht wurden.

Aber Konfigurationsprobleme werden dadurch nicht immer gelöst, besonders wenn Konfigurationsdateien weiterhin bestehen.

---

## Paket-Cache

`apt` speichert heruntergeladene Paketdaten im Cache.

Cache aufräumen:

```bash
sudo apt clean
```

Nicht mehr benötigte Paketdateien entfernen:

```bash
sudo apt autoclean
```

Unterschied grob:

| Befehl          | Bedeutung                                      |
| --------------- | ---------------------------------------------- |
| `apt clean`     | leert den Paketcache stark                     |
| `apt autoclean` | entfernt nur nicht mehr benötigte Paketdateien |

Das kann Speicherplatz freigeben.

Auf Servern mit wenig Speicher kann das wichtig sein.

---

## Paketlogs

Paketaktionen werden protokolliert.

Wichtige Logs:

```text
/var/log/apt/history.log
/var/log/apt/term.log
/var/log/dpkg.log
```

Anzeigen:

```bash
less /var/log/apt/history.log
less /var/log/dpkg.log
```

Diese Logs zeigen zum Beispiel:

- installierte Pakete
- entfernte Pakete
- Updates
- Zeitpunkte
- verwendete Befehle

Das ist sehr hilfreich, wenn nach einem Update ein Problem auftritt.

---

## Welche Updates sind verfügbar?

Verfügbare Updates anzeigen:

```bash
apt list --upgradable
```

Nach `apt update` sieht man oft auch direkt, wie viele Pakete aktualisiert werden können.

Beispiel:

```bash
sudo apt update
apt list --upgradable
```

Das ist nützlich, wenn man erst prüfen möchte, was aktualisiert werden würde.

---

## Paketinstallation simulieren

Man kann manche apt-Aktionen simulieren.

Beispiel:

```bash
apt install paketname --simulate
```

Oder kurz:

```bash
apt install paketname -s
```

Das zeigt, was passieren würde, ohne wirklich zu installieren.

Das ist hilfreich, wenn man unsicher ist, welche Pakete betroffen wären.

---

## Snap

Ubuntu nutzt neben `apt` auch Snap.

Snap-Pakete sind ein anderes Paketformat.

Wichtige Befehle:

```bash
snap list
snap find paketname
sudo snap install paketname
sudo snap remove paketname
```

Snap-Pakete enthalten oft viele Abhängigkeiten selbst und laufen stärker isoliert.

Vorteile:

- einfache Installation
- aktuelle Versionen
- teilweise bessere Isolation
- distributionübergreifend nutzbar

Nachteile:

- manchmal größer
- Start kann langsamer sein
- andere Verwaltung als apt
- nicht immer passend für Server

Für klassische Serveradministration ist `apt` meistens wichtiger.

---

## Flatpak

Flatpak ist ein weiteres Paketformat, besonders für Desktop-Anwendungen.

Wichtige Befehle:

```bash
flatpak list
flatpak search paketname
flatpak install paketname
flatpak uninstall paketname
```

Flatpak wird eher im Desktop-Bereich genutzt.

Für Server ist es weniger wichtig als `apt`.

Für FISI sollte man wissen, dass es verschiedene Paketformate gibt und nicht jedes installierte Programm über `apt` verwaltet wird.

---

## Manuell installierte Software

Nicht jede Software wird über `apt` installiert.

Manchmal wird Software installiert über:

- `.deb`-Datei
- Skript
- Archivdatei
- Git-Repository
- Docker-Image
- Snap
- Flatpak
- selbst kompilierte Software
- Herstellerinstaller

Problem:

Manuell installierte Software wird nicht immer automatisch über den Paketmanager aktualisiert.

Deshalb muss man dokumentieren:

- woher die Software kommt
- welche Version installiert wurde
- wohin sie installiert wurde
- wie Updates funktionieren
- wie sie entfernt wird
- welche Dienste dazugehören

---

## Paketverwaltung und Dienste

Viele Pakete installieren Dienste.

Beispiel:

```bash
sudo apt install nginx
```

Danach prüfen:

```bash
systemctl status nginx
systemctl is-enabled nginx
ss -tulpen | grep :80
```

Nicht nur die Installation ist wichtig.

Man muss auch prüfen:

- läuft der Dienst?
- startet der Dienst automatisch?
- auf welchem Port lauscht der Dienst?
- gibt es Logs?
- wurde eine Konfiguration angelegt?
- ist der Dienst von außen erreichbar?

Paketverwaltung hängt also oft mit systemd, Logs und Netzwerk zusammen.

---

## Paketverwaltung und Konfigurationsdateien

Beim Installieren von Paketen werden oft Konfigurationsdateien erstellt.

Typische Orte:

```text
/etc
/etc/paketname
```

Beispiel:

```text
/etc/ssh/sshd_config
/etc/nginx/nginx.conf
```

Wichtig:

Bei Updates kann das System fragen, ob eine geänderte Konfigurationsdatei behalten oder ersetzt werden soll.

Man sollte solche Fragen nicht blind bestätigen.

Vor größeren Änderungen:

```bash
sudo cp /etc/paket/config.conf /etc/paket/config.conf.backup
```

---

## Paketverwaltung und Sicherheit

Paketverwaltung ist Teil der Systemsicherheit.

Wichtige Punkte:

- Paketquellen müssen vertrauenswürdig sein
- Sicherheitsupdates müssen eingespielt werden
- unnötige Pakete sollten entfernt werden
- Dienste nach Installation prüfen
- alte Pakete können Schwachstellen enthalten
- Fremdquellen erhöhen Risiko
- Paketlogs helfen bei Nachvollziehbarkeit
- keine zufälligen Installationsskripte aus dem Internet ausführen

Besonders gefährlich ist dieses Muster:

```bash
curl example.com/install.sh | sudo bash
```

Das führt ein Skript aus dem Internet direkt mit Root-Rechten aus.

So etwas sollte man nicht blind verwenden.

---

## Typischer Ablauf auf Ubuntu

Ein typischer sicherer Ablauf:

```bash
sudo apt update
apt list --upgradable
sudo apt upgrade
sudo apt autoremove
```

Wenn ein neues Paket installiert werden soll:

```bash
apt search paketname
apt show paketname
sudo apt install paketname
```

Danach prüfen:

```bash
which programmname
programmname --version
systemctl status dienstname
```

Nicht jeder Schritt ist immer nötig, aber dieser Ablauf ist sauber und nachvollziehbar.

---

## Typische Fehler

| Fehler                                     | Problem                                                  |
| ------------------------------------------ | -------------------------------------------------------- |
| `apt update` und `apt upgrade` verwechseln | Updates werden nicht installiert oder Listen bleiben alt |
| Paketquellen blind hinzufügen              | Sicherheits- und Stabilitätsrisiko                       |
| Fehlermeldungen nicht lesen                | Ursache bleibt unklar                                    |
| Lock-Dateien einfach löschen               | Paketdatenbank kann beschädigt werden                    |
| `purge` nutzen ohne Nachdenken             | Konfiguration wird gelöscht                              |
| `autoremove` blind bestätigen              | eventuell wichtige Pakete werden entfernt                |
| Updates nie installieren                   | Sicherheitslücken bleiben offen                          |
| zu viele Fremdquellen nutzen               | Paketkonflikte werden wahrscheinlicher                   |
| manuelle Software nicht dokumentieren      | spätere Wartung wird schwierig                           |
| Dienste nach Installation nicht prüfen     | Software ist installiert, aber nicht nutzbar             |

---

## Praktische Beispiele

### Beispiel 1: htop installieren

```bash
sudo apt update
sudo apt install htop
htop
```

Damit wird das Paket installiert und direkt getestet.

### Beispiel 2: Nginx installieren und prüfen

```bash
sudo apt update
sudo apt install nginx
systemctl status nginx
ss -tulpen | grep :80
```

Damit prüft man nicht nur die Installation, sondern auch den Dienst und den offenen Port.

### Beispiel 3: Paketinformationen prüfen

```bash
apt search openssh
apt show openssh-server
apt list --installed | grep openssh
```

Damit findet man das Paket, liest Informationen und prüft, ob es installiert ist.

### Beispiel 4: Paketlogs prüfen

```bash
less /var/log/apt/history.log
less /var/log/dpkg.log
```

Damit kann man nachvollziehen, welche Pakete zuletzt installiert, entfernt oder aktualisiert wurden.

---

## Nützliche Befehle

| Befehl                     | Bedeutung                               |
| -------------------------- | --------------------------------------- |
| `sudo apt update`          | Paketlisten aktualisieren               |
| `sudo apt upgrade`         | installierte Pakete aktualisieren       |
| `sudo apt full-upgrade`    | umfangreicheres Upgrade                 |
| `sudo apt install paket`   | Paket installieren                      |
| `sudo apt remove paket`    | Paket entfernen                         |
| `sudo apt purge paket`     | Paket inklusive Konfiguration entfernen |
| `sudo apt autoremove`      | nicht mehr benötigte Pakete entfernen   |
| `sudo apt clean`           | Paketcache leeren                       |
| `apt search paket`         | Paket suchen                            |
| `apt show paket`           | Paketinformationen anzeigen             |
| `apt list --installed`     | installierte Pakete anzeigen            |
| `apt list --upgradable`    | verfügbare Updates anzeigen             |
| `apt-mark hold paket`      | Paket zurückhalten                      |
| `apt-mark unhold paket`    | Paket wieder freigeben                  |
| `dpkg -l`                  | installierte Pakete anzeigen            |
| `dpkg -L paket`            | Dateien eines Pakets anzeigen           |
| `dpkg -S datei`            | Paket zu einer Datei finden             |
| `sudo dpkg --configure -a` | unvollständige Pakete konfigurieren     |
| `sudo apt install -f`      | Abhängigkeitsprobleme reparieren        |
| `snap list`                | Snap-Pakete anzeigen                    |
| `flatpak list`             | Flatpak-Pakete anzeigen                 |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Paketverwaltung eine wichtige Alltagsaufgabe.

In der Praxis bedeutet das:

- Software auf Servern installieren
- Updates einspielen
- Sicherheitsupdates beachten
- Paketquellen prüfen
- installierte Pakete dokumentieren
- Paketfehler beheben
- Dienste nach Installation prüfen
- Abhängigkeiten verstehen
- Paketlogs auswerten
- Fremdquellen kritisch bewerten
- manuelle Installationen dokumentieren
- Systeme aktuell und wartbar halten

Ein guter FISI installiert nicht einfach nur Pakete, sondern prüft danach auch Version, Dienststatus, Logs, offene Ports, Konfiguration und Sicherheit.

---

## Kurze Zusammenfassung

Paketverwaltung steuert die Installation, Aktualisierung und Entfernung von Software.

Auf Ubuntu und Debian sind `apt` und `dpkg` besonders wichtig.

Wichtige Befehle sind `apt update`, `apt upgrade`, `apt install`, `apt remove`, `apt purge`, `apt autoremove`, `apt search`, `apt show`, `apt list`, `dpkg -l`, `dpkg -L` und `dpkg -S`.

Für FISI ist Paketverwaltung wichtig, weil sichere und stabile Systeme regelmäßig gepflegt, aktualisiert und sauber dokumentiert werden müssen.
