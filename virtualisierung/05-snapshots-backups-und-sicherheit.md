# 5. Snapshots, Backups und Sicherheit

In diesem Kapitel geht es um Snapshots, Backups und Sicherheit bei virtuellen Maschinen.

Virtuelle Maschinen sind praktisch, weil man sie schnell erstellen, kopieren, testen und zurücksetzen kann. Trotzdem muss man vorsichtig arbeiten. Ein Snapshot ist kein echtes Backup, und eine VM ist nicht automatisch sicher, nur weil sie virtuell ist.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil VMs in Unternehmen oft wichtige Dienste betreiben. Wenn Snapshots falsch genutzt, Backups nicht getestet oder VMs schlecht abgesichert werden, kann das zu Datenverlust, Ausfällen oder Sicherheitsproblemen führen.

---

## Kurz erklärt

Snapshots speichern einen Zustand einer VM zu einem bestimmten Zeitpunkt.

Backups sichern Daten oder Systeme für eine echte Wiederherstellung.

Sicherheit bedeutet, dass die VM geschützt betrieben wird.

Vereinfacht:

```text
Snapshot = kurzer Rücksprungpunkt für Tests
Backup = echte Sicherung für Wiederherstellung
Sicherheit = VM sauber absichern und pflegen
```

Wichtige Regel:

```text
Ein Snapshot ersetzt kein Backup.
```

---

## Was ist ein Snapshot?

Ein Snapshot speichert den Zustand einer virtuellen Maschine zu einem bestimmten Zeitpunkt.

Gespeichert werden können je nach System:

```text
Zustand der virtuellen Festplatte
VM-Konfiguration
RAM-Zustand
laufender Zustand der VM
```

Typische Nutzung:

```text
vor Updates
vor Softwareinstallation
vor Konfigurationsänderungen
vor Tests
vor Schulungsübungen
```

Wenn etwas schiefgeht, kann man die VM auf den Snapshot zurücksetzen.

---

## Beispiel für einen Snapshot

Situation:

```text
Eine Ubuntu Server VM soll aktualisiert werden.
```

Sinnvolle Arbeitsweise:

```text
1. Snapshot erstellen
2. Updates installieren
3. Dienste prüfen
4. Wenn alles funktioniert, Snapshot später löschen
5. Wenn Fehler auftreten, Snapshot zurücksetzen
```

Der Snapshot hilft hier beim Testen.

Er ist aber nicht als langfristige Sicherung gedacht.

---

## Vorteile von Snapshots

Snapshots haben einige Vorteile.

| Vorteil | Erklärung |
|---|---|
| schneller Rücksprung | VM kann auf alten Zustand zurückgesetzt werden |
| gut für Tests | riskante Änderungen können ausprobiert werden |
| praktisch beim Lernen | Fehler können rückgängig gemacht werden |
| hilfreich bei Updates | Zustand vor Update kann gespeichert werden |
| einfache Wiederholung | Übungsumgebungen können zurückgesetzt werden |

Snapshots sind besonders praktisch in Laboren, Schulungen und Testumgebungen.

---

## Nachteile von Snapshots

Snapshots haben auch Risiken.

| Nachteil | Erklärung |
|---|---|
| kein echtes Backup | liegt oft auf demselben Host oder Storage |
| Speicherverbrauch | Snapshots können viel Platz belegen |
| Performance | lange Snapshot-Ketten können Systeme verlangsamen |
| falsches Sicherheitsgefühl | man denkt, Daten seien sicher |
| Verwaltung wird unübersichtlich | viele alte Snapshots erschweren Überblick |
| Risiko bei produktiven Systemen | falsches Zurücksetzen kann Datenverlust verursachen |

Ein Snapshot ist gut für kurze Zeiträume, aber schlecht als Dauerlösung.

---

## Warum Snapshots keine Backups sind

Ein Snapshot liegt meistens zusammen mit der VM auf demselben Host oder Storage.

Problem:

```text
Host-Festplatte geht kaputt.
VM ist weg.
Snapshot ist auch weg.
```

Ein Backup sollte unabhängig vom ursprünglichen System gespeichert werden.

Besser:

```text
VM läuft auf Host.
Backup liegt auf anderem Speicher.
Restore wurde getestet.
```

Wichtiger Satz:

```text
Snapshot schützt vor manchen Änderungen.
Backup schützt vor Datenverlust.
```

---

## Snapshot-Ketten

Wenn mehrere Snapshots erstellt werden, entstehen Snapshot-Ketten.

Beispiel:

```text
Basiszustand
└── Snapshot 1
    └── Snapshot 2
        └── Snapshot 3
```

Problem:

```text
je länger die Kette, desto unübersichtlicher
Speicherverbrauch steigt
Performance kann schlechter werden
Fehler werden schwerer nachvollziehbar
```

Deshalb sollte man Snapshots nicht dauerhaft liegen lassen.

Gute Arbeitsweise:

```text
Snapshot erstellen
Änderung testen
Ergebnis prüfen
Snapshot löschen oder sauber konsolidieren
```

---

## Snapshots sinnvoll benennen

Snapshots sollten klare Namen haben.

Schlecht:

```text
snapshot1
test
neu
vorher
asdf
```

Besser:

```text
2026-09-02-vor-updates
2026-09-02-vor-docker-installation
2026-09-02-vor-firewall-test
```

Ein guter Snapshot-Name zeigt:

```text
Datum
Zweck
Grund
```

Das hilft, später nicht den falschen Zustand wiederherzustellen.

---

## Was ist ein Backup?

Ein Backup ist eine Sicherung von Daten oder Systemen.

Ziel:

```text
Daten nach Verlust, Fehler oder Ausfall wiederherstellen können.
```

Backups schützen zum Beispiel gegen:

```text
versehentliches Löschen
defekte Festplatte
kaputte VM-Datei
Ransomware
falsche Konfiguration
Systemausfall
Datenbankfehler
```

Ein Backup ist nur dann gut, wenn es wiederhergestellt werden kann.

---

## Backup-Arten bei VMs

Bei virtuellen Maschinen gibt es verschiedene Backup-Arten.

| Backup-Art | Bedeutung |
|---|---|
| VM-Backup | komplette VM wird gesichert |
| Disk-Backup | virtuelle Festplatte wird gesichert |
| Datei-Backup | bestimmte Dateien in der VM werden gesichert |
| Datenbank-Backup | Datenbank wird gezielt exportiert |
| Konfigurationsbackup | wichtige Einstellungen werden gesichert |
| Image-Backup | gesamtes Systemabbild wird gesichert |

Je nach System braucht man manchmal mehrere Arten.

Beispiel:

```text
VM-Backup für kompletten Server
Datenbank-Dump für saubere Datenbank-Wiederherstellung
Konfigurationsbackup für wichtige Einstellungen
```

---

## Vollbackup

Ein Vollbackup sichert alle ausgewählten Daten komplett.

Beispiel:

```text
komplette VM
komplette virtuelle Festplatte
kompletter Projektordner
komplette Datenbank
```

Vorteil:

```text
einfach zu verstehen
vollständige Sicherung
```

Nachteil:

```text
braucht viel Speicherplatz
dauert länger
```

Vollbackups sind wichtig, aber oft nicht allein ausreichend für große Umgebungen.

---

## Inkrementelles Backup

Ein inkrementelles Backup sichert nur Änderungen seit dem letzten Backup.

Beispiel:

```text
Montag: Vollbackup
Dienstag: Änderungen seit Montag
Mittwoch: Änderungen seit Dienstag
Donnerstag: Änderungen seit Mittwoch
```

Vorteil:

```text
spart Speicherplatz
schneller als Vollbackup
```

Nachteil:

```text
Wiederherstellung kann komplexer sein
mehrere Backupstände werden benötigt
```

---

## Differenzielles Backup

Ein differenzielles Backup sichert Änderungen seit dem letzten Vollbackup.

Beispiel:

```text
Montag: Vollbackup
Dienstag: Änderungen seit Montag
Mittwoch: Änderungen seit Montag
Donnerstag: Änderungen seit Montag
```

Vorteil:

```text
einfachere Wiederherstellung als inkrementell
```

Nachteil:

```text
braucht mit der Zeit mehr Speicherplatz
```

---

## Backup-Planung

Ein Backup muss geplant werden.

Wichtige Fragen:

```text
Was wird gesichert?
Wie oft wird gesichert?
Wo wird gesichert?
Wie lange werden Backups aufbewahrt?
Wer hat Zugriff?
Ist das Backup verschlüsselt?
Wie wird die Wiederherstellung getestet?
Wie lange darf ein Ausfall dauern?
Wie viele Daten dürfen maximal verloren gehen?
```

Ohne klare Planung weiß man im Notfall oft nicht, welches Backup wirklich brauchbar ist.

---

## RPO und RTO

Bei Backup-Konzepten sind zwei Begriffe wichtig.

