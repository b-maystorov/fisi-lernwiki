# 7. IT-Sicherheit in der FISI-Praxis

In diesem Kapitel geht es darum, wie IT-Sicherheit in der praktischen Arbeit eines Fachinformatikers für Systemintegration vorkommt.

IT-Sicherheit ist kein einzelnes Programm und kein einzelner Befehl. Sie ist ein Teil fast jeder IT-Aufgabe: Benutzer anlegen, Server betreiben, Updates einspielen, Backups prüfen, Firewalls konfigurieren, Netzwerke trennen, Logs lesen, Docker-Systeme betreiben oder Dokumentation schreiben.

Für FISI ist wichtig, Sicherheit nicht nur theoretisch zu kennen, sondern im Alltag sauber und bewusst umzusetzen.

---

## Kurz erklärt

IT-Sicherheit in der FISI-Praxis bedeutet:

```text
sicher konfigurieren
Rechte begrenzen
Systeme aktuell halten
Backups prüfen
Firewall-Regeln verstehen
Logs lesen
Benutzer unterstützen
Vorfälle erkennen
Daten schützen
Änderungen dokumentieren
```

Ein guter FISI denkt nicht nur:

```text
Funktioniert das System?
```

Sondern auch:

```text
Ist das System sicher genug?
Wer darf darauf zugreifen?
Sind Backups vorhanden?
Sind Updates aktuell?
Sind unnötige Ports offen?
Ist alles dokumentiert?
```

---

## IT-Sicherheit als Querschnittsthema

IT-Sicherheit betrifft viele andere Bereiche.

| Bereich | Sicherheitsbezug |
|---|---|
| Linux | Benutzerrechte, SSH, Updates, Firewall, Logs |
| Netzwerke | VLANs, Firewall, VPN, WLAN-Sicherheit |
| Docker | Secrets, Ports, Images, Volumes, Netzwerke |
| Virtualisierung | VM-Netzwerk, Snapshots, Updates, Zugriff |
| Datenbanken | Benutzerrechte, Backups, Ports, Datenzugriff |
| Git/GitHub | SSH-Schlüssel, Tokens, öffentliche Repos, Secrets |
| Support | Phishing, Benutzerrechte, Tickets, Datenschutz |
| Dokumentation | Nachvollziehbarkeit, keine Passwörter, saubere Übergabe |

IT-Sicherheit steht also nicht neben der normalen Arbeit, sondern ist Teil der normalen Arbeit.

---

## Typische Aufgaben eines FISI

Ein FISI hat in der Praxis viele Aufgaben mit Sicherheitsbezug.

Beispiele:

```text
Benutzerkonten anlegen und deaktivieren
Gruppen und Rechte verwalten
Server aktualisieren
Firewall-Regeln prüfen
SSH-Zugriff absichern
Backups einrichten und testen
Logs analysieren
WLAN sicher konfigurieren
Gastnetz vom internen Netz trennen
Docker-Container sicher betreiben
VMs sauber ins Netzwerk einbinden
Sicherheitsvorfälle dokumentieren
```

Bei jeder dieser Aufgaben kann eine falsche Konfiguration später zu Problemen führen.

---

## Benutzerverwaltung in der Praxis

Benutzerkonten sind ein zentraler Teil der IT-Sicherheit.

Wichtige Fragen:

```text
Wer braucht ein Konto?
Welche Rolle hat die Person?
Welche Gruppen werden benötigt?
Welche Rechte sind wirklich notwendig?
Wann muss ein Konto deaktiviert werden?
Ist MFA aktiv?
Gibt es alte oder ungenutzte Konten?
```

Ein häufiger Fehler ist, dass Benutzer über lange Zeit immer mehr Rechte sammeln.

Das nennt man oft Rechte-Wildwuchs.

Gute Arbeitsweise:

```text
Rechte nach Rollen vergeben
Gruppen statt Einzelrechte nutzen
Adminrechte sparsam vergeben
alte Konten deaktivieren
Rechte regelmäßig prüfen
```

---

## Onboarding und Offboarding

Beim Onboarding wird ein neuer Benutzer eingerichtet.

Typische Aufgaben:

```text
Benutzerkonto erstellen
Gruppen zuweisen
E-Mail einrichten
Gerät bereitstellen
MFA aktivieren
Zugriff auf benötigte Systeme geben
Benutzer über Sicherheitsregeln informieren
```

Beim Offboarding wird ein Benutzer entfernt oder deaktiviert.

Typische Aufgaben:

