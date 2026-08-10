# 3.3 Grundlagen der Datenübertragung

In diesem Kapitel geht es darum, wie Daten in Netzwerken übertragen werden.

Datenübertragung ist die Grundlage jeder Netzwerkkommunikation. Wenn ein Client eine Webseite öffnet, eine Datei vom Server lädt, eine E-Mail sendet oder auf einen Drucker zugreift, werden Daten zwischen Geräten ausgetauscht.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Netzwerkprobleme nur verstanden werden können, wenn man weiß, wie Daten grundsätzlich übertragen, adressiert, verpackt und weitergeleitet werden.

---

## Kurz erklärt

Datenübertragung bedeutet, dass Informationen von einem Sender zu einem Empfänger transportiert werden.

Dafür braucht man:

- Sender
- Empfänger
- Übertragungsmedium
- Adressen
- Protokolle
- Regeln für Fehlerkontrolle
- Netzwerkgeräte zur Weiterleitung

Ein Netzwerk funktioniert nicht einfach dadurch, dass Geräte verbunden sind. Die Geräte müssen auch dieselben Regeln verstehen und wissen, wohin Daten gesendet werden sollen.

---

## Grundprinzip der Datenübertragung

Bei jeder Datenübertragung gibt es mindestens zwei Seiten.

| Bestandteil        | Bedeutung                                  |
| ------------------ | ------------------------------------------ |
| Sender             | Gerät, das Daten verschickt                |
| Empfänger          | Gerät, das Daten erhält                    |
| Übertragungsmedium | Kabel, Glasfaser, WLAN oder anderes Medium |
| Protokoll          | Regelwerk für die Kommunikation            |
| Adresse            | Zielinformation für die Zustellung         |
| Daten              | eigentliche Nutzinformation                |

Ein Client sendet zum Beispiel eine Anfrage an einen Server. Der Server verarbeitet diese Anfrage und sendet eine Antwort zurück.

---

## Daten als Bits und Bytes

Computer übertragen Daten digital.

Die kleinste Informationseinheit ist das Bit.

| Einheit  | Bedeutung                       |
| -------- | ------------------------------- |
| Bit      | kleinste Einheit, Wert 0 oder 1 |
| Byte     | besteht aus 8 Bit               |
| Kilobyte | ungefähr 1.000 Byte             |
| Megabyte | ungefähr 1 Million Byte         |
| Gigabyte | ungefähr 1 Milliarde Byte       |

In Netzwerken werden Daten als Folge von Bits übertragen. Diese Bits können über elektrische Signale, Lichtsignale oder Funkwellen transportiert werden.

---

## Signale bei der Datenübertragung

Daten müssen in Signale umgewandelt werden, damit sie über ein Medium übertragen werden können.

Je nach Medium werden unterschiedliche Signalarten genutzt.

| Medium      | Signalart                                  |
| ----------- | ------------------------------------------ |
| Kupferkabel | elektrische Signale                        |
| Glasfaser   | Lichtsignale                               |
| WLAN        | Funkwellen                                 |
| Bluetooth   | Funkwellen auf kurzer Distanz              |
| Mobilfunk   | Funkverbindung über Provider-Infrastruktur |

Das Medium beeinflusst Geschwindigkeit, Reichweite, Störanfälligkeit und Sicherheit der Übertragung.

---

## Übertragungsmedien

Übertragungsmedien transportieren Daten zwischen Geräten.

Die wichtigsten Medien in Computernetzen sind:

- Kupferkabel
- Glasfaser
- WLAN
- Mobilfunk
- Bluetooth

Jedes Medium hat eigene Stärken und Schwächen.

Kupferkabel sind im Büro sehr verbreitet. Glasfaser ist besonders gut für hohe Geschwindigkeiten und lange Strecken. WLAN ist flexibel, aber störanfälliger als Kabel.

---

## Kabelgebundene und drahtlose Übertragung

