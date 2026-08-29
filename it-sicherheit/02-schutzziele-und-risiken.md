# 2. Schutzziele und Risiken

In diesem Kapitel geht es um die wichtigsten Schutzziele der IT-Sicherheit und um typische Risiken.

Schutzziele helfen dabei zu verstehen, was genau geschützt werden soll. Risiken helfen dabei zu erkennen, welche Gefahren für Systeme, Daten und Benutzer bestehen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil man in der Praxis nicht nur Technik einrichtet, sondern auch einschätzen muss, welche Auswirkungen Fehler, Ausfälle oder falsche Berechtigungen haben können.

---

## Kurz erklärt

Die wichtigsten Schutzziele sind:

```text
Vertraulichkeit
Integrität
Verfügbarkeit
```

Diese drei Schutzziele werden oft als CIA-Triade bezeichnet.

```text
C = Confidentiality = Vertraulichkeit
I = Integrity = Integrität
A = Availability = Verfügbarkeit
```

Ein Risiko entsteht, wenn eine Bedrohung auf eine Schwachstelle trifft.

Beispiel:

```text
Bedrohung: Phishing-Mail
Schwachstelle: Benutzer erkennt Phishing nicht
Risiko: Zugangsdaten werden gestohlen
```

---

## Warum Schutzziele wichtig sind

Schutzziele helfen dabei, Sicherheitsprobleme besser einzuordnen.

Nicht jedes Problem ist gleich.

Beispiele:

```text
Eine Datei wird von Unbefugten gelesen.
Eine Datenbank wird falsch verändert.
Ein Server ist nicht erreichbar.
```

Diese drei Probleme betreffen unterschiedliche Schutzziele.

| Problem | Betroffenes Schutzziel |
|---|---|
| Unbefugter liest Daten | Vertraulichkeit |
| Daten werden verändert | Integrität |
| Server fällt aus | Verfügbarkeit |

In der Praxis können auch mehrere Schutzziele gleichzeitig betroffen sein.

---

## Vertraulichkeit

Vertraulichkeit bedeutet:

```text
Informationen dürfen nur von berechtigten Personen gelesen oder genutzt werden.
```

Beispiele:

```text
Personalakten dürfen nur von HR gelesen werden.
Kundendaten dürfen nicht öffentlich zugänglich sein.
Passwörter dürfen nicht im Klartext gespeichert werden.
Backups dürfen nicht für alle Benutzer sichtbar sein.
Admin-Zugangsdaten dürfen nicht in Dokumentationen stehen.
```

Vertraulichkeit schützt also vor unberechtigtem Zugriff auf Informationen.

---

## Maßnahmen für Vertraulichkeit

Typische Maßnahmen:

```text
Benutzerrechte
Gruppenrechte
MFA
Verschlüsselung
Need-to-know-Prinzip
sichere Passwörter
VPN
Netztrennung
Firewall-Regeln
Zugriffskontrolle
```

Beispiel:

```text
Ein normaler Benutzer darf keine Personalakten öffnen.
```

Dafür braucht man passende Berechtigungen und klare Rollen.

---

## Verletzung der Vertraulichkeit

Beispiele für Verletzungen der Vertraulichkeit:

```text
Kundendaten werden öffentlich hochgeladen.
Ein Benutzer sieht Dateien, die nicht für ihn bestimmt sind.
Ein Passwort steht in einem GitHub-Repository.
Ein Laptop mit unverschlüsselten Daten geht verloren.
Ein Backup liegt ungeschützt auf einem Netzlaufwerk.
```

Solche Fehler können technische, organisatorische und rechtliche Folgen haben.

---

## Integrität

Integrität bedeutet:

```text
Daten müssen korrekt, vollständig und unverändert bleiben.
```

Es geht nicht nur darum, dass Daten vorhanden sind, sondern dass sie auch richtig sind.

Beispiele:

```text
Rechnungsdaten dürfen nicht unbemerkt verändert werden.
Eine Konfigurationsdatei muss korrekt bleiben.
Benutzerrechte dürfen nicht falsch gesetzt werden.
Datenbankeinträge müssen fachlich stimmen.
Backups dürfen nicht beschädigt sein.
```

Wenn Integrität verletzt wird, kann man Daten nicht mehr vertrauen.

---

## Maßnahmen für Integrität

Typische Maßnahmen:

```text
Rechteverwaltung
Versionskontrolle
Backups
Prüfsummen
Logs
Datenbank-Constraints
Freigabeprozesse
Änderungsdokumentation
Vier-Augen-Prinzip
Monitoring
```

