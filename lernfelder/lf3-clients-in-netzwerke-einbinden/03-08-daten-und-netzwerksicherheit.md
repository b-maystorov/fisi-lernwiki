# 3.8 Grundlagen der Daten- und Netzwerksicherheit

In diesem Kapitel geht es um grundlegende Maßnahmen zum Schutz von Daten, Systemen und Netzwerken.

Daten- und Netzwerksicherheit ist ein zentraler Bestandteil moderner IT-Infrastrukturen. Netzwerke verbinden Clients, Server, Benutzer, Anwendungen und Cloud-Dienste miteinander. Dadurch entstehen viele Möglichkeiten zur Zusammenarbeit, aber auch Risiken durch Fehlkonfigurationen, Ausfälle, Schadsoftware, unbefugten Zugriff oder Datenverlust.

Für Fachinformatiker für Systemintegration ist dieses Thema besonders wichtig, weil Sicherheit nicht erst nach der Installation beginnt, sondern von Anfang an geplant, umgesetzt, geprüft und dokumentiert werden muss.

---

## Kurz erklärt

Daten- und Netzwerksicherheit bedeutet, Informationen und IT-Systeme vor Verlust, Manipulation, unbefugtem Zugriff und Ausfall zu schützen.

Wichtige Ziele sind:

- Daten schützen
- Zugriff kontrollieren
- Netzwerke trennen
- Systeme aktuell halten
- Ausfälle vermeiden
- Backups erstellen
- Angriffe erschweren
- Schäden begrenzen
- Wiederherstellung ermöglichen
- Sicherheitsmaßnahmen dokumentieren

Ein sicheres Netzwerk ist nicht nur ein Netzwerk mit Firewall. Sicherheit entsteht durch mehrere Maßnahmen, die zusammenwirken.

---

## Grundziele der Informationssicherheit

In der IT-Sicherheit werden häufig drei zentrale Schutzziele genannt.

| Schutzziel      | Bedeutung                                                        |
| --------------- | ---------------------------------------------------------------- |
| Vertraulichkeit | Daten dürfen nur von berechtigten Personen gelesen werden        |
| Integrität      | Daten dürfen nicht unbemerkt verändert werden                    |
| Verfügbarkeit   | Systeme und Daten müssen nutzbar sein, wenn sie gebraucht werden |

Diese drei Ziele nennt man oft auch die **CIA-Triade**.

Vertraulichkeit schützt vor unbefugtem Zugriff.  
Integrität schützt vor falschen oder manipulierten Daten.  
Verfügbarkeit schützt vor Ausfall und Nicht-Erreichbarkeit.

---

## Vertraulichkeit

Vertraulichkeit bedeutet, dass Informationen nur für berechtigte Personen zugänglich sind.

Maßnahmen für Vertraulichkeit:

- Benutzerkonten
- sichere Passwörter
- Mehrfaktor-Authentifizierung
- Berechtigungen
- Verschlüsselung
- Zugriffskontrolle
- VPN
- getrennte Netzbereiche
- sichere Dateiablagen
- Schutz mobiler Geräte

Beispiel:

Ein Mitarbeiter aus der Buchhaltung darf auf Buchhaltungsdaten zugreifen. Ein normaler Benutzer aus einer anderen Abteilung sollte diese Daten nicht sehen können.

---

## Integrität

Integrität bedeutet, dass Daten korrekt, vollständig und unverändert bleiben.

Daten dürfen nicht unbemerkt manipuliert werden.

Maßnahmen für Integrität:

- Dateiberechtigungen
- Prüfsummen
- digitale Signaturen
- Protokollierung
- Versionsverwaltung
- Backup
- Schutz vor Schadsoftware
- kontrollierte Änderungen
- Rechteverwaltung
- Monitoring

Integrität ist wichtig, weil falsche Daten zu falschen Entscheidungen führen können.

Beispiel:

Wenn eine Konfigurationsdatei, Datenbank oder Rechnung unbemerkt verändert wird, kann das technische oder wirtschaftliche Schäden verursachen.

---

## Verfügbarkeit

Verfügbarkeit bedeutet, dass Systeme, Dienste und Daten erreichbar sind, wenn sie benötigt werden.

