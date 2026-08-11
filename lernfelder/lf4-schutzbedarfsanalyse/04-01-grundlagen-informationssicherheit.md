# 4.1 Grundlagen der Informationssicherheit

In diesem Kapitel geht es um die Grundlagen der Informationssicherheit.

Informationssicherheit bedeutet, Informationen, IT-Systeme, Netzwerke, Anwendungen und Prozesse so zu schützen, dass ein Unternehmen zuverlässig und sicher arbeiten kann. Dabei geht es nicht nur um Hackerangriffe, sondern auch um Fehlbedienung, Datenverlust, technische Defekte, falsche Berechtigungen, unsichere Passwörter, fehlende Backups und organisatorische Fehler.

Für Fachinformatiker für Systemintegration ist Informationssicherheit ein zentrales Thema, weil technische Systeme nicht nur funktionieren müssen. Sie müssen auch geschützt, kontrolliert, dokumentiert und wiederherstellbar sein.

---

## Kurz erklärt

Informationssicherheit schützt Informationen und IT-Systeme vor Schäden.

Wichtige Ziele sind:

- Daten vor unbefugtem Zugriff schützen
- Daten vor Manipulation schützen
- Systeme verfügbar halten
- Ausfälle vermeiden
- Schäden begrenzen
- Wiederherstellung ermöglichen
- Benutzerrechte kontrollieren
- Sicherheitsvorfälle erkennen
- gesetzliche Anforderungen beachten
- Sicherheitsmaßnahmen dokumentieren

Informationssicherheit ist nicht nur Aufgabe der IT-Abteilung. Sie betrifft das ganze Unternehmen, weil fast jeder Arbeitsbereich mit Daten und IT-Systemen arbeitet.

---

## Unterschied zwischen Informationssicherheit und IT-Sicherheit

Informationssicherheit und IT-Sicherheit werden oft ähnlich verwendet, sind aber nicht genau gleich.

| Begriff                | Bedeutung                                                                                       |
| ---------------------- | ----------------------------------------------------------------------------------------------- |
| Informationssicherheit | schützt Informationen unabhängig davon, ob sie digital, auf Papier oder mündlich vorhanden sind |
| IT-Sicherheit          | schützt IT-Systeme, Netzwerke, Anwendungen und digitale Daten                                   |
| Datenschutz            | schützt personenbezogene Daten und die Rechte betroffener Personen                              |

Informationssicherheit ist also breiter als IT-Sicherheit.

Beispiel:

Eine Kundenliste auf einem Server betrifft IT-Sicherheit und Informationssicherheit.  
Eine ausgedruckte Kundenliste auf einem Schreibtisch betrifft Informationssicherheit und Datenschutz, aber nicht direkt IT-Sicherheit.

---

## Grundziele der Informationssicherheit

Die drei wichtigsten Schutzziele sind:

| Schutzziel      | Bedeutung                                                                |
| --------------- | ------------------------------------------------------------------------ |
| Vertraulichkeit | Informationen dürfen nur von berechtigten Personen gelesen werden        |
| Integrität      | Informationen müssen korrekt, vollständig und unverändert bleiben        |
| Verfügbarkeit   | Informationen und Systeme müssen nutzbar sein, wenn sie gebraucht werden |

Diese drei Ziele sind die Grundlage vieler Sicherheitskonzepte.

Sie werden oft als CIA-Triade bezeichnet:

- Confidentiality
- Integrity
- Availability

Auf Deutsch:

- Vertraulichkeit
- Integrität
- Verfügbarkeit

---

## Vertraulichkeit

Vertraulichkeit bedeutet, dass Informationen nur für berechtigte Personen zugänglich sind.

Beispiele für vertrauliche Informationen:

- Kundendaten
- Personaldaten
- Passwörter
- Finanzdaten
- Verträge
- interne Dokumentationen
- Netzpläne
- Zugangsdaten
- Geschäftsgeheimnisse
- Gesundheitsdaten

Maßnahmen zum Schutz der Vertraulichkeit:

- Benutzerkonten
- starke Passwörter
- Mehrfaktor-Authentifizierung
- Berechtigungen
- Verschlüsselung
- VPN
- Zugriffskontrollen
- sichere Dateiablagen
- getrennte Netzbereiche
- Schulung der Benutzer

