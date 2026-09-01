# 2. Virtuelle Maschinen

In diesem Kapitel geht es um virtuelle Maschinen.

Eine virtuelle Maschine ist ein vollständiger virtueller Computer, der auf einem physischen Host läuft. Sie hat eigene virtuelle Hardware, ein eigenes Betriebssystem, eigene Dienste und eine eigene Konfiguration.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Server, Testsysteme und Schulungsumgebungen als virtuelle Maschinen betrieben werden.

---

## Kurz erklärt

Eine virtuelle Maschine, kurz VM, verhält sich wie ein eigener Computer.

Sie besitzt eigene:

```text
virtuelle CPU
virtuellen Arbeitsspeicher
virtuelle Festplatte
virtuelle Netzwerkkarte
Betriebssystem
Benutzerkonten
Dienste
IP-Adresse
Konfiguration
```

Beispiel:

```text
Physischer Laptop mit Ubuntu
└── VM: Ubuntu Server
    ├── 2 vCPUs
    ├── 4 GB RAM
    ├── 40 GB virtuelle Festplatte
    ├── virtuelle Netzwerkkarte
    └── SSH-Dienst
```

Für das Betriebssystem in der VM sieht es so aus, als würde es auf echter Hardware laufen.

---

## Warum virtuelle Maschinen genutzt werden

Virtuelle Maschinen werden genutzt, um Systeme flexibel zu betreiben.

Beispiele:

```text
Ubuntu Server testen
Windows Server installieren
Datenbankserver aufsetzen
Netzwerklabor bauen
Software gefahrlos testen
Schulungssystem bereitstellen
Serverdienste trennen
Home-Lab betreiben
```

Man braucht nicht für jedes System einen eigenen physischen Computer.

Das spart Hardware und macht Tests einfacher.

---

## VM als eigener Computer

Eine VM ist nicht nur ein Programmfenster.

Sie ist ein eigener virtueller Computer.

Sie kann:

```text
ein Betriebssystem starten
Benutzerkonten haben
Dienste ausführen
Netzwerk nutzen
Dateien speichern
Updates installieren
Logs schreiben
Fehler haben
gehackt werden
gesichert werden müssen
```

Wichtig:

```text
Eine VM muss genauso administriert werden wie ein echtes System.
```

Nur weil sie virtuell ist, ist sie nicht automatisch sicher oder unwichtig.

---

## Bestandteile einer VM

Eine VM besteht aus mehreren Teilen.

| Bestandteil | Bedeutung |
|---|---|
| Konfigurationsdatei | enthält Einstellungen der VM |
| virtuelle Festplatte | enthält Betriebssystem und Daten |
| virtuelle Netzwerkkarte | verbindet VM mit Netzwerk |
| vCPU | virtuelle Prozessorressourcen |
| RAM | zugewiesener Arbeitsspeicher |
| ISO-Datei | Installationsmedium |
| Snapshot | gespeicherter Zustand |
| virtuelle Anzeige | Bildschirm der VM |

Je nach Virtualisierungsplattform heißen diese Dateien und Optionen etwas anders.

Die Grundidee bleibt aber gleich.

---

## Virtuelle CPU

Eine VM bekommt eine bestimmte Anzahl an vCPUs.

Beispiel:

```text
Ubuntu Server VM: 2 vCPUs
Windows Server VM: 4 vCPUs
Test-Client VM: 2 vCPUs
```

Mehr vCPU bedeutet nicht automatisch besser.

Wenn zu viele VMs gleichzeitig viel CPU-Leistung brauchen, wird der Host langsam.

Gute Fragen:

```text
Was macht die VM?
Wie viele Dienste laufen darauf?
Ist es ein Testsystem oder produktives System?
Wie viele CPU-Kerne hat der Host?
Laufen noch andere VMs?
```

---

## Arbeitsspeicher

Eine VM braucht RAM vom Host.

Beispiel:

```text
Host hat 16 GB RAM.
Host-System braucht selbst RAM.
VM 1 bekommt 4 GB.
VM 2 bekommt 4 GB.
VM 3 bekommt 2 GB.
```

