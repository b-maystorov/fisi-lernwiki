# 3.7 Netzwerkkomponenten auswählen und konfigurieren

In diesem Kapitel geht es darum, wichtige Netzwerkkomponenten auszuwählen, technisch einzuordnen und grundlegend zu konfigurieren.

Netzwerkkomponenten verbinden Clients, Server, Drucker, Access Points, Firewalls, Router und andere Systeme miteinander. Damit ein Netzwerk zuverlässig funktioniert, müssen die passenden Geräte gewählt, korrekt eingebaut, sicher konfiguriert und dokumentiert werden.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr wichtig, weil Netzwerkgeräte die Grundlage für Kommunikation, Sicherheit, Verfügbarkeit und Verwaltung bilden.

---

## Kurz erklärt

Netzwerkkomponenten sind Geräte oder Bauteile, die Kommunikation in einem Netzwerk ermöglichen oder steuern.

Wichtige Netzwerkkomponenten sind:

- Netzwerkkarte
- Switch
- Router
- Firewall
- Access Point
- Modem
- Patchpanel
- Medienkonverter
- Netzwerkkabel
- Server
- NAS
- USV

Bei der Auswahl geht es nicht nur um Geschwindigkeit. Wichtig sind auch Sicherheit, Verwaltbarkeit, Kompatibilität, Erweiterbarkeit, Stromversorgung, Support und Dokumentation.

---

## Fachliche Einordnung

Ein Netzwerkgerät erfüllt immer eine bestimmte Rolle im Gesamtsystem.

| Komponente      | Hauptaufgabe                                     |
| --------------- | ------------------------------------------------ |
| Netzwerkkarte   | verbindet ein Endgerät mit dem Netzwerk          |
| Switch          | verbindet Geräte im lokalen Netzwerk             |
| Router          | verbindet unterschiedliche Netzwerke             |
| Firewall        | kontrolliert und filtert Netzwerkverkehr         |
| Access Point    | stellt WLAN bereit                               |
| Modem           | stellt Verbindung zum Provider her               |
| Patchpanel      | verbindet Gebäudeverkabelung mit Netzwerktechnik |
| Medienkonverter | wandelt ein Übertragungsmedium in ein anderes um |
| NAS             | stellt Speicher im Netzwerk bereit               |
| USV             | schützt Geräte vor Stromausfall                  |

Ein gutes Netzwerk entsteht nicht durch einzelne starke Geräte, sondern durch sinnvoll ausgewählte und korrekt konfigurierte Komponenten.

---

## Auswahlkriterien für Netzwerkkomponenten

Bei der Auswahl von Netzwerkkomponenten müssen technische und organisatorische Anforderungen berücksichtigt werden.

Wichtige Kriterien sind:

| Kriterium        | Bedeutung                                              |
| ---------------- | ------------------------------------------------------ |
| Einsatzbereich   | Büro, Serverraum, Rechenzentrum, Homeoffice            |
| Leistung         | Geschwindigkeit, Durchsatz, gleichzeitige Verbindungen |
| Portanzahl       | Anzahl benötigter Anschlüsse                           |
| Verwaltbarkeit   | Webinterface, CLI, zentrale Verwaltung                 |
| Sicherheit       | Firewallfunktionen, VLANs, Authentifizierung           |
| Kompatibilität   | passt zu vorhandener Infrastruktur                     |
| Erweiterbarkeit  | spätere Erweiterung möglich                            |
| Zuverlässigkeit  | Stabilität, Herstellerqualität, Garantie               |
| Energieverbrauch | wichtig für Betriebskosten und Green IT                |
| Support          | Updates, Dokumentation, Ersatzteile                    |
| Kosten           | Anschaffung und Betrieb                                |

Die Auswahl sollte immer aus den Anforderungen abgeleitet werden.

---

## Netzwerkkarte

Eine Netzwerkkarte verbindet ein Gerät mit einem Netzwerk.

Sie kann intern eingebaut oder extern angeschlossen sein.

Arten von Netzwerkkarten:

| Art                     | Erklärung                                              |
| ----------------------- | ------------------------------------------------------ |
| Ethernet-Netzwerkkarte  | kabelgebundene Verbindung über RJ45                    |
| WLAN-Adapter            | drahtlose Verbindung über Funk                         |
| USB-Netzwerkadapter     | externer Adapter über USB                              |
| Glasfaser-Netzwerkkarte | Verbindung über optische Medien                        |
| Server-Netzwerkkarte    | oft mehrere Ports, höhere Leistung, bessere Verwaltung |

