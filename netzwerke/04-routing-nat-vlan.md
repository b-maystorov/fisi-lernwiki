# 4. Routing, NAT und VLAN

In diesem Kapitel geht es um Routing, NAT und VLANs.

Diese drei Themen sind wichtig, wenn Netzwerke nicht nur einfach verbunden sind, sondern sauber getrennt, weitergeleitet und ins Internet angebunden werden sollen.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr wichtig, weil viele praktische Netzwerkprobleme mit falschen Routen, NAT, Gateways, VLANs oder Firewall-Regeln zusammenhängen.

---

## Kurz erklärt

| Thema   | Bedeutung                                   |
| ------- | ------------------------------------------- |
| Routing | Weiterleitung von Daten zwischen Netzwerken |
| NAT     | Übersetzung von IP-Adressen                 |
| VLAN    | logische Trennung innerhalb eines Netzwerks |

Ein einfaches Beispiel:

```text
Client-Netz -> Router/Firewall -> Internet
```

Oder in einer Firma:

```text
VLAN 10 Mitarbeiter
VLAN 20 Gäste
VLAN 30 Server
VLAN 40 VoIP
```

Diese Netze müssen getrennt, aber teilweise kontrolliert miteinander verbunden werden.

---

## Warum Routing wichtig ist

Geräte im gleichen Subnetz können direkt miteinander kommunizieren.

Beispiel:

```text
192.168.1.20/24
192.168.1.50/24
```

Beide liegen im Netzwerk:

```text
192.168.1.0/24
```

Wenn ein Gerät aber ein anderes Netzwerk erreichen will, braucht es Routing.

Beispiel:

```text
Client: 192.168.10.25/24
Server: 192.168.30.10/24
```

Diese Geräte liegen in unterschiedlichen Netzen.

Daten müssen über einen Router oder Layer-3-Switch weitergeleitet werden.

---

## Routing einfach erklärt

Routing bedeutet:

```text
Ein Gerät entscheidet, über welchen Weg ein Datenpaket zum Ziel kommt.
```

Ein Router verbindet verschiedene Netzwerke.

Beispiel:

```text
192.168.10.0/24 -> Router -> 192.168.30.0/24
```

Der Router hat in beiden Netzen eine Adresse.

Beispiel:

```text
Router Interface 1: 192.168.10.1
Router Interface 2: 192.168.30.1
```

Clients nutzen den Router als Gateway.

---

## Standardgateway

Das Standardgateway ist der Weg aus dem eigenen Netzwerk heraus.

Beispiel Client:

```text
IP-Adresse: 192.168.10.25
Netz:       192.168.10.0/24
Gateway:    192.168.10.1
```

Wenn der Client ein Ziel außerhalb von `192.168.10.0/24` erreichen möchte, sendet er die Daten an:

```text
192.168.10.1
```

Ohne korrektes Gateway funktioniert oft nur das eigene lokale Netz.

---

## Routingtabelle

Ein Gerät nutzt eine Routingtabelle, um zu entscheiden, wohin Pakete gehen.

Unter Linux:

```bash
ip route
```

Beispiel:

```text
default via 192.168.1.1 dev wlan0
192.168.1.0/24 dev wlan0
```

Bedeutung:

| Eintrag                    | Bedeutung                               |
| -------------------------- | --------------------------------------- |
| `192.168.1.0/24 dev wlan0` | lokales Netzwerk über Interface `wlan0` |
| `default via 192.168.1.1`  | alles Unbekannte geht zum Gateway       |

Die Default Route ist besonders wichtig für Internetzugang.

---

## Lokale Route und Default Route

Eine lokale Route beschreibt direkt erreichbare Netze.

Beispiel:

```text
192.168.1.0/24 dev wlan0
```

Das bedeutet:

```text
Dieses Netz ist direkt über wlan0 erreichbar.
```

Eine Default Route beschreibt den Standardweg.

Beispiel:

```text
default via 192.168.1.1
```

Das bedeutet:

```text
Wenn kein genauerer Weg bekannt ist, sende an 192.168.1.1.
```

