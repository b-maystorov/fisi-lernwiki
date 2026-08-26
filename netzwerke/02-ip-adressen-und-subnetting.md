# 2. IP-Adressen und Subnetting

In diesem Kapitel geht es um IP-Adressen und Subnetting.

IP-Adressen sind eine der wichtigsten Grundlagen in Netzwerken. Sie sorgen dafür, dass Geräte logisch im Netzwerk erreichbar sind. Subnetting hilft dabei, Netzwerke zu planen, zu trennen und übersichtlich zu strukturieren.

Für Fachinformatiker für Systemintegration ist dieses Thema besonders wichtig, weil viele praktische Fehler mit falschen IP-Adressen, falscher Subnetzmaske, falschem Gateway oder falsch geplanten Netzbereichen zusammenhängen.

---

## Kurz erklärt

Eine IP-Adresse ist eine logische Adresse eines Geräts im Netzwerk.

Beispiel:

```text
192.168.1.25
```

Ein Subnetz ist ein Teilbereich eines IP-Netzwerks.

Beispiel:

```text
192.168.1.0/24
```

Das bedeutet vereinfacht:

```text
Netzwerkadresse: 192.168.1.0
nutzbare Hosts: 192.168.1.1 bis 192.168.1.254
Broadcast:       192.168.1.255
Subnetzmaske:    255.255.255.0
```

---

## Warum IP-Adressen gebraucht werden

Geräte brauchen Adressen, damit sie miteinander kommunizieren können.

Beispiele:

```text
Laptop möchte Server erreichen.
Client möchte Webseite öffnen.
VM möchte ins Internet.
Docker-Container möchte Datenbank erreichen.
Drucker soll im Netzwerk erreichbar sein.
```

Ohne IP-Adresse weiß ein Gerät nicht, wohin es Daten senden soll.

Eine IP-Adresse beantwortet vereinfacht die Frage:

```text
Welches Gerät oder welches Ziel im Netzwerk?
```

---

## IPv4

IPv4 ist die ältere und noch sehr verbreitete Version von IP-Adressen.

Beispiel:

```text
192.168.1.25
```

IPv4 besteht aus vier Zahlenblöcken.

Jeder Block kann Werte von 0 bis 255 haben.

Beispiel:

```text
192 . 168 . 1 . 25
```

Jeder dieser Blöcke wird Oktett genannt.

Eine IPv4-Adresse hat insgesamt 32 Bit.

---

## IPv4-Aufbau

Eine IPv4-Adresse besteht aus:

```text
Netzanteil
Hostanteil
```

Der Netzanteil sagt, zu welchem Netzwerk die Adresse gehört.

Der Hostanteil sagt, welches Gerät innerhalb dieses Netzwerks gemeint ist.

Beispiel:

```text
192.168.1.25/24
```

Bei `/24` ist meistens:

```text
Netzanteil: 192.168.1
Hostanteil: 25
```

Vereinfacht liegt das Gerät also im Netzwerk:

```text
192.168.1.0/24
```

---

## Subnetzmaske

Die Subnetzmaske trennt Netzanteil und Hostanteil.

Beispiel:

```text
IP-Adresse:    192.168.1.25
Subnetzmaske: 255.255.255.0
CIDR:          /24
```

Die Subnetzmaske sagt:

```text
Welche Teile der IP-Adresse gehören zum Netzwerk?
Welche Teile sind für Hosts nutzbar?
```

Bei:

```text
255.255.255.0
```

gehören die ersten drei Blöcke zum Netzwerk.

Der letzte Block ist für Hosts.

---

## CIDR-Schreibweise

CIDR ist eine kurze Schreibweise für die Subnetzmaske.

Beispiele:

| CIDR  | Subnetzmaske      |
| ----- | ----------------- |
| `/8`  | `255.0.0.0`       |
| `/16` | `255.255.0.0`     |
| `/24` | `255.255.255.0`   |
| `/25` | `255.255.255.128` |
| `/26` | `255.255.255.192` |
| `/27` | `255.255.255.224` |
| `/28` | `255.255.255.240` |

