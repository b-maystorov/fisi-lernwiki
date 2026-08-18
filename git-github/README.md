# Git & GitHub

In diesem Bereich sammle ich Grundlagen und praxisnahe Arbeitsweisen rund um Git und GitHub.

Git wird in der Softwareentwicklung, Systemadministration und im DevOps-Umfeld eingesetzt, um Änderungen an Dateien nachvollziehbar zu speichern und gemeinsam an Projekten zu arbeiten.

Für Fachinformatiker für Systemintegration ist Git besonders nützlich für Skripte, Konfigurationsdateien, Dokumentationen, Automatisierung und Infrastrukturprojekte.

---

## Kurz erklärt

Git ist ein verteiltes Versionskontrollsystem.

Damit können Änderungen an Dateien gespeichert, verglichen und bei Bedarf wiederhergestellt werden.

GitHub ist eine Plattform, auf der Git-Repositories zentral gespeichert und gemeinsam bearbeitet werden können.

Wichtige Themen sind:

- Git-Repositories
- Working Directory
- Staging Area
- Commits
- Branches
- Merge
- Remote-Repositories
- Pull und Push
- GitHub
- Pull Requests
- `.gitignore`
- SSH
- Konflikte
- Wiederherstellung
- Zusammenarbeit
- typische Git-Workflows

---

## Inhalte

| Kapitel                                       | Thema                             |
| --------------------------------------------- | --------------------------------- |
| [01](01-git-grundlagen.md)                    | Git Grundlagen                    |
| [02](02-repository-und-arbeitsbereiche.md)    | Repository und Arbeitsbereiche    |
| [03](03-commits-und-historie.md)              | Commits und Historie              |
| [04](04-branches-und-merge.md)                | Branches und Merge                |
| [05](05-remotes-pull-und-push.md)             | Remotes, Pull und Push            |
| [06](06-github-und-zusammenarbeit.md)         | GitHub und Zusammenarbeit         |
| [07](07-gitignore-und-dateiverwaltung.md)     | `.gitignore` und Dateiverwaltung  |
| [08](08-fehlersuche-und-wiederherstellung.md) | Fehlersuche und Wiederherstellung |
| [09](09-ssh-und-mehrere-github-konten.md)     | SSH und mehrere GitHub-Konten     |
| [10](10-git-workflows-in-der-praxis.md)       | Git-Workflows in der Praxis       |

---

## Warum Git wichtig ist

Ohne Versionskontrolle werden Änderungen häufig direkt an Dateien vorgenommen.

Dadurch entstehen schnell Probleme:

- alte Versionen gehen verloren
- Änderungen sind schwer nachvollziehbar
- mehrere Personen überschreiben gegenseitig ihre Arbeit
- Fehler können nur schwer rückgängig gemacht werden
- Konfigurationsänderungen sind schlecht dokumentiert
- verschiedene Dateiversionen werden manuell gespeichert

Typische Dateinamen wie:

```text
config-neu.conf
config-neu2.conf
config-final.conf
config-final-wirklich.conf
```

sind kein sinnvoller Ersatz für Versionskontrolle.

Mit Git können Änderungen als einzelne Commits gespeichert werden.

Dadurch entsteht eine nachvollziehbare Historie.

---

## Git und GitHub sind nicht dasselbe

Git und GitHub werden häufig zusammen verwendet, sind aber unterschiedliche Dinge.

| Git                             | GitHub                                      |
| ------------------------------- | ------------------------------------------- |
| Versionskontrollsystem          | Plattform für Git-Repositories              |
| läuft lokal auf dem Computer    | läuft als Online-Dienst                     |
| verwaltet Commits und Branches  | stellt Repositories zentral bereit          |
| benötigt kein GitHub            | basiert auf Git                             |
| funktioniert auch ohne Internet | ermöglicht Zusammenarbeit über das Internet |

Git kann vollständig lokal verwendet werden.

Beispiel:

```bash
git init
git add .
git commit -m "Initial commit"
```

Dafür wird noch kein GitHub-Konto benötigt.

GitHub wird wichtig, wenn ein Repository zentral gespeichert oder gemeinsam genutzt werden soll.

---

## Typischer Git-Ablauf

Ein einfacher Git-Workflow sieht so aus:

```text
Datei ändern
     ↓
git status
     ↓
git diff
     ↓
git add
     ↓
git commit
     ↓
git pull
     ↓
git push
```

Nicht jeder Workflow sieht exakt so aus.

Die grundlegende Idee bleibt aber ähnlich:

1. Änderungen durchführen
2. Änderungen kontrollieren
3. gewünschte Dateien zum Commit vorbereiten
4. Commit erstellen
5. Änderungen mit dem Remote-Repository abgleichen
6. Änderungen hochladen

