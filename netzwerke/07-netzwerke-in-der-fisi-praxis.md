# 7. Netzwerke in der FISI-Praxis

In diesem Kapitel geht es darum, wie Netzwerkgrundlagen in der praktischen Arbeit eines Fachinformatikers für Systemintegration genutzt werden.

Netzwerke sind nicht nur ein theoretisches Thema. In der Praxis geht es darum, Clients anzubinden, Server erreichbar zu machen, IP-Probleme zu lösen, DNS und DHCP zu prüfen, VLANs zu verstehen, WLAN-Probleme einzugrenzen und technische Dokumentation sauber zu führen.

Für FISI ist Netzwerkverständnis eine Kernkompetenz.

---

## Kurz erklärt

Netzwerke in der FISI-Praxis bedeuten:

```text
Clients verbinden
IP-Konfiguration prüfen
DNS-Probleme erkennen
DHCP-Probleme lösen
Gateways und Routing verstehen
Ports und Dienste prüfen
VLANs einordnen
WLAN-Probleme analysieren
Firewalls berücksichtigen
Netzwerkdokumentation pflegen
```

Ein guter FISI kann nicht nur sagen:

```text
Das Netzwerk geht nicht.
```

Sondern besser:

```text
Der Client hat eine IP-Adresse, Gateway ist erreichbar, externe IP funktioniert, aber DNS-Auflösung schlägt fehl.
```

Das ist der Unterschied zwischen Raten und professioneller Fehlersuche.

---

## Typische Aufgaben in der Praxis

FISI-Aufgaben im Netzwerkbereich können sehr unterschiedlich sein.

Beispiele:

| Aufgabe                     | Typische Themen                     |
| --------------------------- | ----------------------------------- |
| Client ins Netzwerk bringen | DHCP, IP, WLAN/LAN, DNS             |
| Drucker einrichten          | IP, DNS, Treiber, Port              |
| Server erreichbar machen    | IP, Gateway, Firewall, Dienste      |
| WLAN-Problem analysieren    | Signal, SSID, VLAN, DHCP            |
| VLAN prüfen                 | Switch-Port, Trunk, IP-Bereich      |
| SSH-Zugriff prüfen          | IP, Port 22, Dienst, Firewall       |
| Webdienst prüfen            | Port 80/443/8080, DNS, Server       |
| VM-Netzwerk einrichten      | NAT, Bridge, Host-only              |
| Docker-Netzwerk prüfen      | Compose-Netz, Ports, Service-Namen  |
| Dokumentation aktualisieren | IP-Plan, VLAN-Plan, Geräteübersicht |

---

## Client ins Netzwerk einbinden

Ein häufiger Praxisfall:

```text
Ein neuer Client soll ins Netzwerk.
```

Dabei müssen mehrere Dinge passen:

```text
Netzwerkkabel oder WLAN-Verbindung
IP-Adresse
Subnetzmaske
Gateway
DNS-Server
VLAN
Firewall-Regeln
Benutzeranmeldung
```

Prüfen unter Linux:

```bash
ip a
ip route
ping gateway-ip
ping 8.8.8.8
ping github.com
```

Wichtig ist, zuerst zu prüfen, ob die Grundverbindung funktioniert, bevor man Anwendungen oder Dienste untersucht.

---

## Beispiel: Client bekommt keine IP-Adresse

Problem:

```text
Ein Laptop ist verbunden, bekommt aber keine gültige IP-Adresse.
```

Mögliche Ursachen:

```text
DHCP-Server nicht erreichbar
falsches VLAN
WLAN zwar verbunden, aber kein Netz
Switch-Port falsch konfiguriert
Kabel defekt
DHCP-Bereich voll
DHCP Relay fehlt
```

Prüfen:

```bash
ip a
nmcli device status
ip route
```

Wenn eine Adresse im Bereich `169.254.x.x` auftaucht, ist das oft ein Hinweis auf ein DHCP-Problem.

---

## DNS-Probleme in der Praxis

DNS-Probleme sind sehr häufig.

