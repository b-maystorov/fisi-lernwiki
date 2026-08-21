# Git-Befehle Cheatsheet

Dieses Cheatsheet enthält wichtige Git-Befehle für die tägliche Arbeit mit Repositories, Commits, Branches, Remotes und GitHub.

Die ausführlichen Erklärungen stehen im Bereich [Git & GitHub](../git-github/).

---

## Grundlegende Prüfung

| Befehl                  | Bedeutung                                |
| ----------------------- | ---------------------------------------- |
| `git status`            | zeigt aktuellen Zustand des Repositories |
| `git log`               | zeigt Commit-Historie                    |
| `git log --oneline`     | zeigt Historie kompakt                   |
| `git diff`              | zeigt nicht vorgemerkte Änderungen       |
| `git diff --staged`     | zeigt vorgemerkte Änderungen             |
| `git branch`            | zeigt lokale Branches                    |
| `git remote -v`         | zeigt verbundene Remotes                 |
| `git config user.name`  | zeigt Git-Benutzername                   |
| `git config user.email` | zeigt Git-E-Mail                         |

Beispiel:

```bash
git status
git log --oneline -5
git remote -v
```

---

## Repository erstellen und klonen

| Befehl                                       | Bedeutung                             |
| -------------------------------------------- | ------------------------------------- |
| `git init`                                   | erstellt neues lokales Git-Repository |
| `git clone url`                              | lädt ein Repository herunter          |
| `git clone git@github.com:user/repo.git`     | klont Repository über SSH             |
| `git clone https://github.com/user/repo.git` | klont Repository über HTTPS           |

Beispiel:

```bash
mkdir projekt
cd projekt
git init
```

Oder:

```bash
git clone git@github.com:user/repository.git
cd repository
git status
```

---

## Dateien vormerken und committen

| Befehl                         | Bedeutung                                     |
| ------------------------------ | --------------------------------------------- |
| `git add datei`                | merkt eine Datei für Commit vor               |
| `git add ordner/`              | merkt ganzen Ordner vor                       |
| `git add .`                    | merkt alle Änderungen im aktuellen Ordner vor |
| `git commit -m "Text"`         | erstellt Commit mit Nachricht                 |
| `git commit --amend`           | ändert letzten Commit                         |
| `git commit --amend -m "Text"` | ändert letzte Commit-Nachricht                |

Beispiel:

```bash
git status
git add README.md
git commit -m "Update README"
```

Wichtig:

Vor `git add .` immer prüfen:

```bash
git status
```

---

## Änderungen prüfen

| Befehl                     | Bedeutung                                    |
| -------------------------- | -------------------------------------------- |
| `git diff`                 | zeigt Änderungen, die noch nicht staged sind |
| `git diff datei`           | zeigt Änderungen einer Datei                 |
| `git diff --staged`        | zeigt Änderungen in der Staging Area         |
| `git show`                 | zeigt letzten Commit                         |
| `git show commit-id`       | zeigt bestimmten Commit                      |
| `git show commit-id:datei` | zeigt alte Version einer Datei               |

Beispiel:

```bash
git diff README.md
git add README.md
git diff --staged
```

---

## Dateien zurücknehmen

| Befehl                       | Bedeutung                                      |
| ---------------------------- | ---------------------------------------------- |
| `git restore datei`          | verwirft lokale Änderung an Datei              |
| `git restore .`              | verwirft lokale Änderungen im aktuellen Ordner |
| `git restore --staged datei` | entfernt Datei aus Staging Area                |
| `git rm datei`               | löscht Datei lokal und aus Git                 |
| `git rm --cached datei`      | entfernt Datei aus Git, behält sie lokal       |
| `git mv alt neu`             | benennt Datei um oder verschiebt sie           |

Beispiel:

```bash
git restore --staged notes.md
git restore README.md
```

Vorsicht:

```bash
git restore .
```

kann lokale Arbeit verwerfen.

