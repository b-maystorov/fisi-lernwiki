# 6. Netzwerk-Troubleshooting

In diesem Kapitel geht es um systematische Fehlersuche in Netzwerken.

Netzwerkprobleme können viele Ursachen haben. Manchmal ist es ein Kabelproblem, manchmal DNS, DHCP, Gateway, Firewall, Routing, VLAN, WLAN oder ein Dienst, der gar nicht läuft. Deshalb ist es wichtig, nicht einfach blind Befehle zu kopieren, sondern Schritt für Schritt zu prüfen.

Für Fachinformatiker für Systemintegration ist Netzwerk-Troubleshooting besonders wichtig, weil viele praktische Aufgaben aus genau dieser Fehleranalyse bestehen.

---

## Kurz erklärt

Netzwerk-Troubleshooting bedeutet:

```text
Problem verstehen
Verbindung prüfen
IP-Konfiguration prüfen
Gateway prüfen
DNS prüfen
Ports prüfen
Dienste prüfen
Firewall prüfen
Logs prüfen
Ergebnis dokumentieren
```

Wichtige Befehle:

| Befehl              | Bedeutung                         |
| ------------------- | --------------------------------- |
| `ip a`              | IP-Adressen anzeigen              |
| `ip route`          | Routing und Gateway anzeigen      |
| `ping`              | Erreichbarkeit testen             |
| `traceroute`        | Weg zum Ziel prüfen               |
| `dig`               | DNS-Auflösung testen              |
| `nslookup`          | DNS-Auflösung testen              |
| `ss -tulpen`        | offene Ports und Dienste anzeigen |
| `nmcli`             | NetworkManager prüfen             |
| `resolvectl status` | DNS-Konfiguration prüfen          |
| `ip neigh`          | ARP/Nachbarn anzeigen             |
| `curl`              | HTTP/HTTPS-Dienste testen         |
| `journalctl`        | Logs prüfen                       |

---

## Warum systematische Fehlersuche wichtig ist

Netzwerkfehler wirken oft ähnlich.

Ein Benutzer sagt zum Beispiel:

```text
Das Internet geht nicht.
Der Server ist nicht erreichbar.
Die Webseite lädt nicht.
Der Drucker funktioniert nicht.
VPN geht nicht.
WLAN ist kaputt.
```

Diese Aussagen sind aber noch keine genaue Fehlerbeschreibung.

Ein Problem kann liegen bei:

```text
Kabel
WLAN
IP-Adresse
Subnetzmaske
Gateway
DNS
Routing
Firewall
Port
Dienst
Server
Client
VLAN
VPN
Docker-Netzwerk
VM-Netzwerk
```

Deshalb braucht man eine klare Reihenfolge.

---

## Grundregel

Eine gute Grundregel lautet:

```text
Nicht raten. Prüfen.
```

Man sollte nicht sofort alles ändern.

Besser:

```text
1. Ist-Zustand prüfen
2. Fehler eingrenzen
3. kleine Änderung machen
4. erneut testen
5. Ergebnis dokumentieren
```

Wenn man ohne Prüfung mehrere Dinge gleichzeitig ändert, weiß man später nicht, was wirklich geholfen hat.

---

## Problem genau beschreiben

Am Anfang sollte man das Problem möglichst genau formulieren.

Schlecht:

```text
Internet geht nicht.
```

Besser:

```text
Der Laptop hat WLAN-Verbindung, bekommt eine IP-Adresse, kann das Gateway anpingen, aber Namen wie github.com werden nicht aufgelöst.
```

Noch besser:

```text
Ping auf 8.8.8.8 funktioniert.
Ping auf github.com funktioniert nicht.
dig github.com liefert keine Antwort.
DNS-Server ist nicht gesetzt.
```

Je genauer das Problem beschrieben ist, desto schneller findet man die Ursache.

---

## Erste Fragen

Bei Netzwerkproblemen helfen diese Fragen:

```text
Betrifft es ein Gerät oder mehrere?
Betrifft es LAN oder WLAN?
Betrifft es nur Internet oder auch lokale Server?
Funktioniert IP, aber DNS nicht?
Ist der Fehler neu oder schon immer da?
Wurde etwas geändert?
Gibt es VLANs?
Gibt es VPN?
Gibt es eine Firewall?
Läuft der Ziel-Dienst überhaupt?
```

Diese Fragen helfen, das Problem einzugrenzen.

---

## OSI-Modell als Denkmodell

Das OSI-Modell hilft bei der Fehlersuche.

Vereinfacht:

| Schicht | Thema     | Beispiele                   |
| ------- | --------- | --------------------------- |
| 1       | Physisch  | Kabel, Stecker, WLAN-Signal |
| 2       | Sicherung | MAC, Switch, VLAN           |
| 3       | Netzwerk  | IP, Subnetz, Routing        |
| 4       | Transport | TCP, UDP, Ports             |
| 5–7     | Anwendung | DNS, HTTP, SSH, Anwendung   |

Praktische Denkweise:

```text
Erst prüfen, ob Verbindung grundsätzlich da ist.
Dann IP prüfen.
Dann Gateway und Routing.
Dann DNS.
Dann Port und Dienst.
Dann Anwendung.
```

---

## Troubleshooting-Reihenfolge

Eine gute Reihenfolge:

```text
1. Physische Verbindung prüfen
2. Netzwerkschnittstelle prüfen
3. IP-Adresse prüfen
4. Subnetzmaske prüfen
5. Gateway prüfen
6. Gateway anpingen
7. externe IP testen
8. DNS testen
9. Zielsystem testen
10. Port prüfen
11. Dienst prüfen
12. Firewall prüfen
13. Logs prüfen
```

Diese Reihenfolge passt nicht immer perfekt, aber sie ist ein guter Start.

---

## Lokale Netzwerkkarte prüfen

Unter Linux:

```bash
ip a
```

oder:

```bash
ip address
```

Wichtige Fragen:

```text
Ist das Interface vorhanden?
Ist es UP?
Hat es eine IPv4-Adresse?
Hat es eine IPv6-Adresse?
Ist die Adresse im richtigen Netz?
```

Beispiel:

```text
wlp0s20f3: UP
inet 192.168.1.25/24
```

Das zeigt:

```text
WLAN-Interface ist aktiv.
IP-Adresse ist vorhanden.
Subnetz ist /24.
```

---

## Interface-Status prüfen

Mit NetworkManager:

```bash
nmcli device status
```

Beispiel:

```text
DEVICE      TYPE      STATE      CONNECTION
wlan0       wifi      connected  Home-WLAN
eth0        ethernet  disconnected --
```

Wichtige Statuswerte:

| Status       | Bedeutung                            |
| ------------ | ------------------------------------ |
| connected    | verbunden                            |
| disconnected | nicht verbunden                      |
| unavailable  | nicht verfügbar                      |
| unmanaged    | nicht durch NetworkManager verwaltet |

Wenn ein Interface nicht verbunden ist, bringt DNS-Fehlersuche noch nichts.

---

## IP-Adresse prüfen

Befehl:

```bash
ip a
```

Wichtige Fragen:

```text
Hat das Gerät eine IP-Adresse?
Liegt die IP im richtigen Netz?
Ist es eine private Adresse?
Ist es eine 169.254-Adresse?
```

Beispiel gültig:

```text
192.168.1.25/24
```

Problematisch:

```text
169.254.12.34
```

Eine `169.254.x.x`-Adresse weist oft auf ein DHCP-Problem hin.

---

## Routing und Gateway prüfen

Befehl:

```bash
ip route
```

Beispiel:

```text
default via 192.168.1.1 dev wlan0
192.168.1.0/24 dev wlan0
```

Wichtige Fragen:

```text
Gibt es eine Default Route?
Ist das Gateway im richtigen Subnetz?
Geht die Route über das richtige Interface?
```

Ohne Default Route funktioniert oft kein Zugriff auf externe Netze.

---

## Gateway testen

Gateway anpingen:

```bash
ping 192.168.1.1
```

Wenn das Gateway erreichbar ist, funktioniert die lokale Verbindung grundsätzlich.

Wenn das Gateway nicht erreichbar ist, mögliche Ursachen:

```text
falsche IP-Adresse
falsche Subnetzmaske
falsches Gateway
Kabelproblem
WLAN-Problem
Switch-Port falsch
VLAN falsch
Firewall blockiert ICMP
Router offline
```

---

## Externe IP testen

Wenn das Gateway erreichbar ist, kann man eine externe IP testen.

Beispiel:

```bash
ping 8.8.8.8
```

Wenn das funktioniert, ist grundsätzlich Routing ins Internet möglich.

Wenn Gateway funktioniert, aber externe IP nicht, mögliche Ursachen:

```text
Router hat kein Internet
NAT funktioniert nicht
Firewall blockiert
Providerproblem
falsche Route
VPN stört Routing
```

---

## DNS testen

Wenn externe IP funktioniert, aber Namen nicht, ist oft DNS das Problem.

Tests:

```bash
ping github.com
dig github.com
dig +short github.com
```

DNS-Konfiguration prüfen:

```bash
resolvectl status
cat /etc/resolv.conf
```

Typisches Muster:

```text
ping 8.8.8.8 funktioniert
ping github.com funktioniert nicht
```

Wahrscheinliche Ursache:

```text
DNS-Problem
```

---

## DNS-Server direkt testen

Man kann einen bestimmten DNS-Server direkt fragen.

Beispiel:

```bash
dig @8.8.8.8 github.com
```

oder interner DNS:

```bash
dig @192.168.1.1 github.com
```

Wenn ein DNS-Server antwortet und ein anderer nicht, kann man das Problem besser eingrenzen.

In Firmenumgebungen ist wichtig:

```text
Interne Namen brauchen oft internen DNS.
```

Ein öffentlicher DNS kennt interne Servernamen meistens nicht.

---

## Zielsystem prüfen

Wenn ein bestimmter Server nicht erreichbar ist, sollte man prüfen:

```text
Ist die IP korrekt?
Ist der Server eingeschaltet?
Ist der Server im richtigen Netz?
Ist das Gateway des Servers korrekt?
Läuft der Dienst?
Blockiert eine Firewall?
Ist der Port offen?
```

Vom Client:

```bash
ping server-ip
traceroute server-ip
```

Auf dem Server:

```bash
ip a
ip route
ss -tulpen
systemctl status dienstname
sudo ufw status
```

---

## Ports prüfen

Eine IP-Adresse reicht nicht. Der richtige Dienst muss auf einem Port erreichbar sein.

Beispiel SSH:

```text
Server-IP: 192.168.1.50
Port: 22
```

Auf dem Server prüfen:

```bash
ss -tulpen | grep 22
```

Wenn der Dienst lauscht, sieht man einen passenden Eintrag.

Beispiel für Webserver:

```bash
ss -tulpen | grep 80
ss -tulpen | grep 443
```

---

## ss verstehen

`ss -tulpen` zeigt offene Netzwerkverbindungen und lauschende Ports.

Bedeutung der Optionen:

| Option | Bedeutung                |
| ------ | ------------------------ |
| `-t`   | TCP                      |
| `-u`   | UDP                      |
| `-l`   | listening                |
| `-p`   | Prozess anzeigen         |
| `-e`   | erweiterte Informationen |
| `-n`   | numerische Anzeige       |

Befehl:

```bash
ss -tulpen
```

Damit sieht man, welche Dienste auf welchen Ports lauschen.

---

## Verbindung zu Port testen

Von einem anderen Gerät kann man Ports mit `nc` testen.

