# 1. IT-Sicherheit Grundlagen

In diesem Kapitel geht es um die Grundlagen der IT-Sicherheit.

IT-Sicherheit bedeutet, IT-Systeme, Daten, Netzwerke, Benutzerkonten und Dienste vor Ausfall, Missbrauch, Manipulation und unberechtigtem Zugriff zu schützen.

Für Fachinformatiker für Systemintegration ist IT-Sicherheit ein wichtiges Alltagsthema. Man arbeitet mit Benutzerrechten, Servern, Clients, Netzwerken, Firewalls, Backups, Updates, Logs und Dokumentation. Fast jede technische Entscheidung hat auch eine Sicherheitsseite.

---

## Kurz erklärt

IT-Sicherheit schützt:

```text
Daten
Systeme
Benutzerkonten
Netzwerke
Server
Clients
Dienste
Backups
Zugriffe
Konfigurationen
```

Ziel ist nicht, jedes Risiko komplett zu entfernen. Das ist in der Praxis kaum möglich.

Ziel ist:

```text
Risiken erkennen
Risiken reduzieren
Schäden begrenzen
Systeme kontrolliert betreiben
Fehler nachvollziehen
im Notfall reagieren können
```

---

## Warum IT-Sicherheit wichtig ist

Unternehmen, Schulen, Behörden und private Personen sind stark von IT abhängig.

Wenn IT-Systeme nicht sicher betrieben werden, können viele Probleme entstehen:

```text
Datenverlust
Systemausfall
gestohlene Passwörter
unberechtigter Zugriff
verschlüsselte Daten durch Ransomware
veröffentlichte Kundendaten
Ausfall von Arbeitsplätzen
Ausfall von Serverdiensten
finanzieller Schaden
Rufschaden
rechtliche Probleme
```

IT-Sicherheit ist deshalb nicht nur ein technisches Thema. Sie betrifft auch Organisation, Kommunikation, Prozesse und Verantwortung.

---

## IT-Sicherheit ist mehr als Antivirus

Viele denken bei IT-Sicherheit zuerst an Antivirus oder Hackerangriffe.

Das ist aber nur ein kleiner Teil.

IT-Sicherheit umfasst auch:

```text
Benutzerrechte
Passwortrichtlinien
Updates
Backups
Firewall-Regeln
Netztrennung
Verschlüsselung
Logging
Monitoring
Dokumentation
Datenschutz
Notfallplanung
Schulung von Benutzern
sichere Konfiguration
```

Ein System kann ein Antivirenprogramm haben und trotzdem unsicher sein, wenn zum Beispiel alle Benutzer Administratorrechte haben oder keine Backups existieren.

---

## Grundidee von Sicherheit

Sicherheit bedeutet in der IT meistens:

```text
Nur berechtigte Personen dürfen auf Daten zugreifen.
Daten dürfen nicht unbemerkt verändert werden.
Systeme müssen verfügbar bleiben.
Fehler und Angriffe müssen erkennbar sein.
Schäden müssen begrenzt werden.
```

Dafür braucht man technische und organisatorische Maßnahmen.

Beispiel:

```text
Technisch: Firewall blockiert unnötige Ports.
Organisatorisch: Es gibt eine Regel, wer Firewall-Änderungen freigeben darf.
```

Beides gehört zusammen.

---

## Wichtige Schutzziele

Die drei wichtigsten Schutzziele sind:

```text
Vertraulichkeit
Integrität
Verfügbarkeit
```

Diese drei Ziele werden oft als CIA-Triade bezeichnet.

| Begriff         | Englisch        | Bedeutung                                                 |
| --------------- | --------------- | --------------------------------------------------------- |
| Vertraulichkeit | Confidentiality | Daten dürfen nur von berechtigten Personen gelesen werden |
| Integrität      | Integrity       | Daten dürfen nicht unbemerkt verändert werden             |
| Verfügbarkeit   | Availability    | Systeme und Daten müssen nutzbar sein                     |

---

## Vertraulichkeit

Vertraulichkeit bedeutet:

```text
Informationen dürfen nur von berechtigten Personen gesehen werden.
```

Beispiele:

```text
Personalakten dürfen nur von HR gelesen werden.
Kundendaten dürfen nicht öffentlich zugänglich sein.
Passwörter dürfen nicht im Klartext gespeichert werden.
Backups dürfen nicht frei für alle erreichbar sein.
```

Maßnahmen für Vertraulichkeit:

```text
Benutzerrechte
Verschlüsselung
MFA
Zugriffskontrolle
Netztrennung
sichere Passwörter
Need-to-know-Prinzip
```

---

## Integrität

Integrität bedeutet:

```text
Daten müssen korrekt, vollständig und unverändert bleiben.
```

Beispiele:

```text
Eine Rechnung darf nicht unbemerkt verändert werden.
Eine Konfigurationsdatei muss korrekt bleiben.
Ein Backup darf nicht beschädigt sein.
Eine Datenbank darf keine falschen Werte enthalten.
```

Maßnahmen für Integrität:

```text
Rechteverwaltung
Versionskontrolle
Prüfsummen
Logs
Backups
Datenbank-Constraints
Freigabeprozesse
Dokumentation von Änderungen
```

Integrität ist besonders wichtig, weil falsche Daten zu falschen Entscheidungen führen können.

---

## Verfügbarkeit

Verfügbarkeit bedeutet:

```text
Systeme, Dienste und Daten müssen erreichbar sein, wenn sie gebraucht werden.
```

Beispiele:

```text
Dateiserver ist während der Arbeitszeit erreichbar.
Datenbank ist für Anwendungen verfügbar.
Internetverbindung funktioniert.
Backup kann wiederhergestellt werden.
Benutzer können sich anmelden.
```

Maßnahmen für Verfügbarkeit:

```text
Backups
Monitoring
USV
Redundanz
Updates mit Planung
Notfallkonzept
Hardware-Wartung
Logging
Kapazitätsplanung
```

Verfügbarkeit heißt nicht, dass nie etwas ausfallen darf. Es bedeutet, dass Systeme sinnvoll geplant, überwacht und wiederherstellbar sind.

---

## Weitere Sicherheitsziele

Neben Vertraulichkeit, Integrität und Verfügbarkeit gibt es weitere wichtige Ziele.

| Ziel                  | Bedeutung                                            |
| --------------------- | ---------------------------------------------------- |
| Authentizität         | Identität von Benutzer oder System ist echt          |
| Nachvollziehbarkeit   | Aktionen können später geprüft werden                |
| Verbindlichkeit       | Aktionen können nicht einfach abgestritten werden    |
| Wiederherstellbarkeit | Systeme können nach Fehlern wiederhergestellt werden |
| Belastbarkeit         | Systeme halten Störungen besser aus                  |

Beispiel:

```text
Ein Admin ändert eine Firewall-Regel.
Die Änderung wird protokolliert.
Später kann nachvollzogen werden, wer was geändert hat.
```

Das ist wichtig für Kontrolle, Fehleranalyse und Verantwortung.

---

## Bedrohung, Risiko und Schwachstelle

Diese Begriffe werden oft verwechselt.

| Begriff       | Bedeutung                                           | Beispiel                          |
| ------------- | --------------------------------------------------- | --------------------------------- |
| Bedrohung     | mögliche Gefahr                                     | Phishing-Angriff                  |
| Schwachstelle | offene Lücke oder Fehler                            | Benutzer nutzt schwaches Passwort |
| Risiko        | mögliche Auswirkung aus Bedrohung und Schwachstelle | Konto wird übernommen             |

Einfach gesagt:

```text
Bedrohung = Was kann passieren?
Schwachstelle = Wo sind wir angreifbar?
Risiko = Wie schlimm und wahrscheinlich ist es?
```

---

## Beispiel Bedrohung, Schwachstelle und Risiko

Beispiel:

```text
Bedrohung: Angreifer verschickt Phishing-Mail.
Schwachstelle: Benutzer erkennt die Mail nicht und MFA ist nicht aktiv.
Risiko: Zugangsdaten werden gestohlen und Konto wird übernommen.
```