Wenn zu viel RAM vergeben wird, kann der Host langsam werden oder anfangen zu swappen.

Wichtig:

```text
Nicht den kompletten RAM an VMs vergeben.
Der Host braucht selbst auch Arbeitsspeicher.
```

---

## Virtuelle Festplatte

Die virtuelle Festplatte ist der Speicher der VM.

Dort liegen:

```text
Betriebssystem
Programme
Konfigurationen
Benutzerdaten
Logs
Dienste
Datenbanken
```

Häufige Formate:

```text
qcow2
vdi
vmdk
raw
```

Beispiel:

```text
ubuntu-server.qcow2
windows-server.vdi
test-client.vmdk
```

Wenn die virtuelle Festplatte gelöscht oder beschädigt wird, kann die VM nicht mehr normal starten.

---

## Dynamische virtuelle Festplatte

Eine dynamische virtuelle Festplatte wächst nur bei Bedarf.

Beispiel:

```text
VM bekommt 40 GB virtuelle Festplatte.
Auf dem Host belegt sie am Anfang nur 8 GB.
Mit mehr Daten wächst die Datei.
```

Vorteil:

```text
spart Speicherplatz
```

Nachteil:

```text
Host kann voll laufen, wenn viele dynamische Festplatten wachsen
```

Man muss also trotzdem den freien Speicher auf dem Host beobachten.

---

## Fest zugewiesene virtuelle Festplatte

Eine fest zugewiesene virtuelle Festplatte reserviert den Speicher direkt.

Beispiel:

```text
VM bekommt 40 GB.
Host reserviert direkt 40 GB.
```

Vorteil:

```text
planbarer Speicherverbrauch
```

Nachteil:

```text
braucht direkt mehr Platz
```

In Laborumgebungen sind dynamische Festplatten oft praktisch.

In produktiven Umgebungen muss Storage genauer geplant werden.

---

## ISO-Datei

Eine ISO-Datei ist ein Installationsabbild.

Beispiele:

```text
Ubuntu Server ISO
Debian ISO
Windows Server ISO
Rescue-System ISO
```

Ablauf:

```text
ISO herunterladen
VM erstellen
ISO als virtuelles CD/DVD-Laufwerk einbinden
VM starten
Betriebssystem installieren
ISO nach Installation entfernen
```

Wenn die ISO nach der Installation nicht entfernt wird, startet die VM manchmal wieder ins Installationsmenü.

---

## Betriebssystem in der VM

In einer VM kann man verschiedene Betriebssysteme installieren.

Beispiele:

```text
Ubuntu Server
Debian
Windows Server
Windows 10 / 11
Fedora
pfSense
Kali Linux für Lernumgebungen
```

Wichtig ist, das Betriebssystem passend zum Zweck zu wählen.

Beispiel:

```text
Linux-Server für SSH und Docker
Windows Server für Active Directory Tests
pfSense für Firewall-Labor
Windows Client für Domänen-Tests
```

---

## VM erstellen

Eine VM wird normalerweise über eine Oberfläche oder einen Befehl erstellt.

Dabei legt man fest:

```text
Name der VM
Betriebssystemtyp
CPU
RAM
Festplatte
Netzwerkmodus
ISO-Datei
Startreihenfolge
```

Beispiel-Plan:

```text
Name: ubuntu-server-lab
OS: Ubuntu Server
CPU: 2 vCPUs
RAM: 4 GB
Disk: 40 GB
Network: NAT oder Bridge
ISO: Ubuntu Server ISO
```

Eine saubere Planung verhindert später viele Fehler.

---

## VM benennen

Gute Namen sind wichtig.

Schlecht:

```text
test
vm1
linuxneu
ubuntu123
serverfinal
```

Besser:

```text
ubuntu-server-lab
win-server-ad-lab
debian-docker-test
client-win11-test
pfsense-firewall-lab
```

Ein guter Name zeigt direkt:

```text
Betriebssystem
Zweck
Umgebung
```

Das hilft besonders, wenn man viele VMs hat.

---

## VM-Lebenszyklus

Eine VM hat einen Lebenszyklus.

Typische Zustände:

```text
erstellt
installiert
gestartet
gestoppt
pausiert
gesichert
geklont
gelöscht
archiviert
```

Man sollte alte VMs nicht dauerhaft unkontrolliert laufen lassen.

Alte Testsysteme können:

```text
Ressourcen verbrauchen
Sicherheitslücken enthalten
veraltete Dienste betreiben
unübersichtlich werden
```

---

## VM starten und stoppen

Eine VM kann gestartet und gestoppt werden.

Wichtig:

```text
VM sauber herunterfahren, wenn möglich.
Nicht immer hart ausschalten.
```

Sauberes Herunterfahren:

```text
Betriebssystem fährt Dienste korrekt runter.
Dateisystem wird sauber geschlossen.
Daten werden geschrieben.
```

Hartes Ausschalten kann zu Problemen führen:

```text
Dateisystemfehler
Datenverlust
beschädigte Datenbanken
nicht sauber gestoppte Dienste
```

---

## Virtuelle Netzwerkkarte

Eine VM braucht eine virtuelle Netzwerkkarte, wenn sie Netzwerkzugriff haben soll.

Die VM sieht diese Karte wie eine echte Netzwerkkarte.

In der VM kann man prüfen:

```bash
ip a
ip route
ping 8.8.8.8
ping github.com
```

Typische Netzwerkmodi:

```text
NAT
Bridge
Host-only
Internal Network
```

Der Netzwerkmodus entscheidet, wie die VM mit Host, LAN und Internet kommunizieren kann.

---

## NAT bei einer VM

Bei NAT nutzt die VM den Host als Übergang.

Vereinfacht:

```text
VM -> Host -> Internet
```

Vorteile:

```text
einfach für Internetzugang
gut für Tests
VM ist nicht direkt im LAN sichtbar
```

Nachteile:

```text
andere Geräte erreichen die VM oft nicht direkt
Portweiterleitung kann nötig sein
```

NAT ist gut, wenn die VM hauptsächlich Internet braucht und nicht direkt von außen erreichbar sein muss.

---

## Bridge bei einer VM

Bei Bridge ist die VM wie ein eigenes Gerät im lokalen Netzwerk.

Vereinfacht:

```text
VM -> LAN
```

Die VM bekommt oft eine IP-Adresse aus dem normalen Netzwerk.

Vorteile:

```text
VM ist von anderen Geräten erreichbar
gut für Serverdienste im Lab
realistisches Netzwerkverhalten
```

Nachteile:

```text
VM ist sichtbarer im Netzwerk
Firewall und Updates sind wichtiger
nicht jedes WLAN unterstützt Bridge problemlos
```

Bridge ist gut, wenn die VM wie ein echter Server im Netzwerk arbeiten soll.

---

## Host-only bei einer VM

Host-only bedeutet:

```text
Host und VM können miteinander kommunizieren.
Andere Geräte im Netzwerk meistens nicht.
```

Das ist nützlich für isolierte Laborumgebungen.

Beispiel:

```text
Host verbindet sich per SSH auf Ubuntu-Server-VM.
VM ist nicht im normalen LAN sichtbar.
```

Host-only ist gut, wenn man sicher testen möchte, ohne das normale Netzwerk zu beeinflussen.

---

## IP-Adresse in der VM prüfen

Nach der Installation sollte man prüfen, ob die VM eine IP-Adresse bekommen hat.

Linux-Befehl:

```bash
ip a
```

Routing prüfen:

```bash
ip route
```

DNS testen:

```bash
ping 8.8.8.8
ping github.com
```

Typische Fehler:

```text
keine IP-Adresse
falscher Netzwerkmodus
kein Gateway
DNS funktioniert nicht
Bridge funktioniert im WLAN nicht
```

---

## Dienste in der VM

Eine VM kann Dienste bereitstellen.

Beispiele:

```text
SSH
Webserver
Datenbank
Samba
Docker
DNS
DHCP
Monitoring
```

Dienste prüfen:

```bash
systemctl status ssh
ss -tulpen
journalctl -u ssh
```

Wichtig:

```text
Ein Dienst muss laufen.
Der Port muss offen sein.
Die Firewall muss Zugriff erlauben.
Das Netzwerk muss erreichbar sein.
```