Ein Verstoß gegen Vertraulichkeit liegt vor, wenn unberechtigte Personen Informationen sehen, kopieren oder weitergeben können.

---

## Integrität

Integrität bedeutet, dass Informationen korrekt, vollständig und unverändert bleiben.

Daten dürfen nicht unbemerkt verändert oder beschädigt werden.

Beispiele für Integritätsprobleme:

- eine Rechnung wird manipuliert
- eine Konfigurationsdatei wird falsch geändert
- eine Datenbank enthält falsche Werte
- ein Backup ist beschädigt
- Schadsoftware verändert Dateien
- ein Benutzer löscht wichtige Informationen
- ein System schreibt fehlerhafte Daten

Maßnahmen zum Schutz der Integrität:

- Zugriffsrechte
- Prüfsummen
- digitale Signaturen
- Versionsverwaltung
- Protokollierung
- Backup
- Änderungsmanagement
- Schutz vor Schadsoftware
- kontrollierte Administration

Integrität ist wichtig, weil falsche oder manipulierte Daten zu falschen Entscheidungen führen können.

---

## Verfügbarkeit

Verfügbarkeit bedeutet, dass Systeme, Dienste und Daten erreichbar sind, wenn sie benötigt werden.

Beispiele für Verfügbarkeitsprobleme:

- Serverausfall
- Internetstörung
- defekter Switch
- Stromausfall
- DNS-Ausfall
- DHCP-Ausfall
- Datenbank nicht erreichbar
- Cloud-Dienst gestört
- Ransomware verschlüsselt Daten
- Backup kann nicht wiederhergestellt werden

Maßnahmen zum Schutz der Verfügbarkeit:

- redundante Systeme
- USV
- Monitoring
- Backups
- Wartung
- Ersatzhardware
- sichere Updates
- Notfallpläne
- Hochverfügbarkeit
- klare Wiederherstellungsprozesse

Verfügbarkeit ist besonders wichtig bei Systemen, die für den täglichen Betrieb notwendig sind.

---

## Weitere Schutzziele

Neben Vertraulichkeit, Integrität und Verfügbarkeit gibt es weitere wichtige Schutzziele.

| Schutzziel            | Bedeutung                                                       |
| --------------------- | --------------------------------------------------------------- |
| Authentizität         | Echtheit eines Benutzers, Systems oder Dokuments                |
| Verbindlichkeit       | Handlungen können später nicht einfach abgestritten werden      |
| Nachvollziehbarkeit   | Vorgänge können durch Logs und Dokumentation geprüft werden     |
| Belastbarkeit         | Systeme können Störungen widerstehen und weiterarbeiten         |
| Wiederherstellbarkeit | Systeme können nach Störungen wieder in Betrieb genommen werden |

Diese Ziele sind besonders wichtig bei administrativen Tätigkeiten, sicherheitskritischen Prozessen und rechtlichen Anforderungen.

---

## Authentifizierung und Autorisierung

Authentifizierung und Autorisierung sind zwei wichtige Begriffe.

| Begriff           | Frage          | Bedeutung                     |
| ----------------- | -------------- | ----------------------------- |
| Authentifizierung | Wer bist du?   | Identität wird geprüft        |
| Autorisierung     | Was darfst du? | Berechtigungen werden geprüft |

Beispiel:

Ein Benutzer meldet sich mit Benutzername, Passwort und MFA an. Das ist Authentifizierung.

Danach prüft das System, ob dieser Benutzer auf einen Ordner zugreifen darf. Das ist Autorisierung.

Ein Benutzer kann korrekt angemeldet sein, aber trotzdem keinen Zugriff auf bestimmte Daten haben.

---

## Verantwortung in der Informationssicherheit

Informationssicherheit ist eine gemeinsame Verantwortung.

Verschiedene Rollen haben unterschiedliche Aufgaben.

