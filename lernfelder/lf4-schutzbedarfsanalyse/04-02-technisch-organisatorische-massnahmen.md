# 4.2 Technisch-organisatorische Maßnahmen

In diesem Kapitel geht es um technische und organisatorische Maßnahmen zum Schutz von Informationen, IT-Systemen und Arbeitsbereichen.

Informationssicherheit entsteht nicht durch eine einzelne Maßnahme. Eine Firewall allein reicht nicht aus, wenn Benutzer schwache Passwörter verwenden, Backups nicht getestet werden oder Zugriffsrechte falsch vergeben sind. Deshalb müssen technische, organisatorische, physische und personelle Maßnahmen zusammenwirken.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Sicherheitsmaßnahmen im Betrieb geplant, umgesetzt, geprüft und dokumentiert werden müssen.

---

## Kurz erklärt

Technisch-organisatorische Maßnahmen sind Schutzmaßnahmen, die Risiken in der IT reduzieren sollen.

Technische Maßnahmen werden direkt durch Systeme, Geräte, Software oder Konfigurationen umgesetzt.

Organisatorische Maßnahmen regeln Abläufe, Zuständigkeiten, Verhalten und Dokumentation.

Beispiele:

| Art                        | Beispiele                                                |
| -------------------------- | -------------------------------------------------------- |
| technische Maßnahmen       | Firewall, Verschlüsselung, Backup, MFA, Patchmanagement  |
| organisatorische Maßnahmen | Richtlinien, Prozesse, Schulungen, Berechtigungskonzepte |
| physische Maßnahmen        | Zugangskontrolle, Serverraum abschließen, Brandschutz    |
| personelle Maßnahmen       | Sensibilisierung, Rollen, Verantwortlichkeiten           |

Gute Sicherheit entsteht erst, wenn diese Maßnahmen zusammenpassen.

---

## Ziel von Schutzmaßnahmen

Schutzmaßnahmen sollen verhindern, dass Sicherheitsvorfälle entstehen oder große Schäden verursachen.

Wichtige Ziele sind:

- unbefugten Zugriff verhindern
- Datenverlust vermeiden
- Manipulation erkennen oder verhindern
- Systeme verfügbar halten
- Sicherheitsvorfälle früh erkennen
- Schaden begrenzen
- Wiederherstellung ermöglichen
- Verantwortlichkeiten klären
- gesetzliche und interne Vorgaben erfüllen
- Nachvollziehbarkeit schaffen

Eine Maßnahme ist nur sinnvoll, wenn sie zu einem Risiko passt.

---

## Technische Maßnahmen

Technische Maßnahmen werden mit Hardware, Software oder Konfiguration umgesetzt.

Typische technische Maßnahmen sind:

- Firewall
- Virenschutz oder Endpoint-Schutz
- Verschlüsselung
- Multi-Faktor-Authentifizierung
- Backup
- Netzwerksegmentierung
- VLANs
- VPN
- Patchmanagement
- Monitoring
- Logging
- Zugriffskontrolle
- sichere WLAN-Konfiguration
- Festplattenverschlüsselung
- automatische Bildschirmsperre
- sichere Remote-Zugänge

Technische Maßnahmen können viele Angriffe erschweren, ersetzen aber keine klaren Regeln und keine geschulten Benutzer.

---

## Organisatorische Maßnahmen

Organisatorische Maßnahmen regeln, wie Sicherheit im Unternehmen umgesetzt wird.

Typische organisatorische Maßnahmen sind:

- Sicherheitsrichtlinien
- Passwortregeln
- Berechtigungskonzepte
- Rollen und Verantwortlichkeiten
- Onboarding- und Offboarding-Prozesse
- Schulungen
- Meldewege für Sicherheitsvorfälle
- Backupkonzept
- Notfallplan
- Patchmanagement-Prozess
- Änderungsmanagement
- Dokumentationspflicht
- regelmäßige Rechteprüfung
- Umgang mit mobilen Geräten
- Umgang mit externen Dienstleistern

Organisatorische Maßnahmen sorgen dafür, dass Sicherheit nicht zufällig passiert, sondern geplant und nachvollziehbar umgesetzt wird.

---

## Physische Maßnahmen

Physische Maßnahmen schützen IT-Systeme und Informationen vor direktem Zugriff oder Umwelteinflüssen.

