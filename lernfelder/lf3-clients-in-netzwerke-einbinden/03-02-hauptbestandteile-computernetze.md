# 3.2 Hauptbestandteile von Computernetzen unterscheiden

In diesem Kapitel geht es um die wichtigsten Bestandteile eines Computernetzwerks.

Ein Computernetz besteht nicht nur aus Clients und Kabeln. Dazu gehören Endgeräte, Server, Netzwerkkomponenten, Übertragungsmedien, Netzwerkdienste, Adressen, Sicherheitsbereiche und organisatorische Strukturen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil man Netzwerke nur dann richtig planen, einrichten und warten kann, wenn man die einzelnen Bestandteile und ihre Aufgaben versteht.

---

## Kurz erklärt

Ein Computernetz verbindet mehrere IT-Systeme miteinander, damit sie Daten austauschen und gemeinsame Dienste nutzen können.

Zu einem Netzwerk gehören typischerweise:

- Clients
- Server
- Switches
- Router
- Firewalls
- Access Points
- Netzwerkkabel oder Funkverbindungen
- Netzwerkdienste
- IP-Adressen und MAC-Adressen
- Benutzer- und Rechteverwaltung
- Sicherheitszonen
- Dokumentation

Diese Bestandteile arbeiten zusammen, damit Benutzer auf Internet, Dateien, Drucker, Anwendungen, Cloud-Dienste und interne Systeme zugreifen können.

---

## Fachliche Erklärung

Ein Netzwerk ist eine technische und organisatorische Infrastruktur zur Kommunikation zwischen Geräten.

Damit Kommunikation funktioniert, müssen mehrere Bedingungen erfüllt sein:

| Bereich      | Bedeutung                                                                 |
| ------------ | ------------------------------------------------------------------------- |
| Geräte       | Clients, Server und Netzwerkgeräte müssen vorhanden sein                  |
| Verbindung   | Geräte müssen über Kabel, WLAN oder andere Medien verbunden sein          |
| Adressierung | Geräte brauchen eindeutige Adressen                                       |
| Protokolle   | Kommunikation folgt festen Regeln                                         |
| Dienste      | zentrale Funktionen wie DNS, DHCP oder Dateiablagen werden bereitgestellt |
| Sicherheit   | Zugriff muss kontrolliert und geschützt werden                            |
| Verwaltung   | Netzwerk muss dokumentiert, überwacht und gewartet werden                 |

Ein Netzwerk ist deshalb mehr als eine technische Verbindung. Es ist ein System aus Hardware, Software, Diensten, Regeln und Prozessen.

---

## Grundbestandteile eines Netzwerks

Die wichtigsten Bestandteile eines Netzwerks lassen sich in mehrere Gruppen einteilen.

| Gruppe                | Beispiele                                             |
| --------------------- | ----------------------------------------------------- |
| Endgeräte             | PCs, Laptops, Smartphones, Drucker                    |
| Server                | Datei-, Web-, Mail-, Datenbank- oder Backupserver     |
| Netzwerkgeräte        | Switches, Router, Firewalls, Access Points            |
| Übertragungsmedien    | Kupferkabel, Glasfaser, WLAN                          |
| Netzwerkdienste       | DHCP, DNS, Authentifizierung, Datei- und Druckdienste |
| Adressen              | MAC-Adresse, IP-Adresse, Hostname                     |
| Sicherheitsstrukturen | Firewall-Regeln, VLANs, Rechte, VPN                   |
| Dokumentation         | Netzplan, IP-Plan, Geräteinventar                     |

Diese Bestandteile müssen technisch zusammenpassen und sinnvoll organisiert werden.

---

## Endgeräte

Endgeräte sind Geräte, die ein Netzwerk nutzen.

Dazu gehören zum Beispiel:

- Desktop-PCs
- Laptops
- Tablets
- Smartphones
- Drucker
- Scanner
- IP-Telefone
- Kameras
- IoT-Geräte
- Thin Clients

Endgeräte werden oft auch als Hosts bezeichnet, wenn sie aktiv am Netzwerk teilnehmen und eine Netzwerkadresse besitzen.

Ein Endgerät kann Daten senden, empfangen oder Dienste nutzen. Manche Endgeräte können auch selbst Dienste bereitstellen.

