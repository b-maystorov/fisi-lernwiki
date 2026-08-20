# 4. Branches und Merge

In diesem Kapitel geht es um Branches und Merge in Git.

Ein Branch ist ein Entwicklungszweig. Mit Branches kann man Änderungen getrennt vom Hauptstand eines Projekts bearbeiten. Danach können die Änderungen wieder zusammengeführt werden. Dieses Zusammenführen nennt man Merge.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Branches nicht nur in Softwareprojekten genutzt werden. Auch Dokumentation, Skripte, Konfigurationsbeispiele, Docker-Projekte und technische Wikis können sauber über Branches gepflegt werden.

---

## Kurz erklärt

Ein Branch ist ein separater Arbeitszweig in einem Git-Repository.

Der Hauptbranch heißt meistens:

```text
main
```

Ältere Projekte nutzen manchmal noch:

```text
master
```

Ein Branch ist nützlich, wenn man an einer Änderung arbeiten möchte, ohne direkt den Hauptstand zu verändern.

Typischer Ablauf:

```bash
git switch -c neuer-branch
# Dateien bearbeiten
git add datei.md
git commit -m "Add new content"
git switch main
git merge neuer-branch
git push
```

Danach sind die Änderungen aus dem Branch in `main` übernommen.

---

## Warum Branches wichtig sind

Ohne Branches arbeitet man direkt auf dem Hauptstand.

Das kann bei kleinen Einzelprojekten funktionieren, wird aber schnell unübersichtlich.

Branches helfen bei:

- neuen Funktionen
- Dokumentationsänderungen
- Fehlerbehebungen
- Tests
- Experimenten
- Teamarbeit
- Pull Requests
- sauberer Trennung von Aufgaben

Beispiel:

Man möchte ein neues Kapitel schreiben, aber der aktuelle Hauptstand soll stabil bleiben.

Dann erstellt man einen Branch:

```bash
git switch -c add-linux-networking
```

Auf diesem Branch kann man arbeiten, committen und testen.

Wenn alles passt, wird der Branch in `main` gemerged.

---

## main und master

Der Hauptbranch heißt heute meistens:

```text
main
```

Früher war oft dieser Name üblich:

```text
master
```

Beide Begriffe meinen technisch einen Branch.

In neuen GitHub-Repositories wird meistens `main` verwendet.

Prüfen:

```bash
git branch
```

Beispielausgabe:

```text
* main
```

Das `*` zeigt, auf welchem Branch man gerade ist.

---

## Aktuellen Branch anzeigen

Den aktuellen Branch sieht man mit:

```bash
git branch
```

Beispiel:

```text
* main
  add-readme
```

Der aktuelle Branch ist mit `*` markiert.

Auch `git status` zeigt den Branch:

```bash
git status
```

Beispiel:

```text
On branch main
```

Vor einem Commit sollte man immer prüfen, auf welchem Branch man arbeitet.

---

## Neuen Branch erstellen

Einen neuen Branch erstellt man mit:

```bash
git switch -c branchname
```

Beispiel:

```bash
git switch -c add-git-branches-chapter
```

Bedeutung:

| Teil                       | Bedeutung               |
| -------------------------- | ----------------------- |
| `git switch`               | Branch wechseln         |
| `-c`                       | neuen Branch erstellen  |
| `add-git-branches-chapter` | Name des neuen Branches |

Der Befehl erstellt den Branch und wechselt direkt auf ihn.

---

## Branch wechseln

Zu einem bestehenden Branch wechseln:

```bash
git switch branchname
```

Beispiel:

```bash
git switch main
```

Oder:

```bash
git switch add-git-branches-chapter
```

Wichtig:

Vor dem Branchwechsel sollte der Arbeitsstand sauber sein.

Prüfen:

```bash
git status
```

Wenn noch offene Änderungen existieren, kann Git den Wechsel blockieren oder die Änderungen mitnehmen.

---

## Branch-Namen

Branch-Namen sollten kurz und verständlich sein.

Gute Beispiele:

```text
add-linux-readme
fix-git-typos
update-docker-docs
add-networking-notes
improve-troubleshooting
```

Weniger gute Beispiele:

```text
new
test
stuff
changes
branch1
asdf
```

Ein guter Branch-Name beschreibt kurz, woran gearbeitet wird.

In Teams sind klare Branch-Namen besonders wichtig.

---

## Arbeiten auf einem Branch

Ein Branch funktioniert wie ein eigener Arbeitsstand.

Beispiel:

```bash
git switch -c add-example
nano example.md
git add example.md
git commit -m "Add example file"
```

Dieser Commit liegt dann auf dem Branch `add-example`.

Wenn man zurück zu `main` wechselt:

```bash
git switch main
```

