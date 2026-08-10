# 3.4 Netzwerkstrukturen, Komponenten, Standards und Modelle

In diesem Kapitel geht es um den Aufbau von Netzwerken, wichtige Netzwerkstrukturen, Übertragungsmedien, Netzwerkkomponenten, Standards und Schichtenmodelle.

Netzwerke funktionieren nicht zufällig. Sie sind nach technischen Regeln, Standards und Modellen aufgebaut. Diese sorgen dafür, dass Geräte unterschiedlicher Hersteller miteinander kommunizieren können.

Für Fachinformatiker für Systemintegration ist dieses Kapitel besonders wichtig, weil man Netzwerke nur dann sauber planen, dokumentieren und analysieren kann, wenn man ihre Struktur und technischen Grundlagen versteht.

---

## Kurz erklärt

Ein Netzwerk besteht aus mehreren Geräten, Verbindungen, Adressen, Protokollen und Regeln.

Wichtige Themen in diesem Kapitel sind:

- Netzwerktopologien
- strukturierte Verkabelung
- Kupferkabel, Glasfaser und WLAN
- OSI-Modell
- TCP/IP-Modell
- MAC-Adressen und IP-Adressen
- Switches, Router, Firewalls und Access Points
- Netzwerkstandards
- LAN, WLAN, WAN und VLAN
- Dokumentation und Netzpläne

Diese Grundlagen helfen dabei, Netzwerke logisch zu verstehen und Fehler systematisch einzugrenzen.

---

## Netzwerkstruktur

Die Netzwerkstruktur beschreibt, wie ein Netzwerk aufgebaut ist.

Dabei geht es um Fragen wie:

- Welche Geräte gibt es?
- Wie sind Geräte miteinander verbunden?
- Welche Netzbereiche existieren?
- Welche Server stellen Dienste bereit?
- Welche Switches und Router werden genutzt?
- Wie erfolgt der Zugriff auf das Internet?
- Gibt es WLAN, VLANs oder VPN?
- Wie wird Sicherheit umgesetzt?
- Wie ist alles dokumentiert?

Eine klare Netzwerkstruktur erleichtert Verwaltung, Fehlersuche, Erweiterung und Sicherheit.

---

## Physische und logische Struktur

Bei Netzwerken unterscheidet man zwischen physischer und logischer Struktur.

| Struktur           | Bedeutung                                            |
| ------------------ | ---------------------------------------------------- |
| physische Struktur | tatsächliche Verkabelung und Geräteverbindungen      |
| logische Struktur  | IP-Netze, VLANs, Routing, Dienste und Berechtigungen |

Die physische Struktur zeigt, wie Geräte wirklich verbunden sind.

Die logische Struktur zeigt, wie das Netzwerk technisch organisiert ist.

Beispiel:

Ein PC ist physisch mit einem Switch verbunden.  
Logisch kann er aber in einem bestimmten VLAN sein und nur Zugriff auf bestimmte Dienste haben.

---

## Netzwerktopologie

Eine Netzwerktopologie beschreibt die Anordnung und Verbindung von Geräten in einem Netzwerk.

Topologien helfen dabei zu verstehen, wie Daten durch ein Netzwerk fließen und welche Auswirkungen ein Ausfall einzelner Komponenten haben kann.

Wichtige Topologien:

| Topologie        | Erklärung                                           |
| ---------------- | --------------------------------------------------- |
| Bus-Topologie    | alle Geräte teilen sich eine gemeinsame Leitung     |
| Ring-Topologie   | Geräte sind ringförmig verbunden                    |
| Stern-Topologie  | Geräte sind mit einem zentralen Punkt verbunden     |
| Baum-Topologie   | mehrere Sternstrukturen sind hierarchisch verbunden |
| Mesh-Topologie   | Geräte sind mehrfach miteinander verbunden          |
| Hybrid-Topologie | Kombination aus mehreren Topologien                 |

In modernen LANs ist die Stern- oder Baumstruktur besonders verbreitet.

