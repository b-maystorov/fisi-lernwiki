# 3. Volumes und Netzwerke

In diesem Kapitel geht es um Volumes und Netzwerke in Docker.

Container sind oft kurzlebig. Sie können gestartet, gestoppt, gelöscht und neu erstellt werden. Deshalb muss man verstehen, wo Daten gespeichert werden und wie Container miteinander kommunizieren. Dafür sind Volumes und Docker-Netzwerke besonders wichtig.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Docker-Projekte mit Datenbanken, Webservern, Admin-Tools und mehreren Diensten arbeiten. Dabei dürfen Daten nicht versehentlich verloren gehen und Netzwerkverbindungen müssen nachvollziehbar funktionieren.

---

## Kurz erklärt

Volumes speichern Daten dauerhaft.

Docker-Netzwerke verbinden Container miteinander.

| Begriff        | Bedeutung                                                 |
| -------------- | --------------------------------------------------------- |
| Volume         | dauerhafter Docker-Speicher                               |
| Bind Mount     | Host-Ordner wird in Container eingebunden                 |
| tmpfs Mount    | temporärer Speicher im RAM                                |
| Docker Network | Netzwerk für Containerkommunikation                       |
| Bridge Network | Standardnetzwerk für Container                            |
| Port Mapping   | Host-Port wird mit Container-Port verbunden               |
| Service Name   | Name, über den Container sich in Compose erreichen können |

Kurz gesagt:

```text
Volume = Daten behalten
Network = Container verbinden
Port Mapping = Dienst vom Host erreichbar machen
```

---

## Warum Volumes wichtig sind

Ein Container hat ein eigenes Dateisystem.

Wenn man Dateien direkt im Container speichert, gehören sie zum Container. Wird der Container gelöscht, können diese Daten verloren gehen.

Das ist besonders gefährlich bei:

- Datenbanken
- Uploads
- Konfigurationsdateien
- Logdateien
- Anwendungsdaten
- Testdaten
- Projektdateien

Beispiel:

```bash
docker rm db
```

Wenn die Datenbankdaten nur im Container lagen, können sie danach weg sein.

Mit einem Volume bleiben die Daten unabhängig vom Container erhalten.

---

## Container-Dateisystem

Jeder Container hat ein eigenes Dateisystem.

Beispiel:

```bash
docker run --name test -it ubuntu bash
```

Im Container:

```bash
echo "Hallo" > /tmp/test.txt
exit
```

Wenn der Container gelöscht wird:

```bash
docker rm test
```

ist die Datei im Container-Dateisystem weg.

Merke:

```text
Container sind austauschbar.
Wichtige Daten gehören in Volumes oder Bind Mounts.
```

---

## Was ist ein Volume?

Ein Volume ist ein Speicherbereich, den Docker verwaltet.

Volumes liegen auf dem Host-System, werden aber von Docker organisiert.

Volume erstellen:

```bash
docker volume create db_data
```

Volumes anzeigen:

```bash
docker volume ls
```

Volume prüfen:

```bash
docker volume inspect db_data
```

Volume löschen:

```bash
docker volume rm db_data
```

Volumes sind besonders gut für Daten, die dauerhaft bleiben sollen.

---

## Named Volumes

Ein Named Volume hat einen festen Namen.

Beispiel:

```bash
docker volume create db_data
```

Container mit Volume starten:

```bash
docker run -d \
  --name db \
  -v db_data:/var/lib/postgresql/data \
  postgres:16
```

Bedeutung:

| Teil                       | Bedeutung         |
| -------------------------- | ----------------- |
| `db_data`                  | Name des Volumes  |
| `/var/lib/postgresql/data` | Pfad im Container |
| `-v`                       | Mount einbinden   |

Das Volume bleibt erhalten, auch wenn der Container gelöscht wird.

---

## Volume und Container trennen

Ein wichtiger Punkt:

```text
Container und Volume sind getrennte Ressourcen.
```

Beispiel:

```bash
docker stop db
docker rm db
```

Der Container ist gelöscht.

Das Volume bleibt aber bestehen:

```bash
docker volume ls
```

Wenn ein neuer Container wieder dasselbe Volume nutzt, kann er die Daten weiterverwenden.

Das ist wichtig bei Datenbanken.

---

## Beispiel: PostgreSQL mit Volume

PostgreSQL-Container mit dauerhaftem Volume:

```bash
docker volume create postgres_data

docker run -d \
  --name postgres-db \
  -e POSTGRES_PASSWORD=example \
  -v postgres_data:/var/lib/postgresql/data \
  postgres:16
```

Prüfen:

```bash
docker ps
docker logs postgres-db
docker volume ls
docker volume inspect postgres_data
```

Container löschen:

```bash
docker stop postgres-db
docker rm postgres-db
```

Volume bleibt erhalten:

```bash
docker volume ls
```

---

## Bind Mounts

Ein Bind Mount bindet einen Ordner oder eine Datei vom Host in den Container ein.

Beispiel:

```bash
docker run -d \
  --name web \
  -p 8080:80 \
  -v "$(pwd)":/usr/share/nginx/html \
  nginx
```

Bedeutung:

| Teil                    | Bedeutung                     |
| ----------------------- | ----------------------------- |
| `$(pwd)`                | aktueller Ordner auf dem Host |
| `/usr/share/nginx/html` | Zielordner im Container       |
| `-v`                    | Mount einbinden               |

Wenn man eine Datei im Host-Ordner ändert, sieht der Container die Änderung direkt.

Bind Mounts sind praktisch für Entwicklung und Tests.

---

## Volume vs Bind Mount

Volumes und Bind Mounts werden oft verwechselt.

| Bereich       | Volume                    | Bind Mount                             |
| ------------- | ------------------------- | -------------------------------------- |
| Verwaltung    | Docker verwaltet Speicher | Host-Pfad wird direkt eingebunden      |
| Pfad auf Host | Docker-intern             | frei gewählter Host-Pfad               |
| Nutzung       | dauerhafte App-Daten      | Entwicklung, lokale Dateien, Konfigs   |
| Portabilität  | besser                    | hängt vom Host-Pfad ab                 |
| Sicherheit    | oft kontrollierter        | kann mehr Host-Dateien sichtbar machen |
| Beispiel      | Datenbankdaten            | Projektordner in Webserver             |

Einfache Regel:

```text
Datenbankdaten -> Volume
lokaler Projektordner -> Bind Mount
```

---

## Beispiel: Bind Mount mit nginx

Ordner vorbereiten:

```bash
mkdir web-test
cd web-test
echo "Hallo Docker" > index.html
```

Container starten:

```bash
docker run -d \
  --name web \
  -p 8080:80 \
  -v "$(pwd)":/usr/share/nginx/html \
  nginx
```

Prüfen:

```bash
curl http://localhost:8080
```

Wenn `index.html` lokal geändert wird, ändert sich auch der Inhalt im Container.

Das ist sehr praktisch für einfache Webtests.

---

## Read-only Mounts

Ein Mount kann schreibgeschützt eingebunden werden.

Beispiel:

```bash
docker run -d \
  --name web \
  -p 8080:80 \
  -v "$(pwd)":/usr/share/nginx/html:ro \
  nginx
```

`:ro` bedeutet read-only.

Der Container kann die eingebundenen Dateien lesen, aber nicht verändern.

Das ist sicherer, wenn der Container keine Schreibrechte braucht.

---

## tmpfs Mount

Ein tmpfs Mount speichert Daten nur temporär im RAM.

Beispiel:

```bash
docker run --tmpfs /tmp nginx
```

Daten in tmpfs sind nach dem Stoppen oder Löschen des Containers weg.

tmpfs ist nützlich für:

- temporäre Dateien
- sensible kurzlebige Daten
- Cache ohne dauerhafte Speicherung

Für normale Lernprojekte sind Volumes und Bind Mounts wichtiger.

---

## Mounts anzeigen

Mounts eines Containers sieht man mit:

```bash
docker inspect containername
```

Beispiel:

```bash
docker inspect postgres-db
```

In der Ausgabe gibt es einen Bereich:

```text
Mounts
```

Dort sieht man:

- Volume-Name
- Mount-Typ
- Host-Pfad
- Zielpfad im Container
- Schreibrechte

Bei Problemen mit Daten ist `docker inspect` sehr hilfreich.

---

## Volumes aufräumen

Volumes anzeigen:

```bash
docker volume ls
```

Ungenutzte Volumes löschen:

```bash
docker volume prune
```

Ein bestimmtes Volume löschen:

```bash
docker volume rm volume_name
```

Vorsicht:

```bash
docker volume prune
```

kann Daten löschen, die nicht mehr von Containern genutzt werden.