Typisches Muster:

```bash
ping 8.8.8.8
```

funktioniert, aber:

```bash
ping github.com
```

funktioniert nicht.

Dann ist wahrscheinlich nicht „das Internet kaputt“, sondern DNS funktioniert nicht korrekt.

Prüfen:

```bash
resolvectl status
dig github.com
cat /etc/resolv.conf
```

In Firmennetzen ist besonders wichtig:

```text
Interne Servernamen brauchen oft interne DNS-Server.
```

Ein öffentlicher DNS-Server kennt interne Namen meistens nicht.

---

## DHCP in der Praxis

DHCP vergibt Netzwerkkonfiguration automatisch.

Typische DHCP-Werte:

```text
IP-Adresse
Subnetzmaske
Gateway
DNS-Server
Lease-Zeit
```

In der Praxis sollte man wissen:

```text
Welche Netze haben DHCP?
Welche Geräte haben statische IPs?
Welche Geräte haben Reservierungen?
Wo beginnt und endet der DHCP-Bereich?
Gibt es DHCP Relay für VLANs?
```

Ein sauberer IP-Plan verhindert viele Fehler.

---

## Gateway und Routing in der Praxis

Das Gateway ist der Weg aus dem eigenen Netz heraus.

Wenn ein Client lokale Geräte erreicht, aber kein Internet oder kein anderes VLAN, liegt das Problem oft bei:

```text
Gateway
Routing
Firewall
NAT
```

Prüfen:

```bash
ip route
ping gateway-ip
traceroute ziel
```

Typisches Muster:

```text
Gateway nicht erreichbar -> lokales Netz/VLAN/Kabel/WLAN prüfen
Gateway erreichbar, externe IP nicht -> Routing/NAT/Firewall prüfen
externe IP erreichbar, Name nicht -> DNS prüfen
```

---

## Ports und Dienste prüfen

Ein Host kann erreichbar sein, aber der Dienst trotzdem nicht.

Beispiel:

```text
Ping zum Server funktioniert.
SSH funktioniert nicht.
```

Dann muss man den Port und den Dienst prüfen.

Auf dem Server:

```bash
ss -tulpen | grep 22
systemctl status ssh
sudo ufw status
```

Von einem anderen Gerät:

```bash
nc -vz server-ip 22
```

Wichtig:

```text
IP-Erreichbarkeit bedeutet nicht automatisch Dienst-Erreichbarkeit.
```

---

## Firewall in der Praxis

Firewalls kontrollieren, welcher Verkehr erlaubt ist.

Typische Situationen:

```text
Server ist per Ping erreichbar, aber SSH nicht.
Webseite lädt nicht, obwohl Server läuft.
Datenbank ist lokal erreichbar, aber nicht aus anderem Netz.
Gastnetz soll nicht auf interne Server.
```

Prüfen unter Ubuntu:

```bash
sudo ufw status
```

Dienste prüfen:

```bash
ss -tulpen
systemctl status dienstname
```

In Firmenumgebungen können zusätzlich Netzwerk-Firewalls, Router-Regeln oder Cloud-Firewalls beteiligt sein.

---

## VLANs in der Praxis

VLANs trennen Netzwerke logisch.

Beispiel:

| VLAN | Zweck       | Subnetz           |
| ---- | ----------- | ----------------- |
| 10   | Mitarbeiter | `192.168.10.0/24` |
| 20   | Gäste       | `192.168.20.0/24` |
| 30   | Server      | `192.168.30.0/24` |
| 40   | Management  | `192.168.40.0/24` |

In der Praxis muss man wissen:

```text
An welchem VLAN hängt der Client?
Ist der Switch-Port Access oder Trunk?
Ist das richtige VLAN erlaubt?
Hat das VLAN ein Gateway?
Gibt es DHCP für dieses VLAN?
Welche Firewall-Regeln gelten?
```

Ein falsches VLAN kann dazu führen, dass ein Client eine falsche IP bekommt oder gar keine Verbindung hat.

---

