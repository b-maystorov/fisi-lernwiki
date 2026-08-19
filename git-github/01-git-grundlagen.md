````markdown
# 1. Git Grundlagen

In diesem Kapitel geht es um die grundlegende Funktionsweise von Git.

Git ist ein Versionskontrollsystem. Es speichert Änderungen an Dateien und ermöglicht es, verschiedene Entwicklungsstände eines Projekts nachvollziehbar zu verwalten.

Git wird häufig in der Softwareentwicklung eingesetzt, ist aber auch für Systemadministration, Dokumentation, Automatisierung und Infrastrukturprojekte sehr nützlich.

Für Fachinformatiker für Systemintegration ist Git besonders interessant, weil damit zum Beispiel Skripte, Konfigurationsdateien, Docker-Dateien und technische Dokumentationen versioniert werden können.

---

## Kurz erklärt

Git verwaltet Änderungen innerhalb eines Projekts.

Ein Projekt, das mit Git verwaltet wird, nennt man Repository.

Wichtige Grundbegriffe sind:

- Repository
- Working Directory
- Staging Area
- Commit
- Branch
- HEAD
- lokale Historie
- Remote-Repository
- Clone
- Push
- Pull
- Merge

Ein typischer Ablauf sieht so aus:

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
```

Wenn zusätzlich ein Remote-Repository wie GitHub verwendet wird:

```text
lokale Änderungen
      ↓
git add
      ↓
git commit
      ↓
git push
      ↓
GitHub
```

---

## Was ist Versionskontrolle?

Versionskontrolle bedeutet, dass verschiedene Zustände von Dateien gespeichert und nachvollzogen werden können.

Ohne Versionskontrolle könnte ein Projekt zum Beispiel so aussehen:

```text
projekt-alt/
projekt-neu/
projekt-neu2/
projekt-final/
projekt-final-neu/
projekt-final-wirklich/
```

Das wird schnell unübersichtlich.

Mit Git bleibt normalerweise ein Projektverzeichnis bestehen.

Die verschiedenen Versionen werden über Commits gespeichert.

Beispiel:

```text
Commit 1
Initiale Konfiguration

Commit 2
SSH-Konfiguration ergänzt

Commit 3
Dokumentation erweitert

Commit 4
Fehler in Konfiguration behoben
```

Dadurch lässt sich später nachvollziehen:

- was geändert wurde
- wann etwas geändert wurde
- wer etwas geändert hat
- welche Dateien betroffen waren
- welcher Projektstand vorher existierte

---

## Was ist Git?

Git ist ein verteiltes Versionskontrollsystem.

Das bedeutet, dass ein lokales Git-Repository normalerweise die komplette Projekt- und Commit-Historie enthält.

Git arbeitet deshalb auch ohne permanente Internetverbindung.

Viele wichtige Aktionen laufen vollständig lokal:

```bash
git status
git diff
git add
git commit
git log
```

Ein Internetzugang wird erst benötigt, wenn zum Beispiel mit einem Remote-Repository auf GitHub kommuniziert wird.

Beispiele:

```bash
git fetch
git pull
git push
```

---

## Git und GitHub

Git und GitHub sind nicht dasselbe.

Git ist das eigentliche Versionskontrollsystem.

GitHub ist eine Plattform zum Speichern und gemeinsamen Bearbeiten von Git-Repositories.

| Git                         | GitHub                    |
| --------------------------- | ------------------------- |
| Versionskontrollsystem      | Online-Plattform          |
| läuft lokal                 | läuft als externer Dienst |
| verwaltet Commits           | hostet Git-Repositories   |
| verwaltet Branches          | bietet Pull Requests      |
| funktioniert ohne GitHub    | basiert auf Git           |
| kann offline genutzt werden | benötigt Netzwerkzugriff  |

Ein Repository kann also Git verwenden, ohne jemals auf GitHub gespeichert zu werden.

---

## Repository

Ein Repository ist ein Projekt, das von Git verwaltet wird.

Ein neues Repository kann erstellt werden mit:

```bash
git init
```

Beispiel:

```bash
mkdir testprojekt
cd testprojekt
git init
```

Git erstellt dabei im Hintergrund ein verstecktes Verzeichnis:

```text
.git/
```

Dieses Verzeichnis enthält die Git-Daten des Repositorys.

Dazu gehören unter anderem:

- Commit-Historie
- Branch-Informationen
- Konfiguration
- Referenzen
- Git-Objekte

Das `.git`-Verzeichnis sollte nicht manuell gelöscht oder verändert werden, wenn man nicht genau weiß, was man tut.

Wird `.git` gelöscht, bleiben die normalen Projektdateien erhalten, aber die Git-Historie dieses lokalen Repositorys geht verloren.

---

## Prüfen, ob man in einem Git-Repository ist

Ein sehr wichtiger Befehl ist:

```bash
git status
```

Wenn man sich in einem Repository befindet, zeigt Git Informationen zum aktuellen Zustand.

Beispiel:

```text
On branch main
nothing to commit, working tree clean
```

Wenn man sich nicht in einem Git-Repository befindet, erscheint eine Fehlermeldung ähnlich wie:

```text
fatal: not a git repository
```

Deshalb ist `git status` einer der Befehle, die man bei Unsicherheit zuerst verwenden sollte.

---

## Working Directory

Das Working Directory ist der Bereich, in dem die normalen Projektdateien liegen und bearbeitet werden.

Beispiel:

```text
projekt/
├── README.md
├── docker-compose.yml
├── scripts/
└── docs/
```

Wenn eine Datei geändert wird, erkennt Git diese Änderung.

Beispiel:

```bash
git status
```

Mögliche Ausgabe:

```text
modified: README.md
```

Die Datei wurde geändert, aber die Änderung wurde noch nicht als Commit gespeichert.

---

## Untracked Files

Neue Dateien, die Git noch nicht kennt, werden als `untracked` angezeigt.

Beispiel:

```bash
touch test.txt
git status
```

Git kann dann zum Beispiel anzeigen:

```text
Untracked files:
  test.txt
