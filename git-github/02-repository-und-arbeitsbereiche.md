# 2. Repository und Arbeitsbereiche

In diesem Kapitel geht es um Repositories und die Arbeitsbereiche von Git.

Ein Git-Repository ist ein Projektordner, der von Git verwaltet wird. Git speichert darin nicht nur Dateien, sondern auch die komplette Änderungshistorie. Damit Git Änderungen sauber speichern kann, arbeitet Git mit verschiedenen Bereichen: dem Working Directory, der Staging Area und dem lokalen Repository.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Fehler bei Git entstehen, wenn man nicht versteht, in welchem Bereich sich eine Änderung gerade befindet.

---

## Kurz erklärt

Git arbeitet nicht sofort mit jeder Datei gleich.

Eine Datei kann sich in verschiedenen Zuständen befinden:

- untracked
- modified
- staged
- committed

Die wichtigsten Arbeitsbereiche sind:

| Bereich           | Bedeutung                                              |
| ----------------- | ------------------------------------------------------ |
| Working Directory | aktueller Projektordner, in dem man Dateien bearbeitet |
| Staging Area      | vorbereitete Änderungen für den nächsten Commit        |
| Repository        | gespeicherte Git-Historie mit Commits                  |
| Remote Repository | entfernte Kopie, zum Beispiel auf GitHub               |

Ein typischer Ablauf:

```bash
git status
git add datei.md
git commit -m "Add chapter"
git push
```

Dabei wandert eine Änderung vom Working Directory in die Staging Area, dann in das lokale Repository und danach optional zu GitHub.

---

## Was ist ein Repository?

Ein Repository ist ein Projekt, das von Git verwaltet wird.

Ein Repository enthält:

- Projektdateien
- Ordnerstruktur
- Git-Historie
- Commits
- Branches
- Konfiguration
- Informationen über Remotes

Ein Git-Repository erkennt man am versteckten Ordner:

```text
.git
```

Anzeigen:

```bash
ls -la
```

Wenn ein Ordner `.git` enthält, ist dieser Ordner ein Git-Repository.

Wichtig:

Der `.git`-Ordner enthält die interne Git-Datenbank. Man sollte ihn nicht manuell bearbeiten oder löschen.

---

## Lokales Repository

Ein lokales Repository liegt auf dem eigenen Rechner.

Beispiel:

```text
/home/bilgin/github/private/fisi-lernwiki
```

Dort kann man Dateien bearbeiten, Commits erstellen und die Historie ansehen.

Lokale Git-Befehle funktionieren auch ohne Internet:

```bash
git status
git add README.md
git commit -m "Update README"
git log
git diff
```

Erst für GitHub-Funktionen wie `push` oder `pull` braucht man eine Verbindung zum Remote.

---

## Remote Repository

Ein Remote Repository ist eine entfernte Version des Repositories.

Bei GitHub liegt das Remote Repository online.

Remotes anzeigen:

```bash
git remote -v
```

Beispiel:

```text
origin  git@github.com:user/repository.git (fetch)
origin  git@github.com:user/repository.git (push)
```

`origin` ist der Standardname für das Haupt-Remote.

Ein Remote ist wichtig für:

- Backup auf GitHub
- Zusammenarbeit im Team
- Pull Requests
- Projektveröffentlichung
- Synchronisation zwischen Geräten

---

## Working Directory

Das Working Directory ist der normale Projektordner, in dem man arbeitet.

Hier bearbeitet man Dateien mit VS Code, nano oder anderen Programmen.

Beispiel:

```text
fisi-lernwiki/
├── README.md
├── linux/
├── git-github/
└── lernfelder/
```

Wenn man eine Datei verändert, passiert die Änderung zuerst im Working Directory.

Git weiß dann:

```text
Diese Datei wurde geändert, aber noch nicht für einen Commit vorbereitet.
```

Prüfen:

```bash
git status
```

---

## Staging Area

