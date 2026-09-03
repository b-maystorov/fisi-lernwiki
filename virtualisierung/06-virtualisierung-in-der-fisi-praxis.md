# 6. Virtualisierung in der FISI-Praxis

In diesem Kapitel geht es darum, wie Virtualisierung in der praktischen Arbeit eines Fachinformatikers für Systemintegration genutzt wird.

Virtualisierung ist in der Praxis nicht nur ein theoretisches Thema. Viele Server, Testumgebungen, Schulungssysteme, Entwicklungsumgebungen und Home-Labs laufen als virtuelle Maschinen.

Für FISI ist wichtig, virtuelle Maschinen nicht nur zu starten, sondern sie sauber zu planen, zu installieren, zu vernetzen, abzusichern, zu sichern und zu dokumentieren.

---

## Kurz erklärt

Virtualisierung in der FISI-Praxis bedeutet:

```text
VMs planen
VMs erstellen
Betriebssysteme installieren
Ressourcen sinnvoll vergeben
Netzwerkmodi verstehen
Dienste prüfen
Snapshots richtig nutzen
Backups planen
Sicherheit beachten
Fehler systematisch suchen
Dokumentation schreiben
```

Ein FISI fragt nicht nur:

```text
Startet die VM?
```

Sondern auch:

```text
Hat die VM genug Ressourcen?
Ist sie im richtigen Netzwerk?
Ist sie sicher erreichbar?
Sind Backups vorhanden?
Ist alles dokumentiert?
```

---

## Typische Einsatzbereiche

Virtualisierung wird in vielen IT-Bereichen genutzt.

Beispiele:

```text
Servervirtualisierung
Testumgebungen
Schulungslabore
Home-Labs
Entwicklungsumgebungen
Windows- und Linux-Tests
Netzwerklabore
Firewall-Tests
Docker-Umgebungen
Backup- und Restore-Tests
```

In Unternehmen laufen oft viele Dienste nicht mehr auf eigenen physischen Servern, sondern als virtuelle Maschinen auf einem gemeinsamen Host oder Cluster.

---

## Typische FISI-Aufgaben mit VMs

Ein FISI kann in der Praxis zum Beispiel folgende Aufgaben haben:

```text
neue VM erstellen
Ubuntu Server installieren
Windows Server installieren
virtuelle Festplatte vergrößern
RAM oder CPU anpassen
Netzwerkmodus ändern
statische IP konfigurieren
SSH-Zugriff einrichten
Firewall prüfen
Snapshots erstellen
Backups prüfen
Restore testen
Logs analysieren
VM dokumentieren
alte VMs aufräumen
```

Dabei geht es immer um Technik, Sicherheit und Nachvollziehbarkeit.

---

## VM planen

Vor dem Erstellen einer VM sollte klar sein, wofür sie gebraucht wird.

Wichtige Fragen:

```text
Welchen Zweck hat die VM?
Welches Betriebssystem wird benötigt?
Wie viel CPU braucht die VM?
Wie viel RAM braucht die VM?
Wie groß soll die Festplatte sein?
Welcher Netzwerkmodus ist sinnvoll?
Welche Dienste sollen laufen?
Wer braucht Zugriff?
Wie wird die VM gesichert?
Wie wird die VM dokumentiert?
```

Eine schlecht geplante VM verursacht später oft Probleme.

---

## Beispiel für eine VM-Planung

Eine einfache Planung kann so aussehen:

```text
Name: ubuntu-server-lab
Zweck: Linux-Server für SSH- und Docker-Übungen
Betriebssystem: Ubuntu Server
vCPU: 2
RAM: 4 GB
Festplatte: 60 GB
Netzwerk: Bridge
Dienste: SSH, Docker
Backup: manuell nach größeren Änderungen
Sicherheit: UFW aktiv, SSH geschützt
```

So eine Planung hilft, die VM später besser zu verstehen und zu betreiben.

---

## VM sinnvoll benennen

Gute Namen sind wichtig.

Schlecht:

```text
test
vm1
linuxneu
server123
neu-final
```

Besser:

```text
ubuntu-server-lab
win-server-ad-lab
debian-docker-test
pfsense-firewall-lab
client-win11-test
```

Ein guter Name zeigt direkt:

```text
Betriebssystem
Zweck
Umgebung
```