Beispiel:

```text
192.168.1.0/24
```

ist dasselbe wie:

```text
192.168.1.0 mit Subnetzmaske 255.255.255.0
```

---

## Netzwerkadresse

Die Netzwerkadresse beschreibt das Netzwerk selbst.

Beispiel:

```text
192.168.1.0/24
```

Hier ist:

```text
192.168.1.0
```

die Netzwerkadresse.

Diese Adresse wird nicht für ein normales Gerät verwendet.

Sie beschreibt den gesamten Netzbereich.

---

## Hostadressen

Hostadressen sind die nutzbaren Adressen für Geräte.

Beispiel:

```text
192.168.1.0/24
```

Nutzbare Hosts:

```text
192.168.1.1 bis 192.168.1.254
```

Beispiele für Geräte:

```text
192.168.1.1   Router/Gateway
192.168.1.10  Server
192.168.1.25  Laptop
192.168.1.50  Drucker
```

---

## Broadcast-Adresse

Die Broadcast-Adresse ist die letzte Adresse eines Subnetzes.

Beispiel:

```text
192.168.1.0/24
```

Broadcast:

```text
192.168.1.255
```

Ein Broadcast wird an alle Geräte im lokalen Subnetz gesendet.

Die Broadcast-Adresse wird nicht für ein normales Gerät genutzt.

---

## Beispiel /24

Ein sehr häufiges Netz ist:

```text
192.168.1.0/24
```

Dazu gehören:

| Bereich                 | Wert            |
| ----------------------- | --------------- |
| Netzwerkadresse         | `192.168.1.0`   |
| erste nutzbare Adresse  | `192.168.1.1`   |
| letzte nutzbare Adresse | `192.168.1.254` |
| Broadcast-Adresse       | `192.168.1.255` |
| Subnetzmaske            | `255.255.255.0` |
| nutzbare Hosts          | 254             |

Warum 254?

```text
256 Adressen insgesamt
- 1 Netzwerkadresse
- 1 Broadcast-Adresse
= 254 nutzbare Hostadressen
```

---

## Private IPv4-Bereiche

Private IP-Adressen werden in internen Netzwerken genutzt.

Wichtige private Bereiche:

| Bereich                             | CIDR  | Typische Nutzung        |
| ----------------------------------- | ----- | ----------------------- |
| `10.0.0.0` bis `10.255.255.255`     | `/8`  | große interne Netze     |
| `172.16.0.0` bis `172.31.255.255`   | `/12` | Firmen- und Labornetze  |
| `192.168.0.0` bis `192.168.255.255` | `/16` | Heimnetze, kleine Netze |

Beispiele:

```text
192.168.1.25
10.0.0.15
172.16.5.20
```

Diese Adressen sind im Internet nicht direkt öffentlich geroutet.

Für den Internetzugang wird meistens NAT genutzt.

---

## Öffentliche IP-Adressen

Öffentliche IP-Adressen sind im Internet erreichbar.

Beispiel:

```text
84.x.x.x
142.x.x.x
```

Diese Adressen werden von Providern oder Organisationen vergeben.

Ein Heimrouter hat meistens:

```text
private IP innen
öffentliche IP außen
```

Beispiel:

```text
Laptop innen: 192.168.1.25
Router außen: öffentliche IP vom Provider
```

---

## NAT und private IP-Adressen

NAT bedeutet:

```text
Network Address Translation
```

NAT übersetzt private IP-Adressen in eine öffentliche IP-Adresse.

Vereinfacht:

```text
192.168.1.25 -> Router/NAT -> öffentliche IP -> Internet
```

Viele Geräte im Heimnetz können dadurch über eine öffentliche IP-Adresse ins Internet.

Ohne NAT wären private IP-Adressen im Internet nicht direkt erreichbar.