Beispiele:

- Serverraum abschließen
- Zutrittskontrolle
- Besuchermanagement
- Brandschutz
- Wasserschutz
- Klimatisierung
- USV
- sichere Aufbewahrung von Datenträgern
- abschließbare Schränke
- Schutz vor Diebstahl
- Ordnung im Netzwerkschrank
- sichere Entsorgung von Hardware

Physische Sicherheit wird oft unterschätzt.

Ein Server kann technisch gut abgesichert sein. Wenn aber jeder den Serverraum betreten oder Datenträger mitnehmen kann, bleibt ein großes Risiko.

---

## Personelle Maßnahmen

Personelle Maßnahmen betreffen Benutzer, Administratoren, Mitarbeitende und externe Dienstleister.

Beispiele:

- Schulungen
- Sicherheitsunterweisungen
- klare Rollen
- klare Zuständigkeiten
- Verpflichtung auf Vertraulichkeit
- Sensibilisierung gegen Phishing
- Vier-Augen-Prinzip bei kritischen Änderungen
- regelmäßige Rechteprüfung
- sichere Übergabe von Zugangsdaten
- geregeltes Offboarding
- keine geteilten Benutzerkonten

Viele Sicherheitsvorfälle entstehen nicht durch Technik, sondern durch menschliche Fehler oder Manipulation.

Deshalb müssen Benutzer wissen, wie sie sicher mit IT-Systemen umgehen.

---

## Zusammenspiel der Maßnahmen

Ein gutes Sicherheitskonzept kombiniert mehrere Maßnahmen.

Beispiel: Schutz eines Firmenlaptops

| Risiko              | passende Maßnahmen                |
| ------------------- | --------------------------------- |
| Verlust des Geräts  | Festplattenverschlüsselung        |
| unbefugte Anmeldung | starkes Passwort und MFA          |
| Schadsoftware       | Endpoint-Schutz und Updates       |
| Datenverlust        | Backup oder Cloud-Synchronisation |
| unsicheres WLAN     | VPN und sichere WLAN-Regeln       |
| falsche Nutzung     | Schulung und Richtlinien          |
| fehlende Verwaltung | MDM oder zentrale Verwaltung      |

Keine einzelne Maßnahme schützt vollständig. Sicherheit entsteht durch mehrere Schutzschichten.

---

## Defense in Depth

Defense in Depth bedeutet Sicherheit in mehreren Schichten.

Die Grundidee ist:

> Wenn eine Schutzmaßnahme versagt, sollen weitere Maßnahmen den Schaden verhindern oder begrenzen.

Beispiel:

Ein Benutzer klickt auf eine Phishing-Mail.

Mögliche Schutzschichten:

- E-Mail-Filter blockiert viele schädliche Nachrichten
- Benutzer erkennt verdächtige Merkmale
- MFA verhindert Kontoübernahme
- Benutzer hat keine Administratorrechte
- Endpoint-Schutz erkennt Schadsoftware
- Netzwerksegmentierung begrenzt Zugriff
- Backups ermöglichen Wiederherstellung
- Monitoring erkennt ungewöhnliches Verhalten

Sicherheit sollte nicht von einer einzigen Maßnahme abhängig sein.

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
- regelmäßige Prüfung

Ein Benutzer soll nur Zugriff auf die Informationen haben, die er für seine Arbeit benötigt.

Das reduziert Risiken und macht Zugriffe besser nachvollziehbar.

---

## Prinzip der minimalen Rechte

Das Prinzip der minimalen Rechte bedeutet:

> Benutzer, Dienste und Systeme erhalten nur die Rechte, die sie wirklich brauchen.

Beispiele:

- normale Benutzer erhalten keine lokalen Administratorrechte
- Praktikanten erhalten nur Zugriff auf notwendige Systeme
- Dienstkonten erhalten keine unnötigen Rechte
- Gäste bekommen nur Internetzugang
- externe Dienstleister erhalten zeitlich begrenzten Zugriff
- Administratorrechte werden getrennt von normalen Benutzerkonten genutzt

Dieses Prinzip verringert das Schadenspotenzial bei Fehlern, Missbrauch oder kompromittierten Konten.

---

## Rollen- und Berechtigungskonzept

