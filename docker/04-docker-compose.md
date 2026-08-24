# 4. Docker Compose

In diesem Kapitel geht es um Docker Compose.

Docker Compose ist ein Werkzeug, mit dem mehrere zusammengehörende Container gemeinsam definiert, gestartet, gestoppt und verwaltet werden können. Statt viele lange `docker run`-Befehle einzeln einzugeben, beschreibt man die Umgebung in einer YAML-Datei.

Für Fachinformatiker für Systemintegration ist Docker Compose wichtig, weil viele praktische IT-Umgebungen aus mehreren Diensten bestehen: Webserver, Datenbank, Admin-Oberfläche, Backend, Frontend, Cache oder Monitoring.

---

## Kurz erklärt

Docker Compose verwaltet mehrere Container als gemeinsames Projekt.

Die zentrale Datei heißt meistens:

```text
docker-compose.yml
```

oder moderner:

```text
compose.yml
```

Ein Compose-Projekt wird gestartet mit:

```bash
docker compose up -d
```

und gestoppt mit:

```bash
docker compose down
```

Wichtige Begriffe:

| Begriff     | Bedeutung                                   |
| ----------- | ------------------------------------------- |
| Service     | ein Dienst in der Compose-Datei             |
| Image       | verwendete Container-Vorlage                |
| Build       | eigenes Image aus Dockerfile bauen          |
| Ports       | Host-Port mit Container-Port verbinden      |
| Volumes     | dauerhafte Daten oder Host-Ordner einbinden |
| Environment | Umgebungsvariablen setzen                   |
| Networks    | Container miteinander verbinden             |
| Depends_on  | Startreihenfolge grob festlegen             |

---

## Warum Docker Compose genutzt wird

Ein einzelner Container kann mit `docker run` gestartet werden.

Beispiel:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bei mehreren Containern werden die Befehle aber schnell unübersichtlich.

Beispiel:

```text
Webserver
Datenbank
Adminer
Backend
Frontend
```

Mit Docker Compose werden diese Dienste in einer Datei beschrieben.

Vorteile:

- Umgebung ist dokumentiert
- Start ist wiederholbar
- mehrere Container werden gemeinsam verwaltet
- Netzwerke werden automatisch erstellt
- Volumes werden sauber definiert
- Befehle werden kürzer
- Projekte sind leichter auf anderen Systemen startbar

---

## Einfache Compose-Datei

Beispiel für einen nginx-Webserver:

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

Starten:

```bash
docker compose up -d
```

Prüfen:

```bash
docker compose ps
docker compose logs
```

Stoppen:

```bash
docker compose down
```

Der Webserver ist erreichbar über:

```text
http://localhost:8080
```

---

## Aufbau einer Compose-Datei

Eine Compose-Datei besteht meistens aus mehreren Bereichen.

Beispiel:

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"

volumes:
  web_data:

networks:
  appnet:
```

Wichtige Hauptbereiche:

| Bereich    | Bedeutung                                   |
| ---------- | ------------------------------------------- |
| `services` | beschreibt die Container/Dienste            |
| `volumes`  | definiert benannte Volumes                  |
| `networks` | definiert Netzwerke                         |
| `configs`  | Konfigurationsobjekte, eher fortgeschritten |
| `secrets`  | sensible Daten, eher fortgeschritten        |

Der wichtigste Bereich ist fast immer:

```yaml
services:
```

---

## Services

Ein Service beschreibt einen Container-Typ im Compose-Projekt.

Beispiel:

```yaml
services:
  web:
    image: nginx:latest
```

Hier heißt der Service:

```text
web
```

Docker Compose erstellt daraus einen Container.

Der Servicename ist wichtig, weil andere Services ihn im Docker-Netzwerk als DNS-Namen nutzen können.

Beispiel:

```text
db
adminer
web
backend
frontend
```

---

## Image in Compose

Ein Service kann direkt ein fertiges Image verwenden.

Beispiel:

```yaml
services:
  web:
    image: nginx:latest