Vorher prüfen:

```bash
docker ps -a
docker volume ls
docker volume inspect volume_name
```

Gerade bei Datenbanken sollte man Volumes nicht blind löschen.

---

## `docker compose down -v`

Ein sehr wichtiger Befehl:

```bash
docker compose down -v
```

Dieser Befehl stoppt Compose-Container und löscht zusätzlich die Volumes des Compose-Projekts.

Das kann Datenbankdaten löschen.

Normal stoppen:

```bash
docker compose down
```

Mit Volume-Löschung:

```bash
docker compose down -v
```

Merke:

```text
-v bedeutet bei down: Volumes löschen.
```

Bei Datenbanken also vorsichtig.

---

## Backup von Volume-Daten

Volumes sollten bei wichtigen Daten gesichert werden.

Ein einfacher Backup-Gedanke:

```text
Daten aus Volume in Archiv kopieren.
```

Beispiel über temporären Container:

```bash
docker run --rm \
  -v postgres_data:/data \
  -v "$(pwd)":/backup \
  ubuntu \
  tar -czf /backup/postgres_data_backup.tar.gz /data
```

Das ist eher fortgeschritten, zeigt aber das Prinzip:

- Volume wird eingebunden
- Backup-Ordner vom Host wird eingebunden
- Daten werden als Archiv gespeichert

Für echte Datenbanken nutzt man oft zusätzlich datenbankspezifische Backup-Tools.

---

## Warum Netzwerke wichtig sind

Container laufen isoliert.

Trotzdem müssen sie oft miteinander sprechen.

Beispiele:

```text
Web-App -> Datenbank
Adminer -> PostgreSQL
Frontend -> Backend
Monitoring -> Dienst
```

Docker-Netzwerke sorgen dafür, dass Container kontrolliert miteinander kommunizieren können.

Ohne Netzwerkverständnis entstehen schnell Probleme:

- Datenbank nicht erreichbar
- falscher Hostname
- falscher Port
- Container im falschen Netzwerk
- Port nach außen nicht veröffentlicht
- localhost falsch verstanden

---

## Docker-Netzwerke anzeigen

Netzwerke anzeigen:

```bash
docker network ls
```

Typische Ausgabe:

```text
NETWORK ID     NAME      DRIVER    SCOPE
abc123         bridge    bridge    local
def456         host      host      local
ghi789         none      null      local
```

Wichtige Standardnetzwerke:

| Netzwerk         | Bedeutung                                      |
| ---------------- | ---------------------------------------------- |
| `bridge`         | Standardnetzwerk für Container                 |
| `host`           | Container nutzt Host-Netzwerk direkt           |
| `none`           | Container ohne Netzwerk                        |
| eigene Netzwerke | besser für mehrere zusammengehörende Container |

---

## Bridge Network

Das Standardnetzwerk ist meistens `bridge`.

Wenn man einen Container ohne eigenes Netzwerk startet, landet er oft im Bridge-Netzwerk.

Beispiel:

```bash
docker run -d --name web nginx
```

Docker erstellt interne Netzwerkkonnektivität.

Für einfache einzelne Container reicht das oft.

Für mehrere zusammengehörende Container ist ein eigenes Netzwerk besser.

---

## Eigenes Docker-Netzwerk erstellen

Netzwerk erstellen:

```bash
docker network create appnet
```

Prüfen:

```bash
docker network ls
docker network inspect appnet
```

Container in dieses Netzwerk starten:

```bash
docker run -d --name web --network appnet nginx
```

Ein zweiter Container kann in dasselbe Netzwerk:

```bash
docker run -d --name adminer --network appnet adminer
```

Container im gleichen Netzwerk können sich oft über Namen erreichen.

---

## Container über Namen erreichen

In einem eigenen Docker-Netzwerk können Container sich über ihre Namen erreichen.

Beispiel:

```bash
docker network create appnet

docker run -d --name web --network appnet nginx
docker run --rm -it --network appnet ubuntu bash
```

Im Ubuntu-Container könnte man zum Beispiel Tools installieren und `web` ansprechen.

Prinzip:

```text
Containername = DNS-Name im Docker-Netzwerk
```

Das ist besonders wichtig in Docker Compose.

---

## Port Mapping und Docker-Netzwerk unterscheiden

Port Mapping und Docker-Netzwerk sind nicht dasselbe.

