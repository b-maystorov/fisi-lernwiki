# 5. Logs, Exec und Troubleshooting

In diesem Kapitel geht es um Logs, `exec` und Fehlersuche in Docker.

Docker-Container laufen oft im Hintergrund. Wenn ein Container nicht startet, sofort wieder stoppt oder ein Dienst nicht erreichbar ist, muss man systematisch prüfen. Dafür sind Befehle wie `docker ps`, `docker logs`, `docker exec`, `docker inspect`, `docker stats` und `docker compose logs` besonders wichtig.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Fehleranalyse ein großer Teil der praktischen IT-Arbeit ist. Man muss erkennen können, ob ein Problem am Container, Image, Port, Netzwerk, Volume, Dienst oder an der Konfiguration liegt.

---

## Kurz erklärt

Docker-Troubleshooting bedeutet:

- Containerstatus prüfen
- Logs lesen
- Ports prüfen
- Netzwerke prüfen
- Volumes prüfen
- Konfiguration kontrollieren
- in Container hineingehen
- Prozesse prüfen
- Ressourcen prüfen
- Fehler Schritt für Schritt eingrenzen

Wichtige Befehle:

| Befehl                         | Bedeutung                            |
| ------------------------------ | ------------------------------------ |
| `docker ps`                    | laufende Container anzeigen          |
| `docker ps -a`                 | alle Container anzeigen              |
| `docker logs container`        | Logs eines Containers anzeigen       |
| `docker logs -f container`     | Logs live verfolgen                  |
| `docker exec -it container sh` | Shell im Container öffnen            |
| `docker inspect container`     | technische Details anzeigen          |
| `docker stats`                 | Ressourcenverbrauch anzeigen         |
| `docker top container`         | Prozesse im Container anzeigen       |
| `docker port container`        | Port-Mapping anzeigen                |
| `docker compose logs`          | Logs eines Compose-Projekts anzeigen |
| `docker compose ps`            | Compose-Container anzeigen           |

---

## Warum Logs wichtig sind

Logs sind einer der wichtigsten Startpunkte bei Docker-Problemen.

Ein Container kann zum Beispiel:

- nicht starten
- sofort wieder stoppen
- falsche Konfiguration laden
- keine Datenbankverbindung bekommen
- Port-Konflikte haben
- Berechtigungsprobleme haben
- fehlende Dateien melden
- falsche Umgebungsvariablen nutzen

Viele dieser Informationen stehen in den Logs.

Beispiel:

```bash
docker logs web
```

oder bei Compose:

```bash
docker compose logs web
```

Logs zeigen oft klarer als die Oberfläche, was wirklich passiert.

---

## Containerstatus prüfen

Zuerst sollte man prüfen, ob der Container läuft.

Laufende Container:

```bash
docker ps
```

Alle Container:

```bash
docker ps -a
```

Wichtige Statuswerte:

| Status       | Bedeutung                                      |
| ------------ | ---------------------------------------------- |
| `Up`         | Container läuft                                |
| `Exited`     | Container ist beendet                          |
| `Restarting` | Container startet immer wieder neu             |
| `Created`    | Container wurde erstellt, aber nicht gestartet |
| `Paused`     | Container ist pausiert                         |

Beispiel:

```bash
docker ps -a
```

Wenn ein Container `Exited` ist, sollte man direkt die Logs prüfen:

```bash
docker logs containername
```

---

## Logs anzeigen

Logs eines Containers anzeigen:

```bash
docker logs containername
```

Beispiel:

```bash
docker logs web
```

Letzte Zeilen anzeigen:

```bash
docker logs --tail 50 web
```

Logs live verfolgen:

```bash
docker logs -f web
```

Logs seit einer bestimmten Zeit:

```bash
docker logs --since 1h web
```

Logs mit Zeitstempeln:

```bash
docker logs -t web
```

Diese Befehle helfen besonders bei Webservern, Datenbanken und Anwendungen.

---

## Logs bei Docker Compose

Bei Compose-Projekten nutzt man:

```bash
docker compose logs
```

Logs live:

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

Letzte Zeilen:

```bash
docker compose logs --tail 50 db
```

