# 1. Docker-Grundlagen

In diesem Kapitel geht es um die wichtigsten Grundlagen von Docker.

Docker ist eine Plattform, mit der Anwendungen in Containern ausgeführt werden können. Ein Container ist eine isolierte Umgebung, in der ein Dienst oder eine Anwendung läuft. Dadurch kann man Software einfacher starten, testen, dokumentieren und auf verschiedenen Systemen ähnlich ausführen.

Für Fachinformatiker für Systemintegration ist Docker wichtig, weil Container in vielen Bereichen vorkommen: Testumgebungen, Datenbanken, Webserver, Admin-Tools, lokale Labore, Entwicklungssysteme und einfache Deployments.

---

## Kurz erklärt

Docker hilft dabei, Anwendungen kontrolliert in Containern auszuführen.

Die wichtigsten Begriffe sind:

| Begriff        | Bedeutung                                          |
| -------------- | -------------------------------------------------- |
| Image          | Vorlage für einen Container                        |
| Container      | laufende oder gestoppte Instanz eines Images       |
| Dockerfile     | Bauanleitung für ein eigenes Image                 |
| Volume         | dauerhafter Speicher für Containerdaten            |
| Network        | Netzwerk für Containerkommunikation                |
| Port Mapping   | Verbindung zwischen Host-Port und Container-Port   |
| Docker Compose | Verwaltung mehrerer Container über eine YAML-Datei |

Kurz gesagt:

```text
Image = Vorlage
Container = gestartete Instanz
Volume = dauerhafte Daten
Network = Verbindung
Compose = mehrere Container gemeinsam verwalten
```

---

## Warum Docker existiert

Ein typisches Problem in der IT ist:

```text
Auf meinem Rechner funktioniert es, auf einem anderen Rechner nicht.
```

Das kann viele Gründe haben:

- unterschiedliche Betriebssysteme
- unterschiedliche Programmversionen
- fehlende Abhängigkeiten
- andere Konfigurationsdateien
- andere Ports
- andere Datenbankversionen
- andere Benutzerrechte
- fehlende Pakete
- unterschiedliche Laufzeitumgebungen

Docker versucht dieses Problem zu reduzieren.

Die Anwendung läuft nicht direkt unkontrolliert auf dem Host-System, sondern in einer definierten Container-Umgebung.

Dadurch kann ein Projekt leichter nachgebaut, getestet und dokumentiert werden.

---

## Was ist ein Container?

Ein Container ist eine isolierte Umgebung für einen Prozess oder Dienst.

Ein Container enthält zum Beispiel:

- Anwendung
- benötigte Bibliotheken
- Konfiguration
- Laufzeitumgebung
- Dateisystembereich
- Netzwerkzugriff
- Startbefehl

Ein Container ist aber keine vollständige virtuelle Maschine.

Er nutzt den Kernel des Host-Systems mit.

Das macht Container meistens schneller und leichter als virtuelle Maschinen.

---

## Container im Alltag erklärt

Ein Container kann zum Beispiel ein einzelner Dienst sein:

```text
nginx Webserver
PostgreSQL Datenbank
Adminer Datenbank-GUI
Redis Cache
Python-App
Node.js-App
```

Jeder Dienst läuft in einem eigenen Container.

Beispiel:

```text
Container 1: Webserver
Container 2: Datenbank
Container 3: Admin-Tool
```

Diese Container können über Docker-Netzwerke miteinander kommunizieren.

---

## Docker vs virtuelle Maschine

Docker-Container und virtuelle Maschinen werden oft verwechselt.

| Bereich             | Docker-Container                      | Virtuelle Maschine                        |
| ------------------- | ------------------------------------- | ----------------------------------------- |
| Betriebssystem      | nutzt Host-Kernel mit                 | eigenes Gastbetriebssystem                |
| Startzeit           | meist sehr schnell                    | eher langsamer                            |
| Ressourcenverbrauch | geringer                              | höher                                     |
| Isolation           | prozessbasiert                        | stärker getrennt                          |
| Verwaltung          | Images, Container, Volumes, Netzwerke | VM-Images, Hypervisor, virtuelle Hardware |
| Nutzung             | Dienste, Apps, Testumgebungen         | komplette Systeme, Server-Labs, OS-Tests  |

