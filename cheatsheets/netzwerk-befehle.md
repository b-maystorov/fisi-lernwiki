# Netzwerk-Befehle Cheatsheet

Dieses Cheatsheet enthält wichtige Netzwerk-Befehle für Linux, Fehlersuche, IP-Adressen, DNS, Routing, Ports, SSH und grundlegende Netzwerkdiagnose.

Die ausführlichen Erklärungen stehen später im Bereich [Netzwerke](../netzwerke/) und teilweise im Linux-Kapitel [Netzwerk unter Linux](../linux/07-netzwerk-linux.md).

---

## Grundlegende Netzwerkprüfung

| Befehl              | Bedeutung                                |
| ------------------- | ---------------------------------------- |
| `ip a`              | zeigt IP-Adressen und Netzwerkinterfaces |
| `ip route`          | zeigt Routing-Tabelle                    |
| `hostname`          | zeigt Hostname                           |
| `hostname -I`       | zeigt eigene IP-Adressen                 |
| `ping ziel`         | prüft Erreichbarkeit                     |
| `ss -tulpen`        | zeigt offene Ports und Verbindungen      |
| `resolvectl status` | zeigt DNS-Konfiguration                  |
| `curl url`          | ruft eine URL im Terminal ab             |

Beispiel:

```bash
ip a
ip route
ping -c 4 8.8.8.8
ping -c 4 google.com
```

---

## Netzwerkinterfaces

| Befehl                  | Bedeutung                                           |
| ----------------------- | --------------------------------------------------- |
| `ip link`               | zeigt Netzwerkinterfaces                            |
| `ip a`                  | zeigt Interfaces mit IP-Adressen                    |
| `ip -br a`              | zeigt IP-Adressen kompakt                           |
| `ip link show`          | zeigt Interface-Status                              |
| `ethtool interface`     | zeigt technische Interface-Infos, falls installiert |
| `nmcli device status`   | zeigt Geräte mit NetworkManager                     |
| `nmcli connection show` | zeigt gespeicherte Verbindungen                     |

Beispiel:

```bash
ip -br a
ip link show
nmcli device status
```

Typische Interface-Namen:

| Name      | Bedeutung                                        |
| --------- | ------------------------------------------------ |
| `lo`      | Loopback-Interface                               |
| `eth0`    | klassische Ethernet-Bezeichnung                  |
| `ens33`   | Ethernet-Interface in VM                         |
| `enp0s3`  | Ethernet-Interface nach moderner Linux-Benennung |
| `wlan0`   | klassisches WLAN-Interface                       |
| `wlp...`  | WLAN-Interface nach moderner Linux-Benennung     |
| `docker0` | Docker-Bridge-Netzwerk                           |

---

## IP-Adressen

| Befehl                   | Bedeutung                            |
| ------------------------ | ------------------------------------ |
| `ip a`                   | zeigt IP-Adressen                    |
| `ip -4 a`                | zeigt IPv4-Adressen                  |
| `ip -6 a`                | zeigt IPv6-Adressen                  |
| `hostname -I`            | zeigt eigene IP-Adressen             |
| `ip addr show interface` | zeigt IP eines bestimmten Interfaces |

Beispiel:

```bash
ip -4 a
hostname -I
ip addr show enp0s3
```

Wichtige private IPv4-Bereiche:

| Bereich          | Nutzung                            |
| ---------------- | ---------------------------------- |
| `10.0.0.0/8`     | private Netzwerke                  |
| `172.16.0.0/12`  | private Netzwerke                  |
| `192.168.0.0/16` | private Heim- und Firmennetze      |
| `127.0.0.1`      | localhost                          |
| `169.254.0.0/16` | Link-local, oft bei DHCP-Problemen |

---

## Routing

| Befehl              | Bedeutung                            |
| ------------------- | ------------------------------------ |
| `ip route`          | zeigt Routing-Tabelle                |
| `ip r`              | kurze Form von `ip route`            |
| `ip route get ziel` | zeigt Route zu einem Ziel            |
| `traceroute ziel`   | zeigt Netzwerkweg, falls installiert |
| `tracepath ziel`    | einfache Alternative zu traceroute   |

Beispiel:

```bash
ip route
ip route get 8.8.8.8
tracepath google.com
```