| Thema           | Bedeutung                           |
| --------------- | ----------------------------------- |
| Docker-Netzwerk | Container sprechen miteinander      |
| Port Mapping    | Host kann Containerdienst erreichen |

Beispiel:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

Im Browser auf dem Host:

```text
http://localhost:8080
```

Andere Container im gleichen Docker-Netzwerk würden den Dienst eher über Containername und Container-Port erreichen.

---

## localhost in Docker

`localhost` ist bei Docker ein häufiger Denkfehler.

Im Host bedeutet:

```text
localhost = Host-System
```

Im Container bedeutet:

```text
localhost = der Container selbst
```

Wenn ein Container eine Datenbank in einem anderen Container erreichen soll, ist `localhost` meistens falsch.

Besser:

```text
db
postgres
mysql
```

Also der Container- oder Servicename im Docker-Netzwerk.

Beispiel in Compose:

```yaml
services:
  app:
    environment:
      DB_HOST: db

  db:
    image: postgres:16
```

Die App erreicht die Datenbank über `db`.

---

## Host Network

Mit Host Network nutzt ein Container direkt das Netzwerk des Hosts.

Beispiel:

```bash
docker run --network host nginx
```

Das ist auf Linux möglich, aber nicht für jeden Fall sinnvoll.

Eigenschaften:

- kein normales Port Mapping nötig
- Container nutzt Host-Netzwerk direkt
- weniger Isolation
- Port-Konflikte mit Host möglich

Für Lernprojekte und normale Compose-Setups nutzt man meistens Bridge-Netzwerke statt Host Network.

---

## None Network

Ein Container kann ohne Netzwerk gestartet werden.

```bash
docker run --network none ubuntu
```

Dann hat der Container keinen normalen Netzwerkzugriff.

Das kann für Spezialfälle oder Sicherheitstests interessant sein.

Im Alltag ist `none` seltener.

---

## Docker Compose Netzwerke

Docker Compose erstellt meistens automatisch ein eigenes Netzwerk für ein Projekt.

Beispiel:

```yaml
services:
  web:
    image: nginx

  adminer:
    image: adminer
```

Beide Services liegen im gleichen Compose-Netzwerk.

Sie können sich über Servicenamen erreichen:

```text
web
adminer
```

Bei Datenbankprojekten ist das besonders praktisch.

---

## Docker Compose Volumes

In Compose können Volumes sauber definiert werden.

Beispiel PostgreSQL:

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_PASSWORD: example
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

Bedeutung:

| Teil                       | Bedeutung                         |
| -------------------------- | --------------------------------- |
| `db_data`                  | benanntes Volume                  |
| `/var/lib/postgresql/data` | Datenpfad im Container            |
| `volumes:` unten           | Volume wird von Compose verwaltet |

Starten:

```bash
docker compose up -d
```

Prüfen:

```bash
docker compose ps
docker volume ls
```

---

## Compose Beispiel: Datenbank und Adminer

Ein einfaches Compose-Beispiel:

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: example
      POSTGRES_PASSWORD: example
      POSTGRES_DB: app
    volumes:
      - db_data:/var/lib/postgresql/data

  adminer:
    image: adminer
    ports:
      - "8080:8080"

volumes:
  db_data:
```

Starten:

```bash
docker compose up -d
```

Adminer ist erreichbar über:

```text
http://localhost:8080
```

In Adminer als Servername nutzt man:

```text
db
```

weil `db` der Servicename im Compose-Netzwerk ist.

---

## Ports in Docker Compose

Ports werden in Compose so angegeben:

```yaml
ports:
  - "8080:80"
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

Beispiel:

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

Der Webserver ist dann auf dem Host erreichbar über:

```text
http://localhost:8080
```

---

## Expose vs Ports

In Docker gibt es einen Unterschied zwischen `expose` und `ports`.

| Eintrag  | Bedeutung                                       |
| -------- | ----------------------------------------------- |
| `ports`  | veröffentlicht Port auf dem Host                |
| `expose` | dokumentiert/öffnet Port nur im Docker-Netzwerk |

Beispiel:

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

Hier ist der Dienst vom Host erreichbar.

Beispiel:

```yaml
services:
  db:
    image: postgres:16
    expose:
      - "5432"
```

Hier wird der Port nicht automatisch auf dem Host veröffentlicht.

Für Datenbanken ist es oft sicherer, sie nur im Docker-Netzwerk erreichbar zu machen.

