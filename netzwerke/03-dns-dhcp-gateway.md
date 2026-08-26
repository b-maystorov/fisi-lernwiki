# 3. DNS, DHCP und Gateway

In diesem Kapitel geht es um DNS, DHCP und das Standardgateway.

Diese drei Themen gehören zu den wichtigsten Grundlagen in Netzwerken. Ein Client braucht normalerweise eine IP-Adresse, eine Subnetzmaske, ein Gateway und einen DNS-Server, damit Netzwerkkommunikation sauber funktioniert.

Für Fachinformatiker für Systemintegration ist dieses Thema sehr wichtig, weil viele typische Netzwerkfehler genau hier entstehen: Gerät bekommt keine IP-Adresse, Internet funktioniert nicht, Namen werden nicht aufgelöst oder das Gateway ist falsch gesetzt.

---

## Kurz erklärt

Ein Client braucht meistens diese Netzwerkinformationen:

| Wert         | Bedeutung                        |
| ------------ | -------------------------------- |
| IP-Adresse   | Adresse des Geräts im Netzwerk   |
| Subnetzmaske | trennt Netzanteil und Hostanteil |
| Gateway      | Weg in andere Netzwerke          |
| DNS-Server   | löst Namen in IP-Adressen auf    |

Beispiel:

```text
IP-Adresse:    192.168.1.25
Subnetzmaske: 255.255.255.0
Gateway:       192.168.1.1
DNS-Server:    192.168.1.1
```

Wenn einer dieser Werte falsch ist, kann Netzwerkkommunikation teilweise oder vollständig fehlschlagen.

---

## DNS

DNS bedeutet:

```text
Domain Name System
```

DNS übersetzt Namen in IP-Adressen.

Beispiel:

```text
github.com -> IP-Adresse
```

Menschen können sich Namen wie `github.com` besser merken als IP-Adressen.

Computer brauchen aber IP-Adressen, um Ziele im Netzwerk zu erreichen.

DNS ist deshalb wie ein Telefonbuch für Netzwerke.

---

## Warum DNS wichtig ist

Ohne DNS müsste man viele IP-Adressen direkt kennen.

Beispiele:

```text
github.com
google.com
server01.firma.local
mail.firma.local
printer01.office.local
```

Diese Namen müssen in IP-Adressen aufgelöst werden.

Wenn DNS nicht funktioniert, kann es sein, dass das Netzwerk grundsätzlich funktioniert, aber Namen nicht erreichbar sind.

Typisches Beispiel:

```bash
ping 8.8.8.8
```

funktioniert, aber:

```bash
ping github.com
```

funktioniert nicht.

Dann ist oft DNS das Problem.

---

## DNS-Auflösung einfach erklärt

Wenn ein Client eine Webseite öffnen möchte, passiert vereinfacht:

```text
1. Benutzer gibt github.com ein.
2. Client fragt den DNS-Server nach der IP-Adresse.
3. DNS-Server antwortet mit einer IP-Adresse.
4. Client verbindet sich mit dieser IP-Adresse.
5. Webseite wird geladen.
```

Ohne erfolgreiche DNS-Auflösung weiß der Client nicht, welche IP-Adresse zu einem Namen gehört.

---

## DNS-Server

Ein DNS-Server beantwortet Namensanfragen.

Beispiele für DNS-Server:

```text
Router im Heimnetz
DNS-Server im Firmennetz
Provider-DNS
öffentliche DNS-Server
interne Windows-DNS-Server
```

In Firmenumgebungen ist DNS besonders wichtig, weil viele interne Dienste über Namen erreichbar sind.

Beispiele:

```text
dc01.firma.local
fileserver01.firma.local
intranet.firma.local
printer01.firma.local
```

---

## Interner und externer DNS

Man unterscheidet oft zwischen internem und externem DNS.

| DNS-Art      | Bedeutung              | Beispiel               |
| ------------ | ---------------------- | ---------------------- |
| interner DNS | löst interne Namen auf | `server01.firma.local` |
| externer DNS | löst Internetnamen auf | `github.com`           |

In Firmen ist der interne DNS oft besonders wichtig.