```

Oder mit fester Version:

```yaml
services:
  db:
    image: postgres:16
```

Feste Versionen sind oft besser als `latest`, weil das Projekt reproduzierbarer bleibt.

Besser:

```yaml
image: postgres:16
```

statt:

```yaml
image: postgres:latest
```

---

## Build in Compose

Ein Service kann auch aus einem eigenen Dockerfile gebaut werden.

Beispiel:

```yaml
services:
  app:
    build: .
    ports:
      - "8000:8000"
```

Das bedeutet:

Docker Compose baut ein Image aus dem Dockerfile im aktuellen Ordner.

Mit Dockerfile-Pfad:

```yaml
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
```

Neu bauen und starten:

```bash
docker compose up -d --build
```

---

## Ports

Ports verbinden den Host mit dem Container.

Beispiel:

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

Im Browser:

```text
http://localhost:8080
```

Wichtig:

Der linke Port ist der Port auf dem Host.  
Der rechte Port ist der Port im Container.

```text
"HOST:CONTAINER"
```

---

## Port-Konflikte

Ein häufiger Fehler:

```text
port is already allocated
```

Das bedeutet:

Der Host-Port ist bereits belegt.

Beispiel:

```yaml
ports:
  - "8080:80"
```

Wenn ein anderer Dienst schon Port `8080` nutzt, kann der Container nicht starten.

Prüfen:

```bash
ss -tulpen | grep 8080
docker ps
docker ps -a
```

Lösung:

```yaml
ports:
  - "8081:80"
```

Dann ist der Dienst über Port `8081` erreichbar.

---

## Volumes in Compose

Volumes speichern Daten dauerhaft.

Beispiel mit PostgreSQL:

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

| Teil                       | Bedeutung                                |
| -------------------------- | ---------------------------------------- |
| `db_data`                  | benanntes Volume                         |
| `/var/lib/postgresql/data` | Datenpfad im Container                   |
| `volumes:` unten           | Volume wird im Compose-Projekt definiert |

Starten:

```bash
docker compose up -d
```

Volumes prüfen:

```bash
docker volume ls
```

---

## Bind Mounts in Compose

Ein Bind Mount bindet einen Host-Ordner in den Container ein.

Beispiel:

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
```

Bedeutung:

| Teil                    | Bedeutung                      |
| ----------------------- | ------------------------------ |
| `./html`                | Ordner im Projekt auf dem Host |
| `/usr/share/nginx/html` | Zielordner im Container        |

Wenn man Dateien in `./html` ändert, sieht der Container die Änderung.

Bind Mounts sind praktisch für:

- Entwicklung
- Konfigurationsdateien
- lokale Testdateien
- Webinhalte
- Skripte

---

## Volume vs Bind Mount in Compose

| Bereich      | Volume                                    | Bind Mount                           |
| ------------ | ----------------------------------------- | ------------------------------------ |
| Beispiel     | `db_data:/var/lib/postgresql/data`        | `./html:/usr/share/nginx/html`       |
| Verwaltung   | Docker verwaltet Speicher                 | Host-Pfad wird genutzt               |
| Nutzung      | Datenbanken, dauerhafte Daten             | Projektdateien, Entwicklung          |
| Portabilität | besser                                    | hängt vom Pfad ab                    |
| Risiko       | Volume kann mit `down -v` gelöscht werden | Host-Dateien können verändert werden |

Einfache Regel:

```text
Datenbankdaten -> Volume
Projektdateien -> Bind Mount
```

---

## Environment Variables

Viele Images brauchen Umgebungsvariablen.

Beispiel PostgreSQL:

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: example
      POSTGRES_PASSWORD: example
      POSTGRES_DB: app
```

Umgebungsvariablen werden genutzt für:

- Datenbankname
- Benutzername
- Passwort
- Port
- Konfigurationswerte
- App-Einstellungen

Wichtig:

Echte Passwörter gehören nicht in öffentliche Repositories.

Für öffentliche Beispiele lieber Platzhalter nutzen.

---

## `.env` mit Compose

Docker Compose kann Werte aus einer `.env`-Datei lesen.

Beispiel `.env`:

```env
POSTGRES_USER=example
POSTGRES_PASSWORD=change_me
POSTGRES_DB=app
```

Compose-Datei:

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: ${POSTGRES_USER}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
      POSTGRES_DB: ${POSTGRES_DB}
```

