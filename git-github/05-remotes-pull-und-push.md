# 5. Remotes, Pull und Push

In diesem Kapitel geht es um Remotes, Pull und Push in Git.

Ein Git-Repository kann lokal auf dem eigenen Rechner liegen und zusätzlich auf einem entfernten Server gespeichert werden. Bei vielen Projekten ist dieser entfernte Server GitHub. Damit lokale Änderungen und GitHub zusammenpassen, nutzt man Befehle wie `git remote`, `git pull` und `git push`.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele Projekte, Skripte, Dokumentationen und Konfigurationsbeispiele nicht nur lokal bleiben, sondern mit GitHub oder anderen Git-Servern synchronisiert werden.

---

## Kurz erklärt

Ein Remote ist eine entfernte Version eines Git-Repositories.

Bei GitHub liegt das Remote Repository online.

Wichtige Befehle:

```bash
git remote -v
git pull
git push
```

Bedeutung:

| Befehl           | Bedeutung                                            |
| ---------------- | ---------------------------------------------------- |
| `git remote -v`  | zeigt entfernte Repositories an                      |
| `git pull`       | holt Änderungen vom Remote                           |
| `git push`       | lädt lokale Commits zum Remote hoch                  |
| `git clone`      | lädt ein Repository herunter                         |
| `git fetch`      | holt Informationen vom Remote, ohne direkt zu mergen |
| `git branch -vv` | zeigt Branches mit Remote-Verknüpfung                |

Ein typischer Ablauf:

```bash
git status
git pull
git add datei.md
git commit -m "Update documentation"
git push
```

---

## Was ist ein Remote?

Ein Remote ist ein Verweis auf ein entferntes Repository.

Beispiel:

```text
lokales Repository:  ~/github/private/fisi-lernwiki
Remote Repository:  GitHub Repository online
```

Das lokale Repository liegt auf dem eigenen Rechner.  
Das Remote Repository liegt zum Beispiel auf GitHub.

Remotes werden genutzt für:

- Backup auf GitHub
- Zusammenarbeit
- Pull Requests
- Synchronisation zwischen mehreren Geräten
- Veröffentlichung von Projekten
- Arbeiten mit Forks
- Schul- oder Teamprojekte

---

## Remote anzeigen

Remotes zeigt man mit:

```bash
git remote -v
```

Beispielausgabe:

```text
origin  git@github.com:user/repository.git (fetch)
origin  git@github.com:user/repository.git (push)
```

Bedeutung:

| Teil                                 | Bedeutung                            |
| ------------------------------------ | ------------------------------------ |
| `origin`                             | Name des Remotes                     |
| `git@github.com:user/repository.git` | Adresse des Remotes                  |
| `fetch`                              | Adresse zum Holen von Änderungen     |
| `push`                               | Adresse zum Hochladen von Änderungen |

`origin` ist der Standardname für das Haupt-Remote.

---

## origin

`origin` ist nur ein Name.

Wenn man ein Repository von GitHub klont, nennt Git das Remote meistens automatisch `origin`.

Beispiel:

```bash
git clone git@github.com:user/repository.git
```

Danach existiert meistens:

```text
origin
```

Das bedeutet nicht, dass `origin` etwas Besonderes im Internet ist. Es ist einfach der lokale Name für das entfernte Repository.

Man kann Remotes auch anders nennen, aber `origin` ist der Standard.

---

## Remote hinzufügen

Wenn ein lokales Repository noch kein Remote hat, kann man eins hinzufügen.

```bash
git remote add origin git@github.com:user/repository.git
```

Danach prüfen:

```bash
git remote -v
```

Beispiel:

```text
origin  git@github.com:user/repository.git (fetch)
origin  git@github.com:user/repository.git (push)
```

Das braucht man, wenn man ein lokales Projekt zuerst auf dem Rechner erstellt und später mit GitHub verbinden möchte.

---

## Remote ändern

Wenn die Remote-Adresse falsch ist, kann man sie ändern.

```bash
git remote set-url origin neue-url
```

Beispiel:

```bash
git remote set-url origin git@github.com:user/new-repository.git
```

Danach prüfen:

```bash
git remote -v
```

Das ist wichtig, wenn ein Repository umbenannt wurde oder wenn man versehentlich die falsche GitHub-Adresse gesetzt hat.

---

## Remote entfernen

Ein Remote kann entfernt werden.

```bash
git remote remove origin
```

Danach prüfen:

```bash
git remote -v
```

Wenn keine Ausgabe kommt, gibt es kein Remote mehr.

