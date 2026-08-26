# 5. Switching und WLAN

In diesem Kapitel geht es um Switching und WLAN.

Switches und WLAN-Access-Points sind wichtige Bestandteile lokaler Netzwerke. Switches verbinden Geräte über Kabel. WLAN verbindet Geräte über Funk. Beide Themen sind für die tägliche Arbeit in der Systemintegration sehr wichtig.

Für Fachinformatiker für Systemintegration ist dieses Wissen wichtig, weil viele Praxisprobleme mit Switch-Ports, VLANs, MAC-Adressen, WLAN-Signal, Kanälen, Access Points oder falscher Netzwerkkonfiguration zusammenhängen.

---

## Kurz erklärt

| Thema        | Bedeutung                                   |
| ------------ | ------------------------------------------- |
| Switching    | Weiterleitung von Daten im lokalen Netzwerk |
| Switch       | verbindet Geräte im LAN                     |
| MAC-Adresse  | Hardwareadresse einer Netzwerkschnittstelle |
| Access Point | stellt WLAN bereit                          |
| WLAN         | drahtloses lokales Netzwerk                 |
| SSID         | Name eines WLAN-Netzes                      |
| WPA2/WPA3    | WLAN-Verschlüsselung                        |
| Kanal        | Funkbereich, auf dem WLAN arbeitet          |

Ein Switch arbeitet hauptsächlich auf Layer 2 des OSI-Modells.

WLAN nutzt Funk statt Netzwerkkabel, verbindet Geräte aber ebenfalls mit dem Netzwerk.

---

## Switch

Ein Switch verbindet mehrere Geräte in einem lokalen Netzwerk.

Beispiele:

```text
PC
Laptop
Server
Drucker
Access Point
IP-Telefon
Firewall
Router
```

Ein Switch hat mehrere Ports. An diese Ports werden Geräte per Netzwerkkabel angeschlossen.

Beispiel:

```text
PC -> Switch -> Router -> Internet
Server -> Switch -> Clients
Access Point -> Switch -> WLAN-Clients
```

---

## Aufgabe eines Switches

Ein Switch leitet Ethernet-Frames im lokalen Netzwerk weiter.

Vereinfacht:

```text
Ein Gerät sendet Daten.
Der Switch schaut auf die Ziel-MAC-Adresse.
Der Switch sendet die Daten an den passenden Port weiter.
```

Ein Switch ist also nicht einfach nur ein Verteiler. Er lernt, welche MAC-Adresse an welchem Port erreichbar ist.

---

## MAC-Adresse

Eine MAC-Adresse ist eine Hardwareadresse einer Netzwerkschnittstelle.

Beispiel:

```text
a4:bb:6d:12:34:56
```

MAC-Adressen werden im lokalen Netzwerk verwendet.

Ein Switch arbeitet mit MAC-Adressen.

Vereinfacht:

```text
IP-Adresse = logische Adresse
MAC-Adresse = lokale Hardwareadresse
```

Unter Linux kann man MAC-Adressen sehen mit:

```bash
ip link
```

oder:

```bash
ip a
```

---

## MAC-Adress-Tabelle

Ein Switch führt eine MAC-Adress-Tabelle.

Darin steht vereinfacht:

```text
MAC-Adresse A -> Port 1
MAC-Adresse B -> Port 2
MAC-Adresse C -> Port 8
```

Wenn ein Frame an MAC-Adresse B gesendet wird, weiß der Switch:

```text
MAC-Adresse B ist an Port 2.
```

Dann sendet er den Frame gezielt an Port 2.

Das ist effizienter als alles an alle Ports zu senden.

---

## Lernen von MAC-Adressen

Ein Switch lernt MAC-Adressen automatisch.

Ablauf:

```text
1. Gerät sendet Daten über einen Switch-Port.
2. Switch liest die Quell-MAC-Adresse.
3. Switch merkt sich: Diese MAC-Adresse kommt von diesem Port.
4. Beim nächsten Frame kann der Switch gezielt weiterleiten.
```

