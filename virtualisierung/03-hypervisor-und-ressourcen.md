# 3. Hypervisor und Ressourcen

In diesem Kapitel geht es um Hypervisoren und Ressourcenplanung.

Ein Hypervisor ist die Software, die virtuelle Maschinen bereitstellt und verwaltet. Er sorgt dafür, dass mehrere virtuelle Maschinen auf einem physischen Host laufen können und dabei CPU, RAM, Speicher und Netzwerkressourcen nutzen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil virtuelle Maschinen nicht einfach „irgendwie“ erstellt werden sollten. CPU, RAM, Speicherplatz und Netzwerk müssen bewusst geplant werden, sonst werden Systeme langsam, instabil oder schwer zu verwalten.

---

## Kurz erklärt

Ein Hypervisor verwaltet virtuelle Maschinen.

Er verteilt Ressourcen wie:

```text
CPU
RAM
Storage
Netzwerk
virtuelle Geräte
```

Beispiel:

```text
Physischer Host
├── Hypervisor
│   ├── VM 1: Ubuntu Server, 2 vCPU, 4 GB RAM
│   ├── VM 2: Windows Server, 4 vCPU, 8 GB RAM
│   └── VM 3: Test-Client, 2 vCPU, 4 GB RAM
```

Der Host hat echte Hardware.  
Die VMs bekommen virtuelle Hardware.

---

## Aufgabe eines Hypervisors

Der Hypervisor ist die Schicht zwischen Hardware und virtuellen Maschinen.

Er sorgt dafür, dass jede VM so arbeiten kann, als hätte sie eigene Hardware.

Aufgaben eines Hypervisors:

```text
VMs erstellen
VMs starten und stoppen
CPU-Zeit verteilen
RAM zuweisen
virtuelle Festplatten verwalten
virtuelle Netzwerkkarten bereitstellen
Snapshots ermöglichen
VM-Zustände verwalten
Ressourcen überwachen
```

Ohne Hypervisor könnten mehrere VMs nicht sauber auf derselben Hardware laufen.

---

## Typ-1-Hypervisor

Ein Typ-1-Hypervisor läuft direkt auf der Hardware.

Er wird auch Bare-Metal-Hypervisor genannt.

Aufbau:

```text
Hardware
└── Hypervisor
    ├── VM 1
    ├── VM 2
    └── VM 3
```

Beispiele:

```text
VMware ESXi
Microsoft Hyper-V Server
Proxmox VE
Xen
KVM in Serverumgebungen
```

Typ-1-Hypervisoren werden oft in professionellen Serverumgebungen genutzt.

Vorteile:

```text
gute Performance
direkter Zugriff auf Hardware
geeignet für Dauerbetrieb
zentrale Verwaltung möglich
professioneller Serverbetrieb
```

---

## Typ-2-Hypervisor

Ein Typ-2-Hypervisor läuft auf einem normalen Betriebssystem.

Aufbau:

```text
Hardware
└── Host-Betriebssystem
    └── Hypervisor
        ├── VM 1
        └── VM 2
```

Beispiele:

```text
VirtualBox
VMware Workstation
Parallels
UTM
```

Typ-2-Hypervisoren sind besonders praktisch für:

```text
Lernen
Tests
Schulung
lokales Home-Lab
Desktop-Virtualisierung
einfache VM-Experimente
```

Sie sind oft einfacher für Einsteiger, weil man sie auf dem normalen Laptop oder PC installieren kann.

---

## Typ 1 und Typ 2 im Vergleich

| Bereich | Typ 1 | Typ 2 |
|---|---|---|
| läuft auf | direkt auf Hardware | auf einem Betriebssystem |
| typische Nutzung | Server, Rechenzentrum, produktive Umgebung | Lernen, Tests, Desktop |
| Beispiele | ESXi, Proxmox, Hyper-V Server | VirtualBox, VMware Workstation |
| Performance | meist besser | abhängig vom Host-System |
| Verwaltung | professioneller | einfacher lokal nutzbar |
| FISI-Bezug | Servervirtualisierung | Labor und Übungen |

Für FISI sind beide wichtig.

Typ 2 ist gut zum Lernen.  
Typ 1 ist wichtig für echte Serverumgebungen.

---

## KVM und QEMU kurz erklärt

KVM und QEMU werden oft zusammen genutzt.

KVM bedeutet:

```text
Kernel-based Virtual Machine
```

KVM ist Teil des Linux-Kernels und ermöglicht hardwareunterstützte Virtualisierung.

QEMU ist ein Emulator und Virtualisierungswerkzeug.

