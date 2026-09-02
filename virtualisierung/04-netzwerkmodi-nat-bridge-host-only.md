# 4. Netzwerkmodi: NAT, Bridge und Host-only

In diesem Kapitel geht es um Netzwerkmodi bei virtuellen Maschinen.

Eine VM braucht meistens Netzwerkzugriff. Der Netzwerkmodus entscheidet, ob die VM nur ins Internet kommt, ob sie vom Host erreichbar ist, ob andere Geräte im LAN sie erreichen können oder ob sie bewusst isoliert bleibt.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr wichtig, weil viele VM-Probleme keine Fehler im Betriebssystem sind, sondern falsche Netzwerkeinstellungen.

---

## Kurz erklärt

Eine VM hat eine virtuelle Netzwerkkarte.

Diese virtuelle Netzwerkkarte wird über den Hypervisor mit einem Netzwerk verbunden.

Typische Netzwerkmodi:

```text
NAT
Bridge
Host-only
Internal Network
```

Vereinfacht:

```text
NAT       = VM kommt über den Host ins Netzwerk/Internet
Bridge    = VM ist wie ein eigenes Gerät im LAN
Host-only = VM spricht nur mit dem Host
Internal  = VMs sprechen nur untereinander
```

Der Netzwerkmodus beeinflusst Erreichbarkeit, Sicherheit und Fehlersuche.

---

## Warum Netzwerkmodi wichtig sind

Eine VM kann technisch korrekt installiert sein und trotzdem keine Netzwerkverbindung haben.

Typische Ursachen:

```text
falscher Netzwerkmodus
keine IP-Adresse
kein Gateway
DNS funktioniert nicht
Firewall blockiert Verbindung
Bridge funktioniert im WLAN nicht
Portweiterleitung fehlt
```

Deshalb muss man verstehen, wie die VM mit dem Netzwerk verbunden ist.

Wichtige Fragen:

```text
Soll die VM nur Internetzugang haben?
Soll der Host die VM erreichen?
Sollen andere Geräte die VM erreichen?
Soll die VM isoliert sein?
Soll die VM wie ein echter Server im LAN arbeiten?
```

---

## Virtuelle Netzwerkkarte

Eine VM nutzt eine virtuelle Netzwerkkarte.

Für das Betriebssystem in der VM sieht sie aus wie eine normale Netzwerkkarte.

In Linux kann man sie prüfen mit:

```bash
ip a
```

Routing prüft man mit:

```bash
ip route
```

DNS und Internet prüft man mit:

```bash
ping 8.8.8.8
ping github.com
```

Wichtig:

```text
Die VM sieht nur ihre eigene virtuelle Netzwerkkarte.
Der Hypervisor entscheidet, wohin diese Netzwerkkarte verbunden ist.
```

---

## NAT

NAT bedeutet:

```text
Network Address Translation
```

Bei NAT nutzt die VM den Host als Übergang ins Netzwerk oder Internet.

Vereinfacht:

```text
VM -> Host -> Router -> Internet
```

Die VM ist dabei meistens nicht direkt als eigenes Gerät im LAN sichtbar.

Beispiel:

```text
Host im LAN: 192.168.1.20
VM im NAT-Netz: 10.0.2.15
Router: 192.168.1.1
```

Die VM kann oft ins Internet, aber andere Geräte im LAN können die VM nicht direkt erreichen.

---

## NAT im Alltag

NAT ist oft die einfachste Einstellung für Lern-VMs.

Gut geeignet für:

```text
Ubuntu Server installieren
Updates herunterladen
Pakete installieren
Internet in der VM nutzen
einfache Tests durchführen
```

Vorteile:

```text
einfach einzurichten
funktioniert oft sofort
VM ist nicht direkt im LAN sichtbar
gut für erste Tests
```

Nachteile:

```text
VM ist von anderen Geräten oft nicht direkt erreichbar
Serverdienste brauchen Portweiterleitung
Netzwerkverhalten ist weniger realistisch als Bridge
```