Ein Berechtigungskonzept beschreibt, welche Rollen welche Zugriffe erhalten.

Beispiel:

| Rolle             | Zugriff                                              |
| ----------------- | ---------------------------------------------------- |
| normaler Benutzer | eigene Dateien, Abteilungslaufwerk, Standardsoftware |
| Buchhaltung       | Buchhaltungsdaten und Finanzsoftware                 |
| Personalabteilung | Personaldaten                                        |
| IT-Support        | Supportwerkzeuge und Geräteverwaltung                |
| Administrator     | administrative Systeme                               |
| Gast              | nur Internetzugang                                   |

Berechtigungen sollten möglichst über Gruppen vergeben werden, nicht einzeln pro Benutzer.

Das erleichtert Verwaltung, Kontrolle und Dokumentation.

---

## Passwortregeln

Passwörter schützen Benutzerkonten und Systeme.

Wichtige Regeln:

- ausreichend lange Passwörter
- keine einfachen Begriffe
- keine Wiederverwendung wichtiger Passwörter
- keine Weitergabe an andere Personen
- keine Speicherung in Klartext
- Passwortmanager nutzen, wenn möglich
- Standardpasswörter ändern
- bei Verdacht Passwort wechseln

Passwortregeln sollten sicher, aber auch praktikabel sein.

Zu komplizierte Regeln können dazu führen, dass Benutzer Passwörter unsicher notieren.

---

## Multi-Faktor-Authentifizierung

Multi-Faktor-Authentifizierung bedeutet, dass zusätzlich zum Passwort ein weiterer Faktor benötigt wird.

Beispiele für Faktoren:

- Passwort
- Authenticator-App
- Sicherheitsschlüssel
- Einmalcode
- biometrischer Faktor
- Smartcard

MFA ist besonders wichtig bei:

- Administratorzugängen
- VPN
- Cloud-Diensten
- E-Mail-Konten
- Remote-Zugängen
- Zugriff von außerhalb des Unternehmens

MFA reduziert das Risiko, dass ein gestohlenes Passwort allein für einen erfolgreichen Angriff reicht.

---

## Verschlüsselung

Verschlüsselung schützt Daten vor unbefugtem Lesen.

Man unterscheidet:

| Art                             | Bedeutung                      |
| ------------------------------- | ------------------------------ |
| Verschlüsselung bei Speicherung | schützt Daten auf Datenträgern |
| Verschlüsselung bei Übertragung | schützt Daten im Netzwerk      |

Beispiele:

- Festplattenverschlüsselung auf Laptops
- verschlüsselte Backups
- HTTPS für Webseiten
- SSH für Administration
- VPN für externe Verbindungen
- WPA2 oder WPA3 im WLAN

Verschlüsselung ist besonders wichtig bei mobilen Geräten, personenbezogenen Daten, Cloud-Diensten und administrativen Verbindungen.

---

## Backup als Maßnahme

Backups schützen vor Datenverlust.

Sie helfen bei:

- versehentlichem Löschen
- Hardwaredefekt
- Ransomware
- Softwarefehlern
- beschädigten Daten
- Fehlkonfiguration
- Diebstahl
- Brand oder Wasserschaden

Ein Backup ist aber nur dann wertvoll, wenn es wiederhergestellt werden kann.

Deshalb müssen Backups regelmäßig getestet und dokumentiert werden.

---

## Backupkonzept

Ein Backupkonzept beschreibt, wie Sicherungen durchgeführt werden.

Wichtige Fragen:

- Welche Daten werden gesichert?
- Wie oft wird gesichert?
- Wo werden Backups gespeichert?
- Wie lange werden Backups aufbewahrt?
- Wer ist verantwortlich?
- Sind Backups verschlüsselt?
- Sind Backups vor Ransomware geschützt?
- Wie schnell muss wiederhergestellt werden?
- Wurde die Wiederherstellung getestet?

Ein Backupkonzept gehört zu den wichtigsten organisatorischen und technischen Maßnahmen.

---

## Patchmanagement

Patchmanagement bedeutet, Updates geplant und kontrolliert einzuspielen.

Betroffen sein können:

- Betriebssysteme
- Anwendungen
- Browser
- Serverdienste
- Netzwerkgeräte
- Firewalls
- Access Points
- Firmware
- Sicherheitssoftware