| Rolle                              | Aufgabe                                                           |
| ---------------------------------- | ----------------------------------------------------------------- |
| Geschäftsführung                   | trägt Gesamtverantwortung und entscheidet über Sicherheitsniveau  |
| IT-Abteilung                       | setzt technische Maßnahmen um und betreibt Systeme sicher         |
| Administratoren                    | verwalten Systeme, Rechte, Updates und Sicherheitskonfigurationen |
| Datenschutzbeauftragte             | achten auf den Schutz personenbezogener Daten                     |
| Informationssicherheitsbeauftragte | koordinieren Sicherheitsprozesse und Konzepte                     |
| Benutzer                           | müssen Sicherheitsregeln einhalten                                |
| externe Dienstleister              | müssen vertragliche Sicherheitsanforderungen beachten             |

Sicherheit funktioniert nur, wenn Technik, Organisation und Benutzerverhalten zusammenpassen.

---

## Technische und organisatorische Maßnahmen

Sicherheitsmaßnahmen lassen sich grob in technische und organisatorische Maßnahmen einteilen.

| Art                        | Beispiele                                                          |
| -------------------------- | ------------------------------------------------------------------ |
| technische Maßnahmen       | Firewall, Verschlüsselung, Backup, MFA, Virenschutz                |
| organisatorische Maßnahmen | Richtlinien, Schulungen, Prozesse, Verantwortlichkeiten            |
| physische Maßnahmen        | Serverraum abschließen, Zugangskontrolle, Brandschutz              |
| personelle Maßnahmen       | Sensibilisierung, Berechtigungsprüfung, Onboarding und Offboarding |

Ein gutes Sicherheitskonzept besteht immer aus mehreren Maßnahmen.

Eine Firewall allein reicht nicht, wenn Benutzer unsichere Passwörter verwenden oder wichtige Daten nicht gesichert werden.

---

## Sicherheitsbereiche im Unternehmen

Ein Unternehmen kann verschiedene Sicherheitsbereiche haben.

Beispiele:

- öffentlicher Bereich
- Bürobereich
- Serverraum
- Rechenzentrum
- Lager
- Empfang
- Homeoffice
- Produktionsbereich
- WLAN-Bereich
- Gastnetz
- Managementnetz
- Cloud-Umgebung

Nicht jeder Bereich hat den gleichen Schutzbedarf.

Ein Serverraum benötigt zum Beispiel stärkere Zugriffskontrolle als ein normaler Besprechungsraum. Ein Managementnetz muss stärker geschützt werden als ein Gäste-WLAN.

---

## Bedrohungen

Eine Bedrohung ist eine mögliche Ursache für einen Schaden.

Bedrohungen können technisch, menschlich, organisatorisch oder physisch sein.

| Bedrohung                  | Beispiel                                            |
| -------------------------- | --------------------------------------------------- |
| technische Bedrohung       | Hardwaredefekt, Softwarefehler, Netzwerkausfall     |
| menschliche Bedrohung      | Fehlbedienung, schwaches Passwort, falsches Löschen |
| organisatorische Bedrohung | keine Zuständigkeit, fehlende Prozesse              |
| physische Bedrohung        | Feuer, Wasser, Diebstahl, Stromausfall              |
| kriminelle Bedrohung       | Phishing, Ransomware, Datendiebstahl                |

Viele Sicherheitsvorfälle entstehen durch eine Kombination mehrerer Ursachen.

Beispiel: Ein Benutzer klickt auf eine Phishing-Mail, weil Schulung fehlt, MFA nicht aktiv ist und das Konto zu viele Rechte besitzt.

---

## Gefährdungen

Eine Gefährdung entsteht, wenn eine Bedrohung auf eine Schwachstelle trifft.

Beispiel:

- Bedrohung: Schadsoftware
- Schwachstelle: veraltetes Betriebssystem
- Gefährdung: System kann kompromittiert werden

Weitere Beispiele:

| Bedrohung            | Schwachstelle                    | mögliche Gefährdung |
| -------------------- | -------------------------------- | ------------------- |
| Phishing             | fehlende MFA                     | Kontoübernahme      |
| Stromausfall         | keine USV                        | Serverausfall       |
| Ransomware           | kein getestetes Backup           | Datenverlust        |
| Diebstahl            | keine Festplattenverschlüsselung | Datenabfluss        |
| Fehlbedienung        | keine Rechtebegrenzung           | ungewolltes Löschen |
| Angriff aus Internet | offene Ports                     | unbefugter Zugriff  |

