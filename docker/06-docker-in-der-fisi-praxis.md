# 6. Docker in der FISI-Praxis

In diesem Kapitel geht es darum, wie Docker in der Praxis eines Fachinformatikers für Systemintegration genutzt werden kann.

Docker ist nicht nur ein Werkzeug für Entwickler. Auch in der Systemintegration ist Docker sehr nützlich, weil damit Dienste, Testumgebungen, Datenbanken, Webserver, Admin-Tools und kleine Laborumgebungen schnell bereitgestellt werden können.

Für FISI ist besonders wichtig, Docker nicht nur als Befehlssammlung zu sehen, sondern als praktisches Werkzeug für Administration, Dokumentation, Testumgebungen und Fehlersuche.

---

## Kurz erklärt

Docker kann im FISI-Alltag für viele praktische Aufgaben genutzt werden.

Typische Einsatzbereiche:

| Bereich           | Beispiel                             |
| ----------------- | ------------------------------------ |
| Testumgebungen    | Webserver, Datenbank, Admin-Tool     |
| Datenbanken       | PostgreSQL, MySQL, MariaDB           |
| Webdienste        | nginx, Apache, kleine Web-Apps       |
| Admin-Tools       | Adminer, Portainer, Monitoring-Tools |
| Entwicklung       | lokale Umgebung für Projekte         |
| Dokumentation     | reproduzierbare Projektumgebungen    |
| Home-Lab          | kleine Dienste zum Lernen            |
| DevOps-Grundlagen | Images, Compose, Logs, Deployments   |

Docker verbindet viele FISI-Themen:

```text
Linux
Netzwerk
Dienste
Ports
Logs
Sicherheit
Datenbanken
Git
Dokumentation
Automatisierung
```

---

## Warum Docker für FISI wichtig ist

Fachinformatiker für Systemintegration arbeiten viel mit Systemen, Diensten und Infrastruktur.

Docker hilft dabei, solche Dienste schnell und kontrolliert bereitzustellen.

Beispiele:

- einen Webserver testen
- eine Datenbank für ein Projekt starten
- ein Admin-Tool bereitstellen
- ein kleines Lab mit mehreren Diensten bauen
- eine Anwendung unabhängig vom Host-System starten
- Logs und Fehler analysieren
- Ports und Netzwerke prüfen
- Konfigurationsdateien dokumentieren
- eine Umgebung reproduzierbar machen

Docker ist deshalb ein guter Einstieg in moderne Systemadministration und DevOps-Grundlagen.

---

## Docker als Testumgebung

Docker eignet sich sehr gut für Testumgebungen.

Beispiel:

```text
Ich möchte PostgreSQL testen, aber nicht direkt auf meinem System installieren.
```

Mit Docker:

```bash
docker run -d \
  --name test-db \
  -e POSTGRES_PASSWORD=example \
  postgres:16
```

Vorteile:

- schnell gestartet
- leicht zu löschen
- Host-System bleibt sauberer
- verschiedene Versionen testbar
- gut dokumentierbar
- ideal für Lernprojekte

Stoppen und löschen:

```bash
docker stop test-db
docker rm test-db
```

---

## Docker für Datenbanken

Datenbanken sind ein häufiger Docker-Einsatzbereich.

Beispiele:

```text
PostgreSQL
MySQL
MariaDB
MongoDB
Redis
```

Für Lern- und Testprojekte kann man Datenbanken schnell starten.

Wichtig ist dabei:

- Datenbankdaten in Volumes speichern
- Passwörter nicht öffentlich committen
- Ports bewusst veröffentlichen
- Logs prüfen
- Versionen festlegen
- README sauber schreiben

Beispiel PostgreSQL mit Volume:

```bash
docker volume create postgres_data

docker run -d \
  --name postgres-db \
  -e POSTGRES_PASSWORD=example \
  -v postgres_data:/var/lib/postgresql/data \
  postgres:16
```

---

## Docker für Webserver

Webserver lassen sich mit Docker sehr einfach testen.

Beispiel nginx:

```bash
docker run -d --name web -p 8080:80 nginx
```

Prüfen:

```bash
docker ps
docker logs web
curl http://localhost:8080
```

Im Browser:

```text
http://localhost:8080
```