---

## Git im Administrationsbereich

Git wird nicht nur für Programmcode verwendet.

Auch Administratoren können Git für viele Dateien und Projekte einsetzen.

Beispiele:

- Bash-Skripte
- Python-Skripte
- Dockerfiles
- Docker-Compose-Dateien
- Ansible-Konfigurationen
- Terraform-Dateien
- Dokumentation
- Markdown-Dateien
- Konfigurationsvorlagen
- Installationsskripte
- Netzwerkdokumentation

Ein Repository kann zum Beispiel so aussehen:

```text
server-config/
├── README.md
├── scripts/
├── docker/
├── configs/
└── docs/
```

Änderungen können anschließend über Git dokumentiert werden.

---

## Wichtige Git-Befehle

| Befehl          | Bedeutung                                 |
| --------------- | ----------------------------------------- |
| `git init`      | neues Repository erstellen                |
| `git clone`     | Repository kopieren                       |
| `git status`    | aktuellen Zustand anzeigen                |
| `git add`       | Änderungen für einen Commit vormerken     |
| `git commit`    | Änderungen speichern                      |
| `git log`       | Commit-Historie anzeigen                  |
| `git diff`      | Änderungen vergleichen                    |
| `git branch`    | Branches anzeigen oder verwalten          |
| `git switch`    | Branch wechseln                           |
| `git merge`     | Branches zusammenführen                   |
| `git remote -v` | Remote-Repositories anzeigen              |
| `git fetch`     | Änderungen vom Remote abrufen             |
| `git pull`      | Remote-Änderungen abrufen und integrieren |
| `git push`      | lokale Commits hochladen                  |
| `git restore`   | Änderungen an Dateien zurücksetzen        |
| `git stash`     | Änderungen vorübergehend speichern        |

Die einzelnen Befehle werden in den folgenden Kapiteln genauer behandelt.

---

## Lokales und Remote-Repository

Ein Git-Projekt kann lokal und zusätzlich auf einem Remote-Server gespeichert sein.

Beispiel:

```text
Lokaler Computer
      │
      │ git push
      ▼
GitHub Repository
      ▲
      │ git pull
      │
anderer Computer
```

Das lokale Repository enthält die vollständige Git-Historie.

Das Remote-Repository dient unter anderem als:

- zentraler Austauschpunkt
- Backup zusätzlicher Repository-Kopien
- Grundlage für Zusammenarbeit
- Plattform für Pull Requests
- öffentliches Portfolio
- Dokumentationsplattform

---

## Änderungen kontrollieren

Vor einem Commit sollte geprüft werden, was tatsächlich geändert wurde.

Dafür sind besonders wichtig:

```bash
git status
```

und:

```bash
git diff
```

`git status` zeigt unter anderem:

- geänderte Dateien
- neue Dateien
- gelöschte Dateien
- Dateien in der Staging Area
- aktuellen Branch

`git diff` zeigt die tatsächlichen Änderungen innerhalb der Dateien.

Dadurch können versehentliche Änderungen erkannt werden, bevor sie gespeichert oder hochgeladen werden.

---

## Kleine und verständliche Commits

Ein Commit sollte möglichst eine zusammengehörige Änderung enthalten.

Beispiel:

```bash
git commit -m "Add Linux networking chapter"
```

Ein guter Commit beschreibt kurz, was geändert wurde.

Weniger sinnvoll:

```bash
git commit -m "stuff"
```

oder:

```bash
git commit -m "changes"
```

Eine verständliche Commit-Historie hilft später bei der Fehlersuche und Dokumentation.

---

## Branches

Branches ermöglichen parallele Entwicklungsstände innerhalb eines Repositorys.

Beispiel:

```text
main
  │
  ├── commit A
  ├── commit B
  │
  └──── feature-branch
          │
          ├── commit C
          └── commit D
```

Neue Funktionen oder größere Änderungen können zunächst in einem eigenen Branch entwickelt werden.

Nach erfolgreicher Prüfung können sie mit dem Hauptbranch zusammengeführt werden.

---

## Zusammenarbeit mit GitHub

GitHub erweitert Git um Funktionen für Zusammenarbeit.

Dazu gehören unter anderem:

- zentrale Repositories
- Pull Requests
- Code Reviews
- Issues
- Projektverwaltung
- Repository-Berechtigungen
- Actions
- Releases
- Dokumentation

Ein typischer Team-Workflow kann so aussehen:

```text
Repository klonen
      ↓
Branch erstellen
      ↓
Änderungen durchführen
      ↓
Commit erstellen
      ↓
Branch pushen
      ↓
Pull Request erstellen
      ↓
Review
      ↓
Merge
```

