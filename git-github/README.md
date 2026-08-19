# Git und GitHub

In diesem Bereich sammle ich Grundlagen und praktische Arbeitsweisen zu Git und GitHub.

Git ist ein Versionsverwaltungssystem. Damit kann man Änderungen an Dateien nachvollziehen, ältere Zustände wiederherstellen, mit Branches arbeiten und Projekte sauber dokumentieren. GitHub ist eine Plattform, auf der Git-Repositories online gespeichert, geteilt und gemeinsam bearbeitet werden können.

Für Fachinformatiker für Systemintegration ist Git wichtig, weil viele IT-Projekte, Skripte, Dokumentationen, Konfigurationen und Automatisierungen versioniert werden. Auch in Teams ist Git eine wichtige Grundlage, um Änderungen nachvollziehbar und kontrolliert durchzuführen.

---

## Ziel dieses Bereichs

Dieser Bereich soll Git und GitHub praxisnah erklären.

Es geht nicht nur darum, einzelne Befehle auswendig zu lernen. Wichtig ist zu verstehen, was Git im Hintergrund macht und wie man typische Situationen sauber löst.

Wichtige Ziele sind:

- Git-Grundlagen verstehen
- Repositories sicher nutzen
- Arbeitsbereiche von Git unterscheiden
- Änderungen sauber committen
- Branches erstellen und zusammenführen
- Remotes verstehen
- mit GitHub arbeiten
- Pull und Push richtig nutzen
- `.gitignore` sinnvoll einsetzen
- Fehler erkennen und beheben
- SSH-Zugriff verstehen
- mehrere GitHub-Konten sauber trennen
- sinnvolle Workflows im Alltag nutzen

---

## Kapitelübersicht

| Kapitel                                        | Thema                             |
| ---------------------------------------------- | --------------------------------- |
| [1](./01-git-grundlagen.md)                    | Git Grundlagen                    |
| [2](./02-repository-und-arbeitsbereiche.md)    | Repository und Arbeitsbereiche    |
| [3](./03-commits-und-historie.md)              | Commits und Historie              |
| [4](./04-branches-und-merge.md)                | Branches und Merge                |
| [5](./05-remotes-pull-und-push.md)             | Remotes, Pull und Push            |
| [6](./06-github-und-zusammenarbeit.md)         | GitHub und Zusammenarbeit         |
| [7](./07-gitignore-und-dateiverwaltung.md)     | `.gitignore` und Dateiverwaltung  |
| [8](./08-fehlersuche-und-wiederherstellung.md) | Fehlersuche und Wiederherstellung |
| [9](./09-ssh-und-mehrere-github-konten.md)     | SSH und mehrere GitHub-Konten     |
| [10](./10-git-workflows-in-der-praxis.md)      | Git-Workflows in der Praxis       |

---

## Was ist Git?

Git ist ein Werkzeug zur Versionsverwaltung.

Mit Git kann man Änderungen an Dateien speichern und später nachvollziehen.

Ein Git-Projekt besteht aus vielen gespeicherten Zuständen. Diese gespeicherten Zustände heißen Commits.

Ein Commit ist wie ein sauberer Zwischenstand eines Projekts.

Git hilft zum Beispiel bei Fragen wie:

- Was wurde geändert?
- Wann wurde etwas geändert?
- Wer hat etwas geändert?
- Warum wurde etwas geändert?
- Welche Datei war betroffen?
- Wie sah das Projekt vorher aus?
- Kann man eine Änderung rückgängig machen?

Git wird besonders häufig in Softwareentwicklung, DevOps, Dokumentation, Skripting und Infrastrukturprojekten genutzt.

---

## Was ist GitHub?

GitHub ist eine Online-Plattform für Git-Repositories.

Ein Repository kann lokal auf dem eigenen Rechner liegen und zusätzlich online auf GitHub gespeichert werden.

GitHub wird genutzt für:

- Quellcode
- Dokumentation
- Projektarbeit
- Zusammenarbeit im Team
- Issues
- Pull Requests
- Releases
- Wikis
- Portfolio-Projekte
- Open-Source-Projekte

GitHub ersetzt Git nicht.  
GitHub nutzt Git.

Der Unterschied ist wichtig:

| Begriff    | Bedeutung                                                     |
| ---------- | ------------------------------------------------------------- |
| Git        | Versionsverwaltung auf dem eigenen System                     |
| GitHub     | Online-Plattform für Git-Repositories                         |
| Repository | Projektordner mit Git-Historie                                |
| Remote     | entfernte Version eines Repositories, zum Beispiel auf GitHub |

---

## Warum Git wichtig ist

Ohne Git werden Änderungen oft unübersichtlich.

Typische schlechte Dateinamen ohne Versionsverwaltung:

```text
projekt-final.txt
projekt-final-neu.txt
projekt-final-wirklich-neu.txt
projekt-final-abgabe.txt
projekt-final-abgabe-korrektur.txt
```

Mit Git speichert man stattdessen klare Zwischenstände.

Beispiel:

```text
Add Linux README
Fix typo in Git chapter
Update Docker documentation
Add troubleshooting notes
```

