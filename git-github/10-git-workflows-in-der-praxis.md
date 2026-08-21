# 10. Git-Workflows in der Praxis

In diesem Kapitel geht es um praktische Git-Workflows.

Ein Workflow beschreibt, wie man mit Git in einem Projekt regelmäßig arbeitet. Dabei geht es nicht nur um einzelne Befehle, sondern um eine sinnvolle Reihenfolge: Zustand prüfen, Änderungen machen, Änderungen kontrollieren, committen, pushen und den Arbeitsstand sauber halten.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Git in vielen praktischen Bereichen genutzt werden kann: Dokumentation, Skripte, Konfigurationen, Docker-Projekte, Linux-Notizen, Netzwerkdokumentation und Teamarbeit.

---

## Kurz erklärt

Ein Git-Workflow ist ein wiederholbarer Arbeitsablauf.

Ein einfacher Workflow sieht so aus:

```bash
git status
git pull --rebase origin main

# Dateien bearbeiten

git status
git diff
git add datei.md
git diff --staged
git commit -m "Add clear message"
git push
git status
```

Ziel ist ein sauberer Arbeitsstand:

```text
nothing to commit, working tree clean
```

Ein guter Workflow verhindert viele typische Git-Probleme.

---

## Warum Workflows wichtig sind

Git kann sehr viele Dinge tun. Ohne festen Ablauf wird die Arbeit schnell unübersichtlich.

Typische Probleme ohne Workflow:

- man arbeitet im falschen Repository
- man committet falsche Dateien
- man vergisst zu pushen
- lokale Arbeit ist nicht auf GitHub
- GitHub hat neue Änderungen, lokal aber nicht
- Branches werden verwechselt
- Konflikte entstehen unnötig
- private Dateien landen im Commit
- Commit-Nachrichten sind unklar
- der Arbeitsstand bleibt dauerhaft unordentlich

Ein Workflow ist deshalb wie eine Arbeitsroutine.

Man muss nicht bei jedem Projekt alles gleich machen, aber die Grundidee sollte immer sauber sein.

---

## Grundregeln für sauberes Arbeiten

Wichtige Grundregeln:

| Regel                      | Bedeutung                                   |
| -------------------------- | ------------------------------------------- |
| Erst prüfen, dann ändern   | mit `git status` und `git remote -v`        |
| Kleine Arbeitsschritte     | nicht zu viele Themen in einem Commit       |
| Klare Commit-Nachrichten   | später verständlich                         |
| Vor dem Commit diff prüfen | keine falschen Änderungen speichern         |
| Vor Push Remote prüfen     | besonders bei mehreren Konten               |
| Nach Push Status prüfen    | sauberer Endzustand                         |
| Keine privaten Daten       | Secrets, Tokens und Schlüssel nie committen |
| Fehlermeldungen lesen      | Git erklärt meistens den nächsten Schritt   |

Diese Regeln sind wichtiger als komplizierte Git-Befehle.

---

## Einfacher Einzelprojekt-Workflow

Bei kleinen eigenen Projekten arbeitet man oft direkt auf `main`.

Beispiel:

```bash
cd ~/github/private/fisi-lernwiki

git status
git pull --rebase origin main

# Datei bearbeiten

git status
git diff
git add git-github/10-git-workflows-in-der-praxis.md
git commit -m "Add Git workflows chapter"
git push
git status
```

Dieser Workflow passt gut für:

- Lern-Wikis
- kleine Dokumentationsprojekte
- einzelne README-Änderungen
- kleine Skriptprojekte
- persönliche Notizen ohne sensible Daten

Trotzdem sollte man auch bei Einzelprojekten sauber prüfen, was committed wird.

---

## Branch-Workflow

Bei größeren Änderungen ist ein eigener Branch sinnvoll.

Ablauf:

```bash
git switch main
git pull --rebase origin main
git switch -c add-new-chapter

# Dateien bearbeiten

git status
git diff
git add datei.md
git commit -m "Add new chapter"
git push -u origin add-new-chapter
```

Danach kann man:

- lokal mergen
- oder auf GitHub einen Pull Request öffnen

Ein Branch-Workflow ist sinnvoll bei:

- neuen Kapiteln
- größeren Umstrukturierungen
- Tests
- unsicheren Änderungen
- Teamarbeit
- Pull Requests

---

## Lokaler Merge-Workflow

Wenn man einen Branch lokal in `main` übernehmen möchte:

```bash
git switch main
git pull --rebase origin main
git merge add-new-chapter
git push
git branch -d add-new-chapter
```

Wichtig:

Man merged immer in den aktuellen Branch hinein.

Wenn Änderungen nach `main` sollen, muss man vorher auf `main` wechseln.

Prüfen:

```bash
git branch
git status
```

---

## Pull-Request-Workflow

In Teamprojekten oder professionelleren Projekten arbeitet man oft mit Pull Requests.

Ablauf im Terminal:

```bash
git switch main
git pull --rebase origin main
git switch -c fix-readme-links

# Datei bearbeiten

git status
git diff
git add README.md
git commit -m "Fix README links"
git push -u origin fix-readme-links
```

Danach auf GitHub:

1. Pull Request öffnen
2. Änderung beschreiben
3. Review abwarten
4. Kommentare bearbeiten
5. Pull Request mergen
6. Branch löschen

Pull Requests helfen, Änderungen sichtbar und prüfbar zu machen.

---

## Dokumentations-Workflow

Für Markdown-Dokumentation ist ein einfacher, sauberer Ablauf sehr wichtig.

Beispiel:

```bash
git status
git pull --rebase origin main

# Markdown-Datei in VS Code bearbeiten

git status
git diff
git add docs/installation.md
git commit -m "Update installation documentation"
git push
```

Gute Praxis:

- Datei im Browser oder Markdown-Preview prüfen
- Links kontrollieren
- Überschriften sinnvoll setzen
- Codeblöcke korrekt schließen
- keine privaten Daten einfügen
- Commit-Nachricht passend zum Inhalt schreiben

Bei Dokumentation ist nicht nur der Inhalt wichtig, sondern auch Lesbarkeit und Struktur.

---

## Skript-Workflow

Bei Skripten sollte man vor dem Commit testen.

Beispiel Shell-Skript:

```bash
git status

bash -n scripts/check-system.sh
chmod +x scripts/check-system.sh
./scripts/check-system.sh

git diff
git add scripts/check-system.sh
git commit -m "Add system check script"
git push
```

Bedeutung:

| Schritt          | Zweck                      |
| ---------------- | -------------------------- |
| `bash -n`        | Syntax prüfen              |
| `chmod +x`       | Skript ausführbar machen   |
| Skript ausführen | Verhalten testen           |
| `git diff`       | Änderung kontrollieren     |
| Commit           | getesteten Stand speichern |

Skripte sollten nicht blind committed werden, wenn sie noch nicht getestet wurden.

---

## Python-Projekt-Workflow

Bei Python-Projekten sollte man auf virtuelle Umgebungen und Cache-Dateien achten.

Typischer Ablauf:

```bash
git status

python3 main.py

git status
git diff
git add main.py README.md
git commit -m "Improve Python project structure"
git push
```

Wichtig:

Nicht committen:

```text
__pycache__/
*.pyc
.venv/
.env
```

Diese Dateien gehören normalerweise in `.gitignore`.

Bei Python-Projekten sollte die README erklären, wie man das Projekt startet.

---

## Docker-Projekt-Workflow

Bei Docker-Projekten sollte man Änderungen praktisch testen.

Beispiel:

```bash
git status

docker compose up -d
docker compose ps
docker compose logs
docker compose down

git diff
git add Dockerfile docker-compose.yml README.md
git commit -m "Update Docker setup"
git push
```

Gute Praxis:

- Container startet?
- Ports stimmen?
- README passt zur Compose-Datei?
- keine Passwörter im Repository?
- `.env` ignoriert?
- Beispielwerte statt echter Zugangsdaten?

Bei Docker-Projekten ist es wichtig, dass Dokumentation und Konfiguration zusammenpassen.

---

## Workflow mit mehreren Geräten

Wenn man auf mehreren Geräten arbeitet, muss man regelmäßig pullen und pushen.

Gerät 1:

```bash
git add README.md
git commit -m "Update README"
git push
```

Gerät 2 vor neuer Arbeit:

```bash
git status
git pull --rebase origin main
```

Regel:

```text
Vor neuer Arbeit auf einem anderen Gerät zuerst pullen.
```

Sonst arbeitet man schnell auf einem alten Stand und bekommt später Push-Probleme.

---

## Workflow mit mehreren GitHub-Konten

Bei mehreren GitHub-Konten muss man vor Push besonders prüfen.

Wichtige Befehle:

```bash
git remote -v
git config user.name
git config user.email
ssh -T git@github-private
ssh -T git@github-school
```

Prüfen:

| Frage                             | Befehl                                    |
| --------------------------------- | ----------------------------------------- |
| Bin ich im richtigen Repository?  | `pwd` und `git rev-parse --show-toplevel` |
| Nutze ich das richtige Remote?    | `git remote -v`                           |
| Nutze ich die richtige Identität? | `git config user.email`                   |
| Funktioniert SSH?                 | `ssh -T git@alias`                        |

Das ist besonders wichtig bei privaten, schulischen und beruflichen Repositories.

---

## Fork-Workflow

Bei einem Fork arbeitet man an einer eigenen Kopie eines fremden Repositories.

Typische Remotes:

| Remote     | Bedeutung           |
| ---------- | ------------------- |
| `origin`   | eigener Fork        |
| `upstream` | Original-Repository |

Ablauf:

```bash
git remote -v
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

Oder bei eigener Änderung:

```bash
git switch -c fix-docs
# Änderung machen
git add README.md
git commit -m "Fix documentation"
git push -u origin fix-docs
```

Danach öffnet man einen Pull Request zum Originalprojekt.

---

## Hotfix-Workflow

Ein Hotfix ist eine schnelle Fehlerbehebung.

Beispiel:

Ein Link in der README ist kaputt.

Ablauf:

```bash
git switch main
git pull --rebase origin main
git switch -c hotfix-readme-link

# Datei korrigieren

git diff
git add README.md
git commit -m "Fix README link"
git push -u origin hotfix-readme-link
```

Danach Pull Request öffnen oder lokal mergen.

Bei kleinen Einzelprojekten kann man den Hotfix auch direkt auf `main` machen.

In Teamprojekten ist ein Branch sauberer.

---

## Workflow vor jedem Commit

Vor jedem Commit sollte man diesen Ablauf nutzen:

```bash
git status
git diff
git add datei.md
git diff --staged
git commit -m "Clear message"
```

Warum?

| Schritt             | Nutzen                    |
| ------------------- | ------------------------- |
| `git status`        | zeigt betroffene Dateien  |
| `git diff`          | zeigt konkrete Änderungen |
| `git add`           | wählt Änderungen aus      |
| `git diff --staged` | prüft den nächsten Commit |
| `git commit`        | speichert den Stand       |

Das verhindert versehentliche Commits.

---

## Workflow vor jedem Push

Vor jedem Push:

```bash
git status
git log --oneline -3
git remote -v
git push
```

Bei mehreren Konten zusätzlich:

```bash
git config user.name
git config user.email
```

Wenn Push abgelehnt wird:

```bash
git status
git pull --rebase origin main
git push
```

Wichtig:

Nicht sofort Force Push nutzen.

Force Push sollte nur verwendet werden, wenn man genau versteht, warum es nötig ist.

---

## Workflow nach dem Push

Nach dem Push sollte man prüfen:

```bash
git status
```

Guter Endzustand:

```text
nothing to commit, working tree clean
```

Außerdem kann man auf GitHub prüfen:

- ist der Commit sichtbar?
- ist die Datei richtig formatiert?
- funktionieren Links?
- sieht die README sauber aus?
- wurden keine privaten Daten gepusht?

Gerade bei öffentlichen Repositories lohnt sich diese Prüfung.

---

## Saubere Commit-Strategie

Gute Commits sind logisch zusammenhängend.

Schlecht:

```text
Update everything
```

Besser:

```text
Add Git workflow chapter
Fix Linux README links
Update Docker troubleshooting notes
```

Ein Commit sollte möglichst ein Thema behandeln.

Gute Fragen vor einem Commit:

- Gehören diese Änderungen zusammen?
- Ist die Commit-Nachricht verständlich?
- Sind private Dateien ausgeschlossen?
- Wurde die Änderung getestet oder geprüft?
- Ist der Commit nicht zu groß?
- Kann man später verstehen, warum diese Änderung gemacht wurde?

---

## Gute Branch-Namen

Branch-Namen sollten kurz und verständlich sein.

Gute Beispiele:

```text
add-git-workflow-chapter
fix-readme-links
update-docker-docs
improve-linux-networking
hotfix-ssh-section
```

Schlecht:

```text
test
new
stuff
branch1
changes
asdf
```

Ein guter Branch-Name sagt, woran gearbeitet wird.

---

## Gute Pull-Request-Beschreibung

Ein Pull Request sollte kurz erklären, was geändert wurde.

Beispiel:

```text
## Änderung