kann es sein, dass die Datei dort noch nicht vorhanden ist.

Das ist der Sinn eines Branches: Änderungen sind getrennt, bis sie gemerged werden.

---

## Branches anzeigen

Lokale Branches anzeigen:

```bash
git branch
```

Alle Branches inklusive Remote-Branches anzeigen:

```bash
git branch -a
```

Beispiel:

```text
* main
  add-example
  remotes/origin/main
```

Remote-Branches kommen vom Remote Repository, zum Beispiel von GitHub.

---

## Unterschiede zwischen Branches anzeigen

Man kann prüfen, was sich zwischen Branches unterscheidet.

Beispiel:

```bash
git diff main add-example
```

Oder wenn man auf `add-example` ist:

```bash
git diff main
```

Das zeigt Unterschiede zwischen dem aktuellen Branch und `main`.

Auch mit Logs:

```bash
git log --oneline main..add-example
```

Das zeigt Commits, die auf `add-example` sind, aber nicht auf `main`.

---

## Merge

Merge bedeutet, Änderungen aus einem Branch in einen anderen Branch zu übernehmen.

Typischer Ablauf:

```bash
git switch main
git merge add-example
```

Bedeutung:

- zuerst auf den Zielbranch wechseln
- dann den anderen Branch hineinmergen

Wichtig:

Man merged immer **in den aktuellen Branch hinein**.

Wenn man Änderungen nach `main` übernehmen will, muss man vorher auf `main` sein.

---

## Einfacher Merge-Ablauf

Beispiel:

```bash
git switch -c add-notes
touch notes.md
git add notes.md
git commit -m "Add notes"

git switch main
git merge add-notes
```

Danach enthält `main` die Änderung aus `add-notes`.

Wenn alles sauber ist, kann man pushen:

```bash
git push
```

---

## Fast-Forward Merge

Ein Fast-Forward Merge passiert, wenn `main` seit dem Branch-Erstellen nicht weiter verändert wurde.

Beispiel:

```text
A---B main
     \
      C add-example
```

Nach Merge:

```text
A---B---C main
```

Git verschiebt `main` einfach nach vorne.

Das ist einfach und sauber.

Viele kleine Einzelprojekte haben häufig Fast-Forward Merges.

---

## Merge Commit

Ein Merge Commit entsteht, wenn beide Branches eigene neue Commits haben.

Beispiel:

```text
A---B---D main
     \
      C add-example
```

Nach Merge:

```text
A---B---D---M main
     \     /
      C---
```

`M` ist der Merge Commit.

Er dokumentiert, dass zwei Entwicklungszweige zusammengeführt wurden.

Das ist normal in Teamprojekten oder wenn parallel gearbeitet wurde.

---

## Merge-Konflikt

Ein Merge-Konflikt entsteht, wenn Git Änderungen nicht automatisch zusammenführen kann.

Typisches Beispiel:

Zwei Branches ändern dieselbe Zeile in derselben Datei unterschiedlich.

Dann weiß Git nicht, welche Version richtig ist.

Beim Merge kann dann eine Meldung erscheinen:

```text
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Das bedeutet:

Git braucht menschliche Entscheidung.

---

## Konfliktmarker verstehen

Bei einem Merge-Konflikt schreibt Git Markierungen in die Datei.

Beispiel:

```text
<<<<<<< HEAD
Text aus dem aktuellen Branch
=======
Text aus dem anderen Branch
>>>>>>> add-example
```

Bedeutung:

| Marker               | Bedeutung                                   |
| -------------------- | ------------------------------------------- |
| `<<<<<<< HEAD`       | Beginn der Version aus dem aktuellen Branch |
| `=======`            | Trennung zwischen beiden Versionen          |
| `>>>>>>> branchname` | Ende der Version aus dem anderen Branch     |

Man muss die Datei manuell bearbeiten und entscheiden, welcher Inhalt bleiben soll.

---

## Merge-Konflikt lösen

Typischer Ablauf:

1. Status prüfen:

```bash
git status
```

2. Betroffene Datei öffnen:

```bash
code README.md
```

oder:

```bash
nano README.md
```

3. Konfliktmarker entfernen und finalen Inhalt setzen.

4. Datei speichern.

5. Gelöste Datei vormerken:

```bash
git add README.md
```

6. Merge abschließen:

```bash
git commit
```

Oder wenn Git den Commit automatisch vorbereitet:

```bash
git commit
```

Danach ist der Merge abgeschlossen.

---

## Merge abbrechen

Wenn ein Merge schiefgeht und man zurück zum Zustand vor dem Merge möchte:

```bash
git merge --abort
```

Dieser Befehl bricht den laufenden Merge ab.

Wichtig:

Das funktioniert nur, wenn ein Merge gerade aktiv ist.

Vorher prüfen:

```bash
git status
```

Git zeigt meistens an, ob man sich gerade in einem Merge-Zustand befindet.

---

## Branch nach Merge löschen

Wenn ein Branch erfolgreich gemerged wurde, kann man ihn lokal löschen.

```bash
git branch -d branchname
```

Beispiel:

```bash
git branch -d add-example
```

Wenn Git warnt, dass der Branch nicht gemerged ist, sollte man vorsichtig sein.

Erzwungen löschen:

```bash
git branch -D branchname
```

`-D` sollte man nur nutzen, wenn man sicher ist, dass die Änderungen nicht mehr gebraucht werden.

---

## Remote Branch löschen

Wenn ein Branch auch auf GitHub existiert, kann man ihn dort löschen.

```bash
git push origin --delete branchname
```

Beispiel:

```bash
git push origin --delete add-example
```

Das braucht man häufiger in Teamprojekten und bei Pull Requests.

Für einfache Einzelprojekte reicht es oft, lokale Branches zu löschen.

---

## Branch zu GitHub pushen

Einen neuen lokalen Branch zu GitHub hochladen:

```bash
git push -u origin branchname
```

Beispiel:

```bash
git push -u origin add-git-branches-chapter
```

Die Option `-u` setzt den Upstream.

Danach reicht später meistens:

```bash
git push
```

oder:

```bash
git pull
```

weil Git weiß, welcher Remote-Branch dazugehört.

---

## Upstream Branch

Ein Upstream Branch ist der Remote-Branch, mit dem ein lokaler Branch verbunden ist.

Beispiel:

```text
lokal: add-example
remote: origin/add-example
```

Prüfen:

```bash
git branch -vv
```

Beispielausgabe:

```text
* add-example a1b2c3d [origin/add-example] Add example
```

Das zeigt, mit welchem Remote-Branch der lokale Branch verbunden ist.

---

## Pull Request kurz erklärt

Ein Pull Request ist eine Anfrage auf GitHub, Änderungen aus einem Branch in einen anderen Branch zu übernehmen.

Typischer Ablauf:

1. Branch erstellen
2. Änderungen committen
3. Branch zu GitHub pushen
4. Pull Request öffnen
5. Änderungen prüfen lassen
6. Merge durchführen

Pull Requests sind besonders wichtig in Teamarbeit.

In Einzelprojekten kann man auch direkt lokal mergen, aber Pull Requests sind gut, um Änderungen sichtbar und prüfbar zu machen.

---

## Merge vs Rebase kurz erklärt

Neben Merge gibt es auch Rebase.

Merge führt Branches zusammen und erhält die Verzweigung sichtbar.

Rebase setzt Commits eines Branches auf einen neueren Stand um.

Sehr einfache Einordnung:

| Methode      | Bedeutung                             |
| ------------ | ------------------------------------- |
| Merge        | Branches zusammenführen               |
| Rebase       | eigene Commits auf neuen Stand setzen |
| Merge Commit | zeigt Zusammenführung sichtbar        |
| Rebase       | Historie wirkt linearer               |

Für den Anfang ist Merge wichtiger und leichter verständlich.

Rebase sollte man bewusst nutzen, weil es Historie umschreiben kann.

---

## Wann Branches nutzen?

Branches sind sinnvoll bei:

- neuen Kapiteln
- größeren Änderungen
- Tests
- riskanten Änderungen
- Teamarbeit
- Pull Requests
- experimentellen Ideen
- Bugfixes
- Umstrukturierungen

Für sehr kleine Änderungen in einem Einzelprojekt kann man auch direkt auf `main` arbeiten.

Beispiel:

Ein kleiner Tippfehler in der README kann direkt auf `main` behoben werden.

Ein neues Kapitel oder eine größere Strukturänderung passt besser in einen eigenen Branch.

---

## Sauberer Branch-Workflow

Ein einfacher sauberer Workflow:

```bash
git status
git switch main
git pull
git switch -c add-new-chapter

# Dateien bearbeiten

