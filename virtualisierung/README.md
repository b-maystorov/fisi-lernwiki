# Virtualisierung

In diesem Bereich geht es um Virtualisierung und virtuelle Maschinen.

Virtualisierung bedeutet, dass Hardware oder IT-Ressourcen logisch nachgebildet werden. Dadurch können mehrere virtuelle Systeme auf einem physischen Gerät laufen. In der Praxis nutzt man Virtualisierung für Server, Testumgebungen, Schulungslabore, Entwicklung, Home-Labs und produktive IT-Infrastruktur.

Für Fachinformatiker für Systemintegration ist Virtualisierung sehr wichtig, weil viele Unternehmen nicht für jeden Dienst einen eigenen physischen Server betreiben. Stattdessen laufen viele Server als virtuelle Maschinen auf gemeinsamen Hosts.

---

## Kurz erklärt

Virtualisierung ermöglicht, dass ein physischer Computer mehrere virtuelle Systeme betreiben kann.

Beispiel:

```text
Physischer Host
├── VM 1: Ubuntu Server
├── VM 2: Windows Server
├── VM 3: Test-Client
└── VM 4: Datenbankserver
```

Jede virtuelle Maschine verhält sich wie ein eigener Computer.

Sie hat eigene:

```text
CPU-Ressourcen
RAM
Festplatte
Netzwerkkarte
Betriebssystem
Dienste
Konfiguration
```

---

## Kapitelübersicht

| Kapitel | Thema |
|---|---|
| [1. Virtualisierung Grundlagen](./01-virtualisierung-grundlagen.md) | Grundidee, Vorteile, Einsatzbereiche und wichtige Begriffe |
| [2. Virtuelle Maschinen](./02-virtuelle-maschinen.md) | Aufbau, Betriebssysteme, virtuelle Hardware und typische VM-Aufgaben |
| [3. Hypervisor und Ressourcen](./03-hypervisor-und-ressourcen.md) | Hypervisor-Typen, CPU, RAM, Storage und Ressourcenplanung |
| [4. Netzwerkmodi: NAT, Bridge und Host-only](./04-netzwerkmodi-nat-bridge-host-only.md) | Netzwerkverbindung von VMs verstehen und prüfen |
| [5. Snapshots, Backups und Sicherheit](./05-snapshots-backups-und-sicherheit.md) | Snapshots richtig nutzen, Backups planen und VMs absichern |
| [6. Virtualisierung in der FISI-Praxis](./06-virtualisierung-in-der-fisi-praxis.md) | praktische Aufgaben, typische Fehler und saubere Dokumentation |

---

## Warum Virtualisierung wichtig ist

Virtualisierung wird genutzt, weil sie IT-Systeme flexibler macht.

Ohne Virtualisierung:

```text
Ein physischer Server für einen Dienst.
Hardware wird oft nicht komplett genutzt.
Tests brauchen eigene Geräte.
Wiederherstellung ist schwieriger.
```

Mit Virtualisierung:

```text
mehrere Server auf einem Host
schnell neue Testsysteme erstellen
Systeme einfacher verschieben
bessere Ressourcennutzung
Snapshots für Tests
einfachere Laborumgebungen
```

Virtualisierung spart nicht automatisch Arbeit, aber sie macht viele Aufgaben planbarer und flexibler.

---

## Wichtige Begriffe

| Begriff | Bedeutung |
|---|---|
| Host | physischer Rechner, auf dem VMs laufen |
| Gast / Guest | virtuelle Maschine innerhalb des Hosts |
| VM | virtuelle Maschine |
| Hypervisor | Software, die virtuelle Maschinen bereitstellt |
| vCPU | virtuelle CPU für eine VM |
| RAM | Arbeitsspeicher, der einer VM zugewiesen wird |
| virtuelle Festplatte | Datei oder Speicherbereich als Festplatte der VM |
| virtuelle Netzwerkkarte | Netzwerkschnittstelle der VM |
| Snapshot | gespeicherter Zustand einer VM zu einem Zeitpunkt |
| ISO-Datei | Installationsabbild für Betriebssysteme |
| NAT | VM nutzt Host als Übergang ins Netzwerk |
| Bridge | VM erscheint wie eigenes Gerät im Netzwerk |
| Host-only | Netzwerk nur zwischen Host und VM |

---

## Host und Gast

Der Host ist das echte physische System.

Beispiel:

```text
Laptop mit Ubuntu
Desktop-PC mit Windows
Server im Rechenzentrum
```

Der Gast ist die virtuelle Maschine, die auf dem Host läuft.

Beispiel:

```text
Ubuntu Server VM
Windows Server VM
Test-Client VM
Firewall VM
```

Vereinfacht:

```text
Host = echter Computer
Gast = virtueller Computer
```

---

## Hypervisor

Ein Hypervisor ist die Software, die virtuelle Maschinen ermöglicht.

Er verteilt die Ressourcen des Hosts an die VMs.

Beispiele für Hypervisor oder Virtualisierungsplattformen:

```text
KVM/QEMU
VirtualBox
VMware Workstation
VMware ESXi
Microsoft Hyper-V
Proxmox VE
```

Der Hypervisor sorgt dafür, dass mehrere VMs auf derselben Hardware laufen können.

---

## Typ-1- und Typ-2-Hypervisor

Es gibt zwei wichtige Arten von Hypervisoren.

| Typ | Bedeutung | Beispiel |
|---|---|---|
| Typ 1 | läuft direkt auf der Hardware | VMware ESXi, Hyper-V Server, Proxmox VE |
| Typ 2 | läuft auf einem normalen Betriebssystem | VirtualBox, VMware Workstation |

Typ 1 wird oft in Serverumgebungen genutzt.

Typ 2 ist häufig für Lernen, Tests und Desktop-Labore.

---

## Virtuelle Hardware

Eine VM bekommt virtuelle Hardware.

Beispiele:

```text
virtuelle CPU
virtueller RAM
virtuelle Festplatte
virtuelle Netzwerkkarte
virtuelles CD/DVD-Laufwerk
virtuelle Grafikkarte
```

Das Betriebssystem in der VM erkennt diese Komponenten wie echte Hardware.

Beispiel:

```text
Ubuntu Server läuft in einer VM.
Für Ubuntu sieht es so aus, als hätte es eine eigene Festplatte und Netzwerkkarte.
```

---

## Vorteile von Virtualisierung

Virtualisierung hat viele Vorteile.

| Vorteil | Erklärung |
|---|---|
| bessere Ressourcennutzung | mehrere Systeme teilen sich einen Host |
| Flexibilität | neue VMs können schnell erstellt werden |
| Testumgebungen | Systeme können gefahrlos ausprobiert werden |
| Isolation | Fehler in einer VM betreffen nicht automatisch alle Systeme |
| Snapshots | Zustand kann vor Tests gespeichert werden |
| einfachere Migration | VMs können oft leichter verschoben werden |
| Home-Lab | realistische Umgebung auf wenig Hardware |

Für Lernen ist Virtualisierung besonders praktisch, weil man Fehler machen kann, ohne direkt ein echtes Produktivsystem zu beschädigen.

---

## Nachteile und Risiken

Virtualisierung hat auch Nachteile.

| Nachteil | Erklärung |
|---|---|
| Ressourcenverbrauch | VMs brauchen CPU, RAM und Speicher |
| Komplexität | Netzwerk, Storage und Rechte müssen geplant werden |
| Host-Abhängigkeit | fällt der Host aus, sind mehrere VMs betroffen |
| Performance | falsche Ressourcenplanung kann Systeme langsam machen |
| Sicherheitsrisiko | unsichere VMs können Netzwerk oder Host gefährden |
| Backup-Aufwand | VMs und Daten müssen richtig gesichert werden |

Virtualisierung ist also nicht automatisch einfacher. Sie braucht gute Planung.

---

## VM vs Container

Virtuelle Maschinen und Container sind nicht dasselbe.

| Bereich | Virtuelle Maschine | Container |
|---|---|---|
| Betriebssystem | eigenes Gast-Betriebssystem | teilt sich Kernel mit Host |
| Isolation | stärker | leichter |
| Startzeit | langsamer | schneller |
| Ressourcen | mehr Verbrauch | weniger Verbrauch |
| Nutzung | ganze Server/Clients | einzelne Anwendungen |
| Beispiel | Ubuntu Server VM | nginx Container |

Vereinfacht:

```text
VM = ganzer virtueller Computer
Container = isolierter Anwendungsprozess mit Umgebung
```

Beides ist wichtig, aber für unterschiedliche Aufgaben.

---

## Typische Einsatzbereiche

Virtualisierung wird in vielen Bereichen genutzt.

