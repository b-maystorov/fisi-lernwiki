# 4.4 Schutzbedarf in Arbeitsbereichen analysieren

In diesem Kapitel geht es darum, den Schutzbedarf direkt in konkreten Arbeitsbereichen zu analysieren.

Ein Arbeitsbereich ist zum Beispiel ein Büroarbeitsplatz, ein Homeoffice-Arbeitsplatz, ein Empfangsbereich, ein Schulungsraum, ein Serverraum oder ein Arbeitsplatz mit besonderer Software. In jedem Bereich werden andere Daten verarbeitet, andere Geräte genutzt und andere Risiken entstehen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil IT-Sicherheit nicht nur auf Servern und Firewalls stattfindet. Auch normale Arbeitsplätze, Clients, mobile Geräte, Software, USB-Sticks, Drucker und Benutzerverhalten haben Einfluss auf die Sicherheit eines Unternehmens.

---

## Kurz erklärt

Schutzbedarf in Arbeitsbereichen bedeutet, zu prüfen, wie stark ein konkreter Arbeitsplatz oder Bereich geschützt werden muss.

Dabei wird betrachtet:

- welche Daten dort verarbeitet werden
- welche Geräte genutzt werden
- welche Software verwendet wird
- welche Benutzer Zugriff haben
- welche Netzwerkverbindungen bestehen
- welche mobilen Datenträger genutzt werden
- welche Ausdrucke oder Papierdokumente vorhanden sind
- welche Risiken durch Diebstahl, Verlust oder Fehlbedienung entstehen
- welche Schutzmaßnahmen notwendig sind

Ein Arbeitsplatz kann technisch einfach aussehen, aber trotzdem hohen Schutzbedarf haben, wenn dort sensible Daten verarbeitet werden.

---

## Fachliche Einordnung

Bei einer Schutzbedarfsanalyse im Arbeitsbereich werden nicht nur einzelne Geräte betrachtet.

Wichtig ist das Zusammenspiel aus:

| Bereich     | Beispiele                                         |
| ----------- | ------------------------------------------------- |
| Personen    | Mitarbeitende, Gäste, externe Dienstleister       |
| Geräte      | PCs, Laptops, Drucker, Smartphones, Tablets       |
| Software    | Fachanwendungen, Office, Browser, E-Mail, VPN     |
| Daten       | Kunden-, Personal-, Finanz- oder Projektdaten     |
| Netzwerk    | LAN, WLAN, VPN, Cloud-Dienste                     |
| Räume       | Büro, Empfang, Homeoffice, Serverraum             |
| Prozesse    | Anmeldung, Drucken, Speichern, Versenden, Support |
| Datenträger | USB-Sticks, externe Festplatten, Speicherkarten   |
| Dokumente   | Ausdrucke, Notizen, Verträge, Zugangsdaten        |

Der Schutzbedarf ergibt sich also aus dem gesamten Arbeitsumfeld.

---

## Warum Arbeitsbereiche analysiert werden müssen

Viele Sicherheitsvorfälle entstehen direkt im Arbeitsalltag.

Beispiele:

- ein Laptop wird verloren
- ein USB-Stick enthält unverschlüsselte Daten
- ein Benutzer öffnet einen Phishing-Anhang
- ein Ausdruck mit Kundendaten bleibt im Drucker liegen
- ein Gast sieht vertrauliche Informationen auf einem Bildschirm
- ein alter Benutzerzugang bleibt aktiv
- ein privates Gerät wird unsicher genutzt
- ein Arbeitsplatz-PC hat lokale Administratorrechte
- eine Fachanwendung enthält sensible Daten
- Daten werden in eine ungeeignete Cloud hochgeladen

Deshalb reicht es nicht, nur Server oder Netzwerkgeräte zu schützen. Auch der normale Arbeitsplatz muss betrachtet werden.

---

## Arbeitsbereich als Schutzobjekt

Ein Arbeitsbereich kann selbst als Schutzobjekt betrachtet werden.

Dabei wird bewertet, welche Daten, Geräte und Prozesse dort vorkommen.

Beispiele:

| Arbeitsbereich            | mögliche Schutzthemen                                    |
| ------------------------- | -------------------------------------------------------- |
| normaler Büroarbeitsplatz | Benutzerkonto, E-Mail, Dateiablagen, Drucker             |
| Personalabteilung         | Personaldaten, Bewerbungen, Verträge                     |
| Buchhaltung               | Finanzdaten, Rechnungen, Bankdaten                       |
| Empfang                   | Besucher, Telefon, Zugangskontrolle, öffentliche Nähe    |
| Homeoffice                | privates Umfeld, WLAN, VPN, Laptopverlust                |
| Schulungsraum             | wechselnde Benutzer, Testdaten, Zurücksetzen der Clients |
| Serverraum                | physischer Zugriff, Strom, Klima, Netzwerkgeräte         |
| IT-Administration         | Adminzugänge, Dokumentation, Passwörter, Tools           |

Je nach Bereich können Vertraulichkeit, Integrität und Verfügbarkeit unterschiedlich wichtig sein.

---

## Schutzziele im Arbeitsbereich

Auch im Arbeitsbereich gelten die drei Grundziele der Informationssicherheit.

| Schutzziel      | Fragestellung im Arbeitsbereich                           |
| --------------- | --------------------------------------------------------- |
| Vertraulichkeit | Können unberechtigte Personen Daten sehen oder kopieren?  |
| Integrität      | Können Daten oder Einstellungen falsch verändert werden?  |
| Verfügbarkeit   | Kann der Arbeitsplatz seine Aufgabe zuverlässig erfüllen? |

Beispiel:

Ein Arbeitsplatz in der Personalabteilung hat oft hohen Schutzbedarf bei Vertraulichkeit, weil dort Personaldaten verarbeitet werden.

Ein Arbeitsplatz in der Produktion kann hohen Schutzbedarf bei Verfügbarkeit haben, wenn ein Ausfall den Betrieb stoppt.

Ein IT-Administrationsplatz hat hohen Schutzbedarf bei Integrität und Vertraulichkeit, weil dort Systeme verändert und Zugangsdaten genutzt werden können.

---

## Arbeitsplatzsoftware

Arbeitsplatzsoftware ist Software, die direkt auf Clients oder über Webanwendungen genutzt wird.

Beispiele:

- Betriebssystem
- Office-Programme
- E-Mail-Client
- Browser
- Fachanwendungen
- ERP-Systeme
- CRM-Systeme
- Buchhaltungssoftware
- Personalsoftware
- VPN-Client
- Remote-Desktop-Client
- Entwicklungswerkzeuge
- Sicherheitssoftware

Software kann selbst schutzbedürftig sein, besonders wenn sie sensible Daten verarbeitet oder wichtige Geschäftsprozesse unterstützt.

---

## Schutzbedarf von Arbeitsplatzsoftware

Bei Arbeitsplatzsoftware muss geprüft werden, welche Bedeutung sie für den Arbeitsbereich hat.

Wichtige Fragen:

- Welche Daten werden mit der Software verarbeitet?
- Sind personenbezogene Daten betroffen?
- Sind Kundendaten oder Finanzdaten betroffen?
- Ist die Software für den täglichen Betrieb notwendig?
- Gibt es Ersatzprozesse bei Ausfall?
- Können falsche Eingaben großen Schaden verursachen?
- Werden Daten lokal gespeichert?
- Werden Daten in der Cloud gespeichert?
- Gibt es Schnittstellen zu anderen Systemen?
- Wer darf die Software nutzen?
- Wie werden Updates eingespielt?

Eine einfache Software kann hohen Schutzbedarf haben, wenn sie kritische Daten verarbeitet.

---

## Risiken bei Arbeitsplatzsoftware

Typische Risiken sind:

| Risiko                   | Beispiel                                         |
| ------------------------ | ------------------------------------------------ |
| veraltete Software       | bekannte Sicherheitslücken bleiben offen         |
| falsche Berechtigungen   | Benutzer sehen Daten, die sie nicht sehen dürfen |
| lokale Datenspeicherung  | Daten bleiben ungeschützt auf dem Client         |
| fehlende Updates         | Schadsoftware nutzt Schwachstellen aus           |
| unsichere Makros         | Office-Dateien können Schadcode ausführen        |
| falsche Konfiguration    | Daten werden unsicher übertragen                 |
| fehlende Protokollierung | Änderungen sind nicht nachvollziehbar            |
| ungeprüfte Erweiterungen | Browser-Add-ons können Daten abgreifen           |
| private Software         | Schatten-IT entsteht                             |

Software muss deshalb regelmäßig gepflegt, aktualisiert und kontrolliert werden.

---

## Maßnahmen für sichere Arbeitsplatzsoftware

Mögliche Maßnahmen:

- Software nur aus vertrauenswürdigen Quellen installieren
- zentrale Softwareverteilung nutzen
- Updates regelmäßig einspielen
- unnötige Software entfernen
- Benutzerrechte begrenzen
- Makros kontrollieren
- Browser sicher konfigurieren
- Erweiterungen einschränken
- Lizenzierung prüfen
- lokale Datenspeicherung reduzieren
- Zugriff über Rollen und Gruppen steuern
- Protokollierung aktivieren
- Fachanwendungen dokumentieren

Wichtig ist, dass Software nicht beliebig und unkontrolliert auf Arbeitsplätzen installiert wird.

---

## Clients eines Arbeitsplatzes

Clients sind Endgeräte, die Benutzer direkt verwenden.

Beispiele:

- Desktop-PC
- Laptop
- Thin Client
- Tablet
- Smartphone
- Dockingstation
- Monitor mit integrierten Funktionen
- lokale Peripheriegeräte

Ein Client ist oft der direkte Zugangspunkt zu Unternehmensdaten.

Wenn ein Client kompromittiert wird, kann ein Angreifer möglicherweise auf E-Mails, Dateien, Cloud-Dienste, VPN oder interne Systeme zugreifen.

---

## Schutzbedarf von Clients

Der Schutzbedarf eines Clients hängt davon ab, welche Daten und Dienste genutzt werden.

Wichtige Fragen:

- Wer nutzt den Client?
- Welche Daten werden verarbeitet?
- Wird der Client mobil genutzt?
- Werden Daten lokal gespeichert?
- Gibt es Zugriff auf interne Systeme?
- Hat der Benutzer besondere Rechte?
- Gibt es lokale Administratorrechte?
- Ist der Client Teil einer Domäne oder zentralen Verwaltung?
- Wird der Client für Homeoffice genutzt?
- Gibt es Verschlüsselung?
- Gibt es Backup oder Synchronisation?

Ein normaler Büro-PC kann normalen oder hohen Schutzbedarf haben. Ein Laptop mit Zugriff auf Kundendaten und VPN hat oft höheren Schutzbedarf.

---

## Technische Schutzmaßnahmen für Clients

Wichtige Maßnahmen sind:

- aktuelle Betriebssystemupdates
- aktuelle Anwendungsupdates
- Endpoint-Schutz
- lokale Firewall
- Festplattenverschlüsselung
- sichere Anmeldung
- MFA bei wichtigen Diensten
- automatische Bildschirmsperre
- keine unnötigen Administratorrechte
- zentrale Verwaltung
- Inventarisierung
- Gerätesperre bei Verlust
- sichere Remote-Wartung
- regelmäßige Kontrolle des Sicherheitsstatus

Clients sollten nicht isoliert verwaltet werden. In Unternehmen ist zentrale Verwaltung meistens sicherer und übersichtlicher.

---

## Lokale Administratorrechte

Lokale Administratorrechte sind ein großes Sicherheitsthema.

Wenn normale Benutzer lokale Administratorrechte haben, können sie:

- Programme installieren
- Sicherheitseinstellungen verändern
- Schutzsoftware deaktivieren
- Systemdateien ändern
- Schadsoftware mehr Rechte geben
- Konfigurationen beschädigen

Deshalb sollten normale Benutzer möglichst mit Standardrechten arbeiten.