---

## Clients

Ein Client ist ein Gerät oder Programm, das einen Dienst nutzt.

Typische Clients sind:

- Arbeitsplatz-PC
- Laptop
- Smartphone
- Tablet
- Browser
- E-Mail-Programm
- Datenbank-Client
- Remote-Desktop-Client

Ein Client fordert eine Leistung an. Der Server stellt diese Leistung bereit.

Beispiele für Client-Aufgaben:

- Webseite öffnen
- Datei vom Server laden
- E-Mail abrufen
- Druckauftrag senden
- Benutzeranmeldung durchführen
- Verbindung zu einer Datenbank herstellen

Clients sind im Unternehmensnetz besonders wichtig, weil sie die Schnittstelle zwischen Benutzer und IT-Infrastruktur bilden.

---

## Client-Arten

Clients können unterschiedlich aufgebaut sein.

| Client-Art    | Erklärung                                                             |
| ------------- | --------------------------------------------------------------------- |
| Fat Client    | leistungsstarker Client mit lokaler Software und lokaler Verarbeitung |
| Thin Client   | einfacher Client, viele Aufgaben laufen zentral auf Servern           |
| Zero Client   | sehr reduzierter Client für virtuelle Desktopumgebungen               |
| Mobile Client | Laptop, Tablet oder Smartphone für mobiles Arbeiten                   |
| Web Client    | Zugriff über Browser auf Webanwendungen                               |
| Remote Client | Zugriff auf entfernte Systeme, zum Beispiel per RDP oder VPN          |

Welche Client-Art sinnvoll ist, hängt vom Einsatzbereich, Sicherheitsbedarf, Verwaltungsaufwand und Budget ab.

---

## Fat Client

Ein Fat Client besitzt eigene Rechenleistung, eigenen Speicher und lokal installierte Programme.

Typische Eigenschaften:

- starke lokale Hardware
- Betriebssystem lokal installiert
- Anwendungen laufen direkt auf dem Gerät
- kann teilweise offline arbeiten
- benötigt lokale Wartung und Updates
- höhere Anforderungen an Hardware und Verwaltung

Fat Clients sind typisch für normale Arbeitsplatz-PCs, Laptops, Entwicklergeräte oder Workstations.

---

## Thin Client

Ein Thin Client ist ein einfacherer Arbeitsplatzrechner.

Viele Aufgaben laufen nicht lokal, sondern auf Servern oder in einer virtuellen Desktopumgebung.

Typische Eigenschaften:

- geringe lokale Rechenleistung
- zentrale Anwendungen oder Desktops
- einfache Verwaltung
- weniger lokale Daten
- abhängig von Netzwerk und Servern
- oft in standardisierten Umgebungen

Thin Clients sind sinnvoll, wenn viele Arbeitsplätze zentral verwaltet werden sollen.

Ein Nachteil ist die starke Abhängigkeit von Netzwerkverbindung und zentraler Infrastruktur.

---

## Server

Ein Server ist ein System, das Dienste für andere Geräte bereitstellt.

Server können physische Maschinen, virtuelle Maschinen oder Cloud-Systeme sein.

Typische Serveraufgaben:

- Dateien bereitstellen
- Webseiten ausliefern
- E-Mails verwalten
- Benutzer authentifizieren
- IP-Adressen vergeben
- Namen auflösen
- Datenbanken bereitstellen
- Backups speichern
- Anwendungen hosten
- virtuelle Maschinen betreiben

Ein Server ist nicht automatisch ein besonders großer Computer. Entscheidend ist die Rolle: Ein Server stellt einen Dienst bereit.

---

## Servertypen

In Unternehmensnetzwerken gibt es verschiedene Servertypen.

| Servertyp                | Aufgabe                                      |
| ------------------------ | -------------------------------------------- |
| Dateiserver              | stellt Dateien und Ordner zentral bereit     |
| Druckserver              | verwaltet Netzwerkdrucker und Druckaufträge  |
| Webserver                | liefert Webseiten oder Webanwendungen aus    |
| Mailserver               | verarbeitet E-Mails                          |
| Datenbankserver          | speichert strukturierte Daten                |
| DNS-Server               | übersetzt Namen in IP-Adressen               |
| DHCP-Server              | vergibt IP-Adressen automatisch              |
| Authentifizierungsserver | prüft Benutzeranmeldungen                    |
| Backupserver             | speichert Sicherungen                        |
| Applikationsserver       | stellt Anwendungen zentral bereit            |
| Virtualisierungsserver   | betreibt virtuelle Maschinen                 |
| Monitoringserver         | überwacht Systeme und Dienste                |
| Proxyserver              | vermittelt und kontrolliert Netzwerkzugriffe |

