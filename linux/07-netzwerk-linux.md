# 7. Netzwerk unter Linux

In diesem Kapitel geht es um Netzwerkgrundlagen und Netzwerkdiagnose unter Linux.

Linux-Systeme sind sehr häufig Teil eines Netzwerks. Server, Clients, virtuelle Maschinen, Docker-Container, Datenbanken, Webserver und Cloud-Systeme müssen über Netzwerke erreichbar sein. Viele Fehler im IT-Betrieb entstehen durch falsche IP-Konfiguration, DNS-Probleme, Routing, Firewall-Regeln, nicht laufende Dienste oder falsch gebundene Ports.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr wichtig, weil Netzwerkprobleme systematisch analysiert werden müssen.

---

## Kurz erklärt

Netzwerk unter Linux bedeutet, dass ein System mit anderen Geräten kommunizieren kann.

Wichtige Themen sind:

- Netzwerkschnittstellen
- IP-Adressen
- Subnetzmasken
- Gateway
- Routing
- DNS
- DHCP
- statische IP-Adressen
- Hostname
- offene Ports
- Dienste
- Firewall
- NetworkManager
- Netplan
- Verbindungstests
- Fehlersuche

Wichtige Befehle sind:

```bash
ip a
ip route
ping
traceroute
ss -tulpen
resolvectl status
hostname
nmcli
curl
wget
```

---

## Warum Netzwerk unter Linux wichtig ist

Viele Linux-Systeme laufen als Server.

Ein Server ist nur sinnvoll, wenn er im Netzwerk erreichbar ist.

Beispiele:

- SSH-Server
- Webserver
- Datenbankserver
- DNS-Server
- DHCP-Server
- Dateiserver
- Docker-Host
- Monitoring-System
- Backup-Server
- virtuelle Maschine
- Cloud-Server

Wenn ein Dienst nicht erreichbar ist, muss man prüfen können:

- Hat das System eine IP-Adresse?
- Ist das Gateway korrekt?
- Funktioniert DNS?
- Läuft der Dienst?
- Lauscht der Dienst auf dem richtigen Port?
- Blockiert eine Firewall?
- Gibt es ein Routingproblem?
- Ist der Zielserver erreichbar?
- Ist ein Container-Port korrekt weitergeleitet?

Netzwerkdiagnose ist deshalb eine wichtige Admin-Fähigkeit.

---

## Netzwerkschnittstellen

Eine Netzwerkschnittstelle ist eine Verbindung des Systems zum Netzwerk.

Beispiele:

| Schnittstelle | Bedeutung                                         |
| ------------- | ------------------------------------------------- |
| `lo`          | Loopback-Schnittstelle                            |
| `eth0`        | häufig kabelgebundene Netzwerkkarte               |
| `ens33`       | kabelgebundene Schnittstelle in VMs               |
| `enp0s3`      | kabelgebundene Schnittstelle                      |
| `wlan0`       | WLAN-Schnittstelle                                |
| `wlp0s20f3`   | WLAN-Schnittstelle mit moderner Namensgebung      |
| `docker0`     | Docker-Bridge-Netzwerk                            |
| `br-*`        | Bridge-Netzwerke, oft Docker oder Virtualisierung |

Moderne Linux-Systeme verwenden oft längere Schnittstellennamen wie `enp0s3` oder `wlp0s20f3`.

Diese Namen wirken am Anfang ungewohnt, sind aber eindeutig an Hardware oder Gerätepfade gebunden.

---

## IP-Adressen anzeigen

Mit `ip a` zeigt man IP-Adressen und Schnittstellen an.

```bash
ip a
```

Oder ausführlicher:

```bash
ip address
```

Typische Ausgabe:

```text
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP>
    inet 192.168.178.50/24
```

Wichtige Informationen:

| Teil                | Bedeutung                      |
| ------------------- | ------------------------------ |
| `enp0s3`            | Name der Netzwerkschnittstelle |
| `UP`                | Schnittstelle ist aktiv        |
| `LOWER_UP`          | physische Verbindung besteht   |
| `inet`              | IPv4-Adresse                   |
| `192.168.178.50/24` | IP-Adresse mit Präfix          |
| `inet6`             | IPv6-Adresse                   |

