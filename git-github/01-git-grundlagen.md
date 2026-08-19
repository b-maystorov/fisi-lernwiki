````markdown
# 1. Git Grundlagen

In diesem Kapitel geht es um die Grundlagen von Git und Versionskontrolle.

Git hilft dabei, Änderungen an Dateien nachvollziehbar zu speichern. Dadurch kann man sehen, was geändert wurde, ältere Versionen wiederfinden und gemeinsam an Projekten arbeiten.

Für Fachinformatiker für Systemintegration ist Git besonders bei Skripten, Konfigurationsdateien, Dokumentationen, Docker-Projekten und Automatisierung nützlich.

---

## Ziel dieses Kapitels

Nach diesem Kapitel sollte ich erklären können:

- was Git ist
- was Versionskontrolle bedeutet
- was ein Repository ist
- was Working Directory und Staging Area bedeuten
- was ein Commit ist
- was ein Branch ist
- was der Unterschied zwischen Git und GitHub ist
- wie ein einfacher Git-Workflow aussieht
- welche grundlegenden Git-Befehle wichtig sind

---

## Was ist Versionskontrolle?

Versionskontrolle bedeutet, dass Änderungen an Dateien gespeichert und nachvollzogen werden können.

Ohne Versionskontrolle entstehen schnell mehrere Kopien derselben Datei.

Zum Beispiel:

```text
config.conf
config-neu.conf
config-neu2.conf
config-final.conf
config-final-wirklich.conf
```

Das wird schnell unübersichtlich.

Git löst dieses Problem, indem Änderungen als Versionen gespeichert werden.

Diese gespeicherten Änderungen heißen bei Git **Commits**.

Dadurch kann später nachvollzogen werden:

- welche Datei geändert wurde
- was geändert wurde
- wann die Änderung durchgeführt wurde
- wer die Änderung durchgeführt hat
- welcher Stand vorher vorhanden war

---

## Was ist Git?

Git ist ein verteiltes Versionskontrollsystem.

Es wurde dafür entwickelt, Änderungen an Dateien und Projekten zu verwalten.

Git arbeitet hauptsächlich lokal auf dem eigenen Computer.

Viele wichtige Befehle benötigen deshalb keine Internetverbindung.

Zum Beispiel:

```bash
git status
git add
git commit
git log
git diff
```

Erst für die Kommunikation mit einem entfernten Repository wird normalerweise eine Netzwerkverbindung benötigt.

Zum Beispiel:

```bash
git pull
git push
```

---

## Git und GitHub

Git und GitHub sind nicht dasselbe.

**Git** ist das Versionskontrollsystem.

**GitHub** ist eine Plattform, auf der Git-Repositories gespeichert und gemeinsam verwendet werden können.

| Git                      | GitHub                         |
| ------------------------ | ------------------------------ |
| Versionskontrollsystem   | Plattform für Git-Repositories |
| arbeitet lokal           | arbeitet über das Netzwerk     |
| verwaltet Commits        | speichert Remote-Repositories  |
| verwaltet Branches       | bietet Pull Requests           |
| funktioniert ohne GitHub | verwendet Git                  |

Ein Git-Repository kann also auch vollständig ohne GitHub verwendet werden.

---

## Repository

Ein Projekt, das mit Git verwaltet wird, nennt man **Repository**.

Ein neues Repository kann mit folgendem Befehl erstellt werden:

```bash
git init
```

Beispiel:

```bash
mkdir testprojekt
cd testprojekt
git init
```

Git erstellt dabei im Hintergrund das versteckte Verzeichnis:

```text
.git
```

Darin speichert Git unter anderem:

- Commits
- Branches
- Repository-Konfiguration
- Referenzen
- Versionshistorie

Das `.git`-Verzeichnis gehört zum Repository und sollte nicht einfach gelöscht werden.

---

## Prüfen, ob man in einem Repository ist

Einer der wichtigsten Git-Befehle ist:

```bash
git status
```

Wenn man sich in einem Git-Repository befindet, zeigt Git den aktuellen Zustand an.