Ein Server kann mehrere Rollen gleichzeitig haben. In größeren Umgebungen werden Rollen oft getrennt, damit Systeme besser wartbar, sicherer und leistungsfähiger sind.

---

## Physische und virtuelle Server

Server können physisch oder virtuell betrieben werden.

### Physischer Server

Ein physischer Server ist echte Hardware im Serverraum oder Rechenzentrum.

Eigenschaften:

- eigene CPU, RAM, Speicher und Netzwerkkarten
- direkte Kontrolle über Hardware
- oft hohe Leistung und Zuverlässigkeit
- Wartung der Hardware notwendig

### Virtueller Server

Ein virtueller Server läuft als virtuelle Maschine auf einem Hostsystem.

Eigenschaften:

- mehrere virtuelle Server auf einer physischen Hardware möglich
- flexible Verwaltung
- einfachere Sicherung und Wiederherstellung
- bessere Ressourcenausnutzung
- abhängig von Virtualisierungsplattform und Host

Virtualisierung ist in modernen IT-Umgebungen sehr verbreitet, weil Ressourcen effizienter genutzt werden können.

---

## Netzwerkgeräte

Netzwerkgeräte verbinden Systeme miteinander und steuern den Datenverkehr.

Wichtige Netzwerkgeräte sind:

| Gerät           | Hauptaufgabe                                     |
| --------------- | ------------------------------------------------ |
| Switch          | verbindet Geräte im lokalen Netzwerk             |
| Router          | verbindet verschiedene Netzwerke                 |
| Firewall        | filtert und schützt Netzwerkverkehr              |
| Access Point    | stellt WLAN bereit                               |
| Modem           | verbindet mit einem Provideranschluss            |
| Patchpanel      | verbindet Gebäudeverkabelung mit Netzwerktechnik |
| Medienkonverter | wandelt Übertragungsmedien um                    |
| Load Balancer   | verteilt Anfragen auf mehrere Server             |

Netzwerkgeräte sind die Infrastruktur, über die Clients und Server miteinander kommunizieren.

---

## Switch

Ein Switch verbindet Geräte innerhalb eines lokalen Netzwerks.

Er arbeitet hauptsächlich mit MAC-Adressen und leitet Daten gezielt an den richtigen Port weiter.

Wichtige Eigenschaften:

- mehrere Netzwerkports
- MAC-Adresstabelle
- Weiterleitung innerhalb eines LANs
- Unterstützung für VLANs bei managed Switches
- PoE bei bestimmten Modellen
- hohe Geschwindigkeit im lokalen Netzwerk

Switches sind zentrale Komponenten in LANs.

Ein einfacher Switch verbindet Geräte nur. Ein managed Switch kann zusätzlich konfiguriert, überwacht und in VLAN-Strukturen eingebunden werden.

---

## Router

Ein Router verbindet unterschiedliche Netzwerke miteinander.

Er arbeitet auf Basis von IP-Adressen und entscheidet, wohin Datenpakete weitergeleitet werden.

Typische Aufgaben:

- Verbindung zwischen LAN und Internet
- Routing zwischen Subnetzen
- Verbindung von Standorten
- Gateway-Funktion
- NAT in kleinen Netzwerken
- statische oder dynamische Routen

Ein Client nutzt einen Router meistens als Standardgateway, wenn er Ziele außerhalb des eigenen Netzwerks erreichen möchte.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr anhand von Regeln.

Sie entscheidet, welche Verbindungen erlaubt oder blockiert werden.

Aufgaben einer Firewall:

- Schutz vor unerlaubtem Zugriff
- Trennung von Netzbereichen
- Filterung nach IP-Adressen, Ports und Protokollen
- Kontrolle von ein- und ausgehendem Verkehr
- Schutz interner Systeme
- Protokollierung von Verbindungen
- VPN-Funktionen bei vielen Geräten

