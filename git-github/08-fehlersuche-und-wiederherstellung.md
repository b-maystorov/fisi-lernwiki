# 8. Fehlersuche und Wiederherstellung

In diesem Kapitel geht es um Fehlersuche und Wiederherstellung in Git.

Git hilft nicht nur beim Speichern von Änderungen, sondern auch beim Analysieren und Reparieren von Fehlern. Viele Git-Probleme wirken am Anfang kompliziert, sind aber lösbar, wenn man den Zustand sauber prüft und die Git-Meldungen genau liest.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil technische Arbeit oft aus Fehlersuche besteht: falscher Branch, abgelehnter Push, Merge-Konflikt, versehentlich geänderte Dateien, falsche Remote-Adresse oder gelöschte Änderungen.

---

## Kurz erklärt

Git-Fehlersuche bedeutet:

- aktuellen Zustand prüfen
- Fehlermeldung lesen
- Branch prüfen
- Remote prüfen
- Änderungen anzeigen
- Staging Area prüfen
- lokale Änderungen sichern
- Konflikte lösen
- falsche Änderungen zurücknehmen
- verlorene Commits suchen
- Arbeitsstand sauber machen

Wichtige Befehle:

```bash
git status
git diff
git log --oneline
git remote -v
git branch
git restore
git restore --staged
git stash
git revert
git reset
git reflog
```

Die wichtigste Regel ist:

```text
Nicht hektisch Befehle kopieren. Erst den Zustand verstehen.
```

---

## Erster Schritt: `git status`

Bei fast jedem Git-Problem ist der erste Befehl:

```bash
git status
```

`git status` zeigt:

- aktuellen Branch
- offene Änderungen
- staged Änderungen
- untracked Dateien
- Merge- oder Rebase-Zustand
- ahead/behind zum Remote
- Hinweise, welche Befehle möglich sind

Viele Git-Meldungen enthalten direkt Vorschläge.

Beispiel:

```text
use "git restore <file>..." to discard changes
use "git add <file>..." to update what will be committed
```

Diese Hinweise sollte man lesen, bevor man handelt.

---

## Zustand verstehen

Vor jeder Lösung sollte man wissen:

| Frage                          | Befehl                                             |
| ------------------------------ | -------------------------------------------------- |
| In welchem Repository bin ich? | `git rev-parse --show-toplevel`                    |
| Auf welchem Branch bin ich?    | `git branch` oder `git status`                     |
| Welche Dateien sind geändert?  | `git status`                                       |
| Was genau wurde geändert?      | `git diff`                                         |
| Was ist staged?                | `git diff --staged`                                |
| Welche Commits gibt es?        | `git log --oneline`                                |
| Welches Remote ist gesetzt?    | `git remote -v`                                    |
| Welche Identität nutzt Git?    | `git config user.name` und `git config user.email` |

Saubere Fehlersuche beginnt nicht mit Reparieren, sondern mit Prüfen.

---

## Arbeitsstand sichern, bevor man repariert

Wenn man unsicher ist, sollte man den aktuellen Stand nicht sofort löschen.

Möglichkeiten:

1. Änderungen committen, wenn sie sinnvoll sind:

```bash
git add datei.md
git commit -m "Save current work"
```

2. Änderungen kurzfristig weglegen:

```bash
git stash
```

3. Dateien manuell kopieren:

```bash
cp datei.md datei.md.backup
```

4. Aktuellen Zustand dokumentieren:

```bash
git status
git log --oneline -5
```

Gerade vor `reset`, `clean`, `restore` oder Konfliktlösungen sollte man vorsichtig sein.

---

## Änderungen anzeigen mit `git diff`

Wenn eine Datei geändert wurde, zeigt `git diff` die Änderung.

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

Das ist wichtig, bevor man Änderungen verwirft oder committed.

Ein guter Ablauf:

```bash
git status
git diff
git add datei.md
git diff --staged
git commit -m "Clear message"
```

So sieht man genau, was in den Commit kommt.

---

## Datei aus der Staging Area entfernen

Problem:

Eine Datei wurde mit `git add` vorgemerkt, soll aber nicht in den Commit.

Lösung:

```bash
git restore --staged datei.md
```

Beispiel:

```bash
git restore --staged private-notes.md
```

Die Datei bleibt im Working Directory geändert, ist aber nicht mehr staged.

Danach prüfen:

```bash
git status
```

Das ist ungefährlich für den Dateiinhalt, weil nur die Staging Area geändert wird.