Wichtig:

Die echte `.env` sollte meistens in `.gitignore` stehen.

```gitignore
.env
```

Für GitHub kann man eine Beispieldatei nutzen:

```text
.env.example
```

---

## Networks in Compose

Docker Compose erstellt normalerweise automatisch ein eigenes Netzwerk.

Beispiel:

```yaml
services:
  web:
    image: nginx

  adminer:
    image: adminer
```

Beide Services sind im gleichen Compose-Netzwerk.

Sie können sich über ihre Servicenamen erreichen:

```text
web
adminer
```

Bei Datenbankprojekten ist das sehr wichtig.

Beispiel:

```text
adminer -> db
app -> db
backend -> postgres
```

---

## Eigenes Netzwerk definieren

Man kann Netzwerke auch selbst benennen.

```yaml
services:
  web:
    image: nginx
    networks:
      - appnet

  db:
    image: postgres:16
    networks:
      - appnet

networks:
  appnet:
```

Dadurch liegen `web` und `db` im gleichen Netzwerk.

Prüfen:

```bash
docker network ls
docker network inspect projektname_appnet
```

---

## Service-Namen als DNS-Namen

In Docker Compose kann ein Service andere Services über den Servicenamen erreichen.

Beispiel:

```yaml
services:
  db:
    image: postgres:16

  adminer:
    image: adminer
    ports:
      - "8080:8080"
```

Adminer erreicht PostgreSQL über:

```text
db
```

Nicht über:

```text
localhost
```

Wichtig:

`localhost` im Container bedeutet der Container selbst.

Für andere Container nutzt man den Servicenamen.

---

## depends_on

Mit `depends_on` kann man eine grobe Startreihenfolge festlegen.

Beispiel:

```yaml
services:
  app:
    build: .
    depends_on:
      - db

  db:
    image: postgres:16
```

Das bedeutet:

`db` wird vor `app` gestartet.

Wichtig:

`depends_on` bedeutet nicht automatisch, dass die Datenbank schon vollständig bereit ist.

Es bedeutet nur, dass der Container gestartet wird.

Für echte Bereitschaft braucht man manchmal Healthchecks oder Warte-Logik in der Anwendung.

---

## Healthcheck

Ein Healthcheck prüft, ob ein Container wirklich gesund ist.

Ein einfaches Beispiel:

```yaml
services:
  web:
    image: nginx:latest
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost"]
      interval: 30s
      timeout: 10s
      retries: 3
```

Healthchecks sind nützlich für:

- Webdienste
- APIs
- Datenbanken
- produktionsnähere Umgebungen
- Monitoring

Für einfache Lernprojekte sind sie nicht immer nötig, aber gut zu kennen.

---

## restart Policy

Man kann festlegen, ob ein Container automatisch neu starten soll.

Beispiel:

```yaml
services:
  web:
    image: nginx:latest
    restart: unless-stopped
```

Häufige Werte:

| Wert             | Bedeutung                             |
| ---------------- | ------------------------------------- |
| `no`             | kein automatischer Neustart           |
| `always`         | immer neu starten                     |
| `unless-stopped` | neu starten, außer man stoppt manuell |
| `on-failure`     | nur bei Fehler neu starten            |

Für einfache Testprojekte reicht oft keine Restart-Policy.

Für dauerhaft laufende Dienste kann `unless-stopped` sinnvoll sein.

---

## container_name

Man kann einen festen Containernamen setzen.

```yaml
services:
  web:
    image: nginx
    container_name: web
```

Das kann für Lernprojekte übersichtlich sein.

Aber in größeren Compose-Projekten kann es auch Nachteile haben:

- Namen können kollidieren
- Skalierung wird schwerer
- Compose erzeugt normalerweise selbst sinnvolle Namen

Für einfache lokale Projekte ist `container_name` okay.

Für professionellere Compose-Projekte lässt man Compose oft die Namen verwalten.

---

## compose.yml vs docker-compose.yml

Heute wird oft genutzt:

```text
compose.yml
```

oder:

```text
docker-compose.yml
```

Beide sind üblich.

Viele Projekte nutzen noch:

```text
docker-compose.yml
```

Wichtig ist, dass Docker Compose die Datei erkennt.

Starten:

```bash
docker compose up -d
```

Bei spezieller Datei:

```bash
docker compose -f dateiname.yml up -d
```

---

## `docker compose up`

Compose-Projekt starten:

```bash
docker compose up
```

Im Hintergrund starten:

```bash
docker compose up -d
```

Mit Build:

```bash
docker compose up -d --build
```

Bedeutung:

| Befehl    | Bedeutung                 |
| --------- | ------------------------- |
| `up`      | erstellt/startet Services |
| `-d`      | läuft im Hintergrund      |
| `--build` | Images vorher neu bauen   |

Im Alltag nutzt man oft:

```bash
docker compose up -d
```

---

## `docker compose down`

Compose-Projekt stoppen und Container entfernen:

```bash
docker compose down
```

Wichtig:

`down` löscht Container und Netzwerke des Compose-Projekts, aber nicht automatisch benannte Volumes.

Mit Volumes löschen:

```bash
docker compose down -v
```

Vorsicht:

```text
docker compose down -v löscht Volumes.
```

Bei Datenbanken kann das Daten löschen.

---

## `docker compose stop` und `start`

Container stoppen, aber nicht entfernen:

```bash
docker compose stop
```

Wieder starten:

```bash
docker compose start
```

Unterschied:

| Befehl    | Bedeutung                     |
| --------- | ----------------------------- |
| `down`    | stoppt und entfernt Container |
| `stop`    | stoppt Container, behält sie  |
| `start`   | startet gestoppte Container   |
| `restart` | startet neu                   |

Für Testprojekte nutzt man oft `down`.

Für kurzzeitiges Pausieren kann `stop` sinnvoll sein.

---

## Status anzeigen

Compose-Status anzeigen:

```bash
docker compose ps
```

Alle Docker-Container:

```bash
docker ps
docker ps -a
```

Compose-Services prüfen:

```bash
docker compose ps
```

Das zeigt, welche Services laufen und welche Ports veröffentlicht sind.

---

## Logs anzeigen

Logs aller Services:

```bash
docker compose logs
```

Logs live verfolgen:

```bash
docker compose logs -f
```

Logs eines bestimmten Services:

```bash
docker compose logs db
```

Live-Logs eines Services:

```bash
docker compose logs -f db
```

Logs sind einer der wichtigsten Startpunkte bei Docker-Compose-Fehlersuche.

---

## Exec in Compose

Befehl in einem Service ausführen:

```bash
docker compose exec service befehl
```

Beispiel:

```bash
docker compose exec db bash
```

Falls Bash nicht vorhanden ist:

```bash
docker compose exec db sh
```

Beispiel PostgreSQL:

```bash
docker compose exec db psql -U example -d app
```

`exec` funktioniert nur, wenn der Service-Container läuft.

---

## Compose-Konfiguration prüfen

Compose-Datei prüfen und aufgelöste Konfiguration anzeigen:

```bash
docker compose config
```

Das ist sehr hilfreich bei YAML-Problemen.

Der Befehl zeigt:

- ob die Datei syntaktisch korrekt ist
- wie Variablen ersetzt wurden
- welche Services erkannt werden
- welche Volumes und Netzwerke definiert sind

Vor Fehlersuche lohnt sich oft:

```bash
docker compose config
```

---

## Compose-Projektname

Docker Compose nutzt einen Projektnamen.

Standardmäßig ist das oft der Name des Ordners.

Beispiel:

```text
metropolis-library-db
```