Maßnahmen für Verfügbarkeit:

- stabile Hardware
- redundante Systeme
- USV
- RAID
- Backups
- Monitoring
- Wartung
- Ersatzteile
- Notfallpläne
- dokumentierte Wiederherstellung
- sichere Updates
- Schutz vor Überlastung

Verfügbarkeit ist besonders wichtig bei zentralen Diensten wie DNS, DHCP, Dateiablagen, E-Mail, Firewalls, Internetanbindung oder Authentifizierung.

Wenn zentrale Dienste ausfallen, können viele Benutzer gleichzeitig betroffen sein.

---

## Bedrohungen für Daten und Netzwerke

IT-Systeme können durch viele Ursachen gefährdet werden.

| Bedrohung          | Bedeutung                                       |
| ------------------ | ----------------------------------------------- |
| Schadsoftware      | Viren, Trojaner, Ransomware                     |
| Phishing           | Täuschung zur Herausgabe von Zugangsdaten       |
| Fehlkonfiguration  | falsche Rechte, offene Ports, unsichere Dienste |
| Hardwareausfall    | defekte Festplatten, Netzteile oder Switches    |
| Stromausfall       | Systeme werden unerwartet abgeschaltet          |
| Datenverlust       | Dateien werden gelöscht oder beschädigt         |
| unbefugter Zugriff | Benutzer oder Angreifer erhalten falsche Rechte |
| Netzwerkangriffe   | Scans, Spoofing, Man-in-the-Middle, DoS         |
| menschliche Fehler | falsches Löschen, falsche Änderung              |
| Naturereignisse    | Feuer, Wasser, Hitze, Sturm                     |

Viele Sicherheitsprobleme entstehen nicht durch hochkomplexe Angriffe, sondern durch schlechte Passwörter, fehlende Updates, falsche Rechte oder fehlende Backups.

---

## Netzwerksicherheit

Netzwerksicherheit umfasst alle Maßnahmen, die Kommunikation und Zugriff im Netzwerk schützen.

Dazu gehören:

- Firewall-Regeln
- Netzwerksegmentierung
- VLANs
- sichere WLAN-Konfiguration
- VPN
- Zugriffskontrolle
- Monitoring
- Protokollierung
- sichere Managementzugänge
- Abschaltung unnötiger Dienste
- Patchmanagement
- Schutz vor unbekannten Geräten

Ziel ist, dass nur erlaubte Geräte, Benutzer und Dienste miteinander kommunizieren können.

---

## Netzwerksegmentierung

Netzwerksegmentierung bedeutet, ein Netzwerk in getrennte Bereiche aufzuteilen.

Das kann physisch oder logisch erfolgen.

In modernen Netzwerken wird häufig VLAN-Technik genutzt.

Typische Segmente:

| Segment        | Zweck                                          |
| -------------- | ---------------------------------------------- |
| Clientnetz     | normale Arbeitsplatzrechner                    |
| Servernetz     | zentrale Serverdienste                         |
| Gastnetz       | Internetzugang für Besucher                    |
| Managementnetz | Verwaltung von Switches, Firewalls und Servern |
| VoIP-Netz      | IP-Telefone                                    |
| WLAN-Netz      | drahtlose Clients                              |
| DMZ            | öffentlich erreichbare Dienste                 |

Segmentierung erhöht die Sicherheit, weil nicht alle Geräte frei miteinander kommunizieren können.

Wenn ein Client kompromittiert wird, soll der Schaden nicht automatisch das gesamte Netzwerk betreffen.

---

## VLANs als Sicherheitsmaßnahme

VLANs trennen ein physisches Netzwerk logisch in mehrere Netzbereiche.

Vorteile:

- Trennung von Abteilungen oder Gerätetypen
- getrenntes Gastnetz
- besser kontrollierbare Firewall-Regeln
- kleinere Broadcast-Bereiche
- klarere Struktur
- bessere Dokumentation
- geringeres Risiko bei kompromittierten Geräten

Wichtig ist: VLANs allein sind noch keine vollständige Sicherheit.