Adminrechte sollten nur vergeben werden, wenn sie wirklich notwendig sind, und dann möglichst kontrolliert, dokumentiert und zeitlich begrenzt.

---

## Bildschirmsperre und Zugriffsschutz

Arbeitsplätze müssen vor unbefugter Nutzung geschützt werden.

Wichtige Maßnahmen:

- automatische Bildschirmsperre
- starkes Passwort
- keine geteilten Benutzerkonten
- MFA bei wichtigen Diensten
- kein sichtbarer Passwortzettel
- Benutzer meldet sich ab oder sperrt den Bildschirm
- Zugriff nur mit eigenem Konto
- klare Regeln für Pausen und Arbeitsplatzwechsel

Ein entsperrter PC kann ein Sicherheitsrisiko sein, wenn andere Personen Zugriff darauf erhalten.

---

## Mobile Geräte

Mobile Geräte haben besondere Risiken, weil sie außerhalb geschützter Unternehmensräume genutzt werden.

Beispiele:

- Laptop im Zug
- Smartphone unterwegs
- Tablet beim Kunden
- Homeoffice-Gerät
- Gerät im Hotel oder Café

Risiken:

- Verlust
- Diebstahl
- unsichere WLANs
- Einsicht durch fremde Personen
- private Mitnutzung
- fehlende Updates
- unsichere Apps
- Cloud-Synchronisation
- lokale Speicherung sensibler Daten

Mobile Geräte haben oft erhöhten Schutzbedarf.

---

## Maßnahmen für mobile Geräte

Mögliche Maßnahmen:

- Festplattenverschlüsselung
- Gerätesperre
- starke Anmeldung
- MFA
- VPN
- zentrale Geräteverwaltung
- Remote-Wipe
- automatische Updates
- keine lokalen sensiblen Daten, wenn vermeidbar
- getrennte private und geschäftliche Nutzung
- Sicherheitsrichtlinie für mobile Arbeit
- Verlust sofort melden
- sichere Aufbewahrung unterwegs

Mobile Geräte müssen so geschützt werden, dass ein Verlust nicht automatisch zu einem Datenabfluss führt.

---

## Homeoffice-Arbeitsplätze

Homeoffice erweitert den Arbeitsbereich außerhalb des Unternehmens.

Besondere Risiken:

- privates WLAN
- Familienmitglieder oder Besucher in der Nähe
- fehlende physische Kontrolle
- private Geräte im gleichen Netzwerk
- ungestörte Sicht auf den Bildschirm nicht immer möglich
- Ausdrucke zu Hause
- Telefonate mit vertraulichem Inhalt
- Nutzung von Cloud-Diensten
- Verlust oder Diebstahl von Geräten

Homeoffice braucht klare technische und organisatorische Regeln.

---

## Schutzmaßnahmen im Homeoffice

Mögliche Maßnahmen:

- Firmenlaptop statt privatem Gerät
- VPN oder sichere Cloud-Zugriffe
- MFA
- Festplattenverschlüsselung
- automatische Updates
- Endpoint-Schutz
- keine Speicherung auf privaten Datenträgern
- keine Nutzung privater E-Mail für Firmenunterlagen
- sichere WLAN-Konfiguration
- Sichtschutz bei sensiblen Daten
- vertrauliche Telefonate schützen
- Ausdrucke sicher aufbewahren oder vermeiden
- klare Meldewege bei Problemen

Homeoffice ist nicht automatisch unsicher, muss aber bewusst abgesichert werden.

---

## Austausch von Daten

Daten werden in Arbeitsbereichen auf verschiedene Arten ausgetauscht.

Beispiele:

- E-Mail
- Dateiablagen
- Netzlaufwerke
- Cloud-Speicher
- USB-Sticks
- externe Festplatten
- Messenger
- Ticketsysteme
- Drucker
- Scanner
- Remote-Zugriff
- Datenbankexporte

Jeder Austauschweg hat eigene Risiken.

Besonders kritisch ist, wenn vertrauliche Daten unverschlüsselt oder über ungeeignete Wege übertragen werden.

---

## Mobile Datenträger

Mobile Datenträger sind transportable Speichermedien.