Docker ersetzt virtuelle Maschinen nicht vollständig.

Beide Werkzeuge haben ihren Platz.

Für einzelne Dienste und Testumgebungen ist Docker sehr praktisch. Für komplette Betriebssysteme, Windows/Linux-Labore oder Netzwerkübungen sind virtuelle Maschinen oft passender.

---

## Host-System

Das Host-System ist der Rechner, auf dem Docker läuft.

Beispiel:

```text
Ubuntu Laptop
Linux Server
Windows mit Docker Desktop
VM mit Docker
```

Container laufen auf diesem Host.

Sie sind vom Host getrennt, nutzen aber Ressourcen des Hosts:

- CPU
- RAM
- Netzwerk
- Speicherplatz
- Kernel-Funktionen

Deshalb sollte man auch beim Arbeiten mit Docker das Host-System im Blick behalten.

Wichtige Befehle:

```bash
docker stats
df -h
free -h
docker system df
```

---

## Docker Engine

Die Docker Engine ist der zentrale Docker-Dienst auf dem System.

Sie verwaltet:

- Images
- Container
- Volumes
- Netzwerke
- Builds
- Logs
- Docker API

Auf Linux läuft Docker meistens als Dienst.

Prüfen:

```bash
systemctl status docker
```

Starten:

```bash
sudo systemctl start docker
```

Neustarten:

```bash
sudo systemctl restart docker
```

Autostart aktivieren:

```bash
sudo systemctl enable docker
```

---

## Docker Client und Docker Daemon

Docker besteht grob aus Client und Daemon.

| Teil          | Bedeutung                                    |
| ------------- | -------------------------------------------- |
| Docker Client | Befehl im Terminal, zum Beispiel `docker ps` |
| Docker Daemon | Hintergrunddienst, der Container verwaltet   |
| Docker Engine | gesamte Docker-Laufzeitumgebung              |

Wenn man eingibt:

```bash
docker ps
```

spricht der Docker Client mit dem Docker Daemon.

Der Daemon liefert dann Informationen über laufende Container zurück.

Wenn Docker nicht läuft, sieht man oft Fehlermeldungen wie:

```text
Cannot connect to the Docker daemon
```

Dann sollte man den Docker-Dienst prüfen.

---

## Docker-Version prüfen

Docker-Version anzeigen:

```bash
docker --version
```

Mehr Details:

```bash
docker version
```

Systeminformationen:

```bash
docker info
```

Diese Befehle helfen, wenn man prüfen möchte:

- ist Docker installiert?
- läuft Docker?
- welche Version ist installiert?
- wie viele Container gibt es?
- wie viele Images gibt es?
- welche Storage- und Netzwerkoptionen werden genutzt?

---

## Image

Ein Image ist eine Vorlage für Container.

Ein Image enthält alles, was für den Start eines Containers vorbereitet ist.

Beispiele für Images:

```text
nginx
ubuntu
postgres
mysql
python
node
adminer
```

Images anzeigen:

```bash
docker images
```

Image herunterladen:

```bash
docker pull nginx
```

Ein Image ist normalerweise unveränderlich. Wenn man daraus einen Container startet, entsteht eine laufende oder gestoppte Instanz.

---

## Container

Ein Container ist eine Instanz eines Images.

Beispiel:

```bash
docker run -d --name web nginx
```

Hier wird aus dem Image `nginx` ein Container mit dem Namen `web` gestartet.

Laufende Container anzeigen:

```bash
docker ps
```

Alle Container anzeigen:

```bash
docker ps -a
```

Container stoppen:

```bash
docker stop web
```

Container starten:

```bash
docker start web
```

Container löschen:

```bash
docker rm web
```

---

## Image und Container unterscheiden

Ein häufiger Anfängerfehler ist die Verwechslung von Image und Container.

| Frage                                  | Image                                | Container                         |
| -------------------------------------- | ------------------------------------ | --------------------------------- |
| Was ist es?                            | Vorlage                              | gestartete oder gestoppte Instanz |
| Kann es laufen?                        | nein                                 | ja                                |
| Wird es mit `docker pull` geladen?     | ja                                   | nein                              |
| Wird es mit `docker run` gestartet?    | aus dem Image entsteht ein Container | ja                                |
| Wird es mit `docker images` angezeigt? | ja                                   | nein                              |
| Wird es mit `docker ps` angezeigt?     | nein                                 | ja                                |

Beispiel:

```bash
docker pull nginx
docker run -d --name web nginx
```

`nginx` ist das Image.  
`web` ist der Container.

---

## Docker Hub und Registries

Images liegen oft in einer Registry.

Die bekannteste öffentliche Registry ist Docker Hub.

Beispiele:

```bash
docker pull nginx
docker pull postgres
docker pull ubuntu
```

Eine Registry ist ein Speicherort für Images.

Es gibt auch private Registries in Firmen oder Organisationen.

Wichtig:

Man sollte Images nicht blind nutzen. Besonders bei produktiven Systemen sollte man prüfen:

- Woher kommt das Image?
- Wird es gepflegt?
- Ist es offiziell?
- Welche Version wird genutzt?
- Gibt es Sicherheitsupdates?

---

## Tags bei Images

Images haben oft Tags.

Beispiel:

```text
nginx:latest
postgres:16
ubuntu:24.04
python:3.12
```

Der Teil nach `:` ist der Tag.

Beispiele:

```bash
docker pull nginx:latest
docker pull postgres:16
docker pull ubuntu:24.04
```

Ein Tag beschreibt meistens eine Version oder Variante.

Wichtig:

`latest` bedeutet nicht immer automatisch „beste“ oder „stabilste“ Version. Es bedeutet nur, dass dieses Tag vom Image-Anbieter so gesetzt wurde.

Für klare Projekte ist eine feste Version oft besser.

Beispiel:

```text
postgres:16
```

statt:

```text
postgres:latest
```

---

## Container starten mit docker run

Ein einfacher Container:

```bash
docker run nginx
```

Dieser Container läuft im Vordergrund.

Im Hintergrund starten:

```bash
docker run -d nginx
```

Mit Namen starten:

```bash
docker run -d --name web nginx
```

Mit Port-Mapping:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bedeutung:

| Teil         | Bedeutung                            |
| ------------ | ------------------------------------ |
| `docker run` | neuen Container starten              |
| `-d`         | detached, also im Hintergrund        |
| `--name web` | Containername                        |
| `-p 8080:80` | Host-Port 8080 auf Container-Port 80 |
| `nginx`      | Image                                |

---

## Port Mapping

Container haben eigene interne Ports.

Damit ein Dienst vom Host erreichbar wird, muss man den Port veröffentlichen.

Beispiel:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

Im Browser:

```text
http://localhost:8080
```

Prüfen:

```bash
docker ps
docker port web
```

Typischer Fehler:

Man startet einen Webserver im Container, aber vergisst `-p`.

Dann läuft der Dienst im Container, ist aber vom Host nicht direkt über den gewünschten Port erreichbar.

---

## Logs

Container schreiben Logs.

Logs anzeigen:

```bash
docker logs web
```

Logs live verfolgen:

```bash
docker logs -f web
```

Letzte Zeilen anzeigen:

```bash
docker logs --tail 50 web
```

Logs sind sehr wichtig für Fehlersuche.

Wenn ein Container startet und sofort wieder stoppt, ist der erste sinnvolle Befehl meistens:

```bash
docker logs containername
```

---

## In Container hinein gehen

Man kann Befehle in einem laufenden Container ausführen.

