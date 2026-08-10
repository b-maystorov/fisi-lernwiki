# 3.5 Clientintegration planen und durchführen

In diesem Kapitel geht es darum, Clients geplant, sicher und nachvollziehbar in ein Netzwerk einzubinden.

Ein Client ist zum Beispiel ein Desktop-PC, Laptop, Tablet, Smartphone oder Thin Client, der Netzwerkdienste nutzt. Damit ein Client im Unternehmensnetz funktioniert, reicht es nicht, ihn nur mit WLAN oder LAN zu verbinden. Er benötigt eine passende Netzwerkkonfiguration, Benutzeranmeldung, Rechte, Sicherheitsrichtlinien, Software, Updates und eine saubere Dokumentation.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr praxisnah, weil die Einbindung von Clients zu den typischen Aufgaben im IT-Betrieb gehört.

---

## Kurz erklärt

Clientintegration bedeutet, ein Endgerät so in eine IT-Umgebung einzubinden, dass es zuverlässig, sicher und passend zur Aufgabe genutzt werden kann.

Dazu gehören:

- Netzwerkverbindung herstellen
- IP-Konfiguration prüfen
- DNS und Gateway einrichten
- Benutzeranmeldung ermöglichen
- Rechte und Gruppen zuweisen
- Software bereitstellen
- Sicherheitsrichtlinien anwenden
- Zugriff auf Drucker und Dateiablagen einrichten
- Cloud-Dienste anbinden
- Funktion testen
- System dokumentieren

Ein integrierter Client soll nicht nur „Internet haben“, sondern korrekt Teil der Unternehmensumgebung sein.

---

## Fachliche Einordnung

Ein Client ist in einem Unternehmensnetz meistens von mehreren Diensten abhängig.

Typische Abhängigkeiten:

| Bereich           | Bedeutung                                                      |
| ----------------- | -------------------------------------------------------------- |
| Netzwerk          | LAN, WLAN, VPN, VLAN, IP-Adresse                               |
| Namensauflösung   | DNS für Server- und Dienstnamen                                |
| Adressvergabe     | DHCP oder statische IP-Konfiguration                           |
| Authentifizierung | Anmeldung über lokale Konten, Domäne oder Cloud-Identität      |
| Berechtigungen    | Zugriff auf Dateien, Drucker, Anwendungen und Systeme          |
| Sicherheit        | Updates, Verschlüsselung, Firewall, Endpoint-Schutz            |
| Verwaltung        | Gruppenrichtlinien, MDM, Inventarisierung                      |
| Software          | Standardprogramme, Fachanwendungen, Treiber                    |
| Dokumentation     | Hostname, Benutzer, Standort, IP, Seriennummer, Besonderheiten |

Wenn einer dieser Bereiche falsch konfiguriert ist, kann der Client nur eingeschränkt oder gar nicht im Netzwerk arbeiten.

---

## Ziel der Clientintegration

Das Ziel ist ein arbeitsfähiger, sicherer und wartbarer Client.

Ein korrekt integrierter Client sollte:

- eine gültige Netzwerkverbindung haben
- eine passende IP-Konfiguration besitzen
- interne und externe Dienste erreichen
- Benutzer korrekt anmelden
- nur erlaubte Zugriffe ermöglichen
- benötigte Software enthalten
- Sicherheitsvorgaben erfüllen
- zentral verwaltbar sein
- dokumentiert sein
- bei Problemen analysierbar sein

Clientintegration ist damit ein Zusammenspiel aus Technik, Sicherheit, Organisation und Dokumentation.

---

## Planung vor der Integration

Vor der eigentlichen Einrichtung sollte geklärt werden, wofür der Client genutzt wird.

Wichtige Fragen:

| Frage                                   | Bedeutung                                  |
| --------------------------------------- | ------------------------------------------ |
| Wer nutzt den Client?                   | Benutzerkonto, Rechte, Gruppen             |
| Wo wird der Client genutzt?             | Büro, Homeoffice, Außendienst, Schulung    |
| Welche Aufgaben werden erledigt?        | Hardware- und Softwareanforderungen        |
| Welche Netzwerkverbindung wird genutzt? | LAN, WLAN, VPN, Dockingstation             |
| Welche Dienste werden benötigt?         | Dateiablagen, Drucker, Cloud, Fachsoftware |
| Welche Sicherheitsanforderungen gelten? | Verschlüsselung, MFA, Endpoint-Schutz      |
| Wie wird der Client verwaltet?          | Domäne, MDM, Gruppenrichtlinien            |
| Wie wird Support geleistet?             | Fernwartung, Ticket, Dokumentation         |