Das ist nützlich für:

- HTML-Testseiten
- Reverse-Proxy-Grundlagen
- Port-Mapping verstehen
- Logs prüfen
- einfache Webdienste testen
- Netzwerkdiagnose üben

---

## Docker für Admin-Tools

Viele Admin-Tools können als Container gestartet werden.

Beispiele:

```text
Adminer
Portainer
Grafana
Prometheus
Uptime Kuma
phpMyAdmin
```

Solche Tools sind praktisch für Lernumgebungen und Home-Labs.

Beispiel Adminer:

```bash
docker run -d --name adminer -p 8080:8080 adminer
```

Adminer öffnen:

```text
http://localhost:8080
```

Adminer ist besonders praktisch, wenn man Datenbanken testen oder verwalten möchte.

---

## Docker Compose in der Praxis

In echten kleinen Projekten nutzt man oft nicht nur einen Container.

Beispiel:

```text
Datenbank + Admin-Oberfläche
```

Mit Docker Compose:

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
docker compose logs
```

Stoppen:

```bash
docker compose down
```

---

## Docker in Projekt-Repositories

Docker-Projekte sollten sauber dokumentiert werden.

Typische Dateien:

```text
projekt/
├── README.md
├── Dockerfile
├── docker-compose.yml
├── .env.example
├── .gitignore
├── scripts/
└── configs/
```

Wichtig:

Die README sollte erklären:

- was das Projekt macht
- welche Container gestartet werden
- welche Ports genutzt werden
- welche Volumes verwendet werden
- wie man das Projekt startet
- wie man Logs prüft
- wie man das Projekt stoppt
- welche Zugangsdaten nur Beispiele sind
- welche Dateien nicht ins Repository gehören

Ein Docker-Projekt ohne README ist für andere schwer nachvollziehbar.

---

## Docker und GitHub-Portfolio

Docker-Projekte sind gut für ein IT-Portfolio, wenn sie realistisch dokumentiert sind.

Gute Portfolio-Projekte können sein:

- PostgreSQL mit Adminer
- nginx-Testserver
- kleines Monitoring-Lab
- Python-App im Container
- Datenbankprojekt mit Compose
- Linux-Service-Testumgebung
- Netzwerk-Testumgebung mit mehreren Containern
- Docker-Dokumentation mit Troubleshooting

Wichtig ist, dass das Projekt nicht künstlich wirkt.

Es sollte zeigen:

```text
Ich verstehe, was ich gebaut habe.
Ich kann es starten.
Ich kann Fehler prüfen.
Ich kann es dokumentieren.
Ich weiß, wo Risiken sind.
```

---

## Docker und Linux-Wissen

Docker hängt stark mit Linux zusammen.

Wichtige Linux-Themen bei Docker:

| Linux-Thema     | Docker-Bezug                        |
| --------------- | ----------------------------------- |
| Prozesse        | Container laufen als Prozesse       |
| Dateisystem     | Container haben eigenes Dateisystem |
| Rechte          | Dateien, Mounts und Benutzerrechte  |
| Netzwerk        | Ports, Interfaces, Bridge-Netzwerke |
| Logs            | Container-Logs und Systemlogs       |
| Dienste         | Docker läuft als Dienst             |
| Speicherplatz   | Images, Container, Volumes          |
| Shell           | `docker exec -it container sh`      |
| Paketverwaltung | Images enthalten eigene Pakete      |
| Sicherheit      | Benutzer, Rechte, Isolation         |

Wer Linux gut versteht, versteht Docker deutlich besser.

---

## Docker und Netzwerk

Docker nutzt eigene Netzwerke.

Wichtige Punkte:

- Container haben interne IP-Adressen
- Container können über Docker-Netzwerke kommunizieren
- Compose-Services erreichen sich über Servicenamen
- Host-Port und Container-Port sind nicht dasselbe
- `localhost` bedeutet je nach Ort etwas anderes
- Port-Konflikte entstehen auf dem Host
- Datenbankports müssen nicht immer nach außen geöffnet werden

Beispiel Port-Mapping:

```bash
docker run -d --name web -p 8080:80 nginx
```

Bedeutung:

```text
Host-Port 8080 -> Container-Port 80
```

Beispiel Compose-Service:

```text
adminer erreicht postgres über db
```

Nicht über:

```text
localhost
```

---

## Docker und Sicherheit

Docker ist praktisch, aber nicht automatisch sicher.

Wichtige Sicherheitsregeln:

- keine echten Passwörter ins Repository
- keine privaten SSH-Schlüssel ins Image kopieren
- `.env` nicht öffentlich committen
- Images aus vertrauenswürdigen Quellen nutzen
- feste Versionen statt blind `latest` verwenden
- nur nötige Ports veröffentlichen
- Container nicht unnötig privilegiert starten
- Volumes bewusst nutzen
- Logs nicht mit sensiblen Daten veröffentlichen
- Container regelmäßig aktualisieren
- Rechte und Benutzer im Container beachten

Docker reduziert manche Probleme, ersetzt aber keine Sicherheitsplanung.

---

## Docker und `.env`

Viele Docker-Projekte nutzen `.env`-Dateien.

Beispiel:

```env
POSTGRES_USER=example
POSTGRES_PASSWORD=change_me
POSTGRES_DB=app
```

Echte `.env`-Dateien gehören meistens in `.gitignore`.

```gitignore
.env
```

Für öffentliche Repositories nutzt man lieber:

```text
.env.example
```

Diese Datei enthält nur Beispielwerte.

Gute Regel:

```text
.env = lokal und privat
.env.example = öffentliches Beispiel
```

---

## Docker und Datenhaltung

Container sind austauschbar.

Daten sollten nicht unüberlegt im Container-Dateisystem liegen.

Wichtige Daten gehören in:

```text
Volumes
Bind Mounts
Backups
Datenbank-Dumps
```

Beispiel:

```yaml
volumes:
  - db_data:/var/lib/postgresql/data