Netzwerke können kabelgebunden oder drahtlos aufgebaut sein.

| Art           | Vorteile                          | Nachteile                                  |
| ------------- | --------------------------------- | ------------------------------------------ |
| kabelgebunden | stabil, schnell, geringe Störung  | weniger flexibel, Verkabelung nötig        |
| drahtlos      | flexibel, mobil, einfache Nutzung | störanfälliger, Sicherheitsplanung wichtig |

In Unternehmen werden oft beide Arten kombiniert.

Stationäre Arbeitsplätze, Server und Netzwerkgeräte nutzen häufig LAN-Kabel. Mobile Geräte wie Laptops, Tablets und Smartphones nutzen oft WLAN.

---

## Bandbreite

Bandbreite beschreibt, wie viele Daten theoretisch pro Sekunde übertragen werden können.

Sie wird häufig angegeben in:

- Mbit/s
- Gbit/s

Beispiele:

| Angabe     | Bedeutung               |
| ---------- | ----------------------- |
| 100 Mbit/s | 100 Megabit pro Sekunde |
| 1 Gbit/s   | 1 Gigabit pro Sekunde   |
| 10 Gbit/s  | 10 Gigabit pro Sekunde  |

Wichtig: Megabit ist nicht das Gleiche wie Megabyte.

1 Byte besteht aus 8 Bit. Deshalb entsprechen 100 Mbit/s nicht 100 MB/s, sondern theoretisch ungefähr 12,5 MB/s.

---

## Durchsatz

Der Durchsatz beschreibt, wie viele Daten tatsächlich übertragen werden.

Der reale Durchsatz ist oft niedriger als die theoretische Bandbreite.

Gründe dafür:

- Protokoll-Overhead
- Netzwerkauslastung
- WLAN-Störungen
- schlechte Kabel
- langsame Endgeräte
- Switch- oder Routerleistung
- Serverauslastung
- Sicherheitsprüfung durch Firewalls
- Verschlüsselung

Bandbreite ist also der theoretische Maximalwert. Durchsatz ist das, was praktisch wirklich ankommt.

---

## Latenz

Latenz beschreibt die Verzögerung bei der Datenübertragung.

Sie wird meistens in Millisekunden gemessen.

Eine niedrige Latenz ist wichtig bei:

- Videokonferenzen
- VoIP-Telefonie
- Online-Anwendungen
- Remote Desktop
- Gaming
- Echtzeitsystemen

Eine Verbindung kann eine hohe Bandbreite haben und trotzdem schlecht wirken, wenn die Latenz sehr hoch ist.

Beispiel: Eine Dateiübertragung braucht vor allem Bandbreite. Eine Videokonferenz braucht zusätzlich niedrige Latenz und stabile Verbindung.

---

## Paketvermittlung

Moderne Netzwerke arbeiten meistens mit Paketvermittlung.

Dabei werden Daten nicht als ein großer Block übertragen, sondern in kleinere Einheiten aufgeteilt.

Diese Einheiten nennt man Pakete oder Frames, je nach Schicht und Kontext.

Vorteile der Paketvermittlung:

- mehrere Geräte können gleichzeitig kommunizieren
- Netzwerkressourcen werden effizient genutzt
- Fehler können gezielter erkannt werden
- Pakete können unterschiedliche Wege nehmen
- große Datenmengen werden besser handhabbar

Wenn eine Datei übertragen wird, wird sie in viele kleine Teile zerlegt. Beim Empfänger werden diese Teile wieder zusammengesetzt.

---

## Frames, Pakete und Segmente

In Netzwerken werden Daten auf verschiedenen Ebenen verpackt.

| Begriff   | Ebene                        | Bedeutung                      |
| --------- | ---------------------------- | ------------------------------ |
| Frame     | Sicherungsschicht / Ethernet | Datenpaket im lokalen Netzwerk |
| Paket     | Netzwerkschicht / IP         | Datenpaket mit IP-Adressen     |
| Segment   | Transportschicht / TCP       | Teil einer TCP-Verbindung      |
| Datagramm | Transportschicht / UDP       | UDP-Dateneinheit               |

