# 8. Logs und Fehlersuche

In diesem Kapitel geht es um Logs und systematische Fehlersuche unter Linux.

Logs sind Protokolle, in denen das System, Dienste und Programme wichtige Ereignisse speichern. Sie zeigen zum Beispiel, ob ein Dienst gestartet wurde, warum ein Fehler aufgetreten ist, ob eine Anmeldung fehlgeschlagen ist oder ob ein Paket installiert wurde.

Für Fachinformatiker für Systemintegration sind Logs sehr wichtig, weil man Fehler nicht nur raten sollte. Man muss Hinweise sammeln, Meldungen lesen, Ursachen eingrenzen und passende Maßnahmen ableiten.

---

## Kurz erklärt

Logs helfen dabei, Probleme nachvollziehbar zu analysieren.

Typische Fragen bei der Fehlersuche:

- Was funktioniert nicht?
- Seit wann besteht der Fehler?
- Welcher Dienst ist betroffen?
- Gibt es Fehlermeldungen?
- Welche Logs passen zum Problem?
- Wurde vorher etwas geändert?
- Läuft der Dienst?
- Ist ein Port offen?
- Gibt es Rechteprobleme?
- Ist Speicherplatz voll?
- Funktioniert das Netzwerk?
- Gibt es Hinweise im systemd-Journal?

Wichtige Werkzeuge:

```bash
journalctl
systemctl status
tail
less
grep
dmesg
df -h
free -h
ss -tulpen
```

---

## Warum Logs wichtig sind

Logs sind eine der wichtigsten Informationsquellen bei Fehlern.

Ohne Logs sieht man oft nur das Symptom.

Beispiel:

```text
Webseite ist nicht erreichbar.
```

Das sagt noch nicht, warum.

Mögliche Ursachen:

- Webserver läuft nicht
- Port ist blockiert
- DNS zeigt falsch
- Firewall blockiert
- Konfigurationsfehler
- Zertifikat fehlt
- Speicherplatz ist voll
- Rechteproblem
- Datenbank ist nicht erreichbar

Logs können Hinweise geben, welche Ursache wahrscheinlich ist.

---

## Typische Log-Orte

Viele klassische Logdateien liegen unter:

```text
/var/log
```

Anzeigen:

```bash
ls /var/log
```

Wichtige Logdateien und Ordner:

| Pfad                       | Bedeutung                                                    |
| -------------------------- | ------------------------------------------------------------ |
| `/var/log/syslog`          | allgemeine Systemmeldungen auf vielen Debian/Ubuntu-Systemen |
| `/var/log/auth.log`        | Anmeldungen, sudo, SSH und Authentifizierung                 |
| `/var/log/kern.log`        | Kernel-Meldungen                                             |
| `/var/log/apt/history.log` | apt-Installationen und Updates                               |
| `/var/log/apt/term.log`    | ausführliche apt-Ausgaben                                    |
| `/var/log/dpkg.log`        | Paketaktionen von dpkg                                       |
| `/var/log/nginx/`          | Nginx-Logs                                                   |
| `/var/log/apache2/`        | Apache-Logs                                                  |
| `/var/log/mysql/`          | MySQL/MariaDB-Logs, falls vorhanden                          |

Nicht jede Distribution nutzt exakt dieselben Dateien.

Auf modernen Systemen ist zusätzlich `journalctl` sehr wichtig.

---

## systemd-Journal

Viele moderne Linux-Systeme nutzen systemd.

Zu systemd gehört auch ein Logging-System: das Journal.

Logs aus dem Journal liest man mit:

```bash
journalctl
```

Das systemd-Journal sammelt Meldungen von:

- systemd
- Diensten
- Kernel
- Bootvorgang
- Anwendungen
- Hintergrundprozessen

Für die Fehlersuche ist `journalctl` einer der wichtigsten Befehle.

---

## journalctl Grundlagen

Alle Logs anzeigen:

```bash
journalctl
```

Letzte Meldungen anzeigen:

```bash
journalctl -n 50
```

Logs live verfolgen:

```bash
journalctl -f
```

Logs seit dem aktuellen Boot:

```bash
journalctl -b
```

Logs eines Dienstes anzeigen:

```bash
journalctl -u ssh
```

Beispiel:

```bash
journalctl -u docker
```

Damit sieht man Logs des Docker-Dienstes.

---

## Logs eines Dienstes prüfen