```

Wichtig bei Compose:

```bash
docker compose down
```

stoppt und entfernt Container.

```bash
docker compose down -v
```

löscht zusätzlich Volumes.

Das kann Daten löschen.

---

## Docker und Troubleshooting

Ein guter FISI muss Docker-Probleme systematisch prüfen können.

Typischer Ablauf:

```bash
docker ps -a
docker logs container
docker inspect container
docker port container
docker stats container
```

Bei Compose:

```bash
docker compose ps
docker compose logs
docker compose config
```

Bei Portproblemen:

```bash
ss -tulpen
curl http://localhost:port
```

Bei Volumeproblemen:

```bash
docker volume ls
docker volume inspect volume
```

Bei Netzwerkproblemen:

```bash
docker network ls
docker network inspect network
```

Wichtig:

```text
Nicht raten. Prüfen.
```

---

## Docker und Dokumentation

Docker-Projekte müssen gut dokumentiert sein.

Eine gute Docker-Dokumentation enthält:

| Abschnitt       | Inhalt                             |
| --------------- | ---------------------------------- |
| Zweck           | Was macht das Projekt?             |
| Voraussetzungen | Docker, Docker Compose             |
| Start           | `docker compose up -d`             |
| Stop            | `docker compose down`              |
| Ports           | Welche Dienste sind wo erreichbar? |
| Volumes         | Wo liegen dauerhafte Daten?        |
| Logs            | Wie prüft man Fehler?              |
| Sicherheit      | Welche Daten sind nur Beispiele?   |
| Troubleshooting | Häufige Fehler und Lösungen        |

Beispiel:

```bash
docker compose up -d
docker compose ps
docker compose logs
docker compose down
```

Diese Befehle sollten in vielen Docker-READMEs vorkommen.

---

## Docker in Schul- und Lernprojekten

Docker ist sehr gut für Lernprojekte geeignet.

Beispiele:

```text
Datenbankprojekt mit PostgreSQL und Adminer
Webserver-Test mit nginx
Python-App als Container
kleines API-Lab
Markdown-Doku mit Compose-Beispiel
SQL-Projekt mit Datenbankcontainer
```

Wichtig ist, dass man nicht nur kopiert, sondern versteht:

- welches Image genutzt wird
- welcher Container läuft
- welche Ports offen sind
- welche Daten dauerhaft gespeichert werden
- wie man Logs liest
- wie man Fehler findet
- wie man alles sauber stoppt

---

## Docker und DevOps-Grundlagen

Docker ist ein wichtiger Baustein für DevOps.

Docker allein ist noch nicht DevOps, aber es gehört oft dazu.

Typische Verbindungen:

| Thema                  | Docker-Bezug                                     |
| ---------------------- | ------------------------------------------------ |
| CI/CD                  | Images bauen und testen                          |
| Deployment             | Container bereitstellen                          |
| Infrastructure as Code | Umgebung als Datei beschreiben                   |
| Monitoring             | Container überwachen                             |
| Logging                | Logs sammeln und auswerten                       |
| Versionierung          | Dockerfile und Compose in Git                    |
| Automatisierung        | Start, Build und Tests automatisieren            |
| Cloud                  | Container auf Servern oder Plattformen betreiben |

Für den Einstieg reicht es, Docker lokal sicher zu verstehen.

Später kann man darauf DevOps-Wissen aufbauen.

---

## Docker im Home-Lab

Docker eignet sich gut für ein Home-Lab.

Mögliche Dienste:

```text
nginx
PostgreSQL
Adminer
Uptime Kuma
Grafana
Prometheus
Portainer
Vaultwarden
Nextcloud
```

Für den Anfang sollte man einfache Dienste nutzen.

Gute Reihenfolge:

1. einzelner nginx-Container
2. nginx mit Bind Mount
3. PostgreSQL mit Volume
4. PostgreSQL + Adminer mit Compose
5. Logs und Troubleshooting
6. kleines eigenes Projekt mit Dockerfile
7. mehrere Dienste mit Compose

So baut man Verständnis Schritt für Schritt auf.

---

## Beispiel: kleines FISI-Docker-Projekt

Ein gutes kleines Projekt:

```text
PostgreSQL + Adminer mit Docker Compose
```

Ziel:

- Datenbankcontainer starten
- Adminer als Web-GUI nutzen
- Daten dauerhaft in Volume speichern
- Datenbank nicht unnötig auf Host-Port veröffentlichen
- README schreiben
- Logs prüfen
- Fehler dokumentieren

Struktur:

```text
docker-db-lab/
├── README.md
├── docker-compose.yml
├── .env.example
└── .gitignore
```

Das ist einfach, realistisch und gut erklärbar.

---

## Beispiel: nginx-Testserver

Ein anderes kleines Projekt:

```text
nginx mit eigener index.html
```

Struktur:

```text
nginx-lab/
├── README.md
├── docker-compose.yml
└── html/
    └── index.html
