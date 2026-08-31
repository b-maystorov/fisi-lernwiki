# 4. Firewall, Updates und Backup

In diesem Kapitel geht es um drei sehr wichtige Schutzmaßnahmen im IT-Alltag:

```text
Firewall
Updates
Backup
```

Diese Themen wirken auf den ersten Blick unterschiedlich, gehören aber eng zusammen. Eine Firewall reduziert unnötige Zugriffe. Updates schließen bekannte Sicherheitslücken. Backups helfen, Daten und Systeme nach Fehlern, Ausfällen oder Angriffen wiederherzustellen.

Für Fachinformatiker für Systemintegration sind diese drei Bereiche besonders wichtig, weil sie direkt zur täglichen Arbeit mit Clients, Servern, Netzwerken, Docker, virtuellen Maschinen und Diensten gehören.

---

## Kurz erklärt

| Thema | Bedeutung |
|---|---|
| Firewall | kontrolliert Netzwerkverkehr |
| Updates | schließen Fehler und Sicherheitslücken |
| Backup | sichert Daten für Wiederherstellung |
| Patchmanagement | geplanter Umgang mit Updates |
| Restore | Wiederherstellung aus einem Backup |
| Recovery | Wiederherstellung des Betriebs |
| Regelwerk | Sammlung von Firewall-Regeln |
| Wartungsfenster | geplanter Zeitraum für Änderungen |

Einfach gesagt:

```text
Firewall = Was darf rein oder raus?
Updates = Ist das System aktuell?
Backup = Können wir Daten wiederherstellen?
```

---

## Warum diese drei Themen wichtig sind

Viele Sicherheitsprobleme entstehen durch einfache Dinge:

```text
unnötig offene Ports
veraltete Software
fehlende Sicherheitsupdates
nicht getestete Backups
falsche Firewall-Regeln
Datenbank öffentlich erreichbar
Backup liegt ungeschützt im Netzwerk
```

Firewall, Updates und Backup gehören deshalb zu den wichtigsten Grundlagen eines sicheren Betriebs.

Sie verhindern nicht jeden Sicherheitsvorfall, aber sie reduzieren Risiken stark.

---

## Firewall

Eine Firewall kontrolliert Netzwerkverkehr.

Sie entscheidet, welcher Datenverkehr erlaubt oder blockiert wird.

Beispiele:

```text
SSH erlauben
HTTP/HTTPS erlauben
Datenbankport blockieren
Gastnetz vom internen Netz trennen
nur Admin-Netz auf Server erlauben
```

Eine Firewall kann auf verschiedenen Ebenen existieren:

```text
Client-Firewall
Server-Firewall
Router-Firewall
Netzwerk-Firewall
Cloud-Firewall
Docker/Container-Netzwerkregeln
```

---

## Warum Firewalls wichtig sind

Ohne Firewall könnten Dienste unnötig erreichbar sein.

Beispiele:

```text
SSH ist aus jedem Netz erreichbar.
Datenbankport ist öffentlich offen.
Admin-Weboberfläche ist aus dem Gastnetz erreichbar.
Testserver ist aus dem Internet erreichbar.
```

Das erhöht die Angriffsfläche.

Eine Firewall hilft, nur die Kommunikation zu erlauben, die wirklich gebraucht wird.

Wichtige Regel:

```text
So wenig wie möglich öffnen, so viel wie nötig erlauben.
```

---

## Eingehender und ausgehender Verkehr

Man unterscheidet oft zwischen eingehendem und ausgehendem Verkehr.

| Richtung | Bedeutung | Beispiel |
|---|---|---|
| eingehend | Verbindung kommt zum System | Client verbindet sich per SSH zum Server |
| ausgehend | System verbindet sich nach außen | Server lädt Updates herunter |

Beispiel Server:

```text
Eingehend erlauben:
- SSH aus Admin-Netz
- HTTPS für Benutzer

Ausgehend erlauben:
- Updates
- DNS
- Monitoring
```

Nicht jeder Server muss alle Verbindungen erlauben.

---

## Ports und Dienste

Firewalls arbeiten häufig mit Ports.