Patchmanagement reduziert bekannte Sicherheitslücken.

In Unternehmen müssen Updates aber kontrolliert erfolgen, damit wichtige Systeme nicht durch fehlerhafte Updates gestört werden.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr anhand von Regeln.

Sie kann Verkehr erlauben oder blockieren.

Typische Kriterien:

- Quelle
- Ziel
- Port
- Protokoll
- Richtung
- Benutzer
- Anwendung
- Zone
- Zeit

Firewall-Regeln sollten klar, notwendig und dokumentiert sein.

Eine gute Regel hat einen Zweck. Alte oder unnötige Regeln sollten regelmäßig geprüft werden.

---

## Netzwerksegmentierung

Netzwerksegmentierung bedeutet, ein Netzwerk in getrennte Bereiche aufzuteilen.

Typische Bereiche:

- Clientnetz
- Servernetz
- Gastnetz
- Managementnetz
- VoIP-Netz
- WLAN-Netz
- DMZ
- VPN-Bereich

Segmentierung begrenzt Schäden.

Wenn ein Gerät kompromittiert wird, soll es nicht automatisch Zugriff auf alle Systeme im Unternehmen haben.

---

## VLANs

VLANs trennen ein physisches Netzwerk logisch in mehrere Netzbereiche.

Vorteile:

- bessere Struktur
- getrennte Sicherheitsbereiche
- kleinere Broadcast-Bereiche
- getrenntes Gastnetz
- gezieltere Firewall-Regeln
- bessere Dokumentation
- einfachere Verwaltung großer Netze

Wichtig:

VLANs allein sind keine vollständige Sicherheit. Zwischen VLANs müssen Regeln existieren, meistens auf Router oder Firewall.

---

## VPN

VPN ermöglicht verschlüsselte Verbindungen über unsichere Netze, zum Beispiel über das Internet.

Typische Einsatzbereiche:

- Homeoffice
- Außendienst
- Fernwartung
- Standortvernetzung
- externe Dienstleister

Sicherheitsmaßnahmen bei VPN:

- MFA
- aktuelle VPN-Software
- Zugriff nur auf notwendige Systeme
- Protokollierung
- klare Benutzerrechte
- keine geteilten Konten
- regelmäßige Prüfung alter Zugänge

VPN darf nicht bedeuten, dass ein Benutzer automatisch Zugriff auf das ganze interne Netzwerk erhält.

---

## Endpoint-Schutz

Endpoint-Schutz betrifft Clients und mobile Geräte.

Dazu gehören:

- Virenschutz
- Endpoint Detection
- lokale Firewall
- Festplattenverschlüsselung
- Updates
- keine unnötigen Adminrechte
- sichere Browserkonfiguration
- USB-Kontrolle
- automatische Bildschirmsperre
- zentrale Verwaltung
- Monitoring

Clients sind häufige Angriffspunkte, weil Benutzer täglich mit E-Mails, Webseiten, Dateien und externen Geräten arbeiten.

---

## Monitoring

Monitoring bedeutet, Systeme und Dienste zu überwachen.

Überwacht werden können:

- Server
- Clients
- Switches
- Router
- Firewalls
- Access Points
- Internetverbindung
- CPU-Auslastung
- RAM-Auslastung
- Speicherplatz
- Netzwerkverkehr
- Backupstatus
- Zertifikate
- Dienste
- Sicherheitsereignisse

Monitoring hilft, Probleme früh zu erkennen.

Dadurch können Störungen manchmal behoben werden, bevor Benutzer sie bemerken.

---

## Logging

Logging bedeutet, Ereignisse zu protokollieren.

Wichtige Logs:

- Anmeldungen
- fehlgeschlagene Anmeldeversuche
- Firewall-Verbindungen
- VPN-Zugriffe
- Systemfehler
- Änderungen an Konfigurationen
- Sicherheitsmeldungen
- Backupfehler
- Dienstabstürze
- Netzwerkereignisse

Logs sind wichtig für Fehlersuche, Sicherheitsanalyse und Nachvollziehbarkeit.

Ohne Logs ist oft schwer zu erkennen, was passiert ist.

---

## Sicherheitsrichtlinien