Wenn keine `inet`-Adresse vorhanden ist, hat die Schnittstelle keine IPv4-Adresse.

---

## Loopback-Adresse

Die Loopback-Schnittstelle heißt:

```text
lo
```

Die typische IPv4-Adresse ist:

```text
127.0.0.1
```

Der Name dafür ist oft:

```text
localhost
```

Loopback bedeutet:

Das System spricht mit sich selbst.

Beispiele:

```bash
ping 127.0.0.1
ping localhost
```

Das ist nützlich, um lokale Dienste zu testen.

Beispiel:

```bash
curl http://localhost:8080
```

Damit prüft man, ob ein Dienst lokal auf Port 8080 antwortet.

---

## IPv4-Adresse

Eine IPv4-Adresse sieht zum Beispiel so aus:

```text
192.168.178.50
```

Sie besteht aus vier Zahlenblöcken von 0 bis 255.

Private IPv4-Bereiche sind zum Beispiel:

| Bereich          | Nutzung           |
| ---------------- | ----------------- |
| `10.0.0.0/8`     | private Netzwerke |
| `172.16.0.0/12`  | private Netzwerke |
| `192.168.0.0/16` | private Netzwerke |

Private IP-Adressen werden in Heimnetzen, Firmen-LANs und Testumgebungen genutzt.

Sie sind im Internet nicht direkt öffentlich erreichbar.

---

## Subnetz und Präfix

Bei Linux sieht man IP-Adressen oft mit Präfix.

Beispiel:

```text
192.168.178.50/24
```

Das `/24` beschreibt die Netzmaske.

Typische Bedeutung:

```text
192.168.178.50/24
```

bedeutet ungefähr:

- IP-Adresse: `192.168.178.50`
- Netzwerk: `192.168.178.0`
- nutzbare Hosts: ungefähr `192.168.178.1` bis `192.168.178.254`
- Broadcast: `192.168.178.255`

Ein Präfix bestimmt, welcher Teil der Adresse das Netzwerk beschreibt und welcher Teil für Hosts genutzt wird.

---

## Gateway

Das Gateway ist der Weg aus dem eigenen Netzwerk heraus.

Meistens ist das der Router.

Beispiel:

```text
192.168.178.1
```

Wenn ein Linux-System ein Ziel außerhalb des eigenen Netzes erreichen will, sendet es die Pakete an das Gateway.

Ohne korrektes Gateway kann das System vielleicht lokale Geräte erreichen, aber nicht das Internet oder andere Netzwerke.

Gateway prüfen:

```bash
ip route
```

Typische Zeile:

```text
default via 192.168.178.1 dev enp0s3
```

Bedeutung:

| Teil                | Bedeutung     |
| ------------------- | ------------- |
| `default`           | Standardroute |
| `via 192.168.178.1` | Gateway       |
| `dev enp0s3`        | Schnittstelle |

---

## Routingtabelle anzeigen

Mit `ip route` zeigt man die Routingtabelle.

```bash
ip route
```

Beispiel:

```text
default via 192.168.178.1 dev enp0s3
192.168.178.0/24 dev enp0s3 proto kernel scope link src 192.168.178.50
```

Bedeutung:

| Zeile                  | Bedeutung                           |
| ---------------------- | ----------------------------------- |
| `default via ...`      | Route für alle unbekannten Ziele    |
| `192.168.178.0/24 ...` | direkt verbundenes lokales Netzwerk |
| `src 192.168.178.50`   | eigene Quelladresse                 |

Wenn keine Default-Route vorhanden ist, funktioniert oft kein Zugriff auf externe Netze.

---

## DNS

DNS bedeutet Domain Name System.

DNS übersetzt Namen in IP-Adressen.

Beispiel:

```text
google.com -> IP-Adresse
```

Ohne DNS müsste man viele IP-Adressen direkt kennen.

DNS-Konfiguration prüfen:

```bash
resolvectl status
```

Oder ältere Datei prüfen:

```bash
cat /etc/resolv.conf
```

Wichtig:

Auf modernen Ubuntu-Systemen wird DNS oft über `systemd-resolved` verwaltet.

---

## DNS-Problem erkennen

Ein typischer Test:

```bash
ping 8.8.8.8
ping google.com
```

Wenn `ping 8.8.8.8` funktioniert, aber `ping google.com` nicht, ist die reine Netzwerkverbindung wahrscheinlich okay.

Dann liegt das Problem oft bei DNS.

Zusätzlich prüfen:

```bash
resolvectl status
```

Oder gezielt auflösen:

```bash
resolvectl query google.com
```

DNS-Probleme sind sehr häufig im IT-Alltag.

---

## DHCP

DHCP bedeutet Dynamic Host Configuration Protocol.

DHCP vergibt Netzwerkinformationen automatisch.

Typische Informationen über DHCP:

- IP-Adresse
- Subnetzmaske
- Gateway
- DNS-Server
- Lease-Zeit

Vorteil:

Clients müssen nicht manuell konfiguriert werden.

Typisch für:

- Heimnetzwerke
- Unternehmensnetzwerke
- WLAN
- virtuelle Maschinen
- Testumgebungen

Wenn DHCP nicht funktioniert, bekommt ein Client eventuell keine passende IP-Adresse.

---

## Statische IP-Adresse

Eine statische IP-Adresse wird fest konfiguriert.

Das ist häufig sinnvoll für:

- Server
- Drucker
- Netzwerkgeräte
- Gateways
- DNS-Server
- Monitoring-Systeme
- wichtige virtuelle Maschinen

Vorteil:

Das Gerät ist immer unter derselben Adresse erreichbar.

Nachteil:

Man muss sorgfältig konfigurieren und IP-Konflikte vermeiden.

Wichtige Angaben bei statischer IP:

- IP-Adresse
- Präfix oder Netzmaske
- Gateway
- DNS-Server

---

## Hostname

Der Hostname ist der Name des Systems.

Anzeigen:

```bash
hostname
```

Oder mit mehr Informationen:

```bash
hostnamectl
```

Hostname ändern:

```bash
sudo hostnamectl set-hostname neuer-name
```

Danach sollte man oft auch prüfen:

```bash
cat /etc/hostname
cat /etc/hosts
```

Der Hostname ist wichtig für:

- SSH
- Logs
- Monitoring
- Serverdokumentation
- Netzwerkidentifikation
- Inventarisierung

Ein sinnvoller Hostname hilft bei der Administration.

---

## `/etc/hosts`

Die Datei `/etc/hosts` kann lokale Namensauflösung enthalten.

Anzeigen:

```bash
cat /etc/hosts
```

Beispiel:

```text
127.0.0.1 localhost
127.0.1.1 ubuntu-server
192.168.178.20 fileserver
```

Damit kann das System den Namen `fileserver` lokal auf eine IP-Adresse auflösen.

Wichtig:

`/etc/hosts` wirkt nur lokal auf diesem System.

Es ersetzt keinen zentralen DNS-Server für ein ganzes Netzwerk.

---

## NetworkManager

Viele Desktop- und Ubuntu-Systeme nutzen NetworkManager.

`nmcli` ist das Terminal-Werkzeug für NetworkManager.

Status anzeigen:

```bash
nmcli
```

Geräte anzeigen:

```bash
nmcli device
```

Verbindungen anzeigen:

```bash
nmcli connection show
```

Netzwerk aktivieren:

```bash
nmcli networking on
```

Netzwerk deaktivieren:

```bash
nmcli networking off
```

`nmcli` ist besonders nützlich, wenn man Netzwerke ohne grafische Oberfläche verwalten möchte.

---

## Verbindung mit nmcli prüfen

Aktive Verbindungen anzeigen:

```bash
nmcli connection show --active
```

Gerätestatus anzeigen:

```bash
nmcli device status
```

Beispielausgabe:

```text
DEVICE  TYPE      STATE      CONNECTION
enp0s3  ethernet  connected  Wired connection 1
wlan0   wifi      disconnected --
```