Beispiel:

```text
Eine Firewall-Regel wird geändert.
Die Änderung wird dokumentiert.
Bei Problemen kann man nachvollziehen, was geändert wurde.
```

---

## Verletzung der Integrität

Beispiele:

```text
Eine Konfigurationsdatei wird falsch geändert.
Ein Angreifer manipuliert Daten.
Eine Datenbank enthält falsche Werte.
Ein Backup ist beschädigt.
Eine Datei wird aus Versehen überschrieben.
Ein Skript löscht oder verändert falsche Daten.
```

Integritätsprobleme sind gefährlich, weil Systeme manchmal weiterlaufen, aber mit falschen Daten arbeiten.

Das kann schlimmer sein als ein klar sichtbarer Ausfall.

---

## Verfügbarkeit

Verfügbarkeit bedeutet:

```text
Systeme, Dienste und Daten müssen nutzbar sein, wenn sie gebraucht werden.
```

Beispiele:

```text
Dateiserver ist während der Arbeitszeit erreichbar.
Internetverbindung funktioniert.
Datenbank antwortet.
Benutzer können sich anmelden.
Backup kann wiederhergestellt werden.
Webserver ist online.
```

Verfügbarkeit ist besonders wichtig für Arbeitsfähigkeit und Betrieb.

---

## Maßnahmen für Verfügbarkeit

Typische Maßnahmen:

```text
Backups
Monitoring
Redundanz
USV
Wartungsfenster
Patchmanagement
Notfallplan
Hardware-Wartung
Kapazitätsplanung
Lastverteilung
Dokumentation
```

Beispiel:

```text
Ein Server fällt aus.
Ein Backup und eine klare Wiederherstellungsanleitung ermöglichen die Wiederherstellung.
```

Verfügbarkeit heißt nicht, dass nie etwas ausfallen darf.

Es bedeutet, dass Ausfälle reduziert, erkannt und behoben werden können.

---

## Verletzung der Verfügbarkeit

Beispiele:

```text
Server ist offline.
Datenbank ist nicht erreichbar.
Netzwerk fällt aus.
DNS funktioniert nicht.
Festplatte ist voll.
Ransomware verschlüsselt Daten.
Backup-Wiederherstellung funktioniert nicht.
Stromausfall legt Systeme lahm.
```

Solche Probleme können den Arbeitsbetrieb stark stören.

Bei kritischen Systemen kann ein Ausfall sehr teuer oder gefährlich werden.

---

## Zusammenhang der Schutzziele

Die Schutzziele hängen zusammen.

Ein Sicherheitsvorfall betrifft oft mehrere Ziele gleichzeitig.

Beispiel Ransomware:

```text
Verfügbarkeit: Daten sind nicht nutzbar.
Integrität: Daten wurden verändert oder verschlüsselt.
Vertraulichkeit: Daten könnten vorher kopiert worden sein.
```

Beispiel falsche Berechtigung:

```text
Vertraulichkeit: Benutzer sieht fremde Daten.
Integrität: Benutzer kann Daten verändern.
Verfügbarkeit: falsche Änderung kann Dienst stören.
```

Deshalb sollte man Sicherheitsprobleme immer ganzheitlich betrachten.

---

## Weitere Schutzziele

Neben Vertraulichkeit, Integrität und Verfügbarkeit gibt es weitere wichtige Ziele.

| Ziel | Bedeutung |
|---|---|
| Authentizität | Identität ist echt |
| Nachvollziehbarkeit | Aktionen können geprüft werden |
| Verbindlichkeit | Aktionen können nicht einfach abgestritten werden |
| Wiederherstellbarkeit | Systeme können nach Fehlern wiederhergestellt werden |
| Belastbarkeit | Systeme halten Störungen besser aus |

Diese Ziele sind in der Praxis sehr wichtig, auch wenn die CIA-Triade am bekanntesten ist.

---

## Authentizität

Authentizität bedeutet:

```text
Die Identität eines Benutzers, Systems oder einer Nachricht ist echt.
```

Beispiele:

```text
Ein Benutzer meldet sich wirklich mit seinem eigenen Konto an.
Ein Serverzertifikat gehört wirklich zur Webseite.
Eine E-Mail stammt wirklich vom angegebenen Absender.
Ein Softwarepaket kommt aus einer vertrauenswürdigen Quelle.
```

Maßnahmen:

```text
MFA
Zertifikate
digitale Signaturen
SSH-Schlüssel
vertrauenswürdige Paketquellen
Benutzerkonten ohne gemeinsame Nutzung
```

---

## Nachvollziehbarkeit

Nachvollziehbarkeit bedeutet:

```text
Aktionen können später geprüft werden.
```

Beispiele:

```text
Wer hat sich angemeldet?
Wer hat eine Datei gelöscht?
Wer hat eine Firewall-Regel geändert?
Wann wurde ein Benutzerkonto erstellt?
Wann ist ein Backup fehlgeschlagen?
```

Maßnahmen:

```text
Logging
Audit-Logs
eindeutige Benutzerkonten
Änderungsdokumentation
Ticket-Systeme
Monitoring
```

Ohne Nachvollziehbarkeit ist Fehlersuche und Sicherheitsanalyse deutlich schwerer.

---

## Verbindlichkeit

Verbindlichkeit bedeutet:

```text
Eine Aktion kann später nicht einfach abgestritten werden.
```

Beispiel:

```text
Ein Administrator ändert eine wichtige Einstellung.
Im Log steht eindeutig, welcher Account die Änderung gemacht hat.
```

Wichtig dafür:

```text
keine geteilten Admin-Konten
sichere Authentifizierung
Logging
klare Prozesse
Freigaben
```

Geteilte Konten sind schlecht für Verbindlichkeit, weil man später nicht weiß, welche Person wirklich gehandelt hat.

---

## Wiederherstellbarkeit

Wiederherstellbarkeit bedeutet:

```text
Systeme und Daten können nach einem Fehler oder Angriff wiederhergestellt werden.
```

Beispiele:

```text
Datei wurde gelöscht -> Backup wiederherstellen
Server fällt aus -> Ersatzsystem starten
Datenbank beschädigt -> Restore durchführen
Ransomware -> Systeme neu aufbauen und Daten aus sauberem Backup wiederherstellen
```

Wichtige Maßnahmen:

```text
Backups
Restore-Tests
Notfallplan
Dokumentation
Ersatzhardware
Installationsanleitungen
Automatisierung
```

Ein Backup ist nur dann wirklich wertvoll, wenn die Wiederherstellung funktioniert.

---

## Belastbarkeit

Belastbarkeit bedeutet:

```text
Systeme können Störungen besser aushalten.
```

Beispiele:

```text
Server hat genug Ressourcen.
Monitoring erkennt Probleme früh.
Systeme sind redundant aufgebaut.
Updates werden geplant durchgeführt.
Netzwerk ist sauber dokumentiert.
Backups sind getrennt gespeichert.
```

Belastbarkeit ist wichtig, damit kleine Störungen nicht direkt zu großen Ausfällen werden.

---

## Risiko

Ein Risiko beschreibt eine mögliche negative Auswirkung.

Ein Risiko entsteht oft aus:

```text
Bedrohung
Schwachstelle
Auswirkung
Wahrscheinlichkeit
```

Einfach gesagt:

```text
Was kann passieren?
Wie wahrscheinlich ist es?
Wie schlimm wäre es?
```

Beispiel:

```text
Schwaches Passwort + Phishing = Risiko für Kontoübernahme
```

---

## Bedrohung

Eine Bedrohung ist eine mögliche Gefahr.

Beispiele:

```text
Malware
Phishing
Ransomware
Hardwareausfall
Stromausfall
Fehlkonfiguration
menschlicher Fehler
Diebstahl
Brand
Wasserschaden
Social Engineering
```

Eine Bedrohung muss nicht immer absichtlich sein.

Auch ein Stromausfall oder versehentliches Löschen ist eine Bedrohung für IT-Systeme.

---

## Schwachstelle

Eine Schwachstelle ist eine Stelle, an der ein System angreifbar oder fehleranfällig ist.

Beispiele:

```text
veraltete Software
schwache Passwörter
fehlende MFA
offene Ports
zu viele Adminrechte
fehlende Backups
ungeschützte WLANs
falsche Firewall-Regeln
fehlende Dokumentation
ungetestete Wiederherstellung
```

Schwachstellen können technisch oder organisatorisch sein.

---

## Auswirkung

Die Auswirkung beschreibt, was passiert, wenn ein Risiko eintritt.

Beispiele:

```text
Datenverlust
Systemausfall
Datenschutzverletzung
Kosten
Arbeitsunterbrechung
Rufschaden
Produktionsstillstand
gestohlene Zugangsdaten
Wiederherstellungsaufwand
```

