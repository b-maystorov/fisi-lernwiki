# 1. Git Grundlagen

In diesem Kapitel geht es um die wichtigsten Grundlagen von Git.

Git ist ein Versionsverwaltungssystem. Damit kann man Änderungen an Dateien speichern, vergleichen, nachvollziehen und bei Bedarf wiederherstellen. Git wird sehr häufig in Softwareprojekten genutzt, ist aber auch für Dokumentation, Skripte, Konfigurationsdateien und IT-Projekte sehr nützlich.

Für Fachinformatiker für Systemintegration ist Git wichtig, weil viele praktische Arbeiten versioniert werden können: Linux-Dokumentation, Netzwerkdokumentation, Docker-Projekte, Shell-Skripte, Python-Projekte, Konfigurationsbeispiele und GitHub-Portfolios.

---

## Kurz erklärt

Git speichert nicht einfach nur Dateien, sondern Änderungen an einem Projekt.

Ein Git-Projekt heißt Repository.

Ein Repository enthält:

- die Projektdateien
- die Git-Historie
- gespeicherte Zwischenstände
- Informationen über Änderungen
- Branches
- Konfigurationen für Remotes

Ein gespeicherter Zwischenstand heißt Commit.

Ein typischer Git-Ablauf sieht so aus:

```bash
git status
git add README.md
git commit -m "Add README"
git push
```

Dabei wird zuerst geprüft, was geändert wurde. Danach werden Änderungen vorgemerkt, lokal gespeichert und später zu GitHub hochgeladen.

---

## Warum Git wichtig ist

Ohne Git werden Projektstände schnell unübersichtlich.

Schlechtes Beispiel ohne Git:

```text
projekt.txt
projekt-neu.txt
projekt-final.txt
projekt-final2.txt
projekt-final-wirklich.txt
projekt-final-abgabe.txt
```

Mit Git speichert man stattdessen klare Zwischenstände.

Beispiel:

```text
Add Linux README
Update network troubleshooting notes
Fix typo in Git chapter
Add Docker setup documentation
```

Dadurch kann man später nachvollziehen:

- was geändert wurde
- wann etwas geändert wurde
- warum etwas geändert wurde
- welche Dateien betroffen waren
- welcher Stand vorher existierte
- ob eine Änderung rückgängig gemacht werden muss

Git bringt Ordnung in Projekte.

---

## Git und GitHub

Git und GitHub sind nicht dasselbe.

| Begriff    | Bedeutung                                  |
| ---------- | ------------------------------------------ |
| Git        | Versionsverwaltung auf dem eigenen Rechner |
| GitHub     | Online-Plattform für Git-Repositories      |
| Repository | Projekt mit Git-Historie                   |
| Remote     | entfernte Version eines Repositories       |
| Commit     | gespeicherter Projektstand                 |
| Push       | lokale Commits hochladen                   |
| Pull       | Änderungen vom Remote holen                |

Git funktioniert auch komplett ohne GitHub.

GitHub nutzt Git, um Repositories online zu speichern und Zusammenarbeit zu ermöglichen.

---

## Repository

Ein Repository ist ein Projektordner, der von Git verwaltet wird.

Ein Repository enthält einen versteckten Ordner:

```text
.git
```

Dieser Ordner enthält die Git-Historie und interne Git-Daten.

Anzeigen:

```bash
ls -la
```

Wenn ein Ordner `.git` enthält, ist er ein Git-Repository.

Wichtig:

Man sollte den `.git`-Ordner nicht manuell löschen oder bearbeiten, wenn man nicht genau weiß, was man tut.

---

## Git installieren

Auf Ubuntu oder Debian kann Git mit `apt` installiert werden.

```bash
sudo apt update
sudo apt install git
```

Version prüfen:

```bash
git --version
```

Beispielausgabe:

```text
git version 2.43.0
```

Die genaue Version kann je nach System unterschiedlich sein.

---

## Git konfigurieren

Git sollte wissen, welcher Name und welche E-Mail-Adresse für Commits genutzt werden.

Global konfigurieren:

```bash
git config --global user.name "Bilgin Maystorov"
git config --global user.email "beispiel@example.com"
```

Konfiguration anzeigen:

```bash
git config --list
```

Einzelne Werte anzeigen:

```bash
git config user.name
git config user.email
```

Wichtig:

In öffentlichen Repositories sollte man keine private E-Mail-Adresse verwenden, wenn man das nicht möchte. GitHub bietet dafür auch No-Reply-Adressen an.

---

## Lokale und globale Git-Konfiguration

Git kann Konfigurationen auf verschiedenen Ebenen speichern.

