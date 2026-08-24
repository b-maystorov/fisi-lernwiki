# 2. Images und Container

In diesem Kapitel geht es um Images und Container in Docker.

Images und Container sind die wichtigsten Grundbausteine von Docker. Ein Image ist die Vorlage. Ein Container ist die gestartete Instanz dieser Vorlage. Viele Docker-Probleme entstehen, wenn man diese beiden Begriffe verwechselt.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil man Container starten, prüfen, stoppen, löschen und neu erstellen können muss. Außerdem muss man verstehen, welche Daten im Container liegen und welche besser dauerhaft in Volumes gespeichert werden.

---

## Kurz erklärt

Ein Docker-Image ist eine Vorlage.

Ein Docker-Container ist eine laufende oder gestoppte Instanz eines Images.

| Begriff       | Bedeutung                           |
| ------------- | ----------------------------------- |
| Image         | Vorlage für Container               |
| Container     | gestartete Instanz eines Images     |
| Tag           | Version oder Variante eines Images  |
| Registry      | Speicherort für Images              |
| Docker Hub    | bekannte öffentliche Image-Registry |
| Layer         | Schicht eines Images                |
| Container-ID  | eindeutige ID eines Containers      |
| Containername | lesbarer Name für einen Container   |

Kurz gesagt:

```text
Image = Bauplan / Vorlage
Container = gestartete Ausführung aus dieser Vorlage
```

---

## Image und Container unterscheiden

Ein Image selbst läuft nicht.

Ein Container läuft oder ist gestoppt.

Beispiel:

```bash
docker pull nginx
docker run -d --name web nginx
```

Dabei passiert:

| Schritt                | Bedeutung                                          |
| ---------------------- | -------------------------------------------------- |
| `docker pull nginx`    | lädt das Image `nginx`                             |
| `docker run ... nginx` | erstellt und startet einen Container aus dem Image |
| `--name web`           | gibt dem Container den Namen `web`                 |

Danach gibt es:

```text
Image: nginx
Container: web
```

Ein Image kann für mehrere Container verwendet werden.

---

## Beispiel mit mehreren Containern aus einem Image

Ein Image kann mehrfach gestartet werden.

Beispiel:

```bash
docker run -d --name web1 -p 8081:80 nginx
docker run -d --name web2 -p 8082:80 nginx
```

Beide Container nutzen das gleiche Image:

```text
nginx
```

Aber sie sind unterschiedliche Container:

```text
web1
web2
```

Prüfen:

```bash
docker ps
```

Im Browser:

```text
http://localhost:8081
http://localhost:8082
```

---

## Images anzeigen

Lokale Images anzeigen:

```bash
docker images
```

oder:

```bash
docker image ls
```

Beispielausgabe:

```text
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
nginx        latest    abc123...      2 weeks ago    190MB
ubuntu       latest    def456...      1 month ago    80MB
postgres     16        ghi789...      3 weeks ago    430MB
```

Wichtige Spalten:

| Spalte       | Bedeutung             |
| ------------ | --------------------- |
| `REPOSITORY` | Name des Images       |
| `TAG`        | Version oder Variante |
| `IMAGE ID`   | eindeutige Image-ID   |
| `CREATED`    | Erstellungszeitpunkt  |
| `SIZE`       | Speichergröße         |

---

## Images herunterladen

Ein Image lädt man mit `docker pull`.

```bash
docker pull nginx
```

Mit bestimmtem Tag:

```bash
docker pull nginx:latest
docker pull postgres:16
docker pull ubuntu:24.04
```

Wenn kein Tag angegeben wird, nutzt Docker meistens:

```text
latest
```

Beispiel:

```bash
docker pull nginx
```

ist ungefähr:

```bash
docker pull nginx:latest
```

---

## Image-Tags

Tags beschreiben Versionen oder Varianten eines Images.

Beispiele:

```text
nginx:latest
postgres:16
ubuntu:24.04
python:3.12
node:20
```

Der Tag steht nach dem Doppelpunkt.

| Beispiel       | Bedeutung             |
| -------------- | --------------------- |
| `nginx:latest` | nginx mit Tag latest  |
| `postgres:16`  | PostgreSQL Version 16 |
| `ubuntu:24.04` | Ubuntu 24.04          |
| `python:3.12`  | Python 3.12           |