Diese Begriffe hängen mit dem Schichtenmodell zusammen.

Für den Anfang ist wichtig: Daten werden verpackt, adressiert, übertragen und beim Empfänger wieder verarbeitet.

---

## Protokolle

Ein Protokoll ist ein Regelwerk für Kommunikation.

Protokolle legen fest:

- wie Daten aufgebaut sind
- wie Geräte sich identifizieren
- wie Verbindungen aufgebaut werden
- wie Fehler erkannt werden
- wie Daten weitergeleitet werden
- wie Empfänger und Sender zusammenarbeiten

Ohne Protokolle könnten Geräte verschiedener Hersteller nicht zuverlässig miteinander kommunizieren.

Wichtige Netzwerkprotokolle sind zum Beispiel:

| Protokoll  | Aufgabe                                 |
| ---------- | --------------------------------------- |
| Ethernet   | Übertragung im lokalen Netzwerk         |
| IP         | logische Adressierung und Weiterleitung |
| TCP        | zuverlässige Datenübertragung           |
| UDP        | schnelle verbindungslose Übertragung    |
| DNS        | Namensauflösung                         |
| DHCP       | automatische Netzwerkkonfiguration      |
| HTTP/HTTPS | Webseiten und Webanwendungen            |
| SMB        | Datei- und Druckfreigaben               |
| SSH        | sichere Fernadministration              |

---

## Ethernet

Ethernet ist ein sehr wichtiger Standard für lokale Netzwerke.

Es wird vor allem in kabelgebundenen LANs genutzt.

Ethernet beschreibt unter anderem:

- Datenübertragung im LAN
- Frames
- MAC-Adressen
- Zugriffsverfahren
- Geschwindigkeiten
- Verkabelungsstandards
- Kommunikation zwischen Netzwerkkarten und Switches

Typische Ethernet-Geschwindigkeiten:

| Standard                   | Geschwindigkeit         |
| -------------------------- | ----------------------- |
| Fast Ethernet              | 100 Mbit/s              |
| Gigabit Ethernet           | 1 Gbit/s                |
| 10 Gigabit Ethernet        | 10 Gbit/s               |
| 25/40/100 Gigabit Ethernet | häufig im Rechenzentrum |

Heute ist 1 Gbit/s bei Arbeitsplatznetzen sehr verbreitet. In Serverräumen und Rechenzentren werden oft höhere Geschwindigkeiten genutzt.

---

## MAC-Adresse

Eine MAC-Adresse ist die Hardwareadresse einer Netzwerkschnittstelle.

Sie wird im lokalen Netzwerk verwendet.

Eigenschaften:

- normalerweise weltweit eindeutig
- gehört zur Netzwerkkarte oder WLAN-Schnittstelle
- wird auf Ethernet-Ebene genutzt
- hilft Switches bei der Weiterleitung im LAN

Ein Switch lernt, welche MAC-Adresse an welchem Port erreichbar ist. Dadurch kann er Frames gezielt weiterleiten.

---

## IP-Adresse

Eine IP-Adresse ist eine logische Adresse in einem Netzwerk.

Sie wird genutzt, damit Geräte über Netzwerke hinweg kommunizieren können.

Es gibt zwei wichtige Versionen:

| Version | Beispiel     |
| ------- | ------------ |
| IPv4    | 192.168.1.10 |
| IPv6    | 2001:db8::1  |

IPv4 ist noch sehr weit verbreitet. IPv6 wird immer wichtiger, weil IPv4-Adressen begrenzt sind.

IP-Adressen gehören zur logischen Netzwerkkommunikation. Sie können manuell gesetzt oder automatisch per DHCP vergeben werden.

---

## TCP/IP