Beispiel:

```text
On branch main
nothing to commit, working tree clean
```

Das bedeutet:

- aktueller Branch ist `main`
- es gibt keine ungespeicherten Änderungen
- das Repository ist sauber

Befindet man sich außerhalb eines Repositorys, erscheint normalerweise eine Fehlermeldung.

---

## Working Directory

Das **Working Directory** ist das normale Projektverzeichnis.

Dort werden die Dateien bearbeitet.

Beispiel:

```text
projekt/
├── README.md
├── docker-compose.yml
├── scripts/
└── docs/
```

Wenn eine Datei verändert wird, erkennt Git die Änderung.

Prüfen kann man das mit:

```bash
git status
```

Beispiel:

```text
modified: README.md
```

Die Datei wurde verändert, aber noch nicht als neuer Commit gespeichert.

---

## Untracked Files

Neue Dateien kennt Git zunächst noch nicht.

Diese Dateien werden als **untracked** bezeichnet.

Beispiel:

```bash
touch test.txt
git status
```

Git kann dann anzeigen:

```text
Untracked files:
    test.txt
```

Damit Git die Datei verfolgen kann, muss sie hinzugefügt werden:

```bash
git add test.txt
```

---

## Staging Area

Bevor Änderungen in einem Commit gespeichert werden, kommen sie normalerweise in die **Staging Area**.

Dafür verwendet man:

```bash
git add DATEI
```

Beispiel:

```bash
git add README.md
```

Mehrere Dateien können ebenfalls hinzugefügt werden:

```bash
git add README.md setup.sh
```

Alle Änderungen im aktuellen Bereich:

```bash
git add .
```

Wichtig:

`git add` erstellt noch keinen Commit und lädt auch nichts auf GitHub hoch.

Der Befehl bereitet Änderungen nur für den nächsten Commit vor.

---

## Warum gibt es die Staging Area?

Mit der Staging Area kann ausgewählt werden, welche Änderungen zusammen in einen Commit gehören.

Angenommen, drei Dateien wurden verändert:

```text
README.md
setup.sh
notes.txt
```

Für den nächsten Commit sollen aber nur zwei Dateien verwendet werden.

Dann kann man schreiben:

```bash
git add README.md setup.sh
```

`notes.txt` bleibt außerhalb des Commits.

Dadurch können Änderungen sauber getrennt werden.

---

## Commit

Ein **Commit** speichert Änderungen in der Git-Historie.

Beispiel:

```bash
git commit -m "Add installation documentation"
```

Jeder Commit enthält unter anderem:

- die gespeicherten Änderungen
- eine Commit-Nachricht
- den Autor
- den Zeitpunkt
- eine eindeutige Commit-ID

Eine Commit-ID kann zum Beispiel so aussehen:

```text
b35e7ba
```

Git verwendet intern einen längeren Hash. Häufig wird nur eine verkürzte Form angezeigt.

---

## Commit-Nachrichten

Eine Commit-Nachricht sollte kurz beschreiben, was geändert wurde.

Gute Beispiele:

```text
Add Linux networking chapter
Update project README
Fix Docker port configuration
Add backup script
```

Weniger hilfreich sind:

```text
update
test
stuff
changes
```

Klare Commit-Nachrichten machen die Historie später deutlich verständlicher.

---

## Änderungen prüfen

Bevor Änderungen gespeichert werden, sollte man sie kontrollieren.

Zuerst:

```bash
git status
```

Danach kann man Änderungen innerhalb der Dateien anzeigen:

```bash
git diff
```

Beispiel:

```diff
- Alte Beschreibung
+ Neue Beschreibung
```

Danach kann die Datei zur Staging Area hinzugefügt werden:

```bash
git add README.md
```

Und anschließend:

```bash
git commit -m "Update README"
```

---

## Commit-Historie

Git speichert Commits als Historie.

Vereinfacht kann das so aussehen:

```text
Commit A
   |
Commit B
   |
Commit C
   |
Commit D
```