Beispiele:

- USB-Sticks
- externe Festplatten
- Speicherkarten
- Smartphones als Speicher
- DVDs
- mobile SSDs

Mobile Datenträger sind praktisch, aber riskant.

Sie können verloren gehen, gestohlen werden, Schadsoftware enthalten oder unkontrolliert Daten aus dem Unternehmen herausbringen.

---

## Risiken mobiler Datenträger

Typische Risiken:

| Risiko                   | Erklärung                                    |
| ------------------------ | -------------------------------------------- |
| Verlust                  | Datenträger geht unterwegs verloren          |
| Diebstahl                | sensible Daten werden entwendet              |
| Schadsoftware            | infizierter USB-Stick kompromittiert Systeme |
| unkontrollierte Kopien   | Daten verlassen das Unternehmen              |
| fehlende Verschlüsselung | Daten sind direkt lesbar                     |
| keine Dokumentation      | niemand weiß, welche Daten kopiert wurden    |
| private Datenträger      | keine Kontrolle über Sicherheit              |
| falsche Entsorgung       | Daten bleiben auf alten Datenträgern         |

Mobile Datenträger sollten deshalb nur kontrolliert und verschlüsselt genutzt werden.

---

## Maßnahmen für mobile Datenträger

Mögliche Schutzmaßnahmen:

- Nutzung nur mit Freigabe
- Verschlüsselung
- Passwortschutz
- zentrale Verwaltung
- USB-Kontrolle
- keine privaten USB-Sticks
- Virenscan
- Protokollierung bei sensiblen Daten
- sichere Aufbewahrung
- sichere Löschung nach Nutzung
- klare Richtlinie für Datenträger
- Nutzung von sicheren Dateiablagen bevorzugen

Bei hohem Schutzbedarf sollte geprüft werden, ob mobile Datenträger überhaupt notwendig sind.

Oft sind zentrale Dateiablagen, VPN oder sichere Cloud-Lösungen besser kontrollierbar.

---

## Drucker und Scanner im Arbeitsbereich

Drucker und Scanner werden oft vergessen, obwohl sie sicherheitsrelevant sind.

Risiken:

- vertrauliche Ausdrucke bleiben im Drucker liegen
- gescannte Dokumente werden falsch abgelegt
- Drucker speichert Kopien intern
- falscher Drucker wird ausgewählt
- Drucker ist aus dem Gastnetz erreichbar
- unberechtigte Personen sehen Ausdrucke
- alte Druckerfestplatten enthalten Daten

Maßnahmen:

- Follow-Me-Printing
- Benutzerfreigabe am Drucker
- sichere Scan-Ziele
- Drucker im passenden Netzwerksegment
- regelmäßige Updates
- Zugriffskontrolle
- sichere Entsorgung alter Drucker
- Ausdrucke sofort abholen

Drucker sind Teil der IT-Infrastruktur und müssen entsprechend geschützt werden.

---

## Papierdokumente und Clean Desk

Informationssicherheit betrifft nicht nur digitale Daten.

Auch Papierdokumente können vertraulich sein.

Beispiele:

- Verträge
- Rechnungen
- Bewerbungsunterlagen
- Personalakten
- Kundendaten
- Notizen mit Zugangsdaten
- Ausdrucke aus Fachsystemen
- interne Pläne

Clean Desk bedeutet, dass vertrauliche Informationen nicht offen herumliegen.

Maßnahmen:

- Dokumente sicher aufbewahren
- abschließbare Schränke nutzen
- Ausdrucke nicht liegen lassen
- Notizen mit Passwörtern vermeiden
- Papier mit sensiblen Daten sicher vernichten
- Besprechungsräume nach Nutzung prüfen

---

## Besucher und externe Personen

Arbeitsbereiche können durch Besucher oder externe Dienstleister beeinflusst werden.

Risiken:

- Einsicht auf Bildschirme
- Zugriff auf offene Dokumente
- unbegleiteter Zugang zu Räumen
- Anschluss unbekannter Geräte
- Fotografieren von Informationen
- Social Engineering
- Zugriff auf Netzwerkdosen