```

Das bedeutet:

Die Datei existiert im Projektverzeichnis, wird aber noch nicht von Git verfolgt.

Um sie für einen Commit vorzubereiten:

```bash
git add test.txt
```

---

## Tracked Files

Tracked bedeutet, dass eine Datei bereits von Git verfolgt wird.

Eine getrackte Datei kann verschiedene Zustände haben.

Zum Beispiel:

- unverändert
- geändert
- für einen Commit vorgemerkt
- gelöscht

Den aktuellen Zustand zeigt:

```bash
git status
```

---

## Staging Area

Die Staging Area ist ein Zwischenbereich vor einem Commit.

Mit:

```bash
git add DATEI
```

wird eine Änderung für den nächsten Commit vorbereitet.

Beispiel:

```bash
git add README.md
```

Mehrere Dateien können gleichzeitig hinzugefügt werden:

```bash
git add README.md setup.sh
```

Alle Änderungen im aktuellen Verzeichnis und seinen Unterverzeichnissen:

```bash
git add .
```

Wichtig:

`git add` lädt noch nichts auf GitHub hoch.

Der Befehl bereitet Änderungen nur für den nächsten lokalen Commit vor.

---

## Warum gibt es die Staging Area?

Die Staging Area ermöglicht es, gezielt auszuwählen, welche Änderungen in einen Commit gehören.

Beispiel:

Man hat drei Dateien geändert:

```text
README.md
setup.sh
notes.txt
```

Aber nur `README.md` und `setup.sh` sollen in den nächsten Commit.

Dann kann man verwenden:

```bash
git add README.md setup.sh
```

`notes.txt` bleibt außerhalb des Commits.

Dadurch können Commits sauberer strukturiert werden.

---

## Commit

Ein Commit speichert einen Projektstand in der Git-Historie.

Beispiel:

```bash
git commit -m "Add installation documentation"
```

Ein Commit enthält unter anderem:

- gespeicherte Änderungen
- Commit-Nachricht
- Autor
- Zeitpunkt
- Referenz auf vorherige Commits

Jeder Commit erhält außerdem eine eindeutige ID.

Beispiel:

```text
b35e7ba
```

Das ist eine verkürzte Darstellung eines längeren Git-Hashes.

---

## Commit-Nachrichten

Eine Commit-Nachricht sollte kurz beschreiben, was geändert wurde.

Gute Beispiele:

```text
Add Linux networking chapter
Fix Docker port documentation
Update Git README
Add backup script
```

Weniger hilfreich sind Nachrichten wie:

```text
update
stuff
test
changes
asdf
```

Eine verständliche Commit-Historie erleichtert später die Fehlersuche.

---

## Änderungen vor dem Commit prüfen

Vor einem Commit sollte man normalerweise zuerst prüfen:

```bash
git status
```

Danach kann man sich Änderungen genauer ansehen:

```bash
git diff
```

`git diff` zeigt Änderungen, die noch nicht in der Staging Area liegen.

Beispiel:

```diff
- Alte Beschreibung
+ Neue Beschreibung
```

Danach kann die gewünschte Datei hinzugefügt werden:

```bash
git add README.md
```

Anschließend erneut prüfen:

```bash
git status
```

Und danach committen:

```bash
git commit -m "Update README"
```

---

## Git speichert Änderungen als Historie

Mehrere Commits ergeben eine Projekt-Historie.

Beispiel:

```text
A --- B --- C --- D
```

Dabei könnte jeder Buchstabe einen Commit darstellen.

Zum Beispiel:

```text
A  Initial commit
B  Add README
C  Add installation script
D  Fix configuration
```

Git kann dadurch frühere Zustände nachvollziehen.

---

## Historie anzeigen

Mit:

```bash
git log
```

zeigt Git die Commit-Historie an.

Eine kompaktere Darstellung erhält man mit:

```bash
git log --oneline
```

Beispiel:

```text
b35e7ba Add Git and GitHub section README
1eaaef0 Add Linux system administration practice chapter
91a1c20 Add Linux shell scripting chapter
```

Das ist besonders praktisch, wenn man schnell die letzten Commits sehen möchte.

---

## Was ist ein Branch?

Ein Branch ist eine Entwicklungslinie innerhalb eines Repositorys.

Der Hauptbranch heißt häufig:

```text
main
```

Branches ermöglichen es, Änderungen getrennt vom Hauptstand zu entwickeln.

Beispiel:

```text
main
  │
  ├── Commit A
  ├── Commit B
  │
  └──── feature-branch
          ├── Commit C
          └── Commit D