Die Historie kann angezeigt werden mit:

```bash
git log
```

Eine kompaktere Darstellung:

```bash
git log --oneline
```

Beispiel:

```text
b35e7ba Add Git and GitHub section README
1eaaef0 Add Linux system administration chapter
91a1c20 Add Linux shell scripting chapter
```

---

## Branches

Ein **Branch** ist eine eigene Entwicklungslinie innerhalb eines Repositorys.

Der Hauptbranch heißt heute häufig:

```text
main
```

Ein zusätzlicher Branch könnte zum Beispiel heißen:

```text
feature-login
```

Dadurch können Änderungen getrennt vom Hauptstand entwickelt werden.

Vereinfacht:

```text
main
 |
 A
 |
 B
 |\
 | C   feature
 | |
 | D
```

Branches werden später in einem eigenen Kapitel genauer behandelt.

---

## HEAD

`HEAD` zeigt auf den aktuell verwendeten Stand im Repository.

Normalerweise zeigt `HEAD` auf den aktiven Branch.

Zum Beispiel:

```text
HEAD -> main
```

Den aktuellen Branch kann man anzeigen mit:

```bash
git branch
```

Beispiel:

```text
* main
```

Der Stern zeigt, welcher Branch aktuell aktiv ist.

---

## Lokales Repository

Git arbeitet zuerst lokal.

Das bedeutet:

Commits werden auf dem eigenen Computer erstellt.

Typische lokale Befehle sind:

```bash
git status
git add
git commit
git diff
git log
git branch
```

Für diese Befehle wird GitHub nicht benötigt.

---

## Remote-Repository

Ein Repository kann zusätzlich auf einem anderen Server gespeichert werden.

Das nennt man **Remote-Repository**.

Mögliche Plattformen sind:

- GitHub
- GitLab
- eigener Git-Server
- Firmenserver

Ein häufig verwendeter Name für das Remote-Repository ist:

```text
origin
```

Remotes anzeigen:

```bash
git remote -v
```

Beispiel:

```text
origin  git@github.com:username/projekt.git (fetch)
origin  git@github.com:username/projekt.git (push)
```

---

## Repository klonen

Ein vorhandenes Repository kann kopiert werden mit:

```bash
git clone URL
```

Beispiel:

```bash
git clone git@github.com:username/projekt.git
```

Git lädt dabei das Repository inklusive seiner Historie auf den lokalen Computer.

Danach kann man in das Projekt wechseln:

```bash
cd projekt
```

Und prüfen:

```bash
git status
```

---

## `git init` oder `git clone`

Die Befehle haben unterschiedliche Aufgaben.

| Befehl      | Bedeutung                       |
| ----------- | ------------------------------- |
| `git init`  | neues Repository erstellen      |
| `git clone` | vorhandenes Repository kopieren |

Für ein komplett neues Projekt:

```bash
mkdir projekt
cd projekt
git init
```

Für ein bereits vorhandenes GitHub-Projekt:

```bash
git clone URL
```

---

## Einfacher Git-Workflow

Ein typischer Ablauf kann so aussehen:

```text
Datei bearbeiten
      ↓
git status
      ↓
git diff
      ↓
git add
      ↓
git commit
      ↓
git push
```

Praktisches Beispiel:

```bash
git status
git diff
git add README.md
git status
git commit -m "Update README"
git push
```

Der zweite `git status` ist hilfreich, um zu kontrollieren, welche Dateien tatsächlich für den Commit vorbereitet wurden.

---

## Aktuelles Verzeichnis beachten

Git arbeitet mit den Dateipfaden des aktuellen Verzeichnisses.

Das aktuelle Verzeichnis kann angezeigt werden mit:

```bash
pwd
```

Beispiel:

Man befindet sich im Hauptverzeichnis:

```text
~/github/private/fisi-lernwiki
```

Dann lautet ein Dateipfad:

```bash
git add git-github/README.md
```

Befindet man sich bereits in:

```text
~/github/private/fisi-lernwiki/git-github
```