Das entfernt nicht das GitHub-Repository selbst. Es entfernt nur die Verbindung im lokalen Repository.

---

## HTTPS und SSH

GitHub-Repositories können über HTTPS oder SSH verbunden werden.

HTTPS-Beispiel:

```text
https://github.com/user/repository.git
```

SSH-Beispiel:

```text
git@github.com:user/repository.git
```

Unterschied:

| Methode   | Bedeutung                                    |
| --------- | -------------------------------------------- |
| HTTPS     | Verbindung über Web-Protokoll, oft mit Token |
| SSH       | Verbindung über SSH-Schlüssel                |
| SSH-Alias | nützlich bei mehreren GitHub-Konten          |

SSH ist praktisch, weil man mit Schlüsseln arbeiten kann und nicht ständig Zugangsdaten eingeben muss.

---

## Remote bei mehreren GitHub-Konten

Wenn man mehrere GitHub-Konten nutzt, kann die Remote-Adresse besonders wichtig sein.

Beispiel mit SSH-Alias:

```text
git@github-private:user/repository.git
git@github-school:user/repository.git
```

So kann man private und schulische Repositories trennen.

Prüfen:

```bash
git remote -v
git config user.name
git config user.email
```

Wichtig:

Bei mehreren Konten sollte man immer prüfen:

- richtige Remote-Adresse
- richtige Git-Identität
- richtiger SSH-Schlüssel
- richtiger Ordner
- richtiges GitHub-Konto

---

## Push

`git push` lädt lokale Commits zum Remote hoch.

```bash
git push
```

Wichtig:

`git push` lädt nur Commits hoch.

Wenn eine Datei nur geändert wurde, aber noch nicht committed ist, wird sie nicht gepusht.

Richtiger Ablauf:

```bash
git status
git add datei.md
git commit -m "Add chapter"
git push
```

Falsche Erwartung:

```text
Ich habe die Datei gespeichert, also ist sie automatisch auf GitHub.
```

Das stimmt nicht.

Erst nach `git commit` und `git push` ist die Änderung auf GitHub.

---

## Pull

`git pull` holt Änderungen vom Remote und integriert sie lokal.

```bash
git pull
```

Ein Pull besteht technisch grob aus:

```text
fetch + merge
```

Das bedeutet:

- Git holt neue Informationen vom Remote
- Git integriert diese Änderungen in den aktuellen Branch

Typische Nutzung:

```bash
git pull
```

oder genauer:

```bash
git pull origin main
```

---

## Fetch

`git fetch` holt Informationen vom Remote, ohne sie direkt in den aktuellen Branch zu integrieren.

```bash
git fetch
```

Danach kann man prüfen, was neu ist.

Beispiel:

```bash
git log --oneline HEAD..origin/main
```

Unterschied:

| Befehl      | Bedeutung                    |
| ----------- | ---------------------------- |
| `git fetch` | nur holen, nicht integrieren |
| `git pull`  | holen und integrieren        |
| `git push`  | lokale Commits hochladen     |

`fetch` ist vorsichtiger als `pull`, weil es den eigenen Arbeitsstand nicht direkt verändert.

---

## Push beim ersten Mal

Wenn ein lokaler Branch noch keinen Upstream hat, kann Git beim Push meckern.

Dann nutzt man:

```bash
git push -u origin main
```

Oder bei einem anderen Branch:

```bash
git push -u origin branchname
```

Die Option `-u` setzt den Upstream.

Danach weiß Git:

```text
Dieser lokale Branch gehört zu diesem Remote-Branch.
```

Dann reicht später meistens:

```bash
git push
git pull
```

---

## Upstream prüfen

Upstream-Verknüpfungen zeigt man mit:

```bash
git branch -vv
```

Beispiel:

```text
* main a1b2c3d [origin/main] Add Git remotes chapter
```

Bedeutung:

| Teil             | Bedeutung                        |
| ---------------- | -------------------------------- |
| `main`           | lokaler Branch                   |
| `origin/main`    | verbundener Remote-Branch        |
| `a1b2c3d`        | letzter Commit                   |
| Commit-Nachricht | Beschreibung des letzten Commits |

Wenn kein Upstream gesetzt ist, weiß Git nicht automatisch, wohin gepusht oder von wo gepullt werden soll.

---

## Ahead und Behind

`git status` zeigt manchmal Hinweise wie:

```text
Your branch is ahead of 'origin/main' by 1 commit.
```

Das bedeutet:

Ein Commit existiert lokal, aber noch nicht auf GitHub.