---

## NAT und Portweiterleitung

Wenn eine VM im NAT-Modus einen Dienst anbietet, ist dieser Dienst nicht automatisch vom LAN erreichbar.

Beispiel:

```text
VM läuft mit SSH auf Port 22.
Host nutzt NAT.
Andere Geräte erreichen die VM nicht direkt.
```

Dann braucht man Portweiterleitung.

Beispiel-Idee:

```text
Host-Port 2222 -> VM-Port 22
```

Dann verbindet man sich zum Beispiel auf den Host-Port 2222 und wird zur VM weitergeleitet.

Vereinfacht:

```text
Client -> Host:2222 -> VM:22
```

Portweiterleitung ist typisch bei NAT, wenn man Dienste in der VM von außen erreichen möchte.

---

## Bridge

Bridge bedeutet:

```text
Die VM wird direkt mit dem lokalen Netzwerk verbunden.
```

Die VM erscheint im LAN wie ein eigenes Gerät.

Vereinfacht:

```text
VM -> LAN -> Router
```

Beispiel:

```text
Host: 192.168.1.20
VM:   192.168.1.55
Router: 192.168.1.1
```

Die VM bekommt oft eine IP-Adresse vom gleichen DHCP-Server wie der Host.

Das ist besonders praktisch, wenn die VM wie ein echter Server erreichbar sein soll.

---

## Bridge im Alltag

Bridge ist gut geeignet für realistische Netzwerktests.

Gut geeignet für:

```text
Serverdienste im Lab
SSH-Zugriff von anderen Geräten
Webserver-Test
Windows-Server-Lab
Active Directory Tests
Samba-Freigaben
Netzwerkdienste wie DNS oder DHCP
```

Vorteile:

```text
VM ist wie eigenes Gerät im LAN
realistisches Netzwerkverhalten
andere Geräte können die VM erreichen
gut für Server-Tests
```

Nachteile:

```text
VM ist sichtbarer im Netzwerk
Firewall und Updates sind wichtiger
nicht jedes WLAN unterstützt Bridge problemlos
falsche Dienste können das LAN stören
```

---

## Bridge und Sicherheit

Eine VM im Bridge-Modus ist stärker im echten Netzwerk sichtbar.

Das bedeutet:

```text
offene Ports sind im LAN erreichbar
andere Geräte können die VM sehen
unsichere Dienste können ein Risiko sein
falsche Netzwerkkonfiguration kann stören
```

Deshalb sollte man prüfen:

```bash
ss -tulpen
sudo ufw status
ip a
ip route
```

Wichtig:

```text
Bridge ist praktisch, aber nicht automatisch sicher.
```

Wenn eine VM als Server im LAN sichtbar ist, muss sie wie ein echter Server gepflegt werden.

---

## Host-only

Host-only bedeutet:

```text
Die VM kann mit dem Host kommunizieren.
Andere Geräte im LAN erreichen die VM meistens nicht.
```

Vereinfacht:

```text
Host <-> VM
```

Beispiel:

```text
Host: 192.168.56.1
VM:   192.168.56.10
```

Dieses Netzwerk ist oft ein eigenes virtuelles Netz zwischen Host und VM.

---

## Host-only im Alltag

Host-only ist gut für isolierte Tests.

Gut geeignet für:

```text
SSH vom Host zur VM
Labor ohne Zugriff aus dem LAN
Tests mit Serverdiensten
sicheres Üben
Client-Server-Test auf einem Gerät
```

Vorteile:

```text
isolierter als Bridge
Host kann VM erreichen
gut für Lernlabore
weniger Risiko für echtes LAN
```

Nachteile:

```text
VM hat nicht immer Internetzugang
andere Geräte erreichen die VM nicht direkt
zusätzliche Netzwerkkarte kann nötig sein
```

Manchmal kombiniert man Host-only mit NAT.