Eine gute Planung verhindert spätere Nacharbeit.

---

## Anforderungen an den Client

Der Client muss technisch zur Aufgabe passen.

Wichtige Client-Anforderungen:

- passende CPU-Leistung
- ausreichend RAM
- ausreichend schneller Massenspeicher
- aktuelles Betriebssystem
- kompatible Treiber
- passende Schnittstellen
- LAN oder WLAN
- TPM für Verschlüsselung
- Unterstützung für zentrale Verwaltung
- ausreichende Akkulaufzeit bei mobilen Geräten
- passende Monitor- oder Dockingfähigkeit
- Support durch Hersteller

Ein Client für Büroarbeit hat andere Anforderungen als ein Entwicklergerät, CAD-Arbeitsplatz oder Schulungsclient.

---

## Anforderungen an das Netzwerk

Damit ein Client sinnvoll eingebunden werden kann, muss auch das Netzwerk vorbereitet sein.

Wichtige Netzwerk-Anforderungen:

- funktionierende Switch-Ports
- passende VLAN-Zuordnung
- stabile WLAN-Abdeckung
- DHCP verfügbar oder statische IP geplant
- DNS erreichbar
- Gateway erreichbar
- notwendige Firewall-Regeln vorhanden
- Zugriff auf Serverdienste möglich
- ausreichende Bandbreite
- sichere Authentifizierung
- Dokumentation der Netzbereiche

Ein Client kann technisch korrekt eingerichtet sein, aber trotzdem nicht funktionieren, wenn Netzwerkdienste oder Firewall-Regeln nicht passen.

---

## LAN-Integration

Bei einer LAN-Integration wird der Client per Netzwerkkabel verbunden.

Typischer Ablauf:

1. Netzwerkkabel anschließen
2. Link-Status prüfen
3. Switch-Port prüfen
4. VLAN-Zuordnung kontrollieren
5. IP-Adresse erhalten oder statisch setzen
6. Gateway testen
7. DNS testen
8. interne Dienste testen
9. Internetzugang testen
10. Dokumentation aktualisieren

LAN ist meistens stabiler als WLAN und wird oft für stationäre Arbeitsplätze, Drucker, Server und wichtige Systeme genutzt.

---

## WLAN-Integration

Bei WLAN wird der Client drahtlos über einen Access Point verbunden.

Wichtige Punkte:

- richtige SSID
- sichere Verschlüsselung
- passende Authentifizierung
- ausreichende Signalstärke
- richtige VLAN-Zuordnung
- keine Überlastung des Funkbereichs
- Roaming bei mehreren Access Points
- Trennung von internem WLAN und Gastnetz

WLAN ist flexibel, aber störanfälliger als LAN.

Für Unternehmen ist besonders wichtig, dass WLAN nicht nur bequem, sondern sicher konfiguriert ist.

---

## VPN-Integration

VPN wird genutzt, wenn Clients von außerhalb sicher auf interne Ressourcen zugreifen sollen.

Typische Einsatzbereiche:

- Homeoffice
- Außendienst
- Fernadministration
- externe Dienstleister
- Standortzugriff

Wichtige Anforderungen:

- verschlüsselte Verbindung
- sichere Anmeldung
- Mehrfaktor-Authentifizierung
- passende Benutzerrechte
- Zugriff nur auf benötigte Dienste
- Protokollierung
- aktueller VPN-Client
- klare Supportwege

VPN sollte nicht als vollständiger Ersatz für Rechteverwaltung gesehen werden. Auch über VPN muss gelten: Benutzer erhalten nur die Zugriffe, die sie wirklich brauchen.

---

## IP-Konfiguration

Ein Client benötigt eine gültige IP-Konfiguration.

Dazu gehören:

| Einstellung           | Bedeutung                              |
| --------------------- | -------------------------------------- |
| IP-Adresse            | logische Adresse des Clients           |
| Subnetzmaske / Präfix | beschreibt das lokale Netz             |
| Standardgateway       | Weg in andere Netzwerke                |
| DNS-Server            | Namensauflösung                        |
| DHCP                  | automatische Vergabe der Einstellungen |

Ohne korrekte IP-Konfiguration kann ein Client nicht sauber kommunizieren.

Typische Fehler sind falsche IP-Adresse, falsches Gateway, falscher DNS-Server oder IP-Adresskonflikte.

