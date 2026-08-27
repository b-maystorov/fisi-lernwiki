# IT-Sicherheit

In diesem Bereich geht es um wichtige Grundlagen der IT-Sicherheit.

IT-Sicherheit bedeutet nicht nur, ein Antivirenprogramm zu installieren. Es geht darum, Systeme, Daten, Benutzerkonten, Netzwerke und Dienste so zu schützen, dass sie zuverlässig und kontrolliert genutzt werden können.

Für Fachinformatiker für Systemintegration ist IT-Sicherheit ein sehr wichtiges Thema, weil man in der Praxis mit Benutzerrechten, Passwörtern, Updates, Firewalls, Backups, Zugriffen, Protokollen, Datenschutz und Sicherheitsvorfällen zu tun hat.

---

## Kurz erklärt

IT-Sicherheit schützt IT-Systeme vor Schäden, Missbrauch, Ausfall und unberechtigtem Zugriff.

Typische Schutzbereiche:

```text
Benutzerkonten
Passwörter
Server
Clients
Netzwerke
Datenbanken
Dateien
Backups
Dienste
Cloud-Systeme
WLAN
Docker-Container
virtuelle Maschinen
```

Wichtige Fragen:

```text
Wer darf auf welche Daten zugreifen?
Wie werden Systeme aktuell gehalten?
Wie werden Daten gesichert?
Wie werden Angriffe erkannt?
Wie werden Fehler dokumentiert?
Wie wird nach einem Vorfall reagiert?
```

---

## Kapitelübersicht

| Kapitel                                                                                       | Thema                                                                 |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| [1. IT-Sicherheit Grundlagen](./01-it-sicherheit-grundlagen.md)                               | Grundbegriffe, Ziele und Bedeutung von IT-Sicherheit                  |
| [2. Schutzziele und Risiken](./02-schutzziele-und-risiken.md)                                 | Vertraulichkeit, Integrität, Verfügbarkeit und typische Risiken       |
| [3. Passwörter, Authentifizierung und Zugriff](./03-passwoerter-authentifizierung-zugriff.md) | Benutzerkonten, Rechte, MFA, Rollen und Zugriffskontrolle             |
| [4. Firewall, Updates und Backup](./04-firewall-updates-backup.md)                            | technische Schutzmaßnahmen im Alltag                                  |
| [5. Malware, Phishing und Social Engineering](./05-malware-phishing-social-engineering.md)    | typische Angriffe und menschliche Faktoren                            |
| [6. Datenschutz und Dokumentation](./06-datenschutz-und-dokumentation.md)                     | personenbezogene Daten, Nachvollziehbarkeit und saubere Dokumentation |
| [7. IT-Sicherheit in der FISI-Praxis](./07-it-sicherheit-in-der-fisi-praxis.md)               | praktische Aufgaben, typische Fehler und sichere Arbeitsweise         |

---

## Warum IT-Sicherheit wichtig ist

IT-Systeme sind heute ein zentraler Teil von Unternehmen, Schulen, Behörden und privaten Haushalten.

Wenn IT-Systeme ausfallen oder kompromittiert werden, kann das viele Folgen haben:

```text
Datenverlust
Arbeitsausfall
finanzieller Schaden
Datenschutzverletzungen
Rufschaden
Produktionsausfall
gestohlene Zugangsdaten
verschlüsselte Systeme durch Ransomware
unberechtigter Zugriff auf interne Systeme
```

IT-Sicherheit soll solche Risiken reduzieren.

Sie kann Risiken nicht komplett entfernen, aber sie kann Schäden unwahrscheinlicher machen und Auswirkungen begrenzen.

---

## Wichtige Schutzziele

In der IT-Sicherheit gibt es drei besonders wichtige Schutzziele.

| Schutzziel      | Bedeutung                                                 | Beispiel                                           |
| --------------- | --------------------------------------------------------- | -------------------------------------------------- |
| Vertraulichkeit | Daten dürfen nur von berechtigten Personen gelesen werden | Personalakten sind nur für HR sichtbar             |
| Integrität      | Daten dürfen nicht unbemerkt verändert werden             | Rechnungsdaten bleiben korrekt                     |
| Verfügbarkeit   | Systeme und Daten müssen nutzbar sein                     | Dateiserver ist während der Arbeitszeit erreichbar |

