# 1. Virtualisierung Grundlagen

In diesem Kapitel geht es um die Grundlagen der Virtualisierung.

Virtualisierung bedeutet, dass IT-Ressourcen wie Computer, Server, Festplatten, Netzwerkkarten oder ganze Betriebssysteme logisch nachgebildet werden. Dadurch kann ein physischer Computer mehrere virtuelle Systeme betreiben.

Für Fachinformatiker für Systemintegration ist Virtualisierung sehr wichtig, weil viele Server, Testumgebungen und Labore heute nicht mehr direkt auf einzelner Hardware laufen, sondern als virtuelle Maschinen.

---

## Kurz erklärt

Virtualisierung macht aus einem physischen Computer mehrere virtuelle Computer.

Beispiel:

```text
Physischer Host
├── VM 1: Ubuntu Server
├── VM 2: Windows Server
├── VM 3: Test-Client
└── VM 4: Datenbankserver
```

Jede VM verhält sich wie ein eigener Computer.

Sie hat eigene:

```text
CPU-Ressourcen
Arbeitsspeicher
virtuelle Festplatte
virtuelle Netzwerkkarte
Betriebssystem
Dienste
Benutzer
Konfiguration
```

Die Hardware ist aber nicht wirklich mehrfach vorhanden. Sie wird vom Host bereitgestellt und vom Hypervisor verwaltet.

---

## Warum Virtualisierung genutzt wird

Ohne Virtualisierung braucht man für viele Aufgaben eigene physische Geräte.

Beispiel:

```text
ein Server für Web
ein Server für Datenbank
ein Server für Dateiablage
ein Server für Tests
ein Server für Monitoring
```

Das wäre teuer, unflexibel und oft nicht effizient.

Mit Virtualisierung können mehrere Systeme auf einem Host laufen.

Beispiel:

```text
Ein physischer Server betreibt mehrere virtuelle Server.
```

Dadurch kann Hardware besser genutzt werden.

---

## Wichtige Vorteile

Virtualisierung hat viele Vorteile.

| Vorteil | Erklärung |
|---|---|
| bessere Ressourcennutzung | mehrere VMs teilen sich einen Host |
| Flexibilität | neue Systeme können schnell erstellt werden |
| Testumgebungen | Änderungen können gefahrlos ausprobiert werden |
| Isolation | Fehler in einer VM betreffen nicht automatisch alle VMs |
| Snapshots | Zustand vor Änderungen kann gespeichert werden |
| Migration | VMs können oft leichter verschoben werden |
| Home-Lab | realistische IT-Umgebung auf wenig Hardware |

Besonders für Lernen und FISI-Praxis ist Virtualisierung sehr nützlich.

Man kann Server installieren, Netzwerke testen, Fehler machen und Systeme neu aufbauen, ohne direkt echte Produktivsysteme zu gefährden.

---

## Wichtige Nachteile

Virtualisierung hat auch Nachteile.

| Nachteil | Erklärung |
|---|---|
| Ressourcenverbrauch | jede VM braucht CPU, RAM und Speicher |
| Komplexität | Netzwerk, Storage und Rechte müssen geplant werden |
| Host-Abhängigkeit | fällt der Host aus, sind mehrere VMs betroffen |
| Performance | falsche Planung kann Systeme langsam machen |
| Backup-Aufwand | VMs müssen richtig gesichert werden |
| Sicherheitsrisiko | unsichere VMs können andere Systeme gefährden |

Virtualisierung macht IT flexibler, aber nicht automatisch einfacher.

Man muss trotzdem sauber planen, dokumentieren und absichern.

---

## Host und Gast

Ein wichtiger Unterschied ist:

```text
Host = physischer Computer
Gast = virtuelle Maschine
```

Der Host ist das echte Gerät.

Beispiele für Hosts:

```text
Laptop mit Ubuntu
Windows-PC
Server im Rechenzentrum
Proxmox-Host
VMware-Host
```

Der Gast ist die VM auf diesem Host.

Beispiele für Gäste:

```text
Ubuntu Server VM
Windows Server VM
Debian VM
Test-Client VM
Firewall VM
```

Vereinfacht:

```text
Der Host stellt die Ressourcen bereit.
Der Gast nutzt diese Ressourcen als virtuelle Hardware.
```

---

## Hypervisor

Ein Hypervisor ist die Software, die Virtualisierung ermöglicht.

Er verwaltet die virtuellen Maschinen und verteilt die Ressourcen des Hosts.