Damit sieht man schnell, welche Schnittstelle aktiv verbunden ist.

---

## Netplan

Ubuntu Server nutzt häufig Netplan für Netzwerkkonfiguration.

Typische Dateien liegen unter:

```text
/etc/netplan/
```

Anzeigen:

```bash
ls /etc/netplan
```

Beispiel einer DHCP-Konfiguration:

```yaml
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true
```

Änderungen anwenden:

```bash
sudo netplan apply
```

Vorsicht:

Falsche Netplan-Konfiguration kann die Netzwerkverbindung unterbrechen, besonders bei entfernten Servern per SSH.

---

## Netplan mit statischer IP

Ein einfaches Beispiel:

```yaml
network:
  version: 2
  ethernets:
    enp0s3:
      addresses:
        - 192.168.178.50/24
      routes:
        - to: default
          via: 192.168.178.1
      nameservers:
        addresses:
          - 192.168.178.1
          - 8.8.8.8
```

Danach:

```bash
sudo netplan apply
```

Wichtig:

- Einrückung in YAML muss stimmen.
- Schnittstellenname muss korrekt sein.
- Gateway muss erreichbar sein.
- IP-Adresse darf nicht doppelt vergeben sein.

---

## Verbindung testen mit ping

`ping` testet, ob ein Ziel erreichbar ist.

Beispiel:

```bash
ping 192.168.178.1
```

Oder:

```bash
ping google.com
```

Beenden mit:

```text
Ctrl + C
```

Wichtige Tests:

```bash
ping 127.0.0.1
ping eigene-ip
ping gateway
ping 8.8.8.8
ping google.com
```

Diese Reihenfolge hilft bei der Fehlersuche.

---

## Systematische Ping-Tests

Wenn Netzwerk nicht funktioniert, kann man stufenweise testen.

1. Loopback:

```bash
ping 127.0.0.1
```

2. Eigene IP:

```bash
ping 192.168.178.50
```

3. Gateway:

```bash
ping 192.168.178.1
```

4. Externe IP:

```bash
ping 8.8.8.8
```

5. Domainname:

```bash
ping google.com
```

Interpretation:

| Ergebnis               | Mögliche Ursache                                   |
| ---------------------- | -------------------------------------------------- |
| Loopback fehlschlägt   | sehr grundlegendes lokales Problem                 |
| eigene IP fehlschlägt  | Schnittstelle/IP-Konfiguration prüfen              |
| Gateway fehlschlägt    | lokales Netzwerk, WLAN, Kabel, VLAN oder IP prüfen |
| externe IP fehlschlägt | Gateway, Routing oder Internetverbindung prüfen    |
| Domain fehlschlägt     | DNS prüfen                                         |

---

## traceroute

`traceroute` zeigt den Weg zu einem Ziel.

Installation, falls nicht vorhanden:

```bash
sudo apt install traceroute
```

Beispiel:

```bash
traceroute google.com
```

`traceroute` zeigt Zwischenstationen auf dem Weg zum Ziel.

Das ist nützlich bei:

- Routingproblemen
- WAN-Problemen
- langsamen Verbindungen
- Prüfung, wo Pakete verloren gehen

Nicht jede Firewall erlaubt alle Antworten, deshalb können manche Zeilen mit `*` erscheinen.

---

## curl

`curl` testet HTTP- und HTTPS-Verbindungen.

Beispiele:

```bash
curl http://localhost
curl http://localhost:8080
curl https://example.com
```

Nur Header anzeigen:

```bash
curl -I https://example.com
```

Mit Ausgabe der Details:

```bash
curl -v http://localhost:8080
```

`curl` ist sehr wichtig, wenn man Webserver, APIs oder lokale Dienste testet.

---

## wget

`wget` kann Dateien aus dem Netzwerk herunterladen.

Beispiel:

```bash
wget https://example.com/file.txt
```

Auch `wget` kann genutzt werden, um zu prüfen, ob eine URL erreichbar ist.

Für reine Tests ist `curl` oft besser.

Für Downloads ist `wget` sehr praktisch.