Die MAC-Adress-Tabelle wird dynamisch aufgebaut.

Wenn ein Gerät den Port wechselt, lernt der Switch das nach einiger Zeit neu.

---

## Unknown Unicast

Wenn der Switch die Ziel-MAC-Adresse noch nicht kennt, sendet er den Frame an mehrere Ports.

Das nennt man:

```text
Unknown Unicast Flooding
```

Vereinfacht:

```text
Switch weiß Ziel nicht -> sendet an alle passenden Ports
```

Sobald das Ziel antwortet, lernt der Switch die MAC-Adresse und kann später gezielter weiterleiten.

---

## Broadcast

Ein Broadcast wird an alle Geräte im lokalen Netzwerksegment gesendet.

Beispiel:

```text
Wer hat die IP-Adresse 192.168.1.10?
```

Broadcasts sind unter anderem bei ARP wichtig.

Broadcast-Adresse auf MAC-Ebene:

```text
ff:ff:ff:ff:ff:ff
```

Zu viele Broadcasts können ein Netzwerk belasten.

VLANs helfen, Broadcast-Bereiche zu trennen.

---

## ARP und Switching

ARP bedeutet:

```text
Address Resolution Protocol
```

ARP verbindet IP-Adressen mit MAC-Adressen.

Beispiel:

```text
Client möchte 192.168.1.10 erreichen.
Client fragt: Welche MAC-Adresse gehört zu 192.168.1.10?
```

Die Antwort enthält die MAC-Adresse.

Danach kann der Client im lokalen Netzwerk direkt senden.

Unter Linux prüfen:

```bash
ip neigh
```

---

## Switch vs Router

Switch und Router haben unterschiedliche Aufgaben.

| Gerät  | Aufgabe                                       |
| ------ | --------------------------------------------- |
| Switch | verbindet Geräte im gleichen lokalen Netzwerk |
| Router | verbindet verschiedene Netzwerke              |

Ein Switch arbeitet hauptsächlich mit MAC-Adressen.

Ein Router arbeitet mit IP-Adressen.

Beispiel:

```text
Switch: PC zu Server im gleichen LAN
Router: LAN zu Internet oder VLAN 10 zu VLAN 30
```

---

## Unmanaged Switch

Ein unmanaged Switch ist ein einfacher Switch ohne große Konfigurationsmöglichkeiten.

Eigenschaften:

```text
anschließen und nutzen
keine VLAN-Konfiguration
keine Management-IP
keine detaillierte Überwachung
einfache Nutzung
```

Typisch für:

```text
Heimnetz
kleine Büros
einfache Erweiterung von Ports
```

Für Lernzwecke ist er einfach, aber für professionelle Netztrennung oft zu begrenzt.

---

## Managed Switch

Ein managed Switch kann konfiguriert und überwacht werden.

Mögliche Funktionen:

```text
VLANs
Trunks
Port-Konfiguration
Port-Security
Monitoring
Spanning Tree
Link Aggregation
Management-IP
Logs
SNMP
```

Für Firmenumgebungen sind managed Switches wichtig.

Sie ermöglichen strukturierte Netzwerke und bessere Fehlersuche.

---

## Access Port

Ein Access Port gehört normalerweise zu einem VLAN.

Beispiel:

```text
Port 5 -> VLAN 10
```

Ein normaler PC hängt meistens an einem Access Port.

Der Client merkt meistens nicht, dass er in einem VLAN ist.

Er bekommt einfach eine IP-Adresse aus dem passenden Netz.

Beispiel:

```text
VLAN 10 -> 192.168.10.0/24
Client -> 192.168.10.25
```

---

## Trunk Port

Ein Trunk Port transportiert mehrere VLANs.

Typische Verbindungen:

```text
Switch zu Switch
Switch zu Router
Switch zu Firewall
Switch zu Access Point
```

