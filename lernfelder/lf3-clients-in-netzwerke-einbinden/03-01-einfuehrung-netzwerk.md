# 3.1 Einführung in Netzwerke im Ausbildungsbetrieb

In diesem Kapitel geht es um den grundsätzlichen Aufbau und die Bedeutung von Netzwerken in einem Unternehmen.

Ein Netzwerk verbindet Computer, Server, Drucker, Smartphones, Access Points, Router, Switches und andere Geräte miteinander. Dadurch können Benutzer gemeinsam auf Daten, Dienste, Anwendungen und das Internet zugreifen.

Für Fachinformatiker für Systemintegration ist dieses Thema besonders wichtig, weil fast jede moderne IT-Umgebung auf funktionierenden Netzwerken basiert.

---

## Kurz erklärt

Ein Rechnernetz ist ein Zusammenschluss mehrerer IT-Systeme, die Daten miteinander austauschen können.

In einem Unternehmen wird ein Netzwerk benötigt, damit Benutzer und Geräte gemeinsam arbeiten können.

Typische Aufgaben eines Unternehmensnetzwerks sind:

- Internetzugang bereitstellen
- Zugriff auf Server ermöglichen
- Dateien gemeinsam nutzen
- Drucker im Netzwerk verwenden
- Benutzer zentral anmelden
- E-Mail und Kommunikation ermöglichen
- Cloud-Dienste erreichbar machen
- Updates verteilen
- Backups durchführen
- Systeme überwachen
- Fernwartung ermöglichen

Ein einzelner Computer kann ohne Netzwerk lokal arbeiten. In einem Unternehmen ist er aber meistens Teil einer größeren IT-Infrastruktur.

---

## Fachliche Erklärung

Ein Netzwerk besteht nicht nur aus Kabeln und WLAN.

Zu einem funktionierenden Netzwerk gehören mehrere Ebenen:

| Ebene                  | Bedeutung                                           |
| ---------------------- | --------------------------------------------------- |
| physische Ebene        | Kabel, WLAN, Switches, Netzwerkkarten               |
| logische Ebene         | IP-Adressen, Subnetze, Routing, DNS                 |
| Dienste-Ebene          | DHCP, Dateiablagen, Druckdienste, Authentifizierung |
| Sicherheits-Ebene      | Firewall, Rechte, Verschlüsselung, Zugriffsschutz   |
| organisatorische Ebene | Dokumentation, Zuständigkeiten, Prozesse            |

Damit ein Client im Unternehmensnetz arbeiten kann, müssen diese Ebenen zusammenpassen.

Ein Netzwerkkabel allein reicht nicht aus. Das Gerät braucht auch eine gültige Netzwerkkonfiguration, passende Rechte, Zugriff auf Dienste und Sicherheitsfreigaben.

---

## Warum Netzwerke im Unternehmen wichtig sind

Unternehmen nutzen Netzwerke, weil IT-Systeme zusammenarbeiten müssen.

Ohne Netzwerk wären viele typische Arbeitsprozesse kaum möglich.

Beispiele:

- Mitarbeiter greifen gemeinsam auf Dateien zu.
- Benutzer melden sich zentral mit ihrem Konto an.
- Drucker werden von mehreren Arbeitsplätzen genutzt.
- Server stellen Anwendungen bereit.
- E-Mails werden versendet und empfangen.
- Backups werden zentral gespeichert.
- IT-Abteilungen verwalten Geräte aus der Ferne.

Netzwerke ermöglichen also Zusammenarbeit, zentrale Verwaltung und effizienten IT-Betrieb.

---

## Grundprinzip eines Netzwerks

Das Grundprinzip eines Netzwerks ist Datenkommunikation.

Ein Gerät sendet Daten, ein anderes Gerät empfängt Daten.

Damit das funktioniert, müssen mehrere Fragen geklärt sein:

- Welches Gerät sendet?
- Welches Gerät empfängt?
- Über welchen Weg werden Daten übertragen?
- Welche Adresse hat das Ziel?
- Welches Protokoll wird genutzt?
- Darf das Gerät kommunizieren?
- Ist der Dienst erreichbar?