---

## Offene Ports anzeigen

Mit `ss` zeigt man offene Ports und Netzwerkverbindungen an.

```bash
ss -tulpen
```

Bedeutung:

| Option | Bedeutung                |
| ------ | ------------------------ |
| `-t`   | TCP                      |
| `-u`   | UDP                      |
| `-l`   | listening                |
| `-p`   | Prozess anzeigen         |
| `-e`   | erweiterte Informationen |
| `-n`   | numerische Ausgabe       |

Beispiel:

```text
tcp LISTEN 0 128 0.0.0.0:22 0.0.0.0:* users:(("sshd",pid=920,fd=3))
```

Das zeigt:

- SSH lauscht auf Port 22
- Prozess ist `sshd`
- PID ist `920`
- Dienst akzeptiert Verbindungen

---

## Ports und Dienste

Typische Ports:

| Port | Dienst                                       |
| ---: | -------------------------------------------- |
|   22 | SSH                                          |
|   53 | DNS                                          |
|   80 | HTTP                                         |
|  443 | HTTPS                                        |
| 3306 | MySQL / MariaDB                              |
| 5432 | PostgreSQL                                   |
| 8080 | häufig Test-Webserver oder Admin-Oberflächen |

Wichtig:

Ein Dienst kann installiert sein, aber trotzdem nicht auf einem Port lauschen.

Deshalb prüft man:

```bash
systemctl status dienstname
ss -tulpen
journalctl -u dienstname
```

---

## Dienst lokal testen

Wenn ein Webdienst auf Port 8080 laufen soll:

```bash
ss -tulpen | grep :8080
curl http://localhost:8080
```

Wenn `curl localhost` funktioniert, aber Zugriff von außen nicht:

Mögliche Ursachen:

- Firewall blockiert
- Dienst lauscht nur auf `127.0.0.1`
- Portweiterleitung fehlt
- falsche IP-Adresse
- Docker-Port nicht gemappt
- Netzwerkroute fehlt

---

## 127.0.0.1, 0.0.0.0 und eigene IP

Diese Adressen sind wichtig.

| Adresse     | Bedeutung                                                 |
| ----------- | --------------------------------------------------------- |
| `127.0.0.1` | nur lokal auf diesem System                               |
| `localhost` | Name für lokale Verbindung                                |
| `0.0.0.0`   | Dienst lauscht auf allen IPv4-Schnittstellen              |
| eigene IP   | Dienst lauscht auf einer bestimmten Netzwerkschnittstelle |

Beispiel:

```text
127.0.0.1:8080
```

Der Dienst ist nur lokal erreichbar.

Beispiel:

```text
0.0.0.0:8080
```

Der Dienst lauscht auf allen IPv4-Adressen des Systems.

Das ist wichtig bei Servern, Docker und Webanwendungen.

---

## Firewall

Eine Firewall filtert Netzwerkverkehr.

Ubuntu nutzt häufig `ufw` als einfache Firewall-Verwaltung.

Status prüfen:

```bash
sudo ufw status
```

Firewall aktivieren:

```bash
sudo ufw enable
```

SSH erlauben:

```bash
sudo ufw allow ssh
```

Port erlauben:

```bash
sudo ufw allow 80/tcp
```

Regeln anzeigen:

```bash
sudo ufw status numbered
```

Firewall-Regel löschen:

```bash
sudo ufw delete NUMMER
```

Vorsicht:

Wenn man per SSH verbunden ist, sollte man SSH erlauben, bevor man die Firewall aktiviert.

---

## SSH und Netzwerk

SSH wird für entfernte Administration genutzt.

Verbindung:

```bash
ssh benutzer@server-ip
```

Beispiel:

```bash
ssh bilgin@192.168.178.50
```

Prüfen auf dem Server:

```bash
systemctl status ssh
ss -tulpen | grep :22
sudo ufw status
```

Typische SSH-Probleme:

| Problem                 | Mögliche Ursache                         |
| ----------------------- | ---------------------------------------- |
| Verbindung abgelehnt    | SSH-Dienst läuft nicht oder Port falsch  |
| Zeitüberschreitung      | Netzwerk, Firewall oder Routing          |
| Permission denied       | Benutzer, Passwort oder SSH-Key          |
| Hostname nicht gefunden | DNS oder `/etc/hosts`                    |
| Connection refused      | Ziel erreichbar, aber Dienst nicht aktiv |

---

## DNS mit dig und nslookup

Für DNS-Analyse sind `dig` und `nslookup` nützlich.

Installation:

```bash
sudo apt install dnsutils
```

Beispiele:

```bash
dig google.com
nslookup google.com
```

Kurz mit `dig`:

```bash
dig google.com +short
```

Diese Befehle zeigen, welche IP-Adresse ein Name auflöst.

Sie sind hilfreich bei DNS-Problemen.

---

## ARP und Nachbarn

Mit `ip neigh` sieht man bekannte Geräte im lokalen Netzwerk.

```bash
ip neigh
```

Beispiel:

```text
192.168.178.1 dev enp0s3 lladdr aa:bb:cc:dd:ee:ff REACHABLE
```

Das zeigt, welche IP-Adressen im lokalen Netz mit welchen MAC-Adressen bekannt sind.

Das ist nützlich bei lokalen Verbindungsproblemen.

---

## Netzwerkverbindungen anzeigen

Aktive Verbindungen anzeigen:

```bash
ss -tunap
```

Listening-Ports anzeigen:

```bash
ss -tulpen
```

Nur TCP-Verbindungen:

```bash
ss -tn
```

Nur Ports im Listening-Zustand:

```bash
ss -ltn
```

`ss` ersetzt auf modernen Systemen häufig das ältere `netstat`.

---

## netstat

`netstat` ist ein älteres Werkzeug.

Es ist oft im Paket `net-tools` enthalten.

Installation:

```bash
sudo apt install net-tools
```

Beispiel:

```bash
netstat -tulpen
```

Viele ältere Tutorials nutzen noch `netstat`.

Auf modernen Linux-Systemen sollte man eher `ss` kennen.

---

## Netzwerkmanager und Dienste prüfen

Netzwerk hängt oft mit Diensten zusammen.

Wichtige Dienste können sein:

```bash
systemctl status NetworkManager
systemctl status systemd-resolved
systemctl status ssh
```

Bei Servern mit Netplan können auch andere Netzwerk-Renderer genutzt werden.

Prüfen:

```bash
networkctl
```

Oder:

```bash
nmcli device status
```

Je nach System ist NetworkManager oder systemd-networkd aktiv.

---

## WLAN unter Linux

WLAN kann über NetworkManager verwaltet werden.

WLAN-Geräte anzeigen:

```bash
nmcli device
```

WLAN-Netze anzeigen:

```bash
nmcli device wifi list
```

Mit WLAN verbinden:

```bash
nmcli device wifi connect "SSID" password "PASSWORT"
```

Wichtig:

WLAN-Probleme können entstehen durch:

- falsches Passwort
- schwaches Signal
- Treiberproblem
- deaktiviertes WLAN
- falsche SSID
- DHCP-Problem
- DNS-Problem

Auf Servern wird meistens kabelgebundenes Netzwerk bevorzugt.

---

## IPv6

Neben IPv4 gibt es IPv6.

IPv6-Adressen sehen zum Beispiel so aus:

```text
2001:db8::1
```

In `ip a` sieht man IPv6-Zeilen mit:

```text
inet6
```

IPv6 ist in vielen Netzwerken aktiv.

Für den Anfang ist IPv4 oft einfacher zu verstehen, aber IPv6 sollte nicht komplett ignoriert werden.

Manchmal funktionieren Verbindungen über IPv4 nicht, aber über IPv6, oder umgekehrt.

---

## Netzwerk und Docker

Docker erstellt eigene Netzwerke.

Typische Schnittstellen:

```text
docker0
br-xxxxxxxx
```

Docker-Netzwerke anzeigen:

```bash
docker network ls
```

Container anzeigen:

```bash
docker ps
```

Ports prüfen:

```bash
docker ps
ss -tulpen
```