```text
Konto deaktivieren
VPN-Zugang entfernen
Gruppenmitgliedschaften prüfen
Geräte zurücknehmen
Tokens und Schlüssel entfernen
Weiterleitungen prüfen
Datenübergabe klären
```

Offboarding ist besonders wichtig. Ein altes aktives Konto kann ein großes Sicherheitsrisiko sein.

---

## Rechte und Least Privilege

Ein wichtiges Prinzip ist:

```text
So wenig Rechte wie möglich, so viele wie nötig.
```

Das bedeutet:

```text
normale Benutzer bekommen keine Adminrechte
Dienstkonten bekommen nur benötigte Rechte
Projektordner sind nur für Projektmitglieder sichtbar
Backups sind nur für berechtigte Personen zugänglich
Adminzugriffe werden getrennt und protokolliert
```

Least Privilege begrenzt Schäden, wenn ein Konto kompromittiert wird oder ein Benutzer einen Fehler macht.

---

## Admin-Konten in der Praxis

Admin-Konten sind besonders kritisch.

Gute Regeln:

```text
normales Konto und Admin-Konto trennen
MFA nutzen
keine gemeinsamen Admin-Konten
Adminrechte nur bei Bedarf verwenden
SSH-Schlüssel schützen
Adminaktionen dokumentieren
Logs prüfen
```

Beispiel:

```text
bilgin.normal
bilgin.admin
```

Das normale Konto wird für Alltag, E-Mail und Browser genutzt.

Das Admin-Konto wird nur für administrative Aufgaben genutzt.

---

## Server sicher betreiben

Ein Server muss nicht nur laufen, sondern sicher betrieben werden.

Wichtige Punkte:

```text
regelmäßige Updates
nur notwendige Dienste aktiv
Firewall-Regeln gesetzt
SSH abgesichert
Backups eingerichtet
Logs werden geprüft
Benutzerrechte passen
Monitoring vorhanden
Dokumentation aktuell
```

Praktische Befehle:

```bash
sudo apt update
sudo apt upgrade
sudo ufw status
ss -tulpen
systemctl status ssh
journalctl -u ssh
```

Wichtig:

```text
Ein offener Dienst ist immer auch eine mögliche Angriffsfläche.
```

---

## Offene Ports prüfen

Offene Ports zeigen, welche Dienste im Netzwerk erreichbar sein können.

Unter Linux:

```bash
ss -tulpen
```

Wichtige Fragen:

```text
Welche Dienste lauschen?
Welche Ports sind offen?
Brauchen wir diese Dienste?
Sind sie nur intern oder auch extern erreichbar?
Blockiert oder erlaubt die Firewall den Zugriff?
```

Beispiel:

```text
Port 22 offen -> SSH
Port 80 offen -> HTTP
Port 443 offen -> HTTPS
Port 5432 offen -> PostgreSQL
```

Ein Datenbankport sollte normalerweise nicht unnötig öffentlich erreichbar sein.

---

## Firewall-Regeln in der Praxis

Firewalls kontrollieren Netzwerkverkehr.

Gute Firewall-Regeln sind:

```text
notwendig
verständlich
dokumentiert
begrenzt
regelmäßig geprüft
```

Schlechte Firewall-Regel:

```text
Alle dürfen auf alles zugreifen.
```

Bessere Regel:

```text
Nur Admin-Netz darf per SSH auf Server zugreifen.
Nur Webserver darf mit Datenbank sprechen.
Gastnetz darf nur ins Internet.
```

Firewall-Regeln sollten immer einen klaren Zweck haben.

---

## Updates und Patchmanagement

Updates schließen Sicherheitslücken und Fehler.

In der Praxis geht es nicht nur um:

```bash
sudo apt upgrade
```

Sondern um einen Prozess:

```text
Systeme erfassen
Updates prüfen
kritische Updates priorisieren
Wartungsfenster planen
Backup vorher prüfen
Update durchführen
Dienste danach testen
Änderung dokumentieren
```

Wichtig:

```text
Updates nicht ewig aufschieben.
Updates aber auch nicht blind auf kritischen Systemen durchführen.
```

---

## Backups in der Praxis

Backups sind eine der wichtigsten Sicherheitsmaßnahmen.

Wichtige Fragen:

```text
Was wird gesichert?
Wie oft wird gesichert?
Wo wird gesichert?
Wer hat Zugriff?
Ist das Backup verschlüsselt?
Wurde Restore getestet?
Wie lange dauert die Wiederherstellung?
```