---

## Statisches Routing

Statisches Routing bedeutet:

```text
Routen werden manuell eingetragen.
```

Beispiel:

```bash
sudo ip route add 192.168.30.0/24 via 192.168.10.1
```

Das bedeutet:

```text
Um das Netz 192.168.30.0/24 zu erreichen, nutze 192.168.10.1 als nächsten Router.
```

Statische Routen sind einfach, aber müssen manuell gepflegt werden.

Sinnvoll bei:

- kleinen Netzwerken
- Laborumgebungen
- einzelnen Sonderrouten
- einfachen Standortverbindungen

---

## Dynamisches Routing

Dynamisches Routing bedeutet:

```text
Router tauschen Routen automatisch aus.
```

Dafür gibt es Routing-Protokolle.

Beispiele:

```text
OSPF
BGP
RIP
EIGRP
```

Für den FISI-Einstieg ist wichtig:

```text
Statische Routen werden manuell gepflegt.
Dynamische Routen werden durch Routing-Protokolle gelernt.
```

In großen Netzwerken wird dynamisches Routing wichtiger.

---

## Route prüfen

Wichtige Befehle unter Linux:

```bash
ip route
ping 192.168.1.1
traceroute github.com
```

Falls `traceroute` nicht installiert ist:

```bash
sudo apt install traceroute
```

`traceroute` zeigt, über welche Zwischenstationen ein Ziel erreicht wird.

Beispiel:

```bash
traceroute github.com
```

Das hilft, Routingprobleme einzugrenzen.

---

## Routingproblem erkennen

Typische Hinweise:

```text
lokale Geräte erreichbar
andere Netze nicht erreichbar
Internet nicht erreichbar
Gateway nicht erreichbar
traceroute bricht früh ab
falsche Route in ip route
```

Prüfreihenfolge:

```text
1. IP-Adresse prüfen
2. Subnetzmaske prüfen
3. Gateway prüfen
4. Gateway anpingen
5. Routingtabelle prüfen
6. Zielnetz prüfen
7. Firewall prüfen
```

---

## NAT

NAT bedeutet:

```text
Network Address Translation
```

NAT übersetzt IP-Adressen.

Typisches Beispiel:

```text
private IP-Adresse -> öffentliche IP-Adresse
```

Viele Geräte im Heimnetz haben private IP-Adressen:

```text
192.168.1.25
192.168.1.26
192.168.1.27
```

Der Router hat nach außen eine öffentliche IP-Adresse.

NAT sorgt dafür, dass die privaten Geräte trotzdem ins Internet können.

---

## Warum NAT genutzt wird

Private IP-Adressen sind im Internet nicht direkt erreichbar.

Beispiele private IPs:

```text
192.168.0.0/16
172.16.0.0/12
10.0.0.0/8
```

Diese Adressen werden intern genutzt.

Damit ein Client mit privater IP ins Internet kommt, übersetzt der Router die Adresse.

Vereinfacht:

```text
192.168.1.25 -> Router/NAT -> öffentliche IP -> Internet
```

---

## PAT / Masquerading

Oft wird nicht nur die IP-Adresse übersetzt, sondern auch der Port.

Das nennt man häufig:

```text
PAT = Port Address Translation
```

oder bei Linux oft:

```text
Masquerading
```

Dadurch können viele interne Geräte gleichzeitig über eine öffentliche IP-Adresse ins Internet.

Vereinfacht merkt sich der Router:

```text
Interner Client 192.168.1.25 mit Port X gehört zu externer Verbindung Y.
```

Wenn die Antwort aus dem Internet zurückkommt, leitet der Router sie an den richtigen internen Client weiter.

---

## NAT Beispiel

Client:

```text
192.168.1.25
```

Router intern:

```text
192.168.1.1
```

Router extern:

```text
84.x.x.x
```

Ablauf:

```text
1. Client sendet Anfrage ins Internet.
2. Router ersetzt private Quell-IP durch öffentliche IP.
3. Internetserver antwortet an öffentliche IP.
4. Router erkennt Verbindung.
5. Router leitet Antwort zurück an 192.168.1.25.
```