---

## Datenbank-Port nicht immer veröffentlichen

Bei einer lokalen Lernumgebung kann man Datenbankports manchmal veröffentlichen.

Beispiel:

```yaml
ports:
  - "5432:5432"
```

Aber das kann Probleme machen:

- Port ist auf dem Host schon belegt
- Datenbank ist unnötig von außen erreichbar
- Konflikte mit lokaler PostgreSQL-Installation
- Sicherheitsrisiko bei falscher Konfiguration

Wenn Adminer oder eine App im gleichen Compose-Netzwerk läuft, braucht man oft kein Host-Port-Mapping für die Datenbank.

Besser:

```yaml
services:
  db:
    image: postgres:16

  adminer:
    image: adminer
    ports:
      - "8080:8080"
```

Adminer erreicht die Datenbank intern über:

```text
db
```

---

## Netzwerkdetails prüfen

Docker-Netzwerk prüfen:

```bash
docker network ls
docker network inspect networkname
```

Bei Compose-Netzwerken sieht der Name oft ungefähr so aus:

```text
projektname_default
```

Alle Container eines Netzwerks sieht man mit:

```bash
docker network inspect networkname
```

Dort stehen unter anderem:

- Container
- IP-Adressen
- Netzwerkname
- Treiber
- Subnetz

---

## Container-IP prüfen

Container-Details:

```bash
docker inspect containername
```

Dort findet man auch Netzwerkinformationen.

Man kann gezielt filtern, aber für den Anfang reicht:

```bash
docker inspect containername
```

Wichtig:

Container-IP-Adressen können sich ändern, wenn Container neu erstellt werden.

Deshalb sollte man Container nicht dauerhaft über Container-IP verbinden, sondern über Namen oder Servicenamen.

---

## Port-Konflikte

Ein häufiger Fehler:

```text
port is already allocated
```

Das bedeutet:

Der Host-Port ist bereits belegt.

Beispiel:

```bash
docker run -d --name web -p 8080:80 nginx
```

Wenn Port 8080 schon genutzt wird, startet der Container nicht korrekt.

Prüfen:

```bash
ss -tulpen | grep 8080
docker ps
docker ps -a
```

Lösung:

- anderen Host-Port nutzen
- alten Container stoppen
- lokalen Dienst stoppen
- Compose-Datei anpassen

Beispiel anderer Host-Port:

```bash
docker run -d --name web -p 8081:80 nginx
```

---

## Netzwerk-Fehlersuche in Docker

Wichtige Befehle:

```bash
docker ps
docker port container
docker logs container
docker inspect container
docker network ls
docker network inspect network
ss -tulpen
curl http://localhost:port
```

Typische Fragen:

```text
Läuft der Container?
Ist der richtige Port veröffentlicht?
Hört der Dienst im Container?
Ist der Host-Port frei?
Sind die Container im gleichen Netzwerk?
Wird der richtige Servicename genutzt?
```

---

## Volume-Fehlersuche in Docker

Wichtige Befehle:

```bash
docker volume ls
docker volume inspect volume
docker inspect container
docker compose ps
docker compose logs
```

Typische Fragen:

```text
Wird ein Volume genutzt?
Ist der richtige Containerpfad gemountet?
Wurde das Volume versehentlich gelöscht?
Wurde docker compose down -v genutzt?
Liegt die Datei im Container oder im Volume?
Ist es ein Volume oder ein Bind Mount?
```

---

## Häufige Fehler

| Fehler                                 | Problem                                  |
| -------------------------------------- | ---------------------------------------- |
| Daten direkt im Container speichern    | Daten können beim Löschen verloren gehen |
| Volume und Bind Mount verwechseln      | falsche Erwartung an Speicherort         |
| `docker compose down -v` blind nutzen  | Volumes werden gelöscht                  |
| falschen Containerpfad mounten         | Anwendung findet Daten nicht             |
| Host-Pfad bei Bind Mount falsch        | Container sieht falschen Ordner          |
| Port-Mapping vergessen                 | Dienst ist vom Host nicht erreichbar     |
| Host-Port bereits belegt               | Container startet nicht richtig          |
| `localhost` zwischen Containern nutzen | zeigt auf den falschen Container         |
| Datenbank-Port unnötig veröffentlichen | Sicherheits- und Konfliktrisiko          |
| Container-IP fest eintragen            | IP kann sich ändern                      |