Dadurch bleibt nachvollziehbar, was passiert ist.

Git ist besonders wichtig, wenn mehrere Personen an einem Projekt arbeiten oder wenn ein Projekt langfristig gepflegt wird.

---

## Grundidee von Git

Git arbeitet mit mehreren Bereichen.

Wichtige Begriffe:

| Begriff           | Bedeutung                                       |
| ----------------- | ----------------------------------------------- |
| Working Directory | aktueller Arbeitsordner mit Dateien             |
| Staging Area      | vorbereitete Änderungen für den nächsten Commit |
| Repository        | gespeicherte Git-Historie                       |
| Commit            | gespeicherter Projektstand                      |
| Branch            | Entwicklungszweig                               |
| Remote            | entfernte Kopie des Repositories                |
| Push              | lokale Commits zum Remote hochladen             |
| Pull              | Änderungen vom Remote holen und integrieren     |

Ein typischer Ablauf sieht so aus:

```bash
git status
git add datei.md
git commit -m "Add documentation"
git push
```

---

## Typischer Git-Ablauf

Ein einfacher Git-Arbeitsablauf:

```bash
git status
git add .
git commit -m "Describe change"
git push
```

Bedeutung:

| Befehl       | Aufgabe                              |
| ------------ | ------------------------------------ |
| `git status` | zeigt den aktuellen Zustand          |
| `git add`    | nimmt Änderungen in die Staging Area |
| `git commit` | speichert Änderungen lokal           |
| `git push`   | lädt Commits zu GitHub hoch          |

Wichtig:

Vor `git add` sollte man immer mit `git status` prüfen, welche Dateien geändert wurden.

Bei größeren Projekten ist es besser, gezielt Dateien zu adden statt immer blind `git add .` zu nutzen.

---

## Wichtige Git-Befehle

| Befehl                     | Bedeutung                                     |
| -------------------------- | --------------------------------------------- |
| `git status`               | aktuellen Zustand anzeigen                    |
| `git add datei`            | Datei für Commit vormerken                    |
| `git add .`                | alle Änderungen im aktuellen Ordner vormerken |
| `git commit -m "Text"`     | Commit mit Nachricht erstellen                |
| `git log`                  | Commit-Historie anzeigen                      |
| `git diff`                 | Änderungen anzeigen                           |
| `git branch`               | Branches anzeigen                             |
| `git switch branchname`    | Branch wechseln                               |
| `git switch -c branchname` | neuen Branch erstellen und wechseln           |
| `git merge branchname`     | Branch zusammenführen                         |
| `git remote -v`            | Remotes anzeigen                              |
| `git pull`                 | Änderungen vom Remote holen                   |
| `git push`                 | lokale Commits hochladen                      |
| `git restore datei`        | Änderungen an Datei verwerfen                 |
| `git stash`                | Änderungen kurzfristig weglegen               |
| `git clone url`            | Repository herunterladen                      |

Diese Befehle sind die Grundlage für die tägliche Arbeit mit Git.

---

## Commit-Nachrichten

Commit-Nachrichten sollten kurz und verständlich sein.

Gute Beispiele:

```text
Add Linux package management chapter
Update GitHub README
Fix typo in network chapter
Create Docker practice notes
Improve troubleshooting section
```

Weniger gute Beispiele:

```text
update
changes
stuff
final
fix
asdf
```

Eine gute Commit-Nachricht erklärt kurz, was geändert wurde.

Sie muss nicht extrem lang sein, aber sie sollte später noch verständlich sein.

---

## Branches

Ein Branch ist ein Entwicklungszweig.

Branches sind nützlich, wenn man an einer Änderung arbeiten möchte, ohne direkt den Hauptstand zu verändern.

Beispiel:

```bash
git switch -c update-readme
```

Danach arbeitet man auf dem neuen Branch.

Später kann der Branch wieder zusammengeführt werden.

Branches werden oft genutzt für:

- neue Features
- Fehlerbehebungen
- Tests
- Dokumentationsänderungen
- Teamarbeit
- Pull Requests

Der Hauptbranch heißt oft:

```text
main
```

oder älter:

```text
master
```

---

## Remotes

Ein Remote ist eine entfernte Version eines Repositories.

Bei GitHub ist das meistens das Repository auf github.com.

Remotes anzeigen:

```bash
git remote -v
```

Beispielausgabe:

```text
origin  git@github.com:user/repo.git (fetch)
origin  git@github.com:user/repo.git (push)
```

`origin` ist der Standardname für das Haupt-Remote.

Mit Remotes kann man lokale Arbeit mit GitHub synchronisieren.

---

## Pull und Push

`push` lädt lokale Commits zum Remote hoch.

```bash
git push
```

`pull` holt Änderungen vom Remote und integriert sie lokal.

```bash
git pull
```

Typische Situation:

Wenn auf GitHub direkt eine Datei geändert wurde und lokal auch Änderungen existieren, kann ein Push abgelehnt werden.

Dann muss man zuerst die entfernten Änderungen holen.

Beispiel:

```bash
git pull --rebase origin main
git push
```

Wichtig:

Man sollte Fehlermeldungen von Git genau lesen. Git sagt meistens ziemlich genau, warum ein Push oder Pull nicht funktioniert.

---

## `.gitignore`

Die Datei `.gitignore` legt fest, welche Dateien Git ignorieren soll.

Typische Dateien, die nicht ins Repository gehören:

- temporäre Dateien
- Logdateien
- lokale Editor-Dateien
- virtuelle Python-Umgebungen
- private Notizen
- Secrets
- Passwörter
- Build-Artefakte
- Cache-Dateien

Beispiel:

```gitignore
__pycache__/
*.pyc
.venv/
.env
.vscode/
*.log
```

Wichtig:

`.gitignore` schützt nicht automatisch Dateien, die bereits getrackt werden.

Wenn eine Datei schon im Repository ist, muss sie aktiv aus dem Tracking entfernt werden.

---

## GitHub und Zusammenarbeit

GitHub wird häufig für Teamarbeit genutzt.

Wichtige Funktionen:

| Funktion     | Bedeutung                                   |
| ------------ | ------------------------------------------- |
| Repository   | Projekt auf GitHub                          |
| Issue        | Aufgabe, Fehler oder Diskussion             |
| Pull Request | Vorschlag für Änderungen                    |
| Review       | Prüfung von Änderungen                      |
| Fork         | eigene Kopie eines fremden Repositories     |
| Star         | Markierung eines interessanten Repositories |
| README       | Startseite und Erklärung eines Projekts     |

In Teams arbeitet man oft nicht direkt auf `main`, sondern über Branches und Pull Requests.

Das macht Änderungen kontrollierbarer.

---

## SSH und GitHub

GitHub kann über HTTPS oder SSH genutzt werden.

Bei SSH arbeitet man mit Schlüsselpaaren:

- privater Schlüssel bleibt auf dem eigenen Rechner
- öffentlicher Schlüssel wird bei GitHub hinterlegt

SSH ist praktisch, weil man ohne Passwort-Eingabe pushen und pullen kann.

Prüfen kann man die Verbindung zum Beispiel mit:

```bash
ssh -T git@github.com
```

Bei mehreren GitHub-Konten muss die SSH-Konfiguration sauber getrennt werden.

Das ist besonders wichtig, wenn man private und schulische oder berufliche Repositories getrennt verwalten möchte.

---

## Git im FISI-Alltag

Git ist nicht nur für klassische Softwareentwicklung wichtig.

Für FISI kann Git genutzt werden für:

- Linux-Dokumentation
- Netzwerkdokumentation
- Skripte
- Docker-Projekte
- Konfigurationsbeispiele
- Home-Lab-Dokumentation
- Schulprojekte
- Projektberichte
- Automatisierungen
- Markdown-Wikis
- Infrastruktur-Dokumentation

Auch kleine Änderungen an Dokumentation oder Skripten sollten sauber versioniert werden.

So bleibt nachvollziehbar, was sich geändert hat.

---

## Typische Fehler beim Lernen von Git

| Fehler                                          | Problem                                  |
| ----------------------------------------------- | ---------------------------------------- |
| `git status` nicht nutzen                       | man weiß nicht, was geändert wurde       |
| zu große Commits machen                         | Änderungen sind schwer nachvollziehbar   |
| schlechte Commit-Nachrichten                    | Historie wird unverständlich             |
| blind `git add .` nutzen                        | ungewollte Dateien landen im Commit      |
| Pull und Push verwechseln                       | Synchronisation wird unklar              |
| direkt auf GitHub und lokal gleichzeitig ändern | Konflikte oder abgelehnte Pushes         |
| `.gitignore` zu spät erstellen                  | unnötige Dateien werden bereits getrackt |
| Branches nicht verstehen                        | Teamarbeit wird schwer                   |
| Fehlermeldungen nicht lesen                     | einfache Probleme wirken kompliziert     |
| private Daten committen                         | Sicherheitsproblem                       |

---

## Sicher arbeiten mit Git

Gute Gewohnheiten:

1. Vor Änderungen Status prüfen:

```bash
git status
```

2. Änderungen ansehen:

```bash
git diff
```

3. Nur passende Dateien vormerken:

```bash
git add datei.md
```

4. Saubere Commit-Nachricht schreiben:

```bash
git commit -m "Add Git basics chapter"
```

5. Hochladen:

```bash
git push
```

6. Danach prüfen:

```bash
git status
```

Das Ziel ist ein sauberer Arbeitsstand:

```text
nothing to commit, working tree clean
```

---

## Kurze Zusammenfassung

Git ist ein Versionsverwaltungssystem. Damit können Änderungen gespeichert, verglichen und wiederhergestellt werden.

GitHub ist eine Plattform, um Git-Repositories online zu speichern und gemeinsam daran zu arbeiten.

Wichtige Grundlagen sind Repository, Working Directory, Staging Area, Commit, Branch, Remote, Pull, Push, `.gitignore`, SSH und Pull Requests.

Für Fachinformatiker für Systemintegration ist Git wichtig, weil Dokumentation, Skripte, Konfigurationen und Projekte nachvollziehbar versioniert werden müssen.