Wichtig:

`latest` bedeutet nicht automatisch „beste Version“. Es ist nur ein Tag.

Für reproduzierbare Projekte sind feste Versionen oft besser.

---

## Warum feste Image-Versionen wichtig sind

Wenn man immer `latest` nutzt, kann sich das Image später ändern.

Beispiel:

```yaml
image: postgres:latest
```

Heute kann das eine andere Version sein als in einigen Monaten.

Besser:

```yaml
image: postgres:16
```

Vorteile fester Versionen:

- Umgebung bleibt stabiler
- Fehler sind leichter nachvollziehbar
- Projekt ist besser reproduzierbar
- Dokumentation passt besser zur echten Version
- Updates passieren bewusster

Für Lernprojekte ist `latest` manchmal okay. Für sauber dokumentierte Projekte sind feste Tags besser.

---

## Image-Details anzeigen

Details zu einem Image anzeigen:

```bash
docker inspect nginx
```

oder mit Tag:

```bash
docker inspect nginx:latest
```

Image-Historie anzeigen:

```bash
docker history nginx
```

`docker history` zeigt die Schichten eines Images.

Das ist interessant, wenn man verstehen möchte, wie ein Image aufgebaut ist.

---

## Image löschen

Ein Image löscht man mit:

```bash
docker rmi image
```

Beispiel:

```bash
docker rmi nginx
```

Mit Tag:

```bash
docker rmi nginx:latest
```

Wenn noch Container auf diesem Image basieren, kann Docker das Löschen verhindern.

Dann muss man zuerst die Container löschen oder ein anderes Image verwenden.

---

## Ungenutzte Images löschen

Ungenutzte Images löschen:

```bash
docker image prune
```

Stärker aufräumen:

```bash
docker image prune -a
```

Vorsicht:

```bash
docker image prune -a
```

löscht alle Images, die gerade von keinem Container genutzt werden.

Vorher prüfen:

```bash
docker images
docker ps -a
docker system df
```

---

## Container anzeigen

Laufende Container anzeigen:

```bash
docker ps
```

Alle Container anzeigen:

```bash
docker ps -a
```

Beispielausgabe:

```text
CONTAINER ID   IMAGE     COMMAND                  STATUS          PORTS                  NAMES
abc123         nginx     "/docker-entrypoint..."  Up 2 minutes    0.0.0.0:8080->80/tcp   web
```

Wichtige Spalten:

| Spalte         | Bedeutung               |
| -------------- | ----------------------- |
| `CONTAINER ID` | eindeutige Container-ID |
| `IMAGE`        | verwendetes Image       |
| `COMMAND`      | Startbefehl             |
| `STATUS`       | Zustand                 |
| `PORTS`        | Port-Mapping            |
| `NAMES`        | Containername           |

---

## Container starten mit `docker run`

Ein Container wird mit `docker run` erstellt und gestartet.

```bash
docker run nginx
```

Im Hintergrund starten:

```bash
docker run -d nginx
```

Mit Namen:

```bash
docker run -d --name web nginx
```

Mit Port-Mapping:

```bash
docker run -d --name web -p 8080:80 nginx
```

Mit automatischem Löschen nach Ende:

```bash
docker run --rm ubuntu echo "Hallo Docker"
```

---

## Wichtige Optionen bei `docker run`

| Option      | Bedeutung                               |
| ----------- | --------------------------------------- |
| `-d`        | detached, läuft im Hintergrund          |
| `--name`    | Containername setzen                    |
| `-p`        | Port veröffentlichen                    |
| `-v`        | Volume oder Bind Mount einbinden        |
| `-e`        | Umgebungsvariable setzen                |
| `--rm`      | Container nach Ende automatisch löschen |
| `-it`       | interaktive Terminal-Sitzung            |
| `--network` | bestimmtes Netzwerk nutzen              |

Beispiel:

```bash
docker run -d --name web -p 8080:80 nginx
```

---

## Container im Vordergrund

Ohne `-d` läuft ein Container im Vordergrund.

Beispiel:

```bash
docker run nginx
```