Beispiele:

| Port | Dienst |
|---|---|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 8080 | Test-Webdienst oder Admin-Oberfläche |

Wichtig:

```text
Ein offener Port bedeutet eine größere Angriffsfläche.
```

Deshalb sollte man prüfen:

```text
Brauchen wir diesen Dienst?
Muss der Dienst aus diesem Netz erreichbar sein?
Muss der Port öffentlich erreichbar sein?
Ist der Zugriff dokumentiert?
```

---

## Firewall-Regeln

Eine Firewall-Regel beschreibt, was erlaubt oder blockiert wird.

Eine Regel kann enthalten:

```text
Quelle
Ziel
Port
Protokoll
Richtung
Aktion
Kommentar
```

Beispiel:

```text
Quelle: Admin-Netz 192.168.40.0/24
Ziel: Server 192.168.30.10
Port: 22
Protokoll: TCP
Aktion: erlauben
```

Das bedeutet:

```text
Nur das Admin-Netz darf per SSH auf den Server.
```

---

## Default Deny

Ein häufiges Sicherheitsprinzip ist:

```text
Default Deny
```

Das bedeutet:

```text
Standardmäßig ist alles blockiert.
Nur ausdrücklich erlaubte Verbindungen sind erlaubt.
```

Das ist sicherer als:

```text
Alles ist erlaubt.
Nur einzelne Dinge werden blockiert.
```

In der Praxis muss Default Deny gut geplant werden, weil sonst wichtige Dienste versehentlich blockiert werden können.

---

## Firewall unter Ubuntu mit UFW

Unter Ubuntu wird häufig UFW genutzt.

UFW bedeutet:

```text
Uncomplicated Firewall
```

Status prüfen:

```bash
sudo ufw status
```

Ausführlicher:

```bash
sudo ufw status verbose
```

Firewall aktivieren:

```bash
sudo ufw enable
```

Firewall deaktivieren:

```bash
sudo ufw disable
```

Wichtig:

```text
Firewall-Regeln vorher prüfen, damit man sich nicht selbst aussperrt.
```

---

## UFW Beispiele

SSH erlauben:

```bash
sudo ufw allow 22/tcp
```

HTTP erlauben:

```bash
sudo ufw allow 80/tcp
```

HTTPS erlauben:

```bash
sudo ufw allow 443/tcp
```

PostgreSQL blockieren:

```bash
sudo ufw deny 5432/tcp
```

Regeln anzeigen:

```bash
sudo ufw status numbered
```

Regel löschen:

```bash
sudo ufw delete NUMMER
```

---

## SSH sicher erlauben

SSH sollte nicht unnötig für alle Netze offen sein.

Schlechter:

```bash
sudo ufw allow 22/tcp
```

Besser, wenn möglich:

```bash
sudo ufw allow from 192.168.40.0/24 to any port 22 proto tcp
```

Das bedeutet:

```text
Nur Geräte aus dem Admin-Netz dürfen SSH nutzen.
```

Zusätzlich wichtig:

```text
starke Passwörter oder SSH-Schlüssel
keine gemeinsamen Admin-Konten
Logs prüfen
MFA, wenn verfügbar
```

---

## Firewall und Dienste prüfen

Eine Firewall-Regel allein reicht nicht.

Der Dienst muss auch laufen.

Beispiel SSH prüfen:

```bash
systemctl status ssh
ss -tulpen | grep 22
sudo ufw status
```

Beispiel Webserver prüfen:

```bash
systemctl status nginx
ss -tulpen | grep 80
sudo ufw status
```

Wichtig:

```text
Firewall erlaubt Port ≠ Dienst läuft automatisch.
Dienst läuft ≠ Firewall erlaubt Zugriff automatisch.
```

Beides muss zusammenpassen.

---

## Firewall und Netztrennung

Firewalls sind besonders wichtig bei VLANs und Netztrennung.

Beispiel:

```text
VLAN 10 Clients
VLAN 20 Gäste
VLAN 30 Server
VLAN 40 Management
```

Mögliche Regeln:

```text
Clients dürfen auf bestimmte Serverdienste.
Gäste dürfen nur ins Internet.
Gäste dürfen nicht auf Server.
Management darf auf Switches und Server.
Server dürfen Updates laden.
```

So wird Kommunikation kontrolliert.

---

## Firewall und Docker

Docker kann Ports vom Container auf den Host veröffentlichen.

Beispiel:

```bash
docker run -p 8080:80 nginx
```

Das bedeutet:

```text
Host-Port 8080 wird auf Container-Port 80 weitergeleitet.
```

Wichtig:

```text
Nur notwendige Ports veröffentlichen.
Datenbankports nicht unnötig nach außen öffnen.
.env-Dateien schützen.
Docker-Netzwerke bewusst nutzen.
```

Schlecht:

```text
PostgreSQL-Port 5432 öffentlich auf Host öffnen, obwohl nur Adminer im Docker-Netz darauf zugreifen muss.
```

Besser:

```text
Datenbank bleibt intern im Docker-Netz.
Nur benötigte Weboberfläche wird bewusst veröffentlicht.
```

---

## Firewall typische Fehler

| Fehler | Problem |
|---|---|
| alle Ports offen | große Angriffsfläche |
| Datenbankport öffentlich | hohes Risiko |
| SSH aus allen Netzen erlaubt | unnötig gefährlich |
| Regeln nicht dokumentiert | spätere Fehlersuche schwer |
| alte Regeln bleiben bestehen | unnötiger Zugriff |
| Firewall als einzige Sicherheit sehen | andere Maßnahmen fehlen |
| Dienststatus nicht prüfen | falsche Diagnose |
| sich selbst aussperren | Remote-Zugriff verloren |
| Gastnetz nicht blockieren | interne Systeme gefährdet |
| Docker-Portfreigaben vergessen | Dienst unerwartet erreichbar |

---

## Updates

Updates schließen Fehler, Sicherheitslücken und Stabilitätsprobleme.

Beispiele:

```text
Betriebssystemupdates
Sicherheitsupdates
Anwendungsupdates
Firmwareupdates
Docker-Image-Updates
Bibliotheksupdates
Browserupdates
```

Updates sind wichtig, weil bekannte Schwachstellen oft aktiv ausgenutzt werden.

Ein System ohne Updates wird mit der Zeit immer riskanter.

---

## Patchmanagement

Patchmanagement bedeutet:

```text
Updates geplant verwalten
```

Dazu gehören:

```text
Systeme erfassen
Updates bewerten
Updates testen
Wartungsfenster planen
Updates installieren
System danach prüfen
Änderungen dokumentieren
Rollback vorbereiten
```

Patchmanagement ist wichtig, weil Updates manchmal Probleme verursachen können.

Trotzdem ist dauerhaftes Aufschieben gefährlich.

---

## Update-Arten

| Update-Art | Bedeutung |
|---|---|
| Sicherheitsupdate | schließt Sicherheitslücken |
| Bugfix | behebt Fehler |
| Feature-Update | bringt neue Funktionen |
| Firmware-Update | aktualisiert Geräte-Firmware |
| Kernel-Update | aktualisiert Betriebssystemkern |
| Paketupdate | aktualisiert Softwarepakete |

Sicherheitsupdates haben oft hohe Priorität.

Feature-Updates müssen manchmal stärker getestet werden.

---

## Updates unter Ubuntu

Paketlisten aktualisieren:

```bash
sudo apt update
```

Pakete aktualisieren:

```bash
sudo apt upgrade
```

System stärker aktualisieren:

```bash
sudo apt full-upgrade
```

Nicht mehr benötigte Pakete entfernen:

```bash
sudo apt autoremove
```

Wichtig:

```text
apt update lädt keine Updates herunter.
apt update aktualisiert nur die Paketlisten.
apt upgrade installiert verfügbare Updates.
```

---

## Update-Status prüfen

Verfügbare Updates anzeigen:

```bash
apt list --upgradable
```

Paketinformationen anzeigen:

```bash
apt show paketname
```

Installierte Pakete suchen:

```bash
apt list --installed | grep paketname
```

Systemversion prüfen:

```bash
lsb_release -a
```

Kernel anzeigen:

```bash
uname -r
```

---

## Updates und Neustart

Manche Updates benötigen einen Neustart.

Typische Beispiele:

```text
Kernel-Updates
wichtige Systembibliotheken
Treiber
bestimmte Dienste
```

Auf Ubuntu kann ein Hinweis erscheinen:

```text
*** System restart required ***
```

Prüfen:

```bash
cat /var/run/reboot-required
```

Nicht jeder Server kann sofort neu gestartet werden.

Dafür braucht man Wartungsfenster und Kommunikation.

---

## Dienste nach Updates prüfen

Nach Updates sollte man prüfen, ob wichtige Dienste laufen.

Beispiele:

```bash
systemctl status ssh
systemctl status nginx
systemctl status docker
```

Offene Ports prüfen:

```bash
ss -tulpen
```

Logs prüfen:

```bash
journalctl -p warning
```

Wichtig:

```text
Update installiert ≠ System funktioniert automatisch perfekt.
```

Nach wichtigen Updates muss getestet werden.

---

## Updates bei Docker

Docker-Container nutzen Images.

Ein Image kann veraltet sein.

Beispiel:

```bash
docker images
```

Neues Image ziehen:

```bash
docker pull nginx:latest
```

Bei Docker Compose:

```bash
docker compose pull
docker compose up -d
```

Wichtig:

```text
latest bedeutet nicht automatisch sicherer oder planbarer.
```

Für produktive Systeme sind feste Versionen oft besser.

Beispiel:

```yaml
image: postgres:16
```

statt unklar:

```yaml
image: postgres:latest
```

---

## Updates und Testumgebung

Updates sollten bei wichtigen Systemen zuerst getestet werden.

Beispiel:

```text
Test-VM
Staging-System
Snapshot vor Update
Backup vor Update
kurzer Funktionstest nach Update
```

Nicht jedes kleine System braucht einen riesigen Prozess.

Aber kritische Systeme sollten nicht blind aktualisiert werden.

---

## Rollback

Rollback bedeutet:

```text
Änderung zurücknehmen
```

Beispiele:

```text
altes Paket wiederherstellen
Konfiguration zurücksetzen
Snapshot zurückrollen
Backup wiederherstellen
Container-Version zurücksetzen
```

Rollback muss vorher mitgedacht werden.

Vor wichtigen Änderungen sollte man fragen:

```text
Wie kommen wir zurück, wenn etwas kaputtgeht?
```

---

## Typische Update-Fehler

| Fehler | Problem |
|---|---|
| Updates nie installieren | bekannte Lücken bleiben offen |
| Updates ohne Prüfung installieren | Dienst kann ausfallen |
| kein Backup vor großer Änderung | Wiederherstellung schwierig |
| Neustart vergessen | Update wirkt nicht vollständig |
| Docker-Images nie aktualisieren | alte Schwachstellen bleiben |
| alles mit `latest` betreiben | schwer planbar |
| keine Dokumentation | Änderung nicht nachvollziehbar |
| keine Tests nach Update | Fehler wird zu spät bemerkt |
| Firmware ignorieren | Netzwerkgeräte bleiben verwundbar |
| alte Systeme weiter betreiben | hoher Sicherheitsaufwand |

---

## Backup

Ein Backup ist eine Sicherung von Daten oder Systemen.

Backups schützen vor:

```text
versehentlichem Löschen
Hardwareausfall
Ransomware
Fehlkonfiguration
defekten Updates
Datenbankfehlern
Diebstahl
Brand
Wasserschaden
```

Ein Backup ist eine der wichtigsten Sicherheitsmaßnahmen überhaupt.

Wichtig:

```text
Backup erstellen reicht nicht.
Restore muss getestet werden.
```

---

## Backup vs Restore

Diese Begriffe gehören zusammen.

| Begriff | Bedeutung |
|---|---|
| Backup | Daten werden gesichert |
| Restore | Daten werden wiederhergestellt |
| Recovery | Betrieb wird wiederhergestellt |
| Snapshot | Zustand zu einem Zeitpunkt |
| Archiv | langfristige Aufbewahrung |