Dann hat die VM:

```text
NAT für Internet
Host-only für Zugriff vom Host
```

---

## Internal Network

Internal Network bedeutet:

```text
VMs kommunizieren nur untereinander.
Der Host ist meistens nicht direkt beteiligt.
Das echte LAN ist nicht beteiligt.
```

Vereinfacht:

```text
VM 1 <-> VM 2 <-> VM 3
```

Gut geeignet für:

```text
isolierte Netzwerklabore
Firewall-Tests
Client-Server-Übungen
DHCP/DNS-Tests ohne echtes LAN
Sicherheitsübungen
```

Vorteile:

```text
starke Isolation
keine Störung des echten LANs
gut für Labore
```

Nachteile:

```text
kein direkter Internetzugang
Host-Zugriff nicht automatisch vorhanden
mehr Planung nötig
```

---

## Vergleich der Netzwerkmodi

| Modus | Internet | Host erreicht VM | LAN erreicht VM | Typischer Einsatz |
|---|---|---|---|---|
| NAT | meistens ja | oft nur mit Portweiterleitung | meistens nein | einfache Tests, Updates |
| Bridge | ja, wenn LAN funktioniert | ja | ja | Server im Lab, realistische Tests |
| Host-only | meistens nein | ja | nein | isolierte Host-VM-Tests |
| Internal Network | nein | meistens nein | nein | isolierte VM-zu-VM-Labore |

Der beste Modus hängt vom Ziel ab.

Es gibt nicht den einen richtigen Netzwerkmodus für alles.

---

## NAT oder Bridge?

NAT wählen, wenn:

```text
VM nur Internet braucht
VM nicht direkt im LAN sichtbar sein soll
man schnell testen möchte
man keine Serverdienste im LAN bereitstellen muss
```

Bridge wählen, wenn:

```text
VM wie ein eigenes Gerät im LAN arbeiten soll
andere Geräte die VM erreichen sollen
Serverdienste getestet werden
realistische Netzwerkanbindung gewünscht ist
```

Merksatz:

```text
NAT = einfacher und abgeschirmter
Bridge = realistischer und erreichbarer
```

---

## Host-only oder Internal Network?

Host-only wählen, wenn:

```text
Host und VM miteinander sprechen sollen
VM nicht im echten LAN sichtbar sein soll
man sicher vom Host zur VM testen möchte
```

Internal Network wählen, wenn:

```text
mehrere VMs nur untereinander sprechen sollen
das echte LAN nicht beteiligt sein soll
ein isoliertes Netzwerklabor gebaut wird
```

Merksatz:

```text
Host-only = Host plus VM
Internal = nur VMs untereinander
```

---

## Zwei Netzwerkkarten in einer VM

Eine VM kann mehrere virtuelle Netzwerkkarten haben.

Beispiel:

```text
Netzwerkkarte 1: NAT
Netzwerkkarte 2: Host-only
```

Dann kann die VM:

```text
über NAT ins Internet
über Host-only vom Host erreicht werden
```

Das ist in Laboren sehr praktisch.

Beispiel:

```text
Ubuntu Server VM
├── NAT: Updates und Internet
└── Host-only: SSH vom Host
```

Wichtig ist, die IP-Adressen und Routen sauber zu prüfen.

---

## IP-Adresse prüfen

In Linux:

```bash
ip a
```

Beispiel:

```text
ens3: 10.0.2.15/24
```

Das zeigt:

```text
Interface-Name
IP-Adresse
Subnetz
Status der Netzwerkkarte
```

Wenn keine passende IP-Adresse vorhanden ist, sollte man prüfen:

```text
Netzwerkmodus
DHCP
virtuelle Netzwerkkarte
Netzwerkkonfiguration in der VM
```

---

## Gateway prüfen

Das Gateway zeigt, wohin Pakete geschickt werden, wenn das Ziel nicht im eigenen Netz liegt.

In Linux:

```bash
ip route
```