Sicherheitsrichtlinien beschreiben Regeln für den sicheren Umgang mit IT.

Beispiele:

- Passwort-Richtlinie
- Backup-Richtlinie
- Homeoffice-Richtlinie
- Mobile-Device-Richtlinie
- Clean-Desk-Policy
- E-Mail-Richtlinie
- Patchmanagement-Richtlinie
- Berechtigungskonzept
- Notfallrichtlinie
- Richtlinie für externe Dienstleister

Richtlinien müssen verständlich und realistisch sein.

Eine Richtlinie ist nur hilfreich, wenn Benutzer sie kennen und im Alltag anwenden können.

---

## Schulung und Sensibilisierung

Benutzer müssen über wichtige Sicherheitsrisiken informiert werden.

Themen für Schulungen:

- Phishing erkennen
- sichere Passwörter
- MFA richtig nutzen
- verdächtige Vorfälle melden
- keine Passwörter weitergeben
- sichere Nutzung von E-Mail
- Umgang mit Anhängen
- Umgang mit USB-Geräten
- Datenschutz
- sichere Arbeit im Homeoffice
- Clean Desk
- Meldewege bei Problemen

Schulung ist wichtig, weil Menschen oft gezielt angegriffen werden.

Technik kann viel schützen, aber Benutzerverhalten bleibt ein wichtiger Faktor.

---

## Onboarding

Onboarding beschreibt den Eintritt neuer Mitarbeitender.

Sicherheitsrelevante Punkte:

- Benutzerkonto anlegen
- passende Gruppen zuweisen
- nur notwendige Rechte vergeben
- Geräte ausgeben
- Sicherheitsrichtlinien erklären
- MFA einrichten
- Datenschutz und Vertraulichkeit erklären
- Software bereitstellen
- Zugriffe dokumentieren

Ein sauberer Onboarding-Prozess verhindert falsche Rechte und erleichtert den Start.

---

## Offboarding

Offboarding beschreibt den Austritt von Mitarbeitenden.

Sicherheitsrelevante Punkte:

- Benutzerkonto deaktivieren
- Zugriffe entfernen
- Geräte zurücknehmen
- Schlüssel und Karten zurückgeben
- Weiterleitungen prüfen
- Datenübergabe regeln
- Cloud-Zugänge entfernen
- VPN-Zugänge entfernen
- externe Konten prüfen
- Berechtigungen dokumentieren

Offboarding ist sehr wichtig.

Alte aktive Benutzerkonten sind ein Sicherheitsrisiko, besonders wenn sie noch Zugriff auf E-Mail, Cloud, VPN oder interne Systeme haben.

---

## Change Management

Change Management bedeutet, Änderungen geplant und kontrolliert durchzuführen.

Wichtige Schritte:

1. Änderung beschreiben
2. Grund der Änderung erklären
3. Risiko bewerten
4. Auswirkungen prüfen
5. Freigabe einholen
6. Backup erstellen
7. Wartungsfenster planen
8. Änderung durchführen
9. Funktion testen
10. Ergebnis dokumentieren
11. Rückfallplan bereithalten

Gerade bei Netzwerken, Firewalls, Servern und Berechtigungen können kleine Änderungen große Auswirkungen haben.

---

## Notfallplanung

Notfallplanung beschreibt, was bei schweren Störungen getan wird.

Wichtige Inhalte:

- wichtige Systeme
- Verantwortliche Personen
- Notfallkontakte
- Wiederherstellungsreihenfolge
- Backup- und Restore-Prozesse
- Kommunikationswege
- Ersatzhardware
- Zugangsdatenverwaltung
- Dokumentation
- Test der Notfallprozesse

Ein Notfallplan sollte vorbereitet sein, bevor ein Notfall passiert.

Im Ernstfall ist keine Zeit, grundlegende Abläufe erst zu entwickeln.

---

## Maßnahmen dokumentieren

Schutzmaßnahmen müssen dokumentiert werden.

Wichtige Dokumente:

- Netzplan
- Rechtekonzept
- Backupkonzept
- Firewall-Regeln
- VLAN-Plan
- Patchmanagement-Prozess
- Notfallplan
- Asset-Inventar
- Sicherheitsrichtlinien
- Schulungsnachweise
- Änderungsprotokolle
- Wartungsprotokolle
- Sicherheitsvorfälle