Ein Backup ist nur dann wirklich brauchbar, wenn ein Restore funktioniert.

---

## Was sollte gesichert werden?

Typische Backup-Daten:

```text
Benutzerdaten
Datenbanken
Konfigurationsdateien
Serverdaten
Projektdateien
Dokumentation
VM-Daten
Docker-Volumes
Zertifikate
wichtige Skripte
```

Nicht alles muss gleich behandelt werden.

Wichtige Fragen:

```text
Welche Daten sind kritisch?
Wie oft ändern sie sich?
Wie schnell müssen sie wiederhergestellt werden?
Wie lange müssen sie aufbewahrt werden?
Wer darf auf Backups zugreifen?
```

---

## Backup-Arten

| Backup-Art | Bedeutung |
|---|---|
| Vollbackup | komplette Sicherung |
| inkrementelles Backup | nur Änderungen seit letztem Backup |
| differentielles Backup | Änderungen seit letztem Vollbackup |
| Image-Backup | ganzes Systemabbild |
| Datei-Backup | einzelne Dateien/Ordner |
| Datenbank-Backup | gezielte Sicherung einer Datenbank |

Vollbackups sind einfacher, brauchen aber mehr Speicher.

Inkrementelle Backups sparen Speicher, brauchen aber eine saubere Backup-Kette.

---

## 3-2-1-Regel

Eine bekannte Backup-Regel ist die 3-2-1-Regel.

```text
3 Kopien der Daten
2 unterschiedliche Speichermedien
1 Kopie extern/offsite
```

Beispiel:

```text
Originaldaten auf Server
Backup auf NAS
zusätzliche Kopie extern oder cloudbasiert
```

Diese Regel hilft gegen viele Ausfälle.

Wichtig bei Ransomware:

```text
Backups dürfen nicht dauerhaft einfach beschreibbar für kompromittierte Systeme sein.
```

---

## Offline- und Offsite-Backups

Offline bedeutet:

```text
Backup ist nicht dauerhaft mit dem System verbunden.
```

Offsite bedeutet:

```text
Backup liegt an einem anderen Ort.
```

Warum wichtig?

```text
Ransomware kann erreichbare Backups verschlüsseln.
Brand kann lokale Systeme zerstören.
Diebstahl kann Geräte betreffen.
```

Ein gutes Backup-Konzept berücksichtigt solche Fälle.

---

## Backup-Verschlüsselung

Backups können sensible Daten enthalten.

Deshalb sollten Backups geschützt werden.

Maßnahmen:

```text
Zugriffsrechte begrenzen
Backups verschlüsseln
Backup-Medien sicher lagern
keine öffentlichen Freigaben
Backup-Logs prüfen
Schlüssel sicher verwalten
```

Wichtig:

```text
Ein Backup mit Kundendaten ist genauso schützenswert wie das Originalsystem.
```

---

## Restore-Test

Ein Restore-Test prüft, ob Daten wirklich wiederhergestellt werden können.

Beispiele:

```text
einzelne Datei wiederherstellen
Datenbank in Testumgebung wiederherstellen
VM aus Backup starten
Konfiguration zurückspielen
kompletten Server-Wiederaufbau testen
```

Ein Restore-Test beantwortet:

```text
Funktioniert das Backup?
Wie lange dauert die Wiederherstellung?
Sind alle wichtigen Daten vorhanden?
Ist die Anleitung korrekt?
```

---

## RPO und RTO

In Backup-Konzepten gibt es zwei wichtige Begriffe.

| Begriff | Bedeutung | Frage |
|---|---|---|
| RPO | Recovery Point Objective | Wie viel Datenverlust ist maximal akzeptabel? |
| RTO | Recovery Time Objective | Wie lange darf die Wiederherstellung dauern? |

Beispiel:

```text
RPO: maximal 4 Stunden Datenverlust
RTO: System muss innerhalb von 2 Stunden wieder laufen
```

Diese Werte helfen bei der Planung von Backup und Wiederherstellung.

---

## Backup und Datenbanken

Datenbanken brauchen besondere Aufmerksamkeit.