Eine Firewall ist ein wichtiger Sicherheitsbaustein, ersetzt aber keine weiteren Maßnahmen wie Updates, Rechteverwaltung, sichere Passwörter oder Monitoring.

---

## Access Point

Ein Access Point stellt WLAN bereit.

Er verbindet drahtlose Geräte mit dem kabelgebundenen Netzwerk.

Wichtige Begriffe:

| Begriff        | Bedeutung                                 |
| -------------- | ----------------------------------------- |
| SSID           | Name des WLANs                            |
| WPA2 / WPA3    | Verschlüsselungsstandards                 |
| Frequenzband   | 2,4 GHz, 5 GHz oder 6 GHz                 |
| Kanal          | Funkkanal für die Übertragung             |
| Roaming        | Wechsel zwischen Access Points            |
| Gastnetz       | getrenntes WLAN für Gäste                 |
| VLAN-Zuordnung | Trennung von WLAN-Verkehr in Netzbereiche |

Access Points müssen sinnvoll platziert und sicher konfiguriert werden. Schlechte Platzierung oder falsche Kanäle können WLAN-Probleme verursachen.

---

## Übertragungsmedien

Übertragungsmedien transportieren Daten zwischen Geräten.

Es gibt kabelgebundene und drahtlose Medien.

| Medium      | Eigenschaften                                 |
| ----------- | --------------------------------------------- |
| Kupferkabel | häufig für Ethernet im LAN                    |
| Glasfaser   | sehr schnell, große Entfernungen, störungsarm |
| WLAN        | flexibel, aber störanfälliger                 |
| Bluetooth   | kurze Distanzen, Zubehör und kleine Geräte    |
| Mobilfunk   | mobile Datenverbindungen über Provider        |

Die Wahl des Mediums beeinflusst Geschwindigkeit, Reichweite, Stabilität, Kosten und Sicherheit.

---

## Kupferkabel

Kupferkabel werden häufig für Ethernet-Netzwerke genutzt.

Typische Eigenschaften:

- relativ günstig
- einfach zu installieren
- häufig RJ45-Stecker
- typisch in Büros und Gebäuden
- begrenzte Kabellänge pro Segment
- anfälliger für elektromagnetische Störungen als Glasfaser

Häufige Kategorien sind zum Beispiel Cat 5e, Cat 6, Cat 6A oder Cat 7.

Die Kategorie beeinflusst mögliche Übertragungsgeschwindigkeit und Frequenzbereich.

---

## Glasfaser

Glasfaser überträgt Daten mit Licht.

Typische Eigenschaften:

- sehr hohe Geschwindigkeit
- große Entfernungen möglich
- unempfindlich gegen elektromagnetische Störungen
- wichtig für Backbone-Verbindungen
- häufig im Rechenzentrum und zwischen Gebäuden
- aufwendiger und teurer als Kupfertechnik

Glasfaser wird oft dort genutzt, wo hohe Bandbreite, lange Strecken oder störungsarme Übertragung wichtig sind.

---

## WLAN als Übertragungsmedium

WLAN überträgt Daten per Funk.

Vorteile:

- mobil und flexibel
- keine Kabel zum Endgerät nötig
- gut für Laptops, Tablets und Smartphones
- schnell erweiterbar

Nachteile:

- abhängig von Signalstärke
- störanfällig
- Sicherheitskonfiguration sehr wichtig
- Geschwindigkeit schwankt
- Reichweite begrenzt
- viele Geräte teilen sich das Funkmedium

WLAN ist bequem, muss aber sorgfältig geplant werden. Besonders in Unternehmen sind Verschlüsselung, Gastnetz, Kanalplanung und Access-Point-Positionierung wichtig.

---

## Netzwerkbereiche

Netzwerke können in Bereiche unterteilt werden.

Diese Unterteilung hilft bei Sicherheit, Verwaltung und Übersicht.