Die Staging Area ist der Vorbereitungsbereich für den nächsten Commit.

Mit `git add` legt man Änderungen in die Staging Area.

Beispiel:

```bash
git add git-github/02-repository-und-arbeitsbereiche.md
```

Danach ist diese Datei für den nächsten Commit vorgemerkt.

Die Staging Area ist nützlich, weil man genau auswählen kann, welche Änderungen in einen Commit sollen.

Beispiel:

Man hat drei Dateien geändert, möchte aber nur eine Datei committen:

```bash
git add README.md
git commit -m "Update README"
```

Die anderen Änderungen bleiben im Working Directory.

---

## Lokales Repository

Das lokale Repository enthält die gespeicherten Commits.

Ein Commit entsteht mit:

```bash
git commit -m "Add repository chapter"
```

Nach dem Commit ist die Änderung lokal gespeichert.

Wichtig:

Ein Commit ist nach diesem Schritt noch nicht automatisch auf GitHub.

Dafür braucht man:

```bash
git push
```

Git unterscheidet also zwischen lokal speichern und online hochladen.

---

## Remote Repository auf GitHub

Mit `git push` werden lokale Commits zu GitHub hochgeladen.

```bash
git push
```

Mit `git pull` holt man Änderungen von GitHub.

```bash
git pull
```

Typischer Ablauf:

```bash
git status
git add datei.md
git commit -m "Add chapter"
git push
```

Wenn jemand anderes oder man selbst über GitHub direkt etwas geändert hat, muss man vor dem Push eventuell zuerst pullen.

---

## Die drei wichtigsten Bereiche

Die drei wichtigsten Git-Bereiche kann man so sehen:

```text
Working Directory -> Staging Area -> Local Repository -> Remote Repository
```

Dazu passen diese Befehle:

| Richtung                           | Befehl       |
| ---------------------------------- | ------------ |
| Working Directory zu Staging Area  | `git add`    |
| Staging Area zu lokalem Repository | `git commit` |
| lokales Repository zu Remote       | `git push`   |
| Remote zu lokalem Repository       | `git pull`   |

Diese Struktur ist eine der wichtigsten Grundlagen von Git.

Viele Git-Probleme werden einfacher, wenn man versteht, in welchem Bereich die Änderung gerade liegt.

---

## Datei-Zustände

Dateien können verschiedene Zustände haben.

| Zustand   | Bedeutung                                      |
| --------- | ---------------------------------------------- |
| untracked | Git kennt die Datei noch nicht                 |
| modified  | Datei wurde geändert                           |
| staged    | Änderung ist für Commit vorgemerkt             |
| committed | Änderung ist im lokalen Repository gespeichert |
| pushed    | Commit wurde zum Remote hochgeladen            |

Beispiel:

Eine neue Datei wird erstellt:

```bash
touch notes.md
```

Dann ist sie zuerst:

```text
untracked
```

Nach:

```bash
git add notes.md
```

ist sie:

```text
staged
```

Nach:

```bash
git commit -m "Add notes"
```

ist sie:

```text
committed
```

Nach:

```bash
git push
```

ist sie auch auf GitHub.

---

## git status verstehen

`git status` zeigt den aktuellen Zustand.

```bash
git status
```

Typische Ausgaben:

```text
Untracked files:
  git-github/02-repository-und-arbeitsbereiche.md
```

Das bedeutet:

Die Datei existiert, aber Git verfolgt sie noch nicht.

```text
Changes not staged for commit:
  modified: README.md
```

Das bedeutet:

Die Datei wurde geändert, aber noch nicht mit `git add` vorgemerkt.

```text
Changes to be committed:
  modified: README.md
```

Das bedeutet:

Die Änderung ist staged und bereit für den Commit.

---

## git add gezielt nutzen

Man kann einzelne Dateien gezielt vormerken.

```bash
git add README.md
```

Oder mehrere Dateien:

```bash
git add README.md git-github/README.md
```

Oder einen ganzen Ordner:

```bash
git add git-github/
```

Oder alles im aktuellen Ordner:

```bash
git add .
```

Wichtig:

`git add .` ist praktisch, aber man sollte vorher immer `git status` prüfen.

Sonst können versehentlich falsche Dateien im Commit landen.

---

## Warum nicht immer blind `git add .`?

`git add .` nimmt alle Änderungen im aktuellen Ordner auf.

Das kann problematisch sein, wenn zum Beispiel diese Dateien dabei sind:

- temporäre Dateien
- Logs
- private Notizen
- Testdateien
- `.env`
- versehentlich erzeugte Dateien
- private Screenshots
- falsche Änderungen

Besserer Ablauf:

```bash
git status
git add gewünschte-datei.md
git status
git commit -m "Add chapter"
```

Bei kleinen, kontrollierten Änderungen ist `git add .` okay. Trotzdem sollte man wissen, was man addet.

---

## git diff vor dem Commit

Mit `git diff` sieht man Änderungen, die noch nicht staged sind.

```bash
git diff
```

Für eine bestimmte Datei:

```bash
git diff README.md
```

Staged Änderungen anzeigen:

```bash
git diff --staged
```

Das ist sehr wichtig vor einem Commit.

So sieht man, ob die Änderung wirklich korrekt ist.

Guter Ablauf:

```bash
git status
git diff
git add datei.md
git diff --staged
git commit -m "Add chapter"
```

---

## Dateien aus der Staging Area entfernen

Wenn man eine Datei versehentlich staged hat:

```bash
git restore --staged datei.md
```

Beispiel:

```bash
git restore --staged private-notes.md
```

Die Datei bleibt im Working Directory geändert, ist aber nicht mehr für den Commit vorgemerkt.

Das ist nützlich, wenn man einen Commit sauber halten möchte.

---

## Änderungen im Working Directory verwerfen

Wenn man eine Änderung nicht behalten möchte:

```bash
git restore datei.md
```

Beispiel:

```bash
git restore README.md
```

Wichtig:

Dieser Befehl löscht lokale Änderungen an dieser Datei.

Vorher sollte man prüfen:

```bash
git diff README.md
```

Wenn man die Änderung vielleicht noch braucht, sollte man sie nicht sofort verwerfen.

---

## Neue Dateien und gelöschte Dateien

Git erkennt auch neue und gelöschte Dateien.

Neue Datei:

```bash
touch new-file.md
git status
```

Gelöschte Datei:

```bash
rm old-file.md
git status
```

Die Löschung muss ebenfalls committed werden:

```bash
git add old-file.md
git commit -m "Remove old file"
```

Oder allgemein:

```bash
git add .
git commit -m "Update files"
```

Wichtig:

Auch das Löschen einer Datei ist eine Änderung in Git.

---

## Umbenennen und Verschieben

Dateien können mit `mv` umbenannt oder verschoben werden.

Beispiel:

```bash
mv old-name.md new-name.md
```

Git erkennt das oft als Umbenennung, besonders wenn der Inhalt ähnlich bleibt.

Danach:

```bash
git status
git add old-name.md new-name.md
git commit -m "Rename file"
```

Oder einfacher:

```bash
git add .
git commit -m "Rename file"
```

Es gibt auch:

```bash
git mv old-name.md new-name.md
```

Das führt Verschieben und Staging zusammen aus.

---

## .gitignore und Arbeitsbereiche

Die Datei `.gitignore` bestimmt, welche Dateien Git ignorieren soll.

Beispiel:

```gitignore
*.log
.env
.venv/
__pycache__/
private/
```

Wichtig:

`.gitignore` wirkt hauptsächlich auf untracked Dateien.

Wenn eine Datei bereits von Git verfolgt wird, wird sie nicht automatisch ignoriert.

Dann muss man sie aus dem Tracking entfernen:

```bash
git rm --cached datei
```

Beispiel:

```bash
git rm --cached .env
```