---

## Bus-Topologie

Bei der Bus-Topologie hängen alle Geräte an einer gemeinsamen Leitung.

Eigenschaften:

- einfache Struktur
- früher in alten Netzwerken genutzt
- alle Geräte teilen sich dasselbe Medium
- Fehler auf der Hauptleitung betreffen alle Geräte
- schlecht skalierbar
- heute kaum noch relevant für moderne Ethernet-LANs

Die Bus-Topologie ist historisch wichtig, spielt aber in heutigen Unternehmensnetzwerken kaum noch eine praktische Rolle.

---

## Ring-Topologie

Bei der Ring-Topologie sind Geräte in einem geschlossenen Kreis verbunden.

Daten laufen von Gerät zu Gerät weiter.

Eigenschaften:

- klare Richtung des Datenflusses
- jedes Gerät ist Teil der Verbindung
- Ausfall eines Geräts kann den Ring stören
- spezielle Varianten können Ausfallsicherheit erhöhen

Ringstrukturen findet man heute eher in speziellen oder industriellen Netzwerken, nicht typisch bei normalen Büro-LANs.

---

## Stern-Topologie

Bei der Stern-Topologie sind alle Geräte mit einem zentralen Gerät verbunden, meistens einem Switch.

Eigenschaften:

- sehr verbreitet in LANs
- einfache Fehlersuche
- einzelne Client-Ausfälle beeinflussen andere Geräte kaum
- zentrale Komponente ist wichtig
- leicht erweiterbar

Wenn ein einzelner PC ausfällt, bleibt das Netzwerk meistens funktionsfähig. Wenn aber der zentrale Switch ausfällt, sind alle daran angeschlossenen Geräte betroffen.

---

## Baum-Topologie

Die Baum-Topologie ist eine hierarchische Struktur aus mehreren Sternen.

Typisch ist zum Beispiel:

- Core-Switch
- Distribution-Switches
- Access-Switches
- Clients an Access-Switches

Diese Struktur wird häufig in größeren Unternehmensnetzwerken genutzt.

Vorteile:

- gut erweiterbar
- übersichtliche Struktur
- klare Ebenen
- gut dokumentierbar
- geeignet für größere Gebäude oder Standorte

---

## Mesh-Topologie

Bei der Mesh-Topologie sind Geräte mehrfach miteinander verbunden.

Es gibt mehrere mögliche Wege zwischen Netzwerkknoten.

Vorteile:

- hohe Ausfallsicherheit
- alternative Wege bei Störungen
- gut für kritische Netzwerkbereiche

Nachteile:

- aufwendiger
- teurer
- komplexere Planung
- schwieriger zu dokumentieren

Mesh-Strukturen werden häufig bei Backbone-Verbindungen, Standortvernetzung oder drahtlosen Mesh-Netzen genutzt.

---

## Strukturierte Verkabelung

Strukturierte Verkabelung bedeutet, dass die Netzwerkverkabelung nach einem klaren, standardisierten Konzept aufgebaut ist.

Ziel ist eine flexible, wartbare und langfristig nutzbare Verkabelungsstruktur.

Typische Bestandteile:

- Etagenverteiler
- Gebäudeverteiler
- Patchpanel
- Netzwerkschrank
- Switches
- Verlegekabel
- Patchkabel
- Netzwerkdosen
- Beschriftung
- Dokumentation

Strukturierte Verkabelung ist wichtig, weil Netzwerke oft viele Jahre genutzt und erweitert werden.

---

## Vorteile strukturierter Verkabelung

Eine strukturierte Verkabelung bietet viele Vorteile:

- bessere Übersicht
- einfachere Fehlersuche
- saubere Dokumentation
- flexible Arbeitsplatzänderungen
- bessere Erweiterbarkeit
- professioneller Betrieb
- weniger Kabelchaos
- einfachere Wartung
- klare Zuordnung von Ports und Räumen

Ohne strukturierte Verkabelung wird ein Netzwerk schnell unübersichtlich und schwer wartbar.