Dadurch können Änderungen geprüft werden, bevor sie in den Hauptbranch gelangen.

---

## Sicherheit

Nicht jede Datei gehört in ein Git-Repository.

Besonders sensible Daten sollten niemals veröffentlicht werden.

Dazu gehören zum Beispiel:

- Passwörter
- private SSH-Schlüssel
- API-Keys
- Tokens
- Zugangsdaten
- private Zertifikate
- interne vertrauliche Konfigurationen
- personenbezogene Daten

Solche Dateien können über `.gitignore` ausgeschlossen werden.

Beispiel:

```gitignore
.env
*.key
*.pem
secrets/
```

Wichtig:

`.gitignore` schützt keine Datei, die bereits in Git eingecheckt wurde.

Sensible Daten sollten deshalb bereits vor dem ersten Commit erkannt und ausgeschlossen werden.

---

## Git ersetzt kein Backup

Git speichert Dateiversionen und Änderungen sehr zuverlässig.

Trotzdem ist Git kein vollständiges Backup-System.

Ein Repository schützt zum Beispiel nicht automatisch:

- Datenbanken
- virtuelle Maschinen
- komplette Betriebssysteme
- laufende Server
- Binärdaten
- große Backup-Archive

Git ist hauptsächlich für versionierbare Dateien gedacht.

Ein Remote-Repository bietet eine zusätzliche Kopie des Projekts, ersetzt aber keine vollständige Backup-Strategie.

---

## Typische Fehler

| Fehler                             | Problem                                                |
| ---------------------------------- | ------------------------------------------------------ |
| `git status` nicht prüfen          | falsche Dateien können committed werden                |
| `git diff` nicht prüfen            | unerwünschte Änderungen bleiben unbemerkt              |
| sehr große Commits                 | Änderungen sind schwer nachvollziehbar                 |
| unklare Commit-Nachrichten         | Historie wird schwer verständlich                      |
| Passwörter committen               | Sicherheitsrisiko                                      |
| direkt auf `main` arbeiten         | bei Teamprojekten oft ungünstig                        |
| `pull` vergessen                   | lokale und entfernte Historie können auseinanderlaufen |
| falscher Branch                    | Änderungen landen an der falschen Stelle               |
| Merge-Konflikte ignorieren         | Code oder Konfiguration kann beschädigt werden         |
| `.gitignore` falsch verstehen      | bereits getrackte Dateien bleiben in Git               |
| `reset` ohne Verständnis verwenden | Commits oder Änderungen können verloren gehen          |

---

## Praktischer Einsatz

Dieses Lern-Wiki selbst ist ein Beispiel für einen Git-Workflow.

Bei einer neuen Dokumentation kann der Ablauf zum Beispiel so aussehen:

```bash
git status
```

Datei bearbeiten.

Danach:

```bash
git diff
```

Änderung vorbereiten:

```bash
git add pfad/zur/datei.md
```

Commit erstellen:

```bash
git commit -m "Add new documentation chapter"
```

Repository aktualisieren und Änderung hochladen:

```bash
git pull
git push
```

Damit wird nicht nur die aktuelle Datei gespeichert, sondern auch ihre Änderungshistorie dokumentiert.

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Git besonders bei Dokumentation, Automatisierung und modernen Infrastrukturprojekten nützlich.

Typische Einsatzbereiche sind:

- Skripte versionieren
- Konfigurationsdateien verwalten
- Änderungen dokumentieren
- gemeinsam an Projekten arbeiten
- Docker-Konfigurationen speichern
- Automatisierungsdateien verwalten
- Infrastruktur als Code verwenden
- Dokumentationen pflegen
- Fehler über die Versionshistorie nachvollziehen
- Änderungen vor der Übernahme prüfen

Git gehört außerdem zu vielen DevOps- und Cloud-Workflows.

Ein grundlegendes Verständnis von Git hilft deshalb auch bei späteren Themen wie CI/CD, Infrastructure as Code und automatisierter Systembereitstellung.

---

## Kurze Zusammenfassung

Git ist ein verteiltes Versionskontrollsystem zur Verwaltung von Dateien und Änderungen.

GitHub ist eine Plattform, auf der Git-Repositories zentral gespeichert und gemeinsam bearbeitet werden können.

Wichtige Git-Konzepte sind Repository, Working Directory, Staging Area, Commit, Branch, Merge und Remote.

Für die tägliche Arbeit sind Befehle wie `git status`, `git diff`, `git add`, `git commit`, `git pull` und `git push` besonders wichtig.

Für Fachinformatiker für Systemintegration ist Git ein nützliches Werkzeug für Skripte, Konfigurationen, Dokumentationen, Automatisierung und moderne Infrastrukturprojekte.