Für den Client wirkt es so, als hätte er direkt Internet.

---

## NAT und eingehende Verbindungen

NAT funktioniert für ausgehende Verbindungen sehr gut.

Eingehende Verbindungen sind schwieriger.

Beispiel:

```text
Jemand aus dem Internet möchte auf einen Server im Heimnetz zugreifen.
```

Der Router weiß nicht automatisch, an welches interne Gerät die Anfrage gehen soll.

Dafür braucht man Portweiterleitung.

---

## Portweiterleitung

Portweiterleitung bedeutet:

```text
Ein Port auf dem Router wird an ein internes Gerät weitergeleitet.
```

Beispiel:

```text
Router öffentlich Port 2222 -> interner Server 192.168.1.50 Port 22
```

Dann kann man von außen vielleicht verbinden mit:

```text
öffentliche-ip:2222
```

und landet intern auf:

```text
192.168.1.50:22
```

Wichtig:

Portweiterleitungen sollten sehr bewusst gesetzt werden, weil sie Dienste von außen erreichbar machen.

---

## NAT und Sicherheit

NAT ist keine vollständige Sicherheitslösung.

Es versteckt interne Geräte etwas, aber ersetzt keine Firewall.

Wichtig:

```text
NAT ≠ Firewall
```

Sicherheitsregeln:

- nur notwendige Ports weiterleiten
- keine Datenbankports unnötig veröffentlichen
- SSH nicht leichtfertig ins Internet öffnen
- starke Passwörter oder Schlüssel verwenden
- Firewall-Regeln prüfen
- Logs beobachten
- Updates einspielen

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

Obwohl Geräte am gleichen Switch hängen können, sind sie logisch getrennt.

Ohne Routing können Geräte in verschiedenen VLANs nicht direkt miteinander kommunizieren.

---

## Warum VLANs genutzt werden

VLANs helfen bei:

- Netztrennung
- Sicherheit
- Übersicht
- weniger Broadcasts
- strukturierter Planung
- Trennung von Gästen und internen Geräten
- Trennung von Servern, Clients und Telefonie
- bessere Kontrolle über Firewall-Regeln

Beispiel:

```text
Gäste-WLAN soll ins Internet.
Gäste-WLAN soll nicht auf interne Server.
```

Dafür ist ein eigenes VLAN sinnvoll.

---

## VLAN und Subnetz

Sehr häufig bekommt jedes VLAN ein eigenes Subnetz.

Beispiel:

| VLAN    | Bereich     | Subnetz           |
| ------- | ----------- | ----------------- |
| VLAN 10 | Mitarbeiter | `192.168.10.0/24` |
| VLAN 20 | Gäste       | `192.168.20.0/24` |
| VLAN 30 | Server      | `192.168.30.0/24` |
| VLAN 40 | VoIP        | `192.168.40.0/24` |

Das macht die Struktur klar.

Merke:

```text
VLAN = logische Trennung auf Layer 2
Subnetz = IP-Bereich auf Layer 3
```

In der Praxis werden beide oft gemeinsam geplant.

---

## Access Port

Ein Access Port gehört normalerweise zu genau einem VLAN.

Beispiel:

```text
Switch-Port 5 -> VLAN 10
```

Ein normaler PC hängt meistens an einem Access Port.

Der PC merkt vom VLAN oft nichts direkt.

Er bekommt einfach eine IP-Adresse aus dem passenden Netz.

Beispiel:

```text
PC an VLAN 10 -> IP 192.168.10.25
```

---

## Trunk Port

Ein Trunk Port transportiert mehrere VLANs über eine Verbindung.

Beispiel:

```text
Switch -> Switch
Switch -> Router
Switch -> Access Point
```

Ein Trunk kann mehrere VLANs tragen:

```text
VLAN 10
VLAN 20
VLAN 30
```

Dafür werden VLAN-Tags genutzt.

Trunks sind wichtig, wenn mehrere VLANs über ein Kabel weitergeleitet werden sollen.

---

