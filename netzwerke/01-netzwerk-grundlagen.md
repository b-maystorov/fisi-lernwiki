# 1. Netzwerk-Grundlagen

In diesem Kapitel geht es um die Grundlagen von Netzwerken.

Ein Netzwerk verbindet Geräte miteinander, damit sie Daten austauschen können. Ohne Netzwerke könnten Clients, Server, Drucker, virtuelle Maschinen, Container, Cloud-Dienste und Anwendungen nicht sinnvoll zusammenarbeiten.

Für Fachinformatiker für Systemintegration ist Netzwerkverständnis sehr wichtig, weil viele praktische IT-Probleme mit Erreichbarkeit, IP-Adressen, DNS, DHCP, Gateways, Ports, Routing, VLANs oder Firewalls zusammenhängen.

---

## Kurz erklärt

Ein Netzwerk ist eine Verbindung zwischen mehreren Geräten.

Beispiele für Geräte in einem Netzwerk:

```text
Laptop
PC
Server
Drucker
Router
Switch
Access Point
Firewall
Smartphone
virtuelle Maschine
Docker-Container
```

Diese Geräte können über ein Netzwerk Daten austauschen.

Beispiele:

```text
Ein Client öffnet eine Webseite.
Ein Benutzer meldet sich an einem Server an.
Ein PC druckt über einen Netzwerkdrucker.
Ein Laptop verbindet sich per WLAN.
Eine VM bekommt Internet über NAT.
Ein Docker-Container verbindet sich mit einer Datenbank.
```

---

## Warum Netzwerke wichtig sind

Fast alle modernen IT-Systeme sind miteinander verbunden.

Ohne Netzwerk funktionieren viele Dinge nicht:

- Internetzugang
- E-Mail
- Webseiten
- Cloud-Dienste
- Datei-Server
- Drucker
- Datenbanken
- Remote-Zugriff
- Updates
- Monitoring
- Backup-Systeme
- Benutzeranmeldung an zentralen Systemen

Ein Netzwerk ist also nicht nur „Internet“. Es ist die Grundlage dafür, dass IT-Systeme miteinander sprechen können.

---

## Client und Server

Ein sehr wichtiges Grundprinzip ist das Client-Server-Modell.

| Begriff | Bedeutung                                          |
| ------- | -------------------------------------------------- |
| Client  | Gerät oder Programm, das einen Dienst nutzt        |
| Server  | Gerät oder Programm, das einen Dienst bereitstellt |

Beispiele:

| Client          | Server          |
| --------------- | --------------- |
| Browser         | Webserver       |
| E-Mail-Programm | Mailserver      |
| PC              | Dateiserver     |
| Adminer         | Datenbankserver |
| SSH-Client      | SSH-Server      |

Beispiel:

```text
Browser -> Webserver
```

Der Browser fragt eine Webseite an.  
Der Webserver liefert die Webseite zurück.

---

## Peer-to-Peer kurz erklärt

Nicht alle Netzwerke arbeiten streng nach Client-Server-Prinzip.

Bei Peer-to-Peer können Geräte direkt miteinander kommunizieren.

Beispiel:

```text
PC zu PC
Gerät zu Gerät
Dateifreigabe zwischen zwei Systemen
```

In Firmenumgebungen ist Client-Server aber sehr häufig, weil Dienste zentral verwaltet werden.

---

## LAN

LAN bedeutet:

```text
Local Area Network
```

Ein LAN ist ein lokales Netzwerk.

Beispiele:

```text
Heimnetzwerk
Büronetzwerk
Schulnetzwerk
Serverraum-Netzwerk
```

Typische LAN-Geräte:

```text
Switch
Router
Firewall
Clients
Server
Drucker
Access Points
```

Ein LAN ist meistens auf ein Gebäude, eine Wohnung, ein Büro oder einen Standort begrenzt.

---

## WLAN

WLAN bedeutet:

```text
Wireless Local Area Network
```

WLAN ist ein drahtloses lokales Netzwerk.

Statt Netzwerkkabel nutzt WLAN Funk.

Typische WLAN-Geräte:

```text
Access Point
WLAN-Router
Laptop
Smartphone
Tablet
IoT-Geräte
```

WLAN ist praktisch, aber anfälliger für Störungen als Kabelnetzwerke.