Mögliche Maßnahmen:

```text
MFA aktivieren
Benutzer schulen
Spamfilter nutzen
Login-Versuche überwachen
Passwortrichtlinie einführen
```

Dadurch wird das Risiko reduziert.

---

## Sicherheitsmaßnahmen

Sicherheitsmaßnahmen können unterschiedlich sein.

Typische Gruppen:

```text
technische Maßnahmen
organisatorische Maßnahmen
physische Maßnahmen
personelle Maßnahmen
```

Beispiele:

| Gruppe          | Beispiele                                 |
| --------------- | ----------------------------------------- |
| technisch       | Firewall, MFA, Updates, Verschlüsselung   |
| organisatorisch | Richtlinien, Prozesse, Freigaben          |
| physisch        | Serverraum abschließen, Zutrittskontrolle |
| personell       | Schulungen, Rollen, Verantwortlichkeiten  |

Gute IT-Sicherheit kombiniert mehrere Arten von Maßnahmen.

---

## Technische Maßnahmen

Technische Maßnahmen werden direkt an Systemen, Netzwerken oder Anwendungen umgesetzt.

Beispiele:

```text
Firewall aktivieren
Updates installieren
MFA aktivieren
SSH absichern
Backups erstellen
Daten verschlüsseln
Ports schließen
Dienste deaktivieren
Logs sammeln
Monitoring einrichten
VLANs nutzen
VPN verwenden
```

Technische Maßnahmen sind wichtig, aber sie lösen nicht jedes Problem allein.

Eine Firewall hilft wenig, wenn Passwörter öffentlich in GitHub stehen.

---

## Organisatorische Maßnahmen

Organisatorische Maßnahmen regeln Abläufe und Zuständigkeiten.

Beispiele:

```text
Wer darf neue Benutzer anlegen?
Wer darf Adminrechte vergeben?
Wie werden Backups geprüft?
Wie werden Updates geplant?
Wie werden Sicherheitsvorfälle gemeldet?
Wie wird dokumentiert?
Wie läuft Offboarding?
```

Ohne klare Organisation entstehen oft Sicherheitslücken.

Beispiel:

```text
Ein Mitarbeiter verlässt die Firma.
Das Konto wird nicht deaktiviert.
Der Zugriff bleibt bestehen.
```

Das ist kein technischer Fehler allein, sondern auch ein Prozessproblem.

---

## Physische Sicherheit

Physische Sicherheit schützt Geräte und Räume.

Beispiele:

```text
Serverraum abschließen
Zutritt nur für berechtigte Personen
Laptops nicht unbeaufsichtigt lassen
Bildschirm sperren
Netzwerkschränke sichern
Backup-Datenträger geschützt lagern
USV gegen Stromausfall nutzen
```

Auch ein perfekt konfigurierter Server ist gefährdet, wenn jeder physischen Zugriff darauf hat.

---

## Menschlicher Faktor

Viele Sicherheitsprobleme entstehen durch menschliche Fehler.

Beispiele:

```text
Phishing-Mail geöffnet
Passwort weitergegeben
falsche Datei gelöscht
falscher Empfänger bei E-Mail
USB-Stick unbekannter Herkunft genutzt
Adminrechte aus Bequemlichkeit vergeben
Warnmeldung ignoriert
```

Deshalb gehören Schulung, klare Regeln und einfache Prozesse zur IT-Sicherheit.

Sicherheit darf nicht nur kompliziert sein. Sie muss im Alltag funktionieren.

---

## Least Privilege

Least Privilege bedeutet:

```text
Jeder Benutzer und jeder Dienst bekommt nur die Rechte, die wirklich benötigt werden.
```

Beispiele:

```text
Normaler Benutzer bekommt keine Adminrechte.
Webserver bekommt keinen Zugriff auf private Benutzerdateien.
Praktikant bekommt nur Zugriff auf benötigte Systeme.
Datenbankbenutzer bekommt nur notwendige Datenbankrechte.
```

Vorteil:

```text
Wenn ein Konto kompromittiert wird, ist der Schaden kleiner.
```