Der Hypervisor entscheidet zum Beispiel:

```text
Welche VM bekommt wie viel CPU-Zeit?
Welche VM bekommt wie viel RAM?
Welche virtuelle Festplatte gehört zu welcher VM?
Welche Netzwerkkarte nutzt die VM?
```

Beispiele für Hypervisoren und Virtualisierungsplattformen:

```text
KVM/QEMU
VirtualBox
VMware Workstation
VMware ESXi
Microsoft Hyper-V
Proxmox VE
```

Ohne Hypervisor könnten mehrere VMs nicht sauber auf derselben Hardware laufen.

---

## Typ-1-Hypervisor

Ein Typ-1-Hypervisor läuft direkt auf der Hardware.

Er braucht kein normales Desktop-Betriebssystem darunter.

Beispiele:

```text
VMware ESXi
Microsoft Hyper-V Server
Proxmox VE
Xen
```

Typ-1-Hypervisoren werden häufig in professionellen Serverumgebungen genutzt.

Vereinfacht:

```text
Hardware
└── Hypervisor
    ├── VM 1
    ├── VM 2
    └── VM 3
```

Vorteile:

```text
gute Performance
stabil für Serverbetrieb
professionelle Verwaltung
geeignet für Rechenzentren und Firmen
```

---

## Typ-2-Hypervisor

Ein Typ-2-Hypervisor läuft auf einem normalen Betriebssystem.

Beispiele:

```text
VirtualBox
VMware Workstation
UTM
Parallels
```

Vereinfacht:

```text
Hardware
└── Betriebssystem
    └── Hypervisor
        ├── VM 1
        └── VM 2
```

Typ-2-Hypervisoren sind gut für:

```text
Lernen
Tests
Desktop-Labore
kleine lokale Umgebungen
Schulung
```

Sie sind sehr praktisch, wenn man auf einem normalen Laptop oder PC virtuelle Maschinen ausprobieren möchte.

---

## Typ 1 vs Typ 2

| Bereich | Typ 1 | Typ 2 |
|---|---|---|
| läuft auf | direkt auf Hardware | auf Betriebssystem |
| Nutzung | Serverumgebung | Desktop/Test/Lernen |
| Beispiele | ESXi, Proxmox, Hyper-V | VirtualBox, VMware Workstation |
| Performance | meist besser | abhängig vom Host-OS |
| Verwaltung | professioneller | einfacher für Einsteiger |
| FISI-Bezug | produktive Infrastruktur | Labor und Lernen |

Für den Einstieg ist Typ 2 oft einfacher.

Für echte Serverumgebungen ist Typ 1 sehr wichtig.

---

## Virtuelle Hardware

Eine VM bekommt virtuelle Hardware.

Beispiele:

```text
vCPU
virtueller RAM
virtuelle Festplatte
virtuelle Netzwerkkarte
virtuelles CD/DVD-Laufwerk
virtuelle Grafikkarte
```

Das Gast-Betriebssystem erkennt diese Komponenten wie echte Hardware.

Beispiel:

```text
Ubuntu Server läuft in einer VM.
Ubuntu sieht eine Festplatte, eine Netzwerkkarte und CPU-Kerne.
```

Aber diese Hardware wird vom Hypervisor bereitgestellt.

---

## vCPU

vCPU bedeutet:

```text
virtuelle CPU
```

Eine VM bekommt eine bestimmte Anzahl virtueller CPU-Kerne.

Beispiel:

```text
VM 1: 2 vCPUs
VM 2: 4 vCPUs
VM 3: 1 vCPU
```

Wichtig:

```text
Mehr vCPU bedeutet nicht automatisch besser.
```

Wenn zu viele VMs zu viele CPU-Ressourcen bekommen, kann der Host überlastet werden.

Man muss prüfen, was die VM wirklich braucht.

---

## RAM

Jede VM braucht Arbeitsspeicher.

Beispiel:

```text
Host hat 16 GB RAM.
Host-Betriebssystem braucht selbst RAM.
VM 1 bekommt 4 GB.
VM 2 bekommt 4 GB.
VM 3 bekommt 2 GB.
```

Wenn zu viel RAM an VMs vergeben wird, bleibt zu wenig für den Host.

Dann kann das ganze System langsam werden.

Wichtige Regel:

```text
RAM bewusst planen und nicht blind zu viel vergeben.
```

---

## Virtuelle Festplatte

Eine VM nutzt eine virtuelle Festplatte.

Diese liegt oft als Datei auf dem Host.