Typische Probleme:

```text
schlechtes Signal
falsches Passwort
überlasteter Kanal
zu große Entfernung
Störungen durch Wände
falsche Verschlüsselung
```

---

## WAN

WAN bedeutet:

```text
Wide Area Network
```

Ein WAN verbindet Netzwerke über größere Entfernungen.

Beispiele:

```text
Internet
Standortverbindung zwischen Firmengebäuden
Verbindung zwischen Zentrale und Außenstelle
```

Das Internet ist das bekannteste WAN.

In Firmen gibt es oft WAN-Verbindungen zwischen Standorten.

---

## VPN

VPN bedeutet:

```text
Virtual Private Network
```

Ein VPN baut eine verschlüsselte Verbindung über ein unsicheres Netzwerk auf.

Beispiel:

```text
Mitarbeiter zu Hause -> VPN -> Firmennetzwerk
```

Dadurch kann ein Benutzer von außen sicher auf interne Ressourcen zugreifen.

Typische VPN-Arten:

| VPN-Art        | Bedeutung                                        |
| -------------- | ------------------------------------------------ |
| Client-to-Site | einzelner Benutzer verbindet sich mit Firmennetz |
| Site-to-Site   | zwei Netzwerke werden verbunden                  |

VPN ist wichtig für Remote-Arbeit, Standortverbindungen und sichere Zugriffe.

---

## VLAN

VLAN bedeutet:

```text
Virtual Local Area Network
```

Ein VLAN trennt ein physisches Netzwerk logisch in mehrere Netzwerke.

Beispiel:

```text
VLAN 10 = Mitarbeiter
VLAN 20 = Gäste
VLAN 30 = Server
VLAN 40 = VoIP
```

VLANs helfen bei:

- Netztrennung
- Sicherheit
- Übersicht
- Broadcast-Begrenzung
- strukturierter Netzwerkplanung

Ein VLAN ist nicht einfach nur ein anderer WLAN-Name.  
Es ist eine logische Trennung auf Netzwerkebene.

---

## Netzwerkgeräte

In Netzwerken gibt es verschiedene Geräte mit unterschiedlichen Aufgaben.

| Gerät           | Aufgabe                                  |
| --------------- | ---------------------------------------- |
| Switch          | verbindet Geräte im lokalen Netzwerk     |
| Router          | verbindet verschiedene Netzwerke         |
| Firewall        | kontrolliert und filtert Datenverkehr    |
| Access Point    | stellt WLAN bereit                       |
| Modem           | verbindet mit Anschlussart des Providers |
| Server          | stellt Dienste bereit                    |
| Client          | nutzt Dienste                            |
| Patchpanel      | strukturiert Netzwerkverkabelung         |
| Netzwerkdrucker | Druckdienst im Netzwerk                  |

Diese Geräte arbeiten zusammen, damit Kommunikation möglich ist.

---

## Switch

Ein Switch verbindet Geräte im lokalen Netzwerk.

Beispiel:

```text
PC
Server
Drucker
Access Point
```

Alle diese Geräte können an einen Switch angeschlossen sein.

Ein Switch arbeitet hauptsächlich mit MAC-Adressen.

Er lernt, an welchem Port welches Gerät angeschlossen ist.

Vereinfacht:

```text
Switch merkt sich:
MAC-Adresse A ist an Port 1.
MAC-Adresse B ist an Port 2.
```

Dadurch kann er Daten gezielt weiterleiten.

---

## Router

Ein Router verbindet verschiedene Netzwerke miteinander.

Beispiel:

```text
Heimnetzwerk -> Router -> Internet
```

Der Router entscheidet, wohin Datenpakete weitergeleitet werden.

Ein Router arbeitet mit IP-Adressen.

Typische Aufgaben eines Routers:

- Netzwerke verbinden
- Standardgateway bereitstellen
- Routing durchführen
- oft NAT verwenden
- manchmal DHCP und DNS weiterleiten
- Internetzugang bereitstellen

Ein Switch verbindet Geräte im gleichen Netz.  
Ein Router verbindet verschiedene Netze.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr.

Sie entscheidet, welcher Datenverkehr erlaubt oder blockiert wird.

Beispiele:

```text
SSH erlauben
HTTP/HTTPS erlauben
Datenbankport blockieren
Zugriff aus Gastnetz verbieten
bestimmte IPs blockieren
```