---

## Patchpanel

Ein Patchpanel ist ein Anschlussfeld im Netzwerkschrank.

Dort enden die fest verlegten Netzwerkkabel aus den Räumen.

Aufgaben eines Patchpanels:

- Verbindung zwischen Gebäudeverkabelung und Switch
- saubere Organisation von Kabeln
- einfache Änderung von Portzuordnungen
- bessere Dokumentation
- Schutz der fest verlegten Kabel

Ein Patchpanel wird mit kurzen Patchkabeln mit Switch-Ports verbunden.

---

## Netzwerkschrank

Ein Netzwerkschrank enthält zentrale Netzwerkkomponenten.

Dazu können gehören:

- Patchpanel
- Switches
- Router
- Firewalls
- USV
- Kabelmanagement
- Server
- NAS-Systeme
- Stromleisten
- Lüfter oder Kühlung

Ein Netzwerkschrank sollte ordentlich beschriftet, gesichert und dokumentiert sein.

Unordnung im Netzwerkschrank erschwert Wartung und Fehlersuche.

---

## Kupferkabel

Kupferkabel werden sehr häufig für Ethernet-Netzwerke genutzt.

Typisch ist Twisted-Pair-Kabel mit RJ45-Steckern.

Wichtige Eigenschaften:

- weit verbreitet
- relativ günstig
- einfach zu installieren
- gut für Büroarbeitsplätze
- typische maximale Länge bei Ethernet: 100 Meter pro Verbindung
- anfälliger für elektromagnetische Störungen als Glasfaser

Häufige Kabelkategorien:

| Kategorie      | Typische Nutzung                              |
| -------------- | --------------------------------------------- |
| Cat 5e         | Gigabit Ethernet möglich                      |
| Cat 6          | bessere Übertragungseigenschaften             |
| Cat 6A         | häufig für 10 Gigabit Ethernet geeignet       |
| Cat 7 / Cat 7A | hohe Schirmung, häufig in Gebäudeverkabelung  |
| Cat 8          | sehr hohe Geschwindigkeit auf kurzen Strecken |

Die Kabelkategorie muss zur geplanten Geschwindigkeit und Umgebung passen.

---

## Twisted Pair

Twisted Pair bedeutet, dass Adernpaare im Kabel miteinander verdrillt sind.

Diese Verdrillung reduziert Störungen und verbessert die Signalqualität.

Es gibt unterschiedliche Schirmungsarten.

| Bezeichnung | Bedeutung                                              |
| ----------- | ------------------------------------------------------ |
| U/UTP       | ungeschirmtes Kabel                                    |
| F/UTP       | Gesamtschirm aus Folie                                 |
| S/FTP       | Geflechtschirm und paarweise Folienschirmung           |
| SF/FTP      | Geflecht und Folie als Gesamtschirm plus Paarschirmung |

In störungsreichen Umgebungen sind besser geschirmte Kabel sinnvoll.

---

## Glasfaser

Glasfaser überträgt Daten mit Licht.

Sie wird häufig für schnelle Verbindungen, lange Strecken oder Backbone-Verbindungen genutzt.

Vorteile:

- sehr hohe Bandbreite
- lange Strecken möglich
- unempfindlich gegen elektromagnetische Störungen
- geeignet für Gebäudeverbindungen
- wichtig im Rechenzentrum
- schwerer abzuhören als Kupfer

Nachteile:

- empfindlicher bei unsachgemäßer Handhabung
- teurere Komponenten
- spezielles Werkzeug und Know-how nötig
- Stecker und Fasertypen müssen passen

---

## Singlemode und Multimode

Bei Glasfaser unterscheidet man häufig zwischen Singlemode und Multimode.

| Typ        | Eigenschaften                                                              |
| ---------- | -------------------------------------------------------------------------- |
| Singlemode | sehr lange Strecken, kleiner Faserkern, meist teurer                       |
| Multimode  | kürzere Strecken, größerer Faserkern, häufig im Gebäude oder Rechenzentrum |