Netzwerkkommunikation ist also nicht zufällig, sondern folgt festen Regeln und Protokollen.

---

## Clients und Server

In Unternehmensnetzwerken unterscheidet man häufig zwischen Clients und Servern.

| Begriff | Bedeutung                                   |
| ------- | ------------------------------------------- |
| Client  | Gerät oder Programm, das einen Dienst nutzt |
| Server  | System, das einen Dienst bereitstellt       |

Ein Client kann zum Beispiel ein Laptop, Desktop-PC, Smartphone oder Tablet sein.

Ein Server stellt Dienste bereit, zum Beispiel:

- Dateiserver
- Druckserver
- Webserver
- Mailserver
- Datenbankserver
- DHCP-Server
- DNS-Server
- Authentifizierungsserver
- Backup-Server

Client und Server beschreiben nicht immer nur Geräte, sondern auch Rollen.

Ein Computer kann in einem Zusammenhang Client sein und in einem anderen Zusammenhang selbst Dienste bereitstellen.

---

## Client-Server-Prinzip

Beim Client-Server-Prinzip fordert ein Client eine Leistung an und ein Server stellt diese Leistung bereit.

Beispielhafter Ablauf:

1. Ein Benutzer öffnet eine Datei auf einem Netzlaufwerk.
2. Der Client fragt den Dateiserver an.
3. Der Server prüft Berechtigungen.
4. Der Server liefert die Datei an den Client.
5. Der Benutzer kann mit der Datei arbeiten.

Dieses Prinzip ist sehr wichtig, weil viele Unternehmensdienste zentral bereitgestellt werden.

Vorteile:

- zentrale Datenhaltung
- bessere Verwaltung
- einfachere Datensicherung
- zentrale Benutzerrechte
- bessere Kontrolle
- einfacherer Support

Nachteile:

- Serverausfall kann viele Benutzer betreffen
- Netzwerk muss zuverlässig funktionieren
- zentrale Systeme müssen gut geschützt werden

---

## Peer-to-Peer-Prinzip

Neben dem Client-Server-Prinzip gibt es auch Peer-to-Peer.

Dabei kommunizieren Geräte direkt miteinander, ohne zentralen Server.

Peer-to-Peer kann in kleinen Umgebungen vorkommen, ist in professionellen Unternehmensnetzwerken aber oft weniger geeignet.

Nachteile von Peer-to-Peer im Unternehmen:

- schwerere Verwaltung
- unklare Zuständigkeiten
- schlechtere Sicherheit
- schwierige Datensicherung
- unübersichtliche Rechtevergabe
- schlechter skalierbar

Für Unternehmensnetzwerke ist eine zentrale Struktur meistens besser kontrollierbar.

---

## Netzwerkarten

Netzwerke können nach Größe und Einsatzbereich unterschieden werden.

| Netzwerkart | Bedeutung                                                  |
| ----------- | ---------------------------------------------------------- |
| PAN         | sehr kleines persönliches Netzwerk, zum Beispiel Bluetooth |
| LAN         | lokales Netzwerk innerhalb eines Gebäudes oder Bereichs    |
| WLAN        | drahtloses lokales Netzwerk                                |
| WAN         | großes Netzwerk über Standorte hinweg                      |
| VPN         | verschlüsselte Verbindung über ein unsicheres Netz         |
| Internet    | weltweites öffentliches Netzwerk                           |

In Unternehmen ist besonders das LAN wichtig. Dazu kommen oft WLAN, VPN, WAN-Verbindungen und Cloud-Anbindungen.

---

## LAN

LAN bedeutet **Local Area Network**.

Ein LAN ist ein lokales Netzwerk, zum Beispiel in einem Büro, einer Schule oder einem Rechenzentrum.

Typische Eigenschaften:

- hohe Geschwindigkeit
- geringe Verzögerung
- meistens private IP-Adressen
- zentrale Netzwerkkomponenten
- kontrollierte Umgebung
- oft kabelgebunden über Ethernet