---

## Branches

| Befehl                 | Bedeutung                                 |
| ---------------------- | ----------------------------------------- |
| `git branch`           | zeigt lokale Branches                     |
| `git branch -a`        | zeigt lokale und Remote-Branches          |
| `git branch -vv`       | zeigt Branches mit Upstream               |
| `git switch branch`    | wechselt zu Branch                        |
| `git switch -c branch` | erstellt neuen Branch und wechselt hinein |
| `git branch -d branch` | löscht gemergten Branch                   |
| `git branch -D branch` | löscht Branch erzwungen                   |
| `git merge branch`     | merged Branch in aktuellen Branch         |

Beispiel:

```bash
git switch -c add-readme
git add README.md
git commit -m "Update README"
git switch main
git merge add-readme
```

Wichtig:

Merge passiert immer in den aktuellen Branch hinein.

---

## Remotes

| Befehl                            | Bedeutung                             |
| --------------------------------- | ------------------------------------- |
| `git remote -v`                   | zeigt Remotes                         |
| `git remote add origin url`       | fügt Remote hinzu                     |
| `git remote set-url origin url`   | ändert Remote-Adresse                 |
| `git remote remove origin`        | entfernt Remote                       |
| `git push`                        | lädt Commits hoch                     |
| `git pull`                        | holt Änderungen vom Remote            |
| `git fetch`                       | holt Remote-Infos ohne direkten Merge |
| `git push -u origin branch`       | pusht neuen Branch und setzt Upstream |
| `git push origin --delete branch` | löscht Remote-Branch                  |

Beispiel:

```bash
git remote -v
git push
```

Bei neuem Branch:

```bash
git push -u origin add-readme
```

---

## Pull und Push

| Befehl                          | Bedeutung                                                  |
| ------------------------------- | ---------------------------------------------------------- |
| `git push`                      | lokale Commits zu GitHub hochladen                         |
| `git pull`                      | Änderungen von GitHub holen und integrieren                |
| `git pull origin main`          | main von origin holen                                      |
| `git pull --rebase origin main` | Remote-Änderungen holen und eigene Commits danach anwenden |
| `git fetch origin`              | Änderungen vom Remote nur holen                            |
| `git status`                    | zeigt ahead/behind Zustand                                 |

Beispiel bei abgelehntem Push:

```bash
git status
git pull --rebase origin main
git push
```

---

## Historie ansehen

| Befehl                            | Bedeutung                    |
| --------------------------------- | ---------------------------- |
| `git log`                         | vollständige Historie        |
| `git log --oneline`               | kompakte Historie            |
| `git log --oneline -5`            | letzte fünf Commits          |
| `git log --graph --oneline --all` | grafische Branch-Historie    |
| `git show`                        | Details zum letzten Commit   |
| `git show commit-id`              | Details zu bestimmtem Commit |
| `git reflog`                      | zeigt frühere HEAD-Zustände  |

Beispiel:

```bash
git log --oneline -10
git show
git reflog
```

---

## Stash

| Befehl                        | Bedeutung                                   |
| ----------------------------- | ------------------------------------------- |
| `git stash`                   | legt offene Änderungen kurz weg             |
| `git stash push -m "Text"`    | legt Änderungen mit Nachricht weg           |
| `git stash list`              | zeigt Stashes                               |
| `git stash pop`               | holt letzten Stash zurück und entfernt ihn  |
| `git stash apply`             | holt Stash zurück, behält ihn aber in Liste |
| `git stash show -p stash@{0}` | zeigt Inhalt eines Stashes                  |
| `git stash drop stash@{0}`    | löscht bestimmten Stash                     |
| `git stash clear`             | löscht alle Stashes                         |

Beispiel:

```bash
git stash push -m "temporary changes"
git switch main
git pull
git stash pop
```

---

## Konflikte