---

## Praktische Beispiele

### Beispiel 1: Volume erstellen und nutzen

```bash
docker volume create app_data

docker run -d \
  --name app \
  -v app_data:/data \
  ubuntu sleep infinity
```

Prüfen:

```bash
docker volume ls
docker inspect app
```

---

### Beispiel 2: Bind Mount für nginx

```bash
mkdir web-test
cd web-test
echo "Hallo Docker" > index.html

docker run -d \
  --name web \
  -p 8080:80 \
  -v "$(pwd)":/usr/share/nginx/html \
  nginx
```

Prüfen:

```bash
curl http://localhost:8080
```

---

### Beispiel 3: Eigenes Netzwerk

```bash
docker network create appnet

docker run -d --name web --network appnet nginx
docker run --rm -it --network appnet ubuntu bash
```

Danach kann man im zweiten Container Netzwerktools nutzen, wenn sie installiert sind.

---

### Beispiel 4: Compose mit Datenbank und Adminer

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: example
      POSTGRES_PASSWORD: example
      POSTGRES_DB: app
    volumes:
      - db_data:/var/lib/postgresql/data

  adminer:
    image: adminer
    ports:
      - "8080:8080"

volumes:
  db_data:
```

Starten:

```bash
docker compose up -d
```

Adminer Servername:

```text
db
```

---

## Nützliche Befehle

| Befehl                        | Bedeutung                                    |
| ----------------------------- | -------------------------------------------- |
| `docker volume ls`            | Volumes anzeigen                             |
| `docker volume create name`   | Volume erstellen                             |
| `docker volume inspect name`  | Volume-Details anzeigen                      |
| `docker volume rm name`       | Volume löschen                               |
| `docker volume prune`         | ungenutzte Volumes löschen                   |
| `docker network ls`           | Netzwerke anzeigen                           |
| `docker network create name`  | Netzwerk erstellen                           |
| `docker network inspect name` | Netzwerkdetails anzeigen                     |
| `docker network rm name`      | Netzwerk löschen                             |
| `docker network prune`        | ungenutzte Netzwerke löschen                 |
| `docker inspect container`    | Mounts und Netzwerke eines Containers prüfen |
| `docker port container`       | Port-Mapping anzeigen                        |
| `docker ps`                   | laufende Container anzeigen                  |
| `docker ps -a`                | alle Container anzeigen                      |
| `ss -tulpen`                  | offene Host-Ports prüfen                     |
| `curl http://localhost:port`  | Dienst testen                                |
| `docker compose up -d`        | Compose-Projekt starten                      |
| `docker compose down`         | Compose-Projekt stoppen                      |
| `docker compose down -v`      | Compose-Projekt stoppen und Volumes löschen  |
| `docker compose ps`           | Compose-Container anzeigen                   |
| `docker compose logs`         | Compose-Logs anzeigen                        |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Volumes und Netzwerke in Docker besonders wichtig.

In der Praxis bedeutet das:

- Datenverlust vermeiden
- Datenbankdaten dauerhaft speichern
- Container sauber miteinander verbinden
- Port-Mappings verstehen
- Dienste erreichbar machen
- interne und externe Erreichbarkeit unterscheiden
- Docker-Compose-Projekte planen
- Fehler bei Ports, DNS und Netzwerken analysieren
- sichere Konfigurationen dokumentieren
- Testumgebungen reproduzierbar aufbauen

Ein guter FISI weiß, dass Container austauschbar sind. Dauerhafte Daten gehören in Volumes, und Kommunikation zwischen Containern läuft sauber über Docker-Netzwerke und Servicenamen.

---

## Kurze Zusammenfassung

Volumes speichern Daten dauerhaft und unabhängig vom Container.

Bind Mounts verbinden Host-Dateien oder Host-Ordner direkt mit dem Container.

Docker-Netzwerke ermöglichen Kommunikation zwischen Containern. Port Mapping macht Containerdienste vom Host erreichbar.

Wichtige Befehle sind `docker volume ls`, `docker volume create`, `docker volume inspect`, `docker network ls`, `docker network create`, `docker network inspect`, `docker inspect`, `docker port`, `docker compose up -d` und `docker compose down`.

Für FISI ist dieses Kapitel wichtig, weil Datenhaltung und Netzwerkverbindungen zentrale Bestandteile vieler Docker-Projekte sind.