Wenn ein Client den falschen DNS-Server nutzt, kann es passieren, dass Internetseiten funktionieren, aber interne Servernamen nicht.

---

## DNS und Active Directory

In Windows-Umgebungen ist DNS sehr wichtig für Active Directory.

Clients finden Domänencontroller und andere Dienste über DNS.

Wenn DNS falsch konfiguriert ist, können Probleme entstehen wie:

```text
Domänenanmeldung funktioniert nicht
Gruppenrichtlinien werden nicht geladen
Servernamen werden nicht gefunden
Netzlaufwerke verbinden nicht
interne Dienste sind nicht erreichbar
```

Deshalb ist bei Windows-Domänen oft der interne DNS-Server einzutragen, nicht irgendein öffentlicher DNS-Server.

---

## DNS testen

Unter Linux kann man DNS mit verschiedenen Befehlen testen.

Einfach:

```bash
ping github.com
```

Besser für DNS:

```bash
dig github.com
```

oder:

```bash
nslookup github.com
```

Beispiel:

```bash
dig github.com
```

Das zeigt, ob ein Name aufgelöst wird und welche DNS-Informationen zurückkommen.

---

## DNS mit dig prüfen

`dig` ist ein gutes Werkzeug für DNS-Abfragen.

Beispiel:

```bash
dig github.com
```

Nur kurze Antwort:

```bash
dig +short github.com
```

Einen bestimmten DNS-Server fragen:

```bash
dig @8.8.8.8 github.com
```

Beispiel interner DNS:

```bash
dig @192.168.1.1 server01.local
```

So kann man prüfen, ob ein bestimmter DNS-Server einen Namen kennt.

---

## DNS-Konfiguration unter Linux prüfen

DNS-Konfiguration prüfen:

```bash
resolvectl status
```

oder:

```bash
cat /etc/resolv.conf
```

Bei modernen Linux-Systemen mit systemd ist `resolvectl` oft sehr hilfreich.

Beispiel:

```bash
resolvectl status
```

Dort sieht man unter anderem:

```text
DNS-Server
DNS-Domain
Interface-Zuordnung
```

---

## Typische DNS-Fehler

| Fehler                      | Bedeutung                               |
| --------------------------- | --------------------------------------- |
| IP funktioniert, Name nicht | DNS-Problem wahrscheinlich              |
| falscher DNS-Server         | Namen werden nicht korrekt aufgelöst    |
| interner Name geht nicht    | interner DNS fehlt oder falsch          |
| DNS-Cache alt               | alter Eintrag wird genutzt              |
| Tippfehler im Namen         | Name existiert nicht                    |
| Firewall blockiert DNS      | Port 53 nicht erreichbar                |
| VPN-DNS fehlt               | interne Namen über VPN nicht erreichbar |

DNS-Probleme wirken für Benutzer oft wie „Internet kaputt“, obwohl nur die Namensauflösung nicht funktioniert.

---

## DHCP

DHCP bedeutet:

```text
Dynamic Host Configuration Protocol
```

DHCP vergibt Netzwerkkonfiguration automatisch an Clients.

Ein DHCP-Server kann einem Client geben:

```text
IP-Adresse
Subnetzmaske
Gateway
DNS-Server
Lease-Zeit
Domain
weitere Optionen
```

Ohne DHCP müsste man diese Werte manuell eintragen.

---

## Warum DHCP wichtig ist

DHCP erleichtert die Verwaltung vieler Geräte.

Ohne DHCP müsste man bei jedem Client manuell konfigurieren:

```text
IP-Adresse
Subnetzmaske
Gateway
DNS-Server
```

Das wäre fehleranfällig und aufwendig.

Mit DHCP bekommt ein Client automatisch passende Werte.

Typische Geräte mit DHCP:

```text
Laptops
PCs
Smartphones
Tablets
Gäste-Geräte
normale Clients
```

Typische Geräte mit statischer IP:

```text
Server
Router
Firewalls
Switch-Management
Drucker
Access Points
NAS-Systeme
```

---

## DHCP-Ablauf

Der DHCP-Ablauf wird oft mit DORA erklärt.

```text
D = Discover
O = Offer
R = Request
A = Acknowledge
```

Vereinfacht:

```text
1. Client fragt: Gibt es einen DHCP-Server?
2. DHCP-Server bietet eine IP-Adresse an.
3. Client fordert diese Adresse an.
4. DHCP-Server bestätigt die Vergabe.
```

Danach hat der Client eine gültige Netzwerkkonfiguration.

---

## DHCP-Lease

Eine DHCP-Adresse wird nicht für immer vergeben, sondern für eine bestimmte Zeit.

Diese Zeit heißt:

```text
Lease
```

Beispiel:

```text
Lease Time: 24 Stunden
```

Nach Ablauf oder während der Laufzeit kann der Client die Adresse erneuern.

Das hilft, IP-Adressen wieder freizugeben, wenn Geräte nicht mehr im Netzwerk sind.

---

## DHCP-Bereich

Ein DHCP-Server vergibt Adressen aus einem definierten Bereich.

Beispiel:

```text
Netz: 192.168.10.0/24
Gateway: 192.168.10.1
DHCP-Bereich: 192.168.10.100 bis 192.168.10.200
```

So bleiben andere Bereiche frei für statische Adressen.

Beispiel Planung:

| Bereich                           | Nutzung      |
| --------------------------------- | ------------ |
| `192.168.10.1`                    | Gateway      |
| `192.168.10.10 - 192.168.10.49`   | Server       |
| `192.168.10.50 - 192.168.10.79`   | Drucker      |
| `192.168.10.100 - 192.168.10.200` | DHCP-Clients |

Eine saubere Planung verhindert IP-Konflikte.

---

## DHCP-Reservierung

Eine DHCP-Reservierung sorgt dafür, dass ein bestimmtes Gerät immer dieselbe IP-Adresse bekommt.

Dabei wird meistens die MAC-Adresse des Geräts verwendet.

Beispiel:

```text
MAC-Adresse: a4:bb:6d:12:34:56
reservierte IP: 192.168.10.50
```

Das ist praktisch für:

```text
Drucker
Access Points
bestimmte Clients
kleine Server
NAS-Systeme
```

Vorteil:

Das Gerät bekommt die Adresse automatisch, aber trotzdem immer gleich.

---

## DHCP vs statische IP

| Bereich            | DHCP                          | Statische IP                   |
| ------------------ | ----------------------------- | ------------------------------ |
| Einrichtung        | automatisch                   | manuell                        |
| Fehleranfälligkeit | weniger manuelle Fehler       | mehr manuelle Fehler möglich   |
| Nutzung            | Clients, Gäste, mobile Geräte | Server, Drucker, Infrastruktur |
| Verwaltung         | zentral                       | pro Gerät                      |
| Adresse            | kann sich ändern              | bleibt gleich                  |
| Dokumentation      | DHCP-Server wichtig           | IP-Plan wichtig                |

Beides ist wichtig.

In der Praxis nutzt man oft eine Mischung.

---

## DHCP-Problem erkennen

Wenn ein Gerät keine IP-Adresse bekommt, kann es manchmal eine Adresse im Bereich bekommen:

```text
169.254.x.x
```

Das ist ein Hinweis auf ein DHCP-Problem.

Mögliche Ursachen:

```text
DHCP-Server nicht erreichbar
falsches VLAN
Netzwerkkabel nicht verbunden
WLAN nicht verbunden
DHCP-Bereich voll
Firewall blockiert DHCP
Switch-Port falsch konfiguriert
```

Dann sollte man Netzwerkverbindung und DHCP-Server prüfen.

---

## DHCP unter Linux prüfen

IP-Adresse anzeigen:

```bash
ip a
```

Routing anzeigen:

```bash
ip route
```

NetworkManager prüfen:

```bash
nmcli device status
```

Verbindung neu starten:

```bash
nmcli connection down "Verbindungsname"
nmcli connection up "Verbindungsname"
```

DHCP-Leases können je nach System an unterschiedlichen Orten liegen.

Bei NetworkManager ist oft `nmcli` der wichtigste Einstieg.

---

## Gateway

Das Standardgateway ist der Weg aus dem eigenen Netzwerk heraus.

Beispiel:

```text
Client: 192.168.1.25/24
Gateway: 192.168.1.1
```