## VLAN-Tagging

Bei VLAN-Tagging wird ein Ethernet-Frame mit einer VLAN-ID markiert.

Standard dafür ist:

```text
802.1Q
```

Ein Trunk-Port erkennt anhand des Tags, zu welchem VLAN der Datenverkehr gehört.

Ein normaler Access-Port sendet an den Client meistens untagged Traffic.

Vereinfacht:

```text
Access Port = ein VLAN, für normales Endgerät
Trunk Port = mehrere VLANs, für Netzwerkgeräte
```

---

## Inter-VLAN-Routing

Geräte in verschiedenen VLANs können nicht einfach direkt miteinander kommunizieren.

Beispiel:

```text
VLAN 10: 192.168.10.0/24
VLAN 30: 192.168.30.0/24
```

Wenn ein Client aus VLAN 10 einen Server in VLAN 30 erreichen soll, braucht man Routing.

Das nennt man:

```text
Inter-VLAN-Routing
```

Das kann erfolgen über:

```text
Router
Layer-3-Switch
Firewall
```

---

## Router-on-a-Stick

Router-on-a-Stick ist eine Methode für Inter-VLAN-Routing.

Dabei hat ein Router eine physische Verbindung zum Switch, aber mehrere logische Subinterfaces.

Beispiel:

```text
Router eth0.10 -> VLAN 10
Router eth0.20 -> VLAN 20
Router eth0.30 -> VLAN 30
```

Die Verbindung zwischen Switch und Router ist ein Trunk.

Das ist ein klassisches Lernbeispiel für VLAN-Routing.

---

## VLAN und Firewall

Nur weil Routing zwischen VLANs möglich ist, heißt das nicht, dass alles erlaubt sein sollte.

Eine Firewall kann Regeln setzen.

Beispiel:

```text
VLAN 10 Mitarbeiter darf auf Server-VLAN zugreifen.
VLAN 20 Gäste darf nur ins Internet.
VLAN 20 Gäste darf nicht auf Server-VLAN.
VLAN 30 Server darf nur notwendige Dienste anbieten.
```

So entsteht kontrollierte Kommunikation.

VLANs trennen Netze.  
Firewall-Regeln kontrollieren Zugriffe.

---

## Beispiel VLAN-Plan

Ein einfacher VLAN-Plan:

| VLAN | Name       | Subnetz           | Zweck                   |
| ---- | ---------- | ----------------- | ----------------------- |
| 10   | Clients    | `192.168.10.0/24` | Mitarbeitergeräte       |
| 20   | Guests     | `192.168.20.0/24` | Gäste-WLAN              |
| 30   | Servers    | `192.168.30.0/24` | Serverdienste           |
| 40   | Management | `192.168.40.0/24` | Switches, APs, Firewall |
| 50   | VoIP       | `192.168.50.0/24` | Telefone                |

So eine Tabelle ist wichtig für Dokumentation und Fehlersuche.

---

## VLAN und DHCP

Jedes VLAN braucht normalerweise eigene DHCP-Einstellungen.

Beispiel:

```text
VLAN 10 -> DHCP-Bereich 192.168.10.100-200
VLAN 20 -> DHCP-Bereich 192.168.20.100-200
VLAN 30 -> keine normalen DHCP-Clients
```

Wenn der DHCP-Server nicht direkt im VLAN liegt, braucht man oft DHCP Relay.

Beispiel:

```text
Client in VLAN 20
DHCP-Server in VLAN 10
Router/Firewall leitet DHCP-Anfrage weiter
```

Ohne DHCP Relay bekommen Clients in anderen VLANs eventuell keine IP-Adresse.

---

## VLAN und WLAN

WLAN-Netze können mit VLANs verbunden werden.

Beispiel:

| SSID       | VLAN    | Zweck       |
| ---------- | ------- | ----------- |
| Firma-WLAN | VLAN 10 | Mitarbeiter |
| Gast-WLAN  | VLAN 20 | Gäste       |
| IoT-WLAN   | VLAN 60 | Geräte      |

Ein Access Point hängt dafür oft an einem Trunk-Port.