Ein LAN verbindet zum Beispiel Arbeitsplatzrechner, Drucker, Server und Switches miteinander.

---

## WLAN

WLAN bedeutet **Wireless Local Area Network**.

Ein WLAN ist ein drahtloses lokales Netzwerk.

Vorteile:

- flexible Nutzung
- keine Netzwerkkabel am Arbeitsplatz nötig
- gut für mobile Geräte
- wichtig für Smartphones, Tablets und Laptops

Nachteile:

- abhängig von Signalqualität
- störanfälliger als Kabel
- Sicherheitskonfiguration besonders wichtig
- Geschwindigkeit kann schwanken
- Reichweite ist begrenzt

WLAN ist praktisch, ersetzt aber in vielen professionellen Bereichen nicht vollständig ein stabiles LAN.

---

## WAN

WAN bedeutet **Wide Area Network**.

Ein WAN verbindet Netzwerke über größere Entfernungen.

Beispiele:

- Verbindung zwischen Firmenstandorten
- Anbindung an ein Rechenzentrum
- Verbindung zu Cloud-Diensten
- Internetanbindung
- MPLS- oder VPN-Verbindungen

WAN-Verbindungen sind wichtig, wenn ein Unternehmen mehrere Standorte hat oder Dienste außerhalb des eigenen Gebäudes nutzt.

---

## VPN

VPN bedeutet **Virtual Private Network**.

Ein VPN stellt eine verschlüsselte Verbindung über ein anderes Netzwerk her, meistens über das Internet.

Typische Einsatzbereiche:

- Homeoffice-Zugriff
- Verbindung zwischen Standorten
- Zugriff auf interne Systeme von unterwegs
- sichere Administration
- externe Dienstleister mit eingeschränktem Zugriff

Ein VPN schützt die Verbindung, ersetzt aber keine saubere Rechteverwaltung oder Sicherheitsprüfung.

---

## Netzwerkkomponenten im Überblick

Ein Unternehmensnetzwerk besteht aus verschiedenen Komponenten.

| Komponente    | Aufgabe                                          |
| ------------- | ------------------------------------------------ |
| Netzwerkkarte | verbindet ein Gerät mit dem Netzwerk             |
| Switch        | verbindet Geräte im lokalen Netzwerk             |
| Router        | verbindet verschiedene Netzwerke                 |
| Firewall      | kontrolliert und filtert Netzwerkverkehr         |
| Access Point  | stellt WLAN bereit                               |
| Patchpanel    | verbindet Gebäudeverkabelung mit Netzwerktechnik |
| Netzwerkkabel | überträgt Daten elektrisch oder optisch          |
| Server        | stellt zentrale Dienste bereit                   |
| Client        | nutzt Dienste im Netzwerk                        |

Diese Komponenten arbeiten zusammen, damit Daten vom Sender zum Empfänger gelangen.

---

## Switch

Ein Switch verbindet Geräte innerhalb eines lokalen Netzwerks.

Er arbeitet hauptsächlich mit MAC-Adressen und leitet Daten gezielt an das richtige Gerät weiter.

Typische Aufgaben:

- Verbindung von PCs, Druckern und Servern
- Aufbau eines lokalen Netzwerks
- VLAN-Unterstützung
- Verbindung zu weiteren Switches
- PoE-Versorgung für Access Points oder IP-Telefone

Switches sind zentrale Bausteine in LANs.

---

## Router

Ein Router verbindet verschiedene Netzwerke miteinander.

Typische Aufgaben:

- Verbindung zwischen LAN und Internet
- Weiterleitung zwischen Subnetzen
- Routing zwischen Standorten
- Übergang zu anderen Netzen
- oft NAT in kleinen Netzwerken
- häufig Gateway-Funktion

Ein Router entscheidet anhand von IP-Adressen, wohin Daten weitergeleitet werden.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr.

Sie entscheidet, welcher Datenverkehr erlaubt oder blockiert wird.

Typische Aufgaben:

- Schutz vor unerlaubtem Zugriff
- Trennung von Netzbereichen
- Filterung nach Regeln
- Kontrolle von ein- und ausgehendem Verkehr
- Schutz von Servern und Clients
- Protokollierung von Verbindungen