Ein Trunk nutzt VLAN-Tags.

Beispiel:

```text
VLAN 10
VLAN 20
VLAN 30
```

werden über eine Verbindung transportiert.

---

## VLAN-Tagging

VLAN-Tagging wird genutzt, um Frames einem VLAN zuzuordnen.

Der Standard heißt:

```text
802.1Q
```

Vereinfacht:

```text
Frame bekommt VLAN-ID.
Switch erkennt, zu welchem VLAN der Frame gehört.
```

Access Ports senden an normale Endgeräte meistens untagged Traffic.

Trunk Ports transportieren tagged Traffic für mehrere VLANs.

---

## Port Security kurz erklärt

Port Security kann einschränken, welche Geräte an einem Switch-Port erlaubt sind.

Beispiel:

```text
Nur eine bestimmte MAC-Adresse darf an Port 5 arbeiten.
```

Mögliche Ziele:

- Schutz vor unerlaubten Geräten
- Begrenzung von MAC-Adressen pro Port
- Kontrolle von Arbeitsplatzanschlüssen
- Erkennung von unerwarteten Geräten

In der Praxis muss Port Security sauber geplant werden, sonst können legitime Geräte blockiert werden.

---

## Spanning Tree kurz erklärt

Spanning Tree Protocol verhindert Schleifen im Netzwerk.

Abkürzung:

```text
STP
```

Ein Netzwerkloop kann entstehen, wenn Switches mehrfach verbunden werden.

Beispiel:

```text
Switch A -> Switch B
Switch B -> Switch C
Switch C -> Switch A
```

Ohne Schutz kann ein Loop Broadcast-Stürme verursachen.

STP blockiert bestimmte Wege, damit keine Schleife aktiv bleibt.

---

## Broadcast Storm

Ein Broadcast Storm entsteht, wenn Broadcasts endlos oder extrem häufig durch das Netzwerk laufen.

Mögliche Ursache:

```text
Switching-Loop
falsch verbundene Kabel
fehlendes oder falsch konfiguriertes STP
```

Auswirkung:

```text
Netzwerk wird langsam
Clients verlieren Verbindung
Switches sind überlastet
Dienste werden unerreichbar
```

Deshalb sind saubere Verkabelung und STP wichtig.

---

## Link Aggregation kurz erklärt

Link Aggregation verbindet mehrere physische Netzwerkverbindungen zu einer logischen Verbindung.

Ziel:

- mehr Bandbreite
- Redundanz
- Lastverteilung

Beispiel:

```text
2 x 1 Gbit/s Verbindung zwischen Switch und Server
```

Ein häufiges Protokoll dafür ist:

```text
LACP
```

Für den Einstieg reicht zu wissen:

```text
Mehrere Links können logisch gebündelt werden.
Beide Seiten müssen passend konfiguriert sein.
```

---

## PoE

PoE bedeutet:

```text
Power over Ethernet
```

Dabei wird Strom über das Netzwerkkabel übertragen.

Typische Geräte mit PoE:

```text
Access Points
IP-Telefone
Überwachungskameras
kleine Netzwerkgeräte
```

Vorteile:

- weniger Netzteile
- zentrale Stromversorgung
- einfachere Montage
- gut für Access Points an Decken

Wichtig:

Switch und Gerät müssen PoE unterstützen.

---

## WLAN

WLAN bedeutet:

```text
Wireless Local Area Network
```

WLAN ist ein drahtloses lokales Netzwerk.

Statt Kabel nutzt WLAN Funk.

Typische Geräte:

```text
Access Point
WLAN-Router
Laptop
Smartphone
Tablet
Drucker
IoT-Geräte
```

WLAN ist bequem, aber störanfälliger als Kabel.

---

## Access Point

Ein Access Point stellt WLAN bereit und verbindet drahtlose Geräte mit dem kabelgebundenen Netzwerk.

Beispiel:

```text
Laptop -> WLAN -> Access Point -> Switch -> Router -> Internet
```