Typischer Ablauf:

```bash
docker compose ps
docker compose logs
docker compose logs db
```

---

## Container startet und stoppt sofort

Wenn ein Container sofort beendet wird, sieht man ihn oft nur mit:

```bash
docker ps -a
```

Dann:

```bash
docker logs containername
```

Typische Ursachen:

| Ursache                   | Erklärung                                          |
| ------------------------- | -------------------------------------------------- |
| Hauptprozess beendet      | Container lebt nur, solange der Hauptprozess läuft |
| falscher Startbefehl      | `CMD` oder `ENTRYPOINT` falsch                     |
| fehlende Datei            | Anwendung findet Datei nicht                       |
| falsche Umgebungsvariable | Konfiguration unvollständig                        |
| Berechtigungsproblem      | Datei oder Ordner nicht lesbar/schreibbar          |
| Port-Konflikt             | Host-Port ist schon belegt                         |
| Datenbankfehler           | Datenverzeichnis oder Passwortproblem              |

Merke:

```text
Ein Container läuft nur, solange sein Hauptprozess läuft.
```

---

## `docker exec`

Mit `docker exec` führt man Befehle in einem laufenden Container aus.

Beispiel:

```bash
docker exec web ls
```

Interaktive Shell:

```bash
docker exec -it web sh
```

oder:

```bash
docker exec -it web bash
```

Viele kleine Images haben kein `bash`.

Dann nutzt man:

```bash
docker exec -it containername sh
```

`exec` ist sehr wichtig, wenn man im Container prüfen möchte:

- welche Dateien vorhanden sind
- welche Konfiguration geladen wurde
- ob ein Pfad existiert
- ob eine Datei lesbar ist
- welche Umgebung gesetzt ist
- ob Prozesse laufen

---

## Shell im Container öffnen

Beispiel:

```bash
docker exec -it web sh
```

Im Container kann man dann prüfen:

```bash
pwd
ls -la
cat /etc/os-release
env
ps
```

Container verlassen:

```bash
exit
```

Wichtig:

Änderungen im Container sind oft nur kurzfristig sinnvoll.

Dauerhafte Änderungen sollten über Dockerfile, Compose, Volumes oder Konfigurationsdateien erfolgen.

---

## Bash oder sh?

Nicht jedes Image enthält Bash.

Beispiel:

```bash
docker exec -it web bash
```

Wenn das nicht funktioniert:

```bash
docker exec -it web sh
```

Unterschied:

| Shell  | Bedeutung                       |
| ------ | ------------------------------- |
| `bash` | umfangreichere Shell            |
| `sh`   | einfachere Shell, oft vorhanden |

Viele schlanke Images enthalten nur `sh`.

Deshalb ist dieser Befehl oft die bessere erste Wahl:

```bash
docker exec -it containername sh
```

---

## Dateien im Container prüfen

Mit `exec` kann man Dateipfade prüfen.

Beispiel nginx:

```bash
docker exec -it web sh
ls -la /usr/share/nginx/html
cat /usr/share/nginx/html/index.html
```

Beispiel Konfigurationsdatei:

```bash
docker exec web cat /etc/nginx/nginx.conf
```

Das hilft bei Fragen wie:

- wurde die Datei korrekt ins Image kopiert?
- ist der Bind Mount richtig?
- liegt die Datei im erwarteten Ordner?
- hat der Container Zugriff auf die Datei?

---

## Umgebungsvariablen prüfen

Viele Container nutzen Umgebungsvariablen.

Im Container anzeigen:

```bash
docker exec containername env
```

Beispiel:

```bash
docker exec db env
```

Bei Datenbanken können wichtige Variablen sein:

```text
POSTGRES_USER
POSTGRES_PASSWORD
POSTGRES_DB
MYSQL_ROOT_PASSWORD
```

Wichtig:

In öffentlichen Dokumentationen keine echten Passwörter zeigen.

Für Beispiele lieber Platzhalter nutzen.

---

## Prozesse im Container prüfen

Prozesse im Container anzeigen:

```bash
docker top containername
```

Beispiel:

```bash
docker top web
```

Alternativ im Container:

```bash
docker exec -it web sh
ps
```

Je nach Image ist `ps` nicht installiert.

`docker top` funktioniert vom Host aus und ist deshalb oft praktischer.

---

## Ressourcenverbrauch prüfen

Live-Ressourcenverbrauch anzeigen:

```bash
docker stats
```

Nur ein Container:

```bash
docker stats web
```

Typische Werte:

| Wert      | Bedeutung                 |
| --------- | ------------------------- |
| CPU %     | CPU-Nutzung               |
| MEM USAGE | RAM-Nutzung               |
| MEM %     | Anteil am verfügbaren RAM |
| NET I/O   | Netzwerkverkehr           |
| BLOCK I/O | Speicherzugriffe          |
| PIDS      | Anzahl Prozesse           |

Das hilft bei Fragen wie:

- verbraucht ein Container zu viel RAM?
- hängt eine Anwendung?
- läuft ein Container unter hoher Last?
- gibt es ungewöhnlich viele Prozesse?

---

## Technische Details mit `docker inspect`

`docker inspect` zeigt sehr viele technische Informationen.

```bash
docker inspect containername
```

Beispiel:

```bash
docker inspect web
```

Wichtige Bereiche:

| Bereich           | Bedeutung                  |
| ----------------- | -------------------------- |
| `State`           | Containerstatus            |
| `NetworkSettings` | Netzwerkdetails            |
| `Mounts`          | Volumes und Bind Mounts    |
| `Config`          | Image-Konfiguration        |
| `Env`             | Umgebungsvariablen         |
| `HostConfig`      | Host-seitige Einstellungen |
| `Ports`           | Port-Mappings              |

`inspect` ist besonders nützlich, wenn normale Befehle nicht genug Informationen liefern.

---

## Port-Mapping prüfen

Port-Mapping anzeigen:

```bash
docker port containername
```

Beispiel:

```bash
docker port web
```

Auch sichtbar mit:

```bash
docker ps
```

Beispiel:

```text
0.0.0.0:8080->80/tcp
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

Wenn ein Dienst nicht erreichbar ist, sollte man prüfen:

```bash
docker ps
docker port web
ss -tulpen | grep 8080
curl http://localhost:8080
```

---

## Port-Konflikte

Ein häufiger Fehler:

```text
port is already allocated
```

Das bedeutet:

Der Host-Port ist schon belegt.

Prüfen:

```bash
ss -tulpen | grep 8080
docker ps
docker ps -a
```

Lösungen:

- anderen Host-Port nutzen
- alten Container stoppen
- lokalen Dienst stoppen
- Compose-Datei anpassen

Beispiel:

```yaml
ports:
  - "8081:80"
```

statt:

```yaml
ports:
  - "8080:80"
```

---

## Netzwerkprobleme prüfen

Wichtige Befehle:

```bash
docker network ls
docker network inspect networkname
docker inspect containername
docker ps
docker port containername
```

Typische Fragen:

```text
Ist der Container im richtigen Netzwerk?
Nutzen die Services den richtigen Namen?
Wird localhost falsch verwendet?
Ist der Port nach außen veröffentlicht?
Ist der Dienst nur intern erreichbar?
```

Bei Docker Compose ist der Servicename sehr wichtig.

Beispiel:

```text
db
adminer
web
backend
```

Ein Container erreicht einen anderen Container im gleichen Compose-Netzwerk über den Servicenamen, nicht über `localhost`.

---

## localhost-Fehler

Ein sehr häufiger Fehler:

```text
App versucht Datenbank über localhost zu erreichen.
```

Im Container bedeutet `localhost`:

```text
dieser Container selbst
```

Nicht der Host.  
Nicht der andere Container.

Bei Compose sollte man meistens den Servicenamen verwenden.

Beispiel:

```yaml
services:
  app:
    environment:
      DB_HOST: db

  db:
    image: postgres:16