Lösung:

```bash
git push
```

Andere Meldung:

```text
Your branch is behind 'origin/main' by 1 commit.
```

Das bedeutet:

Auf GitHub gibt es neue Commits, die lokal noch fehlen.

Lösung:

```bash
git pull
```

Wenn beides passiert ist, kann die Meldung ungefähr bedeuten:

```text
Your branch and 'origin/main' have diverged.
```

Dann haben lokal und remote unterschiedliche neue Commits.

---

## Push wird abgelehnt

Ein Push kann abgelehnt werden, wenn GitHub neue Änderungen hat, die lokal fehlen.

Typische Meldung:

```text
rejected
fetch first
non-fast-forward
```

Das bedeutet meistens:

Auf GitHub gibt es Commits, die lokal noch nicht vorhanden sind.

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

Am besten steht dort:

```text
nothing to commit, working tree clean
```

---

## pull --rebase

`git pull --rebase` holt Änderungen vom Remote und setzt die eigenen lokalen Commits danach oben drauf.

```bash
git pull --rebase origin main
```

Das ist oft sauberer als ein Merge Commit, wenn man nur lokale Arbeit auf den neuesten GitHub-Stand setzen möchte.

Einfach gesagt:

| Befehl              | Wirkung                                         |
| ------------------- | ----------------------------------------------- |
| `git pull`          | holt Änderungen und merged                      |
| `git pull --rebase` | holt Änderungen und setzt eigene Commits danach |

Für Einzelprojekte ist `pull --rebase` oft praktisch, wenn man versehentlich direkt auf GitHub und lokal gearbeitet hat.

---

## Wann pull vor push?

Vor dem Push sollte man pullen, wenn es möglich ist, dass sich auf GitHub etwas geändert hat.

Beispiele:

- man hat auf GitHub direkt eine Datei bearbeitet
- ein Teammitglied hat gepusht
- ein Pull Request wurde gemerged
- man arbeitet auf mehreren Geräten
- GitHub Actions oder ein Bot hat Commits erzeugt

Sauberer Ablauf:

```bash
git status
git pull --rebase origin main
git push
```

Wenn man sicher allein lokal gearbeitet hat und GitHub unverändert ist, reicht oft:

```bash
git push
```

---

## Konflikte beim Pull

Beim Pull kann es Konflikte geben.

Das passiert, wenn lokal und remote dieselbe Stelle unterschiedlich geändert wurde.

Git meldet dann einen Conflict.

Typische Marker in Dateien:

```text
<<<<<<< HEAD
lokale Version
=======
Remote-Version
>>>>>>> commit-id
```

Ablauf:

```bash
git status
# Datei öffnen und Konflikt lösen
git add datei.md
git rebase --continue
```

Wenn es ein normaler Merge-Pull war, danach:

```bash
git commit
```

Je nach Situation sagt Git in der Ausgabe, welcher nächste Befehl nötig ist.

Wichtig:

Git-Meldungen genau lesen.

---

## Rebase abbrechen

Wenn ein Rebase beim Pull Probleme macht und man zurück möchte:

```bash
git rebase --abort
```

Danach ist man wieder ungefähr im Zustand vor dem Rebase.

Prüfen:

```bash
git status
```

Das ist nützlich, wenn man merkt, dass man zuerst mehr verstehen oder sichern möchte.

---

## Fetch vor Entscheidung

Wenn man vorsichtig sein möchte, kann man zuerst nur fetch nutzen.

```bash
git fetch origin
```

Dann prüfen:

```bash
git status
git log --oneline HEAD..origin/main
```

Wenn alles passt:

```bash
git pull --rebase origin main
```

Oder:

```bash
git merge origin/main
```

Das ist eher fortgeschritten, aber gut zu kennen.

---

## Remote Branches

Remote Branches sind Branches, die auf dem Remote existieren.

Anzeigen:

```bash
git branch -a
```

Beispiel:

```text
* main
  remotes/origin/main
  remotes/origin/add-feature
```

Remote Branch lokal auschecken:

```bash
git switch branchname
```

Wenn Git den Remote Branch kennt, erstellt Git oft automatisch einen passenden lokalen Branch.

Oder explizit:

```bash
git switch -c branchname origin/branchname
```

---

## Neuen Branch pushen

Wenn man einen neuen Branch erstellt hat:

```bash
git switch -c add-new-chapter
```

Nach Commit:

```bash
git push -u origin add-new-chapter
```

Danach existiert der Branch auch auf GitHub.