Ein Backup ist nur dann wirklich wertvoll, wenn die Wiederherstellung funktioniert.

Guter Satz:

```text
Nicht das Backup zählt, sondern der erfolgreiche Restore.
```

---

## Restore-Test

Ein Restore-Test prüft, ob Daten wirklich wiederhergestellt werden können.

Beispiele:

```text
einzelne Datei wiederherstellen
Datenbank in Testumgebung wiederherstellen
VM aus Backup starten
Konfigurationsdatei zurückspielen
kompletten Server-Wiederaufbau testen
```

Ein Restore-Test zeigt:

```text
ob das Backup vollständig ist
ob die Anleitung stimmt
wie lange die Wiederherstellung dauert
ob Berechtigungen korrekt bleiben
```

Ohne Restore-Test bleibt ein Backup unsicher.

---

## Netzwerksicherheit in der Praxis

Netzwerke müssen sauber getrennt und kontrolliert werden.

Wichtige Themen:

```text
VLANs
Firewall-Regeln
VPN
Gastnetz
Management-Netz
WLAN-Verschlüsselung
DNS und DHCP
Portfreigaben
Monitoring
```

Beispiel:

```text
Gäste-WLAN darf ins Internet.
Gäste-WLAN darf nicht auf interne Server.
Management-Zugriff nur aus Admin-Netz.
```

VLANs trennen Netze. Firewalls kontrollieren, welche Kommunikation erlaubt ist.

---

## WLAN-Sicherheit

WLAN ist praktisch, aber sicherheitsrelevant.

Wichtige Punkte:

```text
WPA2 oder WPA3 nutzen
starkes WLAN-Passwort
Gäste-WLAN trennen
SSID sinnvoll planen
Access Points aktuell halten
Adminzugriff schützen
Client-Isolation im Gäste-WLAN prüfen
```

In Firmenumgebungen ist oft WPA-Enterprise sinnvoll.

Dabei melden sich Benutzer nicht nur mit einem gemeinsamen WLAN-Passwort an, sondern mit individuellen Zugangsdaten oder Zertifikaten.

---

## VPN in der Praxis

VPN wird genutzt, um sichere Verbindungen in ein Netzwerk aufzubauen.

Typische Fälle:

```text
Homeoffice
Remote-Administration
Standortverbindung
Zugriff auf interne Systeme
```

Wichtige Sicherheitsfragen:

```text
Wer darf VPN nutzen?
Ist MFA aktiv?
Welche Netze sind über VPN erreichbar?
Sind VPN-Logs vorhanden?
Werden alte VPN-Zugänge entfernt?
Funktioniert DNS über VPN?
```

VPN verbunden bedeutet nicht automatisch, dass alles korrekt funktioniert. Routen, DNS und Berechtigungen müssen ebenfalls passen.

---

## Docker sicher betreiben

Docker ist praktisch, aber braucht Sicherheitsbewusstsein.

Wichtige Punkte:

```text
keine Secrets in Git speichern
.env-Dateien schützen
nur notwendige Ports veröffentlichen
Images aktuell halten
Container nicht unnötig als root betreiben
Volumes bewusst nutzen
Datenbankports nicht unnötig öffnen
Docker-Netzwerke trennen
Logs prüfen
```

Typischer Fehler:

```text
PostgreSQL-Port wird auf dem Host veröffentlicht, obwohl nur andere Container darauf zugreifen müssen.
```

Besser:

```text
Datenbank bleibt intern im Docker-Netz.
Nur die benötigte Weboberfläche wird bewusst veröffentlicht.
```

---

## Virtualisierung sicher betreiben

Virtuelle Maschinen müssen wie echte Systeme behandelt werden.

Wichtige Punkte:

```text
VMs aktualisieren
Firewall prüfen
SSH absichern
Netzwerkmodus bewusst wählen
Snapshots nicht mit Backups verwechseln
Zugriffe dokumentieren
Ressourcen überwachen
VMs sauber benennen
```

NAT, Bridge und Host-only haben unterschiedliche Sicherheitswirkungen.

Beispiel:

```text
Bridge macht die VM wie ein eigenes Gerät im LAN sichtbar.
NAT versteckt die VM eher hinter dem Host.
```

Das beeinflusst Erreichbarkeit und Risiko.

---

## GitHub und öffentliche Repositories

Öffentliche Repositories sind gut für ein Portfolio, aber man muss vorsichtig sein.

Nicht veröffentlichen:

```text
Passwörter
API-Tokens
private SSH-Keys
echte .env-Dateien
interne IP-Pläne
Kundendaten
private Screenshots
interne Tickets
echte Zugangsdaten
```

Gute Arbeitsweise:

```text
.env in .gitignore eintragen
.env.example ohne echte Secrets nutzen
Beispieldaten verwenden
Screenshots prüfen
private Informationen entfernen
Commits vor Push kurz prüfen
```

Ein Portfolio soll Kompetenz zeigen, aber keine echten Daten veröffentlichen.

---

## Logs und Monitoring

Logs und Monitoring helfen, Fehler und Sicherheitsprobleme zu erkennen.

Wichtige Logs:

```text
Login-Logs
SSH-Logs
Firewall-Logs
Systemlogs
Docker-Logs
Webserver-Logs
Backup-Logs
VPN-Logs
```

Nützliche Befehle:

```bash
journalctl
journalctl -u ssh
journalctl -u docker
docker logs containername
docker compose logs
```

Monitoring hilft, Probleme früh zu erkennen.

Beispiele:

```text
Festplatte fast voll
Dienst ist offline
Backup fehlgeschlagen
ungewöhnlich viele Login-Fehler
Server nicht erreichbar
```

---

## Umgang mit Sicherheitsvorfällen

Ein Sicherheitsvorfall kann klein oder groß sein.

Beispiele:

```text
Phishing-Mail
Malware-Verdacht
gestohlene Zugangsdaten
unberechtigter Zugriff
falsche Firewall-Regel
Daten versehentlich veröffentlicht
Ransomware
```

Gute erste Reaktion:

```text
ruhig bleiben
Vorfall melden
betroffene Systeme identifizieren
Schaden begrenzen
Logs sichern
nicht vorschnell Beweise löschen
zuständige Personen informieren
Maßnahmen dokumentieren
```

Wichtig:

```text
Nicht vertuschen.
Früh melden ist besser als spät reagieren.
```

---

## Kommunikation mit Benutzern

IT-Sicherheit funktioniert nur, wenn Benutzer mitmachen können.

Gute Kommunikation ist:

```text
klar
ruhig
verständlich
nicht beschuldigend
lösungsorientiert
```

Schlecht:

```text
Warum hast du das angeklickt?
```

Besser:

```text
Danke fürs Melden. Wir prüfen das jetzt und sichern dein Konto ab.
```

Eine gute Sicherheitskultur sorgt dafür, dass Benutzer Vorfälle schnell melden.

---

## Dokumentation in der Praxis

Sicherheitsrelevante Dinge müssen dokumentiert werden.

Beispiele:

```text
Firewall-Regeln
Backup-Konzept
Restore-Tests
Admin-Konten
Gruppenrechte
IP- und VLAN-Pläne
Serverdienste
offene Ports
VPN-Zugänge
Sicherheitsvorfälle
Änderungen an Systemen
```

Dokumentation hilft bei:

```text
Fehlersuche
Übergabe
Notfällen
Audits
Prüfungsvorbereitung
Teamarbeit
```

Wichtig:

```text
Dokumentation darf keine echten Passwörter oder Secrets enthalten.
```

---

## Beispiel 1: Neuer Server wird eingerichtet

Situation:

```text
Ein neuer Ubuntu-Server soll eingerichtet werden.
```

Sicherheitscheck:

```text
Updates installieren
SSH prüfen
Firewall aktivieren
nur notwendige Ports öffnen
Adminzugriff begrenzen
Benutzerrechte sauber setzen
Backups planen
Monitoring einrichten
Dienste dokumentieren
```

Praktische Befehle:

```bash
sudo apt update
sudo apt upgrade
sudo ufw status
ss -tulpen
systemctl status ssh
```

---

## Beispiel 2: Benutzer meldet Phishing-Mail

Situation:

```text
Ein Benutzer meldet eine verdächtige E-Mail.
```

Gute Reaktion:

```text
Meldung ernst nehmen
Benutzer nicht beschuldigen
Absender und Link prüfen
ähnliche Mails suchen
prüfen, ob Zugangsdaten eingegeben wurden
bei Bedarf Passwort ändern
MFA und aktive Sitzungen prüfen
Vorfall dokumentieren
Benutzer informieren
```

Wichtig:

```text
Schnelles Melden kann größeren Schaden verhindern.
```

---

## Beispiel 3: Docker-Datenbank absichern

Situation:

```text
PostgreSQL läuft in Docker Compose.
```

Unsicher:

```text
Datenbankport 5432 ist unnötig auf dem Host veröffentlicht.
Passwort steht direkt im Repository.
```

Besser:

```text
Datenbank bleibt im Docker-Netz
.env wird nicht committed
.env.example enthält nur Platzhalter
nur notwendige Weboberfläche wird veröffentlicht
Volume wird gesichert
README dokumentiert den sicheren Aufbau
```

Prüfen:

```bash
docker compose ps
docker compose config
docker network ls
docker volume ls
```

---

## Beispiel 4: Backup prüfen

Situation:

```text
Ein Dateiserver wird regelmäßig gesichert.
```

Nicht ausreichend:

```text
Backup läuft angeblich.
```

Besser prüfen:

```text
Wann war das letzte erfolgreiche Backup?
Welche Daten wurden gesichert?
Wer hat Zugriff auf das Backup?
Ist das Backup verschlüsselt?
Wurde ein Restore getestet?
Gibt es eine Anleitung?
```

Ein Backup ohne Restore-Test ist keine zuverlässige Sicherheit.

---

## Typische Fehler in der FISI-Praxis

| Fehler | Problem |
|---|---|
| Adminrechte zu großzügig vergeben | Schaden bei Fehlern oder Angriffen größer |
| alte Benutzerkonten aktiv lassen | unnötiger Zugriff bleibt bestehen |
| Firewall-Regeln nicht dokumentieren | spätere Fehlersuche schwer |
| Updates ewig verschieben | bekannte Lücken bleiben offen |
| Backups nie testen | Restore im Notfall unsicher |
| Datenbankports öffentlich öffnen | unnötige Angriffsfläche |
| Secrets in Git speichern | Zugangsdaten können öffentlich werden |
| Logs nicht prüfen | Angriffe oder Fehler bleiben unbemerkt |
| Benutzer bei Phishing beschuldigen | Vorfälle werden später nicht gemeldet |
| Dokumentation vernachlässigen | Wissen geht verloren |

---

## Gute Arbeitsweise

Eine gute sicherheitsbewusste Arbeitsweise:

```text
erst prüfen, dann ändern
nur notwendige Rechte vergeben
nur notwendige Ports öffnen
Updates geplant durchführen
Backups regelmäßig testen
Logs kontrollieren
Vorfälle sachlich dokumentieren
Benutzer unterstützen
öffentliche Repos prüfen
Änderungen nachvollziehbar machen
```

Wichtige Regel:

```text
Sicherheit ist kein Zusatz am Ende.
Sicherheit gehört von Anfang an dazu.
```

---

## Praktische Checkliste für FISI

Bei einem System kann man fragen:

```text
Welche Daten liegen hier?
Wer darf zugreifen?
Sind Rechte sauber gesetzt?
Sind unnötige Ports offen?
Ist die Firewall aktiv?
Sind Updates aktuell?
Gibt es Backups?
Wurde Restore getestet?
Gibt es Logs?
Ist Monitoring vorhanden?
Ist alles dokumentiert?
Gibt es echte Secrets in Dateien oder Repos?
```

Diese Fragen helfen bei Servern, Clients, Docker, VMs, Netzwerken und Projekten.

---

## FISI-Bezug

IT-Sicherheit ist ein Kernbestandteil der Systemintegration.

Ein FISI muss nicht alles wie ein spezialisierter Security-Analyst können.

Aber ein FISI muss:

```text
Risiken erkennen
sicher konfigurieren
Rechte sinnvoll vergeben
Benutzer unterstützen
Updates und Backups ernst nehmen
Netzwerke trennen
Logs lesen
Vorfälle melden
technische Änderungen dokumentieren
Datenschutz beachten
```

Ein funktionierendes System ist gut.

Ein funktionierendes, dokumentiertes und sicher betriebenes System ist besser.

---

## Kurze Zusammenfassung

IT-Sicherheit in der FISI-Praxis betrifft Benutzerkonten, Rechte, Server, Netzwerke, Docker, virtuelle Maschinen, Firewalls, Updates, Backups, Logs, Monitoring, Datenschutz und Dokumentation.

Wichtige Prinzipien sind Least Privilege, Need-to-know, MFA, Patchmanagement, Restore-Tests, Netztrennung und saubere Dokumentation.

Ein FISI arbeitet sicherheitsbewusst, prüft Systeme systematisch, dokumentiert Änderungen und behandelt Vorfälle ruhig und nachvollziehbar.

Sicherheit ist kein einzelner Schritt, sondern Teil der täglichen Arbeitsweise.