Beispiel:

```bash
nc -vz 192.168.1.50 22
```

Wenn `nc` fehlt:

```bash
sudo apt install netcat-openbsd
```

Weitere Beispiele:

```bash
nc -vz 192.168.1.50 80
nc -vz 192.168.1.50 443
nc -vz 192.168.1.50 5432
```

Das hilft zu prüfen, ob ein bestimmter Dienst erreichbar ist.

---

## HTTP/HTTPS testen

Webdienste kann man mit `curl` testen.

Beispiel:

```bash
curl http://localhost:8080
```

oder:

```bash
curl -I https://github.com
```

`-I` zeigt nur die HTTP-Header.

Das ist praktisch, um zu prüfen:

```text
Antwortet der Webserver?
Kommt ein HTTP-Statuscode?
Gibt es Weiterleitungen?
Ist HTTPS erreichbar?
```

---

## traceroute

`traceroute` zeigt den Weg zum Ziel.

Beispiel:

```bash
traceroute github.com
```

Falls nicht installiert:

```bash
sudo apt install traceroute
```

`traceroute` hilft bei Fragen wie:

```text
Wo bricht die Verbindung ab?
Geht der Traffic über das richtige Gateway?
Gibt es Routingprobleme?
```

Wichtig:

Manche Router oder Firewalls beantworten traceroute nicht. Das Ergebnis muss also mit Vorsicht gelesen werden.

---

## ARP und Nachbarn prüfen

Im lokalen Netzwerk kann man Nachbarn anzeigen:

```bash
ip neigh
```

Das zeigt IP-Adressen und MAC-Adressen, die das System kennt.

Beispiel:

```text
192.168.1.1 dev wlan0 lladdr aa:bb:cc:dd:ee:ff REACHABLE
```

Das ist nützlich, wenn man prüfen möchte:

```text
Kennt mein Gerät das Gateway?
Wird eine MAC-Adresse gelernt?
Gibt es lokale Erreichbarkeit?
```

---

## Firewall prüfen

Auch wenn IP und Routing funktionieren, kann eine Firewall den Zugriff blockieren.

Unter Ubuntu häufig:

```bash
sudo ufw status
```

Dienste prüfen:

```bash
ss -tulpen
```

Beispiel:

```text
Ping funktioniert.
SSH funktioniert nicht.
```

Mögliche Ursachen:

```text
SSH-Dienst läuft nicht
Port 22 lauscht nicht
Firewall blockiert Port 22
falscher Benutzer
falsche IP
```

Firewall und Dienststatus müssen beide geprüft werden.

---

## Dienststatus prüfen

Viele Dienste laufen unter Linux als systemd-Service.

Beispiel SSH:

```bash
systemctl status ssh
```

Beispiel nginx:

```bash
systemctl status nginx
```

Beispiel Docker:

```bash
systemctl status docker
```

Wenn ein Dienst nicht läuft, kann der Port auch nicht erreichbar sein.

Logs prüfen:

```bash
journalctl -u ssh
journalctl -u nginx
journalctl -u docker
```

Live-Logs:

```bash
journalctl -u NetworkManager -f
```

---

## NetworkManager prüfen

Auf vielen Desktop- und Laptop-Systemen verwaltet NetworkManager die Verbindung.

Status:

```bash
nmcli device status
```

Verbindungen:

```bash
nmcli connection show
```

WLANs anzeigen:

```bash
nmcli device wifi list
```

Verbindung neu starten:

```bash
nmcli connection down "Verbindungsname"
nmcli connection up "Verbindungsname"
```

Logs:

```bash
journalctl -u NetworkManager
```

Live:

```bash
journalctl -u NetworkManager -f
```

---

## WLAN-Probleme prüfen

Bei WLAN-Problemen zuerst prüfen:

```text
Ist WLAN aktiviert?
Ist die richtige SSID verbunden?
Ist das Passwort korrekt?
Wie stark ist das Signal?
Bekommt der Client eine IP?
Ist das richtige VLAN zugeordnet?
Funktioniert Gateway?
Funktioniert DNS?
```

Befehle:

```bash
nmcli device status
nmcli device wifi list
ip a
ip route
ping gateway-ip
ping 8.8.8.8
ping github.com
```

WLAN-Verbindung allein bedeutet nicht automatisch, dass IP, Gateway und DNS korrekt sind.

---

## DHCP-Probleme prüfen

Hinweise auf DHCP-Probleme:

```text
keine IP-Adresse
169.254.x.x Adresse
falsches Gateway
falscher DNS-Server
falsches Subnetz
```

Prüfen:

```bash
ip a
ip route
nmcli device status
resolvectl status
```

Mögliche Ursachen:

```text
DHCP-Server nicht erreichbar
DHCP-Bereich voll
falsches VLAN
DHCP Relay fehlt
Switch-Port falsch
WLAN falsch zugeordnet
```

---

## VLAN-Probleme prüfen

VLAN-Probleme erkennt man oft an diesen Symptomen:

```text
Client bekommt keine IP
Client bekommt IP aus falschem Netz
Gateway nicht erreichbar
bestimmte Netze nicht erreichbar
Gastnetz erreicht interne Server
Access Point verteilt falsches Netz
```

Prüfen:

```text
Switch-Port Access oder Trunk?
richtiges VLAN gesetzt?
Trunk erlaubt VLAN?
DHCP-Scope richtig?
Gateway im VLAN vorhanden?
Firewall-Regeln korrekt?
```

Auf dem Client sieht man nur die Wirkung. Die eigentliche Ursache liegt oft auf Switch, Access Point, Firewall oder Router.

---

## VM-Netzwerk prüfen

Bei virtuellen Maschinen hängt Erreichbarkeit stark vom Netzwerkmodus ab.

Typische Modi:

| Modus     | Bedeutung                             |
| --------- | ------------------------------------- |
| NAT       | VM kommt über Host ins Netzwerk       |
| Bridge    | VM erscheint wie eigenes Gerät im LAN |
| Host-only | Verbindung zwischen Host und VM       |
| Internal  | nur VMs untereinander                 |

Prüfen in der VM:

```bash
ip a
ip route
ping gateway
ping 8.8.8.8
ping github.com
```

Wichtige Frage:

```text
Soll die VM von außen erreichbar sein?
```

Dann ist Bridge oft passender als NAT.

---

## Docker-Netzwerk prüfen

Docker nutzt eigene Netzwerke.

Wichtige Befehle:

```bash
docker network ls
docker network inspect networkname
docker ps
docker port containername
docker inspect containername
```

Bei Docker Compose:

```bash
docker compose ps
docker compose logs
docker compose config
```

Wichtig:

```text
localhost im Container bedeutet der Container selbst.
```

Container erreichen andere Compose-Services normalerweise über den Servicenamen:

```text
db
web
backend
adminer
```

---

## localhost richtig verstehen

`localhost` bedeutet immer:

```text
dieses System selbst
```

Beispiele:

| Ort              | Bedeutung von localhost |
| ---------------- | ----------------------- |
| Host-System      | der Host                |
| VM               | die VM                  |
| Docker-Container | der Container           |
| Server           | der Server              |

Häufiger Fehler:

```text
App im Container versucht Datenbank über localhost zu erreichen.
```

Problem:

```text
localhost ist dann der App-Container, nicht der Datenbank-Container.
```

Bei Docker Compose nutzt man meistens den Servicenamen, zum Beispiel `db`.

---

## Logs prüfen

Logs sind wichtig bei Netzwerkfehlern.

Beispiele:

```bash
journalctl -u NetworkManager
journalctl -u ssh
journalctl -u nginx
journalctl -u docker
```

Live:

```bash
journalctl -u NetworkManager -f
```