Wenn ein Dienst nicht funktioniert, prüft man zuerst Status und Logs.

Beispiel SSH:

```bash
systemctl status ssh
journalctl -u ssh -n 100
```

Beispiel Docker:

```bash
systemctl status docker
journalctl -u docker -n 100
```

Beispiel Nginx:

```bash
systemctl status nginx
journalctl -u nginx -n 100
```

`systemctl status` zeigt oft schon die letzten Logzeilen.

`journalctl -u` zeigt mehr Details.

---

## Logs live verfolgen

Live-Logs sind nützlich, wenn man einen Fehler direkt nachstellen will.

Beispiel:

```bash
journalctl -u ssh -f
```

Dann versucht man in einem zweiten Terminal eine SSH-Verbindung.

Neue Meldungen erscheinen direkt.

Auch klassische Logdateien kann man live verfolgen:

```bash
tail -f /var/log/syslog
```

Oder:

```bash
sudo tail -f /var/log/auth.log
```

Beenden:

```text
Ctrl + C
```

---

## Logs nach Zeit filtern

Mit `journalctl` kann man Logs nach Zeit filtern.

Beispiele:

```bash
journalctl --since "today"
journalctl --since "1 hour ago"
journalctl --since "2026-08-18 10:00"
journalctl --until "2026-08-18 12:00"
```

Für einen Dienst:

```bash
journalctl -u ssh --since "30 minutes ago"
```

Das ist sehr wichtig, wenn ein Fehler zu einem bestimmten Zeitpunkt aufgetreten ist.

Beispiel:

Ein Benutzer sagt: „Seit 14:00 funktioniert SSH nicht mehr.“

Dann prüft man:

```bash
journalctl -u ssh --since "2026-08-18 14:00"
```

---

## Log-Level

Logs haben oft verschiedene Schweregrade.

Typische Level:

| Level     | Bedeutung                               |
| --------- | --------------------------------------- |
| debug     | sehr detaillierte Diagnoseinformationen |
| info      | normale Information                     |
| notice    | wichtige normale Meldung                |
| warning   | Warnung, mögliches Problem              |
| error     | Fehler                                  |
| critical  | kritischer Fehler                       |
| alert     | sofortiges Eingreifen nötig             |
| emergency | System ist kaum nutzbar                 |

Mit `journalctl` kann man nach Priorität filtern.

Nur Fehler und schlimmer:

```bash
journalctl -p err
```

Fehler seit aktuellem Boot:

```bash
journalctl -b -p err
```

Fehler eines Dienstes:

```bash
journalctl -u nginx -p err
```

---

## systemctl --failed

Fehlgeschlagene Dienste anzeigen:

```bash
systemctl --failed
```

Dieser Befehl ist ein guter Startpunkt nach einem Neustart oder bei allgemeinen Systemproblemen.

Wenn dort ein Dienst als `failed` angezeigt wird, prüft man danach:

```bash
systemctl status dienstname
journalctl -u dienstname
```

Beispiel:

```bash
systemctl status nginx
journalctl -u nginx -n 100
```

---

## systemctl status richtig lesen

Beispiel:

```bash
systemctl status ssh
```

Wichtige Informationen:

| Bereich          | Bedeutung                       |
| ---------------- | ------------------------------- |
| `Loaded`         | ob die Unit-Datei geladen wurde |
| `Active`         | aktueller Zustand des Dienstes  |
| `Main PID`       | Hauptprozess des Dienstes       |
| `Docs`           | mögliche Dokumentationshinweise |
| letzte Logzeilen | direkte Hinweise auf Fehler     |

Wichtige Zustände:

| Zustand            | Bedeutung                 |
| ------------------ | ------------------------- |
| `active (running)` | Dienst läuft              |
| `inactive (dead)`  | Dienst läuft nicht        |
| `failed`           | Dienst ist fehlgeschlagen |
| `activating`       | Dienst startet gerade     |
| `deactivating`     | Dienst stoppt gerade      |

Ein Dienst kann installiert sein, aber trotzdem nicht laufen.

Deshalb immer Status prüfen.

---

## Klassische Logdateien lesen

Kurze Datei anzeigen:

```bash
cat datei.log
```

Lange Datei seitenweise lesen:

```bash
less datei.log
```

Letzte Zeilen anzeigen:

```bash
tail datei.log
```