Die Netzwerkkarte besitzt eine MAC-Adresse und kann eine IP-Adresse erhalten.

---

## Wichtige Eigenschaften einer Netzwerkkarte

Bei Netzwerkkarten achtet man auf:

- Geschwindigkeit
- Schnittstelle
- Treibersupport
- Betriebssystemkompatibilität
- Wake-on-LAN
- VLAN-Unterstützung
- Energieoptionen
- Duplex-Unterstützung
- Stabilität
- Firmware oder Treiberstand

Typische Geschwindigkeiten:

| Geschwindigkeit    | Einsatz                            |
| ------------------ | ---------------------------------- |
| 100 Mbit/s         | ältere Geräte                      |
| 1 Gbit/s           | Standard bei vielen Clients        |
| 2,5 Gbit/s         | moderne Clients oder kleine Server |
| 10 Gbit/s          | Server, NAS, Workstations          |
| 25 Gbit/s und mehr | Rechenzentrum                      |

Für normale Arbeitsplatzrechner ist 1 Gbit/s häufig ausreichend. Für Server, NAS oder Virtualisierung kann mehr Bandbreite sinnvoll sein.

---

## Switch

Ein Switch verbindet mehrere Geräte innerhalb eines lokalen Netzwerks.

Er arbeitet hauptsächlich mit MAC-Adressen und leitet Ethernet-Frames gezielt an den passenden Port weiter.

Typische Aufgaben eines Switches:

- Clients mit dem LAN verbinden
- Server mit dem Netzwerk verbinden
- Drucker und Access Points anbinden
- VLANs bereitstellen
- Ports verwalten
- Netzwerkverkehr innerhalb eines LANs weiterleiten
- PoE-Geräte mit Strom versorgen
- Netzwerksegmente verbinden

Switches sind zentrale Komponenten in fast jedem Unternehmensnetzwerk.

---

## Unmanaged Switch

Ein unmanaged Switch funktioniert ohne Konfiguration.

Eigenschaften:

- einfach einzusetzen
- günstiger
- keine oder kaum Einstellungsmöglichkeiten
- keine VLAN-Konfiguration
- kaum Monitoring
- für kleine, einfache Umgebungen geeignet

Unmanaged Switches sind für professionelle Netzwerke oft nur eingeschränkt geeignet, weil Verwaltung, Sicherheit und Transparenz fehlen.

---

## Managed Switch

Ein managed Switch kann konfiguriert und überwacht werden.

Wichtige Funktionen:

- VLANs
- Trunk-Ports
- Access-Ports
- Port-Security
- Spanning Tree Protocol
- Link Aggregation
- PoE-Verwaltung
- Management-IP
- Logging
- Monitoring
- SNMP
- QoS
- Firmwareupdates

Managed Switches sind in Unternehmensnetzwerken meistens die bessere Wahl, weil sie mehr Kontrolle und Sicherheit ermöglichen.

---

## Switch-Auswahl

Bei der Auswahl eines Switches achtet man auf:

- Anzahl der Ports
- Portgeschwindigkeit
- PoE-Budget
- VLAN-Unterstützung
- Managementfunktionen
- Uplink-Ports
- Glasfaser- oder SFP-Unterstützung
- Rack-Einbau
- Lüfterlautstärke
- Stromverbrauch
- Hersteller-Support
- Redundanzoptionen
- Sicherheitsfunktionen

Ein Switch sollte nicht nur für die aktuelle Anzahl von Geräten reichen, sondern auch etwas Reserve für Erweiterungen bieten.

---

## VLAN-Konfiguration auf Switches

VLANs trennen ein physisches Netzwerk logisch in mehrere Netzbereiche.

Typische VLANs:

| VLAN            | Zweck                          |
| --------------- | ------------------------------ |
| Client-VLAN     | normale Arbeitsplatzrechner    |
| Server-VLAN     | Serverdienste                  |
| Gast-VLAN       | Gästezugang                    |
| Management-VLAN | Verwaltung von Netzwerkgeräten |
| VoIP-VLAN       | IP-Telefone                    |
| WLAN-VLAN       | drahtlose Clients              |

Wichtige Porttypen:

