# Netzwerke

In diesem Bereich geht es um Netzwerkgrundlagen und praktische Netzwerktechnik.

Netzwerke sind ein zentraler Teil der IT-Systemintegration. Fast alle IT-Systeme sind heute miteinander verbunden: Clients, Server, Drucker, Router, Switches, WLAN-Access-Points, virtuelle Maschinen, Container, Cloud-Dienste und Anwendungen.

Für Fachinformatiker für Systemintegration ist Netzwerkverständnis sehr wichtig, weil viele Fehler in der Praxis mit IP-Adressen, DNS, DHCP, Gateways, Routing, VLANs, WLAN oder Firewall-Regeln zusammenhängen.

---

## Kurz erklärt

Ein Netzwerk verbindet Geräte miteinander, damit sie Daten austauschen können.

Beispiele für Netzwerkgeräte:

```text
PC
Laptop
Server
Switch
Router
Access Point
Firewall
Drucker
Smartphone
virtuelle Maschine
Container
```

Typische Netzwerkaufgaben:

- IP-Adressen verstehen
- Subnetze planen
- DNS-Namen auflösen
- DHCP nutzen
- Gateways verstehen
- Routing nachvollziehen
- VLANs einordnen
- WLAN-Grundlagen verstehen
- Netzwerkfehler systematisch prüfen

---

## Kapitelübersicht

| Kapitel                                                                 | Thema                                                              |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------ |
| [1. Netzwerk-Grundlagen](./01-netzwerk-grundlagen.md)                   | Grundbegriffe, Netzwerkarten, Geräte und Kommunikation             |
| [2. IP-Adressen und Subnetting](./02-ip-adressen-und-subnetting.md)     | IPv4, Subnetzmasken, CIDR, Netzanteil und Hostanteil               |
| [3. DNS, DHCP und Gateway](./03-dns-dhcp-gateway.md)                    | Namensauflösung, automatische IP-Vergabe und Standardgateway       |
| [4. Routing, NAT und VLAN](./04-routing-nat-vlan.md)                    | Netzwerke verbinden, Adressübersetzung und logische Trennung       |
| [5. Switching und WLAN](./05-switching-und-wlan.md)                     | Switches, MAC-Adressen, Access Points und WLAN-Grundlagen          |
| [6. Netzwerk-Troubleshooting](./06-netzwerk-troubleshooting.md)         | Fehleranalyse mit `ping`, `ip`, `traceroute`, `ss`, `dig` und Logs |
| [7. Netzwerke in der FISI-Praxis](./07-netzwerke-in-der-fisi-praxis.md) | Praxisbezug, typische Aufgaben und saubere Arbeitsweise            |

---

## Warum Netzwerke wichtig sind

Ohne Netzwerke könnten IT-Systeme kaum sinnvoll zusammenarbeiten.

Beispiele:

| Situation                                 | Netzwerkbezug                            |
| ----------------------------------------- | ---------------------------------------- |
| Benutzer öffnet eine Webseite             | DNS, IP, Routing, HTTPS                  |
| Client meldet sich an Domäne an           | DNS, DHCP, Gateway, Servererreichbarkeit |
| Drucker ist nicht erreichbar              | IP-Adresse, Netzwerk, VLAN, Firewall     |
| Server ist per SSH nicht erreichbar       | IP, Port, Routing, Dienststatus          |
| VM hat kein Internet                      | NAT, Bridge, Gateway, DNS                |
| Docker-Container erreicht Datenbank nicht | Docker-Netzwerk, Service-Name, Port      |
| WLAN ist instabil                         | Signal, Kanal, Access Point, Störung     |

Viele IT-Probleme wirken zuerst wie ein Anwendungsproblem, sind aber eigentlich Netzwerkprobleme.

---

## Wichtige Grundbegriffe

| Begriff      | Bedeutung                                          |
| ------------ | -------------------------------------------------- |
| Client       | Gerät oder Programm, das einen Dienst nutzt        |
| Server       | Gerät oder Programm, das einen Dienst bereitstellt |
| IP-Adresse   | logische Adresse eines Geräts im Netzwerk          |
| MAC-Adresse  | Hardwareadresse einer Netzwerkschnittstelle        |
| Subnetz      | Teilbereich eines IP-Netzwerks                     |
| Subnetzmaske | trennt Netzanteil und Hostanteil                   |
| Gateway      | Übergang in andere Netzwerke                       |
| Router       | verbindet verschiedene Netzwerke                   |
| Switch       | verbindet Geräte im lokalen Netzwerk               |
| DNS          | löst Namen in IP-Adressen auf                      |
| DHCP         | vergibt Netzwerkkonfiguration automatisch          |
| NAT          | übersetzt private und öffentliche IP-Adressen      |
| VLAN         | logische Trennung innerhalb eines Netzwerks        |
| Port         | Nummer für einen bestimmten Dienst auf einem Gerät |

---

## Netzwerkarten

Netzwerke können nach Größe und Einsatzbereich unterschieden werden.