Wenn der Client ein Ziel außerhalb seines eigenen Subnetzes erreichen möchte, sendet er die Daten an das Gateway.

Ohne korrektes Gateway funktioniert oft nur die Kommunikation im lokalen Netz.

---

## Warum das Gateway wichtig ist

Ein Client kann Geräte im gleichen Subnetz direkt erreichen.

Beispiel:

```text
Client: 192.168.1.25/24
Server: 192.168.1.50/24
```

Beide liegen im gleichen Netz:

```text
192.168.1.0/24
```

Für Ziele außerhalb des Netzes braucht der Client das Gateway.

Beispiel:

```text
github.com
8.8.8.8
anderes VLAN
anderer Standort
Internet
```

---

## Gateway muss erreichbar sein

Das Gateway muss normalerweise im gleichen lokalen Subnetz wie der Client liegen.

Richtig:

```text
Client:  192.168.1.25/24
Gateway: 192.168.1.1
```

Falsch:

```text
Client:  192.168.1.25/24
Gateway: 192.168.2.1
```

Bei `/24` liegt `192.168.2.1` in einem anderen Netz.

Der Client kann dieses Gateway nicht direkt erreichen.

---

## Gateway prüfen

Unter Linux:

```bash
ip route
```

Beispiel:

```text
default via 192.168.1.1 dev wlan0
```

Das bedeutet:

```text
Standardgateway ist 192.168.1.1 über Interface wlan0.
```

Gateway testen:

```bash
ping 192.168.1.1
```

Wenn das Gateway nicht erreichbar ist, liegt das Problem oft im lokalen Netzwerk.

---

## Default Route

Die Default Route ist der Standardweg für unbekannte Ziele.

Beispiel:

```text
default via 192.168.1.1
```

Das bedeutet:

```text
Wenn kein spezieller Weg bekannt ist, sende an 192.168.1.1.
```

Ohne Default Route weiß der Client nicht, wohin er Daten für externe Netze schicken soll.

Prüfen:

```bash
ip route
```

---

## Gateway, DNS und Internet unterscheiden

Diese drei Dinge werden oft verwechselt.

| Test                                                 | Ergebnis                          | Hinweis |
| ---------------------------------------------------- | --------------------------------- | ------- |
| `ping gateway` funktioniert nicht                    | lokales Netz/Gateway-Problem      |
| `ping 8.8.8.8` funktioniert nicht                    | Routing, NAT oder Internetproblem |
| `ping github.com` funktioniert nicht                 | DNS möglich                       |
| `ping 8.8.8.8` funktioniert, `ping github.com` nicht | sehr wahrscheinlich DNS           |

Wichtig ist, Schritt für Schritt zu testen.

---

## Beispiel: Lokales Netz geht, Internet nicht

Client:

```text
IP: 192.168.1.25
Gateway: fehlt
DNS: 192.168.1.1
```

Mögliches Verhalten:

```text
Ping zu 192.168.1.50 funktioniert.
Ping zu 8.8.8.8 funktioniert nicht.
Ping zu github.com funktioniert nicht.
```

Erklärung:

Der Client kann lokale Geräte erreichen, aber keine externen Ziele, weil kein Gateway gesetzt ist.

---

## Beispiel: IP geht, Name nicht

Test:

```bash
ping 8.8.8.8
ping github.com
```

Ergebnis:

```text
8.8.8.8 funktioniert
github.com funktioniert nicht
```

Wahrscheinliche Ursache:

```text
DNS-Problem
```

Prüfen:

```bash
resolvectl status
dig github.com
cat /etc/resolv.conf
```

---

## Beispiel: DHCP gibt falsche Werte

Ein Client bekommt:

```text
IP: 192.168.10.55
Maske: 255.255.255.0
Gateway: 192.168.20.1
DNS: 192.168.10.1
```

Problem:

Das Gateway liegt nicht im gleichen Subnetz wie der Client.

Bei `/24` müsste das Gateway zum Beispiel sein:

```text
192.168.10.1
```

Hier ist wahrscheinlich der DHCP-Scope falsch konfiguriert.

---

## DNS-Port

DNS nutzt normalerweise Port:

```text
53
```

DNS nutzt meist UDP, kann aber auch TCP verwenden.