Diese drei Ziele werden oft als CIA-Triade bezeichnet.

```text
C = Confidentiality = Vertraulichkeit
I = Integrity = Integrität
A = Availability = Verfügbarkeit
```

---

## Weitere wichtige Ziele

Neben Vertraulichkeit, Integrität und Verfügbarkeit gibt es weitere wichtige Ziele.

| Ziel                  | Bedeutung                                              |
| --------------------- | ------------------------------------------------------ |
| Authentizität         | Identität eines Benutzers oder Systems ist echt        |
| Nachvollziehbarkeit   | Aktionen können später geprüft werden                  |
| Verbindlichkeit       | Aktionen können nicht einfach abgestritten werden      |
| Belastbarkeit         | Systeme halten Störungen besser aus                    |
| Wiederherstellbarkeit | Systeme können nach Ausfällen wiederhergestellt werden |

Diese Ziele sind besonders wichtig bei Protokollen, Benutzerkonten, Backups und Sicherheitsvorfällen.

---

## Typische Risiken

IT-Systeme können durch viele Dinge gefährdet werden.

| Risiko              | Beispiel                                         |
| ------------------- | ------------------------------------------------ |
| Malware             | Schadsoftware verschlüsselt Dateien              |
| Phishing            | Benutzer gibt Passwort auf falscher Webseite ein |
| schwache Passwörter | Passwort wird erraten                            |
| fehlende Updates    | bekannte Sicherheitslücke bleibt offen           |
| falsche Rechte      | Benutzer darf zu viel                            |
| Datenverlust        | keine funktionierenden Backups                   |
| Fehlkonfiguration   | Dienst ist öffentlich erreichbar                 |
| Hardwareausfall     | Serverfestplatte fällt aus                       |
| menschlicher Fehler | falsche Datei gelöscht                           |
| Social Engineering  | Angreifer täuscht Mitarbeiter                    |

Nicht jedes Risiko ist ein Hackerangriff. Viele Sicherheitsprobleme entstehen durch schlechte Konfiguration, fehlende Dokumentation oder menschliche Fehler.

---

## Technische Maßnahmen

Technische Maßnahmen sind Schutzmaßnahmen, die direkt an Systemen, Netzwerken oder Anwendungen umgesetzt werden.

Beispiele:

```text
Firewall
Updates
Antivirus/Endpoint Protection
Verschlüsselung
Backups
MFA
VPN
Benutzerrechte
Logging
Monitoring
Netztrennung durch VLANs
Patchmanagement
```

Technische Maßnahmen sind wichtig, aber sie reichen allein nicht aus.

---

## Organisatorische Maßnahmen

Organisatorische Maßnahmen regeln Abläufe, Zuständigkeiten und Verhalten.

Beispiele:

```text
Passwortrichtlinie
Backup-Konzept
Berechtigungskonzept
Notfallplan
Schulung der Mitarbeiter
Dokumentationspflicht
Freigabeprozesse
Rollenverteilung
Incident-Response-Prozess
Onboarding und Offboarding
```

Viele Sicherheitsprobleme entstehen, weil Abläufe nicht klar geregelt sind.

---

## TOMs

TOMs bedeutet:

```text
Technische und organisatorische Maßnahmen
```

TOMs sind Maßnahmen zum Schutz von Daten und Systemen.

Beispiele:

| Bereich         | Maßnahme                          |
| --------------- | --------------------------------- |
| technisch       | Firewall, Verschlüsselung, Backup |
| organisatorisch | Richtlinien, Schulungen, Rollen   |
| physisch        | Zutrittskontrolle, Serverraum     |
| administrativ   | Benutzerrechte, Dokumentation     |

In der Praxis gehören technische und organisatorische Maßnahmen zusammen.

Eine Firewall hilft wenig, wenn jeder Benutzer Adminrechte hat.  
Ein Backup hilft wenig, wenn niemand prüft, ob es wiederherstellbar ist.