---

## DHCP oder statische IP-Adresse

Clients erhalten ihre Netzwerkkonfiguration meistens per DHCP.

### DHCP

Vorteile:

- einfache Verwaltung
- weniger manuelle Fehler
- automatische Vergabe
- zentrale Steuerung
- gut für viele Clients

Typisch für:

- Arbeitsplatz-PCs
- Laptops
- Smartphones
- Tablets
- Schulungsgeräte

### Statische IP-Adresse

Eine statische IP-Adresse wird manuell festgelegt.

Typisch für:

- Server
- Netzwerkdrucker
- Router
- Switches
- Firewalls
- Access Points
- wichtige Infrastrukturgeräte

Für normale Clients ist DHCP meistens sinnvoller. Für zentrale Systeme ist eine feste oder reservierte Adresse oft besser.

---

## DNS und Namensauflösung

DNS ist für die Namensauflösung zuständig.

Ein Client nutzt DNS, um Namen in IP-Adressen umzuwandeln.

Beispiele:

- Servername zu IP-Adresse
- Webadresse zu IP-Adresse
- interne Dienste erreichbar machen
- Domänenanmeldung unterstützen

Viele Netzwerkprobleme wirken für Benutzer wie „Internet geht nicht“, sind aber eigentlich DNS-Probleme.

Deshalb gehört DNS-Prüfung immer zur Clientintegration.

---

## Standardgateway

Das Standardgateway ist der Weg aus dem lokalen Netzwerk heraus.

Wenn ein Client ein Ziel außerhalb des eigenen Subnetzes erreichen möchte, sendet er Daten an das Gateway.

Typische Ziele außerhalb des eigenen Netzes:

- Internet
- andere VLANs
- Servernetze
- Cloud-Dienste
- VPN-Ziele
- andere Standorte

Ein falsches Gateway führt dazu, dass lokale Kommunikation vielleicht funktioniert, aber Ziele außerhalb des Netzes nicht erreichbar sind.

---

## Hostname und Namensschema

Jeder Client sollte einen sinnvollen Hostname besitzen.

Ein Hostname hilft bei:

- Inventarisierung
- Support
- Fernwartung
- Monitoring
- Domänenverwaltung
- Dokumentation
- Fehleranalyse

In Unternehmen werden häufig Namensschemata genutzt.

Beispiele für Informationen im Namen:

- Standort
- Gerätetyp
- Abteilung
- fortlaufende Nummer
- Rolle

Ein einheitliches Namensschema erleichtert Verwaltung und Übersicht.

---

## Benutzeranmeldung

Ein Client muss so eingerichtet sein, dass Benutzer sich anmelden können.

Es gibt verschiedene Formen der Anmeldung:

| Art           | Erklärung                                   |
| ------------- | ------------------------------------------- |
| lokales Konto | Konto existiert nur auf diesem Gerät        |
| Domänenkonto  | zentrale Anmeldung über eine Domäne         |
| Cloud-Konto   | Anmeldung über einen Cloud-Identitätsdienst |
| Gastkonto     | eingeschränkter temporärer Zugriff          |

In Unternehmen sind zentrale Benutzerkonten meistens sinnvoller, weil Rechte, Gruppen und Richtlinien besser verwaltet werden können.

---

## Lokale Konten

Lokale Konten existieren nur auf einem bestimmten Gerät.

Vorteile:

- einfach einzurichten
- unabhängig von zentraler Infrastruktur
- sinnvoll für Einzelgeräte oder Tests

Nachteile:

- schwer zentral zu verwalten
- Benutzer und Passwörter müssen lokal gepflegt werden
- Rechte sind schwieriger zu kontrollieren
- ungeeignet für größere Umgebungen
- Support und Nachvollziehbarkeit schlechter

Lokale Konten sollten in Unternehmen nur bewusst und kontrolliert eingesetzt werden.

---

## Domänenanbindung

Bei einer Domänenanbindung wird ein Client in eine zentrale Verwaltungsstruktur aufgenommen.

Typische Vorteile:

- zentrale Benutzeranmeldung
- Gruppenrichtlinien
- zentrale Rechteverwaltung
- einfachere Softwareverteilung
- bessere Sicherheit
- einheitliche Einstellungen
- bessere Inventarisierung
- zentrale Administration

In Windows-Umgebungen wird dafür häufig eine Domäne genutzt. In anderen Umgebungen können auch Verzeichnisdienste oder zentrale Identitätsdienste eingesetzt werden.