Es reicht nicht immer, einfach den Datenordner zu kopieren, während die Datenbank läuft.

Mögliche Methoden:

```text
Datenbank-Dump
datenbankeigene Backup-Funktion
konsistenter Snapshot
Replikation plus Backup
```

Beispiel PostgreSQL-Dump:

```bash
pg_dump datenbankname > backup.sql
```

Bei Docker kann ein Datenbank-Backup über `docker exec` durchgeführt werden, je nach Setup.

Wichtig:

```text
Datenbank-Backups müssen konsistent sein.
Restore muss getestet werden.
```

---

## Backup und Docker-Volumes

Docker-Volumes können wichtige Daten enthalten.

Beispiele:

```text
PostgreSQL-Daten
Uploads
Konfigurationsdaten
Anwendungsdaten
```

Prüfen:

```bash
docker volume ls
```

Compose-Dateien prüfen:

```bash
docker compose config
```

Wichtig:

```text
Container löschen ist nicht immer Datenverlust.
Volume löschen kann Datenverlust sein.
```

Besonders gefährlich:

```bash
docker compose down -v
```

Das kann Volumes entfernen.

---

## Snapshot ist kein vollständiges Backup

Snapshots sind praktisch, aber nicht automatisch vollständige Backups.

Ein Snapshot ist ein Zustand zu einem Zeitpunkt.

Nützlich bei:

```text
Tests
Updates
kurzfristiger Rückkehrpunkt
VM-Labor
```

Problem:

```text
Snapshot liegt oft auf demselben System.
Snapshot schützt nicht immer gegen Hardwareausfall.
Snapshot wird manchmal zu lange behalten.
```

Für wichtige Daten braucht man echte Backups.

---

## Backup-Dokumentation

Ein Backup-Konzept sollte dokumentiert sein.

Wichtige Punkte:

```text
Was wird gesichert?
Wie oft wird gesichert?
Wohin wird gesichert?
Wie lange wird aufbewahrt?
Wer ist verantwortlich?
Wie wird Restore getestet?
Welche Systeme sind kritisch?
Welche RPO/RTO gelten?
Wie werden Fehler gemeldet?
```

Ohne Dokumentation ist im Notfall unklar, was zu tun ist.

---

## Beispiel Backup-Plan

Ein einfacher Backup-Plan:

| System | Daten | Häufigkeit | Aufbewahrung | Restore-Test |
|---|---|---|---|---|
| Dateiserver | Abteilungsdaten | täglich | 30 Tage | monatlich |
| Datenbank | SQL-Dump | täglich | 14 Tage | monatlich |
| Git-Repos | Projektcode | laufend remote | dauerhaft | bei Bedarf |
| VM | Systemabbild | wöchentlich | 4 Wochen | quartalsweise |
| Dokumentation | Markdown/Docs | täglich | 30 Tage | monatlich |

Das ist nur ein Beispiel. In echten Umgebungen hängt der Plan vom Schutzbedarf ab.

---

## Beispiel: Server absichern

Ein einfacher sicherer Serverbetrieb kann so aussehen:

```text
Firewall aktiv
nur SSH und benötigte Dienste offen
Updates regelmäßig installiert
Backups eingerichtet
Restore getestet
Logs werden geprüft
Dienste laufen nur wenn nötig
Zugriffe dokumentiert
```

Befehle:

```bash
sudo ufw status
sudo apt update
apt list --upgradable
ss -tulpen
systemctl status ssh
journalctl -u ssh
```

---

## Beispiel: Webserver

Ein Webserver braucht oft:

```text
HTTP/HTTPS
regelmäßige Updates
Firewall-Regeln
TLS-Zertifikat
Logs
Backup der Konfiguration
Backup der Webdaten
Monitoring
```

Ports:

```text
80/tcp
443/tcp
```

Nicht nötig ist meistens:

```text
Datenbankport öffentlich
Admin-Oberfläche ohne Schutz
SSH aus allen Netzen
```

---

## Beispiel: Ransomware

Ransomware verschlüsselt Daten und fordert oft Geld.

Betroffene Schutzziele:

```text
Verfügbarkeit
Integrität
eventuell Vertraulichkeit
```

Wichtige Schutzmaßnahmen:

```text
Updates
MFA
Least Privilege
E-Mail-Schutz
Schulung
Netztrennung
Backups
Offline/Offsite-Backups
Restore-Tests
Monitoring
```

Backups sind hier besonders wichtig.

Aber nur dann, wenn sie nicht ebenfalls verschlüsselt wurden und die Wiederherstellung funktioniert.

---

## Typische Fehler bei Backups

| Fehler | Problem |
|---|---|
| kein Backup | Datenverlust kann endgültig sein |
| Backup nie getestet | Restore im Notfall unsicher |
| Backup dauerhaft beschreibbar | Ransomware kann es verschlüsseln |
| Backup liegt nur am selben Ort | Brand/Diebstahl gefährdet alles |
| Backup enthält nicht alle Daten | Wiederherstellung unvollständig |
| Backup-Zugang zu offen | Daten können gestohlen werden |
| keine Dokumentation | niemand weiß, wie Restore geht |
| Datenbank falsch gesichert | Backup ist inkonsistent |
| Snapshot mit Backup verwechselt | falsches Sicherheitsgefühl |
| Backup-Fehler ignoriert | Sicherung läuft vielleicht nicht |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Firewall, Updates und Backup:

```text
nur notwendige Ports öffnen
Firewall-Regeln dokumentieren
offene Dienste regelmäßig prüfen
Updates geplant installieren
kritische Updates priorisieren
nach Updates Dienste testen
vor großen Änderungen Backup prüfen
Backups regelmäßig durchführen
Restore regelmäßig testen
Backup-Zugriffe schützen
```

Wichtige Regel:

```text
Sicherheit muss überprüfbar sein.
```

Nicht nur sagen:

```text
Backup läuft.
```

Sondern prüfen:

```text
Backup erfolgreich?
Restore getestet?
Daten vollständig?
Zugriff geschützt?
```

---

## Praktische Befehle

### Firewall prüfen

```bash
sudo ufw status
sudo ufw status verbose
sudo ufw status numbered
```

### Ports prüfen

```bash
ss -tulpen
```

### Updates prüfen

```bash
sudo apt update
apt list --upgradable
sudo apt upgrade
```

### Neustart prüfen

```bash
cat /var/run/reboot-required
```

### Dienste prüfen

```bash
systemctl status ssh
systemctl status nginx
systemctl status docker
```

### Logs prüfen

```bash
journalctl -u ssh
journalctl -p warning
```

### Docker prüfen

```bash
docker ps
docker images
docker volume ls
docker compose ps
docker compose logs
```

---

## FISI-Bezug

Firewall, Updates und Backup gehören direkt zur FISI-Praxis.

Man braucht dieses Wissen für:

```text
Server sicher betreiben
Clients absichern
Firewall-Regeln verstehen
offene Ports prüfen
Updates planen
Patchmanagement durchführen
Dienste nach Updates testen
Backups einrichten
Restore-Tests durchführen
Datenbank-Backups verstehen
Docker-Volumes schützen
VM-Snapshots richtig einordnen
Dokumentation schreiben
Sicherheitsrisiken erkennen
```

Ein FISI muss nicht nur Systeme zum Laufen bringen.

Ein FISI muss Systeme sicher, aktuell, kontrolliert und wiederherstellbar betreiben.

---

## Kurze Zusammenfassung

Firewalls kontrollieren Netzwerkverkehr und reduzieren unnötige Zugriffe.

Updates schließen Fehler und Sicherheitslücken. Patchmanagement sorgt dafür, dass Updates geplant, geprüft und dokumentiert werden.

Backups schützen vor Datenverlust, Ausfällen und Angriffen. Wichtig ist nicht nur das Backup selbst, sondern auch der getestete Restore.

Für FISI sind Firewall, Updates und Backup zentrale Alltagsthemen, weil sie direkt mit Serverbetrieb, Netzwerken, Linux, Docker, Virtualisierung, Datenschutz und IT-Sicherheit zusammenhängen.