Eine Firewall ist ein wichtiger Bestandteil der Netzwerksicherheit, ersetzt aber keine Updates, sicheren Passwörter oder Benutzerrechte.

---

## Access Point

Ein Access Point stellt WLAN bereit.

Er verbindet drahtlose Geräte mit dem kabelgebundenen Netzwerk.

Wichtige Punkte:

- SSID
- WLAN-Verschlüsselung
- Funkkanäle
- Reichweite
- Signalstärke
- Gastnetz
- VLAN-Zuordnung
- zentrale Verwaltung
- Roaming zwischen Access Points

Access Points müssen sinnvoll platziert und sicher konfiguriert werden.

---

## Netzwerkdienste

Viele wichtige Netzwerkfunktionen werden durch Dienste bereitgestellt.

| Dienst                    | Aufgabe                                                   |
| ------------------------- | --------------------------------------------------------- |
| DHCP                      | vergibt IP-Adressen und Netzwerkeinstellungen automatisch |
| DNS                       | übersetzt Namen in IP-Adressen                            |
| Datei- und Freigabedienst | stellt gemeinsame Dateien bereit                          |
| Druckdienst               | stellt Drucker im Netzwerk bereit                         |
| Authentifizierung         | prüft Benutzeranmeldung                                   |
| Verzeichnisdienst         | verwaltet Benutzer, Gruppen und Geräte                    |
| Backup-Dienst             | sichert Daten und Systeme                                 |
| Monitoring                | überwacht Systeme und Dienste                             |
| NTP                       | synchronisiert die Uhrzeit                                |

Ohne diese Dienste wäre ein Unternehmensnetzwerk deutlich schwerer zu verwalten.

---

## IP-Adresse, MAC-Adresse und Name

Ein Gerät kann im Netzwerk auf verschiedene Arten identifiziert werden.

| Identifikation | Bedeutung                         |
| -------------- | --------------------------------- |
| MAC-Adresse    | Hardwareadresse der Netzwerkkarte |
| IP-Adresse     | logische Adresse im Netzwerk      |
| Hostname       | Gerätename                        |
| DNS-Name       | Name, der über DNS aufgelöst wird |

Die MAC-Adresse ist wichtig im lokalen Netzwerk.  
Die IP-Adresse ist wichtig für Kommunikation zwischen Geräten und Netzwerken.  
DNS-Namen machen die Nutzung einfacher, weil Menschen sich Namen besser merken können als Zahlen.

---

## DHCP

DHCP bedeutet **Dynamic Host Configuration Protocol**.

DHCP vergibt Netzwerkeinstellungen automatisch.

Ein Client kann über DHCP erhalten:

- IP-Adresse
- Subnetzmaske
- Standardgateway
- DNS-Server
- weitere Optionen

Ohne DHCP müssten viele Geräte manuell konfiguriert werden.

In Unternehmensnetzwerken spart DHCP viel Aufwand und reduziert Fehler.

---

## DNS

DNS bedeutet **Domain Name System**.

DNS übersetzt Namen in IP-Adressen.

Beispiel:

Ein Benutzer gibt einen Namen ein, zum Beispiel einen Servernamen oder eine Webseite. DNS sorgt dafür, dass daraus die passende IP-Adresse gefunden wird.

Ohne DNS müsste man sich viele IP-Adressen merken.

DNS ist deshalb einer der wichtigsten Dienste im Netzwerk.

---

## Gateway

Ein Gateway ist der Übergang in ein anderes Netzwerk.

Im Alltag ist das Gateway oft der Router.

Wenn ein Client ein Ziel außerhalb des eigenen Netzwerks erreichen möchte, sendet er die Daten an sein Standardgateway.

Beispiel:

Ein Client möchte eine Webseite im Internet öffnen. Das Ziel liegt nicht im lokalen Netzwerk. Deshalb schickt der Client die Daten an das Gateway, das sie weiterleitet.

---

## Netzwerk im Ausbildungsbetrieb