Das ist wichtig für Pull Requests.

---

## Remote Branch löschen

Remote Branch löschen:

```bash
git push origin --delete branchname
```

Beispiel:

```bash
git push origin --delete add-new-chapter
```

Lokalen Branch löschen:

```bash
git branch -d branchname
```

Ein typischer Ablauf nach einem gemergten Pull Request:

```bash
git switch main
git pull
git branch -d add-new-chapter
git push origin --delete add-new-chapter
```

---

## Clone

Mit `git clone` lädt man ein Repository herunter.

```bash
git clone repository-url
```

Beispiel SSH:

```bash
git clone git@github.com:user/repository.git
```

Beispiel HTTPS:

```bash
git clone https://github.com/user/repository.git
```

Nach dem Klonen gibt es meistens direkt:

- Projektordner
- `.git`-Ordner
- Remote `origin`
- Verbindung zu `origin/main`

Prüfen:

```bash
cd repository
git remote -v
git status
```

---

## Remote bei Forks

Ein Fork ist eine eigene Kopie eines fremden GitHub-Repositories.

Typische Remote-Namen:

| Remote     | Bedeutung                          |
| ---------- | ---------------------------------- |
| `origin`   | eigener Fork                       |
| `upstream` | ursprüngliches Original-Repository |

Upstream hinzufügen:

```bash
git remote add upstream git@github.com:original-user/repository.git
```

Remotes anzeigen:

```bash
git remote -v
```

Vom Original holen:

```bash
git fetch upstream
```

Forks sind besonders wichtig bei Open-Source-Projekten.

---

## Synchronisation zwischen Geräten

Wenn man auf mehreren Geräten arbeitet, ist Pull und Push besonders wichtig.

Beispiel:

Gerät 1:

```bash
git add README.md
git commit -m "Update README"
git push
```

Gerät 2:

```bash
git pull
```

Dann hat Gerät 2 den neuen Stand.

Regel:

Vor dem Arbeiten auf einem anderen Gerät zuerst pullen.

```bash
git status
git pull
```

Sonst entstehen schnell abgelehnte Pushes oder Konflikte.

---

## GitHub direkt im Browser bearbeiten

Man kann Dateien auf GitHub direkt im Browser bearbeiten.

Das erstellt ebenfalls Commits im Remote Repository.

Problem:

Wenn man lokal noch den alten Stand hat und dann pushen möchte, wird der Push eventuell abgelehnt.

Lösung:

```bash
git pull --rebase origin main
git push
```

Besser:

Wenn möglich, größere Änderungen lokal machen und dann pushen.

Kleine README-Korrekturen im Browser sind okay, aber man muss danach lokal pullen.

---

## Private Daten und Remotes

Wenn etwas gepusht wurde, ist es auf dem Remote.

Bei öffentlichen Repositories kann es dann sichtbar sein.

Nicht pushen:

- Passwörter
- Tokens
- private SSH-Schlüssel
- `.env` mit echten Daten
- Kundendaten
- private Screenshots
- interne Dokumente
- sensible IP-Adressen oder Hostnamen

Wichtig:

`.gitignore` sollte früh erstellt werden.

Wenn ein Secret schon committed und gepusht wurde, reicht Löschen oft nicht. Das Secret muss als kompromittiert betrachtet und geändert werden.

---

## Typischer sauberer Ablauf

Für ein normales Projekt:

```bash
cd ~/github/private/fisi-lernwiki

git status
git pull --rebase origin main

# Dateien bearbeiten

git status
git diff
git add git-github/05-remotes-pull-und-push.md
git diff --staged
git commit -m "Add Git remotes pull and push chapter"
git push
git status
```

Ziel am Ende:

```text
nothing to commit, working tree clean
```

---

## Typische Fehler

| Fehler                                          | Problem                                               |
| ----------------------------------------------- | ----------------------------------------------------- |
| `commit` und `push` verwechseln                 | Änderung ist lokal, aber nicht auf GitHub             |
| `pull` vergessen                                | lokale Version ist veraltet                           |
| Push-Ablehnung nicht lesen                      | Ursache bleibt unklar                                 |
| direkt auf GitHub und lokal gleichzeitig ändern | Konflikte oder Rejected Push                          |
| falsches Remote nutzen                          | Push geht zum falschen Repository                     |
| falscher SSH-Account                            | Zugriff wird verweigert                               |
| Upstream nicht gesetzt                          | Git weiß nicht, wohin gepusht werden soll             |
| private Daten pushen                            | Sicherheitsproblem                                    |
| Konfliktmarker stehen lassen                    | Dateien wirken kaputt                                 |
| `force push` ohne Verständnis                   | fremde oder eigene Historie kann überschrieben werden |