| Porttyp       | Bedeutung                          |
| ------------- | ---------------------------------- |
| Access-Port   | gehört zu einem einzelnen VLAN     |
| Trunk-Port    | transportiert mehrere VLANs        |
| Tagged VLAN   | VLAN-Information wird mitgesendet  |
| Untagged VLAN | VLAN wird am Port ohne Tag genutzt |

Ein normaler Client hängt meistens an einem Access-Port. Verbindungen zwischen Switches oder zu Firewalls laufen oft über Trunk-Ports.

---

## Port-Security

Port-Security begrenzt, welche Geräte an einem Switch-Port erlaubt sind.

Mögliche Funktionen:

- nur bestimmte MAC-Adressen erlauben
- Anzahl der MAC-Adressen begrenzen
- unbekannte Geräte blockieren
- Verstöße protokollieren
- Port automatisch deaktivieren

Port-Security kann helfen, unbefugte Geräte im Netzwerk zu verhindern.

Sie muss aber sauber geplant werden, damit legitime Geräte nicht versehentlich blockiert werden.

---

## Spanning Tree Protocol

Spanning Tree Protocol, kurz STP, schützt Ethernet-Netzwerke vor Schleifen.

Eine Netzwerkschleife kann entstehen, wenn Switches mehrfach miteinander verbunden sind und Frames endlos im Netzwerk kreisen.

Folgen einer Schleife:

- Broadcast-Stürme
- hohe Netzwerklast
- instabile Verbindungen
- Ausfall ganzer Netzbereiche
- Switches werden überlastet

STP erkennt redundante Verbindungen und blockiert bestimmte Wege, damit keine Schleifen entstehen.

In professionellen Switch-Netzen ist STP ein wichtiges Schutzverfahren.

---

## Link Aggregation

Link Aggregation bündelt mehrere physische Netzwerkverbindungen zu einer logischen Verbindung.

Vorteile:

- höhere Gesamtbandbreite
- bessere Ausfallsicherheit
- Lastverteilung
- sinnvoll für Server, NAS oder Switch-Uplinks

Eine häufige Technik ist LACP.

Link Aggregation muss auf beiden Seiten korrekt unterstützt und konfiguriert werden.

---

## PoE

PoE bedeutet **Power over Ethernet**.

Dabei werden Daten und Strom über dasselbe Netzwerkkabel übertragen.

Typische PoE-Geräte:

- Access Points
- IP-Telefone
- Überwachungskameras
- kleine Netzwerkgeräte
- Sensoren

Wichtige Punkte:

- Switch muss PoE unterstützen
- Endgerät muss PoE unterstützen
- PoE-Budget des Switches beachten
- Kabelqualität beachten
- Standard beachten

PoE erleichtert die Installation, weil nicht jedes Gerät ein eigenes Netzteil braucht.

---

## Router

Ein Router verbindet unterschiedliche Netzwerke miteinander.

Er arbeitet auf Basis von IP-Adressen und Routingtabellen.

Typische Aufgaben:

- LAN mit Internet verbinden
- verschiedene Subnetze verbinden
- Standortvernetzung ermöglichen
- VPN-Verbindungen bereitstellen
- Routing zwischen VLANs ermöglichen
- Datenpakete weiterleiten
- Gateway für Clients sein

Ein Router entscheidet, welchen Weg ein IP-Paket nehmen soll.

---

## Routing

Routing bedeutet Weiterleitung von IP-Paketen zwischen Netzwerken.

Ein Router nutzt dafür Routingtabellen.

Eine Routingtabelle enthält Informationen wie:

- Zielnetz
- nächster Hop
- Ausgangsschnittstelle
- Metrik oder Kosten
- Standardroute

Die Standardroute wird genutzt, wenn kein genauerer Eintrag vorhanden ist.

In kleinen Netzwerken reicht oft eine einfache Standardroute zum Internet. In größeren Netzwerken werden mehrere Routen benötigt.

---

## Statisches und dynamisches Routing

Es gibt verschiedene Arten von Routing.

| Routing-Art         | Erklärung                              |
| ------------------- | -------------------------------------- |
| statisches Routing  | Routen werden manuell eingetragen      |
| dynamisches Routing | Router tauschen Routen automatisch aus |

Statisches Routing ist übersichtlich in kleinen Netzwerken, wird aber bei vielen Netzen schnell aufwendig.

Dynamisches Routing ist sinnvoll in größeren Umgebungen, weil Router Änderungen automatisch lernen können.