Zwischen VLANs müssen Router oder Firewalls den Datenverkehr kontrollieren. Wenn alle VLANs ohne Regeln miteinander kommunizieren dürfen, ist der Sicherheitsgewinn gering.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr anhand von Regeln.

Sie kann Verbindungen erlauben oder blockieren.

Firewall-Regeln können sich beziehen auf:

- Quell-IP-Adresse
- Ziel-IP-Adresse
- Port
- Protokoll
- Richtung
- Benutzer
- Anwendung
- Zone
- Zeit
- Sicherheitsstatus

Eine gute Firewall-Konfiguration folgt dem Prinzip:

> Alles blockieren, was nicht ausdrücklich erlaubt ist.

In der Praxis muss dabei aber darauf geachtet werden, dass notwendige Dienste weiterhin funktionieren.

---

## DMZ

DMZ bedeutet **Demilitarized Zone**.

Eine DMZ ist ein getrenntes Netzwerksegment für Systeme, die von außen erreichbar sein müssen.

Typische Systeme in einer DMZ:

- Webserver
- Reverse Proxy
- Mail-Gateway
- VPN-Gateway
- öffentliche Dienste

Der Zweck einer DMZ ist, das interne Netzwerk zu schützen.

Wenn ein öffentlich erreichbarer Server angegriffen wird, soll der Angreifer nicht direkt Zugriff auf interne Server, Clients oder Dateiablagen bekommen.

---

## Zugriffskontrolle

Zugriffskontrolle legt fest, wer auf welche Systeme, Daten und Dienste zugreifen darf.

Wichtige Bestandteile:

- Benutzerkonten
- Gruppen
- Rollen
- Berechtigungen
- Authentifizierung
- Autorisierung
- Protokollierung
- regelmäßige Rechteprüfung

Authentifizierung beantwortet die Frage:

> Wer bist du?

Autorisierung beantwortet die Frage:

> Was darfst du?

Beide Punkte sind wichtig. Ein Benutzer kann korrekt angemeldet sein, darf aber trotzdem nicht automatisch auf alle Daten zugreifen.

---

## Prinzip der minimalen Rechte

Das Prinzip der minimalen Rechte bedeutet, dass Benutzer und Systeme nur die Rechte erhalten, die sie wirklich benötigen.

Vorteile:

- geringeres Schadenspotenzial
- bessere Kontrolle
- weniger Fehlbedienung
- bessere Nachvollziehbarkeit
- geringeres Risiko bei kompromittierten Konten

Beispiel:

Ein normaler Benutzer braucht meistens keine lokalen Administratorrechte. Wenn Schadsoftware unter einem Benutzerkonto ohne Adminrechte läuft, kann sie oft weniger Schaden anrichten.

---

## Sichere Passwörter und MFA

Passwörter sind ein wichtiger Schutzmechanismus, aber allein oft nicht ausreichend.

Wichtige Passwortregeln:

- ausreichend lang
- nicht leicht erratbar
- nicht mehrfach verwenden
- nicht mit anderen teilen
- nicht in Klartext speichern
- bei Verdacht ändern
- Passwortmanager nutzen, wenn möglich

MFA bedeutet **Multi-Faktor-Authentifizierung**.

Dabei wird zusätzlich zum Passwort ein weiterer Faktor genutzt, zum Beispiel:

- App-Bestätigung
- Sicherheitsschlüssel
- Einmalcode
- biometrischer Faktor

MFA erhöht die Sicherheit deutlich, besonders bei Cloud-Diensten, VPN und administrativen Konten.

---

## Verschlüsselung

Verschlüsselung schützt Daten vor unbefugtem Lesen.

Man unterscheidet grob:

| Art                             | Bedeutung                                    |
| ------------------------------- | -------------------------------------------- |
| Verschlüsselung bei Übertragung | schützt Daten auf dem Weg durch das Netzwerk |
| Verschlüsselung bei Speicherung | schützt Daten auf Datenträgern               |

Beispiele für verschlüsselte Übertragung:

- HTTPS
- SSH
- VPN
- WPA2/WPA3
- TLS

Beispiele für verschlüsselte Speicherung:

- Festplattenverschlüsselung
- verschlüsselte Backups
- verschlüsselte Container
- Datenbankverschlüsselung