---

## Need-to-know-Prinzip

Need-to-know bedeutet:

```text
Benutzer sehen nur Informationen, die sie für ihre Aufgabe brauchen.
```

Beispiele:

```text
HR sieht Personalakten.
IT sieht technische Systeme.
Buchhaltung sieht Rechnungen.
Gäste sehen keine internen Daten.
```

Dieses Prinzip schützt besonders vertrauliche Daten.

Es reduziert unnötige Zugriffe und senkt das Risiko bei Fehlern oder kompromittierten Konten.

---

## Defense in Depth

Defense in Depth bedeutet:

```text
Sicherheit besteht aus mehreren Schutzschichten.
```

Beispiel:

```text
Firewall
Benutzerrechte
MFA
Updates
Backups
Logging
Monitoring
Netztrennung
```

Wenn eine Schutzschicht versagt, sollen andere Schutzschichten den Schaden begrenzen.

Beispiel:

```text
Ein Passwort wird gestohlen.
MFA verhindert trotzdem den Login.
```

Oder:

```text
Malware verschlüsselt Daten.
Getrennte Backups ermöglichen Wiederherstellung.
```

---

## Security by Default

Security by Default bedeutet:

```text
Systeme sollen von Anfang an sicher voreingestellt sein.
```

Beispiele:

```text
Nicht benötigte Dienste sind deaktiviert.
Standardpasswörter werden geändert.
Firewall blockiert zuerst alles Unnötige.
Neue Benutzer haben keine Adminrechte.
Ports werden nur bewusst geöffnet.
```

Das ist besser, als ein System offen zu starten und später zu versuchen, alles abzusichern.

---

## Security by Design

Security by Design bedeutet:

```text
Sicherheit wird schon bei Planung und Aufbau berücksichtigt.
```

Beispiel:

```text
Ein Netzwerk wird geplant.
Dabei werden VLANs, Firewall-Regeln, Adminzugriffe, Backups und Monitoring direkt mitgedacht.
```

Nicht erst am Ende fragen:

```text
Wie machen wir das jetzt sicher?
```

Sondern von Anfang an:

```text
Welche Daten sind kritisch?
Wer braucht Zugriff?
Wie sichern wir das System?
Wie stellen wir es wieder her?
Wie erkennen wir Fehler?
```

---

## Authentifizierung und Autorisierung

Diese Begriffe sind sehr wichtig.

| Begriff            | Frage              | Beispiel                                |
| ------------------ | ------------------ | --------------------------------------- |
| Authentifizierung  | Wer bist du?       | Login mit Passwort und MFA              |
| Autorisierung      | Was darfst du?     | Zugriff auf Ordner erlaubt              |
| Accounting/Logging | Was hast du getan? | Login und Aktionen werden protokolliert |

Beispiel:

```text
Benutzer meldet sich an.
System prüft die Identität.
System prüft die Berechtigungen.
System protokolliert die Aktion.
```

---

## Benutzerkonten

Benutzerkonten sind ein zentraler Teil der IT-Sicherheit.

Wichtige Punkte:

```text
eindeutige Benutzerkonten
keine gemeinsamen Admin-Konten
starke Passwörter
MFA für wichtige Konten
Rechte nach Rolle
Konten deaktivieren, wenn sie nicht mehr gebraucht werden
Adminrechte nur bei Bedarf
```

Gemeinsame Konten sind problematisch, weil man später nicht sauber nachvollziehen kann, wer was getan hat.

---

## Passwörter

Passwörter sind oft eine Schwachstelle.

Gute Passwörter sollten:

```text
lang sein
nicht leicht zu erraten sein
nicht mehrfach verwendet werden
nicht weitergegeben werden
nicht im Klartext gespeichert werden
nicht in Git oder Dokumentation stehen
```

Noch besser ist die Kombination mit MFA.

Ein Passwortmanager kann helfen, lange und unterschiedliche Passwörter zu verwenden.

---

## Multi-Factor Authentication

MFA bedeutet:

```text
Multi-Factor Authentication
```