---

## Lokale Änderung an Datei verwerfen

Problem:

Eine Datei wurde geändert, aber die Änderung soll weg.

Lösung:

```bash
git restore datei.md
```

Beispiel:

```bash
git restore README.md
```

Wichtig:

Dieser Befehl verwirft lokale Änderungen an dieser Datei.

Vorher prüfen:

```bash
git diff README.md
```

Nur nutzen, wenn die Änderung wirklich nicht mehr gebraucht wird.

---

## Alle lokalen Änderungen verwerfen

Mehrere lokale Änderungen verwerfen:

```bash
git restore .
```

Wichtig:

Das kann viele Änderungen löschen.

Vorher unbedingt prüfen:

```bash
git status
git diff
```

Wenn untracked Dateien existieren, werden sie durch `git restore .` nicht gelöscht. Dafür wäre `git clean` zuständig.

---

## Untracked Dateien entfernen

Untracked Dateien sind Dateien, die Git noch nicht verfolgt.

Anzeigen:

```bash
git status
```

Vorschau, was gelöscht würde:

```bash
git clean -n
```

Untracked Dateien löschen:

```bash
git clean -f
```

Untracked Dateien und Ordner löschen:

```bash
git clean -fd
```

Sehr wichtig:

Immer zuerst Vorschau nutzen:

```bash
git clean -n
```

`git clean` kann Dateien löschen, die noch nie committed wurden. Diese Dateien sind danach oft weg.

---

## Ignorierte Dateien auch entfernen

Vorschau inklusive ignorierter Dateien:

```bash
git clean -fdx -n
```

Löschen inklusive ignorierter Dateien:

```bash
git clean -fdx
```

Das ist gefährlich, weil dadurch auch ignorierte Ordner wie `.venv/`, `node_modules/`, Cache-Ordner oder lokale Testdaten gelöscht werden können.

Deshalb nur nutzen, wenn man genau weiß, was betroffen ist.

---

## Änderungen kurzfristig sichern mit `git stash`

`git stash` legt offene Änderungen kurzfristig weg.

```bash
git stash
```

Danach ist das Working Directory meistens wieder sauber.

Stashes anzeigen:

```bash
git stash list
```

Stash zurückholen:

```bash
git stash pop
```

Oder ohne Löschen aus der Stash-Liste anwenden:

```bash
git stash apply
```

`stash` ist nützlich, wenn man schnell Branch wechseln oder pullen muss, aber offene Änderungen noch nicht committen möchte.

---

## Stash mit Nachricht

Ein Stash kann eine Nachricht bekommen.

```bash
git stash push -m "Work on Git troubleshooting chapter"
```

Das ist übersichtlicher als anonyme Stashes.

Anzeigen:

```bash
git stash list
```

Beispiel:

```text
stash@{0}: On main: Work on Git troubleshooting chapter
```

Bei mehreren Stashes ist eine Nachricht sehr hilfreich.

---

## Stash löschen

Einen Stash löschen:

```bash
git stash drop stash@{0}
```

Alle Stashes löschen:

```bash
git stash clear
```

Vorsicht:

Stashes können wichtige Arbeit enthalten.

Vor dem Löschen prüfen:

```bash
git stash list
git stash show -p stash@{0}
```

So sieht man, was im Stash gespeichert ist.

---

## Push wird abgelehnt

Typisches Problem:

```text
rejected
fetch first
non-fast-forward
```

Das bedeutet meistens:

Auf GitHub gibt es Änderungen, die lokal noch fehlen.

Sauberer Ablauf:

```bash
git status
git pull --rebase origin main
git push
```

Wichtig:

Vor `pull --rebase` sollte der Arbeitsstand sauber sein.

Prüfen:

```bash
git status
```

Wenn offene Änderungen existieren, erst committen oder stashing nutzen.

---

## Lokale und Remote-Änderungen auseinanderhalten

Git kann melden:

```text
Your branch is ahead of 'origin/main' by 1 commit.
```

Bedeutung:

Ein Commit ist lokal, aber noch nicht auf GitHub.

Lösung:

```bash
git push
```

Andere Meldung:

```text
Your branch is behind 'origin/main' by 1 commit.
```

Bedeutung:

GitHub hat einen Commit, der lokal fehlt.

Lösung:

```bash
git pull
```

Bei:

```text
Your branch and 'origin/main' have diverged.
```

haben beide Seiten unterschiedliche neue Commits.