---

## Guest Tools

Viele Virtualisierungsplattformen haben zusätzliche Tools für Gäste.

Beispiele:

```text
VirtualBox Guest Additions
VMware Tools
QEMU Guest Agent
Hyper-V Integration Services
```

Diese Tools verbessern oft:

```text
Grafik
Mausintegration
Zeitsynchronisation
Dateiaustausch
sauberes Herunterfahren
Statusinformationen
Netzwerkfunktionen
```

In Serverumgebungen sind Guest Tools wichtig, weil der Hypervisor die VM besser verwalten kann.

---

## Klonen einer VM

Klonen bedeutet:

```text
Eine VM wird kopiert.
```

Das ist praktisch für Tests.

Beispiel:

```text
Basis-VM mit Ubuntu Server erstellen.
Updates installieren.
SSH einrichten.
Danach VM klonen für verschiedene Tests.
```

Wichtig nach dem Klonen:

```text
Hostname prüfen
IP-Adresse prüfen
SSH-Keys prüfen
MAC-Adresse prüfen
Benutzerkonten prüfen
Dokumentation anpassen
```

Sonst können doppelte Namen oder Netzwerkprobleme entstehen.

---

## Template

Ein Template ist eine vorbereitete Vorlage für neue VMs.

Beispiel:

```text
Ubuntu Server Template
- Updates installiert
- SSH aktiv
- Standardtools installiert
- Basis-Konfiguration gesetzt
```

Aus diesem Template können neue VMs schneller erstellt werden.

Vorteile:

```text
einheitliche Systeme
schneller Aufbau
weniger manuelle Fehler
bessere Wiederholbarkeit
```

Templates sind in professionellen Umgebungen sehr nützlich.

---

## Snapshot kurz erklärt

Ein Snapshot speichert den Zustand einer VM zu einem Zeitpunkt.

Nützlich vor:

```text
Updates
Softwareinstallation
Konfigurationsänderungen
Tests
```

Beispiel:

```text
Snapshot vor Update erstellen.
Update testen.
Wenn Fehler entstehen, Snapshot zurücksetzen.
```

Wichtig:

```text
Snapshot ist kein vollständiges Backup.
```

Snapshots sind gut für kurzfristige Tests, aber nicht als langfristige Datensicherung.

---

## Backup einer VM

Eine VM braucht Backups, wenn wichtige Daten darauf liegen.

Gesichert werden können:

```text
gesamte VM
virtuelle Festplatte
Konfigurationsdateien der VM
Dateien innerhalb der VM
Datenbank-Dumps
Anwendungsdaten
```

Wichtig:

```text
Backup muss konsistent sein.
Restore muss getestet werden.
```

Ein Backup ohne erfolgreichen Restore-Test ist unsicher.

---

## Sicherheit in VMs

Eine VM muss sicher betrieben werden.

Wichtige Punkte:

```text
Updates installieren
Firewall prüfen
SSH absichern
starke Passwörter oder SSH-Schlüssel nutzen
nur notwendige Dienste aktivieren
Benutzerrechte begrenzen
Logs prüfen
Backups schützen
Netzwerkmodus bewusst wählen
```

Eine VM im Bridge-Modus ist im Netzwerk sichtbarer als eine VM im NAT-Modus.

Deshalb sind Firewall, Updates und Dienste besonders wichtig.

---

## Dokumentation einer VM

Jede wichtige VM sollte dokumentiert werden.

Sinnvolle Informationen:

```text
Name der VM
Zweck
Betriebssystem
CPU
RAM
Festplattengröße
Netzwerkmodus
IP-Adresse
Dienste
offene Ports
Benutzer/Zugriff
Backup-Status
Snapshot-Status
Besonderheiten
```

Beispiel:

```text
Name: ubuntu-server-lab
Zweck: Linux-Server-Testumgebung
OS: Ubuntu Server
CPU: 2 vCPU
RAM: 4 GB
Disk: 40 GB
Network: Bridge
IP: 192.168.1.50
Dienste: SSH, Docker
```

Gute Dokumentation spart Zeit bei Fehlersuche und Übergabe.