In Heimroutern sind oft mehrere Funktionen kombiniert:

```text
Router
Switch
Firewall
Access Point
DHCP
DNS-Weiterleitung
```

In Firmen sind Access Points meistens eigene Geräte, die zentral verwaltet werden können.

---

## SSID

SSID bedeutet:

```text
Service Set Identifier
```

Die SSID ist der sichtbare oder konfigurierte Name eines WLAN-Netzes.

Beispiel:

```text
Firma-WLAN
Gast-WLAN
IoT-WLAN
```

Ein Access Point kann mehrere SSIDs bereitstellen.

Beispiel:

| SSID       | Zweck       |
| ---------- | ----------- |
| Firma-WLAN | Mitarbeiter |
| Gast-WLAN  | Besucher    |
| IoT-WLAN   | Geräte      |

Diese SSIDs können unterschiedlichen VLANs zugeordnet werden.

---

## WLAN und VLAN

WLAN kann mit VLANs verbunden werden.

Beispiel:

| SSID       | VLAN    | Subnetz           |
| ---------- | ------- | ----------------- |
| Firma-WLAN | VLAN 10 | `192.168.10.0/24` |
| Gast-WLAN  | VLAN 20 | `192.168.20.0/24` |
| IoT-WLAN   | VLAN 60 | `192.168.60.0/24` |

Der Access Point hängt dann oft an einem Trunk-Port.

Der Switch-Port zum Access Point muss die benötigten VLANs transportieren.

Wenn das falsch konfiguriert ist, bekommen WLAN-Clients eventuell keine IP-Adresse oder landen im falschen Netz.

---

## WLAN-Frequenzen

WLAN arbeitet typischerweise in verschiedenen Frequenzbereichen.

Wichtige Bereiche:

| Frequenz | Eigenschaften                                      |
| -------- | -------------------------------------------------- |
| 2,4 GHz  | größere Reichweite, weniger Kanäle, mehr Störungen |
| 5 GHz    | mehr Kanäle, oft schneller, geringere Reichweite   |
| 6 GHz    | moderner, mehr Platz, geeignete Geräte nötig       |

2,4 GHz ist oft stärker durch andere Geräte belastet.

5 GHz ist oft schneller, aber Reichweite und Wanddurchdringung sind geringer.

---

## WLAN-Kanäle

WLAN nutzt Kanäle innerhalb eines Frequenzbereichs.

Wenn viele Access Points denselben oder überlappende Kanäle nutzen, kann es zu Störungen kommen.

Bei 2,4 GHz werden häufig diese Kanäle empfohlen:

```text
1
6
11
```

Der Grund ist, dass sie sich weniger überlappen als viele andere Kanäle.

In dichten Umgebungen ist Kanalplanung wichtig.

---

## Signalstärke

WLAN-Qualität hängt stark vom Signal ab.

Einflussfaktoren:

```text
Entfernung zum Access Point
Wände
Decken
Metall
andere WLANs
Bluetooth
Mikrowellen
Geräteanzahl
Access-Point-Position
```

Schlechtes Signal führt zu:

```text
langsamer Verbindung
Abbrüchen
hoher Latenz
Paketverlust
schlechter Sprach- oder Videoqualität
```

---

## Band Steering kurz erklärt

Band Steering versucht, Clients auf ein besseres Frequenzband zu lenken.

Beispiel:

```text
Client soll statt 2,4 GHz lieber 5 GHz nutzen.
```

Das kann helfen, wenn Clients und Access Points es gut unterstützen.

Es kann aber auch Probleme verursachen, wenn Geräte schlecht reagieren oder ständig zwischen Bändern wechseln.

---

## Roaming kurz erklärt

Roaming bedeutet, dass ein WLAN-Client zwischen Access Points wechselt.

Beispiel:

```text
Laptop bewegt sich vom Büro in den Besprechungsraum.
```