Firewalls können auf verschiedenen Ebenen arbeiten:

```text
Client-Firewall
Server-Firewall
Netzwerk-Firewall
Cloud-Firewall
Router-Firewall
```

Eine Firewall ist wichtig für Sicherheit und Zugriffskontrolle.

---

## Access Point

Ein Access Point stellt WLAN bereit.

Er verbindet drahtlose Geräte mit dem kabelgebundenen Netzwerk.

Beispiel:

```text
Laptop -> WLAN -> Access Point -> Switch -> Router -> Internet
```

In kleinen Heimnetzwerken ist Access Point, Router, Switch und Firewall oft in einem Gerät kombiniert.

In Firmen sind diese Funktionen häufig getrennt.

---

## IP-Adresse

Eine IP-Adresse ist eine logische Adresse im Netzwerk.

Beispiel IPv4:

```text
192.168.1.25
```

Über die IP-Adresse kann ein Gerät im Netzwerk angesprochen werden.

Typische private IPv4-Bereiche:

```text
192.168.0.0/16
172.16.0.0/12
10.0.0.0/8
```

Private IP-Adressen werden in internen Netzwerken genutzt.

Öffentliche IP-Adressen werden im Internet genutzt.

---

## IPv4 und IPv6

Es gibt zwei wichtige IP-Versionen:

| Version | Beispiel       |
| ------- | -------------- |
| IPv4    | `192.168.1.25` |
| IPv6    | `2001:db8::1`  |

IPv4 ist noch sehr verbreitet.

IPv6 wurde entwickelt, weil IPv4-Adressen knapp wurden.

IPv6-Adressen sind länger und anders aufgebaut.

Für den Einstieg ist IPv4 oft einfacher zu verstehen, aber IPv6 wird in modernen Netzwerken immer wichtiger.

---

## MAC-Adresse

Eine MAC-Adresse ist eine Hardwareadresse einer Netzwerkschnittstelle.

Beispiel:

```text
a4:bb:6d:12:34:56
```

MAC-Adressen werden vor allem im lokalen Netzwerk verwendet.

Ein Switch arbeitet mit MAC-Adressen.

Eine IP-Adresse kann sich ändern.  
Eine MAC-Adresse gehört zur Netzwerkkarte oder Schnittstelle.

Vereinfacht:

```text
MAC-Adresse = lokale Hardwareadresse
IP-Adresse = logische Netzwerkadresse
```

---

## Subnetz

Ein Subnetz ist ein Teil eines IP-Netzwerks.

Beispiel:

```text
192.168.1.0/24
```

Das bedeutet vereinfacht:

```text
Netzwerk: 192.168.1.0
Hosts: 192.168.1.1 bis 192.168.1.254
Broadcast: 192.168.1.255
```

Subnetze helfen, Netzwerke zu planen und zu trennen.

Beispiele:

```text
192.168.10.0/24 = Büro
192.168.20.0/24 = Gäste
192.168.30.0/24 = Server
```

---

## Subnetzmaske

Die Subnetzmaske trennt Netzanteil und Hostanteil einer IP-Adresse.

Beispiel:

```text
IP-Adresse:    192.168.1.25
Subnetzmaske: 255.255.255.0
CIDR:         /24
```

Bei `/24` gehören die ersten 24 Bits zum Netzwerk.

Das ist am Anfang schwer, aber wichtig für Subnetting.

Vereinfacht:

```text
192.168.1.0/24
```

Alle Geräte mit `192.168.1.x` liegen meistens im gleichen Subnetz.

---

## Gateway

Das Standardgateway ist der Ausgang aus dem eigenen Netzwerk.

Beispiel:

```text
Client-IP: 192.168.1.25
Gateway:   192.168.1.1
```

Wenn der Client ein Ziel außerhalb seines eigenen Subnetzes erreichen möchte, schickt er die Daten an das Gateway.

Ohne Gateway kann ein Gerät oft nur lokale Geräte erreichen.

Typisches Problem:

```text
Ping zum Router funktioniert.
Internet funktioniert nicht.
```

Dann kann Gateway, DNS, NAT oder Routing das Problem sein.

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

Menschen merken sich Namen besser als IP-Adressen.

Computer brauchen aber IP-Adressen, um Ziele zu erreichen.