---

## Beispiel: Ubuntu Server VM

Ein einfacher Aufbau:

```text
Name: ubuntu-server-lab
CPU: 2 vCPUs
RAM: 4 GB
Disk: 40 GB
Network: NAT
OS: Ubuntu Server
Dienste: SSH
```

Nach Installation prüfen:

```bash
ip a
ip route
ping 8.8.8.8
ping github.com
systemctl status ssh
```

Wenn SSH genutzt werden soll:

```bash
sudo apt install openssh-server
systemctl status ssh
```

---

## Beispiel: Windows Server VM

Ein Windows Server kann für viele Lernzwecke genutzt werden.

Beispiele:

```text
Active Directory testen
DNS und DHCP testen
Benutzerverwaltung üben
Gruppenrichtlinien kennenlernen
Dateifreigaben testen
Windows-Client anbinden
```

Wichtige VM-Einstellungen:

```text
genug RAM
genug Speicherplatz
passender Netzwerkmodus
sauberer Hostname
regelmäßige Updates
Snapshots vor großen Änderungen
```

---

## Beispiel: Test-Client VM

Eine Client-VM ist nützlich, um Benutzer- oder Netzwerkverhalten zu testen.

Beispiele:

```text
Windows-Client in Domäne aufnehmen
Linux-Client mit Server verbinden
DNS-Auflösung testen
DHCP testen
VPN testen
Softwareinstallation testen
```

Client-VMs helfen, reale Arbeitsplatzsituationen nachzustellen.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| VM bekommt zu wenig RAM | System läuft langsam |
| VM bekommt zu viel RAM | Host wird langsam |
| falscher Netzwerkmodus | VM ist nicht erreichbar |
| ISO bleibt eingebunden | VM startet wieder ins Installationsmedium |
| keine Updates | Sicherheitslücken bleiben |
| Snapshot als Backup genutzt | falsches Sicherheitsgefühl |
| VM schlecht benannt | Übersicht geht verloren |
| alte VMs laufen weiter | Ressourcenverbrauch und Risiko |
| keine Dokumentation | Fehlersuche wird schwer |
| Bridge ohne Firewall | VM ist unnötig offen im Netzwerk |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise mit virtuellen Maschinen:

```text
VM vor Erstellung planen
sinnvollen Namen vergeben
Ressourcen bewusst auswählen
Netzwerkmodus passend wählen
Betriebssystem sauber installieren
Updates einspielen
nur notwendige Dienste aktivieren
Firewall prüfen
Snapshots gezielt nutzen
Backups einrichten
wichtige Daten testen und dokumentieren
```

Wichtige Regel:

```text
Eine VM ist ein echtes System mit virtueller Hardware.
```

Sie muss gepflegt, gesichert und dokumentiert werden.

---

## FISI-Bezug

Virtuelle Maschinen sind für FISI sehr wichtig.

Man braucht sie für:

```text
Serverinstallation
Testumgebungen
Windows- und Linux-Labore
Netzwerktests
AD- und DNS-Übungen
Docker-Tests
Backup- und Restore-Übungen
Troubleshooting
IT-Sicherheit
Dokumentation
```

Ein FISI sollte nicht nur wissen, wie man eine VM startet.

Er sollte auch verstehen:

```text
welche Ressourcen die VM braucht
wie sie ins Netzwerk eingebunden ist
welche Dienste laufen
wie sie gesichert wird
wie man Fehler analysiert
wie man sie dokumentiert
```

---

## Kurze Zusammenfassung

Eine virtuelle Maschine ist ein vollständiger virtueller Computer auf einem physischen Host.

Sie besitzt virtuelle CPU, RAM, Festplatte, Netzwerkkarte und ein eigenes Betriebssystem.

Wichtige Themen sind VM-Erstellung, Betriebssysteminstallation, Netzwerkmodus, Ressourcen, virtuelle Festplatten, Dienste, Guest Tools, Klonen, Templates, Snapshots, Backups, Sicherheit und Dokumentation.

Für FISI sind virtuelle Maschinen besonders wichtig, weil viele Server, Testumgebungen und Home-Labs auf Virtualisierung basieren.