Beispiel:

```text
default via 10.0.2.2 dev ens3
```

Das bedeutet:

```text
Standardroute geht über 10.0.2.2
Interface ist ens3
```

Ohne korrektes Gateway hat die VM oft keinen Internetzugang.

---

## DNS prüfen

DNS bedeutet:

```text
Domain Name System
```

DNS übersetzt Namen in IP-Adressen.

Beispiel:

```text
github.com -> IP-Adresse
```

Test:

```bash
ping 8.8.8.8
ping github.com
```

Interpretation:

```text
ping 8.8.8.8 funktioniert, ping github.com nicht
=> wahrscheinlich DNS-Problem
```

DNS-Probleme sind in VMs sehr häufig.

---

## Dienste prüfen

Wenn eine VM einen Dienst anbietet, muss man prüfen:

```text
läuft der Dienst?
lauscht der Dienst auf einem Port?
erlaubt die Firewall den Zugriff?
ist die VM im richtigen Netzwerkmodus?
ist die IP-Adresse korrekt?
```

Befehle:

```bash
systemctl status ssh
ss -tulpen
sudo ufw status
```

Beispiel:

```text
SSH läuft.
Port 22 ist offen.
VM ist im Bridge-Modus.
Host kann VM per SSH erreichen.
```

Dann ist die Grundverbindung korrekt.

---

## Firewall in der VM

Auch wenn der Netzwerkmodus korrekt ist, kann die Firewall in der VM den Zugriff blockieren.

UFW prüfen:

```bash
sudo ufw status
```

SSH erlauben:

```bash
sudo ufw allow ssh
```

Status erneut prüfen:

```bash
sudo ufw status
```

Wichtig:

```text
Netzwerk funktioniert nicht automatisch nur, weil die VM eine IP-Adresse hat.
Firewall-Regeln müssen ebenfalls passen.
```

---

## Fehlersuche Schritt für Schritt

Bei VM-Netzwerkproblemen sollte man systematisch prüfen.

Reihenfolge:

```text
1. Ist die virtuelle Netzwerkkarte aktiviert?
2. Welcher Netzwerkmodus ist eingestellt?
3. Hat die VM eine IP-Adresse?
4. Hat die VM ein Gateway?
5. Funktioniert ping auf eine IP-Adresse?
6. Funktioniert DNS?
7. Läuft der gewünschte Dienst?
8. Lauscht der Dienst auf dem richtigen Port?
9. Erlaubt die Firewall den Zugriff?
10. Ist die VM aus dem gewünschten Netz erreichbar?
```

Diese Reihenfolge verhindert wildes Raten.

---

## Beispiel 1: VM hat Internet, ist aber nicht erreichbar

Situation:

```text
Ubuntu Server VM nutzt NAT.
Updates funktionieren.
Host oder andere Geräte können aber nicht per SSH auf die VM zugreifen.
```

Erklärung:

```text
NAT erlaubt der VM oft Verbindungen nach außen.
Verbindungen von außen zur VM funktionieren aber nicht automatisch.
```

Lösung:

```text
Portweiterleitung einrichten
oder Bridge/Host-only nutzen
```

---

## Beispiel 2: VM ist im LAN erreichbar

Situation:

```text
Ubuntu Server VM nutzt Bridge.
VM bekommt IP 192.168.1.55.
Host hat IP 192.168.1.20.
```

Prüfung:

```bash
ping 192.168.1.55
ssh user@192.168.1.55
```

Wenn SSH nicht funktioniert:

```text
SSH-Dienst prüfen
Firewall prüfen
IP-Adresse prüfen
Netzwerkmodus prüfen
```

Bridge ist gut, wenn die VM wie ein echter Server im Netzwerk erreichbar sein soll.

---

## Beispiel 3: Isoliertes Labor

Situation:

```text
Eine Ubuntu Server VM soll nur vom Host erreichbar sein.
Das normale LAN soll nicht beteiligt sein.
```