Wichtige Begriffe:

| Begriff         | Bedeutung                                       |
| --------------- | ----------------------------------------------- |
| Gateway         | Router, der Pakete in andere Netze weiterleitet |
| Default Route   | Standardweg für unbekannte Ziele                |
| Subnetz         | Teilbereich eines Netzwerks                     |
| Routing-Tabelle | Liste von Wegen zu Netzwerken                   |

Typische Default Route:

```text
default via 192.168.1.1 dev wlan0
```

Das bedeutet:

Pakete zu unbekannten Zielen gehen über `192.168.1.1`.

---

## DNS

| Befehl                 | Bedeutung                              |
| ---------------------- | -------------------------------------- |
| `resolvectl status`    | zeigt DNS-Server und DNS-Konfiguration |
| `dig domain`           | fragt DNS-Eintrag ab                   |
| `nslookup domain`      | einfache DNS-Abfrage                   |
| `host domain`          | DNS-Abfrage                            |
| `cat /etc/resolv.conf` | zeigt Resolver-Konfiguration           |
| `ping domain`          | testet auch Namensauflösung            |

Beispiel:

```bash
resolvectl status
dig google.com
nslookup google.com
```

DNS-Problem erkennen:

```bash
ping -c 4 8.8.8.8
ping -c 4 google.com
```

Wenn IP funktioniert, aber Domain nicht:

```text
Netzwerk geht, aber DNS ist wahrscheinlich das Problem.
```

---

## Ping

| Befehl            | Bedeutung                    |
| ----------------- | ---------------------------- |
| `ping ziel`       | sendet dauerhaft Ping-Pakete |
| `ping -c 4 ziel`  | sendet 4 Ping-Pakete         |
| `ping -i 2 ziel`  | sendet alle 2 Sekunden       |
| `ping localhost`  | testet lokalen Netzwerkstack |
| `ping gateway-ip` | testet Verbindung zum Router |
| `ping 8.8.8.8`    | testet Internet per IP       |
| `ping google.com` | testet Internet und DNS      |

Beispiel für systematische Prüfung:

```bash
ping -c 4 127.0.0.1
ping -c 4 192.168.1.1
ping -c 4 8.8.8.8
ping -c 4 google.com
```

Interpretation:

| Ergebnis                   | Bedeutung                          |
| -------------------------- | ---------------------------------- |
| localhost geht nicht       | lokales Netzwerkproblem            |
| Gateway geht nicht         | lokales Netz oder WLAN/LAN Problem |
| 8.8.8.8 geht nicht         | Internet/Routing Problem           |
| Domain geht nicht, IP geht | DNS Problem                        |

---

## Ports und Verbindungen

| Befehl             | Bedeutung                                      |
| ------------------ | ---------------------------------------------- |
| `ss -tulpen`       | zeigt offene TCP/UDP-Ports                     |
| `ss -tulpn`        | zeigt offene Ports kompakter                   |
| `ss -tunap`        | zeigt viele Netzwerkverbindungen               |
| `ss -tn`           | zeigt TCP-Verbindungen                         |
| `lsof -i`          | zeigt Netzwerkdateien/Ports, falls installiert |
| `nc -vz host port` | testet TCP-Port, falls installiert             |

Beispiel:

```bash
ss -tulpen
ss -tulpen | grep 22
ss -tulpen | grep 80
```

Wichtige Ports:

| Port    | Dienst              |
| ------- | ------------------- |
| `22`    | SSH                 |
| `53`    | DNS                 |
| `67/68` | DHCP                |
| `80`    | HTTP                |
| `443`   | HTTPS               |
| `5432`  | PostgreSQL          |
| `3306`  | MySQL/MariaDB       |
| `8080`  | häufig Web-Testport |

---

## HTTP und Webtests

| Befehl              | Bedeutung                       |
| ------------------- | ------------------------------- |
| `curl url`          | ruft URL ab                     |
| `curl -I url`       | zeigt HTTP-Header               |
| `curl -v url`       | ausführliche Verbindungsausgabe |
| `wget url`          | lädt Datei herunter             |
| `wget -O datei url` | lädt Datei mit bestimmtem Namen |

Beispiel:

```bash
curl http://localhost:8080
curl -I https://example.com
curl -v http://localhost:8080
```

Bei Docker oder Webservern ist `curl` sehr praktisch:

```bash
curl http://localhost:8080
```

Damit prüft man, ob ein Dienst lokal antwortet.

---

## SSH

| Befehl                        | Bedeutung                |
| ----------------------------- | ------------------------ |
| `ssh user@host`               | verbindet per SSH        |
| `ssh -p port user@host`       | SSH über bestimmten Port |
| `ssh -v user@host`            | ausführliche SSH-Ausgabe |
| `scp datei user@host:/pfad`   | kopiert Datei auf Server |
| `scp user@host:/pfad/datei .` | kopiert Datei vom Server |
| `ssh-keygen -t ed25519`       | erstellt SSH-Schlüssel   |
| `ssh -T git@github.com`       | testet GitHub-SSH        |

Beispiel:

```bash
ssh admin@192.168.1.10
ssh -v admin@192.168.1.10
scp test.txt admin@192.168.1.10:/home/admin/
```

Typische SSH-Probleme:

| Problem               | Prüfung                 |
| --------------------- | ----------------------- |
| Verbindung geht nicht | `ping host`             |
| Port geschlossen      | `ss -tulpen` auf Server |
| falscher Benutzer     | SSH-Befehl prüfen       |
| Key-Problem           | `ssh -v user@host`      |
| Firewall blockiert    | `sudo ufw status`       |

---

## NetworkManager mit nmcli

| Befehl                           | Bedeutung                       |
| -------------------------------- | ------------------------------- |
| `nmcli device status`            | zeigt Netzwerkgeräte            |
| `nmcli connection show`          | zeigt gespeicherte Verbindungen |
| `nmcli connection show --active` | zeigt aktive Verbindungen       |
| `nmcli device wifi list`         | zeigt WLAN-Netze                |
| `nmcli device show interface`    | zeigt Details zu Interface      |
| `nmcli networking off`           | Netzwerk deaktivieren           |
| `nmcli networking on`            | Netzwerk aktivieren             |

Beispiel:

```bash
nmcli device status
nmcli connection show --active
nmcli device show wlan0
```

WLAN-Netze anzeigen:

```bash
nmcli device wifi list
```

---

## Netplan

Netplan wird auf vielen Ubuntu-Systemen zur Netzwerkkonfiguration genutzt.

Dateien liegen oft unter:

```text
/etc/netplan/
```

Anzeigen:

```bash
ls -la /etc/netplan/
```

Konfiguration testen/anwenden:

```bash
sudo netplan try
sudo netplan apply
```

Beispiel DHCP-Konfiguration:

```yaml
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true
```

Wichtig:

Bei Servern mit Remote-Zugriff vorsichtig sein. Eine falsche Netzwerkkonfiguration kann SSH-Verbindung trennen.

---

## Firewall mit UFW

| Befehl                     | Bedeutung             |
| -------------------------- | --------------------- |
| `sudo ufw status`          | zeigt Firewall-Status |
| `sudo ufw status verbose`  | zeigt Details         |
| `sudo ufw enable`          | aktiviert UFW         |
| `sudo ufw disable`         | deaktiviert UFW       |
| `sudo ufw allow 22`        | erlaubt SSH           |
| `sudo ufw allow 80`        | erlaubt HTTP          |
| `sudo ufw allow 443`       | erlaubt HTTPS         |
| `sudo ufw deny port`       | blockiert Port        |
| `sudo ufw delete allow 80` | entfernt Regel        |

Beispiel:

```bash
sudo ufw status
sudo ufw allow 22
sudo ufw allow 80
```

Wichtig bei SSH:

```bash
sudo ufw allow 22
sudo ufw enable
```

Erst SSH erlauben, dann Firewall aktivieren.

Sonst kann man sich selbst aussperren.

---

## DHCP

DHCP vergibt IP-Adressen automatisch.

Prüfen:

```bash
ip a
ip route
resolvectl status
```

Lease erneuern, je nach System:

```bash
sudo dhclient -r
sudo dhclient
```

Bei NetworkManager eher:

```bash
sudo systemctl restart NetworkManager
```

oder Verbindung neu starten:

```bash
nmcli networking off
nmcli networking on
```