Informationssicherheit versucht, Schwachstellen zu reduzieren und Schäden zu begrenzen.

---

## Schwachstellen

Eine Schwachstelle ist eine Sicherheitslücke oder ein Mangel in Technik, Organisation oder Verhalten.

Beispiele für Schwachstellen:

- schwache Passwörter
- fehlende Updates
- falsch konfigurierte Firewall
- unnötige Administratorrechte
- unverschlüsselte Geräte
- offene Netzwerkfreigaben
- fehlende Backups
- nicht getestete Wiederherstellung
- alte Software
- ungeschützte WLANs
- fehlende Dokumentation
- keine Schulung der Benutzer

Schwachstellen müssen erkannt, bewertet und behoben oder zumindest kontrolliert werden.

---

## Risiko

Ein Risiko beschreibt, wie wahrscheinlich ein Schaden ist und wie groß die Auswirkung wäre.

Vereinfacht:

```text
Risiko = Eintrittswahrscheinlichkeit × Schadenshöhe
```

Ein Risiko ist besonders kritisch, wenn die Wahrscheinlichkeit hoch und der mögliche Schaden groß ist.

Beispiel:

Ein alter Server ohne Backup hat ein hohes Risiko, wenn er wichtige Daten enthält und ein Ausfall den Betrieb stark beeinflusst.

Risikobewertung hilft, Sicherheitsmaßnahmen sinnvoll zu priorisieren.

---

## Schadensszenarien

Ein Schadensszenario beschreibt, was passieren kann, wenn eine Gefährdung eintritt.

Beispiele:

### Datenverlust

Wichtige Dateien werden gelöscht oder beschädigt. Ohne Backup können sie nicht wiederhergestellt werden.

### Datenabfluss

Unberechtigte Personen erhalten Zugriff auf Kundendaten, Personaldaten oder interne Dokumente.

### Systemausfall

Ein Server, Netzwerkgerät oder Cloud-Dienst fällt aus. Benutzer können nicht arbeiten.

### Manipulation

Daten oder Konfigurationen werden unbemerkt verändert. Dadurch entstehen falsche Ergebnisse oder Sicherheitsprobleme.

### Reputationsschaden

Kunden oder Partner verlieren Vertrauen, weil Sicherheitsvorfälle öffentlich werden.

### Rechtliche Folgen

Bei Datenschutzverstößen oder Vertragsverletzungen können rechtliche und finanzielle Folgen entstehen.

---

## Aktuelle Bedrohungen

Moderne IT-Umgebungen sind vielen aktuellen Bedrohungen ausgesetzt.

Wichtige Beispiele:

- Phishing
- Ransomware
- Identitätsdiebstahl
- Social Engineering
- Schadsoftware
- unsichere Cloud-Konfiguration
- Angriffe auf VPN-Zugänge
- gestohlene Passwörter
- Supply-Chain-Angriffe
- ungepatchte Systeme
- unsichere Remote-Zugänge
- Angriffe auf mobile Geräte

Viele Angriffe zielen nicht direkt auf Technik, sondern auf Benutzer und Zugangsdaten.

Deshalb sind Schulung, MFA, Rechtebegrenzung und Monitoring besonders wichtig.

---

## Phishing

Phishing ist ein Täuschungsversuch, bei dem Angreifer an Zugangsdaten oder vertrauliche Informationen gelangen wollen.

Typische Merkmale:

- gefälschte E-Mail
- dringende Aufforderung
- angeblicher Sicherheitsvorfall
- Link zu gefälschter Login-Seite
- Dateianhang mit Schadsoftware
- gefälschter Absender
- Druck oder Angst

Beispiele:

- “Ihr Konto wurde gesperrt.”
- “Bitte bestätigen Sie sofort Ihr Passwort.”
- “Offene Rechnung im Anhang.”
- “Neue Sicherheitsmeldung.”

Phishing ist gefährlich, weil es Benutzer direkt angreift und oft professionell aussieht.

---

## Ransomware

Ransomware ist Schadsoftware, die Daten verschlüsselt oder Systeme sperrt.

Angreifer verlangen danach meist Geld für die Wiederherstellung.