Dann muss man sauber integrieren, zum Beispiel mit:

```bash
git pull --rebase origin main
```

---

## Merge-Konflikt

Ein Merge-Konflikt entsteht, wenn Git zwei Änderungen nicht automatisch zusammenführen kann.

Typische Meldung:

```text
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Dann prüfen:

```bash
git status
```

Git zeigt, welche Datei betroffen ist.

Die Datei enthält Konfliktmarker.

---

## Konfliktmarker verstehen

Beispiel:

```text
<<<<<<< HEAD
Text aus dem aktuellen Branch
=======
Text aus dem anderen Branch
>>>>>>> feature-branch
```

Bedeutung:

| Marker               | Bedeutung                        |
| -------------------- | -------------------------------- |
| `<<<<<<< HEAD`       | Version aus dem aktuellen Branch |
| `=======`            | Trennung                         |
| `>>>>>>> branchname` | Version aus dem anderen Branch   |

Man muss die Datei bearbeiten und entscheiden, welcher Text bleiben soll.

Die Marker müssen entfernt werden.

---

## Merge-Konflikt lösen

Ablauf:

```bash
git status
```

Datei öffnen:

```bash
code README.md
```

oder:

```bash
nano README.md
```

Konfliktmarker entfernen und finalen Inhalt speichern.

Danach:

```bash
git add README.md
git commit
```

Bei manchen Merge-Situationen ist die Commit-Nachricht schon vorbereitet.

Danach prüfen:

```bash
git status
git log --oneline -5
```

---

## Merge abbrechen

Wenn ein Merge zu kompliziert wird oder man zurück möchte:

```bash
git merge --abort
```

Danach prüfen:

```bash
git status
```

Das bringt das Repository normalerweise zurück in den Zustand vor dem Merge.

Wichtig:

`git merge --abort` funktioniert nur, wenn gerade ein Merge aktiv ist.

---

## Rebase-Konflikt

Bei `git pull --rebase` kann ebenfalls ein Konflikt entstehen.

Git meldet dann, welche Datei betroffen ist.

Ablauf:

```bash
git status
```

Datei öffnen, Konflikt lösen, dann:

```bash
git add datei.md
git rebase --continue
```

Wenn man abbrechen möchte:

```bash
git rebase --abort
```

Wichtig:

Bei Rebase sagt Git meistens genau, welcher nächste Schritt nötig ist.

Die Meldungen lesen.

---

## Falscher Branch

Problem:

Man hat Änderungen auf dem falschen Branch gemacht.

Zuerst prüfen:

```bash
git status
git branch
```

Wenn Änderungen noch nicht committed sind, kann man oft einfach den richtigen Branch wechseln:

```bash
git switch richtiger-branch
```

Wenn Git den Wechsel erlaubt, nimmt es die offenen Änderungen mit.

Wenn Git blockiert, kann man stash nutzen:

```bash
git stash push -m "Move work to correct branch"
git switch richtiger-branch
git stash pop
```

Danach normal committen.

---

## Commit auf falschem Branch

Problem:

Man hat bereits auf dem falschen Branch committed.

Ein einfacher Weg:

1. Commit-ID merken:

```bash
git log --oneline -3
```

2. Zum richtigen Branch wechseln:

```bash
git switch richtiger-branch
```

3. Commit übernehmen:

```bash
git cherry-pick commit-id
```

4. Falschen Branch später bereinigen, wenn nötig.

`cherry-pick` übernimmt einen bestimmten Commit auf den aktuellen Branch.

Wichtig:

Nur nutzen, wenn man verstanden hat, welcher Commit übernommen wird.

---

## Detached HEAD

`detached HEAD` bedeutet, dass man nicht direkt auf einem Branch arbeitet, sondern auf einem bestimmten Commit.

Git kann melden:

```text
You are in 'detached HEAD' state.
```

Das passiert oft, wenn man einen alten Commit auscheckt.

Beispiel:

```bash
git checkout commit-id
```

Oder:

```bash
git switch --detach commit-id
```

In diesem Zustand kann man alte Stände ansehen.

Aber neue Commits hängen nicht normal an einem Branch.

---

## Aus detached HEAD retten

Wenn man im detached HEAD gearbeitet und committed hat, kann man die Arbeit sichern.

Neuen Branch daraus erstellen:

```bash
git switch -c rescue-branch
```

Danach ist der Commit wieder auf einem Branch gesichert.

Prüfen:

```bash
git branch
git log --oneline -5
```

Wenn man nur alte Dateien ansehen wollte und nichts behalten muss:

```bash
git switch main
```

---

## Letzten Commit ändern

Wenn der letzte Commit noch nicht gepusht wurde, kann man ihn ändern.

Datei vergessen:

```bash
git add vergessene-datei.md
git commit --amend
```

Commit-Nachricht ändern:

```bash
git commit --amend -m "Better commit message"
```

Wichtig:

`amend` verändert den letzten Commit.

Nach Push sollte man damit vorsichtig sein, besonders in Teamprojekten.

---

## Commit rückgängig machen mit `git revert`

`git revert` macht einen Commit rückgängig, indem ein neuer Commit erstellt wird.

```bash
git revert commit-id
```

Vorteil:

Die Historie bleibt erhalten.

Das ist sicher für geteilte Repositories und öffentliche Projekte.

Beispiel:

```bash
git log --oneline
git revert a1b2c3d
git push
```

Danach sieht man in der Historie:

```text
Revert "Add wrong file"
```

---

## `git reset` verstehen

`git reset` setzt den Zustand zurück.

Es gibt verschiedene Arten:

| Befehl              | Wirkung                                          |
| ------------------- | ------------------------------------------------ |
| `git reset --soft`  | Commit zurücknehmen, Änderungen bleiben staged   |
| `git reset --mixed` | Commit zurücknehmen, Änderungen bleiben unstaged |
| `git reset --hard`  | Commit und Änderungen verwerfen                  |

Beispiel:

```bash
git reset --soft HEAD~1
```

Das nimmt den letzten Commit zurück, behält die Änderungen aber staged.

Gefährlich:

```bash
git reset --hard HEAD~1
```

Das kann Arbeit löschen.

---

## `reset --hard` nur mit Vorsicht

`reset --hard` sollte man nicht blind nutzen.

Beispiel:

```bash
git reset --hard HEAD
```

Das verwirft lokale Änderungen.

Beispiel:

```bash
git reset --hard HEAD~1
```

Das setzt den Branch einen Commit zurück und verwirft Änderungen.

Vorher prüfen:

```bash
git status
git log --oneline -5
```

Bei Unsicherheit lieber erst fragen, stashen oder Backup machen.

---

## Verlorene Commits finden mit `git reflog`

`git reflog` zeigt, wohin `HEAD` in letzter Zeit gezeigt hat.

```bash
git reflog
```

Das ist sehr nützlich, wenn man durch reset, amend oder Branchwechsel etwas verloren glaubt.

Beispielausgabe:

```text
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
9f8e7d6 HEAD@{1}: commit: Add chapter
```

Dann kann man einen alten Stand wieder erreichen.

Beispiel:

```bash
git switch -c rescue 9f8e7d6
```

`reflog` ist oft die Rettung bei Git-Problemen.

---

## Datei aus altem Commit wiederherstellen

Man kann eine Datei aus einem alten Commit zurückholen.

Commit suchen:

```bash
git log --oneline
```

Datei aus altem Commit wiederherstellen:

```bash
git restore --source commit-id -- pfad/zur/datei
```

Beispiel:

```bash
git restore --source a1b2c3d -- README.md
```

Danach ist die Datei im Working Directory verändert.

Dann prüfen und committen:

```bash
git status
git diff
git add README.md
git commit -m "Restore README from previous version"
```

---

## Datei nur ansehen, nicht wiederherstellen

Alte Version einer Datei anzeigen:

```bash
git show commit-id:pfad/zur/datei
```

Beispiel:

```bash
git show a1b2c3d:README.md
```

Das ist sicher, weil es nichts verändert.

Man sieht nur den alten Inhalt.

---

## Remote falsch gesetzt

Problem:

Push geht zum falschen Repository oder falschen Account.

Prüfen:

```bash
git remote -v
```

Remote ändern:

```bash
git remote set-url origin neue-url
```

Beispiel:

```bash
git remote set-url origin git@github-private:user/repository.git
```

Danach prüfen:

```bash
git remote -v
ssh -T git@github-private
```

Bei mehreren GitHub-Konten ist diese Prüfung besonders wichtig.

---

## Falsche Git-Identität

Problem:

Commits nutzen falschen Namen oder falsche E-Mail.

Prüfen:

```bash
git config user.name
git config user.email
```

Lokale Identität setzen:

```bash
git config user.name "Name"
git config user.email "email@example.com"
```

Wichtig:

Lokale Konfiguration gilt nur für dieses Repository.

Globale Konfiguration:

```bash
git config --global user.name "Name"
git config --global user.email "email@example.com"
```

Bei privaten, schulischen und beruflichen Repositories sollte die Identität sauber getrennt sein.

---

## Permission denied bei GitHub

Typische Meldung:

```text
Permission denied (publickey).
```

Das bedeutet meistens:

SSH-Zugriff funktioniert nicht.

Prüfen:

```bash
ssh -T git@github.com
```

Bei SSH-Alias:

```bash
ssh -T git@github-private
ssh -T git@github-school
```

Zusätzlich prüfen:

```bash
git remote -v
ls -la ~/.ssh
cat ~/.ssh/config
```

Mögliche Ursachen:

- falscher SSH-Schlüssel
- öffentlicher Schlüssel nicht bei GitHub hinterlegt
- falscher SSH-Alias
- falsches GitHub-Konto
- falsche Remote-Adresse
- SSH-Agent kennt Schlüssel nicht

---

## Repository nicht gefunden

Typische Meldung:

```text
Repository not found.
```

Mögliche Ursachen:

- Repository-URL falsch
- Repository existiert nicht
- falsches GitHub-Konto
- keine Berechtigung
- privates Repository ohne Zugriff
- falscher SSH-Key
- Tippfehler im Repo-Namen

Prüfen:

```bash
git remote -v
ssh -T git@github.com
```

Bei mehreren Accounts:

```bash
ssh -T git@github-private
ssh -T git@github-school
```

---

## Konfliktmarker versehentlich committed

Problem:

Eine Datei enthält noch:

```text
<<<<<<< HEAD
=======
>>>>>>> branch
```

Dann wurden Konfliktmarker nicht entfernt.

Lösung:

1. Datei öffnen.
2. Marker entfernen.
3. finalen Inhalt sauber setzen.
4. Commit erstellen.

```bash
git status
grep -R "<<<<<<<" .
git add datei.md
git commit -m "Fix unresolved merge conflict markers"
git push
```

`grep -R "<<<<<<<" .` hilft, Konfliktmarker im Projekt zu finden.

---

## Secret versehentlich committed

Problem:

Passwort, Token oder privater Schlüssel wurde committed.

Wichtig:

Wenn ein Secret gepusht wurde, gilt es als kompromittiert.

Sofortmaßnahmen:

- Passwort ändern
- Token widerrufen
- SSH-Schlüssel ersetzen
- betroffene Zugänge prüfen
- Datei aus Repository entfernen
- `.gitignore` ergänzen
- Historie bereinigen, wenn nötig

Nur die Datei in einem neuen Commit zu löschen reicht bei echten Secrets nicht, weil sie in der Historie bleiben kann.

---

## Große Datei versehentlich committed

Problem:

Eine große Datei wurde committed.

Beispiele:

- ISO-Datei
- VM-Image
- Datenbank-Dump
- großes ZIP
- große Logdatei

Wenn noch nicht gepusht:

```bash
git rm --cached große-datei
echo "große-datei" >> .gitignore
git commit --amend
```

Wenn schon gepusht, wird es komplizierter, weil die Datei in der Historie liegt.

Dann sollte man vorsichtig planen und nicht blind die Historie umschreiben.

---

## Sauberer Rettungsablauf bei Unsicherheit

Wenn man nicht weiß, was los ist:

```bash
git status
git branch
git log --oneline -5
git remote -v
git diff
```

Wenn offene Änderungen wichtig sind:

```bash
git stash push -m "backup before fixing git problem"
```

Dann erneut prüfen:

```bash
git status
```

Erst danach reparieren.

Das verhindert, dass man durch schnelle Befehle Arbeit verliert.

---

## Typische Git-Fehler und Lösungen

| Problem                  | Erste Prüfung   | Mögliche Lösung                                  |
| ------------------------ | --------------- | ------------------------------------------------ |
| Push abgelehnt           | `git status`    | `git pull --rebase origin main`, dann `git push` |
| Datei falsch staged      | `git status`    | `git restore --staged datei`                     |
| Änderung soll weg        | `git diff`      | `git restore datei`                              |
| untracked Dateien stören | `git clean -n`  | `git clean -f`                                   |
| falscher Branch          | `git branch`    | `git switch branch` oder `git stash`             |
| Merge-Konflikt           | `git status`    | Datei lösen, `git add`, `git commit`             |
| Rebase-Konflikt          | `git status`    | Datei lösen, `git add`, `git rebase --continue`  |
| Commit verloren          | `git reflog`    | neuen Branch auf alten Commit erstellen          |
| Remote falsch            | `git remote -v` | `git remote set-url origin ...`                  |
| SSH-Zugriff kaputt       | `ssh -T ...`    | SSH-Key, Alias und GitHub-Konto prüfen           |

---

## Praktische Beispiele

### Beispiel 1: Push wurde abgelehnt

```bash
git status
git pull --rebase origin main
git push
```

Damit werden zuerst die Änderungen von GitHub geholt und die eigenen Commits danach angewendet.

---

### Beispiel 2: Datei versehentlich staged

```bash
git status
git restore --staged notes.md
git status
```

Die Datei ist danach nicht mehr im nächsten Commit.

---

### Beispiel 3: Lokale Änderung verwerfen

```bash
git diff README.md
git restore README.md
```

Damit wird die lokale Änderung an `README.md` verworfen.

---

### Beispiel 4: Arbeit vor Branchwechsel sichern

```bash
git status
git stash push -m "temporary work"
git switch main
git pull
git stash pop
```

Damit werden offene Änderungen kurz gespeichert und später wieder angewendet.

---

### Beispiel 5: Alten Commit wiederfinden

```bash
git reflog
git switch -c rescue commit-id
```

Damit wird ein neuer Branch auf einem alten Commit erstellt.

---

## Nützliche Befehle

| Befehl                       | Bedeutung                                   |
| ---------------------------- | ------------------------------------------- |
| `git status`                 | Zustand prüfen                              |
| `git diff`                   | lokale Änderungen anzeigen                  |
| `git diff --staged`          | staged Änderungen anzeigen                  |
| `git log --oneline`          | Historie kompakt anzeigen                   |
| `git branch`                 | Branches anzeigen                           |
| `git remote -v`              | Remotes anzeigen                            |
| `git restore datei`          | lokale Änderung verwerfen                   |
| `git restore --staged datei` | Datei aus Staging Area entfernen            |
| `git clean -n`               | Vorschau für Löschen untracked Dateien      |
| `git clean -f`               | untracked Dateien löschen                   |
| `git stash`                  | Änderungen kurzfristig weglegen             |
| `git stash list`             | Stashes anzeigen                            |
| `git stash pop`              | letzten Stash anwenden und entfernen        |
| `git merge --abort`          | Merge abbrechen                             |
| `git rebase --continue`      | Rebase nach Konfliktlösung fortsetzen       |
| `git rebase --abort`         | Rebase abbrechen                            |
| `git revert commit-id`       | Commit durch neuen Commit rückgängig machen |
| `git reset --hard`           | Zustand hart zurücksetzen, gefährlich       |
| `git reflog`                 | frühere HEAD-Zustände anzeigen              |
| `git show commit-id`         | Commit anzeigen                             |
| `git show commit-id:datei`   | alte Datei-Version anzeigen                 |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Git-Fehlersuche wichtig, weil technische Projekte zuverlässig gepflegt werden müssen.

In der Praxis bedeutet das:

- Push- und Pull-Probleme lösen
- falsche Branches erkennen
- Änderungen vor Datenverlust schützen
- Merge-Konflikte bearbeiten
- Remote-Adressen prüfen
- SSH-Probleme analysieren
- versehentliche Änderungen zurücknehmen
- alte Projektstände finden
- sensible Daten aus Projekten fernhalten
- sauber dokumentieren, was repariert wurde

Ein guter FISI arbeitet bei Git-Problemen ruhig und systematisch: Zustand prüfen, Ursache verstehen, sichere Lösung wählen und danach den Arbeitsstand kontrollieren.

---

## Kurze Zusammenfassung

Git bietet viele Werkzeuge zur Fehlersuche und Wiederherstellung.

Der wichtigste Startpunkt ist fast immer `git status`. Danach helfen Befehle wie `git diff`, `git log`, `git remote -v`, `git restore`, `git stash`, `git merge --abort`, `git rebase --abort`, `git revert`, `git reset` und `git reflog`.

Besonders vorsichtig sollte man mit `git reset --hard`, `git clean` und Force Push sein, weil dadurch Arbeit verloren gehen kann.

Für FISI ist dieses Kapitel wichtig, weil Git-Probleme in echten Projekten regelmäßig vorkommen und kontrolliert gelöst werden müssen.