Typischer Test:

```bash
ping 8.8.8.8
ping github.com
```

Wenn die IP funktioniert, aber der Name nicht, liegt oft ein DNS-Problem vor.

---

## DHCP

DHCP bedeutet:

```text
Dynamic Host Configuration Protocol
```

DHCP vergibt Netzwerkkonfiguration automatisch.

Typische DHCP-Informationen:

```text
IP-Adresse
Subnetzmaske
Gateway
DNS-Server
Lease-Zeit
```

Ohne DHCP müsste man diese Werte manuell eintragen.

Typischer Fehler:

```text
Gerät bekommt keine gültige IP-Adresse.
```

Dann sollte man prüfen:

```text
DHCP-Server erreichbar?
Netzwerk verbunden?
VLAN korrekt?
WLAN verbunden?
Adressbereich voll?
```

---

## Port

Ein Port identifiziert einen Dienst auf einem Gerät.

Eine IP-Adresse sagt:

```text
Welches Gerät?
```

Ein Port sagt:

```text
Welcher Dienst auf diesem Gerät?
```

Beispiele:

| Port | Dienst                         |
| ---- | ------------------------------ |
| 22   | SSH                            |
| 53   | DNS                            |
| 80   | HTTP                           |
| 443  | HTTPS                          |
| 3306 | MySQL                          |
| 5432 | PostgreSQL                     |
| 8080 | häufig Web-GUI oder Testdienst |

Beispiel:

```text
192.168.1.10:22
```

Das bedeutet:

```text
SSH-Dienst auf 192.168.1.10
```

---

## TCP und UDP

TCP und UDP sind wichtige Transportprotokolle.

| Protokoll | Bedeutung                                            |
| --------- | ---------------------------------------------------- |
| TCP       | verbindungsorientiert und zuverlässig                |
| UDP       | verbindungslos und schneller, aber weniger Kontrolle |

Beispiele:

| Dienst         | Typisch     |
| -------------- | ----------- |
| HTTP/HTTPS     | TCP         |
| SSH            | TCP         |
| DNS            | UDP und TCP |
| DHCP           | UDP         |
| VoIP/Streaming | oft UDP     |

TCP prüft stärker, ob Daten angekommen sind.  
UDP ist einfacher und schneller, aber ohne dieselbe Absicherung.

---

## HTTP und HTTPS

HTTP und HTTPS sind Protokolle für Webseiten.

| Protokoll | Port | Bedeutung                 |
| --------- | ---- | ------------------------- |
| HTTP      | 80   | unverschlüsselte Webseite |
| HTTPS     | 443  | verschlüsselte Webseite   |

Heute sollte für echte Webseiten fast immer HTTPS genutzt werden.

Beispiel:

```text
https://github.com
```

HTTPS schützt die Verbindung zwischen Client und Server.

---

## SSH

SSH bedeutet:

```text
Secure Shell
```

SSH wird genutzt, um sich sicher auf entfernte Systeme zu verbinden.

Beispiel:

```bash
ssh user@server
```

Standardport:

```text
22
```

SSH ist für FISI sehr wichtig, weil viele Server über SSH administriert werden.

Typische SSH-Probleme:

```text
falsche IP
Port 22 blockiert
SSH-Dienst läuft nicht
falscher Benutzer
falscher Schlüssel
Firewall blockiert
```

---

## Datenpakete

Daten werden im Netzwerk in Pakete aufgeteilt.

Ein Paket enthält vereinfacht:

```text
Absender
Empfänger
Protokoll
Nutzdaten
Kontrollinformationen
```

Beispiel:

Wenn eine Webseite geladen wird, werden viele Pakete zwischen Client und Server übertragen.

Das passiert sehr schnell und meistens unsichtbar für den Benutzer.

---

## OSI-Modell

Das OSI-Modell ist ein theoretisches Modell für Netzwerkkommunikation.

Es besteht aus sieben Schichten.

| Schicht | Name           | Beispiel                 |
| ------- | -------------- | ------------------------ |
| 7       | Anwendung      | HTTP, DNS, SSH           |
| 6       | Darstellung    | Verschlüsselung, Formate |
| 5       | Sitzung        | Sitzungen/Verbindungen   |
| 4       | Transport      | TCP, UDP                 |
| 3       | Netzwerk       | IP, Routing              |
| 2       | Sicherung      | MAC, Switch, VLAN        |
| 1       | Bitübertragung | Kabel, Funk, Stecker     |