Docker:

```bash
docker logs containername
docker compose logs
```

Logs können zeigen:

```text
Verbindungsabbrüche
Dienstfehler
Portprobleme
DNS-Probleme
Authentifizierungsfehler
Firewall-Hinweise
```

---

## Beispiel: Kein Internet

Problem:

```text
Laptop hat kein Internet.
```

Prüfung:

```bash
ip a
ip route
ping 192.168.1.1
ping 8.8.8.8
ping github.com
dig github.com
```

Mögliche Interpretation:

| Ergebnis                                  | Hinweis                                  |
| ----------------------------------------- | ---------------------------------------- |
| keine IP                                  | DHCP oder Verbindung                     |
| Gateway nicht erreichbar                  | lokales Netzwerk                         |
| 8.8.8.8 nicht erreichbar                  | Routing/NAT/Internet                     |
| github.com nicht erreichbar, 8.8.8.8 geht | DNS                                      |
| alles erreichbar                          | Problem liegt eher bei Anwendung/Browser |

---

## Beispiel: IP geht, Name nicht

Tests:

```bash
ping 8.8.8.8
ping github.com
dig github.com
resolvectl status
```

Wenn `8.8.8.8` funktioniert, aber `github.com` nicht:

```text
DNS prüfen.
```

Mögliche Ursachen:

```text
kein DNS-Server gesetzt
falscher DNS-Server
DNS-Server nicht erreichbar
VPN-DNS fehlt
interner Name über öffentlichen DNS gefragt
```

---

## Beispiel: SSH geht nicht

Problem:

```text
ssh user@192.168.1.50 funktioniert nicht.
```

Vom Client prüfen:

```bash
ping 192.168.1.50
nc -vz 192.168.1.50 22
```

Auf dem Server prüfen:

```bash
ip a
ip route
ss -tulpen | grep 22
systemctl status ssh
sudo ufw status
```

Mögliche Ursachen:

```text
Server nicht erreichbar
SSH-Dienst läuft nicht
Port 22 blockiert
falscher Benutzer
falsche IP
Firewall blockiert
```

---

## Beispiel: Webdienst nicht erreichbar

Problem:

```text
http://localhost:8080 öffnet nicht.
```

Prüfen:

```bash
ss -tulpen | grep 8080
curl http://localhost:8080
systemctl status nginx
docker ps
docker compose ps
docker compose logs
```

Mögliche Ursachen:

```text
Dienst läuft nicht
Port falsch
Container nicht gestartet
Port-Mapping fehlt
Firewall blockiert
Anwendung bindet nur an falsche Adresse
```

---

## Beispiel: Docker-Container erreicht Datenbank nicht

Problem:

```text
App-Container erreicht PostgreSQL nicht.
```

Prüfen:

```bash
docker compose ps
docker compose logs app
docker compose logs db
docker compose config
docker network ls
```

Wichtige Frage:

```text
Nutzt die App localhost oder den Service-Namen?
```

Bei Compose meistens richtig:

```text
DB_HOST=db
```

Falsch innerhalb eines anderen Containers:

```text
DB_HOST=localhost
```

---

## Beispiel: WLAN verbunden, aber keine IP

Prüfen:

```bash
nmcli device status
nmcli device wifi list
ip a
ip route
```

Mögliche Ursachen:

```text
DHCP nicht erreichbar
falsches VLAN
Access Point falsch konfiguriert
Trunk falsch
DHCP Relay fehlt
WLAN zwar verbunden, aber Netzwerk nicht korrekt
```

---

## Typische Fehler