Verschlüsselung ist besonders wichtig bei mobilen Geräten, Cloud-Diensten, personenbezogenen Daten und administrativen Verbindungen.

---

## WLAN-Sicherheit

WLAN muss besonders geschützt werden, weil Funkwellen nicht an der Gebäudewand enden.

Wichtige Maßnahmen:

- WPA2 oder WPA3 verwenden
- starke WLAN-Schlüssel
- Gastnetz getrennt vom internen Netz
- WPS deaktivieren, wenn nicht benötigt
- regelmäßige Firmwareupdates
- Access Points sicher verwalten
- SSIDs sinnvoll trennen
- VLAN-Zuordnung nutzen
- unbekannte Geräte überwachen
- zentrale Authentifizierung bei größeren Umgebungen

Veraltete oder schwache WLAN-Verschlüsselung ist ein großes Risiko.

Ein Gäste-WLAN sollte niemals direkten Zugriff auf interne Server oder Arbeitsplatzsysteme haben.

---

## VPN-Sicherheit

VPN ermöglicht verschlüsselten Zugriff auf interne Ressourcen über unsichere Netze, meistens über das Internet.

Wichtige Sicherheitsmaßnahmen:

- starke Authentifizierung
- MFA
- aktuelle VPN-Software
- Zugriff nur auf notwendige Systeme
- Protokollierung
- Gerätestatus prüfen
- keine geteilten Benutzerkonten
- klare Rechtevergabe
- regelmäßige Prüfung alter Zugänge

VPN ist praktisch für Homeoffice und Fernwartung, kann aber gefährlich sein, wenn zu breite Zugriffe erlaubt werden.

Ein VPN-Zugang sollte nicht automatisch Zugriff auf das gesamte Unternehmensnetz bedeuten.

---

## Endpoint-Sicherheit

Endpoints sind Endgeräte wie PCs, Laptops, Smartphones oder Tablets.

Diese Geräte sind besonders wichtig, weil Benutzer täglich damit arbeiten und dadurch viele Risiken entstehen.

Maßnahmen für Endpoint-Sicherheit:

- aktuelle Updates
- Sicherheitssoftware
- lokale Firewall
- Festplattenverschlüsselung
- Standardbenutzer statt Adminrechte
- sichere Browser
- Schutz vor Phishing
- USB-Kontrolle
- zentrale Verwaltung
- Monitoring
- automatische Bildschirmsperre

Ein unsicherer Client kann ein Einstiegspunkt in das gesamte Netzwerk sein.

---

## Patchmanagement

Patchmanagement bedeutet, Updates geplant zu verwalten und einzuspielen.

Updates können betreffen:

- Betriebssysteme
- Anwendungen
- Browser
- Treiber
- Firmware
- Firewalls
- Switches
- Access Points
- Serverdienste
- Sicherheitssoftware

Patchmanagement ist wichtig, weil viele Angriffe bekannte Sicherheitslücken ausnutzen.

In Unternehmen müssen Updates aber kontrolliert erfolgen, damit wichtige Systeme nicht durch fehlerhafte Updates gestört werden.

---

## Monitoring und Logging

Monitoring bedeutet, Systeme und Dienste zu überwachen.

Logging bedeutet, Ereignisse zu protokollieren.

Überwacht und protokolliert werden können:

- Anmeldungen
- fehlgeschlagene Anmeldeversuche
- Firewall-Verbindungen
- VPN-Zugriffe
- Systemfehler
- Dienstabstürze
- Speicherplatz
- CPU- und RAM-Auslastung
- Netzwerkauslastung
- Sicherheitsereignisse
- Änderungen an Konfigurationen

Logs sind wichtig für Fehleranalyse, Sicherheitsprüfung und Nachvollziehbarkeit.

Ohne Logs ist es oft schwer zu verstehen, was passiert ist.

---

## Backup

Ein Backup ist eine Sicherung von Daten oder Systemen.

Backups schützen vor Datenverlust.

Ursachen für Datenverlust können sein:

- versehentliches Löschen
- Hardwaredefekt
- Ransomware
- Softwarefehler
- Fehlkonfiguration
- Diebstahl
- Brand oder Wasserschaden
- beschädigte Updates
- menschliche Fehler