Das ist besonders hilfreich, wenn mehrere VMs vorhanden sind.

---

## Ressourcen vergeben

Eine VM braucht Ressourcen vom Host.

Wichtige Ressourcen:

```text
CPU
RAM
Speicherplatz
Netzwerk
I/O-Leistung
```

Man sollte nicht einfach möglichst viel vergeben.

Problem:

```text
Host hat begrenzte Ressourcen.
Andere VMs brauchen ebenfalls Ressourcen.
Der Host selbst braucht auch CPU und RAM.
```

Besser:

```text
mit sinnvollen Werten starten
Last beobachten
bei Bedarf anpassen
Änderungen dokumentieren
```

---

## CPU und RAM in der Praxis

Typische einfache Richtwerte für ein Lab:

| VM-Typ | vCPU | RAM |
|---|---:|---:|
| kleiner Linux Server | 1-2 | 1-2 GB |
| Ubuntu Server mit Docker | 2 | 4 GB |
| Windows Client | 2 | 4 GB |
| Windows Server | 2-4 | 4-8 GB |
| Datenbank-Testserver | 2-4 | 4 GB |

Das sind nur grobe Richtwerte.

Wichtig ist immer:

```text
Ressourcen prüfen
Last beobachten
nicht den Host überlasten
```

---

## Speicherplatz planen

Virtuelle Festplatten brauchen Speicherplatz auf dem Host.

Häufige Formate:

```text
qcow2
vdi
vmdk
raw
```

Wichtige Fragen:

```text
Wie groß soll die virtuelle Festplatte sein?
Ist sie dynamisch oder fest zugewiesen?
Wo liegt die VM-Datei?
Wird der Speicherplatz überwacht?
Wird die virtuelle Festplatte gesichert?
```

Speicherplatz prüfen:

```bash
df -h
du -sh ~/vmtest
```

Wenn der Host-Speicher voll ist, können VMs abstürzen oder beschädigt werden.

---

## Betriebssystem installieren

Eine VM wird oft mit einer ISO-Datei installiert.

Typischer Ablauf:

```text
ISO herunterladen
VM erstellen
ISO einbinden
VM starten
Betriebssystem installieren
Updates einspielen
Guest Tools installieren
Netzwerk prüfen
Dienste prüfen
ISO wieder entfernen
```

Wichtig:

```text
Nach der Installation sollte die ISO entfernt werden.
```

Sonst startet die VM manchmal wieder ins Installationsmenü.

---

## Guest Tools

Guest Tools verbessern die Zusammenarbeit zwischen Host und VM.

Beispiele:

```text
QEMU Guest Agent
VirtualBox Guest Additions
VMware Tools
Hyper-V Integration Services
```

Sie helfen bei:

```text
Zeitsynchronisation
sauberem Herunterfahren
besserer Verwaltung
Statusinformationen
Dateiaustausch
Maus- und Grafikfunktionen
```

In Serverumgebungen sind Guest Tools besonders nützlich, weil der Hypervisor die VM besser kontrollieren kann.

---

## Netzwerk in der Praxis

Der Netzwerkmodus entscheidet, wie die VM erreichbar ist.

Typische Modi:

| Modus | Bedeutung |
|---|---|
| NAT | VM geht über Host ins Netzwerk/Internet |
| Bridge | VM ist wie eigenes Gerät im LAN |
| Host-only | Kommunikation zwischen Host und VM |
| Internal Network | Kommunikation nur zwischen VMs |

Wichtige Frage:

```text
Wer soll die VM erreichen können?
```

Davon hängt der passende Netzwerkmodus ab.

---

## NAT in der Praxis

NAT ist gut, wenn eine VM einfach Internetzugang braucht.

Typische Nutzung:

```text
Updates herunterladen
Pakete installieren
Tests durchführen
VM nicht direkt im LAN sichtbar machen
```

Vorteil:

```text
einfach und oft schnell funktionsfähig
```

Nachteil:

```text
VM ist von anderen Geräten oft nicht direkt erreichbar
```

Für Dienste wie SSH oder Webserver kann bei NAT eine Portweiterleitung nötig sein.

---

## Bridge in der Praxis

Bridge ist gut, wenn die VM wie ein echter Server im Netzwerk erreichbar sein soll.

Typische Nutzung:

```text
SSH-Zugriff aus dem LAN
Webserver-Test
Windows Server Lab
Active Directory Test
Samba-Freigabe
Monitoring-Test
```

Vorteil:

```text
realistisches Netzwerkverhalten
```

Nachteil:

```text
VM ist sichtbarer im Netzwerk und muss sauber abgesichert werden
```

Eine VM im Bridge-Modus sollte wie ein echter Server behandelt werden.

---

## Host-only in der Praxis

Host-only ist gut für isolierte Tests.

Typische Nutzung:

```text
Host greift per SSH auf VM zu
kleines Labor auf einem Gerät
VM soll nicht im echten LAN sichtbar sein
sichere Testumgebung
```

Manchmal nutzt man zwei Netzwerkkarten:

```text
NAT für Internet
Host-only für Zugriff vom Host
```

Das ist für Lernumgebungen sehr praktisch.

---

## Netzwerk prüfen

Nach der Installation sollte das Netzwerk geprüft werden.

Linux-Befehle:

```bash
ip a
ip route
ping 8.8.8.8
ping github.com
```

Interpretation:

```text
ip a zeigt IP-Adresse und Interface
ip route zeigt Gateway und Routen
ping 8.8.8.8 testet Verbindung per IP
ping github.com testet DNS
```

Wenn `ping 8.8.8.8` funktioniert, aber `ping github.com` nicht, ist es oft ein DNS-Problem.

---

## Dienste prüfen

Wenn eine VM einen Dienst bereitstellt, muss man prüfen, ob der Dienst läuft und erreichbar ist.

Beispiele:

```bash
systemctl status ssh
ss -tulpen
sudo ufw status
journalctl -u ssh
```

Wichtige Fragen:

```text
Läuft der Dienst?
Lauscht der Dienst auf dem richtigen Port?
Ist die Firewall korrekt?
Ist die VM im richtigen Netzwerkmodus?
Ist die IP-Adresse korrekt?
```

Ein Dienst ist erst dann wirklich nutzbar, wenn Dienst, Port, Firewall und Netzwerk zusammenpassen.

---

## Sicherheit in der Praxis

Eine VM ist ein echtes System mit virtueller Hardware.

Sie muss gepflegt und abgesichert werden.

Wichtige Maßnahmen:

```text
Updates installieren
Firewall prüfen
nur notwendige Dienste aktivieren
starke Passwörter oder SSH-Schlüssel nutzen
Adminrechte begrenzen
alte Benutzerkonten entfernen
Logs prüfen
Backups schützen
Netzwerkmodus bewusst wählen
```

Nur weil eine VM im Lab läuft, sollte sie nicht komplett unsicher betrieben werden.

---

## SSH-Zugriff absichern

SSH ist bei Linux-Servern sehr wichtig.

Prüfen:

```bash
systemctl status ssh
journalctl -u ssh
```

Gute Maßnahmen:

```text
starke Passwörter oder SSH-Schlüssel nutzen
Root-Login vermeiden
Firewall-Regeln setzen
nur notwendige Benutzer erlauben
SSH-Logs prüfen
```

SSH ist praktisch, aber auch eine häufige Angriffsfläche.

---

## Firewall prüfen

Eine Firewall begrenzt Zugriffe auf die VM.

Unter Ubuntu kann man zum Beispiel UFW nutzen.

Status prüfen:

```bash
sudo ufw status
```

SSH erlauben:

```bash
sudo ufw allow ssh
```

Firewall aktivieren:

```bash
sudo ufw enable
```

Wichtig:

```text
Nur notwendige Ports öffnen.
Nicht alles freigeben, nur weil es im Lab einfacher ist.
```

---

## Updates und Patchmanagement

VMs müssen regelmäßig aktualisiert werden.

Linux-Beispiel:

```bash
sudo apt update
sudo apt upgrade
```

Aber in der Praxis geht es nicht nur um Befehle.

Ein sauberer Ablauf ist:

```text
Änderung planen
Backup oder Snapshot prüfen
Updates installieren
Dienste testen
Logs prüfen
Änderung dokumentieren
```

Bei wichtigen Systemen sollte man nicht blind Updates durchführen.

---

## Snapshots in der Praxis

Snapshots sind gut für kurze Tests.

Sinnvoll vor:

```text
Updates
Softwareinstallation
Konfigurationsänderungen
Laborübungen
riskanten Tests
```

Gute Arbeitsweise:

```text
Snapshot mit klarem Namen erstellen
Änderung durchführen
System testen
Snapshot bei Erfolg später löschen
Snapshot bei Fehler zurücksetzen
```

Wichtig:

```text
Ein Snapshot ist kein Backup.
```

---

## Backups in der Praxis

Backups sind echte Sicherungen für Wiederherstellung.

Wichtige Fragen:

```text
Was wird gesichert?
Wie oft wird gesichert?
Wo liegt das Backup?
Wer hat Zugriff?
Ist das Backup verschlüsselt?
Wurde Restore getestet?
Wie lange dauert die Wiederherstellung?
```

Ein Backup ohne Restore-Test ist unsicher.

Wichtiger Satz:

```text
Nicht das Backup zählt, sondern der erfolgreiche Restore.
```

---

## Alte VMs aufräumen

Alte Test-VMs sind ein typisches Problem.

Risiken:

```text
veraltete Updates
alte Benutzerkonten
offene Ports
unklare Dienste
Speicherverbrauch
unübersichtliche Umgebung
```

Gute Arbeitsweise:

```text
regelmäßig prüfen, welche VMs noch gebraucht werden
nicht benötigte VMs stoppen oder löschen
wichtige Daten vorher sichern
Dokumentation aktualisieren
```

Alte VMs sollten nicht unkontrolliert weiterlaufen.

---

## Troubleshooting bei VMs

Bei VM-Problemen sollte man systematisch prüfen.

Typische Fragen:

```text
Startet die VM?
Hat der Host genug Ressourcen?
Ist die virtuelle Festplatte vorhanden?
Ist die ISO noch eingebunden?
Hat die VM eine IP-Adresse?
Hat die VM ein Gateway?
Funktioniert DNS?
Läuft der Dienst?
Blockiert die Firewall?
Ist der richtige Netzwerkmodus gewählt?
```

Nicht wild raten, sondern Schritt für Schritt prüfen.

---

## Typische Fehleranalyse

Eine einfache Reihenfolge:

```text
1. VM-Zustand prüfen
2. Ressourcen prüfen
3. Netzwerkmodus prüfen
4. IP-Adresse prüfen
5. Gateway prüfen
6. DNS prüfen
7. Dienst prüfen
8. Port prüfen
9. Firewall prüfen
10. Logs prüfen
```

Diese Reihenfolge hilft bei vielen Problemen.

---

## Wichtige Befehle

### Ressourcen prüfen

```bash
free -h
df -h
top
htop
```

### Netzwerk prüfen

```bash
ip a
ip route
ping 8.8.8.8
ping github.com
```

### Dienste prüfen

```bash
systemctl status ssh
ss -tulpen
journalctl -u ssh
```

### Firewall prüfen

```bash
sudo ufw status
```

### Docker in VM prüfen

```bash
docker ps
docker images
docker volume ls
docker stats
```

---

## Dokumentation einer VM

Jede wichtige VM sollte dokumentiert werden.

Sinnvolle Angaben:

```text
Name der VM
Zweck
Host
Betriebssystem
vCPU
RAM
Festplattengröße
Storage-Ort
Netzwerkmodus
IP-Adresse
Dienste
offene Ports
Firewall-Regeln
Backup-Status
Snapshot-Status
letzte Änderung
besondere Hinweise
```

Dokumentation spart Zeit bei Fehlersuche, Übergabe und Wiederherstellung.

---

## Beispiel 1: Ubuntu Server VM für SSH

Situation:

```text
Eine Ubuntu Server VM soll für Linux-Übungen genutzt werden.
```

Planung:

```text
Name: ubuntu-server-lab
vCPU: 2
RAM: 2 GB
Disk: 40 GB
Network: NAT oder Host-only
Dienste: SSH
```

Prüfen:

```bash
ip a
ip route
systemctl status ssh
sudo ufw status
```

Ziel:

```text
Host kann die VM erreichen.
SSH funktioniert.
VM ist dokumentiert.
```

---

## Beispiel 2: Docker VM

Situation:

```text
Eine VM soll Docker-Übungen ausführen.
```

Planung:

```text
Name: docker-lab
vCPU: 2
RAM: 4 GB
Disk: 60 GB
Network: Bridge oder NAT
Dienste: Docker, SSH
```

Prüfen:

```bash
docker ps
docker images
docker volume ls
df -h
free -h
```

Wichtig:

```text
Docker-Images, Volumes und Logs brauchen Speicherplatz.
```

---

## Beispiel 3: Windows Server Lab

Situation:

```text
Windows Server soll für Active Directory, DNS und DHCP getestet werden.
```

Planung:

```text
Name: win-server-ad-lab
vCPU: 2-4
RAM: 4-8 GB
Disk: 80 GB
Network: Host-only oder Internal Network
```

Warum isoliert?

```text
DHCP-Tests sollen das echte LAN nicht stören.
DNS- und AD-Übungen bleiben im Labor.
```

Bei solchen Tests ist der Netzwerkmodus besonders wichtig.

---

## Beispiel 4: Fehler bei VM-Netzwerk

Situation:

```text
VM hat kein Internet.
```

Prüfung:

```bash
ip a
ip route
ping 8.8.8.8
ping github.com
```

Mögliche Ergebnisse:

```text
keine IP-Adresse -> DHCP oder Netzwerkmodus prüfen
kein Gateway -> Routing prüfen
ping 8.8.8.8 geht nicht -> Verbindung/Gateway prüfen
ping 8.8.8.8 geht, github.com nicht -> DNS prüfen
```

So kann man das Problem eingrenzen.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| VM ohne Planung erstellt | Ressourcen und Netzwerk passen später nicht |
| falscher Netzwerkmodus | VM ist nicht erreichbar oder zu offen |
| zu viel RAM vergeben | Host wird langsam |
| zu wenig Speicherplatz | VM kann instabil werden |
| ISO bleibt eingebunden | VM startet wieder ins Installationsmedium |
| Snapshot als Backup genutzt | falsches Sicherheitsgefühl |
| alte VMs laufen weiter | Sicherheitsrisiko und Ressourcenverbrauch |
| Firewall nicht geprüft | Dienst wirkt nicht erreichbar |
| Backups nicht getestet | Wiederherstellung unsicher |
| keine Dokumentation | Fehlersuche und Übergabe schwer |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Virtualisierung:

```text
Zweck der VM klären
VM sinnvoll benennen
Ressourcen passend vergeben
Netzwerkmodus bewusst wählen
Betriebssystem sauber installieren
Updates einspielen
Guest Tools installieren
Dienste prüfen
Firewall prüfen
Snapshots gezielt nutzen
Backups planen
Restore testen
alte VMs aufräumen
alles dokumentieren
```

Wichtige Regel:

```text
Eine VM ist wie ein echter Server oder Client zu behandeln.
```

Virtuell bedeutet nicht automatisch unwichtig oder sicher.

---

## FISI-Bezug

Virtualisierung ist ein zentraler Bestandteil der FISI-Praxis.

Man braucht dieses Wissen für:

```text
Serverbetrieb
Windows- und Linux-Labore
Testumgebungen
Netzwerkübungen
Docker-Umgebungen
Backup-Konzepte
Troubleshooting
Sicherheitsmaßnahmen
Dokumentation
Projektarbeit
Prüfungsvorbereitung
```

Ein FISI sollte nicht nur eine VM starten können.

Er sollte verstehen:

```text
warum die VM diese Ressourcen braucht
warum dieser Netzwerkmodus gewählt wurde
wie die VM abgesichert wird
wie Backups und Snapshots richtig genutzt werden
wie man Fehler systematisch findet
wie man die VM sauber dokumentiert
```

---

## Kurze Zusammenfassung

Virtualisierung in der FISI-Praxis bedeutet, virtuelle Maschinen sauber zu planen, zu betreiben, zu vernetzen, zu sichern und zu dokumentieren.

Wichtige Themen sind Ressourcenplanung, Betriebssysteminstallation, Netzwerkmodi, SSH, Firewall, Updates, Snapshots, Backups, Restore-Tests, Troubleshooting und Dokumentation.

Eine VM ist kein Spielzeug, sondern ein echtes System mit virtueller Hardware.

Für FISI ist Virtualisierung besonders wichtig, weil viele moderne IT-Umgebungen auf virtuellen Servern, Testsystemen und Laboren basieren.