Beispiel:

```text
0.0.0.0:8080->8080/tcp
```

Das bedeutet:

Port 8080 des Hosts wird zum Port 8080 im Container weitergeleitet.

Typische Docker-Netzwerkprobleme:

- Port nicht gemappt
- falscher Container-Port
- Dienst lauscht nur intern
- Container im falschen Netzwerk
- DNS im Container funktioniert nicht
- Host-Port bereits belegt

---

## Netzwerk in virtuellen Maschinen

Bei virtuellen Maschinen gibt es verschiedene Netzwerkmodi.

Typische Modi:

| Modus            | Bedeutung                                     |
| ---------------- | --------------------------------------------- |
| NAT              | VM nutzt Host als Ausgang ins Netzwerk        |
| Bridge           | VM erscheint wie eigenes Gerät im Netzwerk    |
| Host-only        | Kommunikation nur mit Host oder internem Netz |
| Internal Network | nur VMs untereinander                         |

Bei NAT kann die VM oft ins Internet, ist aber von außen nicht direkt erreichbar.

Bei Bridge bekommt die VM meist eine eigene IP im LAN und ist besser von anderen Geräten erreichbar.

Für Serverübungen ist Bridge oft realistischer.

---

## Portkonflikte

Ein Port kann normalerweise nur von einem Dienst gleichzeitig genutzt werden.

Beispiel:

Zwei Dienste wollen Port 80 nutzen.

Prüfen:

```bash
sudo ss -tulpen | grep :80
```

Wenn Port 80 belegt ist, kann ein zweiter Webserver nicht starten.

Typische Lösung:

- anderen Dienst stoppen
- anderen Port verwenden
- Konfiguration ändern
- Docker-Portmapping ändern

Beispiel Docker:

```bash
docker run -p 8080:80 nginx
```

Hier nutzt der Host Port 8080, der Container intern Port 80.

---

## Netzwerkfehler systematisch analysieren

Ein gutes Vorgehen bei Netzwerkproblemen:

1. Schnittstelle und IP prüfen:

```bash
ip a
```

2. Route und Gateway prüfen:

```bash
ip route
```

3. Gateway testen:

```bash
ping gateway-ip
```

4. Externe IP testen:

```bash
ping 8.8.8.8
```

5. DNS testen:

```bash
ping google.com
resolvectl status
```

6. Dienststatus prüfen:

```bash
systemctl status dienstname
```

7. Ports prüfen:

```bash
ss -tulpen
```

8. Firewall prüfen:

```bash
sudo ufw status
```

9. Logs prüfen:

```bash
journalctl -u dienstname
```

Dieses Vorgehen hilft, die Ursache einzugrenzen.

---

## Typische Fehler

| Fehler                             | Problem                                     |
| ---------------------------------- | ------------------------------------------- |
| IP-Adresse nicht geprüft           | unklar, ob System überhaupt im Netz ist     |
| Gateway fehlt                      | Internet oder andere Netze nicht erreichbar |
| DNS mit Internet verwechselt       | IP funktioniert, Name aber nicht            |
| Dienststatus nicht geprüft         | Dienst läuft vielleicht gar nicht           |
| Port nicht geprüft                 | Dienst lauscht eventuell nicht              |
| Firewall vergessen                 | Verbindung wird blockiert                   |
| localhost falsch verstanden        | Dienst ist nur lokal erreichbar             |
| Docker-Portmapping vergessen       | Container ist von außen nicht erreichbar    |
| NAT und Bridge verwechselt         | VM ist nicht wie erwartet erreichbar        |
| falsche Schnittstelle konfiguriert | Änderungen wirken nicht                     |
| Netplan-YAML falsch eingerückt     | Netzwerkconfig wird nicht angewendet        |
| SSH-Firewallregel vergessen        | Gefahr, sich auszusperren                   |

---

## Praktische Beispiele

### Beispiel 1: Internet funktioniert nicht

```bash
ip a
ip route
ping 192.168.178.1
ping 8.8.8.8
ping google.com
resolvectl status
```

Damit prüft man IP-Adresse, Gateway, externe Verbindung und DNS.