Beispiele für dynamische Routingprotokolle sind OSPF oder BGP.

---

## NAT

NAT bedeutet **Network Address Translation**.

NAT wird häufig genutzt, damit private IP-Adressen mit dem Internet kommunizieren können.

In vielen Netzwerken nutzen interne Geräte private IP-Adressen. Diese sind im Internet nicht direkt routbar.

Der Router oder die Firewall übersetzt interne Adressen in eine öffentliche Adresse.

Typischer Einsatz:

- Heimnetzwerke
- kleine Firmennetze
- Internetzugang mit privaten IPv4-Adressen

NAT ist sehr verbreitet, besonders bei IPv4.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr anhand von Regeln.

Sie kann entscheiden, welche Verbindungen erlaubt oder blockiert werden.

Typische Filterkriterien:

- Quell-IP-Adresse
- Ziel-IP-Adresse
- Port
- Protokoll
- Richtung der Verbindung
- Benutzer
- Anwendung
- Zone
- Zeitregel
- Sicherheitsstatus

Eine Firewall ist ein zentraler Bestandteil der Netzwerksicherheit.

---

## Firewall-Regeln

Firewall-Regeln sollten klar, notwendig und dokumentiert sein.

Eine Regel beschreibt meistens:

| Bestandteil   | Bedeutung                        |
| ------------- | -------------------------------- |
| Quelle        | woher der Verkehr kommt          |
| Ziel          | wohin der Verkehr geht           |
| Dienst / Port | welcher Dienst erlaubt wird      |
| Aktion        | erlauben oder blockieren         |
| Richtung      | eingehend oder ausgehend         |
| Kommentar     | Zweck der Regel                  |
| Gültigkeit    | dauerhaft oder zeitlich begrenzt |

Gute Firewall-Regeln folgen dem Prinzip:

> Nur erlauben, was wirklich benötigt wird.

Unnötig offene Regeln erhöhen das Sicherheitsrisiko.

---

## Firewall-Zonen

Viele Firewalls arbeiten mit Zonen.

Typische Zonen:

| Zone       | Bedeutung                                  |
| ---------- | ------------------------------------------ |
| LAN        | internes Netzwerk                          |
| WAN        | externes Netzwerk / Internet               |
| DMZ        | Bereich für öffentlich erreichbare Dienste |
| Guest      | Gastnetz                                   |
| VPN        | entfernte Benutzer oder Standorte          |
| Management | Verwaltungsnetz                            |

Zonen helfen, Netzwerkbereiche sauber zu trennen und Regeln verständlicher zu gestalten.

---

## Access Point

Ein Access Point stellt WLAN bereit.

Er verbindet drahtlose Clients mit dem kabelgebundenen Netzwerk.

Wichtige Konfigurationspunkte:

- SSID
- Verschlüsselung
- Authentifizierung
- Frequenzband
- Kanal
- Sendeleistung
- VLAN-Zuordnung
- Gastnetz
- Roaming
- Firmware
- zentrale Verwaltung

Access Points müssen sicher und sinnvoll platziert werden.

---

## WLAN-Sicherheit

WLAN muss besonders geschützt werden, weil Funk nicht an Wänden endet.

Wichtige Sicherheitsmaßnahmen:

- WPA2 oder WPA3 nutzen
- starke Passwörter
- getrenntes Gastnetz
- keine veraltete WEP-Verschlüsselung
- zentrale Authentifizierung bei Bedarf
- VLAN-Zuordnung
- regelmäßige Firmwareupdates
- unsichere WPS-Funktionen vermeiden
- Monitoring unbekannter Geräte

In Unternehmen ist ein ungeschütztes oder schlecht konfiguriertes WLAN ein großes Risiko.

---

## WLAN-Planung

Bei WLAN reicht es nicht, einfach Access Points aufzustellen.

Wichtige Planungsfaktoren:

- Gebäudestruktur
- Wände und Materialien
- Anzahl der Benutzer
- benötigte Bandbreite
- Roaming-Anforderungen
- Störungen durch andere WLANs
- Kanalplanung
- Position der Access Points
- Stromversorgung über PoE
- Sicherheitszonen
- Gastnetz

Schlechte WLAN-Planung führt zu Funklöchern, langsamen Verbindungen und instabilem Roaming.

---

## Modem

Ein Modem verbindet ein lokales Netzwerk mit einem Provideranschluss.