Für die Praxis hilft das OSI-Modell bei Fehlersuche.

---

## OSI-Modell praktisch denken

Bei Netzwerkproblemen kann man vereinfacht von unten nach oben prüfen.

```text
1. Kabel oder WLAN okay?
2. Netzwerkschnittstelle aktiv?
3. IP-Adresse vorhanden?
4. Gateway erreichbar?
5. DNS funktioniert?
6. Port erreichbar?
7. Dienst antwortet?
```

Beispiel:

```text
Wenn kein Kabel verbunden ist, bringt DNS-Prüfung nichts.
```

Deshalb ist strukturierte Fehlersuche wichtig.

---

## Netzwerkkommunikation einfach erklärt

Beispiel: Ein Client öffnet eine Webseite.

```text
1. Benutzer gibt github.com ein.
2. Client fragt DNS nach der IP-Adresse.
3. DNS liefert eine IP-Adresse zurück.
4. Client baut Verbindung zum Webserver auf.
5. Verbindung läuft über Router und Internet.
6. Server antwortet.
7. Browser zeigt Webseite an.
```

Dabei wirken mehrere Themen zusammen:

```text
DNS
IP
Gateway
Routing
TCP
HTTPS
Firewall
Serverdienst
```

---

## Lokales Netzwerk und Internet

Ein lokales Netzwerk ist vom Internet getrennt.

Beispiel Heimnetz:

```text
192.168.1.0/24
```

Das Internet nutzt öffentliche IP-Adressen.

Damit private Geräte ins Internet kommen, wird meistens NAT genutzt.

Vereinfacht:

```text
Private IP -> Router/NAT -> öffentliche IP -> Internet
```

So können viele Geräte eine öffentliche Internetverbindung gemeinsam nutzen.

---

## NAT kurz erklärt

NAT bedeutet:

```text
Network Address Translation
```

NAT übersetzt private IP-Adressen in eine öffentliche IP-Adresse.

Beispiel:

```text
Laptop: 192.168.1.25
Router öffentlich: 84.x.x.x
```

Der Router merkt sich, welche interne Verbindung zu welcher externen Verbindung gehört.

NAT ist sehr verbreitet in Heim- und Firmennetzwerken.

---

## Broadcast kurz erklärt

Ein Broadcast ist eine Nachricht an alle Geräte im lokalen Netzwerk.

Beispiel:

```text
Wer hat diese IP-Adresse?
```

Broadcasts werden unter anderem bei ARP genutzt.

Zu viele Broadcasts können Netzwerke belasten.

VLANs und Subnetze helfen, Broadcast-Bereiche zu begrenzen.

---

## ARP kurz erklärt

ARP bedeutet:

```text
Address Resolution Protocol
```

ARP verbindet IP-Adressen mit MAC-Adressen im lokalen Netzwerk.

Beispiel:

```text
Welche MAC-Adresse gehört zu 192.168.1.10?
```

Ein Gerät braucht die MAC-Adresse, um im lokalen Netzwerk direkt zu kommunizieren.

Unter Linux kann man Nachbarn prüfen mit:

```bash
ip neigh
```

---

## Netzwerk unter Linux prüfen

Wichtige Befehle:

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

Bedeutung:

| Befehl       | Aufgabe                      |
| ------------ | ---------------------------- |
| `ip a`       | IP-Adressen anzeigen         |
| `ip route`   | Routing und Gateway anzeigen |
| `ping`       | Erreichbarkeit testen        |
| `ss -tulpen` | offene Ports prüfen          |
| `dig`        | DNS-Abfrage testen           |
| `traceroute` | Weg zum Ziel prüfen          |
| `nmcli`      | NetworkManager prüfen        |

Diese Befehle sind sehr wichtig für FISI-Praxis.

---

## Einfache Netzwerk-Checkliste

Bei Netzwerkproblemen kann man so starten:

```text
Ist das Gerät verbunden?
Hat es eine IP-Adresse?
Ist die IP im richtigen Netz?
Ist das Gateway gesetzt?
Kann das Gateway angepingt werden?
Funktioniert Ping auf eine externe IP?
Funktioniert DNS?
Ist der Zielport offen?
Läuft der Dienst?
Blockiert eine Firewall?
```

