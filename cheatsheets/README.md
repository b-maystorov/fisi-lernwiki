# Cheatsheets

In diesem Bereich sammle ich kurze Befehlsübersichten für wichtige IT-Themen.

Die ausführlichen Erklärungen stehen in den jeweiligen Fachkapiteln. Die Cheatsheets sind als schnelle praktische Nachschlagehilfe gedacht, wenn man einen Befehl, eine Option oder einen typischen Ablauf schnell wiederfinden möchte.

---

## Ziel dieses Bereichs

Cheatsheets helfen dabei, häufig genutzte Befehle schneller zu wiederholen.

Sie ersetzen keine vollständige Erklärung, sondern ergänzen die ausführlichen Lernkapitel.

Der Fokus liegt auf:

- wichtigen Befehlen
- kurzen Erklärungen
- typischen Admin-Abläufen
- praktischer Wiederholung
- schneller Orientierung im Terminal
- Git-, Linux-, Docker- und Netzwerk-Grundlagen

---

## Übersicht

| Cheatsheet                                | Thema                                                           |
| ----------------------------------------- | --------------------------------------------------------------- |
| [Linux-Befehle](./linux-befehle.md)       | wichtige Linux-Kommandos für Alltag und Administration          |
| [Git-Befehle](./git-befehle.md)           | wichtige Git-Kommandos für Repository-Arbeit                    |
| [Docker-Befehle](./docker-befehle.md)     | wichtige Docker-Kommandos für Container, Images und Logs        |
| [Netzwerk-Befehle](./netzwerk-befehle.md) | wichtige Befehle für IP, DNS, Routing, Ports und Fehlersuche    |
| [SQL-Befehle](./sql-befehle.md)           | wichtige SQL-Befehle für Abfragen, Tabellen und Datenverwaltung |

---

## Warum Cheatsheets sinnvoll sind

Viele IT-Befehle versteht man erst richtig, wenn man sie regelmäßig benutzt.

Am Anfang vergisst man schnell:

- wie ein Befehl genau geschrieben wird
- welche Option gebraucht wird
- welcher Befehl zuerst kommt
- wie man Fehler prüft
- wie man den aktuellen Zustand kontrolliert

Ein Cheatsheet hilft dabei, schneller wieder in das Thema reinzukommen.

Besonders bei Linux, Git, Docker und Netzwerkdiagnose ist das praktisch, weil man diese Befehle immer wieder braucht.

---

## Aufbau der Cheatsheets

Die Cheatsheets sind bewusst kompakt gehalten.

Typischer Aufbau:

```text
Befehl
kurze Bedeutung
typischer Einsatz
wichtige Hinweise
```

Beispiel:

| Befehl       | Bedeutung                                    |
| ------------ | -------------------------------------------- |
| `pwd`        | zeigt den aktuellen Pfad                     |
| `ls -la`     | zeigt Dateien, Ordner und versteckte Dateien |
| `git status` | zeigt den aktuellen Git-Zustand              |
| `docker ps`  | zeigt laufende Container                     |

---

## Wichtiger Hinweis

Cheatsheets zeigen Befehle kurz und direkt.

Bei gefährlichen Befehlen sollte man trotzdem vorsichtig sein.

Beispiele:

```bash
rm -rf
git reset --hard
git clean -fdx
docker system prune -a
```

Solche Befehle können Daten löschen oder Projektstände verändern.

Vor solchen Befehlen sollte man immer prüfen, was genau passiert.

---

## Gute Arbeitsweise

Auch mit Cheatsheets sollte man nicht blind Befehle kopieren.

Gute Reihenfolge:

1. Zustand prüfen
2. Befehl verstehen
3. Befehl ausführen
4. Ergebnis kontrollieren
5. Änderung dokumentieren

Beispiele für Zustandsprüfung:

```bash
pwd
ls -la
git status
docker ps
ip a
```

Diese Befehle helfen zuerst zu verstehen, wo man ist und was gerade läuft.

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Cheatsheets sehr nützlich.

In der Praxis arbeitet man häufig mit:

- Linux-Terminal
- Servern
- Netzwerken
- Git-Repositories
- Docker-Containern
- Logs
- Diensten
- Konfigurationsdateien

Viele Aufgaben wiederholen sich. Eine gute Befehlsübersicht spart Zeit und hilft, sicherer zu arbeiten.

---

## Kurze Zusammenfassung

Der Cheatsheet-Bereich ist eine schnelle Befehlsübersicht für praktische IT-Arbeit.

Die ausführlichen Erklärungen stehen in den Hauptkapiteln. Die Cheatsheets dienen als kompakte Wiederholung und schnelle Hilfe im Alltag.

Aktuell geplant sind Cheatsheets für Linux, Git, Docker und Netzwerkbefehle.