Der Access Point ordnet dann verschiedene SSIDs unterschiedlichen VLANs zu.

---

## VLAN-Fehler erkennen

Typische VLAN-Probleme:

```text
Client bekommt keine IP-Adresse
Client landet im falschen Netz
Gastnetz erreicht interne Server
Server ist aus Client-Netz nicht erreichbar
Access Point gibt falsches VLAN aus
Trunk erlaubt VLAN nicht
Switch-Port ist im falschen VLAN
DHCP Relay fehlt
```

Prüfen sollte man:

```text
Switch-Port-Konfiguration
Access oder Trunk
VLAN-ID
DHCP-Bereich
Gateway im VLAN
Firewall-Regeln
Routing zwischen VLANs
```

---

## Routing und VLAN zusammen

VLANs trennen Netzwerke logisch.

Routing verbindet Netzwerke wieder kontrolliert.

Beispiel:

```text
VLAN 10 Clients -> VLAN 30 Server
```

Dafür braucht man:

```text
Gateway für VLAN 10
Gateway für VLAN 30
Routing zwischen den VLANs
Firewall-Regeln
passende IP-Konfiguration
```

Ohne Routing bleiben VLANs getrennt.

Mit Routing und Firewall kann man gezielte Kommunikation erlauben.

---

## NAT und VLAN zusammen

In Firmen oder Home-Labs kann jedes VLAN über NAT ins Internet gehen.

Beispiel:

```text
VLAN 10 Clients -> Firewall/NAT -> Internet
VLAN 20 Gäste -> Firewall/NAT -> Internet
VLAN 30 Server -> Firewall/NAT -> Internet
```

Die Firewall kann dabei Regeln setzen.

Beispiel:

```text
Gäste dürfen ins Internet.
Gäste dürfen nicht in VLAN 30.
Server dürfen Updates aus dem Internet laden.
```

---

## Linux Routing prüfen

Wichtige Befehle:

```bash
ip route
ip a
ping gateway-ip
traceroute ziel
```

Beispiel:

```bash
ip route
```

zeigt:

```text
default via 192.168.1.1 dev wlan0
```

Gateway testen:

```bash
ping 192.168.1.1
```

Zielweg prüfen:

```bash
traceroute github.com
```

---

## Ports und Routing unterscheiden

Routing entscheidet, ob ein Zielnetz erreichbar ist.

Ports entscheiden, ob ein Dienst auf einem Ziel erreichbar ist.

Beispiel:

```bash
ping 192.168.30.10
```

zeigt nur grob, ob der Host erreichbar ist.

Ein Dienst kann trotzdem blockiert sein.

Port prüfen:

```bash
ss -tulpen
```

oder von einem anderen System:

```bash
nc -vz 192.168.30.10 22
```

Falls `nc` nicht installiert ist:

```bash
sudo apt install netcat-openbsd
```

---

## Firewall nicht vergessen

Auch wenn Routing korrekt ist, kann eine Firewall Verkehr blockieren.

Beispiel:

```text
Client erreicht Server per Ping.
SSH auf Port 22 funktioniert nicht.
```

Mögliche Ursachen:

```text
SSH-Dienst läuft nicht
Firewall blockiert Port 22
Server hört nicht auf Port 22
falsche IP
Routing nur teilweise korrekt
```

Unter Linux prüfen:

```bash
sudo ufw status
ss -tulpen
systemctl status ssh
```

---

## Beispiel: Client erreicht Server-VLAN nicht

Problem:

```text
Client in VLAN 10 erreicht Server in VLAN 30 nicht.
```

Prüfung:

```text
Client-IP korrekt?
Client-Gateway korrekt?
Server-IP korrekt?
Server-Gateway korrekt?
Routing zwischen VLANs aktiv?
Firewall-Regel erlaubt Zugriff?
Switch-Port im richtigen VLAN?
Trunk erlaubt VLAN 10 und 30?
```

Mögliche Befehle:

```bash
ip a
ip route
ping gateway
ping server-ip
traceroute server-ip
```

---