Danach sollte `.env` in `.gitignore` stehen.

---

## Tracked und untracked

Git unterscheidet zwischen tracked und untracked Dateien.

| Zustand   | Bedeutung                        |
| --------- | -------------------------------- |
| tracked   | Datei ist Git bekannt            |
| untracked | Datei ist Git noch nicht bekannt |

Eine tracked Datei kann modified, staged oder committed sein.

Eine untracked Datei wird erst durch `git add` in Git aufgenommen.

Prüfen:

```bash
git status
```

---

## Repository-Wurzel finden

Manchmal ist man in einem Unterordner eines Repositories.

Beispiel:

```text
~/github/private/fisi-lernwiki/git-github
```

Git-Befehle funktionieren dort trotzdem, weil Git die Repository-Wurzel findet.

Wurzel anzeigen:

```bash
git rev-parse --show-toplevel
```

Beispielausgabe:

```text
/home/bilgin/github/private/fisi-lernwiki
```

Das ist nützlich, wenn man nicht sicher ist, in welchem Repository man gerade arbeitet.

---

## Aktuellen Branch prüfen

`git status` zeigt den aktuellen Branch.

```bash
git status
```

Beispiel:

```text
On branch main
```

Alternativ:

```bash
git branch
```

Der aktuelle Branch ist mit `*` markiert.

Beispiel:

```text
* main
```

Das ist wichtig, weil Commits immer auf dem aktuellen Branch erstellt werden.

---

## Lokale Konfiguration im Repository

Ein Repository kann eigene Git-Konfiguration haben.

Anzeigen:

```bash
git config --local --list
```

Wichtige Werte:

```bash
git config user.name
git config user.email
git remote -v
```

Das ist besonders wichtig, wenn man mehrere GitHub-Konten oder verschiedene Arbeitsbereiche nutzt.

Beispiel:

- private Repositories
- Schul-Repositories
- Firmen-Repositories

Lokale Konfiguration kann globale Konfiguration überschreiben.

---

## Typischer Ablauf in einem Repo

Ein sauberer Ablauf:

```bash
cd ~/github/private/fisi-lernwiki

git status
git add git-github/02-repository-und-arbeitsbereiche.md
git status
git commit -m "Add Git repository and working areas chapter"
git push
git status
```

Am Ende sollte stehen:

```text
nothing to commit, working tree clean
```

Das bedeutet:

- alle Änderungen sind committed
- nichts ist offen
- Arbeitsverzeichnis ist sauber

---

## Wenn Push abgelehnt wird

Manchmal wird `git push` abgelehnt.

Typischer Grund:

Auf GitHub gibt es Änderungen, die lokal noch nicht vorhanden sind.

Dann sieht man oft eine Meldung wie:

```text
rejected
fetch first
```

Saubere Lösung:

```bash
git pull --rebase origin main
git push
```

Bedeutung:

- zuerst Änderungen von GitHub holen
- eigene Commits sauber danach anwenden
- dann erneut pushen

Wichtig:

Vor solchen Befehlen immer `git status` prüfen.

---

## Sauberer Arbeitsstand

Ein sauberer Arbeitsstand bedeutet:

```text
nothing to commit, working tree clean
```

Das ist ein guter Zustand nach einem fertigen Arbeitsschritt.

Prüfen:

```bash
git status
```

Ein sauberer Arbeitsstand ist wichtig, bevor man:

- Branch wechselt
- Pull macht
- größere Änderungen beginnt
- Fehler analysiert
- neuen Arbeitsblock startet

---

## Typische Fehler