### Beispiel 2: SSH ist nicht erreichbar

```bash
systemctl status ssh
ss -tulpen | grep :22
sudo ufw status
ip a
journalctl -u ssh -n 50
```

Damit prüft man Dienst, Port, Firewall, IP-Adresse und Logs.

### Beispiel 3: Webserver auf Port 8080 prüfen

```bash
ss -tulpen | grep :8080
curl http://localhost:8080
sudo ufw status
```

Wenn lokal alles funktioniert, aber extern nicht, liegt das Problem oft bei Firewall, Binding, Routing oder Portweiterleitung.

### Beispiel 4: Docker-Port prüfen

```bash
docker ps
ss -tulpen
curl http://localhost:8080
```

Damit prüft man, ob der Container läuft, ob der Host-Port offen ist und ob der Dienst antwortet.

---

## Nützliche Befehle

| Befehl                    | Bedeutung                                  |
| ------------------------- | ------------------------------------------ |
| `ip a`                    | IP-Adressen und Schnittstellen anzeigen    |
| `ip route`                | Routingtabelle anzeigen                    |
| `ip neigh`                | bekannte Nachbarn im lokalen Netz anzeigen |
| `ping ziel`               | Erreichbarkeit testen                      |
| `traceroute ziel`         | Weg zum Ziel anzeigen                      |
| `resolvectl status`       | DNS-Konfiguration anzeigen                 |
| `resolvectl query name`   | DNS-Auflösung testen                       |
| `hostname`                | Hostnamen anzeigen                         |
| `hostnamectl`             | Hostnamen und Systeminformationen anzeigen |
| `nmcli device`            | Netzwerkgeräte anzeigen                    |
| `nmcli connection show`   | Verbindungen anzeigen                      |
| `ss -tulpen`              | offene Ports mit Prozessen anzeigen        |
| `curl URL`                | HTTP/HTTPS testen                          |
| `curl -I URL`             | HTTP-Header anzeigen                       |
| `wget URL`                | Datei herunterladen                        |
| `dig name`                | DNS-Abfrage durchführen                    |
| `nslookup name`           | DNS-Abfrage durchführen                    |
| `sudo ufw status`         | Firewallstatus anzeigen                    |
| `systemctl status dienst` | Dienststatus prüfen                        |
| `journalctl -u dienst`    | Dienstlogs anzeigen                        |
| `docker network ls`       | Docker-Netzwerke anzeigen                  |
| `docker ps`               | Container und Portmapping anzeigen         |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Netzwerkdiagnose unter Linux eine zentrale Fähigkeit.

In der Praxis bedeutet das:

- IP-Adressen prüfen
- Gateway und Routing analysieren
- DNS-Probleme erkennen
- DHCP und statische IPs verstehen
- SSH-Verbindungen prüfen
- Dienste und offene Ports kontrollieren
- Firewall-Regeln einordnen
- Webdienste mit curl testen
- Docker-Portmapping verstehen
- VM-Netzwerkmodi unterscheiden
- Logs bei Netzwerkdiensten lesen
- Fehler systematisch eingrenzen
- Netzwerkkonfiguration dokumentieren

Ein guter FISI testet Netzwerkprobleme Schritt für Schritt und trennt sauber zwischen IP, Routing, DNS, Dienst, Port und Firewall.

---

## Kurze Zusammenfassung

Linux bietet viele Werkzeuge zur Netzwerkdiagnose.

Wichtige Grundlagen sind Netzwerkschnittstellen, IP-Adressen, Subnetze, Gateway, Routing, DNS, DHCP, statische IPs, Hostname, Ports, Dienste und Firewall.

Wichtige Befehle sind `ip a`, `ip route`, `ping`, `traceroute`, `resolvectl`, `hostname`, `nmcli`, `ss`, `curl`, `dig`, `ufw`, `systemctl` und `journalctl`.

Für FISI ist dieses Kapitel wichtig, weil viele Server- und Clientprobleme durch Netzwerkkonfiguration, DNS, Firewall, Dienste oder Ports entstehen.