```

Hier ist `db` der richtige Hostname für die Datenbank aus Sicht der App.

---

## Volume-Probleme prüfen

Wichtige Befehle:

```bash
docker volume ls
docker volume inspect volume_name
docker inspect containername
docker compose ps
docker compose logs
```

Typische Fragen:

```text
Wird das richtige Volume genutzt?
Ist der richtige Containerpfad gemountet?
Ist es ein Volume oder ein Bind Mount?
Wurde das Volume gelöscht?
Wurde docker compose down -v genutzt?
Hat der Container Schreibrechte?
```

Bei Datenbanken ist der richtige Datenpfad besonders wichtig.

---

## Bind-Mount-Probleme prüfen

Bei Bind Mounts sollte man auf dem Host prüfen:

```bash
pwd
ls -la
```

Dann Container prüfen:

```bash
docker inspect containername
docker exec -it containername sh
ls -la /ziel/pfad
```

Typische Fehler:

| Fehler                | Problem                                    |
| --------------------- | ------------------------------------------ |
| falscher Host-Pfad    | Container sieht falsche Dateien            |
| relativer Pfad falsch | Compose wurde aus anderem Ordner gestartet |
| fehlende Datei        | Anwendung startet nicht                    |
| Rechteproblem         | Container kann Datei nicht lesen/schreiben |
| `:ro` gesetzt         | Container kann nicht schreiben             |

---

## Compose-Konfiguration prüfen

Compose-Datei prüfen:

```bash
docker compose config
```

Dieser Befehl ist sehr nützlich.

Er zeigt:

- ob YAML korrekt ist
- ob Services erkannt werden
- ob Variablen ersetzt wurden
- welche Ports genutzt werden
- welche Volumes definiert sind
- welche Netzwerke entstehen

Bei Compose-Problemen ist dieser Befehl oft einer der ersten Schritte:

```bash
docker compose config
docker compose ps
docker compose logs
```

---

## YAML-Fehler

Docker Compose nutzt YAML.

Häufige YAML-Fehler:

| Fehler                      | Problem                                 |
| --------------------------- | --------------------------------------- |
| falsche Einrückung          | Struktur wird falsch gelesen            |
| Tabs statt Leerzeichen      | YAML kann fehlschlagen                  |
| Doppelpunkt vergessen       | Syntaxfehler                            |
| Liste falsch geschrieben    | Ports oder Volumes werden nicht erkannt |
| Anführungszeichen vergessen | Werte werden falsch interpretiert       |
| falscher Service-Name       | interne Verbindung klappt nicht         |

Prüfen:

```bash
docker compose config
```

YAML ist streng bei Einrückung.

---

## Container neu erstellen

Manchmal reicht ein Neustart nicht.

Neustart:

```bash
docker compose restart
```

Container neu erstellen:

```bash
docker compose down
docker compose up -d
```

Mit neuem Build:

```bash
docker compose up -d --build
```

Wichtig:

Bei Datenbanken vorsichtig mit:

```bash
docker compose down -v
```

Das löscht Volumes.

---

## Image neu bauen

Wenn ein Dockerfile geändert wurde:

```bash
docker compose build
```

oder direkt:

```bash
docker compose up -d --build
```

Wenn man nur die Compose-Datei geändert hat, reicht oft:

```bash
docker compose up -d
```

Wenn man Code oder Dateien im Image geändert hat, muss eventuell neu gebaut werden.

---

## Daten gehen verloren

Typisches Problem:

```text
Ich habe den Container gelöscht und meine Daten sind weg.
```

Mögliche Ursache:

Die Daten lagen im Container-Dateisystem, nicht in einem Volume.

Prüfen:

```bash
docker volume ls
docker inspect containername
```

Vorbeugung:

- Datenbankdaten in Volume speichern
- wichtige Host-Dateien per Bind Mount einbinden
- `.env` und Daten nicht im Image verstecken
- Backups machen
- `down -v` nur bewusst nutzen

---

## Docker-Speicherplatz prüfen

Docker kann viel Speicherplatz belegen.

Prüfen:

```bash
docker system df
```

Zusätzlich auf Linux:

```bash
df -h
du -sh /var/lib/docker
```

Alte Ressourcen anzeigen:

```bash
docker ps -a
docker images
docker volume ls
docker network ls
```

Aufräumen:

```bash
docker container prune
docker image prune
docker network prune
```

Bei Volumes vorsichtig:

```bash
docker volume prune
```

---

## Aufräumen mit Vorsicht

Gefährlichere Befehle:

```bash
docker system prune -a
docker volume prune
docker compose down -v
```

Diese Befehle können viele Daten löschen.

Vorher prüfen:

```bash
docker ps -a
docker images
docker volume ls
docker system df
```

Merke:

```text
Container kann man oft neu erstellen.
Daten in Volumes können wichtig sein.
```

---

## Logs und Datenschutz

Logs können sensible Daten enthalten.

Beispiele:

- Benutzernamen
- IP-Adressen
- Tokens
- Fehlermeldungen mit Pfaden
- Datenbanknamen
- interne Hostnamen
- API-Endpunkte

Deshalb sollte man Logs nicht ungeprüft in öffentliche Repositories kopieren.

Für Dokumentation besser:

```text
gekürzte Beispielausgaben
anonymisierte Werte
keine echten Passwörter
keine echten Kundendaten
```

---

## Typischer Troubleshooting-Ablauf

Ein guter Ablauf bei Docker-Problemen:

```bash
docker ps -a
docker logs containername
docker inspect containername
docker port containername
docker stats containername
```

Bei Compose:

```bash
docker compose ps
docker compose logs
docker compose config
```

Bei Port-Problemen:

```bash
ss -tulpen
curl http://localhost:port
```

Bei Volume-Problemen:

```bash
docker volume ls
docker volume inspect volume
docker inspect containername
```

Bei Netzwerkproblemen:

```bash
docker network ls
docker network inspect network
```

---

## Beispiel: Webcontainer nicht erreichbar

Problem:

```text
http://localhost:8080 funktioniert nicht.
```

Prüfen:

```bash
docker ps
docker ps -a
docker logs web
docker port web
ss -tulpen | grep 8080
curl http://localhost:8080
```

Mögliche Ursachen:

| Ursache                    | Hinweis                     |
| -------------------------- | --------------------------- |
| Container läuft nicht      | `docker ps` zeigt ihn nicht |
| Container ist exited       | `docker ps -a`              |
| Port nicht gemappt         | `docker port web` leer      |
| falscher Host-Port         | anderer Port in `docker ps` |
| Dienst im Container kaputt | `docker logs web`           |
| Port belegt                | `ss -tulpen`                |

---

## Beispiel: Datenbank startet nicht

Prüfen:

```bash
docker ps -a
docker logs db
docker inspect db
docker volume ls
```

Bei Compose:

```bash
docker compose ps
docker compose logs db
docker compose config
```

Mögliche Ursachen:

- Passwortvariable fehlt
- Volume enthält alte inkompatible Daten
- falscher Datenpfad
- Rechteproblem
- Port-Konflikt
- Image-Version geändert
- `.env` wird nicht geladen

---

## Beispiel: Adminer erreicht Datenbank nicht

Prüfen:

```bash
docker compose ps
docker compose logs adminer
docker compose logs db
docker network ls
docker compose config
```

Wichtige Frage:

```text
Welcher Servername wird in Adminer genutzt?
```

Bei Compose ist es meistens:

```text
db
```

Nicht:

```text
localhost
```

Wenn Adminer und Datenbank im gleichen Compose-Projekt laufen, erreicht Adminer die Datenbank über den Servicenamen.

---

## Beispiel: Compose-Datei geändert, aber nichts passiert

Mögliche Lösung:

```bash
docker compose up -d
```

Wenn ein Image neu gebaut werden muss:

```bash
docker compose up -d --build
```

Wenn man sauber neu erstellen möchte:

```bash
docker compose down
docker compose up -d
```

Vorsicht:

```bash
docker compose down -v
```

nur nutzen, wenn Volumes gelöscht werden dürfen.

---

## Häufige Fehler

| Fehler                                 | Problem                              |
| -------------------------------------- | ------------------------------------ |
| Logs nicht prüfen                      | Ursache bleibt unbekannt             |
| `docker ps` statt `docker ps -a`       | gestoppte Container werden übersehen |
| `localhost` zwischen Containern nutzen | falscher Zielhost                    |
| Port-Mapping vergessen                 | Dienst ist nicht vom Host erreichbar |
| Host-Port schon belegt                 | Container startet nicht              |
| `down -v` blind nutzen                 | Daten werden gelöscht                |
| falscher Volume-Pfad                   | Daten liegen nicht dort, wo erwartet |
| Compose-Datei falsch eingerückt        | Services starten nicht korrekt       |
| Image geändert, aber nicht neu gebaut  | alte Version läuft weiter            |
| echte Logs mit Secrets veröffentlichen | Sicherheitsproblem                   |

---

## Praktische Beispiele

### Beispiel 1: Container prüfen

```bash
docker ps -a
docker logs web
docker inspect web
```

### Beispiel 2: Shell im Container öffnen

```bash
docker exec -it web sh
```

oder:

```bash
docker exec -it web bash
```

### Beispiel 3: Compose-Projekt prüfen

```bash
docker compose ps
docker compose logs
docker compose config
```

### Beispiel 4: Portproblem prüfen

```bash
docker port web
ss -tulpen | grep 8080
curl http://localhost:8080
```

---

## Nützliche Befehle

| Befehl                            | Bedeutung                       |
| --------------------------------- | ------------------------------- |
| `docker ps`                       | laufende Container anzeigen     |
| `docker ps -a`                    | alle Container anzeigen         |
| `docker logs container`           | Logs anzeigen                   |
| `docker logs -f container`        | Logs live verfolgen             |
| `docker logs --tail 50 container` | letzte 50 Logzeilen             |
| `docker exec -it container sh`    | Shell im Container öffnen       |
| `docker exec -it container bash`  | Bash im Container öffnen        |
| `docker inspect container`        | technische Details anzeigen     |
| `docker top container`            | Prozesse im Container anzeigen  |
| `docker stats`                    | Ressourcenverbrauch anzeigen    |
| `docker port container`           | Port-Mapping anzeigen           |
| `docker volume ls`                | Volumes anzeigen                |
| `docker volume inspect volume`    | Volume prüfen                   |
| `docker network ls`               | Netzwerke anzeigen              |
| `docker network inspect network`  | Netzwerk prüfen                 |
| `docker system df`                | Docker-Speichernutzung anzeigen |
| `docker compose ps`               | Compose-Container anzeigen      |
| `docker compose logs`             | Compose-Logs anzeigen           |
| `docker compose logs service`     | Logs eines Services             |
| `docker compose exec service sh`  | Shell in Compose-Service        |
| `docker compose config`           | Compose-Konfiguration prüfen    |
| `docker compose restart`          | Services neu starten            |
| `docker compose up -d --build`    | neu bauen und starten           |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Docker-Troubleshooting sehr wichtig.

In der Praxis bedeutet das:

- Containerstatus prüfen
- Logs auswerten
- Dienste im Container prüfen
- Port-Mappings verstehen
- Netzwerke analysieren
- Volumes kontrollieren
- Compose-Dateien prüfen
- Fehler systematisch eingrenzen
- Datenverlust vermeiden
- sichere Dokumentation ohne Secrets erstellen

Ein guter FISI kopiert nicht blind Befehle, sondern prüft Schritt für Schritt: Läuft der Container? Was sagen die Logs? Sind Ports, Volumes, Netzwerke und Umgebungsvariablen korrekt?

---

## Kurze Zusammenfassung

Docker-Fehlersuche beginnt meistens mit `docker ps -a` und `docker logs`.

Mit `docker exec` kann man in laufenden Containern prüfen, was dort wirklich vorhanden ist. Mit `docker inspect` sieht man technische Details zu Ports, Volumes, Netzwerken und Umgebungsvariablen.

Wichtige Befehle sind `docker ps -a`, `docker logs`, `docker exec -it`, `docker inspect`, `docker port`, `docker stats`, `docker top`, `docker compose ps`, `docker compose logs` und `docker compose config`.

Für FISI ist dieses Kapitel wichtig, weil Container in echten IT-Umgebungen nur dann sinnvoll genutzt werden können, wenn man Fehler sauber analysieren und beheben kann.