```

Compose:

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html:ro
```

Starten:

```bash
docker compose up -d
```

Prüfen:

```bash
curl http://localhost:8080
docker compose logs web
```

---

## Beispiel: Python-App im Container

Ein einfaches Python-Projekt kann auch in Docker laufen.

Dockerfile:

```Dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY . .
CMD ["python", "main.py"]
```

Image bauen:

```bash
docker build -t python-test .
```

Container starten:

```bash
docker run --rm python-test
```

Das zeigt, wie Anwendung und Laufzeitumgebung zusammen verpackt werden.

Für den Anfang reicht eine kleine Konsolenanwendung.

---

## Typische praktische Fehler

| Fehler                                           | Problem                        |
| ------------------------------------------------ | ------------------------------ |
| Container gelöscht, Daten weg                    | kein Volume genutzt            |
| Port nicht erreichbar                            | Port-Mapping fehlt oder falsch |
| Datenbank über localhost gesucht                 | falscher Hostname im Container |
| Compose-Datei geändert, aber nicht neu gestartet | alte Konfiguration läuft       |
| `.env` gepusht                                   | Zugangsdaten öffentlich        |
| keine README                                     | Projekt schwer verständlich    |
| Logs nicht gelesen                               | Fehlerursache bleibt unklar    |
| `latest` blind genutzt                           | Version ändert sich unerwartet |
| `down -v` genutzt                                | Volume-Daten gelöscht          |
| Docker als VM verstanden                         | falsche Erwartung an Container |

---

## Gute Arbeitsweise mit Docker

Eine saubere Docker-Arbeitsweise:

1. Projektstruktur erstellen
2. README schreiben oder vorbereiten
3. Compose-Datei erstellen
4. `.env.example` nutzen
5. `.env` ignorieren
6. Container starten
7. Status prüfen
8. Logs prüfen
9. Dienst testen
10. Fehler dokumentieren
11. Projekt sauber stoppen
12. Änderungen committen

Typische Befehle:

```bash
docker compose up -d
docker compose ps
docker compose logs
curl http://localhost:8080
docker compose down
git status
git add .
git commit -m "Add Docker lab"
git push
```

---

## Checkliste vor dem Commit

Vor dem Commit eines Docker-Projekts prüfen:

```text
Sind echte Passwörter entfernt?
Ist .env in .gitignore?
Gibt es eine .env.example?
Sind Ports dokumentiert?
Sind Volumes erklärt?
Funktioniert docker compose up -d?
Funktioniert docker compose down?
Sind Logs geprüft?
Ist README aktuell?
Sind keine lokalen Datenbankdaten im Repo?
```

Passende Befehle:

```bash
git status
docker compose config
docker compose up -d
docker compose ps
docker compose logs
docker compose down
```

---

## Checkliste bei Fehlern

Bei Docker-Fehlern prüfen:

```text
Läuft der Container?
Was sagen die Logs?
Ist der Port richtig?
Ist der Host-Port frei?
Ist das Volume korrekt?
Sind die Services im gleichen Netzwerk?
Wird localhost falsch verwendet?
Wurde die Compose-Datei korrekt gelesen?
Sind Umgebungsvariablen gesetzt?
```

Passende Befehle:

```bash
docker ps -a
docker logs container
docker inspect container
docker port container
docker network ls
docker volume ls
docker compose config
docker compose logs
ss -tulpen
```

---

## Wichtige Befehle für die Praxis

| Befehl                         | Bedeutung                 |
| ------------------------------ | ------------------------- |
| `docker ps`                    | laufende Container        |
| `docker ps -a`                 | alle Container            |
| `docker images`                | Images anzeigen           |
| `docker logs container`        | Logs lesen                |
| `docker logs -f container`     | Logs live verfolgen       |
| `docker exec -it container sh` | Shell im Container öffnen |
| `docker inspect container`     | Details anzeigen          |
| `docker port container`        | Port-Mapping prüfen       |
| `docker volume ls`             | Volumes anzeigen          |
| `docker network ls`            | Netzwerke anzeigen        |
| `docker stats`                 | Ressourcen prüfen         |
| `docker system df`             | Docker-Speicher anzeigen  |
| `docker compose up -d`         | Compose starten           |
| `docker compose down`          | Compose stoppen           |
| `docker compose ps`            | Compose-Status            |
| `docker compose logs`          | Compose-Logs              |
| `docker compose config`        | Compose-Datei prüfen      |
| `docker compose up -d --build` | neu bauen und starten     |

---

## FISI-Bezug

Docker ist für Fachinformatiker für Systemintegration wichtig, weil es viele praktische IT-Themen verbindet.

In der Praxis bedeutet das:

- Dienste schnell bereitstellen
- Testumgebungen aufbauen
- Datenbanken lokal nutzen
- Webserver prüfen
- Logs analysieren
- Ports und Netzwerke verstehen
- Volumes und Datenhaltung planen
- Git-Repositories mit Docker-Dateien pflegen
- Projekte reproduzierbar dokumentieren
- Grundlagen für DevOps entwickeln

Ein guter FISI nutzt Docker nicht blind. Er versteht, was ein Container macht, wo Daten liegen, welche Ports offen sind und wie Fehler systematisch geprüft werden.

---

## Kurze Zusammenfassung

Docker ist in der FISI-Praxis ein nützliches Werkzeug für Testumgebungen, Datenbanken, Webserver, Admin-Tools, Home-Labs und DevOps-Grundlagen.

Wichtig sind nicht nur die Befehle, sondern das Verständnis für Images, Container, Volumes, Netzwerke, Ports, Logs, Compose und Sicherheit.

Docker-Projekte sollten sauber dokumentiert, versioniert und ohne sensible Daten veröffentlicht werden.

Für FISI ist Docker besonders wertvoll, weil es Linux, Netzwerk, Dienste, Datenbanken, Git, Dokumentation und Automatisierung praktisch miteinander verbindet.