---

## Least Privilege

Ein wichtiges Sicherheitsprinzip ist:

```text
Least Privilege
```

Das bedeutet:

```text
Jeder Benutzer und jeder Dienst bekommt nur die Rechte, die wirklich benötigt werden.
```

Beispiel:

```text
Ein normaler Benutzer braucht keine Administratorrechte.
Ein Webdienst braucht keinen Zugriff auf private Benutzerdateien.
Ein Praktikant braucht keinen Zugriff auf alle Kundendaten.
```

Dieses Prinzip reduziert Schäden, wenn ein Konto oder Dienst kompromittiert wird.

---

## Need-to-know-Prinzip

Das Need-to-know-Prinzip bedeutet:

```text
Benutzer bekommen nur Zugriff auf Informationen, die sie für ihre Aufgabe brauchen.
```

Beispiel:

```text
HR sieht Personalakten.
IT sieht technische Systeminformationen.
Marketing sieht Kampagnendaten.
Gäste sehen keine internen Daten.
```

Dieses Prinzip schützt vor unnötigem Datenzugriff.

---

## Authentifizierung und Autorisierung

Diese Begriffe werden oft verwechselt.

| Begriff            | Bedeutung        | Beispiel                   |
| ------------------ | ---------------- | -------------------------- |
| Authentifizierung  | Wer bist du?     | Login mit Passwort         |
| Autorisierung      | Was darfst du?   | Zugriff auf Ordner erlaubt |
| Accounting/Logging | Was wurde getan? | Login wird protokolliert   |

Beispiel:

```text
Benutzer meldet sich an.
System prüft Identität.
System prüft Berechtigungen.
System protokolliert Zugriff.
```

---

## Passwörter und MFA

Passwörter sind ein häufiger Angriffspunkt.

Sichere Passwörter sollten:

```text
lang sein
nicht mehrfach verwendet werden
nicht leicht zu erraten sein
nicht öffentlich geteilt werden
nicht in Klartext gespeichert werden
```

MFA bedeutet:

```text
Multi-Factor Authentication
```

Dabei wird mehr als ein Faktor genutzt.

Beispiele:

```text
Passwort + App-Code
Passwort + Hardware-Key
Passwort + biometrischer Faktor
```

MFA erhöht die Sicherheit deutlich, weil ein gestohlenes Passwort allein nicht ausreicht.

---

## Updates und Patchmanagement

Updates schließen Fehler und Sicherheitslücken.

Patchmanagement bedeutet:

```text
Updates planen
Updates testen
Updates ausrollen
Systeme danach prüfen
Änderungen dokumentieren
```

Fehlende Updates sind ein häufiger Grund für Sicherheitsvorfälle.

Wichtig:

```text
Nicht jedes Update blind installieren.
Nicht alle Updates ewig aufschieben.
```

In der Praxis braucht man einen sauberen Prozess.

---

## Firewalls

Eine Firewall kontrolliert Netzwerkverkehr.

Sie entscheidet, welcher Datenverkehr erlaubt oder blockiert wird.

Beispiele:

```text
SSH erlauben
HTTP/HTTPS erlauben
Datenbankport blockieren
Gastnetz vom internen Netz trennen
nur bestimmte IP-Adressen erlauben
```

Eine Firewall ist wichtig, aber sie ersetzt keine anderen Sicherheitsmaßnahmen.

Wichtig:

```text
Firewall-Regeln müssen dokumentiert werden.
Nur notwendige Ports sollten geöffnet sein.
```

---

## Backups

Backups sind eine der wichtigsten Sicherheitsmaßnahmen.

Sie schützen gegen:

```text
Datenverlust
versehentliches Löschen
Hardwareausfall
Ransomware
fehlerhafte Updates
Fehlkonfiguration
```

Wichtig ist nicht nur das Erstellen von Backups.

Wichtig ist auch:

```text
Backups regelmäßig testen.
Wiederherstellung dokumentieren.
Backups getrennt aufbewahren.
Zugriff auf Backups schützen.
```