Beispiel:

| Protokoll | Port | Nutzung                               |
| --------- | ---- | ------------------------------------- |
| UDP       | 53   | normale DNS-Abfragen                  |
| TCP       | 53   | größere Antworten oder Zonentransfers |

Wenn DNS blockiert ist, können Namen nicht aufgelöst werden.

---

## DHCP-Ports

DHCP nutzt UDP.

| Richtung | Port   |
| -------- | ------ |
| Server   | UDP 67 |
| Client   | UDP 68 |

DHCP funktioniert mit Broadcasts, weil der Client am Anfang noch keine gültige IP-Adresse hat.

Deshalb können VLANs, Firewalls oder falsch konfigurierte Relay-Einstellungen DHCP beeinflussen.

---

## DHCP Relay

Wenn DHCP-Server und Client nicht im gleichen Netzwerk liegen, braucht man oft einen DHCP Relay.

Ein DHCP Relay leitet DHCP-Anfragen aus einem Netz an einen DHCP-Server in einem anderen Netz weiter.

Beispiel:

```text
Client in VLAN 20
DHCP-Server in VLAN 10
Router/Layer-3-Switch leitet DHCP weiter
```

Ohne DHCP Relay bekommt der Client in einem anderen VLAN möglicherweise keine IP-Adresse.

---

## DNS-Cache

Systeme speichern DNS-Antworten oft kurzzeitig zwischen.

Das nennt man DNS-Cache.

Vorteil:

```text
schnellere Namensauflösung
weniger DNS-Anfragen
```

Nachteil:

```text
alte Einträge können kurzzeitig weiter genutzt werden
```

Bei Problemen kann ein DNS-Cache verwirren.

Je nach System gibt es unterschiedliche Befehle, um den Cache zu leeren oder den Dienst neu zu starten.

---

## hosts-Datei

Die `hosts`-Datei kann Namen lokal auf IP-Adressen abbilden.

Unter Linux:

```text
/etc/hosts
```

Beispiel:

```text
192.168.1.10 server01.local
```

Dann kann der Name lokal aufgelöst werden, ohne DNS-Server.

Das ist praktisch für Tests, aber in größeren Netzwerken keine saubere zentrale Lösung.

---

## Reihenfolge bei Namensauflösung

Ein System kann Namen über verschiedene Quellen auflösen.

Typische Quellen:

```text
hosts-Datei
DNS
mDNS
andere lokale Mechanismen
```

Wenn ein Name falsch aufgelöst wird, sollte man auch prüfen, ob er vielleicht in der `hosts`-Datei steht.

---

## mDNS kurz erklärt

mDNS wird oft in kleinen lokalen Netzwerken genutzt.

Namen enden häufig auf:

```text
.local
```

Beispiel:

```text
drucker.local
raspberrypi.local
```

mDNS ist praktisch in Heimnetzen, aber in Firmennetzen sollte Namensauflösung sauber geplant werden.

---

## Netzwerkprüfung Schritt für Schritt

Eine sinnvolle Reihenfolge:

```text
1. IP-Adresse prüfen
2. Subnetzmaske prüfen
3. Gateway prüfen
4. Gateway anpingen
5. externe IP anpingen
6. DNS-Namen anpingen
7. DNS mit dig prüfen
8. Zielport prüfen
9. Dienststatus prüfen
10. Firewall prüfen
```

Wichtige Befehle:

```bash
ip a
ip route
ping 192.168.1.1
ping 8.8.8.8
ping github.com
dig github.com
ss -tulpen
```

---

## Wichtige Linux-Befehle

| Befehl                  | Bedeutung                      |
| ----------------------- | ------------------------------ |
| `ip a`                  | IP-Adressen anzeigen           |
| `ip route`              | Gateway und Routen anzeigen    |
| `ping gateway-ip`       | Gateway testen                 |
| `ping 8.8.8.8`          | externe IP testen              |
| `ping github.com`       | DNS plus Erreichbarkeit testen |
| `dig github.com`        | DNS-Abfrage prüfen             |
| `dig +short github.com` | kurze DNS-Antwort              |
| `resolvectl status`     | DNS-Konfiguration anzeigen     |
| `cat /etc/resolv.conf`  | Resolver-Konfiguration ansehen |
| `nmcli device status`   | Netzwerkgeräte prüfen          |
| `ss -tulpen`            | offene Ports prüfen            |