Je nach Anschlussart kann das sein:

- DSL-Modem
- Kabelmodem
- Glasfasermodem
- Mobilfunkmodem

In Heimnetzwerken sind Modem, Router, Switch und WLAN oft in einem Gerät kombiniert.

In Unternehmensnetzwerken werden diese Funktionen häufiger getrennt, damit Verwaltung, Sicherheit und Skalierbarkeit besser sind.

---

## Patchpanel und Verkabelung

Ein Patchpanel verbindet die feste Gebäudeverkabelung mit der aktiven Netzwerktechnik.

Typischer Aufbau:

- Netzwerkdose im Raum
- Verlegekabel zur Netzwerkverteilung
- Patchpanel im Netzwerkschrank
- Patchkabel vom Patchpanel zum Switch

Vorteile:

- saubere Struktur
- bessere Dokumentation
- einfache Änderungen
- Schutz der festen Verkabelung
- übersichtlicher Netzwerkschrank

Patchpanel und Portdokumentation sind wichtig für professionelle Wartung.

---

## Medienkonverter und SFP-Module

Medienkonverter wandeln ein Übertragungsmedium in ein anderes um.

Beispiel:

- Kupfer auf Glasfaser
- Glasfaser auf Kupfer

SFP-Module sind kleine steckbare Module für Netzwerkgeräte.

Sie ermöglichen unterschiedliche Verbindungstypen, zum Beispiel:

- Glasfaser
- Kupfer
- verschiedene Geschwindigkeiten
- unterschiedliche Reichweiten

Wichtig ist, dass Modul, Switch, Kabeltyp und Geschwindigkeit zusammenpassen.

---

## NAS

NAS bedeutet **Network Attached Storage**.

Ein NAS stellt Speicher im Netzwerk bereit.

Typische Funktionen:

- Dateiablagen
- Backups
- Benutzerfreigaben
- RAID-Verbund
- Snapshots
- zentrale Speicherung
- Zugriff über SMB, NFS oder andere Protokolle

Ein NAS kann in kleinen Unternehmen eine einfache Speicherlösung sein.

Für kritische Unternehmensdaten müssen aber Backup, Rechte, Sicherheit und Verfügbarkeit sauber geplant werden.

---

## USV

USV bedeutet **Unterbrechungsfreie Stromversorgung**.

Eine USV schützt Geräte bei Stromausfall oder Spannungsschwankungen.

Typische Einsatzbereiche:

- Server
- NAS
- Switches
- Router
- Firewalls
- wichtige Netzwerkkomponenten

Eine USV gibt Geräten Zeit, kontrolliert herunterzufahren oder kurze Stromausfälle zu überbrücken.

Sie ersetzt aber keine langfristige Stromversorgung.

---

## Management von Netzwerkgeräten

Netzwerkgeräte müssen verwaltet werden.

Mögliche Verwaltungsarten:

- Weboberfläche
- CLI
- SSH
- serielle Konsole
- zentrale Managementplattform
- SNMP
- API

Wichtige Sicherheitsregeln:

- Standardpasswörter ändern
- sichere Administratorkonten nutzen
- Managementzugriff einschränken
- SSH statt Telnet verwenden
- HTTPS statt HTTP verwenden
- Firmware aktuell halten
- Konfiguration sichern
- Änderungen dokumentieren

Managementzugänge sind besonders schützenswert, weil Angreifer darüber Netzwerke manipulieren könnten.

---

## Basiskonfiguration von Netzwerkgeräten

Eine Basiskonfiguration kann enthalten:

- Gerätename
- Management-IP
- Adminpasswort
- Zeitzone
- DNS-Server
- NTP-Server
- VLANs
- Ports
- Logging
- SNMP
- SSH-Zugang
- Firmwarestand
- Backup der Konfiguration
- Dokumentation

Eine saubere Basiskonfiguration erleichtert Betrieb, Support und spätere Wartung.

---

## Dokumentation der Konfiguration

Jede wichtige Konfiguration sollte dokumentiert werden.

Wichtige Angaben:

- Gerätename
- Standort
- Hersteller und Modell
- Seriennummer
- Management-IP
- Firmwareversion
- Portbelegung
- VLANs
- Uplinks
- Firewall-Regeln
- Routing
- WLAN-SSIDs
- Zugangsdokumentation
- Änderungsverlauf
- Backup-Stand

Ohne Dokumentation kann selbst ein funktionierendes Netzwerk später schwer wartbar werden.