```

Das Thema Branches wird später ausführlicher behandelt.

---

## HEAD

`HEAD` zeigt in Git auf den aktuell ausgecheckten Stand.

Normalerweise zeigt `HEAD` auf den aktuellen Branch.

Beispiel:

```text
HEAD -> main
```

Das bedeutet:

Der Benutzer arbeitet aktuell auf dem Branch `main`.

Welcher Branch aktiv ist, kann unter anderem angezeigt werden mit:

```bash
git branch
```

Beispiel:

```text
* main
```

Der Stern zeigt den aktuell aktiven Branch.

---

## Lokales Repository

Das lokale Repository befindet sich auf dem eigenen Computer.

Hier können Änderungen vorbereitet und Commits erstellt werden.

Typische lokale Befehle:

```bash
git status
git add
git commit
git log
git diff
git branch
```

Diese Aktionen benötigen normalerweise keine Verbindung zu GitHub.

---

## Remote-Repository

Ein Remote-Repository liegt auf einem anderen System.

Das kann zum Beispiel sein:

- GitHub
- GitLab
- eigener Git-Server
- Firmenserver

Ein häufig verwendeter Name für das Haupt-Remote ist:

```text
origin
```

Remote-Repositories anzeigen:

```bash
git remote -v
```

Beispiel:

```text
origin  git@github.com:username/projekt.git (fetch)
origin  git@github.com:username/projekt.git (push)
```

Die genauen Remote-Befehle werden in einem späteren Kapitel behandelt.

---

## Repository klonen

Ein vorhandenes Git-Repository kann mit `git clone` kopiert werden.

Beispiel:

```bash
git clone git@github.com:username/projekt.git
```

Dabei werden normalerweise:

- Projektdateien
- Commit-Historie
- Branch-Informationen
- Remote-Konfiguration

lokal erstellt.

Danach kann man in das Repository wechseln:

```bash
cd projekt
```

Und den Zustand prüfen:

```bash
git status
```

---

## git init und git clone

Diese beiden Befehle haben unterschiedliche Aufgaben.

| Befehl      | Verwendung                         |
| ----------- | ---------------------------------- |
| `git init`  | neues lokales Repository erstellen |
| `git clone` | vorhandenes Repository kopieren    |

Beispiel für ein neues Projekt:

```bash
mkdir projekt
cd projekt
git init
```

Beispiel für ein vorhandenes Projekt:

```bash
git clone git@github.com:username/projekt.git
```

Normalerweise verwendet man nicht `git init`, nachdem ein Repository bereits korrekt mit `git clone` erstellt wurde.

---

## Git-Konfiguration

Git speichert Informationen über den Benutzer, der Commits erstellt.

Prüfen:

```bash
git config user.name
git config user.email
```

Globale Konfiguration anzeigen:

```bash
git config --global --list
```

Benutzer global setzen:

```bash
git config --global user.name "Name"
git config --global user.email "mail@example.com"
```

Bei mehreren Git-Identitäten kann die Konfiguration auch pro Repository oder Verzeichnis unterschiedlich sein.

Das wird später im Kapitel zu SSH und mehreren GitHub-Konten genauer behandelt.

---

## Lokale und globale Konfiguration

Git kennt verschiedene Konfigurationsebenen.

| Ebene  | Bedeutung                       |
| ------ | ------------------------------- |
| System | gilt für das gesamte System     |
| Global | gilt für den aktuellen Benutzer |
| Local  | gilt nur für ein Repository     |

Lokale Konfiguration anzeigen:

```bash
git config --local --list
```

Globale Konfiguration anzeigen:

```bash
git config --global --list
```

Eine lokale Einstellung kann eine globale Einstellung überschreiben.

Das ist zum Beispiel hilfreich, wenn unterschiedliche Git-Identitäten verwendet werden.

---

## Hilfe zu Git-Befehlen

Git besitzt eine eingebaute Hilfe.

Beispiel:

```bash
git help status
```

Oder:

```bash
git status --help
```

Kurze Hilfe:

```bash
git status -h
```

Das funktioniert auch mit anderen Git-Befehlen.

Zum Beispiel:

```bash
git commit -h
git branch -h
git log -h
```

---

## Typischer einfacher Workflow

Eine Datei wurde bearbeitet.

Zuerst prüfen:

```bash
git status
```

Änderungen ansehen:

```bash
git diff
```

Datei für Commit vorbereiten:

```bash
git add README.md
```

Status erneut prüfen:

```bash
git status
```

Commit erstellen:

```bash
git commit -m "Update README"
```

Historie prüfen:

```bash
git log --oneline
```

Wenn ein Remote-Repository vorhanden ist:

```bash
git push
```

---

## Beispiel: Neue Dokumentationsdatei

Neue Datei erstellen:

```bash
touch dokumentation.md
```

Git erkennt sie zunächst als untracked:

```bash
git status
```

Dann:

```bash
git add dokumentation.md
```

Status erneut prüfen:

```bash
git status
```

Commit:

```bash
git commit -m "Add documentation"
```

Danach:

```bash
git status
```

Bei einem sauberen Repository erscheint:

```text
nothing to commit, working tree clean
```

---

## Beispiel: Bestehende Datei ändern

Eine bereits getrackte Datei wird bearbeitet.

Danach:

```bash
git status
```

Git zeigt sie als verändert an.

Änderung ansehen:

```bash
git diff
```

Danach:

```bash
git add README.md
git commit -m "Update project description"
```

Damit wird die neue Version in der Historie gespeichert.

---

## `git status` als wichtiger Kontrollbefehl

`git status` sollte sehr häufig verwendet werden.

Zum Beispiel:

```bash
git status
```

vor:

```bash
git add
```

nach:

```bash
git add
```

und nach:

```bash
git commit
```

Damit sieht man jederzeit, in welchem Zustand sich das Repository befindet.

Das hilft besonders dabei, Fehler früh zu erkennen.

---

## Git arbeitet mit Verzeichnispfaden

Viele Git-Befehle beziehen sich auf den aktuellen Arbeitsort im Terminal.

Beispiel:

Das Repository liegt unter:

```text
~/github/private/fisi-lernwiki
```

Man befindet sich bereits in:

```text
~/github/private/fisi-lernwiki/git-github
```

Dann kann man eine Datei dort so hinzufügen:

```bash
git add README.md
```

Wenn man sich dagegen im Repository-Hauptverzeichnis befindet:

```text
~/github/private/fisi-lernwiki
```

lautet der Pfad:

```bash
git add git-github/README.md
```

Deshalb ist es wichtig zu wissen, in welchem Verzeichnis man sich befindet.

Prüfen:

```bash
pwd
```

---

## Nützliche Grundbefehle

| Befehl                 | Bedeutung                                  |
| ---------------------- | ------------------------------------------ |
| `pwd`                  | aktuelles Verzeichnis anzeigen             |
| `git init`             | neues Git-Repository erstellen             |
| `git clone URL`        | vorhandenes Repository kopieren            |
| `git status`           | aktuellen Repository-Zustand anzeigen      |
| `git add DATEI`        | Datei zur Staging Area hinzufügen          |
| `git add .`            | Änderungen im aktuellen Bereich hinzufügen |
| `git commit -m "Text"` | Commit erstellen                           |
| `git diff`             | nicht gestagte Änderungen anzeigen         |
| `git log`              | Commit-Historie anzeigen                   |
| `git log --oneline`    | kompakte Historie anzeigen                 |
| `git branch`           | Branches anzeigen                          |
| `git remote -v`        | Remote-Repositories anzeigen               |
| `git config --list`    | Git-Konfiguration anzeigen                 |
| `git help BEFEHL`      | Hilfe zu einem Git-Befehl anzeigen         |

---

## Typische Fehler

| Fehler                                 | Problem                                         |
| -------------------------------------- | ----------------------------------------------- |
| falsches Verzeichnis                   | Dateipfade stimmen nicht                        |
| `git status` nicht prüfen              | aktueller Zustand ist unklar                    |
| `git add` vergessen                    | Änderung landet nicht im Commit                 |
| falsche Datei mit `git add` hinzufügen | unerwünschte Änderung wird vorbereitet          |
| unklare Commit-Nachricht               | Historie wird schwer verständlich               |
| Git und GitHub verwechseln             | lokales und Remote-System werden nicht getrennt |
| `.git` löschen                         | lokale Repository-Historie geht verloren        |
| `git init` im falschen Ordner          | unerwünschtes Repository entsteht               |
| sensible Daten committen               | Sicherheitsrisiko                               |
| jeden Befehl blind kopieren            | falscher Pfad oder Branch kann verwendet werden |
| `git add .` ohne Kontrolle             | eventuell werden zu viele Dateien hinzugefügt   |

---

## Praktische Beispiele

### Beispiel 1: Prüfen, wo man sich befindet

```bash
pwd
git status
```

Damit prüft man zuerst das aktuelle Verzeichnis und anschließend den Git-Zustand.

### Beispiel 2: Eine Markdown-Datei committen

```bash
git status
git diff
git add docs/linux.md
git status
git commit -m "Add Linux documentation"
```

Damit wird nur die gewünschte Datei für den Commit vorbereitet.

### Beispiel 3: Letzte Commits anzeigen

```bash
git log --oneline
```

Damit sieht man schnell die Commit-Historie.

### Beispiel 4: Repository prüfen

```bash
git status
git branch
git remote -v
```

Damit sieht man:

- aktuellen Zustand
- aktiven Branch
- konfigurierte Remote-Repositories

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Git ein nützliches Werkzeug für viele technische Aufgaben.

Typische Einsatzbereiche sind:

- Bash-Skripte versionieren
- Python-Skripte verwalten
- Konfigurationsdateien dokumentieren
- Dockerfiles speichern
- Docker-Compose-Dateien verwalten
- technische Dokumentationen pflegen
- Automatisierung nachvollziehbar entwickeln
- Änderungen an Infrastruktur dokumentieren
- gemeinsam an Projekten arbeiten
- Fehler über ältere Versionen nachvollziehen

Auch in DevOps-Umgebungen ist Git ein zentrales Werkzeug.

Viele Technologien und Arbeitsweisen bauen auf Git auf.

Dazu gehören zum Beispiel:

- CI/CD
- Infrastructure as Code
- Ansible
- Terraform
- GitOps
- automatisierte Deployments

Für den Einstieg ist besonders wichtig, die grundlegende Kette sicher zu verstehen:

```text
Working Directory
      ↓
Staging Area
      ↓
Commit
      ↓
Remote-Repository
```

---

## Kurze Zusammenfassung

Git ist ein verteiltes Versionskontrollsystem.

Ein mit Git verwaltetes Projekt wird Repository genannt.

Die normalen Dateien befinden sich im Working Directory. Mit `git add` werden ausgewählte Änderungen in die Staging Area übernommen. Mit `git commit` werden diese Änderungen dauerhaft in der lokalen Git-Historie gespeichert.

`git status` ist einer der wichtigsten Git-Befehle, weil damit jederzeit der aktuelle Zustand eines Repositorys geprüft werden kann.

Mit `git diff` können Änderungen kontrolliert und mit `git log` frühere Commits angezeigt werden.

Git arbeitet lokal und benötigt für viele Funktionen keine Internetverbindung. Plattformen wie GitHub ergänzen Git um Remote-Repositories und Funktionen zur Zusammenarbeit.

Für Fachinformatiker für Systemintegration ist Git besonders für Skripte, Konfigurationen, Dokumentationen, Automatisierung und moderne Infrastrukturprojekte wichtig.
````