Das Terminal bleibt dann an den Container gebunden.

Abbrechen:

```text
Ctrl + C
```

Für Dienste wie Webserver nutzt man meistens:

```bash
docker run -d ...
```

Dann läuft der Container im Hintergrund.

---

## Container im Hintergrund

Mit `-d` startet man einen Container im Hintergrund.

```bash
docker run -d --name web nginx
```

Prüfen:

```bash
docker ps
```

Logs anzeigen:

```bash
docker logs web
```

Container stoppen:

```bash
docker stop web
```

---

## Container mit Namen

Ein Container kann einen Namen bekommen.

```bash
docker run -d --name web nginx
```

Vorteile:

- Befehle sind leichter lesbar
- man muss keine lange Container-ID merken
- Logs lassen sich einfacher prüfen
- Container kann gezielt gestoppt werden

Beispiele:

```bash
docker logs web
docker stop web
docker rm web
```

Ohne Namen erstellt Docker automatisch einen zufälligen Namen.

---

## Container-ID und Containername

Docker kann Container über ID oder Name ansprechen.

Beispiel mit Name:

```bash
docker stop web
```

Beispiel mit ID:

```bash
docker stop abc123
```

Für Menschen ist der Name besser lesbar.

Deshalb ist `--name` in Lernprojekten und Dokumentationen sehr nützlich.

---

## Container stoppen

Container stoppen:

```bash
docker stop web
```

Mehrere Container stoppen:

```bash
docker stop web db adminer
```

`docker stop` beendet den Container normal.

Wenn ein Container nicht reagiert, gibt es auch:

```bash
docker kill web
```

`docker kill` beendet härter und sollte nicht der Standard sein.

---

## Container starten

Einen gestoppten Container wieder starten:

```bash
docker start web
```

Prüfen:

```bash
docker ps
```

Wichtig:

`docker start` startet einen bestehenden Container neu.

`docker run` erstellt einen neuen Container aus einem Image.

Das ist ein wichtiger Unterschied.

---

## `docker run` vs `docker start`

| Befehl                     | Bedeutung                                          |
| -------------------------- | -------------------------------------------------- |
| `docker run image`         | erstellt neuen Container aus Image und startet ihn |
| `docker start container`   | startet bestehenden gestoppten Container           |
| `docker stop container`    | stoppt laufenden Container                         |
| `docker restart container` | startet bestehenden Container neu                  |

Beispiel:

```bash
docker run -d --name web nginx
docker stop web
docker start web
```

Wenn man danach nochmal ausführt:

```bash
docker run -d --name web nginx
```

kommt ein Fehler, weil der Name `web` bereits existiert.

---

## Container neu starten

Container neu starten:

```bash
docker restart web
```

Das ist praktisch nach einfachen Änderungen oder Problemen.

Prüfen:

```bash
docker ps
docker logs web
```

Bei Docker Compose nutzt man:

```bash
docker compose restart
```

oder für einen Service:

```bash
docker compose restart web
```

---

## Container löschen

Ein gestoppter Container wird gelöscht mit:

```bash
docker rm web
```

Wenn der Container noch läuft:

```bash
docker rm -f web
```

Vorsicht:

```bash
docker rm -f web
```

stoppt und löscht den Container direkt.

Daten im Container können verloren gehen, wenn sie nicht in einem Volume liegen.

Sauberer Ablauf:

```bash
docker stop web
docker rm web
```

---

## Alle gestoppten Container löschen

Gestoppte Container aufräumen:

```bash
docker container prune
```

Docker fragt normalerweise nach Bestätigung.

Vorher prüfen:

```bash
docker ps -a
```

Das ist hilfreich, wenn viele alte Testcontainer existieren.

---

## Container-Status verstehen

`docker ps -a` zeigt Container-Zustände.

Typische Zustände:

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

Wenn ein Container direkt wieder stoppt, sollte man Logs lesen:

```bash
docker logs containername
```

---

## Warum Container sofort stoppen

Manche Container stoppen sofort, weil ihr Hauptprozess beendet ist.

Beispiel:

```bash
docker run ubuntu
```

Der Container startet kurz und beendet sich dann, weil kein dauerhaft laufender Prozess gestartet wurde.