| Fehler                                  | Problem                                          |
| --------------------------------------- | ------------------------------------------------ |
| im falschen Ordner arbeiten             | Git-Befehle wirken nicht auf das gewünschte Repo |
| `.git`-Ordner löschen                   | Historie und Git-Verwaltung gehen verloren       |
| `git add .` blind nutzen                | falsche Dateien landen im Commit                 |
| `git status` ignorieren                 | man kennt den Zustand nicht                      |
| Staging Area nicht verstehen            | Commits enthalten falsche Änderungen             |
| Commit und Push verwechseln             | Änderung ist lokal, aber nicht auf GitHub        |
| `.gitignore` zu spät nutzen             | private oder unnötige Dateien werden getrackt    |
| lokale und remote Änderungen vermischen | Push wird abgelehnt oder Konflikte entstehen     |
| Branch nicht prüfen                     | Commit landet auf falschem Branch                |
| Änderungen verwerfen ohne Prüfung       | Arbeit geht verloren                             |

---

## Praktische Beispiele

### Beispiel 1: Neue Datei sauber committen

```bash
touch git-github/example.md
git status
git add git-github/example.md
git commit -m "Add example file"
git push
```

Die Datei geht durch alle Bereiche: untracked, staged, committed, pushed.

### Beispiel 2: Änderung ansehen und committen

```bash
git status
git diff README.md
git add README.md
git diff --staged
git commit -m "Update README"
git push
```

So sieht man vor dem Commit genau, was gespeichert wird.

### Beispiel 3: Datei aus Staging Area entfernen

```bash
git add private-notes.md
git restore --staged private-notes.md
```

Die Datei ist danach nicht mehr für den Commit vorgemerkt.

### Beispiel 4: Repository-Wurzel finden

```bash
pwd
git rev-parse --show-toplevel
```

Damit prüft man, in welchem Repository man arbeitet.

---

## Nützliche Befehle

| Befehl                          | Bedeutung                                     |
| ------------------------------- | --------------------------------------------- |
| `git status`                    | aktuellen Zustand anzeigen                    |
| `git add datei`                 | Datei in Staging Area legen                   |
| `git add .`                     | alle Änderungen im aktuellen Ordner vormerken |
| `git commit -m "Text"`          | staged Änderungen lokal speichern             |
| `git push`                      | lokale Commits zum Remote hochladen           |
| `git pull`                      | Änderungen vom Remote holen                   |
| `git diff`                      | nicht staged Änderungen anzeigen              |
| `git diff --staged`             | staged Änderungen anzeigen                    |
| `git restore datei`             | lokale Änderungen verwerfen                   |
| `git restore --staged datei`    | Datei aus Staging Area entfernen              |
| `git remote -v`                 | Remote-Repositories anzeigen                  |
| `git branch`                    | Branches anzeigen                             |
| `git rev-parse --show-toplevel` | Repository-Wurzel anzeigen                    |
| `git config --local --list`     | lokale Git-Konfiguration anzeigen             |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist das Verständnis von Repositories und Arbeitsbereichen wichtig.

In der Praxis bedeutet das:

- Dokumentationen sauber versionieren
- Skripte kontrolliert ändern
- Konfigurationsbeispiele nachvollziehbar speichern
- GitHub-Projekte ordentlich pflegen
- Änderungen vor dem Commit prüfen
- private Dateien vom Repository fernhalten
- lokale und entfernte Repositories unterscheiden
- Fehler bei Pull und Push besser verstehen
- mit mehreren Projekten und Konten sauber arbeiten

Ein guter FISI nutzt Git nicht nur als Befehlssammlung, sondern versteht, wo eine Änderung gerade liegt und was der nächste sinnvolle Schritt ist.

---

## Kurze Zusammenfassung

Ein Git-Repository ist ein Projektordner mit Git-Historie.

Git arbeitet mit mehreren Bereichen: Working Directory, Staging Area, lokalem Repository und Remote Repository.

Wichtige Befehle sind `git status`, `git add`, `git commit`, `git push`, `git pull`, `git diff`, `git restore`, `git remote -v` und `git rev-parse --show-toplevel`.

Für FISI ist dieses Kapitel wichtig, weil sauberes Arbeiten mit Git hilft, Dokumentation, Skripte, Konfigurationen und Projekte nachvollziehbar zu verwalten.