---

## Verzeichnisdienst

Ein Verzeichnisdienst speichert Informationen über Benutzer, Gruppen, Geräte und Berechtigungen.

Typische Aufgaben:

- Benutzer verwalten
- Gruppen verwalten
- Geräte verwalten
- Anmeldung prüfen
- Rechte zuordnen
- Richtlinien anwenden
- zentrale Verwaltung ermöglichen

Ein Verzeichnisdienst ist besonders wichtig in größeren Netzwerken, weil viele Benutzer und Geräte nicht sinnvoll manuell auf jedem einzelnen System verwaltet werden können.

---

## Gruppen und Rechte

Benutzerrechte sollten nicht einzeln und unkontrolliert vergeben werden.

Besser ist die Verwaltung über Gruppen.

Beispiel:

Ein Benutzer ist Mitglied der Gruppe „Buchhaltung“.  
Diese Gruppe erhält Zugriff auf bestimmte Netzlaufwerke, Drucker oder Anwendungen.

Vorteile der Gruppenverwaltung:

- bessere Übersicht
- einfachere Administration
- weniger Fehler
- klarere Berechtigungen
- bessere Nachvollziehbarkeit
- leichteres Entfernen von Rechten

Wichtig ist das Prinzip der minimalen Rechte. Benutzer sollen nur Zugriff auf das haben, was sie für ihre Arbeit brauchen.

---

## Netzlaufwerke und Dateiablagen

Viele Clients benötigen Zugriff auf zentrale Dateiablagen.

Dazu gehören zum Beispiel:

- Abteilungslaufwerke
- Projektlaufwerke
- persönliche Laufwerke
- gemeinsame Freigaben
- Archivbereiche
- Cloud-Speicher

Wichtige Punkte:

- korrekte Berechtigungen
- sichere Verbindung
- klare Ordnerstruktur
- Backup-Konzept
- keine unnötigen Zugriffe
- Dokumentation der Freigaben

Dateizugriff ist oft einer der wichtigsten Punkte bei der Arbeitsplatzintegration.

---

## Drucker und Scanner

Clients benötigen häufig Zugriff auf Drucker oder Scanner.

Wichtige Punkte:

- Netzwerkdrucker erreichbar
- richtiger Treiber installiert
- passende Druckerwarteschlange
- Berechtigungen korrekt
- Standarddrucker gesetzt, falls nötig
- Scan-Ziele eingerichtet
- Drucktest durchgeführt

Druckerprobleme entstehen häufig durch falsche Treiber, geänderte IP-Adressen, Berechtigungen oder fehlerhafte Warteschlangen.

---

## Softwarebereitstellung

Ein Client muss die benötigte Software erhalten.

Dazu können gehören:

- Betriebssystem
- Office-Programme
- Browser
- E-Mail-Client
- Fachanwendungen
- Sicherheitssoftware
- VPN-Client
- Druckertreiber
- Fernwartungssoftware
- Entwicklungswerkzeuge
- Kommunikationssoftware

In Unternehmen wird Software oft zentral verteilt, damit alle Geräte einheitlich und kontrolliert eingerichtet werden.

---

## Lizenzierung

Software darf nur genutzt werden, wenn die Lizenzbedingungen erfüllt sind.

Wichtige Fragen:

- Ist die Software lizenziert?
- Wird pro Benutzer oder pro Gerät lizenziert?
- Gibt es eine Laufzeit?
- Ist kommerzielle Nutzung erlaubt?
- Darf die Software auf mehreren Geräten installiert werden?
- Gibt es Cloud- oder Abonnementmodelle?
- Wer verwaltet die Lizenz?

Falsche Lizenzierung kann rechtliche und finanzielle Probleme verursachen.

---

## Cloud-Dienste

Viele moderne Clients nutzen Cloud-Dienste.

Beispiele:

- E-Mail
- Kalender
- Cloud-Speicher
- Kollaboration
- Videokonferenzen
- Geräteverwaltung
- Identitätsdienste
- Webanwendungen
- Backup-Dienste

Cloud-Dienste müssen bei der Clientintegration mitgedacht werden.

Wichtige Punkte:

- Benutzerkonto
- Anmeldung
- Mehrfaktor-Authentifizierung
- Datenschutz
- Synchronisation
- Zugriff von außen
- Offline-Verfügbarkeit
- Sicherheitsrichtlinien
- Lizenzmodell
- Abhängigkeit von Internetverbindung