---

## Sicherheitsaspekte bei Netzwerkkomponenten

Netzwerkkomponenten müssen geschützt werden.

Wichtige Maßnahmen:

- keine Standardpasswörter
- sichere Managementprotokolle
- Managementnetz nutzen
- Zugriff nur für Administratoren
- regelmäßige Updates
- Konfigurationsbackup
- Logging aktivieren
- physischer Zugriff beschränken
- unnötige Dienste deaktivieren
- alte Geräte rechtzeitig ersetzen

Ein unsicher konfigurierter Switch, Router oder Access Point kann ein großes Risiko für das gesamte Netzwerk sein.

---

## Praxisbeispiele

### Beispiel 1: Switch für ein Büro

Ein Büro benötigt 20 Netzwerkanschlüsse. Ein managed Switch mit 24 Ports, VLAN-Unterstützung und PoE-Reserve ist sinnvoll, wenn zusätzlich Access Points oder IP-Telefone angeschlossen werden sollen.

### Beispiel 2: Firewall für ein kleines Unternehmen

Ein Unternehmen braucht eine Firewall zwischen LAN und Internet. Wichtig sind passende Leistung, VPN-Unterstützung, verständliche Regelverwaltung, Updates, Logging und getrennte Zonen für LAN, Gäste und eventuell DMZ.

### Beispiel 3: Access Points für WLAN

Ein Unternehmen benötigt WLAN für Mitarbeiter und Gäste. Access Points werden per PoE versorgt, mit getrennten SSIDs konfiguriert und unterschiedlichen VLANs zugeordnet.

---

## Typische Fehler

| Fehler                                              | Problem                                           |
| --------------------------------------------------- | ------------------------------------------------- |
| unmanaged Switch in professioneller Umgebung nutzen | keine VLANs, kein Monitoring, wenig Kontrolle     |
| zu wenig Ports einplanen                            | spätere Erweiterung wird schwierig                |
| PoE-Budget ignorieren                               | Access Points oder Telefone bekommen keinen Strom |
| Firewall-Regeln zu offen setzen                     | Sicherheitsrisiko                                 |
| VLANs nicht dokumentieren                           | Fehlersuche wird schwierig                        |
| Standardpasswörter nicht ändern                     | großes Sicherheitsrisiko                          |
| Firmware nie aktualisieren                          | Sicherheitslücken bleiben bestehen                |
| WLAN ohne Planung aufbauen                          | schlechte Abdeckung und instabile Verbindung      |
| keine Konfigurationsbackups erstellen               | Wiederherstellung dauert länger                   |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist die Auswahl und Konfiguration von Netzwerkkomponenten eine zentrale praktische Fähigkeit.

Ein FISI muss verstehen, welche Komponente welche Aufgabe erfüllt und wie diese Komponenten zusammenarbeiten.

In der Praxis bedeutet das:

- passende Netzwerkgeräte auswählen
- technische Anforderungen bewerten
- Switches, Router, Firewalls und Access Points einordnen
- VLANs und Ports verstehen
- Basiskonfigurationen durchführen
- Sicherheitseinstellungen beachten
- Konfigurationen sichern
- Netzwerkgeräte dokumentieren
- Fehler systematisch analysieren

Ein guter FISI betrachtet Netzwerkgeräte nicht isoliert, sondern als Teil einer gesamten Infrastruktur aus Clients, Servern, Diensten, Sicherheitszonen und Dokumentation.

---

## Kurze Zusammenfassung

Netzwerkkomponenten ermöglichen und steuern die Kommunikation in IT-Netzwerken.

Wichtige Komponenten sind Netzwerkkarten, Switches, Router, Firewalls, Access Points, Modems, Patchpanel, Medienkonverter, NAS-Systeme und USV-Anlagen.

Bei der Auswahl zählen Leistung, Portanzahl, Sicherheit, Verwaltbarkeit, Kompatibilität, Erweiterbarkeit, Support und Wirtschaftlichkeit.

Bei der Konfiguration sind Basiseinstellungen, VLANs, Routing, Firewall-Regeln, WLAN-Sicherheit, Managementzugänge, Updates, Backups und Dokumentation besonders wichtig.

Für FISI ist dieses Kapitel wichtig, weil Netzwerkgeräte die technische Grundlage für stabile, sichere und wartbare IT-Infrastrukturen bilden.