Ein Backup ist nur dann sinnvoll, wenn es wiederhergestellt werden kann.

Deshalb müssen Backups regelmäßig geprüft werden.

---

## Backupstrategie

Eine Backupstrategie beschreibt, welche Daten wie oft, wohin und wie lange gesichert werden.

Wichtige Fragen:

- Welche Daten müssen gesichert werden?
- Wie oft wird gesichert?
- Wo werden Backups gespeichert?
- Wie lange werden Backups aufbewahrt?
- Wer ist verantwortlich?
- Sind Backups verschlüsselt?
- Sind Backups vor Ransomware geschützt?
- Wie schnell muss wiederhergestellt werden?
- Wurde die Wiederherstellung getestet?

Backups sollten nicht zufällig entstehen, sondern geplant und dokumentiert sein.

---

## 3-2-1-Regel

Eine bekannte Backup-Regel ist die 3-2-1-Regel.

Sie bedeutet:

| Regel           | Bedeutung                                                        |
| --------------- | ---------------------------------------------------------------- |
| 3 Kopien        | Originaldaten plus mindestens zwei Sicherungen                   |
| 2 Medien        | Sicherungen auf mindestens zwei unterschiedlichen Speichermedien |
| 1 externe Kopie | mindestens eine Kopie außerhalb des Hauptstandorts               |

Diese Regel schützt besser vor Hardwareausfall, Ransomware, Diebstahl oder Standortschäden.

In modernen Umgebungen kann die externe Kopie auch in einem anderen Rechenzentrum oder Cloud-Speicher liegen, wenn Datenschutz und Sicherheit beachtet werden.

---

## Backuparten

Es gibt verschiedene Arten von Backups.

| Backupart              | Erklärung                                |
| ---------------------- | ---------------------------------------- |
| Vollbackup             | alle ausgewählten Daten werden gesichert |
| inkrementelles Backup  | nur Änderungen seit dem letzten Backup   |
| differenzielles Backup | Änderungen seit dem letzten Vollbackup   |
| Image-Backup           | komplettes Systemabbild                  |
| Datei-Backup           | einzelne Dateien oder Ordner             |
| Snapshot               | Zustand eines Systems zu einem Zeitpunkt |

Jede Methode hat Vor- und Nachteile bei Speicherbedarf, Geschwindigkeit und Wiederherstellung.

---

## Restore

Restore bedeutet Wiederherstellung aus einem Backup.

Ein Backup ist nur dann wertvoll, wenn ein Restore funktioniert.

Wichtige Punkte:

- Wiederherstellung regelmäßig testen
- Wiederherstellungszeit kennen
- Verantwortlichkeiten klären
- Notfallzugang sicherstellen
- Dokumentation aktuell halten
- benötigte Systeme kennen
- Reihenfolge der Wiederherstellung planen

Ein ungeprüftes Backup kann im Ernstfall wertlos sein.

---

## RTO und RPO

RTO und RPO sind wichtige Begriffe für Wiederherstellung und Verfügbarkeit.

| Begriff | Bedeutung                                        |
| ------- | ------------------------------------------------ |
| RTO     | maximale Zeit, bis ein System wieder laufen muss |
| RPO     | maximal akzeptabler Datenverlust in Zeit         |

RTO beantwortet:

> Wie lange darf ein System ausfallen?

RPO beantwortet:

> Wie viele Daten dürfen maximal verloren gehen?

Beispiel:

Wenn ein System ein RPO von 1 Stunde hat, dürfen maximal Daten der letzten Stunde verloren gehen.

Diese Werte beeinflussen Backupstrategie, Systemdesign und Kosten.

---

## RAID

RAID bedeutet **Redundant Array of Independent Disks**.

RAID verbindet mehrere Festplatten oder SSDs zu einem logischen Speicherverbund.

Ziele von RAID können sein:

- höhere Verfügbarkeit
- Schutz vor Ausfall einzelner Laufwerke
- bessere Leistung
- größere Speicherkapazität

Wichtig:

> RAID ist kein Backup.