| Begriff | Bedeutung |
|---|---|
| RPO | wie viele Daten maximal verloren gehen dürfen |
| RTO | wie lange die Wiederherstellung maximal dauern darf |

RPO bedeutet:

```text
Recovery Point Objective
```

Beispiel:

```text
RPO 24 Stunden
```

Das bedeutet:

```text
Im schlimmsten Fall dürfen Daten der letzten 24 Stunden verloren gehen.
```

RTO bedeutet:

```text
Recovery Time Objective
```

Beispiel:

```text
RTO 4 Stunden
```

Das bedeutet:

```text
Das System soll innerhalb von 4 Stunden wieder laufen.
```

---

## Restore-Test

Ein Restore-Test prüft, ob ein Backup wirklich wiederhergestellt werden kann.

Beispiele:

```text
einzelne Datei wiederherstellen
Datenbank in Testumgebung wiederherstellen
VM aus Backup starten
Konfigurationsdatei zurückspielen
kompletten Server neu aufbauen
```

Ein Restore-Test zeigt:

```text
ob das Backup vollständig ist
ob die Anleitung stimmt
wie lange die Wiederherstellung dauert
ob Berechtigungen erhalten bleiben
ob Dienste nach Restore starten
```

Wichtiger Satz:

```text
Nicht das Backup zählt, sondern der erfolgreiche Restore.
```

---

## Backup-Speicherort

Backups sollten nicht nur auf demselben Host liegen wie die VM.

Schlecht:

```text
VM liegt auf Host.
Backup liegt im gleichen Ordner auf demselben Host.
```

Problem:

```text
Wenn der Host kaputtgeht, sind VM und Backup weg.
```

Besser:

```text
Backup auf anderem Storage
Backup auf NAS
Backup auf externem Datenträger
Backup in separater Backup-Umgebung
zusätzliche Offsite-Sicherung
```

Das Ziel ist, dass nicht ein einzelner Fehler alles zerstört.

---

## 3-2-1-Regel

Eine bekannte Backup-Idee ist die 3-2-1-Regel.

Sie bedeutet:

```text
3 Kopien der Daten
2 unterschiedliche Speichermedien
1 Kopie an einem anderen Ort
```

Beispiel:

```text
Produktivdaten auf Server
Backup auf NAS
zusätzliche Kopie extern oder Offsite
```

Diese Regel hilft, Backups robuster zu planen.

---

## Verschlüsselung von Backups

Backups können sehr viele sensible Daten enthalten.

Beispiele:

```text
Kundendaten
Personaldaten
Datenbanken
E-Mails
Konfigurationen
Zugangsdaten
Logs
```

Deshalb sollten Backups geschützt werden.

Maßnahmen:

```text
Backup verschlüsseln
Zugriff begrenzen
Backup-Speicher absichern
Passwörter und Schlüssel sicher verwalten
Backup-Zugriffe protokollieren
```

Ein ungeschütztes Backup kann gefährlicher sein als ein einzelner offener Ordner, weil es sehr viele Daten enthält.

---

## Sicherheit von VMs

Eine VM muss wie ein echtes System abgesichert werden.

Wichtige Punkte:

```text
Updates installieren
Firewall aktivieren oder prüfen
nur notwendige Dienste starten
starke Passwörter oder SSH-Schlüssel nutzen
Adminrechte begrenzen
Logs prüfen
Backups schützen
Netzwerkmodus bewusst wählen
Snapshots kontrolliert nutzen
```

Eine VM im Bridge-Modus ist im LAN sichtbar und sollte besonders sauber abgesichert werden.

---

## Updates in VMs

VMs müssen regelmäßig aktualisiert werden.

Linux-Beispiel:

```bash
sudo apt update
sudo apt upgrade
```

Dienste prüfen:

```bash
systemctl status ssh
```

Offene Ports prüfen:

```bash
ss -tulpen
```

Wichtig:

```text
Eine alte Test-VM kann Sicherheitslücken enthalten.
Auch Labor-VMs sollten nicht dauerhaft ungepflegt laufen.
```

---

## Firewall in VMs

Eine Firewall begrenzt Zugriffe.

Unter Ubuntu kann man zum Beispiel UFW nutzen.

Status prüfen:

```bash
sudo ufw status
```

SSH erlauben:

```bash
sudo ufw allow ssh
```

Firewall aktivieren:

```bash
sudo ufw enable
```

Wichtig:

```text
Nur notwendige Ports öffnen.
Nicht alles freigeben, nur weil es im Lab einfacher ist.
```

---

## Offene Ports prüfen

Offene Ports zeigen, welche Dienste erreichbar sind.