---

## Force Push

Force Push überschreibt den Stand auf dem Remote.

```bash
git push --force
```

Oder sicherer:

```bash
git push --force-with-lease
```

Wichtig:

Force Push kann gefährlich sein, besonders in Teamprojekten.

Mögliche Probleme:

- Commits anderer Personen werden überschrieben
- Remote-Historie wird verändert
- Teammitglieder bekommen Probleme beim Pull
- Arbeit kann verloren gehen

Für Anfänger gilt:

```text
Kein Force Push, wenn man nicht genau weiß, warum es nötig ist.
```

In normalen Lern- und Dokumentationsprojekten braucht man Force Push fast nie.

---

## Praktische Beispiele

### Beispiel 1: Remote prüfen

```bash
git remote -v
git config user.name
git config user.email
```

Damit prüft man, wohin gepusht wird und mit welcher Git-Identität man arbeitet.

### Beispiel 2: Lokalen Commit hochladen

```bash
git status
git add README.md
git commit -m "Update README"
git push
```

Damit wird eine Änderung lokal gespeichert und zu GitHub hochgeladen.

### Beispiel 3: Push wurde abgelehnt

```bash
git status
git pull --rebase origin main
git push
```

Damit holt man zuerst die GitHub-Änderungen und pusht danach erneut.

### Beispiel 4: Neuen Branch hochladen

```bash
git switch -c add-example
git add example.md
git commit -m "Add example"
git push -u origin add-example
```

Damit wird der neue Branch auch auf GitHub erstellt.

---

## Nützliche Befehle

| Befehl                            | Bedeutung                                                  |
| --------------------------------- | ---------------------------------------------------------- |
| `git remote -v`                   | Remotes anzeigen                                           |
| `git remote add origin url`       | Remote hinzufügen                                          |
| `git remote set-url origin url`   | Remote-Adresse ändern                                      |
| `git remote remove origin`        | Remote entfernen                                           |
| `git clone url`                   | Repository herunterladen                                   |
| `git fetch`                       | Änderungen vom Remote holen, ohne direkt zu integrieren    |
| `git pull`                        | Änderungen vom Remote holen und integrieren                |
| `git pull --rebase origin main`   | Remote-Änderungen holen und eigene Commits danach anwenden |
| `git push`                        | lokale Commits hochladen                                   |
| `git push -u origin branch`       | Branch hochladen und Upstream setzen                       |
| `git branch -vv`                  | Branches mit Upstream anzeigen                             |
| `git branch -a`                   | lokale und Remote-Branches anzeigen                        |
| `git push origin --delete branch` | Remote-Branch löschen                                      |
| `git status`                      | Zustand und ahead/behind anzeigen                          |
| `git rebase --continue`           | Rebase nach Konfliktlösung fortsetzen                      |
| `git rebase --abort`              | Rebase abbrechen                                           |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Remotes, Pull und Push wichtig, weil viele technische Projekte nicht nur lokal existieren.

In der Praxis bedeutet das:

- Dokumentation zu GitHub hochladen
- Skripte und Konfigurationsbeispiele sichern
- mit mehreren Geräten arbeiten
- Teamprojekte synchronisieren
- Pull Requests vorbereiten
- Push-Probleme analysieren
- Remote-Adressen prüfen
- SSH-Zugriff korrekt nutzen
- sensible Daten vor dem Push vermeiden

Ein guter FISI versteht, dass `commit` nur lokal speichert und `push` die Arbeit zum Remote hochlädt. Ebenso ist `pull` wichtig, damit lokale Arbeit nicht auf einem veralteten Stand basiert.

---

## Kurze Zusammenfassung

Ein Remote ist eine entfernte Version eines Git-Repositories, zum Beispiel auf GitHub.

Mit `git push` lädt man lokale Commits hoch. Mit `git pull` holt man Änderungen vom Remote. Mit `git fetch` holt man Informationen, ohne direkt zu integrieren.

Wichtige Befehle sind `git remote -v`, `git remote add`, `git remote set-url`, `git clone`, `git fetch`, `git pull`, `git pull --rebase`, `git push`, `git push -u origin branch` und `git branch -vv`.

Für FISI ist dieses Kapitel wichtig, weil Dokumentationen, Skripte, Konfigurationsbeispiele und Projekte häufig lokal und remote sauber synchronisiert werden müssen.