Dabei werden mehrere Faktoren kombiniert.

Faktoren können sein:

| Faktor | Beispiel                         |
| ------ | -------------------------------- |
| Wissen | Passwort                         |
| Besitz | Smartphone-App, Hardware-Key     |
| Sein   | Fingerabdruck, Gesichtserkennung |

Beispiel:

```text
Passwort + App-Code
```

MFA schützt besser, weil ein gestohlenes Passwort allein nicht ausreicht.

---

## Updates

Updates schließen Fehler und Sicherheitslücken.

Wichtige Begriffe:

```text
Update
Patch
Security Update
Patchmanagement
Wartungsfenster
Rollback
```

Patchmanagement bedeutet:

```text
Updates planen
Updates testen
Updates installieren
System danach prüfen
Änderung dokumentieren
```

Updates sind wichtig, aber sie sollten kontrolliert durchgeführt werden.

---

## Backup

Backups schützen vor Datenverlust.

Sie helfen bei:

```text
versehentlichem Löschen
Hardwareausfall
Ransomware
fehlgeschlagenem Update
Fehlkonfiguration
Datenbankfehler
```

Wichtig ist:

```text
Backup erstellen reicht nicht.
Wiederherstellung muss getestet werden.
```

Ein nicht getestetes Backup ist unsicher.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr.

Beispiele:

```text
SSH nur aus Admin-Netz erlauben
HTTP/HTTPS für Webserver erlauben
Datenbankport nicht öffentlich freigeben
Gastnetz vom internen Netz trennen
```

Wichtig:

```text
Nur notwendige Ports öffnen.
Regeln dokumentieren.
Alte Regeln regelmäßig prüfen.
```

Eine Firewall ist eine Schutzschicht, aber nicht die komplette Sicherheit.

---

## Verschlüsselung

Verschlüsselung schützt Daten vor unberechtigtem Lesen.

Beispiele:

```text
HTTPS für Webseiten
SSH für Remote-Zugriff
VPN für sichere Verbindung
Festplattenverschlüsselung
verschlüsselte Backups
```

Wichtig:

```text
Verschlüsselung schützt nur, wenn Schlüssel und Passwörter sicher verwaltet werden.
```

Wenn der Schlüssel öffentlich ist, bringt Verschlüsselung wenig.

---

## Logging

Logging bedeutet:

```text
Ereignisse werden protokolliert.
```

Beispiele:

```text
Login erfolgreich
Login fehlgeschlagen
Dienst gestartet
Firewall blockiert Verbindung
Backup fehlgeschlagen
Benutzer geändert
Systemfehler aufgetreten
```

Logs helfen bei:

```text
Fehlersuche
Sicherheitsanalyse
Nachvollziehbarkeit
Incident Response
```

Logs müssen geschützt werden, weil sie sensible Informationen enthalten können.

---

## Monitoring

Monitoring bedeutet:

```text
Systeme werden überwacht.
```

Beispiele:

```text
CPU-Auslastung
Speicherplatz
Netzwerkverfügbarkeit
Dienststatus
Backup-Erfolg
Login-Fehler
Zertifikatsablauf
```

Monitoring hilft, Probleme früher zu erkennen.

Ohne Monitoring merkt man manche Fehler erst, wenn Benutzer sich beschweren.

---

## Notfallplan

Ein Notfallplan beschreibt, was bei einem größeren Problem getan werden soll.

Beispiele für Notfälle:

```text
Serverausfall
Ransomware
Datenverlust
gestohlene Zugangsdaten
Firewall-Fehlkonfiguration
Backup funktioniert nicht
```

Ein Notfallplan sollte klären:

```text
Wer wird informiert?
Wer entscheidet?
Welche Systeme sind kritisch?
Wie wird isoliert?
Wie wird wiederhergestellt?
Wie wird dokumentiert?
```

Im Ernstfall spart ein vorbereiteter Plan viel Zeit.

---

## Sicherheitsvorfall

Ein Sicherheitsvorfall ist ein Ereignis, das die Sicherheit gefährdet.

Beispiele:

```text
Malware-Fund
Phishing erfolgreich
Admin-Konto kompromittiert
unberechtigter Zugriff
Daten öffentlich geteilt
Laptop verloren
ungewöhnlich viele Login-Fehler
```

Wichtig ist:

```text
nicht vertuschen
nicht hektisch alles löschen
zuständige Personen informieren
Beweise und Logs sichern
Schaden begrenzen
Ursache analysieren
Maßnahmen dokumentieren
```

---

## Datenschutz und IT-Sicherheit

Datenschutz und IT-Sicherheit hängen eng zusammen.

Datenschutz schützt personenbezogene Daten.

IT-Sicherheit schützt die Systeme und Maßnahmen, damit diese Daten sicher verarbeitet werden.

Beispiele für personenbezogene Daten:

```text
Name
Adresse
E-Mail
Telefonnummer
Geburtsdatum
Personalnummer
Kundennummer
IP-Adresse
Login-Name
```

In der Praxis bedeutet das:

```text
Zugriffe begrenzen
Daten nicht unnötig speichern
Daten nicht öffentlich machen
Backups schützen
Logs bewusst behandeln
Löschfristen beachten
```

---

## IT-Sicherheit bei Linux

Linux-Systeme müssen sicher betrieben werden.

Wichtige Punkte:

```text
Updates installieren
nur notwendige Dienste aktivieren
SSH absichern
Firewall prüfen
Benutzerrechte sauber setzen
sudo bewusst nutzen
Dateirechte prüfen
Logs lesen
Backups einrichten
```

Nützliche Befehle:

```bash
sudo apt update
sudo apt upgrade
sudo ufw status
ss -tulpen
systemctl status ssh
journalctl -u ssh
```

---

## IT-Sicherheit bei Netzwerken

Netzwerke müssen sauber getrennt und kontrolliert werden.

Wichtige Punkte:

```text
Firewall-Regeln
VLANs
Gastnetz
Management-Netz
VPN
WLAN-Verschlüsselung
DNS-Sicherheit
DHCP-Kontrolle
Monitoring
Portfreigaben
```

Beispiel:

```text
Gäste-WLAN darf ins Internet.
Gäste-WLAN darf nicht auf interne Server.
Admin-Zugriff nur aus Management-Netz.
```

---

## IT-Sicherheit bei Docker

Docker braucht ebenfalls Sicherheitsbewusstsein.

Wichtige Punkte:

```text
keine Secrets in Git speichern
.env-Dateien schützen
nur notwendige Ports veröffentlichen
Images aktuell halten
Container nicht unnötig als root betreiben
Datenbankports nicht unnötig nach außen öffnen
Volumes bewusst nutzen
Logs prüfen
```

Typischer Fehler:

```text
PostgreSQL-Port wird öffentlich geöffnet, obwohl nur andere Container darauf zugreifen müssen.
```

Besser:

```text
Datenbank bleibt intern im Docker-Netz.
```

---

## IT-Sicherheit bei virtuellen Maschinen

Virtuelle Maschinen sind echte Systeme und müssen auch so behandelt werden.

Wichtige Punkte:

```text
Updates installieren
SSH absichern
Firewall prüfen
Netzwerkmodus bewusst wählen
Snapshots nicht mit Backups verwechseln
Zugriffe dokumentieren
VMs sauber benennen
Ressourcen überwachen
```

Beispiel:

```text
Bridge-Modus macht die VM im LAN sichtbarer.
NAT-Modus versteckt sie eher hinter dem Host.
```

Das hat Auswirkungen auf Erreichbarkeit und Sicherheit.

---

## Dokumentation

Dokumentation ist ein wichtiger Teil der IT-Sicherheit.

Dokumentiert werden sollten zum Beispiel:

```text
Benutzerrechte
Admin-Konten
Firewall-Regeln
Backup-Konzept
Wiederherstellungstests
IP- und VLAN-Pläne
Serverdienste
offene Ports
Sicherheitsvorfälle
Änderungen an Systemen
```

Ohne Dokumentation kann man später schwer nachvollziehen, warum etwas so konfiguriert wurde.