Dokumentation macht Maßnahmen nachvollziehbar.

Ohne Dokumentation ist schwer zu prüfen, ob Sicherheit wirklich umgesetzt wurde.

---

## Wirksamkeit prüfen

Maßnahmen müssen regelmäßig geprüft werden.

Wichtige Fragen:

- Funktionieren Backups?
- Sind Rechte noch korrekt?
- Sind Updates aktuell?
- Sind Firewall-Regeln noch notwendig?
- Sind alte Konten deaktiviert?
- Sind Logs vorhanden?
- Werden Sicherheitsvorfälle erkannt?
- Sind Benutzer geschult?
- Ist die Dokumentation aktuell?
- Funktioniert der Notfallplan?

Eine Maßnahme, die nie geprüft wird, kann im Ernstfall versagen.

---

## Praxisbeispiele

### Beispiel 1: Schutz eines Dateiservers

Ein Dateiserver wird durch Berechtigungen, Gruppen, Backups, Monitoring, Updates und Protokollierung geschützt. Zusätzlich wird dokumentiert, wer Zugriff auf welche Freigaben hat.

### Beispiel 2: Schutz eines Homeoffice-Laptops

Ein Laptop wird mit Festplattenverschlüsselung, MFA, VPN, Endpoint-Schutz, Updates und zentraler Verwaltung abgesichert. Benutzer erhalten zusätzlich eine kurze Sicherheitsunterweisung.

### Beispiel 3: Schutz eines Gäste-WLANs

Das Gäste-WLAN wird in ein eigenes VLAN gelegt. Über Firewall-Regeln ist nur Internetzugang erlaubt. Zugriff auf interne Server, Drucker oder Clients wird blockiert.

---

## Typische Fehler

| Fehler                                     | Problem                                             |
| ------------------------------------------ | --------------------------------------------------- |
| nur technische Maßnahmen einsetzen         | Organisation und Benutzerverhalten werden vergessen |
| Richtlinien schreiben, aber nicht erklären | Benutzer kennen die Regeln nicht                    |
| Backups erstellen, aber nie testen         | Wiederherstellung kann scheitern                    |
| Rechte nicht regelmäßig prüfen             | Benutzer behalten unnötige Zugriffe                 |
| alte Konten aktiv lassen                   | Risiko für unbefugten Zugriff                       |
| Firewall-Regeln nicht dokumentieren        | spätere Wartung wird schwierig                      |
| keine MFA bei kritischen Zugängen          | gestohlene Passwörter reichen für Angriffe          |
| Updates ohne Planung ignorieren            | bekannte Sicherheitslücken bleiben offen            |
| Änderungen ohne Rückfallplan durchführen   | Störungen lassen sich schwer beheben                |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind technisch-organisatorische Maßnahmen ein wichtiger Teil der täglichen Arbeit.

Ein FISI muss technische Schutzmaßnahmen verstehen und gleichzeitig organisatorische Vorgaben beachten.

In der Praxis bedeutet das:

- Firewalls und VLANs einordnen
- Benutzerrechte sauber vergeben
- Backups und Restore prüfen
- Updates planen
- Endgeräte absichern
- VPN und WLAN sicher konfigurieren
- Monitoring und Logs nutzen
- Dokumentation pflegen
- Sicherheitsrichtlinien umsetzen
- Änderungen kontrolliert durchführen

Ein guter FISI denkt nicht nur technisch, sondern auch organisatorisch.

Sicherheit funktioniert nur, wenn Systeme, Prozesse, Menschen und Dokumentation zusammenpassen.

---

## Kurze Zusammenfassung

Technisch-organisatorische Maßnahmen schützen Informationen, Systeme und Netzwerke vor Schäden.

Technische Maßnahmen sind zum Beispiel Firewall, Verschlüsselung, Backup, MFA, Patchmanagement, Monitoring und Netzwerksegmentierung.

Organisatorische Maßnahmen sind zum Beispiel Richtlinien, Prozesse, Schulungen, Berechtigungskonzepte, Notfallplanung und Dokumentation.

Für FISI ist wichtig, beide Seiten zu verstehen, weil professionelle IT-Sicherheit immer aus Technik, Organisation, Menschen und regelmäßiger Prüfung besteht.