| Fehler                                           | Problem                                 |
| ------------------------------------------------ | --------------------------------------- |
| sofort DNS prüfen, obwohl keine IP vorhanden ist | falsche Reihenfolge                     |
| `ping github.com` als einzigen Test nutzen       | DNS und Erreichbarkeit werden vermischt |
| Gateway nicht prüfen                             | Routingproblem bleibt unklar            |
| Firewall ignorieren                              | Port kann blockiert sein                |
| Dienststatus nicht prüfen                        | Port ist vielleicht gar nicht offen     |
| `localhost` falsch verstehen                     | besonders bei Docker/VMs                |
| VLANs vergessen                                  | Client ist eventuell im falschen Netz   |
| Logs nicht lesen                                 | Ursache bleibt unbekannt                |
| mehrere Dinge gleichzeitig ändern                | Ergebnis nicht nachvollziehbar          |
| keine Dokumentation                              | Fehler kommt später wieder              |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise beim Netzwerk-Troubleshooting:

1. Problem genau beschreiben
2. betroffene Geräte eingrenzen
3. aktuelle Konfiguration prüfen
4. Verbindung lokal testen
5. Gateway testen
6. externe IP testen
7. DNS testen
8. Ports und Dienste testen
9. Firewall und Logs prüfen
10. Änderung dokumentieren

Wichtig:

```text
Jeder Test soll eine Frage beantworten.
```

Beispiel:

```bash
ping 8.8.8.8
```

beantwortet:

```text
Kann ich eine externe IP erreichen?
```

```bash
dig github.com
```

beantwortet:

```text
Funktioniert DNS-Auflösung?
```

---

## Praktische Befehlsübersicht

| Aufgabe               | Befehl                        |
| --------------------- | ----------------------------- |
| IP anzeigen           | `ip a`                        |
| Gateway anzeigen      | `ip route`                    |
| Interface-Status      | `nmcli device status`         |
| WLANs anzeigen        | `nmcli device wifi list`      |
| Gateway testen        | `ping gateway-ip`             |
| externe IP testen     | `ping 8.8.8.8`                |
| DNS grob testen       | `ping github.com`             |
| DNS genau testen      | `dig github.com`              |
| DNS-Server anzeigen   | `resolvectl status`           |
| offene Ports anzeigen | `ss -tulpen`                  |
| Port von außen testen | `nc -vz host port`            |
| HTTP testen           | `curl -I https://example.com` |
| Route verfolgen       | `traceroute ziel`             |
| Nachbarn anzeigen     | `ip neigh`                    |
| Firewall prüfen       | `sudo ufw status`             |
| Dienst prüfen         | `systemctl status dienst`     |
| Logs prüfen           | `journalctl -u dienst`        |

---

## FISI-Bezug

Netzwerk-Troubleshooting gehört zu den wichtigsten praktischen Fähigkeiten für FISI.

In der Praxis braucht man es für:

- Clients ins Netzwerk einbinden
- Internetprobleme analysieren
- DNS-Probleme erkennen
- DHCP-Probleme prüfen
- Gateway- und Routingprobleme verstehen
- WLAN-Probleme eingrenzen
- VLAN-Probleme erkennen
- Serverdienste erreichbar machen
- SSH- und Webdienste prüfen
- Docker- und VM-Netzwerke verstehen
- Firewall-Probleme nachvollziehen
- technische Dokumentation schreiben

Ein guter FISI arbeitet nicht nach Bauchgefühl, sondern prüft systematisch und dokumentiert die Ergebnisse.

---

## Kurze Zusammenfassung

Netzwerk-Troubleshooting bedeutet, Fehler Schritt für Schritt einzugrenzen.

Wichtige Prüfungen sind IP-Adresse, Subnetzmaske, Gateway, Routing, DNS, Ports, Dienste, Firewall und Logs.

Wichtige Befehle sind `ip a`, `ip route`, `ping`, `dig`, `traceroute`, `ss -tulpen`, `nmcli`, `resolvectl status`, `curl`, `nc`, `journalctl` und `systemctl`.

Für FISI ist dieses Thema besonders wichtig, weil viele echte IT-Probleme mit Netzwerkverbindungen, Namensauflösung, Ports, Diensten oder falscher Konfiguration zusammenhängen.