Interaktiv starten:

```bash
docker run -it ubuntu bash
```

Oder automatisch löschen nach Ende:

```bash
docker run --rm -it ubuntu bash
```

Merke:

```text
Ein Container lebt, solange sein Hauptprozess läuft.
```

---

## Interaktive Container

Für Tests kann man interaktive Container starten.

```bash
docker run --rm -it ubuntu bash
```

Bedeutung:

| Option   | Bedeutung                     |
| -------- | ----------------------------- |
| `--rm`   | nach Ende automatisch löschen |
| `-i`     | interaktiv                    |
| `-t`     | Terminal                      |
| `ubuntu` | Image                         |
| `bash`   | Startbefehl                   |

Im Container kann man dann Befehle testen:

```bash
ls
cat /etc/os-release
apt update
```

Container verlassen:

```bash
exit
```

---

## Befehle im laufenden Container ausführen

Mit `docker exec` führt man Befehle in einem laufenden Container aus.

Beispiel:

```bash
docker exec web ls
```

Shell öffnen:

```bash
docker exec -it web bash
```

Falls Bash nicht vorhanden ist:

```bash
docker exec -it web sh
```

Beispiel:

```bash
docker exec -it web sh
ls -la
exit
```

---

## Logs eines Containers

Logs anzeigen:

```bash
docker logs web
```

Logs live verfolgen:

```bash
docker logs -f web
```

Nur letzte Zeilen:

```bash
docker logs --tail 50 web
```

Logs seit einer bestimmten Zeit:

```bash
docker logs --since 1h web
```

Logs sind besonders wichtig bei:

- Container startet nicht
- Anwendung gibt Fehler aus
- Port reagiert nicht
- Datenbank startet nicht
- Webserver liefert Fehler

---

## Container-Details mit inspect

Details anzeigen:

```bash
docker inspect web
```

Das zeigt viele technische Informationen:

- Container-ID
- Image
- Startbefehl
- Status
- IP-Adresse
- Netzwerke
- Port-Mapping
- Mounts
- Umgebungsvariablen
- Volumes

Bei Fehlersuche ist `inspect` sehr nützlich.

Beispiel:

```bash
docker inspect web
```

---

## Prozesse im Container anzeigen

Prozesse im Container anzeigen:

```bash
docker top web
```

Das zeigt, welche Prozesse im Container laufen.

Ressourcenverbrauch anzeigen:

```bash
docker stats web
```

Alle Container live:

```bash
docker stats
```

Das hilft bei Fragen wie:

- verbraucht der Container viel RAM?
- läuft der erwartete Prozess?
- hängt der Dienst?
- nutzt der Container CPU?

---

## Dateien zwischen Host und Container kopieren

Datei aus Container auf Host kopieren:

```bash
docker cp web:/etc/nginx/nginx.conf .
```

Datei vom Host in Container kopieren:

```bash
docker cp index.html web:/usr/share/nginx/html/
```

Wichtig:

Das ist praktisch für Tests.

Für dauerhafte und saubere Projekte sollte man Änderungen eher über Dockerfile, Volumes oder Compose verwalten.

---

## Container-Dateisystem

Jeder Container hat ein eigenes Dateisystem.

Wenn man im Container eine Datei ändert, gilt diese Änderung nur für diesen Container.

Beispiel:

```bash
docker exec -it web sh
echo "test" > /tmp/test.txt
exit
```

Wenn der Container gelöscht wird, ist diese Datei weg.

Deshalb:

```text
Wichtige Daten nicht nur im Container speichern.
```

Für dauerhafte Daten nutzt man Volumes oder Bind Mounts.

---

## Container mit Umgebungsvariablen

Manche Images brauchen Umgebungsvariablen.

Beispiel PostgreSQL:

```bash
docker run -d \
  --name db \
  -e POSTGRES_PASSWORD=example \
  postgres:16
```

`-e` setzt eine Umgebungsvariable.

Mehrere Variablen:

```bash
docker run -d \
  --name db \
  -e POSTGRES_USER=example \
  -e POSTGRES_PASSWORD=example \
  -e POSTGRES_DB=app \
  postgres:16
```

Wichtig:

Echte Passwörter nicht öffentlich dokumentieren oder committen.