Daraus entstehen Namen wie:

```text
metropolis-library-db-db-1
metropolis-library-db-adminer-1
metropolis-library-db_default
```

Man kann den Projektnamen setzen:

```bash
docker compose -p testprojekt up -d
```

Das ist nützlich, wenn man mehrere ähnliche Compose-Projekte parallel testen möchte.

---

## Beispiel: Webserver mit nginx

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

Starten:

```bash
docker compose up -d
```

Prüfen:

```bash
docker compose ps
curl http://localhost:8080
docker compose logs web
```

Stoppen:

```bash
docker compose down
```

---

## Beispiel: PostgreSQL und Adminer

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: example
      POSTGRES_PASSWORD: example
      POSTGRES_DB: library
    volumes:
      - db_data:/var/lib/postgresql/data

  adminer:
    image: adminer
    ports:
      - "8080:8080"
    depends_on:
      - db

volumes:
  db_data:
```

Starten:

```bash
docker compose up -d
```

Prüfen:

```bash
docker compose ps
docker compose logs db
docker compose logs adminer
```

Adminer öffnen:

```text
http://localhost:8080
```

Servername in Adminer:

```text
db
```

---

## Datenbank-Port nicht immer veröffentlichen

In Compose muss man den Datenbank-Port nicht immer auf den Host veröffentlichen.

Beispiel ohne Host-Port:

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_PASSWORD: example

  adminer:
    image: adminer
    ports:
      - "8080:8080"
```

Adminer erreicht die Datenbank intern über:

```text
db
```

Vorteile:

- weniger Port-Konflikte
- Datenbank ist nicht unnötig auf dem Host offen
- sicherer für lokale Testumgebungen
- einfacher bei mehreren Projekten

---

## Compose und YAML

Docker Compose nutzt YAML.

Wichtige YAML-Regeln:

- Einrückung ist wichtig
- Leerzeichen statt Tabs nutzen
- Listen beginnen mit `-`
- Schlüssel und Werte werden mit `:` getrennt
- Strings können in Anführungszeichen stehen
- falsche Einrückung führt oft zu Fehlern

Beispiel:

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

Falsch wäre zum Beispiel:

```yaml
services:
web:
image: nginx
```

Die Struktur geht verloren.

---

## Compose-Datei nach Änderung anwenden

Wenn man die Compose-Datei ändert, muss man das Projekt neu starten oder neu erstellen.

Oft reicht:

```bash
docker compose up -d
```

Wenn ein Image neu gebaut werden muss:

```bash
docker compose up -d --build
```

Wenn man sauber neu starten möchte:

```bash
docker compose down
docker compose up -d
```

Bei Datenbanken vorsichtig mit:

```bash
docker compose down -v
```

Das löscht Volumes.

---

## Typischer Compose-Workflow

Ein sauberer Ablauf:

```bash
docker compose config
docker compose up -d
docker compose ps
docker compose logs
```

Testen:

```bash
curl http://localhost:8080
```

Stoppen:

```bash
docker compose down
```

Bei Problemen:

```bash
docker compose ps
docker compose logs service
docker inspect container
docker network ls
docker volume ls
```

---

## Compose und Git

Eine Compose-Umgebung sollte sauber im Repository dokumentiert sein.

Sinnvolle Dateien:

```text
README.md
docker-compose.yml
Dockerfile
.env.example
scripts/
configs/
```

Nicht ins öffentliche Repository:

```text
.env
echte Passwörter
private Schlüssel
lokale Datenbankdaten
große Dumps
private Logs
```

Beispiel `.gitignore`:

```gitignore
.env
*.log
data/
private/
```

Die README sollte erklären:

- wie man startet
- welche Ports genutzt werden
- welche Services existieren
- wie man Logs prüft
- wie man stoppt
- welche Daten dauerhaft gespeichert werden

---

## Häufige Fehler