Der Client soll möglichst ohne Abbruch zum besseren Access Point wechseln.

Gutes Roaming ist wichtig in:

```text
Schulen
Büros
Lagerhallen
Krankenhäusern
großen Gebäuden
```

Schlechtes Roaming kann zu Verbindungsabbrüchen führen.

---

## WLAN-Sicherheit

WLAN muss verschlüsselt werden.

Wichtige Begriffe:

| Begriff    | Bedeutung                                           |
| ---------- | --------------------------------------------------- |
| WPA2       | weit verbreitete WLAN-Verschlüsselung               |
| WPA3       | neuerer Sicherheitsstandard                         |
| PSK        | gemeinsames Passwort                                |
| Enterprise | Anmeldung über Benutzer/Zertifikate, oft mit RADIUS |
| Gastnetz   | getrenntes WLAN für Besucher                        |

Für private oder kleine Netze wird oft WPA2/WPA3 mit Passwort genutzt.

In Firmenumgebungen ist WPA-Enterprise häufig sinnvoll.

---

## WPA-Personal und WPA-Enterprise

WPA-Personal nutzt ein gemeinsames WLAN-Passwort.

Beispiel:

```text
Alle Mitarbeiter nutzen dasselbe WLAN-Passwort.
```

WPA-Enterprise nutzt individuelle Anmeldung.

Beispiel:

```text
Benutzername + Passwort
Zertifikat
RADIUS-Server
```

Vergleich:

| Bereich           | WPA-Personal      | WPA-Enterprise       |
| ----------------- | ----------------- | -------------------- |
| Einrichtung       | einfacher         | komplexer            |
| Benutzerkontrolle | schwächer         | stärker              |
| Passwortwechsel   | für alle          | pro Benutzer möglich |
| Firmenumgebung    | begrenzt geeignet | besser geeignet      |

---

## Gäste-WLAN

Ein Gäste-WLAN sollte vom internen Netzwerk getrennt sein.

Ziel:

```text
Gäste dürfen ins Internet.
Gäste dürfen nicht auf interne Server.
```

Typische Umsetzung:

```text
eigene SSID
eigenes VLAN
eigener IP-Bereich
Firewall-Regeln
Client-Isolation
```

Beispiel:

```text
SSID: Gast-WLAN
VLAN: 20
Subnetz: 192.168.20.0/24
```

---

## Client-Isolation

Client-Isolation bedeutet, dass WLAN-Clients nicht direkt miteinander kommunizieren dürfen.

Das ist besonders bei Gäste-WLAN sinnvoll.

Beispiel:

```text
Gast A soll Gast B nicht direkt erreichen.
```

Das erhöht die Sicherheit im Gäste-Netz.

Für interne Netze muss man prüfen, ob Client-Isolation sinnvoll ist, weil manche Dienste direkte Kommunikation brauchen.

---

## WLAN und DHCP

WLAN-Clients brauchen genau wie kabelgebundene Clients eine IP-Konfiguration.

Diese kommt oft per DHCP.

Wenn ein WLAN-Client verbunden ist, aber keine gültige IP bekommt, mögliche Ursachen:

```text
DHCP-Server nicht erreichbar
falsches VLAN
Access Point falsch konfiguriert
Trunk-Port falsch
DHCP Relay fehlt
Firewall blockiert DHCP
```

Ein häufiger Fehler:

```text
WLAN-Verbindung steht, aber Netzwerk funktioniert nicht.
```

Dann ist oft nicht das WLAN-Passwort das Problem, sondern IP/DHCP/VLAN.

---

## WLAN und DNS

Wenn WLAN verbunden ist und IP funktioniert, aber Webseiten nicht über Namen erreichbar sind, kann DNS das Problem sein.

Test:

```bash
ping 8.8.8.8
ping github.com
dig github.com
```

Wenn externe IP funktioniert, aber Name nicht:

```text
DNS prüfen.
```

Das gilt bei WLAN genauso wie bei Kabelnetzwerken.

