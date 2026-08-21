# Docker-Befehle Cheatsheet

Dieses Cheatsheet enthält wichtige Docker-Befehle für Container, Images, Volumes, Netzwerke, Logs und Fehlersuche.

Die ausführlichen Erklärungen kommen später im eigenen Docker-Bereich. Dieses Cheatsheet dient als schnelle praktische Übersicht.

---

## Grundbegriffe

| Begriff    | Bedeutung                                                         |
| ---------- | ----------------------------------------------------------------- |
| Image      | Vorlage für Container                                             |
| Container  | laufende oder gestoppte Instanz eines Images                      |
| Volume     | dauerhafter Speicher für Containerdaten                           |
| Network    | Docker-Netzwerk für Containerkommunikation                        |
| Dockerfile | Bauanleitung für ein Image                                        |
| Compose    | Werkzeug zum Starten mehrerer Container über `docker-compose.yml` |

Kurz gesagt:

```text
Image = Vorlage
Container = ausgeführte Instanz
Volume = dauerhafte Daten
Network = Verbindung zwischen Containern
Compose = mehrere Container gemeinsam verwalten
```

---

## Docker-Version und Systeminfo

| Befehl                 | Bedeutung                        |
| ---------------------- | -------------------------------- |
| `docker --version`     | zeigt Docker-Version             |
| `docker version`       | zeigt Client- und Server-Version |
| `docker info`          | zeigt Docker-Systeminformationen |
| `docker help`          | zeigt Hilfe                      |
| `docker befehl --help` | zeigt Hilfe zu einem Befehl      |

Beispiel:

```bash
docker --version
docker info
docker ps --help
```

---

## Container anzeigen

| Befehl                     | Bedeutung                      |
| -------------------------- | ------------------------------ |
| `docker ps`                | zeigt laufende Container       |
| `docker ps -a`             | zeigt alle Container           |
| `docker container ls`      | zeigt laufende Container       |
| `docker container ls -a`   | zeigt alle Container           |
| `docker stats`             | zeigt Live-Ressourcenverbrauch |
| `docker top container`     | zeigt Prozesse im Container    |
| `docker inspect container` | zeigt technische Details       |

Beispiel:

```bash
docker ps
docker ps -a
docker stats
docker inspect web
```

---

## Container starten

| Befehl                               | Bedeutung                              |
| ------------------------------------ | -------------------------------------- |
| `docker run image`                   | startet neuen Container aus Image      |
| `docker run -d image`                | startet Container im Hintergrund       |
| `docker run --name name image`       | startet Container mit Namen            |
| `docker run -p host:container image` | veröffentlicht Port                    |
| `docker run -v volume:pfad image`    | bindet Volume ein                      |
| `docker run --rm image`              | löscht Container nach Ende automatisch |
| `docker run -it image bash`          | startet interaktiven Container         |

Beispiele:

```bash
docker run nginx
docker run -d --name web nginx
docker run -d --name web -p 8080:80 nginx
docker run --rm -it ubuntu bash
```

---

## Container stoppen, starten und neu starten

| Befehl                     | Bedeutung                    |
| -------------------------- | ---------------------------- |
| `docker stop container`    | stoppt Container             |
| `docker start container`   | startet gestoppten Container |
| `docker restart container` | startet Container neu        |
| `docker pause container`   | pausiert Container           |
| `docker unpause container` | setzt Container fort         |
| `docker kill container`    | beendet Container hart       |

Beispiel:

```bash
docker stop web
docker start web
docker restart web
```

Vorsicht:

```bash
docker kill web
```

beendet den Container hart. Normal ist meistens `docker stop` besser.

---

## Container löschen

| Befehl                   | Bedeutung                        |
| ------------------------ | -------------------------------- |
| `docker rm container`    | löscht gestoppten Container      |
| `docker rm -f container` | stoppt und löscht Container      |
| `docker container prune` | löscht alle gestoppten Container |

Beispiel:

```bash
docker stop web
docker rm web
```

Oder direkt:

```bash
docker rm -f web
```

Vorsicht:

Ein gelöschter Container ist weg. Daten im Container gehen verloren, wenn sie nicht in einem Volume gespeichert sind.

---

## Images anzeigen und verwalten

| Befehl                   | Bedeutung                 |
| ------------------------ | ------------------------- |
| `docker images`          | zeigt lokale Images       |
| `docker image ls`        | zeigt lokale Images       |
| `docker pull image`      | lädt Image herunter       |
| `docker rmi image`       | löscht Image              |
| `docker image prune`     | löscht ungenutzte Images  |
| `docker build -t name .` | baut Image aus Dockerfile |
| `docker history image`   | zeigt Image-Schichten     |

Beispiele:

```bash
docker images
docker pull nginx
docker rmi nginx
docker build -t myapp:1.0 .
```

---

## Container-Logs

| Befehl                             | Bedeutung                         |
| ---------------------------------- | --------------------------------- |
| `docker logs container`            | zeigt Logs eines Containers       |
| `docker logs -f container`         | verfolgt Logs live                |
| `docker logs --tail 50 container`  | zeigt letzte 50 Logzeilen         |
| `docker logs --since 1h container` | zeigt Logs der letzten Stunde     |
| `docker compose logs`              | zeigt Logs aller Compose-Services |
| `docker compose logs -f service`   | verfolgt Logs eines Services live |

Beispiele:

```bash
docker logs web
docker logs -f web
docker logs --tail 50 web
```

---

## In Container hinein gehen

| Befehl                           | Bedeutung                         |
| -------------------------------- | --------------------------------- |
| `docker exec container befehl`   | führt Befehl im Container aus     |
| `docker exec -it container bash` | öffnet Bash im Container          |
| `docker exec -it container sh`   | öffnet Shell im Container         |
| `docker attach container`        | hängt sich an laufenden Container |

Beispiele:

```bash
docker exec -it web bash
docker exec -it web sh
docker exec web ls -la /usr/share/nginx/html
```

Hinweis:

Viele kleine Images haben kein `bash`, aber meistens `sh`.

Dann nutzt man:

```bash
docker exec -it container sh
```

---

## Dateien zwischen Host und Container kopieren

| Befehl                              | Bedeutung                            |
| ----------------------------------- | ------------------------------------ |
| `docker cp container:/pfad/datei .` | kopiert Datei aus Container auf Host |
| `docker cp datei container:/pfad/`  | kopiert Datei vom Host in Container  |

Beispiele:

```bash
docker cp web:/etc/nginx/nginx.conf .
docker cp index.html web:/usr/share/nginx/html/
```

Das ist praktisch für Tests, aber dauerhafte Änderungen sollten besser über Dockerfile, Volume oder Compose verwaltet werden.

---

## Ports

| Befehl                        | Bedeutung                                      |
| ----------------------------- | ---------------------------------------------- |
| `docker port container`       | zeigt Port-Mappings eines Containers           |
| `docker ps`                   | zeigt veröffentlichte Ports                    |
| `docker run -p 8080:80 nginx` | verbindet Host-Port 8080 mit Container-Port 80 |

Beispiel:

```bash
docker run -d --name web -p 8080:80 nginx
docker port web
```

Dann ist der Container im Browser erreichbar über:

```text
http://localhost:8080
```

---

## Volumes

| Befehl                       | Bedeutung                 |
| ---------------------------- | ------------------------- |
| `docker volume ls`           | zeigt Volumes             |
| `docker volume create name`  | erstellt Volume           |
| `docker volume inspect name` | zeigt Details             |
| `docker volume rm name`      | löscht Volume             |
| `docker volume prune`        | löscht ungenutzte Volumes |

Beispiele:

```bash
docker volume ls
docker volume create db_data
docker volume inspect db_data
```

Volume in Container einbinden:

```bash
docker run -d --name db -v db_data:/var/lib/postgresql/data postgres
```

Wichtig:

Volumes speichern Daten dauerhaft, auch wenn der Container gelöscht wird.

---

## Bind Mounts

Ein Bind Mount verbindet einen Host-Ordner mit einem Container-Ordner.

Beispiel:

```bash
docker run -d --name web -p 8080:80 -v "$(pwd)":/usr/share/nginx/html nginx
```

Bedeutung:

| Teil                    | Bedeutung                        |
| ----------------------- | -------------------------------- |
| `$(pwd)`                | aktueller Ordner auf dem Host    |
| `/usr/share/nginx/html` | Zielordner im Container          |
| `-v`                    | Volume oder Bind Mount einbinden |

Bind Mounts sind praktisch für Entwicklung und Tests.

---

## Netzwerke

| Befehl                            | Bedeutung                                |
| --------------------------------- | ---------------------------------------- |
| `docker network ls`               | zeigt Docker-Netzwerke                   |
| `docker network create name`      | erstellt Netzwerk                        |
| `docker network inspect name`     | zeigt Details                            |
| `docker network rm name`          | löscht Netzwerk                          |
| `docker network prune`            | löscht ungenutzte Netzwerke              |
| `docker run --network name image` | startet Container in bestimmtem Netzwerk |

Beispiele:

```bash
docker network ls
docker network create appnet
docker network inspect appnet
```

Container im gleichen Docker-Netzwerk können sich oft über Container- oder Servicenamen erreichen.

---

## Docker Compose Grundlagen

| Befehl                   | Bedeutung                                 |
| ------------------------ | ----------------------------------------- |
| `docker compose up`      | startet Services aus Compose-Datei        |
| `docker compose up -d`   | startet Services im Hintergrund           |
| `docker compose down`    | stoppt und entfernt Services              |
| `docker compose ps`      | zeigt Compose-Container                   |
| `docker compose logs`    | zeigt Logs                                |
| `docker compose logs -f` | verfolgt Logs live                        |
| `docker compose restart` | startet Services neu                      |
| `docker compose config`  | prüft/zeigt fertige Compose-Konfiguration |

Beispiele:

```bash
docker compose up -d
docker compose ps
docker compose logs -f
docker compose down
```

---

## Docker Compose Services

| Befehl                             | Bedeutung                         |
| ---------------------------------- | --------------------------------- |
| `docker compose up -d service`     | startet bestimmten Service        |
| `docker compose stop service`      | stoppt bestimmten Service         |
| `docker compose restart service`   | startet bestimmten Service neu    |
| `docker compose logs service`      | zeigt Logs eines Services         |
| `docker compose exec service bash` | öffnet Bash im Service-Container  |
| `docker compose exec service sh`   | öffnet Shell im Service-Container |

Beispiele:

```bash
docker compose logs db
docker compose exec db bash
docker compose restart web
```

---

## Compose neu bauen

| Befehl                         | Bedeutung                     |
| ------------------------------ | ----------------------------- |
| `docker compose build`         | baut Images aus Dockerfile    |
| `docker compose up -d --build` | baut neu und startet          |
| `docker compose pull`          | lädt neue Images              |
| `docker compose down`          | stoppt und entfernt Container |
| `docker compose down -v`       | entfernt zusätzlich Volumes   |

Beispiele:

```bash
docker compose build
docker compose up -d --build
```

Vorsicht:

```bash
docker compose down -v
```

löscht auch Volumes. Bei Datenbanken können dadurch Daten verloren gehen.

---

## Dockerfile

| Befehl / Anweisung | Bedeutung                          |
| ------------------ | ---------------------------------- |
| `FROM`             | Basis-Image                        |
| `RUN`              | Befehl beim Image-Build ausführen  |
| `COPY`             | Dateien ins Image kopieren         |
| `WORKDIR`          | Arbeitsordner setzen               |
| `EXPOSE`           | dokumentiert Container-Port        |
| `CMD`              | Standardbefehl beim Containerstart |
| `ENTRYPOINT`       | fester Startbefehl                 |

Beispiel:

```Dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```

Image bauen:

```bash
docker build -t my-nginx .
```

Container starten:

```bash
docker run -d --name web -p 8080:80 my-nginx
```

---

## Container-Details prüfen

| Befehl                     | Bedeutung                   |
| -------------------------- | --------------------------- |
| `docker inspect container` | zeigt technische Details    |
| `docker inspect image`     | zeigt Image-Details         |
| `docker stats container`   | zeigt Ressourcenverbrauch   |
| `docker top container`     | zeigt Prozesse im Container |
| `docker port container`    | zeigt Port-Mapping          |

Beispiele:

```bash
docker inspect web
docker stats web
docker top web
docker port web
```

---

## Aufräumen

| Befehl                   | Bedeutung                                       |
| ------------------------ | ----------------------------------------------- |
| `docker container prune` | löscht gestoppte Container                      |
| `docker image prune`     | löscht ungenutzte Images                        |
| `docker image prune -a`  | löscht alle nicht verwendeten Images            |
| `docker volume prune`    | löscht ungenutzte Volumes                       |
| `docker network prune`   | löscht ungenutzte Netzwerke                     |
| `docker system prune`    | räumt mehrere Docker-Ressourcen auf             |
| `docker system prune -a` | räumt stärker auf, inklusive ungenutzter Images |

Vorsicht:

```bash
docker system prune -a
docker volume prune
docker compose down -v
```

Diese Befehle können wichtige Daten oder Images löschen.

Vorher prüfen:

```bash
docker ps -a
docker images
docker volume ls
docker network ls
```

---

## Typische Admin-Abläufe

### Container starten und prüfen

```bash
docker run -d --name web -p 8080:80 nginx
docker ps
docker logs web
docker port web
```

### In Container gehen

```bash
docker exec -it web sh
```

oder:

```bash
docker exec -it web bash
```

### Container sauber entfernen

```bash
docker stop web
docker rm web
```

### Compose-Projekt starten

```bash
docker compose up -d
docker compose ps
docker compose logs
```

### Compose-Projekt stoppen

```bash
docker compose down
```

---

## Fehlersuche

| Problem                             | Prüfung                                            |
| ----------------------------------- | -------------------------------------------------- |
| Container läuft nicht               | `docker ps -a`                                     |
| Container startet und stoppt sofort | `docker logs container`                            |
| Port nicht erreichbar               | `docker ps`, `docker port container`, `ss -tulpen` |
| falscher Containername              | `docker ps -a`                                     |
| Image fehlt                         | `docker images`, `docker pull image`               |
| Compose-Datei fehlerhaft            | `docker compose config`                            |
| Service startet nicht               | `docker compose logs service`                      |
| Daten verschwunden                  | Volumes prüfen: `docker volume ls`                 |
| Netzwerkproblem                     | `docker network ls`, `docker network inspect name` |
| zu viele alte Ressourcen            | `docker system df`                                 |

Beispiele:

```bash
docker ps -a
docker logs web
docker inspect web
docker system df
```

---

## Port-Probleme prüfen

Wenn ein Container-Port nicht erreichbar ist:

```bash
docker ps
docker port container
ss -tulpen
curl http://localhost:8080
docker logs container
```

Typische Ursachen:

- falscher Host-Port
- Port nicht veröffentlicht
- Dienst im Container läuft nicht
- Container ist gestoppt
- Firewall blockiert Verbindung
- anderer Prozess nutzt den Port bereits

Beispiel Port-Mapping:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

---

## Datenbank-Container

Beispiel PostgreSQL:

```bash
docker run -d \
  --name db \
  -e POSTGRES_PASSWORD=example \
  -v db_data:/var/lib/postgresql/data \
  postgres:16
```

Prüfen:

```bash
docker ps
docker logs db
docker volume ls
```

In Container gehen:

```bash
docker exec -it db bash
```

Wichtig:

Datenbankdaten sollten in einem Volume liegen, sonst können sie beim Löschen des Containers verloren gehen.

---

## Docker und `.env`