Beispiele:

```text
Servervirtualisierung
Testumgebungen
Entwicklungsumgebungen
Schulungslabore
Home-Lab
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
Fehler systematisch prüfen
```

---

## Ressourcenplanung

Eine VM braucht Ressourcen vom Host.

Wichtige Ressourcen:

```text
CPU
RAM
Speicherplatz
Netzwerk
I/O-Leistung
```

Beispiel:

```text
Host hat 16 GB RAM.
VM 1 bekommt 4 GB RAM.
VM 2 bekommt 4 GB RAM.
Host braucht selbst auch RAM.
```

Man sollte nicht einfach allen VMs zu viele Ressourcen geben.

Sonst wird der Host langsam oder instabil.

---

## Storage

Virtuelle Festplatten liegen oft als Dateien oder Storage-Volumes auf dem Host.

Beispiele:

```text
.qcow2
.vdi
.vmdk
.raw
```

Wichtige Fragen:

```text
Wie groß ist die virtuelle Festplatte?
Ist sie dynamisch oder fest zugewiesen?
Wo liegt sie?
Wird sie gesichert?
Wie schnell ist der Storage?
```

Storage ist wichtig, weil VMs ohne funktionierende virtuelle Festplatte nicht starten oder Daten verlieren können.

---

## Netzwerkmodi

VMs brauchen Netzwerkanbindung.

Typische Netzwerkmodi:

| Modus | Bedeutung |
|---|---|
| NAT | VM nutzt den Host als Übergang |
| Bridge | VM ist wie eigenes Gerät im LAN |
| Host-only | Verbindung zwischen Host und VM |
| Internal Network | Verbindung nur zwischen VMs |

Der Netzwerkmodus entscheidet, wie die VM erreichbar ist.

Beispiel:

```text
NAT = gut für Internetzugang der VM
Bridge = gut, wenn VM wie eigener Server im LAN erreichbar sein soll
Host-only = gut für isolierte Labore
```

---

## NAT bei VMs

Bei NAT nutzt die VM den Host als Übergang ins Netzwerk.

Vereinfacht:

```text
VM -> Host -> Netzwerk/Internet
```

Vorteile:

```text
einfacher Internetzugang
VM ist nicht direkt wie eigenes Gerät im LAN sichtbar
gut für Tests
```

Nachteile:

```text
VM ist von anderen Geräten oft nicht direkt erreichbar
Portweiterleitung kann nötig sein
Netzwerkverhalten ist manchmal schwerer zu verstehen
```

---

## Bridge bei VMs

Bei Bridge erscheint die VM wie ein eigenes Gerät im lokalen Netzwerk.

Vereinfacht:

```text
VM -> direkt im LAN
```

Die VM bekommt oft eine eigene IP-Adresse aus dem normalen Netzwerk.

Vorteile:

```text
VM ist leichter von anderen Geräten erreichbar
gut für Serverdienste im Lab
realistisches Netzwerkverhalten
```

Nachteile:

```text
VM ist sichtbarer im Netzwerk
Sicherheitsregeln wichtiger
nicht jedes WLAN/Netzwerk erlaubt Bridge problemlos
```

---

## Host-only

Host-only bedeutet:

```text
Host und VM können miteinander kommunizieren.
Andere Geräte im Netzwerk meistens nicht.
```

Das ist gut für isolierte Tests.

Beispiel:

```text
Host testet SSH zu Ubuntu-Server-VM.
VM ist nicht im normalen LAN sichtbar.
```

Host-only ist praktisch, wenn man sicher testen möchte, ohne das normale Netzwerk zu beeinflussen.

---

## Snapshots

Ein Snapshot speichert den Zustand einer VM zu einem bestimmten Zeitpunkt.

Beispiel:

```text
Snapshot vor Update
Snapshot vor Softwaretest
Snapshot vor riskanter Konfiguration
```

Wenn etwas schiefgeht, kann man zum Snapshot zurückkehren.

Wichtig:

```text
Snapshot ist kein vollständiges Backup.
```

Snapshots liegen oft auf demselben Host und schützen nicht zuverlässig gegen Hardwareausfall.

---

## Backups von VMs

VMs müssen gesichert werden.

Möglichkeiten:

```text
VM-Datei sichern
Image-Backup
Datei-Backup innerhalb der VM
Datenbank-Backup innerhalb der VM
Konfigurationsdateien sichern
```