| Fehler                                                | Problem                                      |
| ----------------------------------------------------- | -------------------------------------------- |
| YAML falsch eingerückt                                | Compose-Datei wird nicht korrekt gelesen     |
| falscher Port                                         | Dienst ist nicht erreichbar                  |
| Host-Port bereits belegt                              | Container startet nicht                      |
| `localhost` zwischen Containern genutzt               | falscher Zielhost                            |
| Datenbank-Port unnötig veröffentlicht                 | Port-Konflikt oder Sicherheitsrisiko         |
| `down -v` blind genutzt                               | Volumes und Daten werden gelöscht            |
| `.env` committed                                      | Zugangsdaten können öffentlich werden        |
| Compose geändert, aber nicht neu gestartet            | alte Konfiguration läuft weiter              |
| Logs nicht geprüft                                    | Ursache bleibt unklar                        |
| `depends_on` als vollständige Bereitschaft verstanden | Dienst ist gestartet, aber noch nicht bereit |

---

## Praktische Beispiele

### Beispiel 1: Compose-Projekt starten

```bash
docker compose up -d
docker compose ps
docker compose logs
```

### Beispiel 2: Logs eines Services prüfen

```bash
docker compose logs db
docker compose logs -f db
```

### Beispiel 3: Shell in Service öffnen

```bash
docker compose exec db bash
```

oder:

```bash
docker compose exec db sh
```

### Beispiel 4: Projekt stoppen

```bash
docker compose down
```

Mit Volume-Löschung:

```bash
docker compose down -v
```

Nur nutzen, wenn die Daten wirklich gelöscht werden sollen.

---

## Nützliche Befehle

| Befehl                             | Bedeutung                                |
| ---------------------------------- | ---------------------------------------- |
| `docker compose up`                | Services starten                         |
| `docker compose up -d`             | Services im Hintergrund starten          |
| `docker compose up -d --build`     | neu bauen und starten                    |
| `docker compose down`              | Services stoppen und Container entfernen |
| `docker compose down -v`           | zusätzlich Volumes löschen               |
| `docker compose stop`              | Services stoppen                         |
| `docker compose start`             | Services starten                         |
| `docker compose restart`           | Services neu starten                     |
| `docker compose ps`                | Compose-Container anzeigen               |
| `docker compose logs`              | Logs anzeigen                            |
| `docker compose logs -f`           | Logs live verfolgen                      |
| `docker compose logs service`      | Logs eines Services                      |
| `docker compose exec service sh`   | Shell im Service öffnen                  |
| `docker compose config`            | Compose-Datei prüfen                     |
| `docker compose build`             | Images bauen                             |
| `docker compose pull`              | Images herunterladen                     |
| `docker compose -f file.yml up -d` | bestimmte Compose-Datei nutzen           |
| `docker compose -p name up -d`     | Projektnamen setzen                      |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Docker Compose sehr praktisch.

In der Praxis bedeutet das:

- mehrere Dienste gemeinsam starten
- Testumgebungen dokumentieren
- Datenbanken mit Admin-Tools bereitstellen
- Webdienste lokal testen
- Ports und Netzwerke verstehen
- Volumes für dauerhafte Daten definieren
- Logs und Servicezustände prüfen
- Projekte reproduzierbar machen
- `.env` und Beispielkonfigurationen sauber trennen
- Grundlagen für DevOps und Deployment verstehen

Ein guter FISI nutzt Docker Compose nicht nur zum Starten von Containern, sondern versteht, wie Services, Netzwerke, Volumes, Ports und Umgebungsvariablen zusammenhängen.

---

## Kurze Zusammenfassung

Docker Compose verwaltet mehrere Container über eine YAML-Datei.

Die wichtigsten Bereiche einer Compose-Datei sind `services`, `volumes` und `networks`.

Wichtige Befehle sind `docker compose up -d`, `docker compose down`, `docker compose ps`, `docker compose logs`, `docker compose exec`, `docker compose config` und `docker compose up -d --build`.

Für FISI ist Docker Compose wichtig, weil damit kleine IT-Umgebungen wie Webserver, Datenbanken, Admin-Tools und Testsysteme sauber beschrieben und gestartet werden können.