Je wichtiger ein System ist, desto größer kann die Auswirkung sein.

---

## Wahrscheinlichkeit

Wahrscheinlichkeit beschreibt, wie realistisch ein Risiko ist.

Beispiel:

```text
Ein öffentlich erreichbarer Server ohne Updates hat ein höheres Risiko als ein isoliertes Testsystem.
```

Wahrscheinlichkeit wird beeinflusst durch:

```text
Angriffsfläche
Bekanntheit der Schwachstelle
Wert der Daten
Schutzmaßnahmen
Benutzerverhalten
Systemexposition
```

---

## Risikobewertung

Eine einfache Risikobewertung kann so aussehen:

| Risiko | Wahrscheinlichkeit | Auswirkung | Bewertung |
|---|---|---|---|
| schwaches Passwort | hoch | hoch | kritisch |
| einzelner Client-Ausfall | mittel | niedrig | moderat |
| Ausfall zentraler Dateiserver | mittel | hoch | hoch |
| veralteter öffentlicher Webserver | hoch | hoch | kritisch |
| verlorener verschlüsselter Laptop | niedrig | mittel | moderat |

Die Bewertung hilft zu entscheiden, welche Maßnahmen zuerst wichtig sind.

---

## Risiko reduzieren

Risiken können auf verschiedene Weise behandelt werden.

| Umgang | Bedeutung | Beispiel |
|---|---|---|
| vermeiden | Risiko gar nicht eingehen | unsicheren Dienst nicht betreiben |
| reduzieren | Schutzmaßnahmen einsetzen | MFA aktivieren |
| übertragen | Risiko teilweise abgeben | Versicherung oder externer Dienst |
| akzeptieren | bewusst annehmen | kleines Restrisiko dokumentieren |

In der Praxis geht es oft darum, Risiken zu reduzieren.

Komplett entfernen kann man Risiken selten.

---

## Restrisiko

Restrisiko bedeutet:

```text
Ein Risiko bleibt trotz Maßnahmen bestehen.
```

Beispiel:

```text
Backups reduzieren das Risiko von Datenverlust.
Trotzdem kann ein Restore fehlschlagen, wenn Backups beschädigt sind.
```

Deshalb müssen Maßnahmen regelmäßig geprüft werden.

Sicherheit ist kein Zustand, den man einmal erreicht und dann nie wieder anfassen muss.

---

## Typische Risiken in der FISI-Praxis

| Risiko | Beispiel |
|---|---|
| schwache Passwörter | Benutzer nutzt `Sommer2026` |
| fehlende MFA | Konto wird nach Passwortdiebstahl übernommen |
| veraltete Systeme | bekannte Sicherheitslücke bleibt offen |
| falsche Rechte | Benutzer darf zu viel |
| kein Backup-Test | Wiederherstellung schlägt im Notfall fehl |
| offene Ports | Dienst ist unnötig aus dem Netzwerk erreichbar |
| falsches VLAN | Gastnetz erreicht interne Systeme |
| DNS-Fehler | interne Dienste nicht erreichbar |
| DHCP-Fehler | Clients bekommen falsche IPs |
| fehlende Dokumentation | Fehleranalyse dauert zu lange |

---

## Sicherheitsrisiko durch Fehlkonfiguration

Viele Sicherheitsprobleme entstehen nicht durch komplizierte Angriffe, sondern durch einfache Fehlkonfiguration.

Beispiele:

```text
Datenbankport öffentlich erreichbar
Firewall-Regel zu offen
Adminrechte für normale Benutzer
Standardpasswort nicht geändert
Backup-Freigabe für alle sichtbar
SSH mit schwachem Passwort offen
Docker .env-Datei in Git gespeichert
```

Fehlkonfigurationen sind besonders gefährlich, weil sie oft lange unbemerkt bleiben.

---

## Sicherheitsrisiko durch veraltete Software

Veraltete Software kann bekannte Sicherheitslücken enthalten.

Beispiele:

```text
altes Betriebssystem
ungepatchter Webserver
veraltetes CMS
alte Docker-Images
nicht aktualisierte Bibliotheken
alte Firmware auf Router oder Switch
```

Maßnahmen:

```text
regelmäßige Updates
Patchmanagement
Inventar der Systeme
Testumgebung
Wartungsfenster
Dokumentation
```

Updates müssen geplant werden, aber dauerhaftes Aufschieben ist riskant.

---

## Sicherheitsrisiko durch Benutzerrechte

Zu viele Rechte erhöhen den möglichen Schaden.