Diese Reihenfolge hilft, Probleme einzugrenzen.

---

## Beispiel: Kein Internet

Problem:

```text
Laptop hat kein Internet.
```

Prüfung:

```bash
ip a
ip route
ping 192.168.1.1
ping 8.8.8.8
ping github.com
```

Mögliche Ergebnisse:

| Ergebnis                             | Hinweis                                           |
| ------------------------------------ | ------------------------------------------------- |
| keine IP-Adresse                     | DHCP oder Verbindung prüfen                       |
| Gateway nicht erreichbar             | lokales Netzwerkproblem                           |
| 8.8.8.8 erreichbar, github.com nicht | DNS-Problem                                       |
| nichts erreichbar                    | Verbindung, Gateway, Firewall oder Routing prüfen |

---

## Beispiel: Server nicht per SSH erreichbar

Problem:

```text
ssh user@192.168.1.50 funktioniert nicht.
```

Prüfung:

```bash
ping 192.168.1.50
ssh user@192.168.1.50
ss -tulpen | grep 22
```

Auf dem Server prüfen:

```bash
systemctl status ssh
sudo ufw status
ip a
```

Mögliche Ursachen:

```text
Server hat falsche IP
SSH-Dienst läuft nicht
Firewall blockiert Port 22
Benutzername falsch
Netzwerk nicht erreichbar
```

---

## Typische Fehler

| Fehler                             | Problem                                            |
| ---------------------------------- | -------------------------------------------------- |
| IP und DNS verwechseln             | Name und Adresse sind nicht dasselbe               |
| Gateway vergessen                  | kein Zugriff auf andere Netzwerke                  |
| falsches Subnetz                   | Geräte sehen sich nicht direkt                     |
| Port nicht geprüft                 | Dienst läuft vielleicht, ist aber nicht erreichbar |
| DNS nicht getestet                 | IP geht, Name geht nicht                           |
| Firewall ignoriert                 | Verbindung wird blockiert                          |
| WLAN-Signal überschätzt            | Verbindung instabil                                |
| NAT und Bridge bei VMs verwechselt | VM ist anders erreichbar als erwartet              |
| `localhost` falsch verstanden      | zeigt immer auf das eigene System                  |
| ohne Struktur gesucht              | Fehleranalyse dauert länger                        |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise im Netzwerkbereich:

1. Problem genau beschreiben
2. lokale Verbindung prüfen
3. IP-Adresse prüfen
4. Gateway prüfen
5. DNS prüfen
6. Zielsystem prüfen
7. Port prüfen
8. Dienststatus prüfen
9. Firewall prüfen
10. Ergebnisse dokumentieren

Wichtig ist:

```text
Nicht direkt alles ändern.
Erst prüfen, dann gezielt handeln.
```

---

## FISI-Bezug

Für FISI gehören Netzwerkgrundlagen zum Kernwissen.

In der Praxis braucht man sie für:

- Clients ins Netzwerk einbinden
- Server erreichbar machen
- Druckerprobleme analysieren
- DNS- und DHCP-Probleme erkennen
- VLANs verstehen
- VPN-Verbindungen einordnen
- Router und Switches grundlegend verstehen
- Firewall-Probleme prüfen
- Docker- und VM-Netzwerke verstehen
- Home-Lab aufbauen
- technische Dokumentation schreiben

Ein FISI muss Netzwerke nicht nur theoretisch kennen, sondern praktisch testen und erklären können.

---

## Kurze Zusammenfassung

Ein Netzwerk verbindet Geräte, damit sie Daten austauschen können.

Wichtige Grundlagen sind Client, Server, LAN, WLAN, WAN, VPN, VLAN, Switch, Router, Firewall, IP-Adresse, MAC-Adresse, Subnetz, Gateway, DNS, DHCP, Ports, TCP, UDP und NAT.

Das OSI-Modell hilft, Netzwerkprobleme strukturiert zu prüfen.

Für FISI ist Netzwerkverständnis besonders wichtig, weil viele Fehler in echten IT-Umgebungen mit Erreichbarkeit, Namensauflösung, IP-Konfiguration, Routing, Ports oder Firewalls zusammenhängen.