Maßnahmen:

- Besucher anmelden
- Besucher begleiten
- Besucherausweise
- sensible Bereiche abschließen
- Bildschirme sperren
- Netzwerkdosen sichern
- externe Dienstleister kontrolliert einweisen
- Vertraulichkeitsregeln beachten

Nicht jede Person im Gebäude sollte Zugriff auf alle Bereiche haben.

---

## Arbeitsplatz im Empfangsbereich

Der Empfang ist ein besonderer Arbeitsbereich, weil dort interne IT und öffentliche Nähe zusammenkommen.

Typische Risiken:

- Besucher können Bildschirme sehen
- Telefonate können mitgehört werden
- Dokumente liegen offen
- Pakete oder Datenträger werden angenommen
- Besucher erhalten Informationen
- Social-Engineering-Versuche
- unbefugter Zutritt in interne Bereiche

Mögliche Maßnahmen:

- Sichtschutz
- Bildschirmsperre
- klare Besucherprozesse
- keine vertraulichen Dokumente offen liegen lassen
- sichere Paketannahme
- Zutrittskontrolle
- keine Passwörter oder interne Details nennen
- Schulung gegen Social Engineering

Der Empfang hat oft hohen organisatorischen Schutzbedarf.

---

## Arbeitsplatz in der Personalabteilung

Die Personalabteilung verarbeitet besonders sensible personenbezogene Daten.

Beispiele:

- Bewerbungen
- Arbeitsverträge
- Gehaltsdaten
- Krankmeldungen
- Abmahnungen
- Personalakten
- Kontaktdaten
- Zeugnisse

Schutzbedarf:

| Schutzziel      | Bewertung                       |
| --------------- | ------------------------------- |
| Vertraulichkeit | meistens hoch bis sehr hoch     |
| Integrität      | hoch                            |
| Verfügbarkeit   | je nach Prozess normal bis hoch |

Mögliche Maßnahmen:

- strenge Berechtigungen
- verschlüsselte Speicherung
- sichere Dateiablagen
- keine offenen Ausdrucke
- Zugriff nur für berechtigte Personen
- Protokollierung
- sichere E-Mail-Nutzung
- klare Löschfristen
- Datenschutz beachten

---

## Arbeitsplatz in der Buchhaltung

Die Buchhaltung verarbeitet Finanzdaten und oft auch personenbezogene Daten.

Beispiele:

- Rechnungen
- Bankdaten
- Zahlungsinformationen
- Steuerunterlagen
- Lieferantendaten
- Kundendaten
- Gehaltsinformationen
- Finanzberichte

Schutzbedarf:

| Schutzziel      | Bewertung    |
| --------------- | ------------ |
| Vertraulichkeit | hoch         |
| Integrität      | sehr wichtig |
| Verfügbarkeit   | oft hoch     |

Integrität ist besonders wichtig, weil falsche Finanzdaten direkte wirtschaftliche Folgen haben können.

Mögliche Maßnahmen:

- Berechtigungskonzept
- Vier-Augen-Prinzip bei kritischen Zahlungen
- sichere Banking-Verfahren
- Protokollierung
- Backup
- Schutz vor Phishing
- sichere E-Mail-Prozesse
- klare Freigaben

---

## IT-Administrationsarbeitsplatz

Ein IT-Administrationsarbeitsplatz hat besonders hohen Schutzbedarf.

Dort werden oft Systeme verwaltet, Rechte geändert, Server administriert und Netzwerkgeräte konfiguriert.

Risiken:

- Kompromittierung von Adminzugängen
- Zugriff auf Passwörter oder Dokumentation
- Änderung kritischer Systeme
- falsche Konfiguration
- Ausbreitung von Schadsoftware
- Zugriff auf viele Unternehmensdaten

Maßnahmen:

- getrennte Admin-Konten
- MFA
- keine normalen Tätigkeiten mit Admin-Konto
- Zugriff aus Managementnetz
- sichere Passwortverwaltung
- Protokollierung
- regelmäßige Rechteprüfung
- keine unnötigen Tools
- besonders sichere Clients
- Bildschirm sperren
- Notfallzugänge kontrolliert verwalten