Typische DHCP-Probleme:

| Zeichen             | Bedeutung                          |
| ------------------- | ---------------------------------- |
| keine IPv4-Adresse  | DHCP möglicherweise fehlgeschlagen |
| `169.254.x.x`       | Link-local, oft kein DHCP          |
| keine Default Route | Gateway fehlt                      |
| DNS fehlt           | Namensauflösung funktioniert nicht |

---

## ARP und Nachbarn

| Befehl               | Bedeutung                               |
| -------------------- | --------------------------------------- |
| `ip neigh`           | zeigt Nachbarn im lokalen Netz          |
| `arp -a`             | zeigt ARP-Tabelle, falls installiert    |
| `ip neigh flush all` | leert Nachbartabelle, vorsichtig nutzen |

Beispiel:

```bash
ip neigh
```

Damit sieht man Geräte, mit denen das System im lokalen Netzwerk kommuniziert hat.

---

## WLAN

| Befehl                   | Bedeutung                                    |
| ------------------------ | -------------------------------------------- |
| `nmcli device wifi list` | zeigt WLAN-Netze                             |
| `nmcli device status`    | zeigt WLAN-Gerät                             |
| `iw dev`                 | zeigt WLAN-Interfaces, falls installiert     |
| `iwconfig`               | ältere WLAN-Informationen, falls installiert |
| `rfkill list`            | zeigt, ob WLAN blockiert ist                 |
| `rfkill unblock wifi`    | entsperrt WLAN                               |

Beispiel:

```bash
nmcli device wifi list
rfkill list
```

Typische WLAN-Probleme:

- WLAN deaktiviert
- falsches Passwort
- schwaches Signal
- DHCP-Probleme
- DNS-Probleme
- Treiberproblem
- Flugmodus / rfkill blockiert

---

## Docker-Netzwerk

| Befehl                         | Bedeutung                    |
| ------------------------------ | ---------------------------- |
| `docker network ls`            | zeigt Docker-Netzwerke       |
| `docker network inspect name`  | zeigt Details                |
| `docker ps`                    | zeigt Port-Mappings          |
| `docker port container`        | zeigt Ports eines Containers |
| `docker exec -it container sh` | Shell im Container öffnen    |

Beispiel:

```bash
docker network ls
docker ps
docker port web
docker network inspect bridge
```

Typischer Docker-Port:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

---

## Virtuelle Maschinen

Bei VMs sind Netzwerkeinstellungen besonders wichtig.

Typische Modi:

| Modus            | Bedeutung                                                     |
| ---------------- | ------------------------------------------------------------- |
| NAT              | VM kommt ins Internet, ist aber schwerer von außen erreichbar |
| Bridge           | VM hängt wie eigenes Gerät im Netzwerk                        |
| Host-only        | Verbindung nur zwischen Host und VM                           |
| Internal Network | nur Kommunikation zwischen VMs                                |

Prüfen in der VM:

```bash
ip a
ip route
ping -c 4 8.8.8.8
ping -c 4 google.com
```

Wenn SSH zur VM nicht geht:

```bash
ip a
systemctl status ssh
ss -tulpen | grep 22
sudo ufw status
```

---

## Systematische Fehlersuche

Bei Netzwerkproblemen nicht wild Befehle ausführen, sondern Schritt für Schritt prüfen.

### 1. Interface und IP prüfen

```bash
ip a
```

Fragen:

```text
Hat das Interface eine IP-Adresse?
Ist das Interface UP?
Ist die IP im richtigen Netz?
```

### 2. Route prüfen

```bash
ip route
```

Fragen:

```text
Gibt es eine Default Route?
Ist das Gateway korrekt?
```

### 3. Gateway testen

```bash
ping -c 4 gateway-ip
```

### 4. Internet per IP testen

```bash
ping -c 4 8.8.8.8
```

### 5. DNS testen

```bash
ping -c 4 google.com
dig google.com
```

### 6. Ports prüfen

```bash
ss -tulpen
```

### 7. Logs prüfen

```bash
journalctl --since "1 hour ago"
```

---

## Typische Fehlerbilder