Beispiel:

```bash
docker exec web ls
```

Interaktive Shell öffnen:

```bash
docker exec -it web bash
```

Falls Bash nicht vorhanden ist:

```bash
docker exec -it web sh
```

Viele kleine Images enthalten kein Bash.

Dann nutzt man `sh`.

Wichtig:

Änderungen im Container sind oft nicht dauerhaft sinnvoll. Dauerhafte Änderungen sollten über Dockerfile, Volumes oder Konfigurationsdateien gemacht werden.

---

## Container-Dateisystem

Ein Container hat ein eigenes Dateisystem.

Wenn man im Container Dateien ändert, gelten diese Änderungen nur für diesen Container.

Wenn der Container gelöscht wird, können diese Änderungen verloren gehen.

Deshalb sollte man wichtige Daten nicht einfach nur im Container speichern.

Für dauerhafte Daten nutzt man:

```text
Volumes
Bind Mounts
Datenbank-Volumes
Konfigurationsdateien
```

---

## Volumes

Volumes speichern Daten dauerhaft.

Beispiel:

```bash
docker volume create db_data
```

Volumes anzeigen:

```bash
docker volume ls
```

Volume in Container nutzen:

```bash
docker run -d --name db -v db_data:/var/lib/postgresql/data postgres:16
```

Das Volume `db_data` bleibt erhalten, auch wenn der Container gelöscht wird.

Das ist besonders wichtig bei Datenbanken.

---

## Bind Mounts

Ein Bind Mount verbindet einen Ordner vom Host mit einem Ordner im Container.

Beispiel:

```bash
docker run -d --name web -p 8080:80 -v "$(pwd)":/usr/share/nginx/html nginx
```

Bedeutung:

| Teil                    | Bedeutung                     |
| ----------------------- | ----------------------------- |
| `$(pwd)`                | aktueller Ordner auf dem Host |
| `/usr/share/nginx/html` | Zielordner im Container       |
| `-v`                    | Mount einbinden               |

Bind Mounts sind praktisch bei Entwicklung und Tests.

Wenn man eine Datei auf dem Host ändert, sieht der Container diese Änderung direkt.

---

## Docker-Netzwerke

Container können über Docker-Netzwerke miteinander kommunizieren.

Netzwerke anzeigen:

```bash
docker network ls
```

Netzwerk erstellen:

```bash
docker network create appnet
```

Netzwerk prüfen:

```bash
docker network inspect appnet
```

Container können in ein Netzwerk gestartet werden:

```bash
docker run -d --name web --network appnet nginx
```

In Docker Compose wird meistens automatisch ein gemeinsames Netzwerk erstellt.

---

## Docker Compose

Docker Compose verwaltet mehrere Container über eine YAML-Datei.

Die Datei heißt meistens:

```text
docker-compose.yml
```

oder:

```text
compose.yml
```

Starten:

```bash
docker compose up -d
```

Stoppen:

```bash
docker compose down
```

Logs anzeigen:

```bash
docker compose logs
```

Status anzeigen:

```bash
docker compose ps
```

Docker Compose ist sehr praktisch für Projekte mit mehreren Diensten.

Beispiel:

```text
Datenbank + Adminer
Web-App + Datenbank
API + Datenbank + Cache
```

---

## Dockerfile

Ein Dockerfile ist eine Bauanleitung für ein eigenes Image.

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

Ein Dockerfile macht ein Projekt reproduzierbarer, weil die Umgebung beschrieben wird.

---

## Docker und YAML

Docker Compose nutzt YAML.

YAML ist eine Konfigurationssprache.

Beispiel:

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

Wichtig bei YAML:

- Einrückung ist wichtig
- Leerzeichen statt Tabs nutzen
- Listen beginnen mit `-`
- Werte werden oft als `key: value` geschrieben

Viele Compose-Fehler entstehen durch falsche Einrückung.

Prüfen:

```bash
docker compose config
```

---

## Container-Lebenszyklus