Dieses PR ergänzt das Kapitel zu Git-Workflows.

## Inhalt

- einfacher Einzelprojekt-Workflow
- Branch-Workflow
- Pull-Request-Workflow
- Workflow für Dokumentation, Skripte und Docker-Projekte

## Prüfung

- Markdown-Struktur geprüft
- interne Links geprüft
- keine privaten Daten enthalten
```

Eine gute Beschreibung macht Reviews leichter.

---

## Konflikt-Workflow

Wenn ein Konflikt entsteht:

```bash
git status
```

Dann:

1. betroffene Datei öffnen
2. Konfliktmarker suchen
3. finalen Inhalt festlegen
4. Marker entfernen
5. Datei speichern
6. Datei adden
7. Merge oder Rebase fortsetzen

Bei Merge:

```bash
git add datei.md
git commit
```

Bei Rebase:

```bash
git add datei.md
git rebase --continue
```

Bei Unsicherheit abbrechen:

```bash
git merge --abort
```

oder:

```bash
git rebase --abort
```

---

## Stash-Workflow

Wenn man offene Änderungen kurz weglegen muss:

```bash
git stash push -m "temporary work"
```

Danach ist der Arbeitsstand meist sauber.

Später zurückholen:

```bash
git stash pop
```

Stashes anzeigen:

```bash
git stash list
```

Stash genauer prüfen:

```bash
git stash show -p stash@{0}
```

Stash ist nützlich vor:

- Branchwechsel
- Pull
- Rebase
- kurzfristigen Hotfixes
- Tests auf anderem Branch

---

## Release-Workflow

Bei fertigen Projektständen kann man Tags nutzen.

Beispiel:

```bash
git tag v1.0.0
git push origin v1.0.0
```

Ein Tag markiert einen bestimmten Commit.

Das ist sinnvoll für:

- stabile Versionen
- Projektabgaben
- Software-Releases
- wichtige Zwischenstände
- dokumentierte Projektstände

Für reine Lern-Wikis sind Tags nicht immer nötig.

Für Tools, Skripte oder Docker-Projekte können sie sinnvoll sein.

---

## Repository-Pflege

Ein Repository sollte regelmäßig gepflegt werden.

Dazu gehört:

- README aktuell halten
- alte Branches löschen
- `.gitignore` prüfen
- Links kontrollieren
- sensible Daten vermeiden
- klare Ordnerstruktur behalten
- Commit-Historie verständlich halten
- offene Issues prüfen
- Dokumentation an echte Projektstruktur anpassen
- veraltete Dateien entfernen

Ein gutes Repository wirkt nicht nur durch viel Inhalt professionell, sondern durch Ordnung.

---

## Checkliste vor einer größeren Änderung

Vor einer größeren Änderung:

```text
1. Bin ich im richtigen Repository?
2. Bin ich auf dem richtigen Branch?
3. Ist main aktuell?
4. Sollte ich einen neuen Branch erstellen?
5. Gibt es offene Änderungen?
6. Ist das Remote korrekt?
7. Ist die Git-Identität korrekt?
8. Gibt es private Dateien im Projekt?
9. Habe ich eine sinnvolle Commit-Strategie?
10. Kann ich die Änderung testen oder prüfen?
```

Dazu passende Befehle:

```bash
pwd
git rev-parse --show-toplevel
git branch
git status
git pull --rebase origin main
git remote -v
git config user.email
```

---

## Checkliste nach einer Änderung

Nach einer Änderung:

```text
1. Funktioniert die Änderung?
2. Ist die Dokumentation korrekt?
3. Wurden keine privaten Daten eingefügt?
4. Sind nur passende Dateien geändert?
5. Ist der Commit sinnvoll?
6. Wurde gepusht?
7. Ist GitHub aktuell?
8. Ist der Arbeitsstand sauber?
```

Befehle:

```bash
git status
git diff
git diff --staged
git log --oneline -3
git push
git status
```

---

## Typische Fehler in Workflows

| Fehler                         | Problem                                   |
| ------------------------------ | ----------------------------------------- |
| ohne `git status` arbeiten     | Zustand bleibt unklar                     |
| vor Arbeit nicht pullen        | lokaler Stand ist veraltet                |
| alles direkt auf `main` machen | größere Änderungen werden unübersichtlich |
| Branch nicht prüfen            | Commit landet falsch                      |
| zu große Commits               | Historie wird schwer lesbar               |
| schlechte Commit-Nachrichten   | spätere Prüfung wird schwer               |
| `git add .` blind nutzen       | falsche Dateien werden committed          |
| Push vergessen                 | GitHub ist nicht aktuell                  |
| falsches Remote nutzen         | Push geht zum falschen Repository         |
| private Daten pushen           | Sicherheitsproblem                        |
| Force Push ohne Grund          | Historie kann beschädigt werden           |
| nach Merge nicht aufräumen     | alte Branches sammeln sich                |

---

## Praktische Beispiele

### Beispiel 1: Kleines Dokumentationsupdate

```bash
cd ~/github/private/fisi-lernwiki