Mögliche Folgen:

- Daten nicht mehr nutzbar
- Serverausfall
- Produktionsausfall
- Datenabfluss
- Erpressung
- hohe Wiederherstellungskosten
- Images und Backups ebenfalls betroffen
- Reputationsschaden

Wichtige Schutzmaßnahmen:

- aktuelle Updates
- sichere Backups
- getrennte Backup-Kopien
- MFA
- keine unnötigen Adminrechte
- E-Mail-Schutz
- Benutzer sensibilisieren
- Netzwerksegmentierung
- Monitoring
- Notfallplan

Backups müssen getrennt und getestet sein. Ein Backup, das ebenfalls verschlüsselt wird oder nicht wiederherstellbar ist, hilft im Ernstfall nicht.

---

## Identitätsdiebstahl

Identitätsdiebstahl bedeutet, dass Angreifer fremde Zugangsdaten oder Identitäten nutzen.

Beispiele:

- gestohlene Passwörter
- kompromittierte E-Mail-Konten
- gestohlene Session-Cookies
- missbrauchte Administratorzugänge
- gefälschte Identitäten bei Supportanfragen
- Zugriff über alte Benutzerkonten

Folgen:

- unbefugter Zugriff auf Daten
- Versand von Phishing-Mails
- Manipulation von Systemen
- Zugriff auf Cloud-Dienste
- finanzielle Schäden
- Vertrauensverlust

Schutzmaßnahmen:

- MFA
- starke Passwörter
- Passwortmanager
- regelmäßige Rechteprüfung
- Deaktivierung alter Konten
- Monitoring von Anmeldungen
- keine geteilten Benutzerkonten
- sichere Prozesse im Support

---

## Social Engineering

Social Engineering bedeutet, dass Menschen manipuliert werden, um Sicherheitsregeln zu umgehen.

Angreifer nutzen dabei Vertrauen, Hilfsbereitschaft, Stress oder Zeitdruck.

Beispiele:

- Anruf angeblich vom IT-Support
- Bitte um Passwort oder MFA-Code
- gefälschte Nachricht vom Chef
- angeblicher Dienstleister vor Ort
- Druck durch angebliche Dringlichkeit
- USB-Stick wird absichtlich liegen gelassen
- gefälschte Rechnung

Social Engineering ist gefährlich, weil technische Schutzmaßnahmen oft umgangen werden, wenn Menschen falsche Entscheidungen treffen.

Schutzmaßnahmen:

- Schulungen
- klare Supportprozesse
- keine Passwortweitergabe
- Identität von Anfragenden prüfen
- MFA-Codes nie weitergeben
- verdächtige Vorfälle melden
- klare Regeln für externe Personen
- Sensibilisierung für Druck und Manipulation

---

## Schadsoftware

Schadsoftware ist Software, die Systeme oder Daten schädigt.

Arten von Schadsoftware:

| Art            | Bedeutung                                    |
| -------------- | -------------------------------------------- |
| Virus          | verbreitet sich über Dateien oder Programme  |
| Wurm           | verbreitet sich selbstständig über Netzwerke |
| Trojaner       | tarnt sich als legitime Software             |
| Spyware        | sammelt Informationen                        |
| Ransomware     | verschlüsselt Daten oder sperrt Systeme      |
| Keylogger      | zeichnet Tastatureingaben auf                |
| Botnet-Malware | macht Systeme Teil eines Botnetzes           |

Schutzmaßnahmen:

- aktuelle Systeme
- Sicherheitssoftware
- eingeschränkte Rechte
- sichere E-Mail-Filter
- keine unbekannten Anhänge öffnen
- keine unsichere Software installieren
- Netzwerksegmentierung
- Monitoring
- Backups

---

## Sicherheitsrichtlinien

Sicherheitsrichtlinien legen fest, wie Systeme und Benutzer sicher arbeiten sollen.

Beispiele für Richtlinien:

- Passwort-Richtlinie
- Backup-Richtlinie
- Clean-Desk-Policy
- Homeoffice-Richtlinie
- Mobile-Device-Richtlinie
- Rechte- und Rollenkonzept
- Patchmanagement-Richtlinie
- Umgang mit USB-Geräten
- Umgang mit E-Mails und Anhängen
- Meldeweg für Sicherheitsvorfälle