Beispiele:

```text
normaler Benutzer ist lokaler Administrator
Praktikant hat Zugriff auf alle Kundendaten
Dienstkonto hat mehr Rechte als nötig
alte Benutzerkonten bleiben aktiv
gemeinsames Admin-Konto wird genutzt
```

Maßnahmen:

```text
Least Privilege
rollenbasierte Rechte
regelmäßige Rechteprüfung
Offboarding-Prozess
eindeutige Benutzerkonten
keine gemeinsamen Admin-Konten
```

---

## Sicherheitsrisiko durch fehlende Backups

Ohne funktionierende Backups können Datenverluste sehr schwerwiegend sein.

Risiken:

```text
versehentliches Löschen
Hardwareausfall
Ransomware
fehlerhaftes Update
Datenbankfehler
Brand oder Diebstahl
```

Wichtig:

```text
Backups erstellen
Backups schützen
Backups getrennt speichern
Wiederherstellung testen
Backup-Ergebnisse überwachen
```

Ein Backup ohne Restore-Test ist nur eine Hoffnung.

---

## Sicherheitsrisiko durch Social Engineering

Social Engineering nutzt Menschen als Angriffspunkt.

Beispiele:

```text
Phishing-Mail
Anruf als angeblicher Support
USB-Stick auf Parkplatz
falscher Lieferant am Empfang
Druck durch angeblichen Chef
gefälschte Login-Seite
```

Maßnahmen:

```text
Awareness-Schulungen
klare Meldewege
MFA
keine Passwörter am Telefon
USB-Regeln
Phishing-Simulationen
Sicherheitskultur
```

Menschen sind nicht „das Problem“, aber sie brauchen klare Regeln und Unterstützung.

---

## Risikoanalyse einfach gedacht

Eine einfache Risikoanalyse kann mit diesen Fragen beginnen:

```text
Was wollen wir schützen?
Welche Bedrohungen gibt es?
Welche Schwachstellen haben wir?
Wie wahrscheinlich ist das?
Wie schlimm wäre der Schaden?
Welche Maßnahmen gibt es?
Wer ist verantwortlich?
Wie dokumentieren wir das?
```

Diese Fragen helfen, IT-Sicherheit strukturiert zu betrachten.

---

## Beispiel Risikoanalyse: Dateiserver

System:

```text
Dateiserver mit wichtigen Abteilungsdaten
```

Mögliche Risiken:

| Risiko | Schutzziel | Maßnahme |
|---|---|---|
| unberechtigter Zugriff | Vertraulichkeit | Gruppenrechte, MFA, Logging |
| versehentliche Löschung | Integrität/Verfügbarkeit | Backups, Papierkorb, Berechtigungen |
| Hardwareausfall | Verfügbarkeit | RAID, Backup, Monitoring |
| Ransomware | Verfügbarkeit/Integrität | Offline-Backup, Rechte begrenzen, Updates |
| falsche Rechte | Vertraulichkeit | regelmäßige Rechteprüfung |

---

## Beispiel Risikoanalyse: Webserver

System:

```text
öffentlicher Webserver
```

Mögliche Risiken:

| Risiko | Schutzziel | Maßnahme |
|---|---|---|
| bekannte Sicherheitslücke | Integrität/Vertraulichkeit | Updates, Patchmanagement |
| DDoS oder Überlastung | Verfügbarkeit | Monitoring, Schutzdienste, Skalierung |
| falsche Konfiguration | Vertraulichkeit | sichere Defaults, Review |
| unverschlüsselter Zugriff | Vertraulichkeit | HTTPS |
| Log-Dateien öffentlich | Vertraulichkeit | Rechte prüfen |

---

## Beispiel Risikoanalyse: Laptop

System:

```text
Firmenlaptop
```

Mögliche Risiken:

| Risiko | Schutzziel | Maßnahme |
|---|---|---|
| Laptop verloren | Vertraulichkeit | Festplattenverschlüsselung |
| schwaches Passwort | Vertraulichkeit | MFA, Passwortrichtlinie |
| veraltete Software | Integrität/Vertraulichkeit | Updates |
| keine Backups | Verfügbarkeit | Cloud- oder Netzbackup |
| öffentliches WLAN | Vertraulichkeit | VPN, sichere Verbindungen |

---

## Zusammenhang mit Schutzbedarf

In Unternehmen wird oft bewertet, wie hoch der Schutzbedarf eines Systems ist.

Schutzbedarf kann zum Beispiel sein:

```text
normal
hoch
sehr hoch
```

Ein System mit sehr sensiblen Daten braucht stärkere Schutzmaßnahmen als ein unkritisches Testsystem.

Beispiel:

```text
Personalakte -> hoher Schutzbedarf
öffentliches Infoblatt -> niedrigerer Schutzbedarf
zentrale Datenbank -> hoher Schutzbedarf
Test-VM ohne echte Daten -> niedrigerer Schutzbedarf
```

Der Schutzbedarf beeinflusst die Maßnahmen.

---

## Priorisierung von Maßnahmen

Nicht jede Maßnahme ist gleich dringend.

Man sollte zuerst die größten Risiken reduzieren.

Beispiele für hohe Priorität:

```text
kritische Updates auf öffentlich erreichbaren Systemen
MFA für Admin-Konten
funktionierende Backups
offene Datenbankports schließen
alte Benutzerkonten deaktivieren
Firewall-Regeln prüfen
```

Eine gute Priorisierung spart Zeit und reduziert reale Risiken schneller.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| nur auf Hackerangriffe achten | Ausfälle und Fehlkonfiguration werden vergessen |
| Verfügbarkeit ignorieren | Systeme fallen aus und Arbeit stoppt |
| Backups als reine IT-Routine sehen | Restore wird nicht getestet |
| alle Risiken gleich behandeln | wichtige Risiken werden zu spät bearbeitet |
| Schutzziele nicht trennen | Ursache und Maßnahme bleiben unklar |
| zu viele Rechte vergeben | Schaden bei Fehlern wird größer |
| keine Dokumentation | Risiko bleibt unsichtbar |
| alte Systeme vergessen | bekannte Lücken bleiben offen |
| Benutzer nicht schulen | Phishing bleibt leicht erfolgreich |
| Restrisiko nicht akzeptieren/dokumentieren | falsches Sicherheitsgefühl |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Schutzzielen und Risiken:

```text
Systeme und Daten erfassen
Schutzziele bestimmen
Risiken erkennen
Schwachstellen prüfen
Auswirkungen bewerten
Maßnahmen auswählen
Verantwortliche festlegen
Maßnahmen dokumentieren
regelmäßig prüfen
```

Wichtig:

```text
Sicherheit soll zur Realität passen.
```

Ein kleines Testsystem braucht nicht dieselben Maßnahmen wie ein produktiver Server mit Kundendaten.

Aber auch Testsysteme dürfen nicht völlig unsicher betrieben werden.

---

## Praktische Fragen für FISI

Bei jedem System kann man sich fragen:

```text
Welche Daten liegen hier?
Wer braucht Zugriff?
Was passiert, wenn das System ausfällt?
Was passiert, wenn Daten verändert werden?
Was passiert, wenn Unbefugte Zugriff bekommen?
Gibt es Backups?
Sind Updates geregelt?
Sind Rechte sauber gesetzt?
Gibt es Logs?
Ist das System dokumentiert?
```

Diese Fragen helfen bei Planung, Betrieb und Fehlersuche.

---

## FISI-Bezug

Schutzziele und Risiken sind für FISI wichtig, weil technische Entscheidungen immer Auswirkungen auf Sicherheit haben.

Man braucht dieses Wissen für:

```text
Serverbetrieb
Benutzerverwaltung
Netzwerkplanung
Backup-Konzepte
Firewall-Regeln
Docker-Umgebungen
Virtualisierung
Support
Dokumentation
Datenschutz
Incident Response
```

Ein FISI muss Risiken nicht nur theoretisch kennen.

Er muss in der Praxis erkennen, ob eine Konfiguration gefährlich ist und welche Maßnahme sinnvoll wäre.

---

## Kurze Zusammenfassung

Die wichtigsten Schutzziele sind Vertraulichkeit, Integrität und Verfügbarkeit.

Vertraulichkeit schützt vor unberechtigtem Lesen.  
Integrität schützt vor unbemerkter Veränderung.  
Verfügbarkeit schützt die Nutzbarkeit von Systemen und Daten.

Risiken entstehen durch Bedrohungen, Schwachstellen, Wahrscheinlichkeit und Auswirkungen.

Typische Risiken sind schwache Passwörter, fehlende MFA, veraltete Software, falsche Rechte, fehlende Backups, offene Ports, Fehlkonfiguration und Social Engineering.

Für FISI ist dieses Thema wichtig, weil man Systeme nicht nur funktionsfähig, sondern auch sicher und nachvollziehbar betreiben muss.