## Access Port und Trunk in der Praxis

Ein normaler Client hängt meistens an einem Access Port.

Beispiel:

```text
Port 12 -> VLAN 10
```

Ein Access Point oder eine Verbindung zwischen Switches nutzt oft einen Trunk.

Beispiel:

```text
Switch -> Access Point
VLAN 10 Mitarbeiter-WLAN
VLAN 20 Gäste-WLAN
```

Wenn ein Trunk falsch konfiguriert ist, können bestimmte VLANs nicht funktionieren.

Typische Fehler:

```text
VLAN nicht erlaubt
falsches Native VLAN
Access Point hängt an falschem Porttyp
SSID ist falschem VLAN zugeordnet
```

---

## WLAN in der Praxis

WLAN-Probleme sind oft schwieriger als Kabelprobleme, weil Funk viele Einflussfaktoren hat.

Typische Ursachen:

```text
schlechtes Signal
falsches Passwort
überlasteter Kanal
zu viele Clients
Access Point falsch platziert
falsches VLAN zur SSID
DHCP nicht erreichbar
DNS falsch
Roaming-Probleme
```

Prüfen:

```bash
nmcli device status
nmcli device wifi list
ip a
ip route
ping gateway-ip
ping 8.8.8.8
ping github.com
```

Wichtig:

```text
WLAN verbunden bedeutet nicht automatisch Netzwerk funktioniert.
```

---

## Gäste-WLAN in der Praxis

Ein Gäste-WLAN sollte sauber vom internen Netzwerk getrennt sein.

Ziel:

```text
Gäste dürfen ins Internet.
Gäste dürfen nicht auf interne Server.
Gäste dürfen nicht auf Management-Netze.
```

Typische Umsetzung:

```text
eigene SSID
eigenes VLAN
eigener IP-Bereich
eigene Firewall-Regeln
Client-Isolation
```

Beispiel:

| Bereich | Wert                               |
| ------- | ---------------------------------- |
| SSID    | `Gast-WLAN`                        |
| VLAN    | `20`                               |
| Subnetz | `192.168.20.0/24`                  |
| Zugriff | Internet erlaubt, intern blockiert |

Das ist ein gutes Beispiel für Netzwerksicherheit in der Praxis.

---

## Netzwerk und Serveradministration

Viele Serverprobleme sind Netzwerkprobleme.

Beispiele:

```text
SSH nicht erreichbar
Webserver nicht erreichbar
Datenbank nicht erreichbar
Update-Server nicht erreichbar
DNS-Auflösung funktioniert nicht
Monitoring bekommt keine Daten
Backup-Ziel ist nicht erreichbar
```

Prüfen auf dem Server:

```bash
ip a
ip route
ss -tulpen
systemctl status dienstname
sudo ufw status
journalctl -u dienstname
```

Ein Server muss nicht nur laufen. Er muss auch über das Netzwerk korrekt erreichbar sein.

---

## Netzwerk und Linux

Linux ist in der FISI-Praxis sehr wichtig.

Wichtige Netzwerkbefehle:

```bash
ip a
ip route
ip neigh
ping
dig
traceroute
ss -tulpen
curl
nmcli
resolvectl status
journalctl
```

Mit diesen Befehlen kann man viele Probleme eingrenzen.

Ein guter FISI sollte diese Befehle nicht nur auswendig kennen, sondern verstehen, welche Frage jeder Befehl beantwortet.

Beispiel:

```bash
ip route
```

beantwortet:

```text
Welches Gateway und welche Routen nutzt das System?
```

---

## Netzwerk und Docker

Docker bringt eigene Netzwerkthemen mit.

Wichtig:

```text
Container haben eigene Netzwerke.
Docker Compose erstellt oft ein eigenes Projekt-Netzwerk.
Ports müssen nach außen veröffentlicht werden.
Container erreichen andere Services über Service-Namen.
localhost im Container ist der Container selbst.
```

Beispiel:

```text
App-Container -> db
```

Nicht:

```text
App-Container -> localhost
```