---

## Container mit Port-Mapping

Webserver-Beispiel:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

Prüfen:

```bash
docker ps
docker port web
curl http://localhost:8080
```

Wenn der Dienst nicht erreichbar ist, prüfen:

```bash
docker logs web
ss -tulpen
docker inspect web
```

---

## Container automatisch entfernen

Für kurze Tests ist `--rm` praktisch.

Beispiel:

```bash
docker run --rm ubuntu echo "Hallo"
```

Interaktiv:

```bash
docker run --rm -it ubuntu bash
```

Nach dem Beenden wird der Container automatisch gelöscht.

Das hält das System sauber.

Nicht verwenden, wenn man den Container später noch prüfen möchte.

---

## Container mit Restart-Policy

Man kann festlegen, ob Container automatisch neu starten.

Beispiel:

```bash
docker run -d --name web --restart unless-stopped nginx
```

Häufige Policies:

| Policy           | Bedeutung                             |
| ---------------- | ------------------------------------- |
| `no`             | kein automatischer Neustart           |
| `always`         | immer neu starten                     |
| `unless-stopped` | neu starten, außer man stoppt manuell |
| `on-failure`     | nur bei Fehler neu starten            |

Für Testprojekte reicht oft keine Restart-Policy.

Für dauerhaftere Dienste kann `unless-stopped` sinnvoll sein.

---

## Container umbenennen

Container umbenennen:

```bash
docker rename alter-name neuer-name
```

Beispiel:

```bash
docker rename web old-web
```

Prüfen:

```bash
docker ps -a
```

Namen sollten klar und verständlich sein.

Gute Namen:

```text
web
db
adminer
frontend
backend
```

---

## Container pausieren

Container pausieren:

```bash
docker pause web
```

Fortsetzen:

```bash
docker unpause web
```

Das wird im Alltag weniger häufig gebraucht als `stop`, `start` oder `restart`.

Prüfen:

```bash
docker ps -a
```

---

## Images bauen

Ein eigenes Image baut man aus einem Dockerfile.

Beispiel:

```bash
docker build -t my-nginx .
```

Bedeutung:

| Teil           | Bedeutung                          |
| -------------- | ---------------------------------- |
| `docker build` | Image bauen                        |
| `-t my-nginx`  | Image-Name setzen                  |
| `.`            | aktueller Ordner als Build-Kontext |

Container starten:

```bash
docker run -d --name web -p 8080:80 my-nginx
```

Eigene Images sind wichtig, wenn man eigene Anwendungen oder Konfigurationen in Container packen möchte.

---

## Images taggen

Ein Image kann einen Tag bekommen.

```bash
docker build -t myapp:1.0 .
```

Weiteren Tag setzen:

```bash
docker tag myapp:1.0 myapp:latest
```

Tags helfen, Versionen zu unterscheiden.

Beispiele:

```text
myapp:1.0
myapp:1.1
myapp:latest
```

---

## Images und Container aufräumen

Überblick:

```bash
docker ps -a
docker images
docker system df
```

Gestoppte Container löschen:

```bash
docker container prune
```

Ungenutzte Images löschen:

```bash
docker image prune
```

Stärker aufräumen:

```bash
docker system prune
```

Vorsicht:

```bash
docker system prune -a
```

kann viele Images löschen.

Vorher immer prüfen.

---

## Typischer Ablauf: Container testen

Ein sauberer Ablauf für einen Testcontainer:

```bash
docker pull nginx
docker run -d --name web -p 8080:80 nginx
docker ps
docker logs web
curl http://localhost:8080
docker stop web
docker rm web
```

Das ist ein guter Basisablauf für viele Docker-Tests.

---

## Typischer Ablauf: Container debuggen

Wenn ein Container nicht funktioniert:

```bash
docker ps -a
docker logs containername
docker inspect containername
docker port containername
docker top containername
```

Wenn der Container läuft:

```bash
docker exec -it containername sh
```

oder:

```bash
docker exec -it containername bash
```

Bei Port-Problemen zusätzlich:

```bash
ss -tulpen
curl http://localhost:port
```

---

## Häufige Fehler