RAID kann vor dem Ausfall einer Festplatte schützen, aber nicht vor versehentlichem Löschen, Ransomware, Brand, Diebstahl oder beschädigten Daten.

---

## Wichtige RAID-Level

| RAID-Level | Eigenschaften                                      |
| ---------- | -------------------------------------------------- |
| RAID 0     | hohe Leistung, keine Redundanz                     |
| RAID 1     | Spiegelung, Schutz bei Ausfall einer Platte        |
| RAID 5     | Parität, Ausfall einer Platte möglich              |
| RAID 6     | doppelte Parität, Ausfall von zwei Platten möglich |
| RAID 10    | Kombination aus Spiegelung und Striping            |

RAID 0 bietet keine Ausfallsicherheit.  
RAID 1 ist einfach und zuverlässig für kleinere Systeme.  
RAID 5 und RAID 6 werden bei mehreren Laufwerken genutzt.  
RAID 10 bietet gute Leistung und Redundanz, benötigt aber mehr Laufwerke.

Die Auswahl hängt von Leistung, Kapazität, Kosten und Verfügbarkeitsanforderungen ab.

---

## Hochverfügbarkeit und Redundanz

Redundanz bedeutet, dass wichtige Komponenten mehrfach vorhanden sind.

Ziel ist, dass ein einzelner Ausfall nicht sofort den gesamten Dienst stoppt.

Beispiele für Redundanz:

- mehrere Netzteile
- mehrere Festplatten
- mehrere Switches
- mehrere Internetleitungen
- mehrere Server
- Cluster
- Load Balancer
- USV
- redundante Glasfaserverbindungen

Hochverfügbarkeit bedeutet, Systeme so zu planen, dass sie möglichst wenig ausfallen.

Redundanz erhöht die Verfügbarkeit, ersetzt aber keine Wartung, kein Backup und keine Dokumentation.

---

## Ausfallzeiten

Ausfallzeit bedeutet, dass ein System oder Dienst nicht verfügbar ist.

Ausfallzeiten können entstehen durch:

- Hardwaredefekte
- Softwarefehler
- Stromausfall
- Netzwerkprobleme
- Wartungsarbeiten
- Fehlkonfiguration
- Sicherheitsvorfälle
- Providerprobleme
- menschliche Fehler

Ausfälle können Kosten verursachen, weil Mitarbeiter nicht arbeiten können, Kunden nicht bedient werden oder Daten nicht verfügbar sind.

Deshalb müssen kritische Dienste besonders geschützt und überwacht werden.

---

## Notfallplanung

Notfallplanung beschreibt, was bei schweren Störungen getan wird.

Wichtige Inhalte:

- wichtige Systeme
- Verantwortliche Personen
- Notfallkontakte
- Backup- und Restore-Prozesse
- Prioritäten
- Wiederherstellungsreihenfolge
- Ersatzhardware
- Kommunikationswege
- Zugangsdatenverwaltung
- Dokumentation
- Test der Notfallprozesse

Ein Notfallplan sollte nicht erst im Notfall geschrieben werden.

---

## Physische Sicherheit

Physische Sicherheit schützt Hardware und Infrastruktur vor direktem Zugriff oder Schäden.

Maßnahmen:

- abschließbarer Serverraum
- Zugangskontrolle
- Besucherregelung
- Brandschutz
- Klimatisierung
- Wasserschutz
- USV
- ordentliche Verkabelung
- Schutz vor Diebstahl
- Inventarisierung

Ein Server kann technisch sehr sicher konfiguriert sein. Wenn aber jeder physischen Zugriff darauf hat, entsteht trotzdem ein großes Risiko.

---

## Datenschutz

Datenschutz schützt personenbezogene Daten.

Personenbezogene Daten sind Informationen, die sich auf eine bestimmte Person beziehen.

Beispiele:

- Name
- Adresse
- Telefonnummer
- E-Mail-Adresse
- Personalnummer
- Kundennummer
- IP-Adresse in bestimmten Zusammenhängen
- Gesundheitsdaten
- Bewerbungsdaten

Beim Umgang mit personenbezogenen Daten müssen rechtliche Vorgaben beachtet werden.