---

## Typische Fehler

| Fehler                                   | Problem                                |
| ---------------------------------------- | -------------------------------------- |
| DNS und Internet verwechseln             | Netzwerk geht, aber Namen gehen nicht  |
| Gateway fehlt                            | externe Netze nicht erreichbar         |
| Gateway im falschen Subnetz              | Client erreicht Gateway nicht          |
| DHCP-Bereich falsch                      | Clients bekommen falsche Werte         |
| DHCP-Server nicht erreichbar             | keine gültige IP-Adresse               |
| falscher DNS-Server                      | interne oder externe Namen gehen nicht |
| öffentlicher DNS in Domänennetz          | interne Namen funktionieren nicht      |
| DHCP und statische IP überschneiden sich | IP-Konflikte                           |
| `localhost` falsch genutzt               | zeigt auf das eigene System            |
| Tests nicht getrennt durchgeführt        | Fehlerursache bleibt unklar            |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei DNS-, DHCP- und Gateway-Problemen:

1. aktuelle IP-Konfiguration prüfen
2. prüfen, ob IP-Adresse gültig ist
3. prüfen, ob Gateway gesetzt ist
4. Gateway anpingen
5. externe IP testen
6. DNS-Namen testen
7. DNS-Server prüfen
8. DHCP-Werte mit Netzwerkdokumentation vergleichen
9. bei DHCP-Problemen VLAN und DHCP-Server prüfen
10. Ergebnisse dokumentieren

Wichtig:

```text
IP, Gateway und DNS getrennt testen.
```

Nur so erkennt man, wo der Fehler wirklich liegt.

---

## Praktische Beispiele

### Beispiel 1: DNS testen

```bash
ping 8.8.8.8
ping github.com
dig github.com
```

Wenn `8.8.8.8` funktioniert, aber `github.com` nicht, ist DNS wahrscheinlich das Problem.

### Beispiel 2: Gateway prüfen

```bash
ip route
ping 192.168.1.1
```

Wenn das Gateway nicht erreichbar ist, zuerst lokales Netzwerk prüfen.

### Beispiel 3: DHCP-Problem erkennen

```bash
ip a
```

Wenn die Adresse im Bereich `169.254.x.x` liegt, wurde wahrscheinlich keine gültige DHCP-Adresse erhalten.

### Beispiel 4: DNS-Server direkt testen

```bash
dig @8.8.8.8 github.com
dig @192.168.1.1 github.com
```

So kann man verschiedene DNS-Server vergleichen.

---

## FISI-Bezug

DNS, DHCP und Gateway gehören zu den wichtigsten Themen in der FISI-Praxis.

Man braucht sie für:

- Clients ins Netzwerk einbinden
- Internetprobleme analysieren
- DNS-Probleme erkennen
- DHCP-Probleme beheben
- Gateway- und Routingprobleme verstehen
- Windows-Domänenumgebungen einordnen
- VPN-Probleme analysieren
- VLANs mit DHCP planen
- Serverdienste erreichbar machen
- Netzwerkdokumentation prüfen

Ein guter FISI prüft nicht nur, ob „Internet geht“, sondern trennt sauber zwischen IP-Erreichbarkeit, Gateway, DNS und Dienst.

---

## Kurze Zusammenfassung

DNS übersetzt Namen in IP-Adressen.

DHCP vergibt Netzwerkkonfigurationen automatisch, zum Beispiel IP-Adresse, Subnetzmaske, Gateway und DNS-Server.

Das Gateway ist der Weg aus dem eigenen Netzwerk heraus.

Viele Netzwerkfehler lassen sich sauber eingrenzen, wenn man IP-Adresse, Gateway und DNS getrennt prüft.

Wichtige Befehle sind `ip a`, `ip route`, `ping`, `dig`, `resolvectl status`, `nmcli` und `ss -tulpen`.

Für FISI sind DNS, DHCP und Gateway zentrale Grundlagen, weil sehr viele Praxisprobleme genau mit diesen Themen zusammenhängen.