---

## Typische Fehler

| Fehler                              | Problem                                  |
| ----------------------------------- | ---------------------------------------- |
| alle Benutzer haben Adminrechte     | hoher Schaden bei Fehlern oder Angriffen |
| gleiche Passwörter mehrfach genutzt | ein Leak gefährdet mehrere Konten        |
| keine MFA                           | Passwortdiebstahl reicht oft aus         |
| Updates werden ignoriert            | bekannte Lücken bleiben offen            |
| Backups werden nie getestet         | Wiederherstellung ist unsicher           |
| Firewall-Regeln nicht dokumentiert  | Fehlersuche und Kontrolle schwierig      |
| unnötige Ports offen                | größere Angriffsfläche                   |
| Secrets in Git gespeichert          | Zugangsdaten können öffentlich werden    |
| Logs nicht geprüft                  | Angriffe bleiben unbemerkt               |
| keine klare Zuständigkeit           | Vorfälle werden langsam behandelt        |

---

## Gute Arbeitsweise

Eine sichere Arbeitsweise bedeutet:

```text
erst verstehen, dann ändern
Rechte sparsam vergeben
Änderungen dokumentieren
Updates planen
Backups testen
Logs prüfen
Firewall-Regeln bewusst setzen
Passwörter schützen
MFA nutzen
Sicherheitsvorfälle ernst nehmen
```

Wichtige Regel:

```text
Sicherheit ist kein einmaliger Schritt.
Sicherheit ist ein laufender Prozess.
```

Systeme ändern sich. Benutzer ändern sich. Software ändert sich. Angriffe ändern sich.

Deshalb muss Sicherheit regelmäßig geprüft werden.

---

## Praktische Beispiele

### Beispiel 1: SSH absichern

```text
SSH nur für benötigte Benutzer erlauben.
Starke Passwörter oder SSH-Schlüssel nutzen.
Firewall-Regeln prüfen.
Logs kontrollieren.
```

Befehle:

```bash
systemctl status ssh
sudo ufw status
journalctl -u ssh
```

### Beispiel 2: Offene Ports prüfen

```bash
ss -tulpen
```

Danach fragen:

```text
Brauchen wir diesen Dienst wirklich?
Soll dieser Port öffentlich erreichbar sein?
Ist der Dienst aktuell?
Ist der Zugriff dokumentiert?
```

### Beispiel 3: Backup prüfen

```text
Backup vorhanden?
Backup aktuell?
Backup getrennt gespeichert?
Wiederherstellung getestet?
Zugriff auf Backup geschützt?
```

### Beispiel 4: Benutzerrechte prüfen

```text
Wer hat Adminrechte?
Sind alte Konten deaktiviert?
Gibt es gemeinsame Konten?
Sind Rechte dokumentiert?
```

---

## FISI-Bezug

IT-Sicherheit ist für FISI ein Querschnittsthema.

Man braucht sie bei:

```text
Linux-Administration
Windows-Administration
Netzwerkplanung
Benutzerverwaltung
Serverbetrieb
Docker
Virtualisierung
Cloud
Backups
Support
Dokumentation
Troubleshooting
```

Ein FISI muss nicht jedes Thema so tief wie ein Security-Spezialist können.

Aber ein FISI muss Risiken erkennen, sicher konfigurieren, sauber dokumentieren und bei Problemen strukturiert reagieren.

---

## Kurze Zusammenfassung

IT-Sicherheit schützt Systeme, Daten, Benutzer und Netzwerke vor Ausfall, Missbrauch, Manipulation und unberechtigtem Zugriff.

Wichtige Grundlagen sind Vertraulichkeit, Integrität, Verfügbarkeit, Authentifizierung, Autorisierung, Least Privilege, Defense in Depth, Updates, Backups, Firewalls, Logging, Monitoring und Dokumentation.

Sicherheit besteht aus technischen, organisatorischen, physischen und personellen Maßnahmen.

Für FISI ist IT-Sicherheit besonders wichtig, weil fast jede praktische Aufgabe auch eine Sicherheitsseite hat.