Cloud-Dienste können die Arbeit flexibler machen, erhöhen aber auch die Bedeutung von Identitäts- und Zugriffsschutz.

---

## Gerätemanagement

Gerätemanagement bedeutet, Clients zentral zu verwalten.

Mögliche Funktionen:

- Geräte inventarisieren
- Richtlinien verteilen
- Software installieren
- Updates steuern
- Sicherheitsstatus prüfen
- Geräte sperren
- Geräte zurücksetzen
- Konfigurationen ausrollen
- Compliance prüfen

Zentrales Gerätemanagement ist besonders wichtig bei vielen Laptops, mobilen Geräten oder Homeoffice-Arbeitsplätzen.

---

## Gruppenrichtlinien und Richtlinien

Richtlinien sorgen dafür, dass Clients einheitlich konfiguriert werden.

Typische Einstellungen:

- Passwortregeln
- Bildschirmsperre
- Firewall
- Netzlaufwerke
- Drucker
- Updateverhalten
- Desktop-Einstellungen
- Softwareeinschränkungen
- Sicherheitsoptionen
- Laufwerksverschlüsselung

Richtlinien verhindern, dass jedes Gerät einzeln und unterschiedlich konfiguriert wird.

---

## Updates und Patchmanagement

Clients müssen aktuell gehalten werden.

Dazu gehören:

- Betriebssystemupdates
- Sicherheitsupdates
- Treiberupdates
- Firmwareupdates
- Softwareupdates
- Browserupdates
- Updates für Sicherheitssoftware

Patchmanagement bedeutet, Updates geplant und kontrolliert einzuspielen.

Wichtig ist ein Gleichgewicht zwischen Sicherheit und Stabilität. Updates schließen Sicherheitslücken, können aber in seltenen Fällen auch Probleme verursachen. Deshalb werden sie in Unternehmen oft getestet und gesteuert verteilt.

---

## Endpoint-Sicherheit

Endpoint-Sicherheit schützt Clients als Endgeräte im Netzwerk.

Wichtige Maßnahmen:

- Virenschutz oder Endpoint Detection
- lokale Firewall
- Festplattenverschlüsselung
- sichere Passwörter
- Mehrfaktor-Authentifizierung
- Bildschirmsperre
- keine unnötigen Adminrechte
- sichere Browserkonfiguration
- USB-Kontrolle
- regelmäßige Updates
- Protokollierung
- zentrale Überwachung

Clients sind ein häufiger Angriffspunkt, weil Benutzer täglich mit E-Mails, Webseiten, Dateien und externen Geräten arbeiten.

---

## Festplattenverschlüsselung

Festplattenverschlüsselung schützt gespeicherte Daten.

Sie ist besonders wichtig bei:

- Laptops
- mobilen Geräten
- Homeoffice-Geräten
- Geräten mit personenbezogenen Daten
- Geräten mit Kundendaten
- Geräten außerhalb sicherer Büroräume

Wenn ein verschlüsseltes Gerät verloren geht, sind die Daten deutlich besser geschützt.

Verschlüsselung schützt aber nur, wenn Anmeldung, Schlüsselverwaltung und Wiederherstellung sauber organisiert sind.

---

## Lokale Administratorrechte

Lokale Administratorrechte sollten in Unternehmen vorsichtig vergeben werden.

Risiken unnötiger Adminrechte:

- Benutzer kann Sicherheitssoftware deaktivieren
- Schadsoftware erhält mehr Rechte
- Systemkonfiguration kann beschädigt werden
- unerlaubte Software kann installiert werden
- Fehlersuche wird schwieriger
- Sicherheitsrichtlinien können umgangen werden

Für normale Benutzer ist ein Standardkonto meistens besser. Adminrechte sollten nur gezielt, dokumentiert und zeitlich begrenzt vergeben werden.

---

## Integration mobiler Geräte

Mobile Geräte wie Laptops, Tablets und Smartphones benötigen besondere Aufmerksamkeit.

Wichtige Punkte:

- WLAN und VPN
- Verschlüsselung
- Gerätesperre
- MFA
- zentrale Verwaltung
- Verlust oder Diebstahl
- private und geschäftliche Daten trennen
- Cloud-Zugriff
- Updatekontrolle
- Fernlöschung bei Bedarf

Mobile Geräte verlassen häufiger das Unternehmensnetz und müssen deshalb besonders gut abgesichert werden.

---

## Funktionstest nach der Integration