Viele Docker-Projekte nutzen `.env`-Dateien.

Beispiel:

```env
POSTGRES_USER=example
POSTGRES_PASSWORD=change_me
POSTGRES_DB=app
```

Wichtig:

Echte `.env`-Dateien gehören meistens nicht ins öffentliche Repository.

In `.gitignore`:

```gitignore
.env
```

Stattdessen kann man eine Beispieldatei nutzen:

```text
.env.example
```

---

## Gefährliche Befehle

| Befehl                             | Risiko                               |
| ---------------------------------- | ------------------------------------ |
| `docker rm -f container`           | stoppt und löscht Container direkt   |
| `docker volume rm volume`          | löscht Volume-Daten                  |
| `docker volume prune`              | löscht ungenutzte Volumes            |
| `docker compose down -v`           | löscht Compose-Container und Volumes |
| `docker image prune -a`            | löscht viele Images                  |
| `docker system prune -a`           | löscht viele Docker-Ressourcen       |
| `docker system prune -a --volumes` | kann sehr viele Daten entfernen      |

Vorher prüfen:

```bash
docker ps -a
docker images
docker volume ls
docker system df
```

---

## Häufige Fehler

| Fehler                                               | Problem                        |
| ---------------------------------------------------- | ------------------------------ |
| Image und Container verwechseln                      | falsche Befehle werden genutzt |
| Container löschen, obwohl Daten nicht im Volume sind | Datenverlust                   |
| Port falsch mappen                                   | Anwendung ist nicht erreichbar |
| `docker compose down -v` blind nutzen                | Volumes werden gelöscht        |
| Logs nicht prüfen                                    | Ursache bleibt unklar          |
| falscher Containername                               | Befehl wirkt nicht             |
| Compose nach Änderung nicht neu bauen                | alte Version läuft weiter      |
| `.env` mit echten Passwörtern committen              | Sicherheitsproblem             |
| zu viele alte Container/Images behalten              | System wird unübersichtlich    |
| keine README zum Docker-Projekt schreiben            | Projekt schwer nachvollziehbar |

---

## Nützliche Befehle kompakt

| Befehl                            | Bedeutung                       |
| --------------------------------- | ------------------------------- |
| `docker ps`                       | laufende Container              |
| `docker ps -a`                    | alle Container                  |
| `docker images`                   | lokale Images                   |
| `docker run -d --name name image` | Container starten               |
| `docker stop name`                | Container stoppen               |
| `docker start name`               | Container starten               |
| `docker restart name`             | Container neu starten           |
| `docker rm name`                  | Container löschen               |
| `docker logs name`                | Logs anzeigen                   |
| `docker logs -f name`             | Logs live verfolgen             |
| `docker exec -it name sh`         | Shell im Container öffnen       |
| `docker inspect name`             | Details anzeigen                |
| `docker stats`                    | Ressourcenverbrauch             |
| `docker volume ls`                | Volumes anzeigen                |
| `docker network ls`               | Netzwerke anzeigen              |
| `docker compose up -d`            | Compose-Projekt starten         |
| `docker compose down`             | Compose-Projekt stoppen         |
| `docker compose logs -f`          | Compose-Logs live               |
| `docker compose ps`               | Compose-Container anzeigen      |
| `docker system df`                | Docker-Speichernutzung anzeigen |

---

## Kurze Zusammenfassung

Dieses Cheatsheet enthält wichtige Docker-Befehle für Container, Images, Volumes, Netzwerke, Logs, Dockerfile, Docker Compose und Fehlersuche.

Die wichtigsten Befehle für den Alltag sind:

```bash
docker ps
docker ps -a
docker images
docker run
docker stop
docker start
docker restart
docker rm
docker logs
docker exec -it
docker inspect
docker volume ls
docker network ls
docker compose up -d
docker compose down
docker compose logs
```

Für FISI ist Docker wichtig, weil Container häufig für Testumgebungen, Datenbanken, Webdienste, lokale Labs und einfache Deployments genutzt werden.