Ein Backup, das nie getestet wurde, ist unsicher.

---

## Logging und Monitoring

Logging bedeutet:

```text
Ereignisse werden protokolliert.
```

Monitoring bedeutet:

```text
Systemzustände werden überwacht.
```

Beispiele für Logs:

```text
Login-Versuche
Dienstfehler
Firewall-Blockierungen
Systemstarts
fehlgeschlagene SSH-Anmeldungen
Backup-Ergebnisse
```

Logs helfen, Fehler und Angriffe nachzuvollziehen.

Wichtig:

```text
Logs müssen geschützt werden.
Logs müssen lesbar und auswertbar sein.
```

---

## Netzwerksicherheit

Netzwerksicherheit schützt Kommunikation und Zugriffe.

Wichtige Themen:

```text
Firewall
VLANs
VPN
WLAN-Verschlüsselung
Netztrennung
Portfreigaben
DNS-Sicherheit
DHCP-Kontrolle
Monitoring
Gastnetz
Management-Netz
```

Beispiel:

```text
Gäste-WLAN darf ins Internet.
Gäste-WLAN darf nicht auf Server-VLAN.
Management-Zugriff nur für Admins.
```

Netztrennung ist eine wichtige Sicherheitsmaßnahme.

---

## Sicherheit bei Linux

Linux-Systeme müssen ebenfalls sicher betrieben werden.

Wichtige Punkte:

```text
regelmäßige Updates
nur notwendige Dienste aktivieren
SSH absichern
Firewall prüfen
Benutzerrechte sauber setzen
sudo bewusst nutzen
Logs kontrollieren
Dateirechte prüfen
Backups einrichten
Dienste überwachen
```

Beispiele:

```bash
sudo apt update
sudo apt upgrade
sudo ufw status
ss -tulpen
systemctl status ssh
journalctl -u ssh
```

---

## Sicherheit bei Docker

Docker bringt eigene Sicherheitsfragen mit.

Wichtige Punkte:

```text
keine Secrets in Git speichern
nur notwendige Ports veröffentlichen
Container nicht unnötig als root betreiben
Images aktuell halten
Volumes bewusst nutzen
.env-Dateien schützen
Netzwerke trennen
Logs prüfen
```

Typischer Fehler:

```text
Datenbankport wird unnötig auf dem Host veröffentlicht.
```

Besser:

```text
Datenbank bleibt nur im Docker-Netz erreichbar.
Admin-Oberfläche wird bewusst begrenzt.
```

---

## Sicherheit bei Virtualisierung

Virtuelle Maschinen müssen wie echte Systeme behandelt werden.

Wichtige Punkte:

```text
VMs aktualisieren
Netzwerkmodus bewusst wählen
Snapshots nicht mit Backups verwechseln
Zugriffe dokumentieren
SSH und Firewall prüfen
Ressourcen überwachen
VMs sauber benennen
```

NAT, Bridge und Host-only haben unterschiedliche Sicherheitswirkungen.

Beispiel:

```text
Bridge macht eine VM wie ein eigenes Gerät im LAN sichtbar.
NAT versteckt die VM eher hinter dem Host.
```

---

## Datenschutz

Datenschutz schützt personenbezogene Daten.

Personenbezogene Daten sind Informationen, die sich auf eine Person beziehen.

Beispiele:

```text
Name
Adresse
E-Mail-Adresse
Telefonnummer
Kundennummer
IP-Adresse
Geburtsdatum
Personalnummer
Login-Name
```

In der Praxis bedeutet Datenschutz:

```text
nur notwendige Daten verarbeiten
Zugriffe begrenzen
Daten sicher speichern
Daten nicht unnötig teilen
Löschfristen beachten
Vorfälle melden
```

---

## Sicherheitsvorfälle

Ein Sicherheitsvorfall ist ein Ereignis, das die Sicherheit eines Systems oder von Daten gefährdet.

Beispiele:

```text
gestohlene Zugangsdaten
Malware-Fund
Ransomware
unberechtigter Zugriff
verlorener Laptop
Daten versehentlich veröffentlicht
Firewall-Regel falsch gesetzt
Admin-Konto kompromittiert
```