Prüfen:

```bash
docker ps
docker port containername
docker network ls
docker network inspect networkname
docker compose ps
docker compose logs
```

---

## Netzwerk und Virtualisierung

Virtuelle Maschinen können unterschiedlich ans Netzwerk angebunden sein.

| Modus     | Bedeutung                               |
| --------- | --------------------------------------- |
| NAT       | VM nutzt Host als Übergang              |
| Bridge    | VM ist wie eigenes Gerät im LAN         |
| Host-only | Host und VM können miteinander sprechen |
| Internal  | nur VMs untereinander                   |

In der Praxis ist die wichtigste Frage:

```text
Soll die VM nur Internet haben oder auch von anderen Geräten erreichbar sein?
```

Für reine Internetnutzung reicht oft NAT.

Wenn die VM wie ein echter Server im LAN erreichbar sein soll, ist Bridge oft passender.

---

## Netzwerk und Home-Lab

Ein Home-Lab ist gut, um Netzwerke praktisch zu lernen.

Mögliche Übungen:

```text
Ubuntu Server installieren
statische IP setzen
SSH aktivieren
Samba-Freigabe testen
Docker Compose starten
VM mit NAT testen
VM mit Bridge testen
DNS-Probleme simulieren
Firewall-Regeln testen
kleine VLAN-Struktur planen
```

Wichtig ist, die Ergebnisse zu dokumentieren.

Beispiel:

```text
Welche IP hat der Server?
Welches Gateway nutzt er?
Welche Ports sind offen?
Welche Dienste laufen?
Wie wurde getestet?
Welche Fehler gab es?
```

---

## Netzwerkdokumentation

Gute Netzwerkdokumentation ist extrem wichtig.

Sie kann enthalten:

| Dokumentation           | Inhalt                                  |
| ----------------------- | --------------------------------------- |
| IP-Plan                 | Netze, Gateways, DHCP-Bereiche          |
| VLAN-Plan               | VLAN-ID, Name, Subnetz, Zweck           |
| Geräteübersicht         | Router, Switches, Server, Access Points |
| Portbelegung            | Switch-Port, Raum, Gerät, VLAN          |
| WLAN-Übersicht          | SSIDs, VLANs, Sicherheitsart            |
| Firewall-Regeln         | erlaubte und blockierte Verbindungen    |
| Serverdienste           | Host, IP, Ports, Dienste                |
| Troubleshooting-Notizen | Fehler, Ursache, Lösung                 |

Ohne Dokumentation wird Fehlersuche langsamer und riskanter.

---

## Beispiel IP-Plan

Ein einfacher IP-Plan:

| Bereich    | Netz              | Gateway        | DHCP                 |
| ---------- | ----------------- | -------------- | -------------------- |
| Clients    | `192.168.10.0/24` | `192.168.10.1` | `192.168.10.100-200` |
| Gäste      | `192.168.20.0/24` | `192.168.20.1` | `192.168.20.100-220` |
| Server     | `192.168.30.0/24` | `192.168.30.1` | kein normaler DHCP   |
| Management | `192.168.40.0/24` | `192.168.40.1` | reserviert           |

So sieht man schnell, welches Netz welchen Zweck hat.

---

## Beispiel VLAN-Dokumentation

| VLAN | Name       | Subnetz           | Zweck                   |
| ---- | ---------- | ----------------- | ----------------------- |
| 10   | Clients    | `192.168.10.0/24` | Mitarbeitergeräte       |
| 20   | Guests     | `192.168.20.0/24` | Gäste-WLAN              |
| 30   | Servers    | `192.168.30.0/24` | Server                  |
| 40   | Management | `192.168.40.0/24` | Switches, APs, Firewall |
| 50   | VoIP       | `192.168.50.0/24` | Telefone                |

Diese Tabelle hilft bei Planung und Troubleshooting.

---

## Beispiel Port-Dokumentation