Befehl:

```bash
ss -tulpen
```

Typische Ports:

```text
22   SSH
80   HTTP
443  HTTPS
3306 MySQL/MariaDB
5432 PostgreSQL
```

Wichtige Fragen:

```text
Braucht die VM diesen Dienst wirklich?
Soll der Dienst aus dem LAN erreichbar sein?
Ist die Firewall korrekt eingestellt?
Ist der Dienst aktuell?
```

---

## SSH absichern

SSH ist wichtig für Linux-Server, aber auch ein häufiges Angriffsziel.

Gute Maßnahmen:

```text
starke Passwörter oder SSH-Schlüssel nutzen
MFA prüfen, wenn verfügbar
Root-Login vermeiden
nur notwendige Benutzer erlauben
Firewall-Regeln setzen
SSH-Logs prüfen
```

SSH-Status prüfen:

```bash
systemctl status ssh
```

SSH-Logs ansehen:

```bash
journalctl -u ssh
```

---

## VM-Netzwerk und Sicherheit

Der Netzwerkmodus beeinflusst die Sicherheit.

| Modus | Sicherheitswirkung |
|---|---|
| NAT | VM ist meist weniger direkt erreichbar |
| Bridge | VM ist wie eigenes Gerät im LAN sichtbar |
| Host-only | VM ist eher isoliert zwischen Host und VM |
| Internal Network | VMs sind vom echten LAN getrennt |

Wichtige Regel:

```text
Erreichbarkeit ist immer auch ein Sicherheitsrisiko.
```

Eine VM sollte nur dort erreichbar sein, wo es wirklich nötig ist.

---

## Alte VMs

Alte VMs sind ein häufiges Risiko.

Probleme:

```text
veraltete Updates
alte Benutzerkonten
schwache Passwörter
vergessene Dienste
unnötig offene Ports
unklare Daten
veraltete Snapshots
Speicherverbrauch
```

Gute Arbeitsweise:

```text
alte VMs stoppen
nicht mehr benötigte VMs löschen
wichtige VMs archivieren
Dokumentation aktualisieren
Backups prüfen
```

Alte Testsysteme sollten nicht unkontrolliert weiterlaufen.

---

## Snapshots sicher nutzen

Gute Regeln für Snapshots:

```text
Snapshot nur mit klarem Zweck erstellen
Snapshot sinnvoll benennen
Snapshot nicht monatelang liegen lassen
nach erfolgreichem Test bereinigen
nicht als Backup verwenden
vor produktiven Änderungen besonders vorsichtig sein
```

Beispiel guter Name:

```text
2026-09-02-vor-security-updates
```

Beispiel schlechter Name:

```text
test123
```

---

## Backups sicher nutzen

Gute Regeln für Backups:

```text
regelmäßig sichern
Backup-Speicher schützen
Backup verschlüsseln
Zugriff begrenzen
Restore testen
Backup-Logs prüfen
Aufbewahrung planen
alte Backups kontrolliert löschen
```

Ein Backup-Konzept muss nicht nur existieren.

Es muss auch funktionieren.

---

## Dokumentation

Snapshots, Backups und Sicherheitsmaßnahmen sollten dokumentiert werden.

Dokumentiert werden sollte:

```text
Name der VM
Zweck der VM
Backup-Zeitplan
Backup-Speicherort
letzter erfolgreicher Restore-Test
wichtige Snapshots
offene Ports
Firewall-Regeln
Adminzugriffe
besondere Sicherheitsmaßnahmen
```

Beispiel:

```text
VM: ubuntu-server-lab
Backup: manuell nach größeren Änderungen
Snapshot: vor Updates
Firewall: UFW aktiv, SSH erlaubt
Restore-Test: Datei-Restore am 02.09.2026 erfolgreich
```

Dokumentation hilft besonders im Notfall.

---

## Beispiel 1: Snapshot vor Update

Situation:

```text
Eine VM soll aktualisiert werden.
```

Ablauf:

```text
Snapshot erstellen
Updates installieren
Dienste prüfen
Logs prüfen
bei Erfolg Snapshot später löschen
bei Fehler Snapshot zurücksetzen
```

Prüfen:

```bash
sudo apt update
sudo apt upgrade
systemctl status ssh
journalctl -p err
```

---

## Beispiel 2: Backup einer wichtigen VM

Situation:

```text
Eine VM enthält wichtige Projektdaten.
```

Gute Arbeitsweise:

```text
regelmäßiges Backup einrichten
Backup auf anderem Speicher ablegen
Backup verschlüsseln
Restore-Test durchführen
Backup-Dokumentation schreiben
```