Wichtig ist ein strukturierter Umgang.

Nicht hektisch handeln, sondern:

```text
Vorfall erkennen
Auswirkungen begrenzen
Beweise sichern
zuständige Personen informieren
Systeme analysieren
Ursache beheben
Systeme wiederherstellen
Vorfall dokumentieren
Verbesserungen ableiten
```

---

## Typische Fehler

| Fehler                             | Problem                            |
| ---------------------------------- | ---------------------------------- |
| gleiche Passwörter mehrfach nutzen | ein Leak gefährdet mehrere Konten  |
| keine MFA nutzen                   | Passwortdiebstahl reicht aus       |
| Updates ignorieren                 | bekannte Lücken bleiben offen      |
| Backups nie testen                 | Wiederherstellung ist unsicher     |
| alle Benutzer haben Adminrechte    | hoher Schaden bei Kompromittierung |
| Ports unnötig öffnen               | Angriffsfläche wird größer         |
| Logs nicht prüfen                  | Angriffe bleiben unbemerkt         |
| Daten in Git speichern             | Secrets können öffentlich werden   |
| Gastnetz nicht trennen             | interne Systeme gefährdet          |
| Dokumentation fehlt                | Fehler wiederholen sich            |

---

## Gute Arbeitsweise

Eine sichere Arbeitsweise bedeutet:

```text
bewusst konfigurieren
nur notwendige Rechte vergeben
Änderungen dokumentieren
Updates planen
Backups testen
Logs prüfen
Zugriffe begrenzen
Passwörter schützen
MFA nutzen
Fehler offen dokumentieren
```

Wichtig:

```text
Sicherheit ist kein einmaliger Schritt.
Sicherheit ist ein laufender Prozess.
```

Systeme ändern sich, Benutzer ändern sich, Software ändert sich und Angriffe ändern sich.

---

## FISI-Bezug

IT-Sicherheit gehört direkt zur Arbeit eines Fachinformatikers für Systemintegration.

In der Praxis braucht man Sicherheitswissen für:

- Benutzerkonten und Rechte verwalten
- Server sicher betreiben
- Clients absichern
- Firewalls verstehen
- Updates planen
- Backups einrichten und prüfen
- Netzwerke trennen
- WLAN sicher konfigurieren
- Docker- und VM-Umgebungen sicher betreiben
- Logs lesen
- Sicherheitsvorfälle dokumentieren
- Datenschutz beachten
- technische Dokumentation schreiben

Ein FISI muss nicht alles wie ein Security-Spezialist können, aber er muss sicherheitsbewusst arbeiten und Risiken erkennen.

---

## Praktische Lernziele

Nach diesem Bereich sollte man erklären können:

```text
was IT-Sicherheit bedeutet
was Vertraulichkeit, Integrität und Verfügbarkeit sind
warum Passwörter und MFA wichtig sind
warum Benutzerrechte begrenzt werden müssen
warum Updates und Backups wichtig sind
wie Firewalls grundsätzlich schützen
was Malware und Phishing sind
warum Datenschutz wichtig ist
wie man Sicherheitsprobleme dokumentiert
wie IT-Sicherheit mit Linux, Netzwerken, Docker und VMs zusammenhängt
```

---

## Kurze Zusammenfassung

IT-Sicherheit schützt Systeme, Daten und Benutzer vor Ausfall, Missbrauch und unberechtigtem Zugriff.

Wichtige Grundlagen sind Vertraulichkeit, Integrität, Verfügbarkeit, Authentifizierung, Autorisierung, Least Privilege, Firewalls, Updates, Backups, Logging, Monitoring, Datenschutz und sichere Dokumentation.

Für FISI ist IT-Sicherheit besonders wichtig, weil viele praktische Aufgaben direkt mit Benutzerrechten, Serverdiensten, Netzwerken, Firewalls, Updates, Backups und Fehlersuche zusammenhängen.

Sicherheit ist kein einzelnes Tool, sondern eine saubere Arbeitsweise.