| Ebene  | Bedeutung                              |
| ------ | -------------------------------------- |
| system | gilt für das ganze System              |
| global | gilt für den aktuellen Benutzer        |
| local  | gilt nur für ein bestimmtes Repository |

Lokale Konfiguration anzeigen:

```bash
git config --local --list
```

Globale Konfiguration anzeigen:

```bash
git config --global --list
```

Lokale Werte überschreiben globale Werte.

Das ist nützlich, wenn man verschiedene Identitäten nutzt, zum Beispiel private und schulische Repositories.

---

## Repository erstellen mit git init

Ein neuer Ordner kann mit Git initialisiert werden.

```bash
mkdir testprojekt
cd testprojekt
git init
```

Danach ist der Ordner ein Git-Repository.

Prüfen:

```bash
ls -la
```

Man sieht dann den Ordner:

```text
.git
```

`git init` nutzt man, wenn man ein neues lokales Projekt starten möchte.

---

## Repository klonen mit git clone

Ein bestehendes Repository kann man herunterladen.

```bash
git clone repository-url
```

Beispiel:

```bash
git clone git@github.com:user/repository.git
```

Dadurch wird ein neuer Ordner erstellt, der bereits ein Git-Repository ist.

`git clone` wird genutzt, wenn ein Projekt schon auf GitHub oder einem anderen Git-Server existiert.

---

## Arbeitsbereiche in Git

Git arbeitet grob mit drei wichtigen Bereichen.

| Bereich           | Bedeutung                                       |
| ----------------- | ----------------------------------------------- |
| Working Directory | Dateien, an denen man gerade arbeitet           |
| Staging Area      | vorbereitete Änderungen für den nächsten Commit |
| Repository        | gespeicherte Commits                            |

Ein normaler Ablauf:

```text
Working Directory -> Staging Area -> Repository
```

Befehle dazu:

```bash
git add datei
git commit -m "Nachricht"
```

`git add` legt Änderungen in die Staging Area.  
`git commit` speichert diese Änderungen fest in der lokalen Git-Historie.

---

## git status

`git status` ist einer der wichtigsten Git-Befehle.

```bash
git status
```

Der Befehl zeigt:

- auf welchem Branch man ist
- ob Dateien geändert wurden
- ob Dateien untracked sind
- ob Änderungen staged sind
- ob der lokale Stand vor oder hinter dem Remote ist

Vor fast jedem Git-Schritt sollte man `git status` nutzen.

Gute Gewohnheit:

```bash
git status
```

vor `git add`, vor `git commit` und nach `git push`.

---

## Untracked Dateien

Eine untracked Datei ist eine Datei, die Git noch nicht verfolgt.

Beispiel:

```text
Untracked files:
  notes.md
```

Das bedeutet:

Die Datei existiert im Ordner, aber Git speichert sie noch nicht in der Historie.

Vormerken:

```bash
git add notes.md
```

Danach ist die Datei in der Staging Area.

---

## Modified Dateien

Eine modified Datei ist eine Datei, die Git bereits kennt und die geändert wurde.

Beispiel:

```text
modified: README.md
```

Das bedeutet:

Die Datei wurde verändert, aber die Änderung ist noch nicht committed.

Änderung anzeigen:

```bash
git diff README.md
```

Änderung vormerken:

```bash
git add README.md
```

Danach kann sie committed werden.

---

## Staging Area

Die Staging Area ist ein Vorbereitungsbereich.

Man entscheidet dort, welche Änderungen in den nächsten Commit sollen.

Datei vormerken:

```bash
git add README.md
```

Mehrere Dateien vormerken:

```bash
git add file1.md file2.md
```

Alle Änderungen im aktuellen Ordner vormerken:

```bash
git add .
```

Wichtig:

`git add .` ist praktisch, aber man sollte vorher mit `git status` prüfen, damit keine falschen Dateien in den Commit kommen.

---

## Commit

Ein Commit speichert einen Projektstand in der Git-Historie.

```bash
git commit -m "Add Git basics chapter"
```

Ein Commit enthält:

- Änderungen
- Autor
- Datum
- Commit-Nachricht
- eindeutige Commit-ID
- Bezug zum vorherigen Commit

Commit-Nachrichten sollten verständlich sein.

Gut:

```text
Add Linux package management chapter
Update GitHub README
Fix typo in SSH section
```

Schlecht:

```text
update
final
stuff
test
asdf
```

---

## Commit-Historie anzeigen

Mit `git log` sieht man die Commit-Historie.

```bash
git log
```

Kompakter:

```bash
git log --oneline
```

Beispiel:

```text
a1b2c3d Add Git basics chapter
9f8e7d6 Add Git and GitHub section README
```

`git log --oneline` ist oft übersichtlicher.

Die Historie hilft zu verstehen, wie sich ein Projekt entwickelt hat.

---

## Änderungen anzeigen mit git diff

Mit `git diff` sieht man Änderungen, die noch nicht staged sind.

```bash
git diff
```

Änderungen einer Datei anzeigen:

```bash
git diff README.md
```

Staged Änderungen anzeigen:

```bash
git diff --staged
```

`git diff` ist wichtig, bevor man committet.

So sieht man, was genau gespeichert wird.

---

## Dateien aus der Staging Area entfernen

Wenn man eine Datei versehentlich mit `git add` vorgemerkt hat:

```bash
git restore --staged datei
```

Beispiel:

```bash
git restore --staged notes.md
```

Die Änderung bleibt im Working Directory erhalten, wird aber aus der Staging Area entfernt.

Das ist nützlich, wenn man einen Commit sauber aufteilen möchte.

---

## Änderungen verwerfen

Nicht gespeicherte Änderungen an einer Datei verwerfen:

```bash
git restore datei
```

Beispiel:

```bash
git restore README.md
```

Wichtig:

Dieser Befehl verwirft lokale Änderungen an der Datei.

Das sollte man nur machen, wenn man diese Änderungen wirklich nicht mehr braucht.

Vorher prüfen:

```bash
git diff README.md
```

---

## Unterschied zwischen lokal und remote

Git arbeitet zuerst lokal.

Ein Commit ist nach `git commit` nur auf dem eigenen Rechner gespeichert.

Damit GitHub den Commit bekommt, muss man pushen:

```bash
git push
```

Remote bedeutet:

Das Repository liegt auf einem anderen Server, zum Beispiel GitHub.

Lokale Arbeit:

```bash
git add
git commit
```

Online synchronisieren:

```bash
git push
git pull
```

---

## Branch-Grundidee

Ein Branch ist ein Entwicklungszweig.

Der Hauptbranch heißt oft:

```text
main
```

Branch anzeigen:

```bash
git branch
```

Neuen Branch erstellen und wechseln:

```bash
git switch -c neuer-branch
```

Branch wechseln:

```bash
git switch main
```

Branches helfen, Änderungen getrennt zu entwickeln.

Für einfache Einzelprojekte arbeitet man oft direkt auf `main`. In Teams oder größeren Projekten nutzt man häufiger eigene Branches.

---

## Hilfe zu Git-Befehlen

Git bietet eingebaute Hilfe.

Beispiele:

```bash
git help status
git status --help
git help commit
```

Kurzinfos bekommt man oft auch durch Fehlermeldungen von Git.

Git-Fehlermeldungen wirken manchmal lang, enthalten aber meistens wichtige Hinweise.

Deshalb sollte man sie genau lesen.

---

## Typischer einfacher Ablauf

Ein normaler Ablauf in einem Dokumentationsprojekt:

```bash
cd ~/github/private/fisi-lernwiki

git status
git add git-github/01-git-grundlagen.md
git commit -m "Add Git basics chapter"
git push
git status
```

Bedeutung:

| Schritt      | Zweck                        |
| ------------ | ---------------------------- |
| `cd`         | in das Repository wechseln   |
| `git status` | Zustand prüfen               |
| `git add`    | Datei vormerken              |
| `git commit` | Änderung lokal speichern     |
| `git push`   | Änderung zu GitHub hochladen |
| `git status` | prüfen, ob alles sauber ist  |

Am Ende sollte stehen:

```text
nothing to commit, working tree clean
```

---

## Git im Alltag

Git ist nicht nur für Programmcode sinnvoll.

Git kann genutzt werden für:

- Markdown-Dokumentation
- Linux-Notizen
- Shell-Skripte
- Python-Projekte
- Docker-Projekte
- Netzwerkdokumentation
- Konfigurationsbeispiele
- Lern-Wikis
- Bewerbungs- und Portfolio-Projekte
- Home-Lab-Dokumentation

Für FISI ist Git besonders nützlich, weil viele technische Arbeiten dokumentiert und versioniert werden können.

---

## Was sollte nicht in Git?

Nicht alles gehört in ein Git-Repository.

Nicht committen:

- Passwörter
- private SSH-Schlüssel
- API-Tokens
- `.env` mit echten Zugangsdaten
- private Kundendaten
- personenbezogene Daten
- große temporäre Dateien
- lokale Cache-Dateien
- Build-Artefakte, wenn nicht nötig
- interne IP-Adressen, wenn sie sensibel sind