Nicht ausreichend:

```text
Snapshot erstellen und hoffen, dass das reicht.
```

---

## Beispiel 3: Alte Test-VM aufräumen

Situation:

```text
Mehrere alte Test-VMs laufen noch auf dem Host.
```

Risiken:

```text
Speicher wird verbraucht
alte Sicherheitslücken bleiben offen
unklare Dienste laufen weiter
Netzwerk wird unübersichtlich
```

Gute Reaktion:

```text
prüfen, welche VMs noch gebraucht werden
wichtige Daten sichern
nicht benötigte VMs löschen
Dokumentation aktualisieren
```

---

## Beispiel 4: Bridge-VM absichern

Situation:

```text
Eine Ubuntu Server VM läuft im Bridge-Modus.
Sie ist im LAN erreichbar.
```

Prüfen:

```bash
ip a
ss -tulpen
sudo ufw status
systemctl status ssh
```

Gute Maßnahmen:

```text
nur notwendige Dienste aktivieren
Firewall korrekt setzen
Updates installieren
SSH absichern
VM dokumentieren
```

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| Snapshot als Backup nutzen | Datenverlust bei Host- oder Storage-Ausfall möglich |
| Snapshots monatelang behalten | Speicherverbrauch und Performanceprobleme |
| Snapshots schlecht benennen | falscher Zustand wird wiederhergestellt |
| Backup nie testen | Restore im Notfall unsicher |
| Backup auf gleichem Host speichern | Host-Ausfall zerstört VM und Backup |
| Backups nicht verschlüsseln | sensible Daten können offengelegt werden |
| alte VMs weiterlaufen lassen | Sicherheitsrisiko und Ressourcenverbrauch |
| VM ohne Updates betreiben | bekannte Sicherheitslücken bleiben |
| zu viele Ports öffnen | größere Angriffsfläche |
| keine Dokumentation | Wiederherstellung und Fehlersuche schwer |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Snapshots, Backups und Sicherheit:

```text
Snapshots nur gezielt nutzen
Snapshots klar benennen
Snapshots nach Tests bereinigen
Backups regelmäßig erstellen
Backups getrennt speichern
Backups schützen und verschlüsseln
Restore regelmäßig testen
VMs aktuell halten
Firewall und offene Ports prüfen
alte VMs aufräumen
wichtige Maßnahmen dokumentieren
```

Wichtige Regel:

```text
Schnell zurücksetzen ist gut.
Sicher wiederherstellen ist wichtiger.
```

---

## Praktische Befehle

### Updates installieren

```bash
sudo apt update
sudo apt upgrade
```

### Speicherplatz prüfen

```bash
df -h
```

### RAM prüfen

```bash
free -h
```

### Offene Ports prüfen

```bash
ss -tulpen
```

### Firewall prüfen

```bash
sudo ufw status
```

### SSH prüfen

```bash
systemctl status ssh
```

### SSH-Logs prüfen

```bash
journalctl -u ssh
```

---

## FISI-Bezug

Snapshots, Backups und Sicherheit sind wichtige Themen für FISI.

Man braucht dieses Wissen für:

```text
Serverbetrieb
VM-Verwaltung
Patchmanagement
Backup-Konzepte
Restore-Tests
IT-Sicherheit
Troubleshooting
Dokumentation
Home-Lab
Prüfungsvorbereitung
```

Ein FISI sollte erklären können:

```text
warum ein Snapshot kein Backup ist
wie man Backups plant
warum Restore-Tests wichtig sind
wie man VMs absichert
warum alte VMs ein Risiko sind
wie man Sicherheitsmaßnahmen dokumentiert
```

---

## Kurze Zusammenfassung

Snapshots speichern einen VM-Zustand zu einem bestimmten Zeitpunkt und sind gut für kurze Tests oder Änderungen.

Backups sind echte Sicherungen, die für Wiederherstellung nach Datenverlust, Fehlern oder Ausfällen gedacht sind.

Ein Snapshot ersetzt kein Backup, weil er oft vom gleichen Host oder Storage abhängig ist.

VMs müssen wie echte Systeme gepflegt werden: Updates, Firewall, SSH-Sicherheit, Backup, Restore-Test, saubere Dokumentation und bewusste Netzwerkeinstellungen.

Für FISI ist dieses Thema wichtig, weil virtuelle Systeme in der Praxis nur dann zuverlässig sind, wenn sie nicht nur laufen, sondern auch gesichert, getestet und geschützt werden.