---

## Loopback-Adresse

Die wichtigste Loopback-Adresse ist:

```text
127.0.0.1
```

Sie bedeutet:

```text
dieses Gerät selbst
```

Der Name dazu ist oft:

```text
localhost
```

Beispiel:

```bash
ping 127.0.0.1
ping localhost
```

Wichtig:

`localhost` zeigt immer auf das System, auf dem man gerade ist.

In einem Docker-Container bedeutet `localhost` also der Container selbst, nicht der Host und nicht ein anderer Container.

---

## Link-Local-Adresse

Wenn ein Gerät keine gültige IP-Adresse per DHCP bekommt, kann es manchmal eine Link-Local-Adresse erhalten.

Bei IPv4 ist das oft:

```text
169.254.x.x
```

Beispiel:

```text
169.254.12.34
```

Das ist oft ein Hinweis auf ein DHCP-Problem.

Mögliche Ursachen:

```text
DHCP-Server nicht erreichbar
Kabel/WLAN-Problem
falsches VLAN
Adressbereich voll
Netzwerkdienst gestört
```

---

## APIPA kurz erklärt

APIPA steht für:

```text
Automatic Private IP Addressing
```

Das ist die automatische Vergabe einer Adresse im Bereich:

```text
169.254.0.0/16
```

Wenn ein Client so eine Adresse bekommt, hat er meistens keine normale Netzwerkkonfiguration erhalten.

In der Praxis bedeutet das oft:

```text
DHCP prüfen.
Netzwerkverbindung prüfen.
VLAN prüfen.
```

---

## IP-Adresse, Subnetzmaske, Gateway und DNS

Eine vollständige Netzwerkkonfiguration besteht meistens aus mehreren Werten.

Beispiel:

```text
IP-Adresse:    192.168.1.25
Subnetzmaske: 255.255.255.0
Gateway:       192.168.1.1
DNS-Server:    192.168.1.1
```

Bedeutung:

| Wert         | Aufgabe                       |
| ------------ | ----------------------------- |
| IP-Adresse   | Adresse des Geräts            |
| Subnetzmaske | trennt Netz und Host          |
| Gateway      | Weg in andere Netzwerke       |
| DNS-Server   | löst Namen in IP-Adressen auf |

Alle vier Werte müssen zusammenpassen.

---

## Gleiches Subnetz erkennen

Zwei Geräte können direkt miteinander kommunizieren, wenn sie im gleichen Subnetz liegen.

Beispiel:

```text
Gerät A: 192.168.1.20/24
Gerät B: 192.168.1.50/24
```

Beide liegen im Netzwerk:

```text
192.168.1.0/24
```

Sie können direkt im lokalen Netz kommunizieren.

Anderes Beispiel:

```text
Gerät A: 192.168.1.20/24
Gerät B: 192.168.2.50/24
```

Gerät A liegt in:

```text
192.168.1.0/24
```

Gerät B liegt in:

```text
192.168.2.0/24
```

Diese Geräte brauchen einen Router, um miteinander zu kommunizieren.

---

## Subnetting

Subnetting bedeutet, ein größeres Netzwerk in kleinere Netzwerke aufzuteilen.

Beispiel:

```text
192.168.0.0/24
```

kann aufgeteilt werden in:

```text
192.168.0.0/25
192.168.0.128/25
```

Dadurch entstehen zwei kleinere Netze.

Warum macht man das?

- bessere Struktur
- weniger Broadcasts
- logische Trennung
- Sicherheitsbereiche
- VLAN-Planung
- bessere Adressplanung
- weniger Verschwendung

---

## Beispiel Subnetting im Unternehmen

Ein Unternehmen könnte Netze so planen:

| Bereich      | Netz              |
| ------------ | ----------------- |
| Verwaltung   | `192.168.10.0/24` |
| IT-Abteilung | `192.168.20.0/24` |
| Server       | `192.168.30.0/24` |
| Gäste-WLAN   | `192.168.40.0/24` |
| VoIP         | `192.168.50.0/24` |