| Gerät    | Port    | VLAN    | Nutzung                    |
| -------- | ------- | ------- | -------------------------- |
| Switch 1 | Port 1  | Trunk   | Verbindung zur Firewall    |
| Switch 1 | Port 2  | Trunk   | Verbindung zu Access Point |
| Switch 1 | Port 5  | VLAN 10 | Arbeitsplatz Büro 1        |
| Switch 1 | Port 6  | VLAN 10 | Arbeitsplatz Büro 2        |
| Switch 1 | Port 10 | VLAN 30 | Server                     |
| Switch 1 | Port 15 | VLAN 20 | Gäste-Bereich              |

Solche Dokumentation spart viel Zeit bei Fehlern.

---

## Beispiel: Server nicht erreichbar

Problem:

```text
Server 192.168.30.10 ist aus dem Client-Netz nicht erreichbar.
```

Prüfung:

```text
Client-IP korrekt?
Client-Gateway korrekt?
Server-IP korrekt?
Server-Gateway korrekt?
Routing zwischen VLANs vorhanden?
Firewall-Regel erlaubt Zugriff?
Dienst läuft auf dem Server?
Port ist offen?
```

Befehle:

```bash
ip a
ip route
ping 192.168.30.10
traceroute 192.168.30.10
nc -vz 192.168.30.10 22
```

Auf dem Server:

```bash
ss -tulpen
sudo ufw status
systemctl status ssh
```

---

## Beispiel: Drucker nicht erreichbar

Problem:

```text
Netzwerkdrucker funktioniert nicht.
```

Mögliche Ursachen:

```text
Drucker hat neue IP
Drucker ist im falschen VLAN
DNS-Name zeigt auf alte IP
Firewall blockiert
Drucker offline
falscher Druckerport am Client
DHCP-Reservierung fehlt
```

Prüfen:

```bash
ping drucker-ip
ping drucker-name
```

Weitere Prüfung:

```text
IP am Druckerdisplay prüfen
DHCP-Reservierung prüfen
Drucker-Weboberfläche öffnen
VLAN und Port prüfen
```

---

## Beispiel: VPN verbunden, interne Systeme nicht erreichbar

Problem:

```text
VPN ist verbunden, aber interne Server gehen nicht.
```

Mögliche Ursachen:

```text
VPN-Routen fehlen
DNS über VPN fehlt
Firewall blockiert
falscher Benutzer/VPN-Profil
Split-Tunneling falsch
interne Namen werden extern aufgelöst
```

Prüfen:

```bash
ip route
ping interne-ip
ping interner-name
dig interner-name
```

Wichtig:

```text
VPN verbunden bedeutet nicht automatisch, dass DNS und Routen korrekt sind.
```

---

## Professionelle Fehlersuche

Professionelle Fehlersuche bedeutet:

```text
klar beschreiben
sauber prüfen
nicht blind ändern
Ergebnisse dokumentieren
bei Unsicherheit eskalieren
```

Gute Formulierung:

```text
Client hat IP 192.168.10.55/24, Gateway 192.168.10.1 ist erreichbar, externe IP 8.8.8.8 ist erreichbar, aber DNS-Auflösung über den eingetragenen DNS-Server schlägt fehl.
```

Schlechte Formulierung:

```text
Netzwerk kaputt.
```

---

## Wichtige Prüfkommandos

| Aufgabe               | Befehl                    |
| --------------------- | ------------------------- |
| IP prüfen             | `ip a`                    |
| Route/Gateway prüfen  | `ip route`                |
| Gateway testen        | `ping gateway-ip`         |
| externe IP testen     | `ping 8.8.8.8`            |
| DNS testen            | `dig github.com`          |
| DNS-Server prüfen     | `resolvectl status`       |
| Ports prüfen          | `ss -tulpen`              |
| Port von außen testen | `nc -vz host port`        |
| Webdienst testen      | `curl -I http://host`     |
| Weg prüfen            | `traceroute ziel`         |
| Nachbarn prüfen       | `ip neigh`                |
| WLAN prüfen           | `nmcli device wifi list`  |
| Dienst prüfen         | `systemctl status dienst` |
| Logs prüfen           | `journalctl -u dienst`    |