| Bereich        | Bedeutung                                          |
| -------------- | -------------------------------------------------- |
| LAN            | internes lokales Netzwerk                          |
| WLAN           | drahtloses lokales Netzwerk                        |
| Gastnetz       | getrenntes Netzwerk für Besucher                   |
| Servernetz     | Bereich für Server                                 |
| Managementnetz | Bereich für Administration von Geräten             |
| DMZ            | Sicherheitszone für öffentlich erreichbare Dienste |
| WAN            | Verbindung zu entfernten Standorten                |
| VPN            | verschlüsselte Verbindung über fremde Netze        |

Nicht jedes Unternehmen hat alle diese Bereiche. Größere Umgebungen sind aber oft in mehrere Netzbereiche getrennt.

---

## LAN, WLAN und Gastnetz

Ein internes LAN ist normalerweise für Unternehmensgeräte gedacht.

Ein WLAN kann für Firmenlaptops und mobile Geräte genutzt werden.

Ein Gastnetz sollte getrennt vom internen Netzwerk sein.

Der Grund ist Sicherheit: Gäste sollen vielleicht Internet nutzen dürfen, aber keinen Zugriff auf Server, Drucker oder interne Daten haben.

Eine sinnvolle Netztrennung verhindert, dass alle Geräte im gleichen Netzbereich liegen.

---

## Servernetz

Ein Servernetz ist ein Netzbereich, in dem Server betrieben werden.

Vorteile:

- bessere Übersicht
- gezieltere Firewall-Regeln
- getrennte Verwaltung
- einfacheres Monitoring
- bessere Sicherheitsstruktur
- klare Trennung von Clients und Servern

Server sollten nicht unkontrolliert im gleichen Netz wie alle Clients betrieben werden, besonders wenn sie wichtige Dienste bereitstellen.

---

## DMZ

DMZ bedeutet **Demilitarized Zone**.

In der IT ist damit ein Netzwerkbereich gemeint, der zwischen internem Netzwerk und externem Netzwerk liegt.

Eine DMZ wird häufig für Systeme genutzt, die von außen erreichbar sein müssen.

Beispiele:

- Webserver
- Reverse Proxy
- Mail-Gateway
- VPN-Gateway

Der Zweck einer DMZ ist, öffentlich erreichbare Dienste vom internen Netzwerk zu trennen.

Wenn ein System in der DMZ angegriffen wird, soll nicht automatisch das interne Netzwerk betroffen sein.

---

## Rechenzentrum

Ein Rechenzentrum ist ein speziell eingerichteter Bereich oder Standort für IT-Infrastruktur.

Dort werden Server, Speicher, Netzwerkkomponenten und Sicherheitslösungen betrieben.

Wichtige Merkmale:

- stabile Stromversorgung
- unterbrechungsfreie Stromversorgung
- Klimatisierung
- Brandschutz
- Zugangskontrolle
- redundante Netzwerkanbindung
- Monitoring
- strukturierte Verkabelung
- physische Sicherheit
- geregelte Wartungsprozesse

Ein Rechenzentrum ist deutlich mehr als ein Raum mit Servern. Es ist eine kontrollierte Umgebung für zuverlässigen IT-Betrieb.

---

## Serverraum

Ein Serverraum ist eine kleinere Variante eines Rechenzentrums.

Er kann sich direkt im Unternehmen befinden.

Wichtige Anforderungen:

- abschließbarer Raum
- ausreichende Kühlung
- stabile Stromversorgung
- USV
- Brandschutz
- Ordnung im Rack
- strukturierte Verkabelung
- Dokumentation
- begrenzter Zugang
- Monitoring von Temperatur und Geräten

Viele kleine und mittlere Unternehmen haben eher einen Serverraum als ein eigenes großes Rechenzentrum.

---

## Cloud als Netzbestandteil

Moderne Unternehmensnetzwerke enden nicht mehr immer im eigenen Gebäude.

Cloud-Dienste sind oft Teil der IT-Umgebung.

Beispiele:

- Microsoft 365
- Cloud-Speicher
- Webanwendungen
- virtuelle Server
- Backup in der Cloud
- zentrale Geräteverwaltung
- Identitätsdienste

Cloud-Dienste müssen über Netzwerkverbindungen erreichbar sein. Deshalb werden Internetverbindung, DNS, Authentifizierung, Sicherheit und Datenschutz noch wichtiger.

Die Cloud ist kein „fremder Bereich ohne Zusammenhang“, sondern Teil der gesamten IT-Architektur.