In einem Ausbildungsbetrieb kann das Netzwerk je nach Größe sehr unterschiedlich aufgebaut sein.

Kleine Betriebe haben oft eine einfache Struktur:

- Router
- Switch
- WLAN
- Arbeitsplatzrechner
- Drucker
- eventuell NAS oder kleiner Server

Größere Betriebe haben meistens komplexere Strukturen:

- mehrere Switches
- VLANs
- Serverräume
- Firewalls
- mehrere WLAN-Zonen
- zentrale Benutzerverwaltung
- Backup-Systeme
- Monitoring
- Standortvernetzung
- Cloud-Anbindungen

Für Auszubildende ist wichtig, die eigene Umgebung schrittweise zu verstehen und zu dokumentieren.

---

## Netzwerkdokumentation

Netzwerke müssen dokumentiert werden, damit sie wartbar bleiben.

Wichtige Inhalte einer Netzwerkdokumentation:

- Netzplan
- IP-Adressbereiche
- VLANs
- Switches und Ports
- Router und Firewalls
- WLAN-SSIDs
- Server und Dienste
- Drucker
- Verkabelung
- Zugangsdatenverwaltung
- Verantwortlichkeiten
- Änderungen
- Notfallinformationen

Ohne Dokumentation wird Fehlersuche deutlich schwieriger.

Ein Netzwerk kann technisch funktionieren, aber trotzdem schlecht betreibbar sein, wenn niemand die Struktur kennt.

---

## Sicherheit im Unternehmensnetzwerk

Netzwerksicherheit beginnt nicht erst bei Angriffen aus dem Internet.

Auch interne Struktur, Rechte und Konfiguration sind wichtig.

Wichtige Sicherheitsmaßnahmen:

- Firewall-Regeln
- sichere WLAN-Verschlüsselung
- getrennte Gastnetze
- VLANs
- sichere Passwörter
- Benutzerrechte
- Netzwerksegmentierung
- Updates
- Monitoring
- Protokollierung
- VPN mit MFA
- kein unnötiger Zugriff zwischen Netzbereichen

Ein Unternehmensnetzwerk sollte nicht als eine große offene Fläche geplant werden. Besser ist eine sinnvolle Trennung nach Bereichen und Schutzbedarf.

---

## Verfügbarkeit

Verfügbarkeit bedeutet, dass Systeme und Dienste dann erreichbar sind, wenn sie gebraucht werden.

Im Netzwerk beeinflussen viele Faktoren die Verfügbarkeit:

- Internetverbindung
- Switches
- Router
- Firewalls
- Server
- Stromversorgung
- DNS
- DHCP
- WLAN-Abdeckung
- Verkabelung
- Konfiguration

Ein einzelner Fehler kann viele Benutzer betreffen.

Beispiel: Wenn der DHCP-Server ausfällt, bekommen neue Clients eventuell keine IP-Adresse. Wenn DNS ausfällt, funktionieren viele Dienste nicht mehr über Namen.

---

## Typische Netzwerkprobleme

| Problem                      | Mögliche Ursache                             |
| ---------------------------- | -------------------------------------------- |
| kein Internet                | Gateway, DNS, Router, Provider oder WLAN     |
| keine IP-Adresse             | DHCP-Problem, Kabel, WLAN oder Netzwerkkarte |
| Server nicht erreichbar      | DNS, Routing, Firewall oder Serverdienst     |
| langsames Netzwerk           | WLAN-Störung, Auslastung, defekte Kabel      |
| Drucker nicht erreichbar     | IP geändert, Treiber, Freigabe oder Netzwerk |
| Anmeldung funktioniert nicht | Domäne, DNS, Netzwerk oder Benutzerkonto     |
| Verbindung bricht ab         | WLAN-Signal, Kabel, Switch oder Treiber      |

Bei Netzwerkproblemen ist strukturiertes Vorgehen wichtig. Man sollte nicht zufällig Einstellungen ändern, sondern logisch prüfen.

---

## Grundlegendes Vorgehen bei Netzwerkproblemen