Zusammen ermöglichen sie leistungsfähige virtuelle Maschinen unter Linux.

Vereinfacht:

```text
KVM = Virtualisierungsfunktion im Linux-Kernel
QEMU = Werkzeug zum Erstellen und Starten von VMs
```

Viele Linux-basierte Virtualisierungslösungen nutzen KVM/QEMU als technische Grundlage.

---

## Proxmox VE kurz erklärt

Proxmox VE ist eine Virtualisierungsplattform.

Sie nutzt unter anderem KVM/QEMU für virtuelle Maschinen und LXC für Container.

Typische Eigenschaften:

```text
Weboberfläche
VM-Verwaltung
Container-Verwaltung
Storage-Verwaltung
Netzwerkverwaltung
Snapshots
Backups
Cluster-Funktionen
```

Proxmox ist beliebt für Home-Labs und auch für kleinere Serverumgebungen.

Für FISI ist Proxmox interessant, weil man damit viele Themen praktisch üben kann:

```text
VMs
Linux
Netzwerke
Backups
Storage
Cluster-Grundlagen
Serverbetrieb
```

---

## Ressourcen einer VM

Eine VM braucht Ressourcen vom Host.

Wichtige Ressourcen:

```text
CPU
RAM
Storage
Netzwerk
I/O-Leistung
```

Wenn Ressourcen falsch geplant werden, kann das ganze System langsam oder instabil werden.

Beispiel:

```text
Host hat 16 GB RAM.
VM 1 bekommt 8 GB.
VM 2 bekommt 8 GB.
Host selbst braucht aber auch RAM.
```

Dann bleibt zu wenig Arbeitsspeicher für den Host.

---

## CPU-Ressourcen

Eine VM bekommt virtuelle CPUs.

Diese heißen oft:

```text
vCPU
```

Beispiel:

```text
Ubuntu Server VM: 2 vCPU
Windows Server VM: 4 vCPU
Test-Client VM: 2 vCPU
```

Die vCPUs werden vom Hypervisor auf die echten CPU-Kerne des Hosts verteilt.

Wichtig:

```text
Mehr vCPU bedeutet nicht automatisch mehr Leistung.
```

Wenn zu viele VMs gleichzeitig viel CPU-Leistung brauchen, entsteht Konkurrenz um die echte CPU.

---

## CPU-Overcommitment

Overcommitment bedeutet:

```text
Es werden mehr virtuelle Ressourcen vergeben, als physisch vorhanden sind.
```

Beispiel:

```text
Host hat 8 echte CPU-Threads.
VM 1 bekommt 4 vCPU.
VM 2 bekommt 4 vCPU.
VM 3 bekommt 4 vCPU.
VM 4 bekommt 4 vCPU.
```

Zusammen sind das 16 vCPU auf 8 echten Threads.

Das kann funktionieren, wenn nicht alle VMs gleichzeitig viel CPU brauchen.

Es wird problematisch, wenn viele VMs gleichzeitig hohe Last haben.

---

## CPU-Planung

Bei CPU-Planung sollte man fragen:

```text
Welche Aufgabe hat die VM?
Ist es ein Testsystem oder produktives System?
Wie viele Benutzer greifen zu?
Laufen CPU-intensive Dienste?
Wie viele andere VMs laufen auf dem Host?
Wie viel CPU braucht der Host selbst?
```

Typische einfache Planung im Lab:

| VM-Typ | Mögliche vCPU |
|---|---:|
| kleiner Linux Server | 1-2 |
| Docker-Testserver | 2 |
| Windows Client | 2 |
| Windows Server | 2-4 |
| Datenbank-Testsystem | 2-4 |

Das sind nur Richtwerte. Die echte Last muss beobachtet werden.

---

## RAM-Ressourcen

RAM ist oft die kritischste Ressource bei Virtualisierung.

Jede VM bekommt einen bestimmten Arbeitsspeicher.

Beispiel:

```text
Host: 16 GB RAM
Host-System: braucht selbst RAM
Ubuntu Server VM: 4 GB
Windows Server VM: 6 GB
Test-Client VM: 4 GB
```

Wenn zu viel RAM vergeben wird, wird der Host langsam.

Im schlimmsten Fall beginnt der Host zu swappen.

---

## Swap

Swap ist Speicher auf der Festplatte, der genutzt wird, wenn RAM knapp wird.

Problem:

```text
RAM ist schnell.
Festplatte/SSD ist deutlich langsamer.
```

Wenn ein Host stark swappen muss, werden VMs langsam.

Typische Anzeichen:

```text
System reagiert träge
VMs starten langsam
hohe Festplattenaktivität
hohe Load
Programme frieren kurz ein
```

Deshalb sollte RAM bewusst geplant werden.

---

## RAM-Planung

Gute Fragen für RAM-Planung:

```text
Wie viel RAM hat der Host?
Wie viel braucht das Host-System?
Welche VMs laufen gleichzeitig?
Welche Dienste laufen in den VMs?
Brauchen manche VMs nur zeitweise RAM?
Gibt es genug Reserve?
```

Einfache Lab-Richtwerte:

| VM-Typ | Möglicher RAM |
|---|---:|
| kleiner Ubuntu Server | 1-2 GB |
| Ubuntu Server mit Docker | 2-4 GB |
| Windows Client | 4 GB |
| Windows Server | 4-8 GB |
| Datenbank-Testsystem | 2-4 GB |

Wichtig:

```text
Nicht den kompletten RAM des Hosts an VMs vergeben.
```

---

## Storage

Storage ist der Speicher, auf dem virtuelle Festplatten liegen.

Virtuelle Festplatten können zum Beispiel diese Formate haben:

```text
qcow2
vdi
vmdk
raw
```

Auf der virtuellen Festplatte liegen:

```text
Betriebssystem
Programme
Dienste
Konfigurationsdateien
Benutzerdaten
Logs
Datenbanken
```

Wenn der Storage voll oder langsam ist, betrifft das direkt die VMs.

---

## Dynamischer Speicher

Dynamische virtuelle Festplatten wachsen bei Bedarf.

Beispiel:

```text
VM bekommt 60 GB virtuelle Festplatte.
Die Datei auf dem Host ist am Anfang nur 10 GB groß.
Wenn in der VM mehr Daten gespeichert werden, wächst die Datei.
```

Vorteil:

```text
spart Speicherplatz am Anfang
```

Nachteil:

```text
Host-Speicher kann unerwartet voll werden
```

Deshalb muss man freien Speicher auf dem Host überwachen.

---

## Fest zugewiesener Speicher

Bei fest zugewiesenem Speicher wird der Platz direkt reserviert.

Beispiel:

```text
VM bekommt 60 GB.
Host reserviert direkt 60 GB.
```

Vorteil:

```text
Speicherverbrauch ist planbarer
```

Nachteil:

```text
braucht direkt mehr Platz
```

Für produktive Systeme ist Planbarkeit oft wichtiger.

Für Lernumgebungen ist dynamischer Speicher meistens praktischer.

---

## Storage-Performance

Nicht nur die Größe ist wichtig, sondern auch die Geschwindigkeit.

Wichtig sind:

```text
Lesegeschwindigkeit
Schreibgeschwindigkeit
IOPS
Latenz
SSD oder HDD
Storage-Auslastung
```

VMs mit Datenbanken oder vielen Logs brauchen mehr I/O-Leistung als einfache Testsysteme.

Wenn mehrere VMs gleichzeitig viel schreiben, kann Storage zum Engpass werden.

---

## Speicherplatz überwachen

Unter Linux kann man Speicherplatz prüfen mit:

```bash
df -h
```

Größe von Ordnern prüfen:

```bash
du -sh ordnername
```

Beispiel:

```bash
du -sh ~/vmtest
```

Das zeigt, wie viel Speicher der VM-Ordner belegt.

Wichtig:

```text
Wenn der Host-Speicher voll ist, können VMs abstürzen oder beschädigt werden.
```

---

## Netzwerkressourcen

VMs brauchen virtuelle Netzwerkkarten.

Der Hypervisor verbindet diese virtuellen Netzwerkkarten mit dem Host-Netzwerk.

Typische Modi:

```text
NAT
Bridge
Host-only
Internal Network
```

Der Netzwerkmodus beeinflusst:

```text
ob die VM Internet hat
ob die VM vom Host erreichbar ist
ob andere Geräte die VM erreichen
ob die VM im gleichen Netz wie der Host ist
wie sicher oder isoliert die VM ist
```

---

## Bridge und virtuelle Switches

Bei vielen Virtualisierungslösungen gibt es virtuelle Switches oder Bridges.

Vereinfacht:

```text
VM-Netzwerkkarte -> virtuelle Bridge -> echte Netzwerkkarte
```

Bei Bridge-Netzwerken kann die VM wie ein eigenes Gerät im LAN erscheinen.

Beispiel:

```text
Host: 192.168.1.20
VM:   192.168.1.50
```

Die VM bekommt dann oft eine IP-Adresse vom gleichen DHCP-Server wie echte Geräte.

---

## NAT-Netzwerk