Admin-Arbeitsplätze haben häufig sehr hohen Schutzbedarf.

---

## Serverraum als Arbeitsbereich

Ein Serverraum ist ein besonders kritischer Bereich.

Dort befinden sich oft:

- Server
- Switches
- Router
- Firewalls
- NAS
- Backup-Systeme
- Patchpanel
- USV
- Netzwerkdokumentation
- Klimatisierung

Risiken:

- unbefugter physischer Zugriff
- Stromausfall
- Überhitzung
- Kabel werden falsch gezogen
- Diebstahl
- Wasserschaden
- Brand
- fehlende Dokumentation
- unsachgemäße Arbeiten

Maßnahmen:

- Zutrittskontrolle
- abschließbarer Raum
- Klimatisierung
- USV
- Brandschutz
- Kabelmanagement
- Dokumentation
- Monitoring
- Zugang nur für berechtigte Personen
- Besucher nur begleitet

Ein Serverraum hat meistens hohen oder sehr hohen Schutzbedarf.

---

## Schutzbedarf dokumentieren

Die Analyse eines Arbeitsbereichs muss dokumentiert werden.

Wichtige Inhalte:

- Name des Arbeitsbereichs
- Standort
- verantwortliche Personen
- genutzte Geräte
- genutzte Software
- verarbeitete Daten
- Benutzergruppen
- Netzwerkzugänge
- mobile Datenträger
- Drucker und Scanner
- besondere Risiken
- Bewertung der Vertraulichkeit
- Bewertung der Integrität
- Bewertung der Verfügbarkeit
- vorhandene Maßnahmen
- empfohlene Maßnahmen
- offene Risiken
- Datum der Analyse

Dokumentation hilft, Entscheidungen nachvollziehbar zu machen und später zu prüfen.

---

## Vorgehen bei der Analyse

Ein mögliches Vorgehen:

1. Arbeitsbereich festlegen
2. Geräte und Software erfassen
3. Datenarten bestimmen
4. Benutzer und Berechtigungen prüfen
5. Netzwerkzugänge betrachten
6. mobile Datenträger und Drucker prüfen
7. physische Umgebung bewerten
8. Vertraulichkeit, Integrität und Verfügbarkeit bewerten
9. Risiken und Schwachstellen notieren
10. Maßnahmen ableiten
11. Ergebnis dokumentieren
12. regelmäßig überprüfen

Wichtig ist, nicht nur technische Details zu sehen, sondern auch Arbeitsabläufe und Benutzerverhalten.

---

## Maßnahmen aus der Analyse ableiten

Nach der Bewertung müssen passende Maßnahmen ausgewählt werden.

Beispiele:

| Feststellung                      | mögliche Maßnahme                         |
| --------------------------------- | ----------------------------------------- |
| sensible Daten auf Laptop         | Festplattenverschlüsselung                |
| viele Ausdrucke mit Kundendaten   | Follow-Me-Printing                        |
| USB-Sticks werden frei genutzt    | Datenträgerrichtlinie und Verschlüsselung |
| Benutzer haben lokale Adminrechte | Rechte reduzieren                         |
| Homeoffice ohne klare Regeln      | Homeoffice-Richtlinie                     |
| Drucker im falschen Netz          | Netzwerksegmentierung                     |
| Personalakten offen zugänglich    | Berechtigungen und sichere Ablage         |
| Adminzugänge ohne MFA             | MFA aktivieren                            |
| Serverraum offen zugänglich       | Zutrittskontrolle                         |

Die Maßnahme muss zum Schutzbedarf passen und praktisch umsetzbar sein.

---

## Regelmäßige Überprüfung

Arbeitsbereiche verändern sich.

Beispiele:

- neue Software wird eingeführt
- mehr Benutzer arbeiten in einem Bereich
- Homeoffice wird häufiger genutzt
- neue Datenarten werden verarbeitet
- Drucker oder Scanner werden ersetzt
- Cloud-Dienste kommen hinzu
- Rollen und Rechte ändern sich
- neue gesetzliche Anforderungen entstehen
- neue Sicherheitsbedrohungen werden bekannt