git status
git diff
git add datei.md
git commit -m "Add new chapter"
git push -u origin add-new-chapter
```

Danach kann man auf GitHub einen Pull Request erstellen oder lokal mergen.

Lokaler Merge:

```bash
git switch main
git pull
git merge add-new-chapter
git push
git branch -d add-new-chapter
```

---

## Branches in Dokumentationsprojekten

Branches sind nicht nur für Code sinnvoll.

Auch bei Dokumentation helfen sie.

Beispiele:

```text
add-linux-section
update-git-readme
fix-spelling-lf5
add-docker-notes
restructure-network-chapter
```

So kann man größere Textänderungen sauber trennen.

Für öffentliche GitHub-Repositories wirkt das professionell, weil Änderungen nachvollziehbar bleiben.

---

## Typische Fehler mit Branches

| Fehler                                          | Problem                                 |
| ----------------------------------------------- | --------------------------------------- |
| Branch nicht prüfen                             | Commit landet auf falschem Branch       |
| direkt auf `main` alles ändern                  | große Änderungen werden unübersichtlich |
| Branch-Namen unklar wählen                      | später schwer verständlich              |
| Merge in falsche Richtung machen                | Änderungen landen am falschen Ort       |
| vor Merge nicht pullen                          | Konflikte oder veralteter Stand         |
| Konfliktmarker im Text lassen                   | Datei ist kaputt oder unprofessionell   |
| Branch löschen, bevor Änderungen gesichert sind | Arbeit kann verloren gehen              |
| `-D` blind nutzen                               | ungemergte Arbeit wird gelöscht         |
| Rebase ohne Verständnis nutzen                  | Historie kann verwirrend werden         |
| nach Merge nicht testen                         | Fehler werden erst später bemerkt       |

---

## Praktische Beispiele

### Beispiel 1: Branch für neues Kapitel

```bash
git switch -c add-git-branches-chapter
# Datei bearbeiten
git add git-github/04-branches-und-merge.md
git commit -m "Add Git branches and merge chapter"
git switch main
git merge add-git-branches-chapter
git push
```

Damit wird ein Kapitel auf einem eigenen Branch erstellt und danach in `main` übernommen.

### Beispiel 2: Branch anzeigen und wechseln

```bash
git branch
git switch main
git switch add-git-branches-chapter
```

Damit sieht man Branches und wechselt zwischen ihnen.

### Beispiel 3: Konflikt prüfen

```bash
git status
```

Wenn Git einen Merge-Konflikt meldet, zeigt `git status`, welche Dateien betroffen sind.

Danach Datei öffnen, Konflikt lösen und committen.

### Beispiel 4: Branch nach Merge löschen

```bash
git branch -d add-git-branches-chapter
```

Damit wird der lokale Branch gelöscht, nachdem er gemerged wurde.

---

## Nützliche Befehle

| Befehl                               | Bedeutung                                       |
| ------------------------------------ | ----------------------------------------------- |
| `git branch`                         | lokale Branches anzeigen                        |
| `git branch -a`                      | alle Branches anzeigen                          |
| `git branch -vv`                     | Branches mit Upstream anzeigen                  |
| `git switch branch`                  | Branch wechseln                                 |
| `git switch -c branch`               | neuen Branch erstellen und wechseln             |
| `git merge branch`                   | Branch in aktuellen Branch mergen               |
| `git merge --abort`                  | laufenden Merge abbrechen                       |
| `git branch -d branch`               | gemergten Branch löschen                        |
| `git branch -D branch`               | Branch erzwungen löschen                        |
| `git push -u origin branch`          | neuen Branch zu GitHub pushen                   |
| `git push origin --delete branch`    | Remote-Branch löschen                           |
| `git diff branch1 branch2`           | Unterschiede zwischen Branches anzeigen         |
| `git log --oneline branch1..branch2` | Commits anzeigen, die nur auf einem Branch sind |
| `git status`                         | Zustand und Merge-Konflikte prüfen              |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Branches wichtig, weil viele technische Änderungen kontrolliert vorbereitet werden müssen.

In der Praxis bedeutet das:

- Dokumentationsänderungen getrennt bearbeiten
- Skripte sicher weiterentwickeln
- Konfigurationsbeispiele testen
- Änderungen vor dem Hauptstand prüfen
- Teamarbeit über Pull Requests vorbereiten
- Fehlerbehebungen sauber trennen
- neue Ideen ausprobieren, ohne den stabilen Stand zu beschädigen
- GitHub-Projekte professioneller pflegen

Ein guter FISI versteht, dass Branches nicht nur für Entwickler wichtig sind. Sie helfen auch bei Infrastruktur, Dokumentation, Automatisierung und sauberer Projektarbeit.

---

## Kurze Zusammenfassung

Ein Branch ist ein Entwicklungszweig in Git.

Mit Branches kann man Änderungen getrennt vom Hauptstand bearbeiten. Mit Merge werden Änderungen aus einem Branch in einen anderen Branch übernommen.

Wichtige Befehle sind `git branch`, `git switch`, `git switch -c`, `git merge`, `git merge --abort`, `git branch -d`, `git push -u origin branch` und `git branch -vv`.

Für FISI ist dieses Kapitel wichtig, weil Branches helfen, Dokumentation, Skripte, Konfigurationen und Projekte kontrolliert und nachvollziehbar zu bearbeiten.