| Fehlerbild                 | Mögliche Ursache                                    |
| -------------------------- | --------------------------------------------------- |
| keine IP-Adresse           | DHCP-Problem, Interface down                        |
| IP `169.254.x.x`           | keine DHCP-Adresse erhalten                         |
| Gateway nicht erreichbar   | WLAN/LAN, VLAN, falsches Netz                       |
| IP-Ping geht, Domain nicht | DNS-Problem                                         |
| Domain geht, Dienst nicht  | Port, Firewall oder Dienstproblem                   |
| SSH geht nicht             | SSH-Dienst, Firewall, falsche IP, falscher Benutzer |
| Website nicht erreichbar   | Webdienst down, Port nicht offen, DNS oder Firewall |
| Docker-Port geht nicht     | falsches Port-Mapping oder Container down           |
| VM nicht erreichbar        | NAT/Bridge falsch, Firewall, falsche VM-IP          |

---

## Praktische Admin-Abläufe

### Netzwerk komplett prüfen

```bash
ip a
ip route
ping -c 4 8.8.8.8
ping -c 4 google.com
resolvectl status
```

### Webdienst lokal prüfen

```bash
ss -tulpen
curl http://localhost:8080
```

### SSH-Server prüfen

```bash
systemctl status ssh
ss -tulpen | grep 22
sudo ufw status
```

### DNS prüfen

```bash
resolvectl status
dig google.com
nslookup google.com
```

### Docker-Webcontainer prüfen

```bash
docker ps
docker port web
curl http://localhost:8080
docker logs web
```

---

## Gefährliche oder vorsichtige Befehle

| Befehl                                  | Risiko                                           |
| --------------------------------------- | ------------------------------------------------ |
| `sudo ip addr flush dev interface`      | entfernt IP-Adressen vom Interface               |
| `sudo ip route flush table main`        | entfernt Routing-Tabelle                         |
| `sudo netplan apply`                    | kann Netzwerkverbindung ändern                   |
| `sudo ufw enable`                       | kann SSH aussperren, wenn Port nicht erlaubt ist |
| `sudo ufw deny 22`                      | blockiert SSH                                    |
| `nmcli networking off`                  | deaktiviert Netzwerk                             |
| `sudo systemctl restart NetworkManager` | Netzwerkverbindung wird kurz getrennt            |

Vor solchen Befehlen prüfen:

```bash
ip a
ip route
sudo ufw status
```

Bei Remote-Servern besonders vorsichtig sein.

---

## Nützliche Befehle kompakt

| Befehl                      | Bedeutung                    |
| --------------------------- | ---------------------------- |
| `ip a`                      | IP-Adressen anzeigen         |
| `ip -br a`                  | IP-Adressen kompakt          |
| `ip route`                  | Routen anzeigen              |
| `ip route get ziel`         | Route zu Ziel prüfen         |
| `ping -c 4 ziel`            | Erreichbarkeit testen        |
| `ss -tulpen`                | offene Ports anzeigen        |
| `resolvectl status`         | DNS-Status anzeigen          |
| `dig domain`                | DNS-Abfrage                  |
| `nslookup domain`           | DNS-Abfrage                  |
| `curl url`                  | Webdienst testen             |
| `wget url`                  | Datei herunterladen          |
| `ssh user@host`             | SSH-Verbindung               |
| `scp datei user@host:/pfad` | Datei kopieren               |
| `nmcli device status`       | Netzwerkgeräte anzeigen      |
| `nmcli connection show`     | Verbindungen anzeigen        |
| `sudo ufw status`           | Firewall prüfen              |
| `ip neigh`                  | Nachbarn im lokalen Netz     |
| `docker network ls`         | Docker-Netzwerke anzeigen    |
| `docker port container`     | Docker-Port-Mapping anzeigen |

---

## Kurze Zusammenfassung

Dieses Cheatsheet enthält wichtige Netzwerk-Befehle für Linux und Systemadministration.

Die wichtigsten Befehle für den Alltag sind:

```bash
ip a
ip route
ping -c 4
ss -tulpen
resolvectl status
dig
curl
ssh
scp
nmcli device status
sudo ufw status
```

Für FISI ist Netzwerkdiagnose besonders wichtig, weil viele Probleme systematisch eingegrenzt werden müssen: IP-Adresse, Gateway, DNS, Routing, Ports, Firewall und Dienste.