| Netzwerkart | Bedeutung               | Beispiel                                  |
| ----------- | ----------------------- | ----------------------------------------- |
| LAN         | Local Area Network      | Heimnetz, Firmennetz                      |
| WLAN        | Wireless LAN            | drahtloses lokales Netzwerk               |
| WAN         | Wide Area Network       | Verbindung über große Distanzen           |
| VPN         | Virtual Private Network | verschlüsselte Verbindung in ein Netzwerk |
| PAN         | Personal Area Network   | Bluetooth-Verbindung                      |
| VLAN        | Virtual LAN             | logische Trennung im LAN                  |

Für FISI sind besonders wichtig:

```text
LAN
WLAN
WAN
VPN
VLAN
```

---

## Einfaches Netzwerkbild

Ein einfaches Heim- oder Büronetzwerk kann so aussehen:

```text
Internet
   |
Router / Firewall
   |
Switch
   |
Clients, Server, Drucker, Access Points
```

Der Router verbindet das lokale Netzwerk mit dem Internet.

Der Switch verbindet Geräte im lokalen Netzwerk.

Access Points stellen WLAN bereit.

Server stellen Dienste bereit.

Clients nutzen diese Dienste.

---

## IP-Adresse

Eine IP-Adresse identifiziert ein Gerät logisch im Netzwerk.

Beispiel IPv4:

```text
192.168.1.25
```

Typische private IPv4-Bereiche:

```text
192.168.0.0/16
172.16.0.0/12
10.0.0.0/8
```

Private IP-Adressen werden in internen Netzwerken genutzt.

Öffentliche IP-Adressen werden im Internet genutzt.

---

## Subnetz

Ein Subnetz ist ein Teil eines IP-Netzwerks.

Beispiel:

```text
192.168.1.0/24
```

Das bedeutet meistens:

```text
Netzwerk: 192.168.1.0
Hosts: 192.168.1.1 bis 192.168.1.254
Broadcast: 192.168.1.255
```

Subnetze helfen, Netzwerke zu strukturieren und zu trennen.

---

## Gateway

Das Standardgateway ist der Weg aus dem eigenen Netzwerk heraus.

Beispiel:

```text
Client: 192.168.1.25
Gateway: 192.168.1.1
```

Wenn der Client ein Ziel außerhalb seines eigenen Netzes erreichen will, sendet er die Daten an das Gateway.

Ohne korrektes Gateway funktioniert oft nur das lokale Netzwerk, aber kein Internet oder kein Zugriff auf andere Netze.

---

## DNS

DNS bedeutet:

```text
Domain Name System
```

DNS übersetzt Namen in IP-Adressen.

Beispiel:

```text
github.com -> IP-Adresse
```

Ohne DNS müsste man viele IP-Adressen auswendig kennen.

Typischer Fehler:

```text
Ping auf IP funktioniert.
Ping auf Namen funktioniert nicht.
```

Dann ist oft DNS das Problem.

---

## DHCP

DHCP bedeutet:

```text
Dynamic Host Configuration Protocol
```

DHCP vergibt automatisch Netzwerkkonfigurationen.

Typische DHCP-Werte:

```text
IP-Adresse
Subnetzmaske
Gateway
DNS-Server
Lease-Zeit
```

Ohne DHCP müsste man diese Werte manuell eintragen.

---

## Ports

Ein Port identifiziert einen Dienst auf einem Gerät.

Beispiele:

| Port | Dienst                         |
| ---- | ------------------------------ |
| 22   | SSH                            |
| 53   | DNS                            |
| 80   | HTTP                           |
| 443  | HTTPS                          |
| 5432 | PostgreSQL                     |
| 3306 | MySQL                          |
| 8080 | häufig Web-GUI oder Testdienst |

Eine IP-Adresse zeigt auf das Gerät.  
Ein Port zeigt auf den Dienst auf diesem Gerät.

Beispiel:

```text
192.168.1.10:22
```

Das bedeutet:

```text
SSH-Dienst auf dem Gerät 192.168.1.10
```

---

## Netzwerk und Linux

Unter Linux gibt es viele wichtige Netzwerkbefehle.

Beispiele:

```bash
ip a
ip route
ping 8.8.8.8
ping github.com
ss -tulpen
dig github.com
traceroute github.com
nmcli device status
```

Diese Befehle helfen bei Fragen wie:

```text
Hat das Gerät eine IP-Adresse?
Ist ein Gateway gesetzt?
Funktioniert DNS?
Ist ein Dienst offen?
Wo bricht die Verbindung ab?
```

---

## Netzwerk und Docker

Docker nutzt eigene Netzwerke.

Beispiele:

```text
bridge network
custom Docker network
Docker Compose network
port mapping
service names
```

Bei Docker ist wichtig:

```text
localhost im Container bedeutet der Container selbst.
```

Wenn ein Container eine Datenbank in einem anderen Container erreichen soll, nutzt man meistens den Service-Namen.