Bei NAT nutzt die VM den Host als Übergang.

Vereinfacht:

```text
VM -> NAT -> Host -> Internet
```

Vorteile:

```text
einfacher Internetzugang
VM ist nicht direkt im LAN sichtbar
gut für Tests
```

Nachteile:

```text
andere Geräte erreichen die VM oft nicht direkt
Portweiterleitung kann nötig sein
```

NAT ist gut für Lernsysteme, die hauptsächlich Internetzugang brauchen.

---

## Host-only-Netzwerk

Host-only bedeutet:

```text
Host und VM können miteinander kommunizieren.
Andere Geräte im LAN meistens nicht.
```

Das ist gut für isolierte Labore.

Beispiel:

```text
Host testet SSH zur VM.
VM ist nicht im normalen Netzwerk sichtbar.
```

Host-only ist sinnvoll, wenn man bewusst isoliert testen möchte.

---

## Ressourcen überwachen

Ressourcen müssen beobachtet werden.

Unter Linux:

```bash
free -h
df -h
top
htop
```

CPU und RAM:

```bash
top
htop
free -h
```

Speicherplatz:

```bash
df -h
du -sh ordnername
```

Netzwerk:

```bash
ip a
ip route
ss -tulpen
```

Bei Docker zusätzlich:

```bash
docker stats
```

Bei VMs hängt die Überwachung auch vom Hypervisor ab.

---

## Typische Ressourcenprobleme

| Problem | Mögliche Ursache |
|---|---|
| VM läuft langsam | zu wenig RAM, zu wenig CPU, langsamer Storage |
| Host läuft langsam | zu viele VMs, zu viel RAM vergeben |
| VM startet nicht | zu wenig Speicherplatz, falsche Konfiguration |
| Netzwerk geht nicht | falscher Netzwerkmodus |
| VM friert ein | RAM knapp, Storage überlastet |
| Datenbank langsam | zu wenig RAM oder langsamer Storage |
| Host-Speicher voll | dynamische VM-Festplatten gewachsen |
| hohe CPU-Last | zu viele aktive VMs oder falsche vCPU-Planung |

---

## Ressourcen nicht blind vergeben

Ein häufiger Fehler ist:

```text
VM bekommt einfach sehr viel CPU und RAM.
```

Das klingt gut, ist aber nicht immer sinnvoll.

Problem:

```text
Andere VMs und der Host brauchen auch Ressourcen.
```

Besser:

```text
mit sinnvollen Werten starten
Last beobachten
bei Bedarf anpassen
Änderungen dokumentieren
```

Virtualisierung bedeutet Teilen von Ressourcen.  
Deshalb muss man fair und sinnvoll planen.

---

## Beispiel: Host mit 16 GB RAM

Ein Laptop oder kleiner Host hat:

```text
16 GB RAM
```

Mögliche Laborplanung:

| System | RAM |
|---|---:|
| Host-System | 4 GB Reserve |
| Ubuntu Server VM | 2 GB |
| Docker VM | 4 GB |
| Windows Client VM | 4 GB |
| Reserve | 2 GB |

Das ist nur ein Beispiel.

Wichtig ist:

```text
Nicht alle VMs müssen immer gleichzeitig laufen.
Reserve einplanen.
Host darf nicht dauerhaft am Limit sein.
```

---

## Beispiel: Kleine Server-VM

Eine kleine Ubuntu-Server-VM könnte so geplant werden:

```text
Name: ubuntu-server-lab
vCPU: 2
RAM: 2 GB
Disk: 40 GB
Network: NAT oder Bridge
Dienste: SSH
```

Nach Installation prüfen:

```bash
free -h
df -h
ip a
ip route
systemctl status ssh
```

So sieht man, ob die VM grundsätzlich sauber läuft.

---

## Beispiel: Docker-Test-VM

Eine VM für Docker-Tests könnte so aussehen:

```text
Name: docker-lab
vCPU: 2
RAM: 4 GB
Disk: 60 GB
Network: Bridge
Dienste: Docker, SSH
```

Warum mehr Speicher?

```text
Docker-Images brauchen Platz.
Container-Volumes brauchen Platz.
Logs können wachsen.
```

Prüfen:

```bash
docker images
docker ps
docker volume ls
df -h
free -h
```

---

## Beispiel: Windows Server VM

Eine Windows Server VM braucht meistens mehr Ressourcen als ein kleiner Linux Server.

Beispiel:

```text
Name: win-server-lab
vCPU: 2-4
RAM: 4-8 GB
Disk: 80 GB
Network: Bridge oder Host-only
```