reicht:

```bash
git add README.md
```

Deshalb sollte man bei Problemen immer prüfen:

```bash
pwd
git status
```

---

## Wichtige Grundbefehle

| Befehl                 | Bedeutung                            |
| ---------------------- | ------------------------------------ |
| `git init`             | Repository erstellen                 |
| `git clone URL`        | Repository kopieren                  |
| `git status`           | aktuellen Zustand anzeigen           |
| `git add DATEI`        | Änderung zur Staging Area hinzufügen |
| `git commit -m "Text"` | Commit erstellen                     |
| `git diff`             | Änderungen anzeigen                  |
| `git log`              | Commit-Historie anzeigen             |
| `git log --oneline`    | kompakte Historie anzeigen           |
| `git branch`           | Branches anzeigen                    |
| `git remote -v`        | Remote-Repositories anzeigen         |
| `pwd`                  | aktuelles Verzeichnis anzeigen       |

---

## Typische Fehler

### Falsches Verzeichnis

Man befindet sich nicht dort, wo man denkt.

Prüfen:

```bash
pwd
```

---

### `git add` vergessen

Eine Datei wurde verändert, aber nicht zur Staging Area hinzugefügt.

Prüfen:

```bash
git status
```

---

### Zu viele Dateien hinzufügen

Mit:

```bash
git add .
```

werden viele Änderungen gleichzeitig hinzugefügt.

Deshalb vorher prüfen:

```bash
git status
```

Bei wichtigen Projekten ist es oft besser, Dateien gezielt hinzuzufügen.

---

### Unklare Commit-Nachrichten

Nachrichten wie:

```text
update
test
changes
```

erklären später kaum noch, was gemacht wurde.

Besser:

```text
Add Git basics chapter
```

---

### Git und GitHub verwechseln

Ein Commit wird zuerst lokal erstellt.

```bash
git commit
```

Erst mit:

```bash
git push
```

werden lokale Commits an ein Remote-Repository übertragen.

---

## Praktisches Beispiel

Eine Markdown-Datei wurde in VS Code bearbeitet.

Danach im Terminal:

```bash
git status
```

Änderungen prüfen:

```bash
git diff
```

Datei vorbereiten:

```bash
git add dokumentation.md
```

Kontrollieren:

```bash
git status
```

Commit erstellen:

```bash
git commit -m "Update documentation"
```

Danach hochladen:

```bash
git push
```

Das ist ein einfacher und sauberer Git-Workflow.

---

## FISI-Bezug

Git ist für Fachinformatiker für Systemintegration besonders bei technischen Projekten nützlich.

Typische Beispiele sind:

- Bash-Skripte
- Python-Skripte
- Dockerfiles
- Docker-Compose-Dateien
- Konfigurationsdateien
- Installationsskripte
- technische Dokumentation
- Automatisierung
- Infrastructure as Code

Git hilft dabei, Änderungen nachvollziehbar zu dokumentieren.

Dadurch kann ein Administrator später erkennen, wann eine Konfiguration geändert wurde und welche Änderung möglicherweise zu einem Fehler geführt hat.

Auch viele DevOps-Werkzeuge und CI/CD-Prozesse verwenden Git als Grundlage.

---

## Kurze Zusammenfassung

Git ist ein Versionskontrollsystem zur Verwaltung von Änderungen an Dateien.

Ein Git-Projekt wird Repository genannt.

Dateien werden zunächst im Working Directory bearbeitet. Mit `git add` werden Änderungen zur Staging Area hinzugefügt. Mit `git commit` werden sie anschließend in der lokalen Git-Historie gespeichert.

Wichtige Befehle für den Einstieg sind:

```bash
git status
git diff
git add
git commit
git log
```

Git und GitHub sind nicht dasselbe. Git verwaltet die Versionen, während GitHub Git-Repositories online bereitstellt und Zusammenarbeit ermöglicht.

Für FISI ist Git besonders bei Skripten, Konfigurationen, Dokumentationen und Automatisierung wichtig.
````