So sind die Bereiche logisch getrennt.

Das passt gut zu VLANs:

```text
VLAN 10 -> 192.168.10.0/24
VLAN 20 -> 192.168.20.0/24
VLAN 30 -> 192.168.30.0/24
```

---

## /24 verstehen

`/24` ist sehr häufig.

Beispiel:

```text
192.168.1.0/24
```

Eigenschaften:

```text
Subnetzmaske: 255.255.255.0
Adressen insgesamt: 256
nutzbare Hosts: 254
```

Bereich:

```text
192.168.1.0 bis 192.168.1.255
```

Nutzbar:

```text
192.168.1.1 bis 192.168.1.254
```

---

## /25 verstehen

`/25` teilt ein `/24` in zwei kleinere Netze.

Beispiel:

```text
192.168.1.0/25
192.168.1.128/25
```

Erstes Netz:

```text
Netzwerk: 192.168.1.0
Hosts:    192.168.1.1 bis 192.168.1.126
Broadcast:192.168.1.127
```

Zweites Netz:

```text
Netzwerk: 192.168.1.128
Hosts:    192.168.1.129 bis 192.168.1.254
Broadcast:192.168.1.255
```

Ein `/25` hat 128 Adressen insgesamt und 126 nutzbare Hosts.

---

## /26 verstehen

`/26` teilt ein `/24` in vier Netze.

Beispiel:

```text
192.168.1.0/26
192.168.1.64/26
192.168.1.128/26
192.168.1.192/26
```

Jedes `/26` hat:

```text
64 Adressen insgesamt
62 nutzbare Hosts
```

Beispiel erstes Netz:

```text
Netzwerk:  192.168.1.0
Hosts:     192.168.1.1 bis 192.168.1.62
Broadcast: 192.168.1.63
```

---

## /27 verstehen

`/27` teilt ein `/24` in acht Netze.

Schrittweite:

```text
32
```

Netze:

```text
192.168.1.0/27
192.168.1.32/27
192.168.1.64/27
192.168.1.96/27
192.168.1.128/27
192.168.1.160/27
192.168.1.192/27
192.168.1.224/27
```

Jedes `/27` hat:

```text
32 Adressen insgesamt
30 nutzbare Hosts
```

---

## /28 verstehen

`/28` teilt ein `/24` in kleinere Netze mit 16 Adressen.

Schrittweite:

```text
16
```

Beispiel:

```text
192.168.1.0/28
192.168.1.16/28
192.168.1.32/28
192.168.1.48/28
```

Jedes `/28` hat:

```text
16 Adressen insgesamt
14 nutzbare Hosts
```

Das kann für kleine Bereiche genutzt werden, zum Beispiel kleine Serversegmente oder Punkt-zu-Punkt-nahe Strukturen.

---

## Wichtige Subnetzgrößen

| CIDR  | Subnetzmaske      | Adressen gesamt | Nutzbare Hosts |
| ----- | ----------------- | --------------: | -------------: |
| `/24` | `255.255.255.0`   |             256 |            254 |
| `/25` | `255.255.255.128` |             128 |            126 |
| `/26` | `255.255.255.192` |              64 |             62 |
| `/27` | `255.255.255.224` |              32 |             30 |
| `/28` | `255.255.255.240` |              16 |             14 |
| `/29` | `255.255.255.248` |               8 |              6 |
| `/30` | `255.255.255.252` |               4 |              2 |

Merke:

```text
Je größer die CIDR-Zahl, desto kleiner das Netz.
```

---

## Schrittweite berechnen

Bei Subnetting ist die Schrittweite wichtig.

Beispiel `/26`:

```text
Subnetzmaske: 255.255.255.192
```

Rechnung im letzten Oktett:

```text
256 - 192 = 64
```

Die Schrittweite ist also:

```text
64
```

Netze:

```text
192.168.1.0
192.168.1.64
192.168.1.128
192.168.1.192
```

---

## Hostanzahl berechnen

Bei IPv4 gilt vereinfacht:

```text
Anzahl Hostbits = 32 - CIDR
Adressen gesamt = 2 hoch Hostbits
nutzbare Hosts = Adressen gesamt - 2
```

Beispiel `/24`:

```text
Hostbits = 32 - 24 = 8
2^8 = 256 Adressen
256 - 2 = 254 nutzbare Hosts
```

Beispiel `/26`:

```text
Hostbits = 32 - 26 = 6
2^6 = 64 Adressen
64 - 2 = 62 nutzbare Hosts
```

Die zwei abgezogenen Adressen sind Netzwerkadresse und Broadcast-Adresse.

---

## Kleine Subnetting-Tabelle

| CIDR  | Hostbits | Adressen | Nutzbare Hosts |
| ----- | -------: | -------: | -------------: |
| `/24` |        8 |      256 |            254 |
| `/25` |        7 |      128 |            126 |
| `/26` |        6 |       64 |             62 |
| `/27` |        5 |       32 |             30 |
| `/28` |        4 |       16 |             14 |
| `/29` |        3 |        8 |              6 |
| `/30` |        2 |        4 |              2 |

Diese Tabelle reicht für viele einfache Praxisfälle.

---

## Gateway-Adresse planen

Das Gateway ist oft die erste oder letzte nutzbare Adresse im Netz.

Beispiele:

```text
Netz: 192.168.10.0/24
Gateway: 192.168.10.1
```

oder:

```text
Netz: 192.168.10.0/24
Gateway: 192.168.10.254
```

Beides kann funktionieren.

Wichtig ist:

```text
Die Dokumentation muss klar sein.
Die Clients müssen das richtige Gateway bekommen.
```

---

## DHCP-Bereich planen

In einem Netzwerk gibt es oft feste und dynamische IP-Adressen.

Beispiel:

```text
Netz: 192.168.10.0/24
Gateway: 192.168.10.1
Server: 192.168.10.10 bis 192.168.10.49
Drucker: 192.168.10.50 bis 192.168.10.79
DHCP: 192.168.10.100 bis 192.168.10.200
```

So vermeidet man Konflikte zwischen festen IPs und DHCP-Adressen.

---

## Statische IP-Adresse

Eine statische IP-Adresse wird manuell festgelegt.

Typische Geräte mit statischer IP:

```text
Server
Drucker
Firewall
Router
Switch-Management
Access Points
NAS-Systeme
```

Vorteile:

- Adresse bleibt gleich
- einfacher für Serverdienste
- einfacher für Dokumentation
- besser für feste Zugriffe

Nachteile:

- manuelle Pflege nötig
- Risiko von Adresskonflikten
- Fehler bei Maske/Gateway/DNS möglich

---

## Dynamische IP-Adresse

Eine dynamische IP-Adresse wird über DHCP vergeben.

Typische Geräte mit DHCP:

```text
Laptops
Smartphones
Tablets
normale Clients
Gäste-Geräte
```

Vorteile:

- automatische Konfiguration
- weniger manuelle Fehler
- einfache Verwaltung vieler Clients
- zentrale Änderung von Gateway/DNS möglich

Nachteile:

- Adresse kann sich ändern
- bei DHCP-Problemen bekommt das Gerät keine gültige Konfiguration

---

## Adresskonflikt

Ein Adresskonflikt entsteht, wenn zwei Geräte dieselbe IP-Adresse nutzen.

Beispiel:

```text
PC A: 192.168.1.50
PC B: 192.168.1.50
```

Mögliche Folgen:

- instabile Verbindung
- ein Gerät ist manchmal erreichbar, manchmal nicht
- Verbindungsabbrüche
- Warnmeldungen im Betriebssystem
- schwer nachvollziehbare Fehler