Beispiel bei Docker Compose:

```text
db
adminer
web
backend
```

---

## Netzwerk und Virtualisierung

Virtuelle Maschinen können unterschiedlich ans Netzwerk angebunden werden.

Typische Modi:

| Modus            | Bedeutung                               |
| ---------------- | --------------------------------------- |
| NAT              | VM nutzt Host als Übergang ins Netzwerk |
| Bridge           | VM ist wie eigenes Gerät im Netzwerk    |
| Host-only        | Verbindung nur zwischen Host und VM     |
| Internal Network | Verbindung nur zwischen VMs             |

Für Home-Lab und FISI-Praxis sind besonders wichtig:

```text
NAT
Bridge
Host-only
```

---

## Typische Netzwerkfehler

| Fehler                                    | Mögliche Ursache                      |
| ----------------------------------------- | ------------------------------------- |
| Kein Internet                             | Gateway, DNS, Routing, Kabel, WLAN    |
| IP funktioniert, Name nicht               | DNS-Problem                           |
| Lokales Netz funktioniert, Internet nicht | Gateway oder NAT                      |
| Dienst nicht erreichbar                   | Port, Firewall, Dienststatus          |
| falsches Subnetz                          | Client und Ziel sind logisch getrennt |
| doppelte IP-Adresse                       | Adresskonflikt                        |
| DHCP gibt keine Adresse                   | DHCP-Server nicht erreichbar          |
| WLAN instabil                             | Signal, Kanal, Entfernung, Störung    |
| VM nicht erreichbar                       | NAT/Bridge falsch gewählt             |
| Docker-Container erreicht DB nicht        | falscher Hostname oder Netzwerk       |

---

## Gute Arbeitsweise bei Netzwerkproblemen

Eine gute Fehlersuche läuft Schritt für Schritt.

Beispiel:

```text
1. Hat das Gerät eine IP-Adresse?
2. Ist die Subnetzmaske korrekt?
3. Ist ein Gateway gesetzt?
4. Funktioniert Ping zum Gateway?
5. Funktioniert Ping zu einer externen IP?
6. Funktioniert DNS?
7. Ist der Zielport offen?
8. Blockiert eine Firewall?
9. Läuft der Dienst?
10. Gibt es Logs?
```

Wichtige Regel:

```text
Nicht raten. Von unten nach oben prüfen.
```

---

## Verbindung zum OSI-Modell

Das OSI-Modell hilft, Netzwerkprobleme zu strukturieren.

Vereinfacht:

| Schicht       | Beispiel                  |
| ------------- | ------------------------- |
| 1 Physisch    | Kabel, WLAN-Signal        |
| 2 Sicherung   | MAC-Adresse, Switch, VLAN |
| 3 Netzwerk    | IP, Routing               |
| 4 Transport   | TCP, UDP, Ports           |
| 5–7 Anwendung | DNS, HTTP, SSH, Anwendung |

Bei Fehlersuche kann man fragen:

```text
Ist das Kabel oder WLAN okay?
Hat das Gerät eine IP?
Funktioniert Routing?
Ist der Port erreichbar?
Antwortet der Dienst?
```

---

## FISI-Bezug

Netzwerke gehören zu den wichtigsten FISI-Themen.

In der Praxis braucht man Netzwerkverständnis für:

- Clients in Netzwerke einbinden
- IP-Konfiguration prüfen
- DHCP und DNS verstehen
- Router, Switches und Access Points einordnen
- VLANs und Netztrennung verstehen
- Serverdienste erreichbar machen
- SSH, Webdienste und Datenbanken prüfen
- Docker- und VM-Netzwerke verstehen
- Fehler systematisch analysieren
- technische Dokumentation schreiben

Ein guter FISI muss Netzwerke nicht nur auswendig kennen, sondern praktisch prüfen können.

---

## Praktische Lernziele

Nach diesem Bereich sollte man erklären können:

- was ein Netzwerk ist
- was IP-Adressen und Subnetze sind
- wofür Gateway, DNS und DHCP genutzt werden
- was Ports und Dienste sind
- wie Router und Switches grob funktionieren
- warum VLANs genutzt werden
- was NAT macht
- wie WLAN grundsätzlich funktioniert
- welche Befehle bei Netzwerkproblemen helfen
- wie man Netzwerkfehler Schritt für Schritt eingrenzt

---

## Kurze Zusammenfassung

Netzwerke verbinden IT-Systeme miteinander.

Wichtige Grundlagen sind IP-Adressen, Subnetze, Gateway, DNS, DHCP, Ports, Router, Switches, WLAN, NAT und VLANs.

Für FISI ist Netzwerkverständnis besonders wichtig, weil viele praktische Probleme mit Erreichbarkeit, Namensauflösung, IP-Konfiguration, Routing oder Ports zusammenhängen.

Dieses Kapitel bildet die Grundlage für spätere Themen wie Troubleshooting, Serverdienste, Virtualisierung, Docker, IT-Sicherheit und Home-Lab.