Wichtig:

```text
Backup muss konsistent sein.
Restore muss getestet werden.
```

Ein VM-Snapshot ersetzt kein Backup.

---

## Sicherheit bei Virtualisierung

VMs sind eigene Systeme und müssen sicher betrieben werden.

Wichtige Punkte:

```text
Updates installieren
Firewall prüfen
SSH absichern
nur notwendige Dienste aktivieren
starke Passwörter oder SSH-Schlüssel nutzen
Netzwerkmodus bewusst wählen
Snapshots nicht als Backup verstehen
Zugriffe dokumentieren
Backups schützen
```

Eine unsichere VM kann ein Risiko für das Netzwerk sein.

---

## Virtualisierung und Home-Lab

Virtualisierung ist perfekt für ein Home-Lab.

Mögliche Übungen:

```text
Ubuntu Server installieren
Windows Server testen
SSH einrichten
statische IP konfigurieren
NAT und Bridge vergleichen
Docker in einer VM installieren
Samba-Freigabe testen
Firewall-Regeln testen
Snapshots nutzen
Backup und Restore üben
```

Ein Home-Lab hilft, FISI-Themen praktisch zu verstehen.

---

## Virtualisierung und FISI

Für FISI ist Virtualisierung wichtig, weil viele echte IT-Umgebungen virtualisiert sind.

Man braucht Wissen über:

```text
VM-Erstellung
Betriebssysteminstallation
Ressourcenplanung
Netzwerkmodi
Snapshots
Backups
Serverdienste
Sicherheit
Troubleshooting
Dokumentation
```

Beispiel Praxisfall:

```text
Ein Ubuntu Server soll als VM laufen.
Er braucht 2 vCPUs, 4 GB RAM, 40 GB Speicher, Bridge-Netzwerk, SSH-Zugriff und Backup.
```

Das ist eine typische Aufgabe für Systemintegration.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| zu wenig RAM für Host übrig | Host wird langsam |
| zu viele VMs gleichzeitig | Ressourcen überlastet |
| NAT und Bridge verwechselt | VM ist nicht wie erwartet erreichbar |
| Snapshot als Backup verstanden | Datenverlust bei Hostproblem möglich |
| keine Updates in VMs | Sicherheitslücken bleiben |
| VM ohne Firewall | unnötige Dienste erreichbar |
| virtuelle Festplatte nicht gesichert | Datenverlust |
| unklare Namen | VMs schwer zuzuordnen |
| keine Dokumentation | Fehlersuche wird schwer |
| alte Test-VMs laufen weiter | unnötige Risiken und Ressourcenverbrauch |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Virtualisierung:

```text
VMs sauber benennen
Zweck der VM dokumentieren
Ressourcen passend vergeben
Netzwerkmodus bewusst wählen
nur notwendige Dienste aktivieren
Updates durchführen
Snapshots gezielt nutzen
Backups einrichten
Restore testen
alte VMs entfernen oder archivieren
```

Wichtige Regel:

```text
Eine VM ist kein Spielzeug, nur weil sie virtuell ist.
```

Auch virtuelle Systeme brauchen Pflege, Sicherheit und Dokumentation.

---

## Praktische Lernziele

Nach diesem Bereich sollte man erklären können:

```text
was Virtualisierung ist
was Host und Gast bedeuten
was ein Hypervisor macht
was Typ 1 und Typ 2 bedeutet
wie eine VM aufgebaut ist
wie Ressourcen geplant werden
was NAT, Bridge und Host-only bedeuten
warum Snapshots keine Backups ersetzen
wie VMs sicher betrieben werden
wie Virtualisierung in der FISI-Praxis genutzt wird
```

---

## Kurze Zusammenfassung

Virtualisierung ermöglicht, mehrere virtuelle Systeme auf einem physischen Host zu betreiben.

Wichtige Begriffe sind Host, Gast, VM, Hypervisor, vCPU, RAM, virtuelle Festplatte, virtuelle Netzwerkkarte, NAT, Bridge, Host-only, Snapshot und Backup.

Virtualisierung ist wichtig für Serverbetrieb, Testumgebungen, Home-Labs, Schulung, Entwicklung und moderne IT-Infrastruktur.

Für FISI ist Virtualisierung besonders wichtig, weil viele praktische Aufgaben mit VMs, Ressourcen, Netzwerken, Backups, Sicherheit und Dokumentation zusammenhängen.