Singlemode wird oft für lange Strecken genutzt.  
Multimode wird häufig innerhalb von Gebäuden oder Rechenzentren eingesetzt.

Die Wahl hängt von Entfernung, Geschwindigkeit, Kosten und vorhandener Infrastruktur ab.

---

## WLAN als Netzwerkmedium

WLAN überträgt Daten über Funk.

Es ist besonders wichtig für mobile Geräte.

Wichtige WLAN-Themen:

- SSID
- Frequenzband
- Kanalwahl
- Verschlüsselung
- Signalstärke
- Reichweite
- Roaming
- Access-Point-Positionierung
- Störungen
- Gastnetz
- VLAN-Zuordnung

WLAN ist flexibler als Kabel, aber auch schwieriger zuverlässig zu planen.

Wände, Metall, andere Funknetze und viele gleichzeitige Benutzer können die Leistung stark beeinflussen.

---

## Netzwerkmodelle

Netzwerkmodelle helfen, Kommunikation in Schichten zu verstehen.

Die wichtigsten Modelle sind:

- OSI-Modell
- TCP/IP-Modell

Diese Modelle zeigen, welche Aufgaben auf welcher Ebene stattfinden.

Das ist wichtig für Fehlersuche, weil Netzwerkprobleme oft auf bestimmten Ebenen eingegrenzt werden können.

---

## OSI-Modell

Das OSI-Modell besteht aus sieben Schichten.

Jede Schicht hat eine bestimmte Aufgabe.

| Schicht | Name           | Aufgabe                                        |
| ------: | -------------- | ---------------------------------------------- |
|       7 | Anwendung      | Dienste für Anwendungen                        |
|       6 | Darstellung    | Datenformat, Verschlüsselung, Codierung        |
|       5 | Sitzung        | Aufbau und Steuerung von Sitzungen             |
|       4 | Transport      | Ende-zu-Ende-Kommunikation, TCP/UDP            |
|       3 | Vermittlung    | IP-Adressen und Routing                        |
|       2 | Sicherung      | MAC-Adressen, Frames, Switches                 |
|       1 | Bitübertragung | Kabel, Funk, elektrische oder optische Signale |

Das OSI-Modell ist ein Lern- und Analysemodell. Es hilft, Netzwerkkommunikation besser zu strukturieren.

---

## Schicht 1: Bitübertragung

Schicht 1 beschreibt die physische Übertragung von Bits.

Dazu gehören:

- Kabel
- Glasfaser
- WLAN-Funk
- Stecker
- elektrische Signale
- Lichtsignale
- Funkfrequenzen
- Netzwerkkarten
- Repeater
- physische Verbindung

Typische Probleme auf Schicht 1:

- Kabel defekt
- Stecker lose
- falscher Port
- kein Link
- WLAN-Signal zu schwach
- Glasfaser falsch gesteckt
- Gerät hat keinen Strom

---

## Schicht 2: Sicherung

Schicht 2 sorgt für Kommunikation im lokalen Netzwerk.

Wichtige Begriffe:

- Ethernet
- Frames
- MAC-Adressen
- Switch
- VLAN
- Fehlererkennung
- lokale Weiterleitung

Ein Switch arbeitet hauptsächlich auf Schicht 2. Er lernt MAC-Adressen und leitet Frames an passende Ports weiter.

Typische Probleme auf Schicht 2:

- falsches VLAN
- MAC-Adressproblem
- Switch-Port deaktiviert
- Port-Security blockiert Gerät
- Duplex- oder Speed-Probleme
- Loop im Netzwerk

---

## Schicht 3: Vermittlung

Schicht 3 ist für logische Adressierung und Routing zuständig.

Wichtige Begriffe:

- IP-Adresse
- Subnetz
- Router
- Gateway
- Routingtabelle
- ICMP
- IPv4
- IPv6

Ein Router arbeitet auf Schicht 3 und verbindet unterschiedliche Netzwerke miteinander.