Beispiele für Formate:

```text
qcow2
vdi
vmdk
raw
```

Die VM sieht diese Datei wie eine echte Festplatte.

Auf dieser virtuellen Festplatte liegen:

```text
Betriebssystem
Programme
Konfiguration
Daten
Logs
```

Wichtig:

```text
Virtuelle Festplatten müssen gesichert werden.
```

Wenn die Datei beschädigt oder gelöscht wird, kann die VM nicht mehr richtig funktionieren.

---

## Dynamische und feste Festplatten

Virtuelle Festplatten können unterschiedlich angelegt werden.

| Art | Bedeutung |
|---|---|
| dynamisch | Datei wächst nur bei Bedarf |
| fest zugewiesen | Speicher wird direkt reserviert |

Dynamisch ist platzsparend.

Feste Zuweisung kann planbarer sein.

Beispiel:

```text
VM bekommt 40 GB virtuelle Festplatte.
Tatsächlich nutzt sie am Anfang nur 8 GB auf dem Host.
```

Bei dynamischen Festplatten muss man trotzdem genug freien Speicher auf dem Host behalten.

---

## ISO-Datei

Eine ISO-Datei ist ein Installationsabbild.

Beispiele:

```text
Ubuntu Server ISO
Windows Server ISO
Debian ISO
Rescue-System ISO
```

Eine VM kann von einer ISO starten, als wäre es eine DVD oder ein USB-Stick.

Typischer Ablauf:

```text
ISO herunterladen
neue VM erstellen
ISO einbinden
VM starten
Betriebssystem installieren
ISO später entfernen
```

---

## Netzwerk in VMs

Eine VM braucht meistens eine virtuelle Netzwerkkarte.

Darüber bekommt sie Netzwerkzugriff.

Typische Modi:

```text
NAT
Bridge
Host-only
Internal Network
```

Der Netzwerkmodus bestimmt, wie die VM erreichbar ist.

Beispiel:

```text
NAT = VM kommt meist einfach ins Internet
Bridge = VM ist wie ein eigenes Gerät im LAN
Host-only = Host und VM sprechen miteinander, aber isolierter
```

Netzwerkmodi sind einer der wichtigsten Punkte in der FISI-Praxis.

---

## NAT kurz erklärt

Bei NAT nutzt die VM den Host als Übergang.

Vereinfacht:

```text
VM -> Host -> Netzwerk/Internet
```

Vorteile:

```text
einfacher Internetzugang
gut für Tests
VM ist nicht direkt wie ein eigenes Gerät im LAN sichtbar
```

Nachteile:

```text
andere Geräte erreichen die VM oft nicht direkt
Portweiterleitung kann nötig sein
Netzwerkverhalten ist manchmal weniger sichtbar
```

---

## Bridge kurz erklärt

Bei Bridge ist die VM wie ein eigenes Gerät im lokalen Netzwerk.

Vereinfacht:

```text
VM -> LAN
```

Die VM bekommt oft eine eigene IP-Adresse vom gleichen DHCP wie andere Geräte im Netzwerk.

Vorteile:

```text
VM ist von anderen Geräten leichter erreichbar
gut für Serverdienste im Labor
realistisches Netzwerkverhalten
```

Nachteile:

```text
VM ist sichtbarer im Netzwerk
Firewall und Sicherheit werden wichtiger
nicht jedes WLAN unterstützt Bridge problemlos
```

---

## Host-only kurz erklärt

Host-only bedeutet:

```text
Host und VM können miteinander kommunizieren.
Andere Geräte im Netzwerk meistens nicht.
```

Das ist gut für isolierte Tests.

Beispiel:

```text
Host verbindet sich per SSH zur Ubuntu-Server-VM.
Die VM ist nicht im normalen LAN sichtbar.
```

Host-only ist praktisch, wenn man eine sichere kleine Testumgebung bauen möchte.

---

## Snapshot

Ein Snapshot speichert den Zustand einer VM zu einem bestimmten Zeitpunkt.

Beispiele:

```text
Snapshot vor Update
Snapshot vor Softwareinstallation
Snapshot vor gefährlicher Konfiguration
Snapshot vor Test
```

Wenn etwas schiefgeht, kann man auf diesen Zustand zurückgehen.

Wichtig:

```text
Snapshot ist kein vollständiges Backup.
```

Ein Snapshot liegt meistens auf demselben Host. Wenn der Host oder Storage kaputtgeht, kann auch der Snapshot verloren sein.