---

## Netzwerkdienste

Netzwerkdienste stellen grundlegende Funktionen bereit.

Ohne Netzwerkdienste wäre ein Unternehmensnetz schwer nutzbar und schwer verwaltbar.

Wichtige Dienste:

| Dienst            | Aufgabe                                |
| ----------------- | -------------------------------------- |
| DHCP              | automatische IP-Konfiguration          |
| DNS               | Namensauflösung                        |
| NTP               | Zeitsynchronisation                    |
| Datei-Freigabe    | gemeinsame Dateiablagen                |
| Druckdienst       | gemeinsame Druckernutzung              |
| Verzeichnisdienst | Benutzer, Gruppen und Geräte verwalten |
| Authentifizierung | Anmeldung und Zugriff prüfen           |
| Backupdienst      | Daten sichern                          |
| Monitoring        | Systeme überwachen                     |
| Logging           | Ereignisse und Fehler protokollieren   |

Diese Dienste sind oft unsichtbar für normale Benutzer, aber entscheidend für den Betrieb.

---

## Adressierung im Netzwerk

Damit Geräte kommunizieren können, müssen sie identifizierbar sein.

Wichtige Adressarten:

| Adresse     | Bedeutung                                 |
| ----------- | ----------------------------------------- |
| MAC-Adresse | Hardwareadresse der Netzwerkschnittstelle |
| IP-Adresse  | logische Adresse im Netzwerk              |
| Hostname    | Gerätename                                |
| DNS-Name    | auflösbarer Netzwerkname                  |

Die MAC-Adresse wird vor allem im lokalen Netzwerk verwendet.

Die IP-Adresse wird für die logische Kommunikation genutzt.

DNS-Namen machen Systeme für Menschen leichter nutzbar.

---

## Netzwerkprotokolle

Netzwerkprotokolle sind Regeln für die Kommunikation.

Sie legen fest, wie Daten aufgebaut, übertragen und verarbeitet werden.

Wichtige Protokolle:

| Protokoll  | Aufgabe                                   |
| ---------- | ----------------------------------------- |
| Ethernet   | Datenübertragung im lokalen Netzwerk      |
| IP         | logische Adressierung und Weiterleitung   |
| TCP        | zuverlässige Verbindung zwischen Systemen |
| UDP        | schnelle verbindungslose Übertragung      |
| DNS        | Namensauflösung                           |
| DHCP       | automatische Netzwerkkonfiguration        |
| HTTP/HTTPS | Webseiten und Webanwendungen              |
| SMTP/IMAP  | E-Mail-Versand und -Abruf                 |
| SMB        | Datei- und Druckfreigaben                 |
| SSH        | sichere Fernadministration                |

Diese Protokolle werden in späteren LF3-Kapiteln noch genauer wichtig.

---

## Sicherheit der Netzbestandteile

Jeder Bestandteil eines Netzwerks kann ein Sicherheitsrisiko sein.

Typische Risiken:

- unsichere WLAN-Konfiguration
- offene Netzwerkports
- veraltete Firmware
- falsche Firewall-Regeln
- zu viele Benutzerrechte
- ungeschützte Serverdienste
- unbekannte Geräte im Netzwerk
- fehlende Netztrennung
- schlechte Passwörter
- keine Dokumentation

Netzwerksicherheit bedeutet daher nicht nur Firewall, sondern auch saubere Struktur, aktuelle Systeme, klare Rechte und kontrollierte Zugänge.

---

## Verfügbarkeit der Netzbestandteile

Ein Netzwerk muss zuverlässig verfügbar sein.

Wichtige Faktoren:

- stabile Stromversorgung
- zuverlässige Switches
- funktionierende Router
- saubere Verkabelung
- redundante Systeme
- Backup-Internetverbindung bei Bedarf
- Überwachung wichtiger Dienste
- Ersatzgeräte oder Ersatzteile
- klare Dokumentation
- schnelle Fehlersuche

Wenn zentrale Komponenten ausfallen, können viele Benutzer betroffen sein.

Beispiel: Ein defekter Switch kann einen ganzen Bereich vom Netzwerk trennen. Ein DNS-Ausfall kann dazu führen, dass viele Dienste nicht mehr über Namen erreichbar sind.