Typische Probleme auf Schicht 3:

- falsche IP-Adresse
- falsche Subnetzmaske
- falsches Gateway
- Routingfehler
- IP-Konflikt
- Zielnetz nicht erreichbar

---

## Schicht 4: Transport

Schicht 4 sorgt für die Kommunikation zwischen Anwendungen auf verschiedenen Systemen.

Wichtige Protokolle:

- TCP
- UDP

Wichtige Begriffe:

- Ports
- Verbindungen
- Zuverlässigkeit
- Sequenzierung
- Flusskontrolle
- Paketverlust

Typische Probleme auf Schicht 4:

- Port blockiert
- Dienst lauscht nicht
- Firewall blockiert Verbindung
- TCP-Verbindung kann nicht aufgebaut werden
- UDP-Verkehr wird gefiltert

---

## Schichten 5 bis 7

Die oberen Schichten betreffen Anwendungen, Sitzungen und Datenformate.

Wichtige Themen:

- Anwendungsprotokolle
- Verschlüsselung
- Zertifikate
- Authentifizierung
- Datenformate
- Sitzungsverwaltung
- Benutzerzugriff

Beispiele:

- HTTPS
- DNS
- SMB
- SSH
- SMTP
- IMAP
- RDP

Viele praktische Fehler zeigen sich auf Anwendungsebene, haben aber ihre Ursache manchmal in tieferen Schichten.

---

## TCP/IP-Modell

Das TCP/IP-Modell ist praxisnah und beschreibt die Kommunikation im Internet und modernen Netzwerken.

Es wird oft in vier Schichten dargestellt.

| TCP/IP-Schicht | Vergleich zum OSI-Modell | Aufgabe                                    |
| -------------- | ------------------------ | ------------------------------------------ |
| Anwendung      | OSI 5–7                  | Anwendungen und Dienste                    |
| Transport      | OSI 4                    | TCP und UDP                                |
| Internet       | OSI 3                    | IP und Routing                             |
| Netzzugang     | OSI 1–2                  | Ethernet, WLAN, MAC, physische Übertragung |

Das TCP/IP-Modell ist besonders wichtig, weil TCP/IP die Grundlage des Internets ist.

---

## OSI-Modell und Fehlersuche

Das OSI-Modell hilft bei der systematischen Fehlersuche.

Eine einfache Denkweise ist:

1. Gibt es eine physische Verbindung?
2. Funktioniert die lokale Verbindung?
3. Hat das Gerät eine gültige IP-Adresse?
4. Ist das Gateway erreichbar?
5. Funktioniert DNS?
6. Ist der benötigte Port erreichbar?
7. Funktioniert die Anwendung?

Dadurch springt man nicht direkt zu komplizierten Ursachen, sondern prüft von unten nach oben.

---

## Adressen im Netzwerk

In Netzwerken gibt es verschiedene Arten von Adressen.

| Adresse     | Ebene           | Aufgabe                            |
| ----------- | --------------- | ---------------------------------- |
| MAC-Adresse | Schicht 2       | lokale Hardwareadresse             |
| IP-Adresse  | Schicht 3       | logische Netzwerkadresse           |
| Port        | Schicht 4       | Zuordnung zu Anwendung oder Dienst |
| DNS-Name    | Anwendungsebene | menschenlesbarer Name              |

Diese Adressen erfüllen unterschiedliche Aufgaben und dürfen nicht verwechselt werden.

---

## MAC-Adresse

Eine MAC-Adresse ist die Hardwareadresse einer Netzwerkschnittstelle.

Sie wird für die Kommunikation im lokalen Netzwerk verwendet.

Eigenschaften:

- besteht aus 48 Bit
- wird meist hexadezimal dargestellt
- ist einer Netzwerkschnittstelle zugeordnet
- wird von Switches zur Weiterleitung genutzt
- arbeitet auf Schicht 2

Beispielhafte Darstellung:

```text
A4:5E:60:12:AB:9F
```