---

## Backup

Ein Backup ist eine echte Sicherung von Daten oder Systemen.

Bei VMs kann man sichern:

```text
ganze VM
virtuelle Festplatte
Konfigurationsdateien
Daten innerhalb der VM
Datenbank innerhalb der VM
wichtige Dienste
```

Wichtig:

```text
Backup muss wiederherstellbar sein.
Restore muss getestet werden.
```

Ein Snapshot ist gut für kurze Tests.

Ein Backup ist wichtig für echte Wiederherstellung.

---

## VM vs Container

Virtuelle Maschinen und Container werden oft verwechselt.

| Bereich | VM | Container |
|---|---|---|
| Betriebssystem | eigenes Gast-System | teilt Kernel mit Host |
| Isolation | stärker | leichter |
| Startzeit | langsamer | schneller |
| Ressourcen | mehr Verbrauch | weniger Verbrauch |
| Nutzung | ganze Server/Clients | einzelne Anwendungen |
| Beispiel | Ubuntu Server VM | nginx Container |

Vereinfacht:

```text
VM = ganzer virtueller Computer
Container = isolierte Anwendung mit Umgebung
```

Beides ist wichtig, aber für unterschiedliche Aufgaben.

---

## Typische Einsatzbereiche

Virtualisierung wird genutzt für:

```text
Servervirtualisierung
Testumgebungen
Schulungslabore
Home-Lab
Entwicklungsumgebungen
Windows- und Linux-Tests
Netzwerklabore
Firewall-Tests
Datenbankserver
Backup- und Restore-Tests
```

Für FISI ist besonders wichtig:

```text
VMs installieren
Ressourcen planen
Netzwerkmodi verstehen
Snapshots richtig nutzen
Backups unterscheiden
VMs sicher betreiben
Fehler systematisch prüfen
```

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| Host überlasten | zu viele VMs oder zu viel RAM vergeben |
| NAT und Bridge verwechseln | VM ist nicht wie erwartet erreichbar |
| Snapshot als Backup sehen | falsches Sicherheitsgefühl |
| VM nicht aktualisieren | Sicherheitslücken bleiben |
| keine Firewall in VM | unnötige Dienste erreichbar |
| virtuelle Festplatte nicht sichern | Datenverlust möglich |
| unklare VM-Namen | schlechte Übersicht |
| alte Test-VMs laufen lassen | Ressourcen und Sicherheitsrisiko |
| keine Dokumentation | Fehlersuche wird schwer |
| zu wenig Speicherplatz auf Host | VMs können abstürzen oder nicht starten |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Virtualisierung:

```text
VMs sinnvoll benennen
Zweck jeder VM dokumentieren
Ressourcen bewusst vergeben
Netzwerkmodus bewusst wählen
Snapshots nur gezielt nutzen
Backups einrichten
Restore testen
Updates in VMs durchführen
Firewall prüfen
alte VMs entfernen oder archivieren
```

Wichtige Regel:

```text
Virtuell bedeutet nicht unwichtig.
```

Eine VM muss genauso gepflegt und abgesichert werden wie ein physisches System.

---

## FISI-Bezug

Virtualisierung ist ein wichtiges Thema für FISI.

Man braucht dieses Wissen für:

```text
Serverbetrieb
Testumgebungen
Home-Lab
Windows- und Linux-Installationen
Netzwerklabore
Docker-Umgebungen
Backup-Konzepte
Troubleshooting
IT-Sicherheit
Dokumentation
```

Ein FISI sollte erklären können:

```text
was eine VM ist
was ein Hypervisor macht
was Host und Gast bedeuten
was NAT, Bridge und Host-only unterscheiden
warum Snapshots keine Backups ersetzen
wie Ressourcen geplant werden
wie VMs sicher betrieben werden
```

---

## Kurze Zusammenfassung

Virtualisierung ermöglicht, mehrere virtuelle Systeme auf einem physischen Host zu betreiben.

Wichtige Begriffe sind Host, Gast, VM, Hypervisor, vCPU, RAM, virtuelle Festplatte, ISO, NAT, Bridge, Host-only, Snapshot und Backup.

Virtualisierung ist wichtig für Server, Tests, Home-Labs, Schulung, Entwicklung und moderne IT-Infrastruktur.

Für FISI ist dieses Thema besonders wichtig, weil viele praktische Aufgaben mit virtuellen Maschinen, Ressourcen, Netzwerken, Backups, Sicherheit und Dokumentation zusammenhängen.