Ursachen:

```text
statische IP doppelt vergeben
DHCP-Bereich überschneidet sich mit statischen IPs
alte Dokumentation
manuelle Fehlkonfiguration
```

---

## IPv6 kurz erklärt

IPv6 ist die neuere Version des Internet Protocols.

Beispiel:

```text
2001:db8::1
```

IPv6-Adressen sind länger als IPv4-Adressen.

IPv6 nutzt 128 Bit statt 32 Bit.

Vorteile:

- sehr großer Adressraum
- weniger Bedarf für NAT
- moderne Netzwerktechnik
- automatische Adresskonfiguration möglich

Für den Anfang ist IPv4 oft leichter. Trotzdem sollte man wissen, dass IPv6 in modernen Netzwerken wichtig ist.

---

## IPv6 Link-Local

IPv6-Geräte haben oft Link-Local-Adressen.

Diese beginnen häufig mit:

```text
fe80::
```

Beispiel:

```text
fe80::1234:abcd:5678
```

Link-Local-Adressen gelten nur im lokalen Netzwerksegment.

Sie sind für bestimmte interne Kommunikationsprozesse wichtig.

---

## IP-Adresse unter Linux anzeigen

Unter Linux zeigt man IP-Adressen mit:

```bash
ip a
```

oder ausführlicher:

```bash
ip address
```

Beispielausgabe enthält:

```text
Interface
MAC-Adresse
IPv4-Adresse
IPv6-Adresse
Status UP/DOWN
```

Wichtig sind oft diese Fragen:

```text
Hat das Interface eine IP?
Ist die IP im richtigen Netz?
Ist das Interface UP?
```

---

## Routing und Gateway anzeigen

Das Gateway sieht man mit:

```bash
ip route
```

Beispiel:

```text
default via 192.168.1.1 dev wlan0
192.168.1.0/24 dev wlan0
```

Bedeutung:

| Eintrag                    | Bedeutung                         |
| -------------------------- | --------------------------------- |
| `default via 192.168.1.1`  | Standardgateway                   |
| `192.168.1.0/24 dev wlan0` | lokales Netz über Interface wlan0 |

Ohne Default Route funktioniert oft kein Zugriff auf externe Netze.

---

## IP-Adresse testen

Gateway testen:

```bash
ping 192.168.1.1
```

Externe IP testen:

```bash
ping 8.8.8.8
```

DNS-Namen testen:

```bash
ping github.com
```

Interpretation:

| Ergebnis                             | Bedeutung                    |
| ------------------------------------ | ---------------------------- |
| Gateway nicht erreichbar             | lokales Netzwerkproblem      |
| Gateway erreichbar, externe IP nicht | Routing/NAT/Firewall möglich |
| externe IP erreichbar, Name nicht    | DNS-Problem                  |
| alles erreichbar                     | Netzwerk grundsätzlich okay  |

---

## Subnetz mit ipcalc prüfen

Auf manchen Systemen kann man `ipcalc` nutzen.

Beispiel:

```bash
ipcalc 192.168.1.25/24
```

Das zeigt Informationen wie:

```text
Netzwerkadresse
Broadcast-Adresse
Hostbereich
Subnetzmaske
```

`ipcalc` ist praktisch zum Lernen und Prüfen von Subnetzen.

---

## Beispiel: Prüfen, ob zwei Geräte im gleichen Netz sind

Gerät A:

```text
192.168.10.20/24
```

Gerät B:

```text
192.168.10.50/24
```

Beide liegen im Netz:

```text
192.168.10.0/24
```

Sie sind im gleichen Subnetz.

Anderes Beispiel:

```text
192.168.10.20/24
192.168.11.50/24
```

Diese Geräte liegen in verschiedenen Netzen.

Sie brauchen Routing.

---

## Beispiel: falsche Subnetzmaske

Client:

```text
IP:      192.168.1.50
Maske:   255.255.0.0
Gateway: 192.168.1.1
```