Passender Modus:

```text
Host-only
```

Vorteile:

```text
Host kann testen
VM bleibt vom LAN getrennt
gut für sichere Übungen
```

Typischer Test:

```bash
ping <vm-ip>
ssh user@<vm-ip>
```

---

## Beispiel 4: Zwei VMs im isolierten Netz

Situation:

```text
Eine Client-VM und eine Server-VM sollen miteinander sprechen.
Das echte LAN soll nicht betroffen sein.
```

Passender Modus:

```text
Internal Network
```

Beispiel:

```text
Server VM: 192.168.50.10
Client VM: 192.168.50.20
Netz:      192.168.50.0/24
```

Das ist gut für DNS-, DHCP-, Firewall- oder Server-Client-Übungen.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| NAT erwartet wie Bridge | VM ist nicht direkt erreichbar |
| Bridge ohne Firewall | VM ist unnötig offen im LAN |
| Host-only erwartet Internet | VM hat keinen Internetzugang |
| falsches Interface geprüft | IP-Adresse wird falsch interpretiert |
| kein Gateway | Internet funktioniert nicht |
| DNS nicht geprüft | Namen funktionieren nicht |
| Dienst läuft nicht | Port ist nicht erreichbar |
| Firewall blockiert Zugriff | Netzwerk wirkt kaputt |
| Bridge im WLAN funktioniert nicht | VM bekommt keine passende Verbindung |
| IP-Adressen nicht dokumentiert | Fehlersuche dauert länger |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei VM-Netzwerken:

```text
Ziel der VM festlegen
passenden Netzwerkmodus wählen
IP-Adresse prüfen
Gateway prüfen
DNS prüfen
offene Ports prüfen
Firewall prüfen
Erreichbarkeit testen
Netzwerke dokumentieren
unnötige Erreichbarkeit vermeiden
```

Wichtige Regel:

```text
Erreichbarkeit ist immer eine Sicherheitsentscheidung.
```

Eine VM sollte nur aus den Netzen erreichbar sein, aus denen sie wirklich erreichbar sein muss.

---

## Praktische Befehle

### IP-Adresse anzeigen

```bash
ip a
```

### Routing anzeigen

```bash
ip route
```

### Internet per IP testen

```bash
ping 8.8.8.8
```

### DNS testen

```bash
ping github.com
```

### Offene Ports anzeigen

```bash
ss -tulpen
```

### SSH-Dienst prüfen

```bash
systemctl status ssh
```

### Firewall prüfen

```bash
sudo ufw status
```

---

## FISI-Bezug

Netzwerkmodi bei VMs sind für FISI sehr wichtig.

Man braucht dieses Wissen für:

```text
Server-VMs einrichten
Testumgebungen bauen
SSH-Zugriff prüfen
Windows- und Linux-Labore verbinden
Docker-VMs betreiben
Firewall-Labore aufbauen
DNS- und DHCP-Tests durchführen
Netzwerkprobleme analysieren
Sicherheit und Erreichbarkeit planen
Dokumentation schreiben
```

Ein FISI sollte nicht nur wissen, dass eine VM „Internet hat“.

Er sollte verstehen, warum sie erreichbar ist oder warum sie nicht erreichbar ist.

---

## Kurze Zusammenfassung

Der Netzwerkmodus entscheidet, wie eine VM mit Host, LAN und Internet verbunden ist.

NAT ist einfach und gut für Internetzugang, macht die VM aber meistens nicht direkt im LAN erreichbar.

Bridge macht die VM wie ein eigenes Gerät im LAN sichtbar und ist gut für realistische Server-Tests.

Host-only verbindet Host und VM in einem isolierten Netz.

Internal Network verbindet VMs untereinander, ohne das echte LAN einzubeziehen.

Für FISI ist dieses Thema wichtig, weil VM-Netzwerkprobleme häufig vorkommen und nur mit systematischer Prüfung sauber gelöst werden können.