| Befehl                  | Bedeutung                             |
| ----------------------- | ------------------------------------- |
| `git status`            | zeigt Konfliktdateien                 |
| `git merge --abort`     | bricht Merge ab                       |
| `git rebase --abort`    | bricht Rebase ab                      |
| `git rebase --continue` | setzt Rebase nach Konfliktlösung fort |
| `git add datei`         | markiert Konflikt als gelöst          |
| `grep -R "<<<<<<<" .`   | sucht Konfliktmarker                  |

Typische Konfliktmarker:

```text
<<<<<<< HEAD
eigene Version
=======
andere Version
>>>>>>> branchname
```

Ablauf bei Merge-Konflikt:

```bash
git status
# Datei öffnen und Konflikt lösen
git add datei.md
git commit
```

Ablauf bei Rebase-Konflikt:

```bash
git status
# Datei öffnen und Konflikt lösen
git add datei.md
git rebase --continue
```

---

## Rückgängig machen

| Befehl                       | Bedeutung                                                |
| ---------------------------- | -------------------------------------------------------- |
| `git restore datei`          | lokale Änderung verwerfen                                |
| `git restore --staged datei` | Datei aus Staging Area entfernen                         |
| `git revert commit-id`       | macht Commit durch neuen Commit rückgängig               |
| `git reset --soft HEAD~1`    | nimmt letzten Commit zurück, Änderungen bleiben staged   |
| `git reset --mixed HEAD~1`   | nimmt letzten Commit zurück, Änderungen bleiben unstaged |
| `git reset --hard HEAD~1`    | nimmt letzten Commit zurück und verwirft Änderungen      |
| `git reflog`                 | hilft, alte Zustände wiederzufinden                      |

Vorsicht:

```bash
git reset --hard
```

kann Arbeit löschen.

Für öffentliche oder geteilte Repositories ist oft sicherer:

```bash
git revert commit-id
```

---

## `.gitignore`

| Befehl / Datei              | Bedeutung                                          |
| --------------------------- | -------------------------------------------------- |
| `.gitignore`                | Datei mit Ignore-Regeln                            |
| `git check-ignore -v datei` | zeigt, warum Datei ignoriert wird                  |
| `git rm --cached datei`     | entfernt getrackte Datei aus Git, behält sie lokal |
| `git status`                | zeigt untracked und ignored Verhalten indirekt     |
| `git clean -n`              | Vorschau für untracked Dateien                     |
| `git clean -f`              | löscht untracked Dateien                           |

Beispiel `.gitignore`:

```gitignore
.env
*.log
__pycache__/
.venv/
.vscode/
private/
```

Bereits getrackte Datei entfernen:

```bash
git rm --cached .env
git add .gitignore
git commit -m "Stop tracking env file"
```

---

## Git-Konfiguration

| Befehl                                  | Bedeutung                       |
| --------------------------------------- | ------------------------------- |
| `git config --list`                     | zeigt Git-Konfiguration         |
| `git config --global --list`            | zeigt globale Konfiguration     |
| `git config --local --list`             | zeigt lokale Repo-Konfiguration |
| `git config user.name`                  | zeigt aktuellen Namen           |
| `git config user.email`                 | zeigt aktuelle E-Mail           |
| `git config user.name "Name"`           | setzt lokalen Namen             |
| `git config user.email "mail"`          | setzt lokale E-Mail             |
| `git config --global user.name "Name"`  | setzt globalen Namen            |
| `git config --global user.email "mail"` | setzt globale E-Mail            |
| `git config --show-origin user.email`   | zeigt Quelle der Einstellung    |

Beispiel:

```bash
git config user.name
git config user.email
git config --show-origin user.email
```

---

## SSH und GitHub