Für solche Dateien nutzt man `.gitignore`.

Beispiel:

```gitignore
.env
*.log
__pycache__/
.venv/
private/
```

---

## Typische Fehler am Anfang

| Fehler                                  | Problem                                        |
| --------------------------------------- | ---------------------------------------------- |
| `git status` nicht prüfen               | man weiß nicht, was geändert wurde             |
| blind `git add .` nutzen                | falsche Dateien können im Commit landen        |
| schlechte Commit-Nachrichten            | Historie wird unverständlich                   |
| zu große Commits machen                 | Änderungen sind schwer nachvollziehbar         |
| `git commit` mit `git push` verwechseln | Commit ist nur lokal, Push ist online          |
| `.gitignore` vergessen                  | unnötige Dateien werden getrackt               |
| private Daten committen                 | Sicherheitsproblem                             |
| im falschen Ordner arbeiten             | Git-Befehle wirken nicht auf das richtige Repo |
| Fehlermeldungen nicht lesen             | einfache Probleme werden größer                |
| `.git`-Ordner löschen                   | Git-Historie kann verloren gehen               |

---

## Praktische Beispiele

### Beispiel 1: Neue Datei committen

```bash
touch notes.md
git status
git add notes.md
git commit -m "Add notes file"
git push
```

Damit wird eine neue Datei erstellt, vorgemerkt, committed und hochgeladen.

### Beispiel 2: Änderung prüfen und committen

```bash
git status
git diff README.md
git add README.md
git commit -m "Update README"
git push
```

Damit prüft man vor dem Commit, was sich geändert hat.

### Beispiel 3: Datei versehentlich staged

```bash
git add notes.md
git restore --staged notes.md
```

Die Datei ist danach nicht mehr für den Commit vorgemerkt.

### Beispiel 4: Lokale Änderung verwerfen

```bash
git diff notes.md
git restore notes.md
```

Damit wird die lokale Änderung an `notes.md` verworfen.

Vorsicht: Die Änderung ist danach weg.

---

## Nützliche Befehle

| Befehl                       | Bedeutung                        |
| ---------------------------- | -------------------------------- |
| `git --version`              | Git-Version anzeigen             |
| `git config --list`          | Git-Konfiguration anzeigen       |
| `git config user.name`       | Git-Benutzername anzeigen        |
| `git config user.email`      | Git-E-Mail anzeigen              |
| `git init`                   | neues Repository erstellen       |
| `git clone url`              | Repository herunterladen         |
| `git status`                 | Zustand anzeigen                 |
| `git add datei`              | Datei vormerken                  |
| `git add .`                  | alle Änderungen vormerken        |
| `git commit -m "Text"`       | Commit erstellen                 |
| `git log`                    | Historie anzeigen                |
| `git log --oneline`          | Historie kompakt anzeigen        |
| `git diff`                   | Änderungen anzeigen              |
| `git diff --staged`          | staged Änderungen anzeigen       |
| `git restore datei`          | lokale Änderungen verwerfen      |
| `git restore --staged datei` | Datei aus Staging Area entfernen |
| `git branch`                 | Branches anzeigen                |
| `git switch branch`          | Branch wechseln                  |
| `git switch -c branch`       | neuen Branch erstellen           |
| `git push`                   | Commits hochladen                |
| `git pull`                   | Änderungen holen                 |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Git eine wichtige Grundlage.

In der Praxis bedeutet das:

- Dokumentation versionieren
- Skripte nachvollziehbar verwalten
- Konfigurationsbeispiele speichern
- Änderungen an Projekten dokumentieren
- alte Zustände vergleichen
- Fehler nach Änderungen leichter finden
- mit GitHub-Projekten arbeiten
- Teamarbeit über Branches und Pull Requests vorbereiten
- eigene Lern- und Portfolio-Projekte sauber pflegen

Ein guter FISI nutzt Git nicht nur für Code, sondern auch für technische Dokumentation und wiederverwendbare Admin-Arbeiten.

---

## Kurze Zusammenfassung

Git ist ein Versionsverwaltungssystem. Es speichert Änderungen an einem Projekt in Commits.

Wichtige Grundlagen sind Repository, Working Directory, Staging Area, Commit, Branch, Remote, Push und Pull.

Die wichtigsten Befehle am Anfang sind `git status`, `git add`, `git commit`, `git log`, `git diff`, `git push` und `git pull`.

Für FISI ist Git wichtig, weil Dokumentation, Skripte, Konfigurationen und IT-Projekte sauber versioniert und nachvollziehbar gepflegt werden können.