Mehr letzte Zeilen anzeigen:

```bash
tail -n 100 datei.log
```

Live verfolgen:

```bash
tail -f datei.log
```

Für Logs ist `less` oft besser als `cat`, weil man suchen und scrollen kann.

In `less` suchen:

```text
/suchwort
```

Nächster Treffer:

```text
n
```

Beenden:

```text
q
```

---

## Logs durchsuchen mit grep

Mit `grep` sucht man nach Text in Logs.

Beispiele:

```bash
grep "error" app.log
grep -i "error" app.log
grep -i "failed" /var/log/syslog
```

Optionen:

| Option | Bedeutung                            |
| ------ | ------------------------------------ |
| `-i`   | Groß- und Kleinschreibung ignorieren |
| `-n`   | Zeilennummer anzeigen                |
| `-r`   | rekursiv in Ordnern suchen           |
| `-v`   | Treffer ausschließen                 |

Beispiel:

```bash
grep -i "permission denied" /var/log/auth.log
```

Das sucht nach fehlgeschlagenen Zugriffen oder Rechteproblemen.

---

## Mehrere Begriffe suchen

Mit `grep -E` kann man mehrere Muster suchen.

```bash
grep -Ei "error|failed|denied" app.log
```

Bedeutung:

- suche nach `error`
- oder `failed`
- oder `denied`
- Groß- und Kleinschreibung egal

Das ist praktisch bei großen Logs.

Beispiel:

```bash
journalctl -u nginx | grep -Ei "error|failed|denied"
```

---

## Kernel-Meldungen mit dmesg

`dmesg` zeigt Kernel-Meldungen.

```bash
dmesg
```

Mit menschenlesbarer Zeit:

```bash
dmesg -T
```

Fehler und Warnungen:

```bash
dmesg -T | grep -Ei "error|fail|warn"
```

Kernel-Meldungen sind wichtig bei:

- Hardwareproblemen
- Treiberproblemen
- USB-Geräten
- Festplattenfehlern
- Netzwerkadapterproblemen
- Bootproblemen
- Kernelmodulen

Beispiel:

Nach dem Einstecken eines USB-Sticks:

```bash
dmesg -T | tail -n 30
```

---

## Logs und Speicherplatz

Ein voller Datenträger ist eine häufige Fehlerursache.

Speicherplatz prüfen:

```bash
df -h
```

Ordnergrößen prüfen:

```bash
du -sh /var/log
du -sh *
```

Wenn `/var` oder `/` voll ist, können Dienste oft keine Daten mehr schreiben.

Mögliche Folgen:

- Datenbank startet nicht
- Logs können nicht geschrieben werden
- Paketinstallation schlägt fehl
- Dienst bricht ab
- Benutzer können keine Dateien speichern
- System wird langsam

Logs können selbst sehr groß werden, wenn ein Fehler ständig wiederholt wird.

---

## Größe des Journals prüfen

Größe des systemd-Journals anzeigen:

```bash
journalctl --disk-usage
```

Alte Journal-Einträge löschen, zum Beispiel älter als 7 Tage:

```bash
sudo journalctl --vacuum-time=7d
```

Oder auf maximale Größe begrenzen:

```bash
sudo journalctl --vacuum-size=500M
```

Wichtig:

Logs nicht blind löschen.

Logs können für Analyse, Sicherheit und Nachvollziehbarkeit wichtig sein.

Bei produktiven Systemen sollte Logrotation und Aufbewahrung geplant sein.

---

## Logrotation

Logrotation bedeutet, dass alte Logdateien automatisch umbenannt, komprimiert oder gelöscht werden.

Unter Linux wird dafür häufig `logrotate` verwendet.

Typische Konfigurationsorte:

```text
/etc/logrotate.conf
/etc/logrotate.d/
```

Anzeigen:

```bash
cat /etc/logrotate.conf
ls /etc/logrotate.d/
```

Logrotation verhindert, dass Logdateien unbegrenzt wachsen und Speicherplatz füllen.

Für Serverbetrieb ist das wichtig.

---

## Authentifizierungslogs

Auf Ubuntu/Debian sind Anmelde- und sudo-Ereignisse oft in:

```text
/var/log/auth.log
```

Anzeigen:

```bash
sudo less /var/log/auth.log
```

Nach SSH suchen:

```bash
sudo grep -i "ssh" /var/log/auth.log
```