---

## Dokumentation der Netzbestandteile

Netzwerkbestandteile müssen dokumentiert werden.

Wichtige Dokumentationspunkte:

- Gerätebezeichnung
- Standort
- IP-Adresse
- MAC-Adresse
- Hostname
- Seriennummer
- Switch-Port
- VLAN
- Funktion
- Verantwortliche Person
- Zugangsdatenverwaltung
- Wartungsverträge
- Firmwarestand
- Änderungen

Dokumentation hilft bei Wartung, Fehleranalyse, Sicherheit, Inventar und Übergabe.

Ohne Dokumentation wird ein Netzwerk schwer kontrollierbar.

---

## Praxisbeispiele

### Beispiel 1: Kleines Büronetzwerk

Ein kleines Büro nutzt Router, Switch, WLAN, mehrere PCs, einen Netzwerkdrucker und ein NAS. Der Router stellt Internetzugang bereit, der Switch verbindet die Geräte, WLAN ermöglicht mobile Nutzung und das NAS speichert gemeinsame Dateien.

### Beispiel 2: Unternehmensnetz mit Serverraum

Ein Unternehmen betreibt Clients im Büronetz, Server in einem eigenen Servernetz, WLAN für Mitarbeiter, ein getrenntes Gastnetz und eine Firewall zum Internet. Dadurch sind Dienste besser strukturiert und sicherer trennbar.

### Beispiel 3: Cloud-erweiterte Umgebung

Ein Unternehmen nutzt lokale Clients, aber viele Dienste laufen in der Cloud. Benutzer melden sich zentral an, Dateien liegen teilweise in Cloud-Speichern und Geräte werden über eine zentrale Plattform verwaltet.

---

## Typische Fehler

| Fehler                                     | Problem                                                           |
| ------------------------------------------ | ----------------------------------------------------------------- |
| nur Clients und Router betrachten          | wichtige Server, Dienste und Sicherheitsbereiche werden übersehen |
| keine Netztrennung nutzen                  | Sicherheitsrisiken durch zu offene Kommunikation                  |
| Netzwerkdienste unterschätzen              | DNS, DHCP oder NTP sind für den Betrieb zentral                   |
| Switches nicht dokumentieren               | Portsuche und Fehlersuche werden schwierig                        |
| WLAN ohne Planung betreiben                | schlechte Abdeckung und Sicherheitsprobleme                       |
| Server im falschen Netz betreiben          | unnötige Risiken und unklare Struktur                             |
| alte Geräte nicht inventarisieren          | Sicherheits- und Wartungsprobleme                                 |
| Cloud nicht in Netzwerkplanung einbeziehen | Abhängigkeiten und Datenschutz werden übersehen                   |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist es wichtig, Netzwerke als Gesamtsystem zu verstehen.

Ein FISI muss erkennen, welche Geräte und Dienste zusammenarbeiten und welche Rolle einzelne Komponenten haben.

In der Praxis bedeutet das:

- Clients und Server unterscheiden
- Netzwerkgeräte einordnen
- Netzbereiche verstehen
- Dienste wie DNS und DHCP erkennen
- Serverräume und Rechenzentren verstehen
- Cloud-Dienste in die Infrastruktur einordnen
- Sicherheitsbereiche planen
- Netzbestandteile dokumentieren
- Fehler logisch eingrenzen

Ein guter FISI betrachtet nicht nur ein einzelnes Gerät, sondern die gesamte Verbindungskette vom Client bis zum Dienst.

---

## Kurze Zusammenfassung

Computernetze bestehen aus Endgeräten, Clients, Servern, Netzwerkgeräten, Übertragungsmedien, Netzwerkdiensten, Adressen und Sicherheitsbereichen.

Wichtige Netzwerkgeräte sind Switches, Router, Firewalls und Access Points.

Wichtige Netzbereiche sind LAN, WLAN, Gastnetz, Servernetz, DMZ, WAN und VPN.

Server, Rechenzentren, Cloud-Dienste und Netzwerkdienste bilden die Grundlage moderner IT-Infrastrukturen.

Für FISI ist entscheidend, diese Bestandteile unterscheiden und ihre Aufgaben im Gesamtsystem verstehen zu können.