Für FISI bedeutet das: Daten dürfen nicht unnötig kopiert, ungeschützt gespeichert oder unberechtigt weitergegeben werden.

---

## Sicherheitsdokumentation

Sicherheitsmaßnahmen müssen dokumentiert werden.

Wichtige Dokumente:

- Netzplan
- VLAN-Plan
- Firewall-Regeln
- Backupkonzept
- Rechtekonzept
- Notfallplan
- Patchmanagement-Prozess
- Inventarliste
- Zugriffsdokumentation
- Änderungsprotokoll
- Wartungsprotokoll
- Wiederherstellungsanleitungen

Dokumentation macht Sicherheitsmaßnahmen nachvollziehbar und unterstützt Betrieb, Support, Audits und Notfälle.

---

## Praxisbeispiele

### Beispiel 1: Gastnetz

Ein Unternehmen richtet ein separates Gäste-WLAN ein. Gäste erhalten Internetzugang, aber keinen Zugriff auf interne Server, Drucker oder Dateiablagen. Die Trennung erfolgt über VLANs und Firewall-Regeln.

### Beispiel 2: Ransomware-Schutz durch Backup

Ein Dateiserver wird durch Ransomware verschlüsselt. Durch getrennte, aktuelle und getestete Backups können die Daten wiederhergestellt werden. Ohne funktionierende Backups wäre der Schaden deutlich größer.

### Beispiel 3: Laptop-Verlust

Ein Firmenlaptop geht verloren. Weil Festplattenverschlüsselung, starkes Passwort und MFA aktiv sind, sind die gespeicherten Daten besser geschützt.

---

## Typische Fehler

| Fehler                                    | Problem                                     |
| ----------------------------------------- | ------------------------------------------- |
| RAID als Backup betrachten                | schützt nicht vor Löschen oder Ransomware   |
| Backups nie testen                        | Wiederherstellung kann im Notfall scheitern |
| alle Geräte im gleichen Netz betreiben    | Angriffe können sich leichter ausbreiten    |
| Benutzer mit zu vielen Rechten ausstatten | höheres Schadensrisiko                      |
| Updates aufschieben                       | bekannte Sicherheitslücken bleiben offen    |
| Gäste-WLAN nicht trennen                  | Risiko für interne Systeme                  |
| keine Logs auswerten                      | Angriffe oder Fehler bleiben unbemerkt      |
| Firewall-Regeln nicht dokumentieren       | spätere Wartung wird schwierig              |
| Notfallplan fehlt                         | Wiederherstellung dauert länger             |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Daten- und Netzwerksicherheit eine zentrale Grundlage.

Ein FISI muss Systeme nicht nur einrichten, sondern auch sicher betreiben und vor Ausfällen schützen.

In der Praxis bedeutet das:

- Netzwerke segmentieren
- Firewall-Regeln verstehen
- Benutzerrechte sinnvoll setzen
- WLAN und VPN sicher konfigurieren
- Updates und Patches beachten
- Backups planen und prüfen
- RAID richtig einordnen
- Verfügbarkeit bewerten
- Sicherheitsrisiken erkennen
- Notfallmaßnahmen dokumentieren

Ein guter FISI denkt nicht nur daran, ob ein System funktioniert, sondern auch daran, ob es sicher, verfügbar, wartbar und wiederherstellbar ist.

---

## Kurze Zusammenfassung

Daten- und Netzwerksicherheit schützt Informationen, Systeme und Netzwerkkommunikation vor unbefugtem Zugriff, Manipulation, Datenverlust und Ausfall.

Wichtige Schutzziele sind Vertraulichkeit, Integrität und Verfügbarkeit.

Zentrale Maßnahmen sind Netzwerksegmentierung, VLANs, Firewalls, sichere Passwörter, MFA, Verschlüsselung, WLAN-Sicherheit, VPN-Sicherheit, Endpoint-Schutz, Patchmanagement, Monitoring, Logging, Backups, RAID, Redundanz und Notfallplanung.

Für FISI ist dieses Wissen wichtig, weil professionelle IT-Systeme nicht nur funktionieren müssen, sondern sicher und zuverlässig betrieben werden sollen.s