| Fehler                                      | Problem                              |
| ------------------------------------------- | ------------------------------------ |
| `docker run` statt `docker start` verwenden | es wird ein neuer Container erstellt |
| Image und Container verwechseln             | falscher Befehl wird genutzt         |
| Containername bereits vergeben              | alter Container existiert noch       |
| Port-Mapping vergessen                      | Dienst ist nicht erreichbar          |
| falscher Host-Port                          | Browser zeigt nichts                 |
| Logs nicht prüfen                           | Ursache bleibt unbekannt             |
| Container gelöscht, Daten weg               | keine Volumes genutzt                |
| `latest` blind nutzen                       | Version kann sich ändern             |
| Container manuell verändern                 | Änderung ist nicht reproduzierbar    |
| zu viele alte Container behalten            | System wird unübersichtlich          |

---

## Praktische Beispiele

### Beispiel 1: nginx starten

```bash
docker run -d --name web -p 8080:80 nginx
docker ps
curl http://localhost:8080
```

Stoppen und löschen:

```bash
docker stop web
docker rm web
```

---

### Beispiel 2: Ubuntu interaktiv starten

```bash
docker run --rm -it ubuntu bash
```

Im Container:

```bash
cat /etc/os-release
exit
```

---

### Beispiel 3: Containerlogs prüfen

```bash
docker logs web
docker logs -f web
docker logs --tail 50 web
```

---

### Beispiel 4: Fehler prüfen

```bash
docker ps -a
docker logs web
docker inspect web
docker port web
```

---

## Nützliche Befehle

| Befehl                         | Bedeutung                             |
| ------------------------------ | ------------------------------------- |
| `docker images`                | Images anzeigen                       |
| `docker image ls`              | Images anzeigen                       |
| `docker pull image`            | Image herunterladen                   |
| `docker rmi image`             | Image löschen                         |
| `docker history image`         | Image-Schichten anzeigen              |
| `docker build -t name .`       | eigenes Image bauen                   |
| `docker tag image neuer-tag`   | Image taggen                          |
| `docker ps`                    | laufende Container anzeigen           |
| `docker ps -a`                 | alle Container anzeigen               |
| `docker run image`             | neuen Container erstellen und starten |
| `docker run -d image`          | Container im Hintergrund starten      |
| `docker run --name name image` | Container mit Name starten            |
| `docker start container`       | gestoppten Container starten          |
| `docker stop container`        | Container stoppen                     |
| `docker restart container`     | Container neu starten                 |
| `docker rm container`          | Container löschen                     |
| `docker rm -f container`       | laufenden Container löschen           |
| `docker logs container`        | Logs anzeigen                         |
| `docker exec -it container sh` | Shell im Container öffnen             |
| `docker inspect container`     | Details anzeigen                      |
| `docker top container`         | Prozesse im Container anzeigen        |
| `docker stats`                 | Ressourcenverbrauch anzeigen          |
| `docker cp`                    | Dateien kopieren                      |
| `docker container prune`       | gestoppte Container löschen           |
| `docker image prune`           | ungenutzte Images löschen             |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist der sichere Umgang mit Images und Containern wichtig.

In der Praxis bedeutet das:

- Dienste als Container starten
- Containerstatus prüfen
- Logs auswerten
- Container stoppen und neu starten
- Images versioniert nutzen
- Port-Mappings verstehen
- Datenverlust durch falsches Löschen vermeiden
- Testumgebungen sauber aufbauen
- Docker-Projekte dokumentieren
- Fehler systematisch eingrenzen

Ein guter FISI versteht den Unterschied zwischen Image und Container und weiß, dass ein Container nicht automatisch dauerhafte Daten garantiert.

---

## Kurze Zusammenfassung

Ein Image ist die Vorlage für Container.

Ein Container ist eine laufende oder gestoppte Instanz eines Images.

Wichtige Befehle sind `docker images`, `docker pull`, `docker rmi`, `docker ps`, `docker ps -a`, `docker run`, `docker start`, `docker stop`, `docker restart`, `docker rm`, `docker logs`, `docker exec`, `docker inspect` und `docker container prune`.

Für FISI ist dieses Kapitel wichtig, weil Images und Container die Grundlage fast jeder Docker-Arbeit bilden.