Nach der Einrichtung muss geprüft werden, ob der Client korrekt funktioniert.

Typische Tests:

- Gerät startet fehlerfrei
- Benutzer kann sich anmelden
- LAN oder WLAN funktioniert
- IP-Adresse ist korrekt
- DNS funktioniert
- Gateway ist erreichbar
- Internetzugang funktioniert
- interne Server sind erreichbar
- Netzlaufwerke sind verbunden
- Drucker funktioniert
- benötigte Software startet
- Updates sind installiert
- Sicherheitssoftware ist aktiv
- Verschlüsselung ist aktiv
- Richtlinien wurden angewendet

Ein Test sollte aus Sicht der IT und aus Sicht des Benutzers durchgeführt werden.

---

## Dokumentation der Clientintegration

Die Clientintegration muss dokumentiert werden.

Wichtige Informationen:

- Hostname
- Gerätetyp
- Seriennummer
- Inventarnummer
- Standort
- Benutzer
- Betriebssystem
- installierte Software
- Lizenzinformationen
- Netzwerkanschluss
- VLAN
- IP-Adresse oder DHCP-Reservierung
- MAC-Adresse
- Sicherheitsstatus
- Verschlüsselung
- besondere Konfiguration
- Übergabedatum
- offene Punkte

Dokumentation ist wichtig für Support, Wartung, Sicherheit, Inventar und spätere Fehleranalyse.

---

## Praxisbeispiele

### Beispiel 1: Büro-Client

Ein Desktop-PC wird per LAN verbunden, erhält per DHCP eine IP-Adresse, wird in die Domäne aufgenommen, bekommt Standardsoftware, Netzlaufwerke, Drucker und Sicherheitsrichtlinien. Danach wird die Funktion getestet und dokumentiert.

### Beispiel 2: Homeoffice-Laptop

Ein Laptop wird mit Verschlüsselung, VPN, Cloud-Anmeldung, MFA, Webcam, Headset und zentraler Verwaltung eingerichtet. Besonders wichtig sind Sicherheit, Updates und Support bei Problemen außerhalb des Büros.

### Beispiel 3: Schulungsclient

Ein Schulungsclient wird mit Standardsoftware vorbereitet und so eingerichtet, dass er schnell zurückgesetzt oder neu installiert werden kann. Wichtig sind einfache Wiederherstellung, klare Benutzerrechte und ein einheitlicher Zustand.

---

## Typische Fehler

| Fehler                                          | Problem                                        |
| ----------------------------------------------- | ---------------------------------------------- |
| Client nur mit WLAN verbinden                   | zentrale Dienste, Rechte und Sicherheit fehlen |
| DNS nicht prüfen                                | interne Dienste sind nicht erreichbar          |
| falsches VLAN verwenden                         | Client landet im falschen Netzbereich          |
| lokale Adminrechte unnötig vergeben             | Sicherheitsrisiko                              |
| Software manuell und uneinheitlich installieren | Wartung wird schwieriger                       |
| Lizenzen nicht prüfen                           | rechtliche und finanzielle Risiken             |
| Verschlüsselung vergessen                       | Datenrisiko bei Verlust                        |
| keine Funktionstests durchführen                | Fehler fallen erst beim Benutzer auf           |
| Client nicht dokumentieren                      | Support und Inventar werden schwierig          |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist die Clientintegration eine typische Kernaufgabe.

Ein FISI muss nicht nur Geräte anschließen, sondern sicherstellen, dass sie korrekt in die gesamte IT-Umgebung eingebunden sind.

Dazu gehören Netzwerk, Benutzerkonten, Rechte, Software, Sicherheit, Cloud-Dienste, Updates, Tests und Dokumentation.

Ein guter FISI betrachtet einen Client nicht isoliert, sondern als Teil eines größeren Systems aus Netzwerk, Diensten, Benutzern und Sicherheitsrichtlinien.

---

## Kurze Zusammenfassung

Clientintegration bedeutet, ein Endgerät geplant und sicher in eine IT-Umgebung einzubinden.

Wichtige Bestandteile sind Netzwerkverbindung, IP-Konfiguration, DNS, Gateway, Benutzeranmeldung, Rechte, Software, Cloud-Dienste, Gerätemanagement, Sicherheitsmaßnahmen, Funktionstests und Dokumentation.

Für FISI ist dieses Thema besonders wichtig, weil Clients die direkte Arbeitsumgebung der Benutzer bilden und zuverlässig, sicher und wartbar betrieben werden müssen.