## Beispiel: Gastnetz soll nur Internet

Ziel:

```text
Gäste sollen Internet haben, aber keine internen Server erreichen.
```

Möglicher Aufbau:

```text
VLAN 20 Gäste: 192.168.20.0/24
VLAN 30 Server: 192.168.30.0/24
```

Regeln:

```text
VLAN 20 -> Internet erlauben
VLAN 20 -> VLAN 30 blockieren
VLAN 20 -> Management blockieren
```

Das ist ein typischer Sicherheitsfall.

VLANs trennen.  
Firewall-Regeln kontrollieren.

---

## Typische Fehler

| Fehler                        | Problem                                     |
| ----------------------------- | ------------------------------------------- |
| Gateway fehlt                 | andere Netze nicht erreichbar               |
| falsche Route                 | Pakete gehen zum falschen Router            |
| Routing und DNS verwechselt   | Name geht nicht, Route aber vielleicht okay |
| NAT als Firewall verstanden   | Sicherheitsrisiko                           |
| Portweiterleitung ohne Schutz | Dienst von außen erreichbar                 |
| Access Port im falschen VLAN  | Client landet im falschen Netz              |
| Trunk erlaubt VLAN nicht      | VLAN kommt nicht weiter                     |
| VLAN ohne passendes Subnetz   | Planung unklar                              |
| DHCP Relay fehlt              | Clients bekommen keine IP                   |
| Firewall-Regeln vergessen     | Routing geht, Zugriff trotzdem blockiert    |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Routing-, NAT- und VLAN-Themen:

1. Netzplan prüfen
2. IP-Adresse und Subnetz prüfen
3. Gateway prüfen
4. Routingtabelle ansehen
5. Zielnetz testen
6. VLAN-Zuordnung prüfen
7. Access/Trunk prüfen
8. DHCP-Bereich prüfen
9. NAT-Regeln prüfen
10. Firewall-Regeln prüfen
11. Ergebnisse dokumentieren

Wichtig:

```text
Routing, NAT, VLAN und Firewall getrennt denken.
```

Sie hängen zusammen, sind aber nicht dasselbe.

---

## Praktische Beispiele

### Beispiel 1: Routingtabelle anzeigen

```bash
ip route
```

### Beispiel 2: Gateway testen

```bash
ping 192.168.1.1
```

### Beispiel 3: Weg zum Ziel prüfen

```bash
traceroute github.com
```

### Beispiel 4: Port prüfen

```bash
nc -vz 192.168.30.10 22
```

---

## FISI-Bezug

Für FISI sind Routing, NAT und VLANs wichtige Praxisthemen.

Man braucht sie für:

- Clients in verschiedene Netze einbinden
- VLAN-Strukturen verstehen
- Gäste-Netze trennen
- Server-Netze absichern
- Routingprobleme analysieren
- Internetzugang über NAT verstehen
- Portweiterleitungen einschätzen
- Firewall-Regeln nachvollziehen
- Home-Lab-Netze planen
- VM- und Docker-Netzwerke besser verstehen
- Netzwerkdokumentation lesen und erstellen

Ein guter FISI versteht nicht nur, dass „das Internet geht“, sondern kann erklären, über welches Gateway, welche Route, welches VLAN und welche Regeln die Kommunikation läuft.

---

## Kurze Zusammenfassung

Routing leitet Daten zwischen verschiedenen Netzwerken weiter.

NAT übersetzt IP-Adressen, meistens private interne Adressen zu einer öffentlichen Adresse für Internetzugang.

VLANs trennen ein physisches Netzwerk logisch in mehrere Netzwerke.

Access Ports gehören normalerweise zu einem VLAN. Trunk Ports transportieren mehrere VLANs.

Für Kommunikation zwischen VLANs braucht man Inter-VLAN-Routing über Router, Layer-3-Switch oder Firewall.

Für FISI sind diese Themen wichtig, weil viele echte Netzwerkprobleme mit Routing, NAT, VLAN-Zuordnung, DHCP, Gateway oder Firewall-Regeln zusammenhängen.