---

## WLAN unter Linux prüfen

Wichtige Befehle:

```bash
nmcli device status
nmcli connection show
ip a
ip route
iw dev
```

Je nach System kann auch hilfreich sein:

```bash
iwconfig
```

WLAN-Verbindung mit NetworkManager prüfen:

```bash
nmcli device wifi list
```

Verbindungsstatus:

```bash
nmcli device status
```

---

## WLAN-Signal prüfen

Mit `nmcli` kann man verfügbare WLANs anzeigen:

```bash
nmcli device wifi list
```

Dort sieht man oft Informationen wie:

```text
SSID
Signal
Sicherheit
Kanal
```

Bei schlechter Verbindung sollte man prüfen:

```text
Signalstärke
Frequenzband
Kanal
Entfernung
Access-Point-Auslastung
Störungen
```

---

## Kabel vs WLAN

| Bereich         | Kabel                    | WLAN                              |
| --------------- | ------------------------ | --------------------------------- |
| Stabilität      | meist höher              | abhängig von Signal und Störungen |
| Geschwindigkeit | oft stabiler             | schwankt stärker                  |
| Sicherheit      | physischer Zugriff nötig | Funk sichtbar                     |
| Mobilität       | gering                   | hoch                              |
| Einrichtung     | Kabel/Ports nötig        | Funkabdeckung nötig               |
| Fehlersuche     | oft klarer               | mehr Einflussfaktoren             |

Für Server und wichtige Infrastruktur ist Kabel meistens besser.

Für mobile Geräte ist WLAN praktischer.

---

## Typische Switching-Fehler

| Fehler                       | Problem                         |
| ---------------------------- | ------------------------------- |
| Kabel defekt                 | keine oder instabile Verbindung |
| falscher Switch-Port         | Gerät im falschen Netz          |
| Port deaktiviert             | Gerät bekommt keine Verbindung  |
| Access Port im falschen VLAN | falsche IP oder kein Zugriff    |
| Trunk falsch konfiguriert    | VLANs kommen nicht weiter       |
| Loop im Netzwerk             | Broadcast Storm möglich         |
| PoE fehlt                    | Access Point startet nicht      |
| Port Security blockiert      | Gerät wird nicht erlaubt        |
| MAC-Tabelle nicht verstanden | Fehlersuche wird unklar         |

---

## Typische WLAN-Fehler

| Fehler                        | Problem                          |
| ----------------------------- | -------------------------------- |
| falsches Passwort             | Verbindung schlägt fehl          |
| schlechtes Signal             | langsam oder instabil            |
| falscher Kanal                | Störungen                        |
| Access Point falsch platziert | schlechte Abdeckung              |
| falsches VLAN zur SSID        | falsches Netz                    |
| DHCP nicht erreichbar         | keine gültige IP                 |
| DNS falsch                    | Webseiten über Namen gehen nicht |
| Gastnetz nicht getrennt       | Sicherheitsproblem               |
| zu viele Clients              | Überlastung                      |
| Roaming schlecht              | Verbindungsabbrüche beim Bewegen |

---

## Gute Arbeitsweise bei Switching-Problemen

Eine sinnvolle Reihenfolge:

```text
1. Kabel prüfen
2. Link-LED prüfen
3. Switch-Port prüfen
4. VLAN-Zuordnung prüfen
5. IP-Adresse prüfen
6. Gateway prüfen
7. DNS prüfen
8. Zielport prüfen
9. Firewall prüfen
10. Dokumentation vergleichen
```

Wichtige Fragen:

```text
Ist der Port aktiv?
Ist es Access oder Trunk?
Ist das richtige VLAN gesetzt?
Bekommt der Client eine passende IP?
```

---

## Gute Arbeitsweise bei WLAN-Problemen

Eine sinnvolle Reihenfolge:

```text
1. Ist WLAN aktiviert?
2. Ist die richtige SSID verbunden?
3. Ist das Passwort korrekt?
4. Wie stark ist das Signal?
5. Bekommt der Client eine IP?
6. Ist das richtige VLAN zugeordnet?
7. Funktioniert Gateway?
8. Funktioniert DNS?
9. Gibt es Störungen oder Kanalprobleme?
10. Sind zu viele Clients verbunden?
```

Wichtige Befehle:

```bash
nmcli device status
nmcli device wifi list
ip a
ip route
ping gateway
ping 8.8.8.8
ping github.com
```

---

## Beispiel: Client bekommt am LAN-Port keine IP

Mögliche Ursachen:

```text
Kabel defekt
Switch-Port deaktiviert
falsches VLAN
DHCP nicht erreichbar
DHCP-Bereich voll
Port Security blockiert
```

Prüfen:

```bash
ip a
nmcli device status
ip route
```

Zusätzlich am Switch prüfen:

```text
Port aktiv?
Access VLAN korrekt?
Link vorhanden?
Port Security aktiv?
```

---

## Beispiel: WLAN verbunden, aber kein Internet

Prüfen:

```bash
ip a
ip route
ping gateway-ip
ping 8.8.8.8
ping github.com
```

Mögliche Ursachen:

```text
keine gültige IP
falsches VLAN
Gateway fehlt
DNS falsch
Firewall blockiert
Access Point falsch konfiguriert
```

Wichtig:

```text
WLAN-Verbindung bedeutet nicht automatisch Internet.
```

---

## Beispiel: Gäste-WLAN erreicht interne Server

Problem:

```text
Gäste können interne Server erreichen.
```

Prüfen:

```text
SSID mit richtigem VLAN verbunden?
Gast-VLAN eigenes Subnetz?
Firewall-Regeln korrekt?
Client-Isolation aktiv?
Routing ins interne Netz blockiert?
```

Ziel:

```text
Gastnetz -> Internet erlaubt
Gastnetz -> interne Netze blockiert
```

---

## Praktische Befehle

### Netzwerkstatus prüfen

```bash
ip a
ip route
nmcli device status
```

### WLANs anzeigen

```bash
nmcli device wifi list
```

### Gateway testen

```bash
ping 192.168.1.1
```

### DNS testen

```bash
ping github.com
dig github.com
```

### Nachbarn prüfen

```bash
ip neigh
```

---

## FISI-Bezug

Switching und WLAN gehören zu den häufigsten praktischen Netzwerkbereichen im FISI-Alltag.

Man braucht dieses Wissen für:

- Clients an Switches anschließen
- Switch-Ports verstehen
- VLANs einordnen
- Access Points anbinden
- WLAN-Probleme analysieren
- Gäste-WLAN planen
- DHCP-Probleme im WLAN erkennen
- Netztrennung verstehen
- PoE-Geräte einordnen
- Verkabelung und Portbelegung dokumentieren
- Fehler systematisch prüfen

Ein guter FISI unterscheidet sauber zwischen Kabelproblem, VLAN-Problem, DHCP-Problem, DNS-Problem und WLAN-Signalproblem.

---

## Kurze Zusammenfassung

Switches verbinden Geräte im lokalen Netzwerk und arbeiten hauptsächlich mit MAC-Adressen.

Managed Switches können VLANs, Trunks, Port-Security, Monitoring und weitere Funktionen unterstützen.

Access Ports gehören normalerweise zu einem VLAN. Trunk Ports transportieren mehrere VLANs.

WLAN verbindet Geräte drahtlos mit dem Netzwerk. Wichtige Begriffe sind Access Point, SSID, Frequenzband, Kanal, Signalstärke, WPA2/WPA3, Gäste-WLAN und Client-Isolation.

Für FISI ist dieses Thema wichtig, weil viele echte Netzwerkprobleme mit Switch-Ports, VLANs, DHCP, WLAN-Signal, Access Points oder falscher Konfiguration zusammenhängen.