| Befehl                                              | Bedeutung                    |
| --------------------------------------------------- | ---------------------------- |
| `ssh -T git@github.com`                             | testet GitHub-SSH            |
| `ssh -T git@github-private`                         | testet SSH-Alias             |
| `ssh-add -l`                                        | zeigt geladene SSH-Schlüssel |
| `ssh-add ~/.ssh/key`                                | fügt SSH-Schlüssel hinzu     |
| `git remote -v`                                     | prüft, ob Remote SSH nutzt   |
| `git remote set-url origin git@alias:user/repo.git` | setzt Remote auf SSH-Alias   |

Beispiel:

```bash
ssh -T git@github-private
git remote -v
```

Remote mit Alias:

```bash
git remote set-url origin git@github-private:user/repository.git
```

---

## Typische Arbeitsabläufe

### Neues Kapitel committen

```bash
git status
git add git-github/neues-kapitel.md
git commit -m "Add new Git chapter"
git push
git status
```

### Vor dem Commit sauber prüfen

```bash
git status
git diff
git add datei.md
git diff --staged
git commit -m "Clear message"
```

### Push wurde abgelehnt

```bash
git status
git pull --rebase origin main
git push
```

### Neuer Branch für Änderung

```bash
git switch main
git pull --rebase origin main
git switch -c add-new-section
```

Danach:

```bash
git add .
git commit -m "Add new section"
git push -u origin add-new-section
```

### Nach Merge Branch löschen

```bash
git switch main
git pull
git branch -d add-new-section
git push origin --delete add-new-section
```

---

## Gefährliche Befehle

| Befehl                         | Risiko                              |
| ------------------------------ | ----------------------------------- |
| `git reset --hard`             | verwirft Änderungen und Commits     |
| `git clean -fd`                | löscht untracked Dateien und Ordner |
| `git clean -fdx`               | löscht auch ignorierte Dateien      |
| `git push --force`             | überschreibt Remote-Historie        |
| `git branch -D branch`         | löscht Branch erzwungen             |
| `git rm datei`                 | löscht Datei lokal und aus Git      |
| `git commit --amend` nach Push | kann Remote-Historie komplizieren   |

Vor gefährlichen Befehlen prüfen:

```bash
git status
git log --oneline -5
git diff
git branch
git remote -v
```

---

## Häufige Probleme

| Problem             | Prüfung                 | Lösung                                           |
| ------------------- | ----------------------- | ------------------------------------------------ |
| Push abgelehnt      | `git status`            | `git pull --rebase origin main`, dann `git push` |
| Datei falsch staged | `git status`            | `git restore --staged datei`                     |
| Änderung soll weg   | `git diff`              | `git restore datei`                              |
| falscher Branch     | `git branch`            | `git switch richtiger-branch`                    |
| Remote falsch       | `git remote -v`         | `git remote set-url origin url`                  |
| falsche Identität   | `git config user.email` | lokale Git-Konfiguration setzen                  |
| SSH Fehler          | `ssh -T git@alias`      | Schlüssel, Alias und Remote prüfen               |
| Konflikt            | `git status`            | Datei lösen, adden, fortsetzen                   |
| Commit verloren     | `git reflog`            | alten Commit sichern                             |

---

## Gute Commit-Nachrichten

Gute Beispiele:

```text
Add Linux commands cheatsheet
Update Git README
Fix typo in SSH chapter
Add Docker troubleshooting notes
Improve network command overview
```

Schlechte Beispiele:

```text
update
fix
new
stuff
final
asdf
```

Eine gute Commit-Nachricht erklärt kurz, was der Commit macht.

---

## Kurze Zusammenfassung

Dieses Cheatsheet enthält wichtige Git-Befehle für Repository-Arbeit, Commits, Branches, Remotes, Pull, Push, Stash, Konflikte, `.gitignore`, SSH und Wiederherstellung.

Die wichtigsten Befehle für den Alltag sind:

```bash
git status
git diff
git add
git commit
git log --oneline
git branch
git switch
git pull --rebase origin main
git push
git remote -v
```

Für FISI ist Git wichtig, weil Dokumentation, Skripte, Konfigurationen und Projekte sauber versioniert werden können.