---

## Gute Arbeitsweise im Alltag

Eine gute Netzwerk-Arbeitsweise:

1. Problem genau aufnehmen
2. betroffene Geräte identifizieren
3. Netzwerkdokumentation prüfen
4. IP-Konfiguration prüfen
5. Gateway und DNS testen
6. Zielsystem und Port prüfen
7. Firewall und VLANs beachten
8. Logs prüfen
9. Änderung gezielt durchführen
10. Ergebnis testen
11. Lösung dokumentieren

Wichtig:

```text
Jede Änderung sollte einen Grund haben.
```

Nicht einfach mehrere Dinge gleichzeitig ändern.

---

## Typische Fehler in der Praxis

| Fehler                                    | Problem                             |
| ----------------------------------------- | ----------------------------------- |
| DNS und Routing verwechseln               | falsche Fehlersuche                 |
| nur `ping github.com` testen              | DNS und Verbindung werden vermischt |
| Gateway nicht prüfen                      | externe Ziele bleiben unerklärlich  |
| VLAN-Dokumentation ignorieren             | Client landet im falschen Netz      |
| Firewall vergessen                        | Dienst wirkt offline                |
| Dienststatus nicht prüfen                 | Port ist gar nicht offen            |
| `localhost` falsch verstehen              | besonders bei Docker/VMs            |
| DHCP und statische IPs überschneiden sich | IP-Konflikte                        |
| keine Notizen machen                      | Fehler wiederholt sich              |
| direkt alles ändern                       | Ursache bleibt unbekannt            |

---

## FISI-Kompetenz

Für FISI bedeutet Netzwerkkompetenz nicht, jedes Protokoll perfekt auswendig zu kennen.

Wichtiger ist:

```text
Grundlagen verstehen
Befehle sinnvoll einsetzen
Fehler systematisch eingrenzen
Dokumentation lesen
Zusammenhänge erkennen
sauber kommunizieren
```

Ein FISI sollte erklären können:

```text
Warum braucht ein Client ein Gateway?
Warum funktioniert IP, aber DNS nicht?
Warum ist ein Dienst trotz Ping nicht erreichbar?
Warum braucht ein Gäste-WLAN ein eigenes VLAN?
Warum ist Bridge bei einer VM anders als NAT?
Warum erreicht ein Docker-Container localhost nicht wie erwartet?
```

---

## Verbindung zu anderen Bereichen

Netzwerkwissen verbindet viele andere IT-Themen.

| Bereich         | Netzwerkbezug                            |
| --------------- | ---------------------------------------- |
| Linux           | Interfaces, Routing, Dienste, Firewall   |
| Docker          | Container-Netzwerke, Ports, Compose      |
| Virtualisierung | NAT, Bridge, Host-only                   |
| IT-Sicherheit   | Firewall, VLANs, Zugriffskontrolle       |
| Datenbanken     | Datenbankports, Client-Server-Verbindung |
| Git/GitHub      | SSH, HTTPS, DNS                          |
| Home-Lab        | Server, VMs, Dienste, Netzplanung        |
| Support         | Clients, Drucker, WLAN, VPN              |

Deshalb ist Netzwerkverständnis eine Grundlage für viele weitere FISI-Themen.

---

## Kurze Zusammenfassung

Netzwerke sind ein zentrales Thema in der FISI-Praxis.

Wichtig sind IP-Adressen, Subnetze, Gateway, DNS, DHCP, Routing, NAT, VLANs, Switches, WLAN, Ports, Dienste, Firewalls und Logs.

Ein guter FISI prüft Netzwerkprobleme systematisch und kann erklären, wo ein Problem liegt: Verbindung, IP, Gateway, DNS, Routing, Port, Dienst, Firewall oder VLAN.

Netzwerkdokumentation wie IP-Pläne, VLAN-Pläne, Portbelegung und Dienstübersichten hilft, Fehler schneller zu finden und Systeme sauber zu betreiben.