Nach fehlgeschlagenen Logins suchen:

```bash
sudo grep -i "failed" /var/log/auth.log
```

Diese Logs sind wichtig bei:

- SSH-Problemen
- falschen Passwörtern
- sudo-Nutzung
- verdächtigen Login-Versuchen
- Benutzerproblemen

---

## Paketlogs

Paketinstallationen und Updates werden protokolliert.

Wichtige Dateien:

```text
/var/log/apt/history.log
/var/log/apt/term.log
/var/log/dpkg.log
```

Anzeigen:

```bash
less /var/log/apt/history.log
less /var/log/dpkg.log
```

Das ist nützlich, wenn nach einem Update ein Problem auftritt.

Typische Frage:

```text
Was wurde zuletzt installiert oder aktualisiert?
```

Prüfen:

```bash
grep "install" /var/log/apt/history.log
grep "upgrade" /var/log/apt/history.log
```

---

## Netzwerkfehler prüfen

Bei Netzwerkproblemen helfen Logs, aber auch direkte Tests.

Wichtige Befehle:

```bash
ip a
ip route
ping 8.8.8.8
ping google.com
resolvectl status
ss -tulpen
sudo ufw status
```

Typische Einordnung:

| Test              | Bedeutung                              |
| ----------------- | -------------------------------------- |
| `ip a`            | hat das System eine IP-Adresse?        |
| `ip route`        | gibt es ein Gateway?                   |
| `ping 8.8.8.8`    | funktioniert externe IP-Kommunikation? |
| `ping google.com` | funktioniert DNS?                      |
| `ss -tulpen`      | lauscht der Dienst auf dem Port?       |
| `ufw status`      | blockiert die Firewall?                |

Nicht jedes Netzwerkproblem steht direkt im Log.

Man muss Logs und Tests kombinieren.

---

## Dienst startet nicht

Wenn ein Dienst nicht startet, geht man systematisch vor.

1. Status prüfen:

```bash
systemctl status dienstname
```

2. Logs prüfen:

```bash
journalctl -u dienstname -n 100
```

3. Konfiguration prüfen:

```bash
sudo less /etc/dienstname/config
```

4. Syntax-Test nutzen, wenn vorhanden:

```bash
sudo nginx -t
```

5. Portkonflikt prüfen:

```bash
sudo ss -tulpen
```

6. Rechte prüfen:

```bash
ls -la /pfad/zur/datei
ls -ld /pfad/zum/ordner
```

7. Speicher prüfen:

```bash
df -h
```

So findet man die Ursache deutlich besser als durch blindes Neustarten.

---

## Häufige Fehlermeldungen

| Meldung                                | Mögliche Bedeutung                             |
| -------------------------------------- | ---------------------------------------------- |
| `Permission denied`                    | fehlende Rechte                                |
| `No such file or directory`            | Datei oder Pfad existiert nicht                |
| `Address already in use`               | Port ist bereits belegt                        |
| `Connection refused`                   | Ziel erreichbar, aber Dienst lauscht nicht     |
| `Connection timed out`                 | Netzwerk, Firewall oder Routingproblem         |
| `Temporary failure in name resolution` | DNS-Problem                                    |
| `Read-only file system`                | Dateisystem ist nur lesbar                     |
| `No space left on device`              | Speicherplatz voll                             |
| `Unit not found`                       | Dienstname falsch oder Paket nicht installiert |
| `Failed to start`                      | Dienststart fehlgeschlagen                     |

Fehlermeldungen sind Hinweise, keine fertigen Lösungen.

Man muss sie mit Kontext lesen.

---

## Änderungen vor dem Fehler

Eine wichtige Frage bei Fehlersuche:

```text
Was wurde zuletzt geändert?
```

Mögliche Änderungen:

- Paket installiert
- Update durchgeführt
- Konfigurationsdatei geändert
- Dienst neu gestartet
- Benutzerrechte geändert
- Firewallregel geändert
- Docker-Container neu gebaut
- Netzwerk geändert
- System neu gestartet
- Speicherplatz vollgelaufen
- Zertifikat erneuert oder abgelaufen

Nützliche Prüfungen:

```bash
history
less /var/log/apt/history.log
journalctl --since "today"
git diff
```

Bei Git-Projekten ist `git diff` sehr hilfreich, um Änderungen an Dateien zu sehen.

---

## History nutzen