TCP/IP ist die Grundlage moderner Netzwerke und des Internets.

Der Begriff beschreibt eine Protokollfamilie, nicht nur zwei einzelne Protokolle.

Wichtige Bestandteile sind:

- IP
- TCP
- UDP
- ICMP
- DNS
- DHCP
- HTTP/HTTPS
- viele weitere Protokolle

TCP/IP ermöglicht, dass Geräte in lokalen Netzwerken und über das Internet miteinander kommunizieren können.

---

## IP als Vermittlung

IP ist für logische Adressierung und Weiterleitung zuständig.

IP beantwortet die Frage:

> Wohin soll dieses Paket gesendet werden?

IP arbeitet mit:

- Quell-IP-Adresse
- Ziel-IP-Adresse
- Subnetz
- Gateway
- Routing

IP garantiert aber nicht, dass Daten vollständig oder in richtiger Reihenfolge ankommen. Dafür ist bei zuverlässiger Übertragung TCP zuständig.

---

## TCP

TCP bedeutet **Transmission Control Protocol**.

TCP sorgt für zuverlässige Datenübertragung.

Eigenschaften:

- verbindungsorientiert
- bestätigt empfangene Daten
- erkennt fehlende Daten
- sendet verlorene Daten erneut
- stellt Reihenfolge sicher
- kontrolliert Datenfluss

TCP wird verwendet, wenn Zuverlässigkeit wichtiger ist als maximale Geschwindigkeit.

Typische Anwendungen:

- Webseiten über HTTPS
- Dateiübertragung
- E-Mail
- SSH
- viele Datenbankverbindungen

---

## UDP

UDP bedeutet **User Datagram Protocol**.

UDP ist verbindungslos und einfacher als TCP.

Eigenschaften:

- kein Verbindungsaufbau wie bei TCP
- keine automatische Wiederholung verlorener Daten
- weniger Overhead
- oft schneller
- gut für zeitkritische Anwendungen

UDP wird genutzt, wenn Geschwindigkeit und geringe Verzögerung wichtiger sind als perfekte Vollständigkeit.

Typische Anwendungen:

- DNS-Anfragen
- VoIP
- Videostreaming
- Online-Spiele
- DHCP
- manche VPN-Protokolle

---

## TCP und UDP im Vergleich

| Merkmal         | TCP                     | UDP                  |
| --------------- | ----------------------- | -------------------- |
| Verbindung      | verbindungsorientiert   | verbindungslos       |
| Zuverlässigkeit | hoch                    | keine Garantie       |
| Reihenfolge     | wird sichergestellt     | nicht garantiert     |
| Geschwindigkeit | mehr Overhead           | weniger Overhead     |
| Einsatz         | Dateien, Webseiten, SSH | DNS, VoIP, Streaming |

TCP ist wie ein kontrollierter Versand mit Bestätigung.  
UDP ist eher wie schnelles Senden ohne Rückfrage.

Beide Protokolle sind wichtig und haben unterschiedliche Einsatzbereiche.

---

## Ports

Ports helfen dabei, Daten an die richtige Anwendung auf einem Gerät zuzustellen.

Eine IP-Adresse bestimmt das Gerät.  
Ein Port bestimmt den Dienst oder die Anwendung auf diesem Gerät.

Beispiele:

|  Port | Protokoll / Dienst |
| ----: | ------------------ |
|    22 | SSH                |
|    53 | DNS                |
| 67/68 | DHCP               |
|    80 | HTTP               |
|   443 | HTTPS              |
|   445 | SMB                |
|  3389 | RDP                |

Wenn ein Client eine Webseite über HTTPS öffnet, verbindet er sich normalerweise mit Port 443 des Zielservers.

Ports sind auch für Firewall-Regeln wichtig.

---

## Sockets

Ein Socket beschreibt die Kombination aus IP-Adresse und Port.

Beispiel:

```text
192.168.1.20:443
```