Eigentlich sollte das Netz vielleicht `/24` sein.

Mit falscher Maske kann der Client denken, dass viel mehr Adressen lokal erreichbar sind.

Das kann zu Problemen führen, weil der Client Pakete nicht an das Gateway sendet, obwohl er es müsste.

Subnetzmaske und Gateway müssen zur Netzplanung passen.

---

## Beispiel: falsches Gateway

Client:

```text
IP:      192.168.1.50
Maske:   255.255.255.0
Gateway: 192.168.2.1
```

Problem:

Das Gateway liegt nicht im gleichen Subnetz.

Der Client kann das Gateway nicht direkt erreichen.

Richtig wäre zum Beispiel:

```text
Gateway: 192.168.1.1
```

Das Gateway muss normalerweise im gleichen lokalen Netz wie der Client liegen.

---

## Typische Fehler

| Fehler                                             | Problem                                            |
| -------------------------------------------------- | -------------------------------------------------- |
| falsche Subnetzmaske                               | Geräte werden falsch als lokal oder extern erkannt |
| falsches Gateway                                   | Zugriff auf andere Netze funktioniert nicht        |
| IP-Adresse doppelt vergeben                        | Adresskonflikt                                     |
| DHCP-Bereich überschneidet sich mit statischen IPs | Konflikte möglich                                  |
| Netzwerkadresse als Host nutzen                    | ungültige Hostadresse                              |
| Broadcast-Adresse als Host nutzen                  | ungültige Hostadresse                              |
| private und öffentliche IPs verwechseln            | falsches Verständnis von NAT                       |
| `localhost` falsch verstehen                       | zeigt immer auf das eigene System                  |
| `/24` automatisch überall annehmen                 | nicht jedes Netz ist `/24`                         |
| DNS-Problem mit IP-Problem verwechseln             | falsche Fehlersuche                                |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei IP-Problemen:

1. IP-Adresse prüfen
2. Subnetzmaske prüfen
3. Gateway prüfen
4. DNS prüfen
5. Routingtabelle ansehen
6. Gateway anpingen
7. externe IP testen
8. DNS-Namen testen
9. Adresskonflikte prüfen
10. Dokumentation vergleichen

Wichtige Befehle:

```bash
ip a
ip route
ping gateway-ip
ping 8.8.8.8
ping github.com
```

---

## FISI-Bezug

Für FISI sind IP-Adressen und Subnetting Grundwissen.

In der Praxis braucht man dieses Wissen für:

- Clients ins Netzwerk einbinden
- Drucker und Server adressieren
- DHCP-Bereiche planen
- statische IPs vergeben
- VLAN-Netze verstehen
- Routing-Probleme erkennen
- VM-Netzwerke verstehen
- Docker-Netzwerke einordnen
- Netzwerkdokumentation lesen
- Fehler systematisch analysieren

Ein FISI muss nicht jede Subnetting-Aufgabe sofort im Kopf lösen. Aber die Grundlogik von IP-Adresse, Subnetzmaske, Gateway, DNS, Netzwerkadresse, Broadcast und Hostbereich muss klar sein.

---

## Kurze Zusammenfassung

IP-Adressen identifizieren Geräte logisch im Netzwerk.

Die Subnetzmaske oder CIDR-Schreibweise trennt Netzanteil und Hostanteil.

Wichtige Begriffe sind Netzwerkadresse, Hostadresse, Broadcast-Adresse, Gateway, private IP-Adresse, öffentliche IP-Adresse, DHCP, statische IP und NAT.

Subnetting teilt größere Netzwerke in kleinere Netze auf. Das hilft bei Struktur, Sicherheit, VLANs und Netzwerkplanung.

Für FISI ist dieses Thema besonders wichtig, weil viele Netzwerkprobleme auf falsche IP-Konfiguration, falsche Subnetzmaske, falsches Gateway oder DNS-Probleme zurückgehen.