Eine einfache Reihenfolge zur Fehlersuche:

1. Ist das Gerät eingeschaltet und verbunden?
2. Funktioniert LAN oder WLAN?
3. Hat das Gerät eine IP-Adresse?
4. Ist das Gateway erreichbar?
5. Funktioniert DNS?
6. Ist das Zielsystem erreichbar?
7. Blockiert eine Firewall?
8. Funktioniert der benötigte Dienst?
9. Gibt es Benutzer- oder Rechteprobleme?
10. Wurde etwas an der Konfiguration geändert?

Diese Denkweise hilft, Fehler einzugrenzen.

Die konkreten Befehle und Werkzeuge werden in späteren LF3-Kapiteln genauer behandelt.

---

## Praxisbeispiele

### Beispiel 1: Büroarbeitsplatz im LAN

Ein neuer Arbeitsplatz wird per Netzwerkkabel an einen Switch angeschlossen. Über DHCP erhält der Client eine IP-Adresse, ein Gateway und DNS-Server. Danach kann der Benutzer auf Internet, Netzlaufwerke und Drucker zugreifen.

### Beispiel 2: Laptop im WLAN

Ein Laptop verbindet sich mit dem Firmen-WLAN. Der Access Point leitet die Verbindung ins Unternehmensnetz weiter. Je nach WLAN-Konfiguration bekommt der Benutzer Zugriff auf interne Dienste oder nur auf das Internet.

### Beispiel 3: Homeoffice über VPN

Ein Benutzer arbeitet von zu Hause. Über VPN baut der Laptop eine verschlüsselte Verbindung zum Unternehmensnetz auf. Dadurch können interne Dienste sicher genutzt werden, wenn Benutzerrechte und Sicherheitsrichtlinien passen.

---

## Typische Fehler

| Fehler                                | Problem                                            |
| ------------------------------------- | -------------------------------------------------- |
| Netzwerk nur als “Internet” verstehen | interne Dienste und Infrastruktur werden übersehen |
| DNS und DHCP unterschätzen            | viele Netzwerkprobleme hängen damit zusammen       |
| keine Dokumentation führen            | Fehlersuche wird schwierig                         |
| alle Geräte im gleichen Netz lassen   | Sicherheitsrisiken durch fehlende Trennung         |
| WLAN wie LAN behandeln                | Funknetzwerke haben andere Probleme und Risiken    |
| Firewall-Regeln nicht beachten        | Dienste sind trotz Verbindung nicht erreichbar     |
| Änderungen nicht dokumentieren        | spätere Probleme sind schwer nachvollziehbar       |
| nur Symptome beheben                  | eigentliche Ursache bleibt bestehen                |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Netzwerkwissen eine Kernkompetenz.

Ein FISI muss verstehen, wie Clients, Server, Netzwerkgeräte und Dienste zusammenarbeiten.

In der Praxis bedeutet das:

- Clients ins Netzwerk einbinden
- IP-Konfiguration prüfen
- Netzwerkdienste verstehen
- Fehler systematisch analysieren
- Sicherheitsaspekte beachten
- Netzwerke dokumentieren
- Benutzer unterstützen
- Änderungen nachvollziehbar durchführen

Ein guter FISI denkt nicht nur:

> Das Gerät hat Internet.

sondern:

> Welche Netzwerkkonfiguration hat das Gerät, welche Dienste nutzt es, welche Rechte gelten und über welchen Weg erreicht es sein Ziel?

---

## Kurze Zusammenfassung

Netzwerke verbinden Geräte, Benutzer und Dienste miteinander.

Ein Unternehmensnetzwerk besteht aus Clients, Servern, Switches, Routern, Firewalls, Access Points, Kabeln, WLAN, IP-Adressen und wichtigen Diensten wie DHCP und DNS.

Für FISI ist wichtig, Netzwerke nicht nur oberflächlich zu verstehen, sondern ihre Struktur, Dienste, Sicherheit und Dokumentation zu kennen.

LF3 bildet damit eine wichtige Grundlage für Systemadministration, Netzwerkadministration und professionellen IT-Support.