git status
git pull --rebase origin main

# README bearbeiten

git diff README.md
git add README.md
git commit -m "Update wiki overview"
git push
git status
```

Dieser Workflow passt für kleine Änderungen an Dokumentation.

---

### Beispiel 2: Neues Kapitel auf Branch

```bash
git switch main
git pull --rebase origin main
git switch -c add-git-workflows

# Datei bearbeiten

git status
git diff
git add git-github/10-git-workflows-in-der-praxis.md
git commit -m "Add Git workflows chapter"
git push -u origin add-git-workflows
```

Danach kann ein Pull Request auf GitHub erstellt werden.

---

### Beispiel 3: Push wurde abgelehnt

```bash
git status
git pull --rebase origin main
git push
```

Dieser Ablauf passt, wenn GitHub neue Änderungen hat, die lokal noch fehlen.

---

### Beispiel 4: Offene Arbeit kurz sichern

```bash
git status
git stash push -m "temporary documentation changes"
git switch main
git pull --rebase origin main
git stash pop
```

Dieser Workflow hilft, wenn man offene Änderungen hat, aber zuerst den aktuellen Stand holen oder den Branch wechseln muss.

---

## Nützliche Befehle

| Befehl                          | Bedeutung                        |
| ------------------------------- | -------------------------------- |
| `git status`                    | aktuellen Zustand prüfen         |
| `git pull --rebase origin main` | aktuellen Stand von GitHub holen |
| `git add datei`                 | Datei vormerken                  |
| `git diff`                      | Änderungen prüfen                |
| `git diff --staged`             | staged Änderungen prüfen         |
| `git commit -m "Text"`          | Commit erstellen                 |
| `git push`                      | Commits hochladen                |
| `git switch main`               | zu main wechseln                 |
| `git switch -c branch`          | neuen Branch erstellen           |
| `git merge branch`              | Branch zusammenführen            |
| `git branch -d branch`          | gemergten Branch löschen         |
| `git push -u origin branch`     | neuen Branch hochladen           |
| `git remote -v`                 | Remote prüfen                    |
| `git config user.email`         | Git-Identität prüfen             |
| `git stash push -m "Text"`      | Änderungen kurz sichern          |
| `git stash pop`                 | Stash zurückholen                |
| `git log --oneline -5`          | letzte Commits anzeigen          |
| `git tag v1.0.0`                | Version markieren                |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Git-Workflows wichtig, weil viele technische Aufgaben sauber dokumentiert und nachvollziehbar gepflegt werden müssen.

In der Praxis bedeutet das:

- Dokumentation strukturiert bearbeiten
- Linux- und Netzwerknotizen versionieren
- Skripte sicher weiterentwickeln
- Docker-Projekte prüfen und committen
- Konfigurationsbeispiele sauber verwalten
- private und schulische Repositories trennen
- Teamarbeit mit Branches und Pull Requests vorbereiten
- Fehler durch klare Arbeitsabläufe vermeiden
- GitHub als professionelles Portfolio nutzen
- Änderungen nachvollziehbar machen

Ein guter FISI nutzt Git nicht nur als Befehlssammlung, sondern arbeitet mit klaren Abläufen. Dadurch bleiben Projekte zuverlässig, verständlich und sicher.

---

## Kurze Zusammenfassung

Ein Git-Workflow ist ein wiederholbarer Ablauf für sauberes Arbeiten mit Git.

Wichtige Bestandteile sind `git status`, `git pull`, Änderungen bearbeiten, `git diff`, `git add`, `git commit`, `git push` und danach wieder `git status`.

Bei größeren Änderungen nutzt man Branches und Pull Requests. Bei kleinen Einzelprojekten kann ein einfacher Main-Workflow reichen.

Für FISI ist dieses Kapitel wichtig, weil Dokumentation, Skripte, Konfigurationen und technische Projekte nur dann professionell wirken, wenn sie sauber versioniert und gepflegt werden.