Deshalb muss der Schutzbedarf regelmäßig überprüft werden.

Eine einmalige Analyse reicht nicht dauerhaft aus.

---

## Praxisbeispiele

### Beispiel 1: Homeoffice-Laptop

Ein Mitarbeiter nutzt einen Firmenlaptop im Homeoffice. Der Laptop hat Zugriff auf E-Mail, Cloud-Speicher und VPN. Der Schutzbedarf ist erhöht, weil das Gerät außerhalb des Unternehmens genutzt wird. Sinnvolle Maßnahmen sind Verschlüsselung, MFA, VPN, Endpoint-Schutz und klare Homeoffice-Regeln.

### Beispiel 2: USB-Stick mit Kundendaten

Ein USB-Stick wird genutzt, um Kundendaten zu übertragen. Der Schutzbedarf bei Vertraulichkeit ist hoch. Ohne Verschlüsselung wäre ein Verlust kritisch. Besser ist eine sichere Dateiablage oder ein verschlüsselter, kontrollierter Datenträger.

### Beispiel 3: IT-Admin-Arbeitsplatz

Ein Admin-Arbeitsplatz hat Zugriff auf Server, Netzwerkgeräte und Benutzerverwaltung. Der Schutzbedarf ist sehr hoch. Notwendig sind MFA, getrennte Admin-Konten, Protokollierung, sichere Passwortverwaltung und ein besonders geschützter Client.

---

## Typische Fehler

| Fehler                                       | Problem                                                        |
| -------------------------------------------- | -------------------------------------------------------------- |
| nur Server betrachten                        | Risiken an Arbeitsplätzen werden übersehen                     |
| mobile Datenträger ignorieren                | Daten können unkontrolliert abfließen                          |
| Drucker nicht als IT-System sehen            | vertrauliche Ausdrucke und gespeicherte Daten werden vergessen |
| lokale Adminrechte erlauben                  | Schadenspotenzial steigt                                       |
| Homeoffice wie Büro behandeln                | andere Risiken werden übersehen                                |
| Papierdokumente vergessen                    | Informationssicherheit ist nicht nur digital                   |
| Besucher nicht berücksichtigen               | Einsicht oder Zugriff kann entstehen                           |
| Admin-Arbeitsplätze nicht besonders schützen | sehr hohes Risiko                                              |
| Schutzbedarf nicht dokumentieren             | Maßnahmen sind später nicht nachvollziehbar                    |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist die Analyse von Arbeitsbereichen sehr praxisnah.

Ein FISI muss erkennen, welche technischen und organisatorischen Risiken an normalen Arbeitsplätzen entstehen können.

In der Praxis bedeutet das:

- Clients und Software bewerten
- Benutzerrechte prüfen
- mobile Geräte absichern
- USB-Sticks und externe Datenträger einordnen
- Drucker und Scanner berücksichtigen
- Homeoffice sicher anbinden
- Admin-Arbeitsplätze besonders schützen
- Serverräume als kritische Bereiche verstehen
- Schutzbedarf dokumentieren
- passende Maßnahmen vorschlagen

Ein guter FISI betrachtet Sicherheit nicht nur im Serverraum, sondern auch dort, wo Benutzer täglich arbeiten.

---

## Kurze Zusammenfassung

Der Schutzbedarf in Arbeitsbereichen wird durch Daten, Geräte, Software, Benutzer, Netzwerkzugänge, Räume und Arbeitsprozesse bestimmt.

Wichtige Themen sind Arbeitsplatzsoftware, Clients, mobile Geräte, Homeoffice, mobile Datenträger, Drucker, Papierdokumente, Besucher, Admin-Arbeitsplätze und Serverräume.

Besonders wichtig sind die Schutzziele Vertraulichkeit, Integrität und Verfügbarkeit.

Für FISI ist dieses Kapitel wichtig, weil viele Sicherheitsrisiken direkt am Arbeitsplatz entstehen und passende technische sowie organisatorische Maßnahmen notwendig sind.