Richtlinien müssen verständlich, realistisch und umsetzbar sein.

Eine Richtlinie bringt wenig, wenn sie niemand kennt oder wenn sie in der Praxis nicht eingehalten werden kann.

---

## IT-Grundschutz

IT-Grundschutz ist ein Sicherheitsansatz des Bundesamts für Sicherheit in der Informationstechnik.

Die Grundidee ist, typische Sicherheitsanforderungen, Gefährdungen und Maßnahmen systematisch zu betrachten.

IT-Grundschutz hilft dabei:

- Sicherheitsniveau strukturiert aufzubauen
- Risiken zu erkennen
- Schutzbedarf zu bewerten
- Maßnahmen auszuwählen
- Sicherheitsprozesse zu dokumentieren
- Verantwortlichkeiten zu klären
- Informationssicherheit dauerhaft zu verbessern

Für FISI ist wichtig, den Grundgedanken zu verstehen: Sicherheit wird nicht zufällig umgesetzt, sondern geplant, bewertet, dokumentiert und regelmäßig überprüft.

---

## Sicherheitsprozess

Informationssicherheit ist kein einmaliges Projekt.

Sie ist ein fortlaufender Prozess.

Typischer Ablauf:

1. Werte und Systeme erfassen
2. Schutzbedarf feststellen
3. Risiken und Gefährdungen bewerten
4. Maßnahmen auswählen
5. Maßnahmen umsetzen
6. Wirksamkeit prüfen
7. Dokumentation aktualisieren
8. Verbesserungen planen

Sicherheit muss regelmäßig überprüft werden, weil sich Systeme, Benutzer, Bedrohungen und Anforderungen ändern.

---

## Gesetze und Vorgaben

Informationssicherheit hängt auch mit rechtlichen und organisatorischen Vorgaben zusammen.

Wichtige Themen:

- Datenschutz
- Schutz personenbezogener Daten
- Aufbewahrungspflichten
- Vertraulichkeitspflichten
- Verträge mit Kunden und Dienstleistern
- interne Unternehmensrichtlinien
- Branchenanforderungen
- Meldepflichten bei Sicherheitsvorfällen

Für FISI bedeutet das: Technische Maßnahmen müssen oft auch rechtliche und organisatorische Anforderungen unterstützen.

Besonders bei personenbezogenen Daten muss sorgfältig gearbeitet werden.

---

## Datenschutz und personenbezogene Daten

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
- Bewerbungsdaten
- Gesundheitsdaten

Beim Umgang mit solchen Daten müssen Zugriffe, Speicherung, Weitergabe, Löschung und Sicherheit beachtet werden.

Ein FISI darf personenbezogene Daten nicht unnötig kopieren, offen speichern oder unberechtigt weitergeben.

---

## Sicherheitsvorfälle

Ein Sicherheitsvorfall ist ein Ereignis, das die Sicherheit von Informationen oder Systemen beeinträchtigt.

Beispiele:

- verlorener Laptop
- Malware-Fund
- erfolgreicher Phishing-Angriff
- unberechtigter Zugriff
- Daten wurden versehentlich versendet
- Server wurde kompromittiert
- Backup ist nicht verfügbar
- verdächtige Anmeldung
- Firewall meldet ungewöhnliche Verbindungen

Wichtig ist, Sicherheitsvorfälle schnell zu melden und geordnet zu bearbeiten.

Vertuschen oder Ignorieren kann den Schaden vergrößern.

---

## Umgang mit Sicherheitsvorfällen

Bei Sicherheitsvorfällen ist strukturiertes Vorgehen wichtig.

Typische Schritte:

1. Vorfall erkennen
2. Vorfall melden
3. Schaden begrenzen
4. Systeme sichern
5. Ursache analysieren
6. betroffene Personen oder Stellen informieren
7. Systeme wiederherstellen
8. Maßnahmen verbessern
9. Vorfall dokumentieren

Je nach Vorfall können Datenschutz, Geschäftsführung, IT-Leitung, externe Dienstleister oder Behörden beteiligt sein.

---

## Dokumentation in der Informationssicherheit