Die Shell-History zeigt zuletzt ausgeführte Befehle.

```bash
history
```

Nach apt-Befehlen suchen:

```bash
history | grep apt
```

Nach systemctl suchen:

```bash
history | grep systemctl
```

Wichtig:

History ist hilfreich, aber nicht perfekt.

Befehle können fehlen, gelöscht sein oder von anderen Benutzern ausgeführt worden sein.

Trotzdem kann sie bei Fehlersuche gute Hinweise geben.

---

## Fehler reproduzieren

Ein Fehler sollte möglichst reproduzierbar sein.

Reproduzieren bedeutet:

Man kann den Fehler erneut auslösen und beobachten.

Beispiel:

Ein Webserver antwortet nicht.

Test:

```bash
curl -v http://localhost:8080
```

Währenddessen Logs beobachten:

```bash
journalctl -u nginx -f
```

So sieht man direkt, welche Meldung beim Fehler entsteht.

Das ist besser als nur alte Logs zufällig zu durchsuchen.

---

## Systematisch eingrenzen

Bei Fehlersuche sollte man das Problem schrittweise eingrenzen.

Beispiel: Webanwendung nicht erreichbar.

Prüfung:

1. Läuft der Dienst?

```bash
systemctl status nginx
```

2. Gibt es Fehlerlogs?

```bash
journalctl -u nginx -n 100
```

3. Lauscht der Port?

```bash
ss -tulpen | grep :80
```

4. Antwortet der Dienst lokal?

```bash
curl http://localhost
```

5. Ist Firewall aktiv?

```bash
sudo ufw status
```

6. Funktioniert Netzwerk?

```bash
ip a
ip route
ping gateway-ip
```

So trennt man Dienstproblem, Portproblem, Firewallproblem und Netzwerkproblem.

---

## Keine schnellen Blindlösungen

Bei Fehlern sollte man nicht sofort blind Befehle ausführen.

Schlechte Beispiele:

```bash
sudo chmod -R 777 /
sudo rm -rf /var/log/*
sudo systemctl restart everything
curl example.com/install.sh | sudo bash
```

Solche Befehle können Systeme beschädigen oder unsicher machen.

Besser:

- Fehlermeldung lesen
- Logs prüfen
- Zustand dokumentieren
- gezielt testen
- kleine Änderungen machen
- nach jeder Änderung prüfen
- Backup vor Konfigurationsänderungen erstellen

---

## Dokumentation bei Fehlersuche

Bei echten IT-Problemen sollte man dokumentieren.

Wichtige Punkte:

- Datum und Uhrzeit
- betroffenes System
- Fehlermeldung
- betroffener Dienst
- Symptome
- durchgeführte Prüfungen
- gefundene Ursache
- durchgeführte Maßnahme
- Ergebnis
- offene Punkte

Beispiel:

```text
Problem: SSH-Verbindung nicht möglich
System: ubuntu-server-01
Zeitpunkt: 18.08.2026, 14:30
Symptom: Connection refused
Prüfung: systemctl status ssh -> inactive
Maßnahme: sudo systemctl start ssh
Ergebnis: SSH-Verbindung funktioniert wieder
```

Gute Dokumentation hilft bei späteren ähnlichen Problemen.

---

## Praxisbeispiele

### Beispiel 1: SSH funktioniert nicht

Prüfen:

```bash
systemctl status ssh
journalctl -u ssh -n 100
ss -tulpen | grep :22
sudo ufw status
```

Mögliche Ursachen:

- SSH-Dienst läuft nicht
- Firewall blockiert Port 22
- SSH lauscht auf anderem Port
- Benutzer oder Schlüssel falsch
- Netzwerkproblem

---

### Beispiel 2: Paketinstallation schlägt fehl

Prüfen:

```bash
sudo apt update
sudo apt install -f
sudo dpkg --configure -a
less /var/log/apt/history.log
less /var/log/dpkg.log
```

Mögliche Ursachen:

- Paketquelle nicht erreichbar
- Abhängigkeiten fehlen
- vorherige Installation wurde abgebrochen
- Paketmanager ist gesperrt
- Speicherplatz ist voll

---

### Beispiel 3: Webserver startet nicht

Prüfen:

```bash
systemctl status nginx
journalctl -u nginx -n 100
sudo nginx -t
sudo ss -tulpen | grep :80
df -h
```

Mögliche Ursachen:

- Syntaxfehler in Konfiguration
- Port 80 ist belegt
- Zertifikat oder Datei fehlt
- Rechteproblem
- Speicherplatz voll

---

### Beispiel 4: System ist langsam

Prüfen:

```bash
top
free -h
df -h
ps aux --sort=-%cpu | head
ps aux --sort=-%mem | head
journalctl -b -p err
```

Mögliche Ursachen:

- Prozess verbraucht viel CPU
- RAM ist voll
- Swap wird stark genutzt
- Festplatte ist voll
- Dienst schreibt ständig Fehler
- Hardware- oder I/O-Problem

---

## Typische Fehler bei Logs und Fehlersuche

| Fehler                          | Problem                                 |
| ------------------------------- | --------------------------------------- |
| Logs nicht lesen                | Ursache bleibt unklar                   |
| nur Symptome betrachten         | eigentlicher Fehler wird nicht gefunden |
| sofort alles neu starten        | wichtige Hinweise gehen verloren        |
| Fehlermeldung nicht genau lesen | falsche Maßnahme                        |
| falschen Dienst prüfen          | Zeitverlust                             |
| Zeitbezug ignorieren            | man liest alte irrelevante Logs         |
| `sudo` als Lösung benutzen      | Rechteproblem wird nicht verstanden     |
| Logs löschen ohne Sicherung     | Nachvollziehbarkeit geht verloren       |
| nur lokal testen                | externe Erreichbarkeit bleibt ungeprüft |
| keine Dokumentation schreiben   | Fehler wiederholt sich später           |

---

## Nützliche Befehle

| Befehl                            | Bedeutung                         |
| --------------------------------- | --------------------------------- |
| `journalctl`                      | systemd-Journal anzeigen          |
| `journalctl -f`                   | Logs live verfolgen               |
| `journalctl -b`                   | Logs seit aktuellem Boot anzeigen |
| `journalctl -u dienst`            | Logs eines Dienstes anzeigen      |
| `journalctl -p err`               | Fehler anzeigen                   |
| `journalctl --since "1 hour ago"` | Logs zeitlich filtern             |
| `systemctl status dienst`         | Dienststatus prüfen               |
| `systemctl --failed`              | fehlgeschlagene Dienste anzeigen  |
| `tail -f datei`                   | Datei live verfolgen              |
| `tail -n 100 datei`               | letzte 100 Zeilen anzeigen        |
| `less datei`                      | Datei seitenweise lesen           |
| `grep -i "error" datei`           | Fehler in Datei suchen            |
| `dmesg -T`                        | Kernelmeldungen anzeigen          |
| `df -h`                           | Speicherplatz prüfen              |
| `du -sh ordner`                   | Ordnergröße prüfen                |
| `free -h`                         | RAM prüfen                        |
| `top`                             | Prozesse live prüfen              |
| `ss -tulpen`                      | offene Ports prüfen               |
| `history`                         | letzte Befehle anzeigen           |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Logs und Fehlersuche tägliche Grundlagen.

In der Praxis bedeutet das:

- Fehler systematisch eingrenzen
- Dienststatus prüfen
- Logs lesen und filtern
- Fehlermeldungen verstehen
- Netzwerk, Ports und Firewall prüfen
- Rechteprobleme erkennen
- Paketprobleme analysieren
- Speicherprobleme finden
- Änderungen nachvollziehen
- Maßnahmen dokumentieren
- nicht blind Befehle kopieren
- Ursache statt nur Symptom beheben

Ein guter FISI arbeitet bei Fehlern strukturiert: beobachten, prüfen, eingrenzen, Maßnahme durchführen, Ergebnis kontrollieren und dokumentieren.

---

## Kurze Zusammenfassung

Logs sind eine zentrale Informationsquelle unter Linux.

Wichtige Werkzeuge sind `journalctl`, `systemctl status`, `tail`, `less`, `grep`, `dmesg`, `df`, `free`, `top` und `ss`.

Fehlersuche sollte systematisch erfolgen: Problem verstehen, Zeitpunkt klären, passende Logs prüfen, Dienste und Ressourcen kontrollieren, Ursache eingrenzen und Änderungen dokumentieren.

Für FISI ist dieses Kapitel wichtig, weil stabile IT-Systeme nicht durch Raten betrieben werden, sondern durch nachvollziehbare Analyse und saubere Fehlerbehebung.