Nutzung:

```text
Active Directory testen
DNS/DHCP üben
Windows-Clients anbinden
Gruppenrichtlinien kennenlernen
```

Windows-Systeme brauchen oft mehr RAM und Speicherplatz als minimale Linux-Server.

---

## Ressourcen und Sicherheit

Ressourcenplanung hat auch mit Sicherheit zu tun.

Beispiele:

```text
Wenn Logs wegen vollem Speicher nicht geschrieben werden, fehlt Nachvollziehbarkeit.
Wenn ein Server wegen Ressourcenmangel ausfällt, ist Verfügbarkeit betroffen.
Wenn alte VMs weiterlaufen, bleiben Sicherheitslücken aktiv.
Wenn Backups wegen Platzmangel fehlschlagen, ist Wiederherstellung gefährdet.
```

Sicherheit bedeutet also nicht nur Firewall und Passwort.

Auch stabile Ressourcenplanung gehört dazu.

---

## Ressourcen und Dokumentation

VM-Ressourcen sollten dokumentiert werden.

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
Backup-Status
Snapshot-Status
```

Beispiel:

```text
Name: docker-lab
Zweck: Docker-Übungen
Host: ThinkPad
OS: Ubuntu Server
vCPU: 2
RAM: 4 GB
Disk: 60 GB qcow2
Network: Bridge
Dienste: SSH, Docker
Backup: manuell nach größeren Änderungen
```

Dokumentation hilft bei Fehlersuche und späterer Erweiterung.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| zu viele vCPUs vergeben | Host wird überlastet |
| zu viel RAM vergeben | Host beginnt zu swappen |
| kein RAM für Host übrig | gesamtes System wird langsam |
| Storage nicht überwacht | VM-Dateien füllen die Festplatte |
| dynamische Disks unterschätzt | Speicher wächst unerwartet |
| Netzwerkmodus falsch gewählt | VM ist nicht erreichbar |
| alte VMs laufen dauerhaft | Ressourcenverbrauch und Sicherheitsrisiko |
| keine Guest Tools installiert | schlechtere Verwaltung |
| keine Dokumentation | unklare Ressourcen und Zuständigkeiten |
| Snapshot als Backup genutzt | falsches Sicherheitsgefühl |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Hypervisoren und Ressourcen:

```text
Host-Ressourcen zuerst prüfen
VM-Zweck festlegen
CPU bewusst vergeben
RAM bewusst vergeben
Speicherplatz mit Reserve planen
Netzwerkmodus passend wählen
Ressourcen nach Installation prüfen
Last beobachten
Änderungen dokumentieren
alte VMs entfernen oder stoppen
```

Wichtige Regel:

```text
Ressourcen sind begrenzt.
Virtualisierung verteilt sie nur besser.
```

---

## Praktische Befehle

### RAM prüfen

```bash
free -h
```

### Speicherplatz prüfen

```bash
df -h
```

### Ordnergröße prüfen

```bash
du -sh ~/vmtest
```

### CPU und Prozesse prüfen

```bash
top
htop
```

### Netzwerk prüfen

```bash
ip a
ip route
```

### Dienste prüfen

```bash
systemctl status ssh
```

---

## FISI-Bezug

Hypervisoren und Ressourcenplanung sind wichtige FISI-Themen.

Man braucht dieses Wissen für:

```text
VMs erstellen
Server virtualisieren
Host-Systeme planen
Ressourcen sinnvoll verteilen
Performanceprobleme erkennen
Storage-Probleme vermeiden
Netzwerkmodi verstehen
Backups planen
Home-Lab betreiben
Dokumentation schreiben
```

Ein FISI sollte nicht nur wissen, wie man eine VM erstellt.

Er sollte auch verstehen, warum eine VM bestimmte Ressourcen bekommt und welche Folgen falsche Planung haben kann.

---

## Kurze Zusammenfassung

Ein Hypervisor stellt virtuelle Maschinen bereit und verwaltet ihre Ressourcen.

Typ-1-Hypervisoren laufen direkt auf Hardware und werden oft in Serverumgebungen genutzt. Typ-2-Hypervisoren laufen auf einem normalen Betriebssystem und sind gut für Lernen und Tests.

Wichtige Ressourcen sind CPU, RAM, Storage und Netzwerk.

Diese Ressourcen müssen bewusst geplant, überwacht und dokumentiert werden.

Für FISI ist dieses Thema wichtig, weil viele Server, Testsysteme und Home-Labs auf Virtualisierung basieren und nur stabil funktionieren, wenn Ressourcen sinnvoll verteilt werden.