Sicherheitsmaßnahmen und Entscheidungen müssen dokumentiert werden.

Wichtige Dokumente:

- Sicherheitsrichtlinien
- Netzpläne
- Schutzbedarfsanalyse
- Rechtekonzept
- Backupkonzept
- Notfallplan
- Patchmanagement-Prozess
- Asset-Inventar
- Risikobewertung
- Änderungsprotokoll
- Sicherheitsvorfälle
- Wiederherstellungsanleitungen

Dokumentation hilft bei Betrieb, Support, Audits, Notfällen und Übergaben.

Ohne Dokumentation ist Sicherheit schwer überprüfbar.

---

## Praxisbeispiele

### Beispiel 1: Vertrauliche Personaldaten

Personaldaten liegen auf einem Dateiserver. Nur die Personalabteilung und berechtigte Führungskräfte dürfen darauf zugreifen. Die Daten werden verschlüsselt gesichert und Zugriffe werden protokolliert.

### Beispiel 2: Ransomware-Vorfall

Ein Benutzer öffnet einen schädlichen Anhang. Dateien werden verschlüsselt. Durch Netzwerksegmentierung, eingeschränkte Rechte und getestete Backups kann der Schaden begrenzt und die Wiederherstellung durchgeführt werden.

### Beispiel 3: Unsicherer Administratorzugang

Ein Administratorzugang hat kein MFA und ein schwaches Passwort. Dadurch ist das Risiko einer Kontoübernahme hoch. Eine sinnvolle Maßnahme ist MFA, starke Passwortregeln, Monitoring und regelmäßige Rechteprüfung.

---

## Typische Fehler

| Fehler                                  | Problem                                                 |
| --------------------------------------- | ------------------------------------------------------- |
| Sicherheit nur als Firewall verstehen   | wichtige organisatorische und personelle Aspekte fehlen |
| Benutzer nicht schulen                  | Phishing und Social Engineering bleiben gefährlich      |
| zu viele Administratorrechte vergeben   | Schadenspotenzial steigt                                |
| Backups nicht testen                    | Wiederherstellung kann im Notfall scheitern             |
| Sicherheitsvorfälle nicht dokumentieren | Ursachen und Verbesserungen bleiben unklar              |
| Datenschutz ignorieren                  | rechtliche Risiken entstehen                            |
| alte Benutzerkonten aktiv lassen        | unbefugter Zugriff möglich                              |
| Updates lange aufschieben               | bekannte Schwachstellen bleiben offen                   |
| keine klare Zuständigkeit               | Sicherheitsmaßnahmen werden nicht umgesetzt             |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Informationssicherheit eine Grundlage des beruflichen Handelns.

Ein FISI richtet Systeme nicht nur ein, sondern muss auch deren Schutzbedarf, Risiken und Sicherheitsmaßnahmen verstehen.

In der Praxis bedeutet das:

- Schutzziele kennen
- Vertraulichkeit, Integrität und Verfügbarkeit bewerten
- Benutzerrechte sinnvoll setzen
- Systeme aktuell halten
- Backups und Wiederherstellung beachten
- Netzwerke segmentieren
- Sicherheitsvorfälle erkennen und melden
- Dokumentation pflegen
- Benutzer unterstützen und sensibilisieren
- technische und organisatorische Maßnahmen verbinden

Ein guter FISI fragt nicht nur:

> Funktioniert das System?

sondern auch:

> Ist das System sicher, nachvollziehbar, verfügbar und passend geschützt?

---

## Kurze Zusammenfassung

Informationssicherheit schützt Informationen, Systeme und Prozesse vor unbefugtem Zugriff, Manipulation, Verlust und Ausfall.

Die wichtigsten Schutzziele sind Vertraulichkeit, Integrität und Verfügbarkeit.

Wichtige Grundlagen sind Risiken, Bedrohungen, Schwachstellen, Schutzmaßnahmen, Verantwortlichkeiten, Sicherheitsrichtlinien, Datenschutz, IT-Grundschutz und der Umgang mit Sicherheitsvorfällen.

Für FISI ist dieses Thema besonders wichtig, weil technische Systeme sicher geplant, betrieben, dokumentiert und wiederhergestellt werden müssen.