Ein Container kann verschiedene Zustände haben.

| Zustand    | Bedeutung                      |
| ---------- | ------------------------------ |
| created    | erstellt, aber nicht gestartet |
| running    | läuft                          |
| paused     | pausiert                       |
| exited     | beendet                        |
| restarting | startet neu                    |
| dead       | fehlerhafter Zustand           |

Alle Container anzeigen:

```bash
docker ps -a
```

Nur laufende Container:

```bash
docker ps
```

Container starten:

```bash
docker start name
```

Container stoppen:

```bash
docker stop name
```

Container löschen:

```bash
docker rm name
```

---

## Docker inspect

Mit `docker inspect` sieht man technische Details.

Beispiel:

```bash
docker inspect web
```

Das zeigt viele Informationen:

- Container-ID
- Image
- Netzwerk
- IP-Adresse
- Mounts
- Volumes
- Ports
- Umgebungsvariablen
- Startbefehl
- Status

`inspect` ist sehr hilfreich, wenn man genau prüfen möchte, wie ein Container konfiguriert ist.

---

## Ressourcenverbrauch

Container verbrauchen Ressourcen des Hosts.

Live anzeigen:

```bash
docker stats
```

Docker-Speicherverbrauch anzeigen:

```bash
docker system df
```

Systemspeicher prüfen:

```bash
df -h
free -h
```

Wichtig:

Viele alte Images, Container und Volumes können Speicherplatz belegen.

Deshalb sollte man Docker regelmäßig kontrollieren.

---

## Aufräumen

Gestoppte Container löschen:

```bash
docker container prune
```

Ungenutzte Images löschen:

```bash
docker image prune
```

Ungenutzte Volumes löschen:

```bash
docker volume prune
```

Mehrere Dinge aufräumen:

```bash
docker system prune
```

Vorsicht:

```bash
docker system prune -a
docker volume prune
docker compose down -v
```

Diese Befehle können wichtige Daten entfernen.

Vorher prüfen:

```bash
docker ps -a
docker images
docker volume ls
docker system df
```

---

## Docker und Sicherheit

Docker ist kein Ersatz für Sicherheit.

Wichtige Regeln:

- keine Passwörter in Dockerfiles schreiben
- keine privaten SSH-Schlüssel ins Image kopieren
- `.env` nicht öffentlich committen
- nur nötige Ports veröffentlichen
- Images aus vertrauenswürdigen Quellen nutzen
- feste Versionen statt immer `latest` nutzen
- Container nicht unnötig privilegiert starten
- Volumes bewusst verwenden
- Logs regelmäßig prüfen
- Container und Images aktualisieren

Container isolieren Anwendungen, aber sie machen ein System nicht automatisch sicher.

---

## Docker in Git-Projekten

Docker-Projekte werden oft mit Git verwaltet.

Sinnvolle Dateien:

```text
README.md
Dockerfile
docker-compose.yml
.env.example
scripts/
configs/
```

Nicht ins öffentliche Repository:

```text
.env
private/
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

Eine gute README sollte erklären:

- was gestartet wird
- welche Ports genutzt werden
- welche Befehle nötig sind
- wie man Logs prüft
- wie man alles wieder stoppt
- welche Daten dauerhaft gespeichert werden

---

## Typische Fehler am Anfang

| Fehler                                | Problem                               |
| ------------------------------------- | ------------------------------------- |
| Image und Container verwechseln       | falscher Befehl wird genutzt          |
| Port-Mapping vergessen                | Dienst ist nicht erreichbar           |
| Container gelöscht, Daten weg         | keine Volumes genutzt                 |
| Logs nicht prüfen                     | Fehlerursache bleibt unbekannt        |
| `latest` immer blind nutzen           | Versionen können sich ändern          |
| `.env` committen                      | Zugangsdaten können öffentlich werden |
| Compose-Datei falsch eingerückt       | Projekt startet nicht                 |
| `docker compose down -v` blind nutzen | Volumes werden gelöscht               |
| im Container manuell ändern           | Änderung ist nicht reproduzierbar     |
| alte Container/Images nie aufräumen   | System wird unübersichtlich           |

---

## Praktische Beispiele

### Beispiel 1: nginx starten

```bash
docker run -d --name web -p 8080:80 nginx
docker ps
docker logs web
docker port web
```

Im Browser:

```text
http://localhost:8080
```

Container entfernen:

```bash
docker stop web
docker rm web
```

---

### Beispiel 2: Ubuntu-Container interaktiv starten

```bash
docker run --rm -it ubuntu bash
```

Falls Bash nicht verfügbar wäre:

```bash
docker run --rm -it ubuntu sh
```

`--rm` sorgt dafür, dass der Container nach dem Beenden automatisch gelöscht wird.

---

### Beispiel 3: Docker-System prüfen

```bash
docker ps
docker ps -a
docker images
docker volume ls
docker network ls
docker system df
```

Damit bekommt man einen guten Überblick über Docker-Ressourcen.

---

### Beispiel 4: Logs lesen

```bash
docker logs web
docker logs -f web
docker logs --tail 50 web
```

Logs sind einer der wichtigsten Startpunkte bei Docker-Fehlersuche.

---

## Nützliche Befehle

| Befehl                         | Bedeutung                           |
| ------------------------------ | ----------------------------------- |
| `docker --version`             | Docker-Version anzeigen             |
| `docker info`                  | Docker-Systeminformationen anzeigen |
| `systemctl status docker`      | Docker-Dienststatus prüfen          |
| `docker ps`                    | laufende Container anzeigen         |
| `docker ps -a`                 | alle Container anzeigen             |
| `docker images`                | Images anzeigen                     |
| `docker pull image`            | Image herunterladen                 |
| `docker run image`             | Container starten                   |
| `docker stop container`        | Container stoppen                   |
| `docker start container`       | Container starten                   |
| `docker restart container`     | Container neu starten               |
| `docker rm container`          | Container löschen                   |
| `docker rmi image`             | Image löschen                       |
| `docker logs container`        | Logs anzeigen                       |
| `docker exec -it container sh` | Shell im Container öffnen           |
| `docker inspect container`     | Details anzeigen                    |
| `docker stats`                 | Ressourcenverbrauch anzeigen        |
| `docker volume ls`             | Volumes anzeigen                    |
| `docker network ls`            | Netzwerke anzeigen                  |
| `docker system df`             | Docker-Speichernutzung anzeigen     |
| `docker compose up -d`         | Compose-Projekt starten             |
| `docker compose down`          | Compose-Projekt stoppen             |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Docker-Grundlagen sehr nützlich.

In der Praxis bedeutet das:

- Dienste schnell testen
- Datenbanken lokal starten
- Webserver ausprobieren
- Admin-Tools bereitstellen
- Logs analysieren
- Ports prüfen
- Volumes für Daten verstehen
- Testumgebungen dokumentieren
- Projekte reproduzierbar machen
- Grundlagen für DevOps verstehen

Docker verbindet viele Themen aus der Systemintegration: Linux, Dienste, Netzwerk, Sicherheit, Git, Dokumentation und Automatisierung.

---

## Kurze Zusammenfassung

Docker führt Anwendungen in Containern aus.

Ein Image ist die Vorlage. Ein Container ist eine laufende oder gestoppte Instanz. Volumes speichern Daten dauerhaft. Netzwerke verbinden Container. Docker Compose verwaltet mehrere Container gemeinsam.

Wichtige Befehle sind `docker ps`, `docker images`, `docker run`, `docker stop`, `docker rm`, `docker logs`, `docker exec`, `docker inspect`, `docker volume ls`, `docker network ls`, `docker compose up -d` und `docker compose down`.

Für FISI ist Docker wichtig, weil Container für Testumgebungen, Datenbanken, Webdienste, lokale Labs und DevOps-Grundlagen häufig genutzt werden.
