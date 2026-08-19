# 3. Commits und Historie

In diesem Kapitel geht es um Commits und die Git-Historie.

Ein Commit ist ein gespeicherter Zustand eines Projekts. Mit Commits kann man nachvollziehen, wie sich ein Projekt entwickelt hat. Jeder Commit enthält eine Beschreibung, welche Änderung gemacht wurde. Dadurch entsteht eine Historie, die später gelesen, geprüft und bei Bedarf genutzt werden kann, um Änderungen zu verstehen oder zurückzugehen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Dokumentation, Skripte, Konfigurationsbeispiele und Projektdateien nachvollziehbar gepflegt werden müssen.

---

## Kurz erklärt

Ein Commit ist ein gespeicherter Zwischenstand in Git.

Ein Commit enthält:

- geänderte Dateien
- Autor
- Datum und Uhrzeit
- Commit-Nachricht
- eindeutige Commit-ID
- Verbindung zum vorherigen Commit

Ein einfacher Ablauf:

```bash
git status
git add README.md
git commit -m "Update README"
git log --oneline
```

Die Historie zeigt dann, welche Änderungen im Projekt gespeichert wurden.

---

## Warum Commits wichtig sind

Commits machen Änderungen nachvollziehbar.

Ohne Commits sieht man nur den aktuellen Stand einer Datei. Mit Commits sieht man auch, wie das Projekt dahin gekommen ist.

Git beantwortet Fragen wie:

- Was wurde geändert?
- Wann wurde es geändert?
- Warum wurde es geändert?
- Welche Dateien waren betroffen?
- Wie sah die Datei vorher aus?
- Welche Änderung hat vielleicht einen Fehler verursacht?
- Welche Arbeit wurde bereits erledigt?

Commits sind deshalb nicht nur technische Speicherpunkte, sondern auch Dokumentation der Projektentwicklung.

---

## Commit als Projektstand

Ein Commit speichert einen Zustand des Projekts.

Man kann sich einen Commit vorstellen wie:

```text
Projektstand zu einem bestimmten Zeitpunkt
```

Beispiel:

```text
Add Linux README
Add Linux filesystem chapter
Add Git basics chapter
Fix typo in README
```

Jeder Commit beschreibt eine Änderung oder einen abgeschlossenen Arbeitsschritt.

Wichtig:

Ein Commit sollte nicht zufällig sein, sondern einen sinnvollen kleinen Abschnitt speichern.

---

## Commit-ID

Jeder Commit hat eine eindeutige ID.

Beispiel:

```text
a1b2c3d4e5f678901234567890abcdef12345678
```

In der Praxis sieht man oft nur die kurze Version:

```text
a1b2c3d
```

Anzeigen:

```bash
git log --oneline
```

Beispiel:

```text
a1b2c3d Add Git basics chapter
9f8e7d6 Add Git and GitHub section README
```

Die Commit-ID hilft, einen bestimmten Stand eindeutig zu erkennen.

---

## HEAD

`HEAD` zeigt auf den aktuellen Stand im Repository.

Meistens bedeutet `HEAD`:

```text
der aktuelle Commit auf dem aktuellen Branch
```

Beispiel:

Wenn man auf `main` arbeitet, zeigt `HEAD` normalerweise auf den neuesten Commit von `main`.

Man sieht das zum Beispiel bei:

```bash
git log --oneline
```

Der oberste Commit ist meistens der aktuelle Stand.

`HEAD` wird später wichtig, wenn man ältere Stände prüft, Änderungen zurücknimmt oder Branches wechselt.

---

## Staging vor dem Commit

Ein Commit speichert nur Änderungen, die vorher in der Staging Area liegen.

Ablauf:

```bash
git add datei.md
git commit -m "Add chapter"
```

Wenn eine Datei geändert wurde, aber nicht mit `git add` vorgemerkt ist, landet sie nicht im Commit.

Deshalb ist `git status` so wichtig.

Vor einem Commit:

```bash
git status
```

So sieht man:

- welche Dateien geändert wurden
- welche Dateien staged sind
- welche Dateien noch nicht getrackt werden
- was im nächsten Commit gespeichert wird

---

## Änderungen vor dem Commit prüfen

Vor einem Commit sollte man prüfen, was geändert wurde.

Nicht staged Änderungen anzeigen:

```bash
git diff
```

Staged Änderungen anzeigen:

```bash
git diff --staged
```

Typischer sauberer Ablauf:

```bash
git status
git diff
git add git-github/03-commits-und-historie.md
git diff --staged
git commit -m "Add Git commits and history chapter"
```

So vermeidet man, falsche oder private Änderungen zu committen.

---

## Einen Commit erstellen

Ein Commit wird mit `git commit` erstellt.

Beispiel:

```bash
git commit -m "Add Git commits and history chapter"
```

Die Option `-m` steht für Message.

Die Nachricht beschreibt kurz, was geändert wurde.

Ein Commit ohne vorheriges `git add` funktioniert nur, wenn bereits Änderungen staged sind.

Wenn nichts staged ist, meldet Git:

```text
nothing to commit
```

Das ist kein Fehler, sondern bedeutet: Es gibt nichts Vorgemerktes für den Commit.

---

## Gute Commit-Nachrichten

Eine gute Commit-Nachricht ist kurz und verständlich.

Gute Beispiele:

```text
Add Git basics chapter
Update Linux README
Fix typo in network section
Add Docker troubleshooting notes
Improve package management examples
```

Schlechte Beispiele:

```text
update
fix
stuff
final
new
asdf
```

Eine gute Nachricht sollte später noch verständlich sein.

Man muss nicht jeden kleinen Satz erklären, aber man sollte erkennen können, was passiert ist.

---

## Commit-Nachrichten im Imperativ

Viele Projekte schreiben Commit-Nachrichten im Imperativ.

Beispiele:

```text
Add Git basics chapter
Update README
Fix typo
Remove old notes
Create Linux section
```

Das klingt auf Englisch manchmal wie ein Befehl, ist aber üblich.

Es beschreibt, was der Commit macht.

Beispiel:

```text
Add Git commits and history chapter
```

Bedeutung:

```text
Dieser Commit fügt das Kapitel über Commits und Historie hinzu.
```

---

## Kleine und sinnvolle Commits

Commits sollten nicht zu groß sein.

Schlecht:

```text
Update everything
```

Wenn dieser Commit 20 Dateien ändert, ist später schwer zu verstehen, was genau passiert ist.

Besser:

```text
Add Linux package management chapter
Add Linux networking chapter
Update Linux README links
Fix typo in Git README
```

Vorteile kleiner Commits:

- leichter zu verstehen
- leichter zu prüfen
- leichter rückgängig zu machen
- bessere Historie
- bessere Teamarbeit
- weniger Konflikte

Ein Commit sollte möglichst ein Thema oder einen Arbeitsschritt enthalten.

---

## Zu kleine Commits

Commits sollten aber auch nicht sinnlos klein sein.

Weniger sinnvoll:

```text
Add word
Add dot
Fix one letter
Change again
```

Besser ist ein sinnvoller Abschnitt.

Beispiel:

```text
Fix typos in Git README
```

Das kann mehrere kleine Schreibfehler zusammenfassen.

Gute Commits sind nicht maximal klein, sondern logisch zusammenhängend.

---

## git log

Mit `git log` zeigt man die Historie an.

```bash
git log
```

Die Ausgabe enthält:

- Commit-ID
- Autor
- Datum
- Commit-Nachricht

Beispiel:

```text
commit a1b2c3d4e5f6
Author: Bilgin Maystorov
Date:   Wed Aug 19 21:00:00 2026 +0200

    Add Git commits and history chapter
```

`git log` ist nützlich, wenn man die Entwicklung eines Projekts nachvollziehen möchte.

---

## git log --oneline

Für eine kompakte Ansicht nutzt man:

```bash
git log --oneline
```

Beispiel:

```text
a1b2c3d Add Git commits and history chapter
9f8e7d6 Add Git repository and working areas chapter
123abcd Add Git basics chapter
```

Das ist im Alltag oft übersichtlicher als das normale `git log`.

Man sieht schnell:

- Commit-ID kurz
- Commit-Nachricht
- Reihenfolge der Änderungen

---

## git log mit Begrenzung

Man kann nur die letzten Commits anzeigen.

```bash
git log --oneline -5
```

Das zeigt die letzten fünf Commits.

Auch möglich:

```bash
git log --oneline -10
```

Das ist praktisch bei großen Repositories mit langer Historie.

---

## Änderungen eines Commits anzeigen

Mit `git show` zeigt man Details zu einem Commit.

Letzten Commit anzeigen:

```bash
git show
```

Bestimmten Commit anzeigen:

```bash
git show commit-id
```

Beispiel:

```bash
git show a1b2c3d
```

`git show` zeigt:

- Commit-Nachricht
- Autor
- Datum
- geänderte Dateien
- konkrete Änderungen

Das ist hilfreich, wenn man später verstehen möchte, was ein bestimmter Commit genau gemacht hat.

---

## Commit-Historie als Projekt-Tagebuch

Eine gute Git-Historie wirkt wie ein technisches Projekttagebuch.

Beispiel:

```text
Create GitHub section structure
Add Git and GitHub section README
Add Git basics chapter
Add Git repository and working areas chapter
Add Git commits and history chapter
```

Man versteht sofort, wie der Bereich aufgebaut wurde.

Das ist besonders wichtig für öffentliche GitHub-Repositories, weil andere sehen können, ob ein Projekt sauber gepflegt wurde.

---

## Lokaler Commit und Push

Ein Commit ist zuerst nur lokal.

Beispiel:

```bash
git commit -m "Add Git commits and history chapter"
```

Nach diesem Befehl ist der Commit auf dem eigenen Rechner gespeichert.

Damit er auf GitHub erscheint:

```bash
git push
```

Unterschied:

| Befehl       | Bedeutung           |
| ------------ | ------------------- |
| `git commit` | lokal speichern     |
| `git push`   | zu GitHub hochladen |

Das wird am Anfang oft verwechselt.

---

## Prüfen, ob lokale Commits noch nicht gepusht sind

`git status` zeigt oft, ob lokale Commits noch nicht auf GitHub sind.

Beispiel:

```text
Your branch is ahead of 'origin/main' by 1 commit.
```

Das bedeutet:

Ein Commit existiert lokal, aber noch nicht auf GitHub.

Dann:

```bash
git push
```

Nach dem Push:

```bash
git status
```

Erwartung:

```text
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

---

## Commit nachträglich ändern mit amend

Manchmal möchte man den letzten Commit korrigieren.

Beispiel:

Man hat eine Datei vergessen und noch nicht gepusht.

```bash
git add vergessene-datei.md
git commit --amend
```

Oder Commit-Nachricht ändern:

```bash
git commit --amend -m "Better commit message"
```

Wichtig:

`--amend` verändert den letzten Commit.

Wenn der Commit schon gepusht wurde, sollte man vorsichtig sein, besonders in Teamprojekten.

Für Anfänger gilt:

```text
Amend am besten nur nutzen, wenn der Commit noch nicht gepusht wurde.
```

---

## Änderungen rückgängig machen

Git bietet mehrere Möglichkeiten, Änderungen rückgängig zu machen.

Wichtige Begriffe:

| Befehl                 | Bedeutung                                                       |
| ---------------------- | --------------------------------------------------------------- |
| `git restore`          | lokale Änderungen an Dateien verwerfen                          |
| `git restore --staged` | Datei aus Staging Area entfernen                                |
| `git revert`           | neuen Commit erstellen, der eine alte Änderung rückgängig macht |
| `git reset`            | Historie oder Staging zurücksetzen, vorsichtig nutzen           |

Für öffentliche oder geteilte Repositories ist `git revert` oft sicherer als `git reset`, weil die Historie nicht umgeschrieben wird.

Mehr dazu gehört zur Fehlersuche und Wiederherstellung.

---

## git revert kurz erklärt

`git revert` macht einen alten Commit rückgängig, indem ein neuer Commit erstellt wird.

Beispiel:

```bash
git revert commit-id
```

Vorteil:

Die Historie bleibt nachvollziehbar.

Beispiel:

```text
Add wrong config
Revert "Add wrong config"
```

Man sieht später, was passiert ist.

Das ist in Teamarbeit oft sauberer als die Historie umzuschreiben.

---

## git reset kurz erklärt

`git reset` kann Commits oder Staging-Zustände zurücksetzen.

Beispiel:

```bash
git reset --soft HEAD~1
```

Oder stärker:

```bash
git reset --hard HEAD~1
```

Wichtig:

`reset --hard` kann Änderungen löschen.

Deshalb sollte man `git reset --hard` nicht blind verwenden.

Für Anfänger gilt:

```text
Vor reset immer genau prüfen, was man tut.
```

Dieses Thema wird bei Fehlersuche und Wiederherstellung genauer behandelt.

---

## Dateien aus früheren Commits ansehen

Man kann ältere Zustände ansehen, ohne direkt alles zu ändern.

Historie prüfen:

```bash
git log --oneline
```

Commit anzeigen:

```bash
git show commit-id
```

Datei aus einem Commit anzeigen:

```bash
git show commit-id:pfad/zur/datei
```

Beispiel:

```bash
git show a1b2c3d:README.md
```

Das ist nützlich, wenn man wissen möchte, wie eine Datei früher aussah.

---

## Änderungen zwischen Commits vergleichen

Mit `git diff` kann man auch Commits vergleichen.

```bash
git diff commit1 commit2
```

Beispiel:

```bash
git diff a1b2c3d 9f8e7d6
```

Damit sieht man Unterschiede zwischen zwei Projektständen.

Das ist hilfreich, wenn man herausfinden möchte, welche Änderung zwischen zwei Punkten passiert ist.

---

## Autor und E-Mail in Commits

Commits enthalten Autorinformationen.

Anzeigen:

```bash
git log
```

Dort sieht man:

```text
Author: Name <email>
```

Deshalb ist die Git-Konfiguration wichtig.

Prüfen:

```bash
git config user.name
git config user.email
```

Bei öffentlichen GitHub-Repositories sollte man darauf achten, welche E-Mail-Adresse in Commits landet.

---

## Historie in GitHub

Auf GitHub kann man die Commit-Historie auch im Browser ansehen.

Dort sieht man:

- Commit-Nachrichten
- geänderte Dateien
- Zeitpunkt
- Autor
- Unterschiede zwischen Versionen

Das ist praktisch, wenn man ein Projekt schnell prüfen möchte.

Trotzdem sollte man die wichtigsten Befehle lokal kennen:

```bash
git log --oneline
git show
git diff
```

---

## Gute Gewohnheiten beim Committen

Gute Gewohnheiten:

1. Status prüfen:

```bash
git status
```

2. Änderungen ansehen:

```bash
git diff
```

3. Passende Dateien vormerken:

```bash
git add datei.md
```

4. Staged Änderungen prüfen:

```bash
git diff --staged
```

5. Commit erstellen:

```bash
git commit -m "Add clear message"
```

6. Hochladen:

```bash
git push
```

7. Sauberen Stand prüfen:

```bash
git status
```

Dieser Ablauf verhindert viele typische Git-Probleme.

---

## Typische Fehler

| Fehler                                  | Problem                            |
| --------------------------------------- | ---------------------------------- |
| zu selten committen                     | Änderungen werden unübersichtlich  |
| zu große Commits                        | Historie ist schwer verständlich   |
| schlechte Commit-Nachrichten            | später unklar, was gemacht wurde   |
| `git commit` und `git push` verwechseln | Änderung ist nur lokal             |
| `git add .` ohne Prüfung                | falsche Dateien landen im Commit   |
| `git diff` nicht nutzen                 | man speichert Änderungen blind     |
| private Daten committen                 | Sicherheitsproblem                 |
| amend nach Push ohne Verständnis        | Probleme in geteilten Repositories |
| reset --hard blind nutzen               | Arbeit kann verloren gehen         |
| Historie nie lesen                      | Git wird nur halb verstanden       |

---

## Praktische Beispiele

### Beispiel 1: Sauberer Commit für eine Datei

```bash
git status
git diff git-github/03-commits-und-historie.md
git add git-github/03-commits-und-historie.md
git diff --staged
git commit -m "Add Git commits and history chapter"
git push
```

Damit wird genau eine Datei geprüft, vorgemerkt, committed und hochgeladen.

### Beispiel 2: Historie kompakt anzeigen

```bash
git log --oneline -5
```

Das zeigt die letzten fünf Commits.

### Beispiel 3: Letzten Commit prüfen

```bash
git show
```

Damit sieht man, was im letzten Commit gespeichert wurde.

### Beispiel 4: Commit-Nachricht korrigieren

Nur wenn der Commit noch nicht gepusht wurde:

```bash
git commit --amend -m "Add Git commits and history chapter"
```

Danach prüfen:

```bash
git log --oneline -3
```

---

## Nützliche Befehle

| Befehl                       | Bedeutung                                   |
| ---------------------------- | ------------------------------------------- |
| `git status`                 | aktuellen Zustand anzeigen                  |
| `git add datei`              | Änderung für Commit vormerken               |
| `git diff`                   | nicht staged Änderungen anzeigen            |
| `git diff --staged`          | staged Änderungen anzeigen                  |
| `git commit -m "Text"`       | Commit erstellen                            |
| `git log`                    | vollständige Historie anzeigen              |
| `git log --oneline`          | kompakte Historie anzeigen                  |
| `git log --oneline -5`       | letzte fünf Commits anzeigen                |
| `git show`                   | letzten Commit anzeigen                     |
| `git show commit-id`         | bestimmten Commit anzeigen                  |
| `git push`                   | Commits zu GitHub hochladen                 |
| `git restore datei`          | lokale Änderungen verwerfen                 |
| `git restore --staged datei` | Datei aus Staging Area entfernen            |
| `git commit --amend`         | letzten Commit ändern                       |
| `git revert commit-id`       | Commit durch neuen Commit rückgängig machen |
| `git reset`                  | Zustand zurücksetzen, vorsichtig nutzen     |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration sind Commits und Historie wichtig, weil technische Arbeit nachvollziehbar bleiben muss.

In der Praxis bedeutet das:

- Änderungen an Dokumentation speichern
- Skripte versionieren
- Konfigurationsbeispiele nachvollziehbar pflegen
- Fehler nach Änderungen leichter finden
- Projektfortschritt sichtbar machen
- saubere GitHub-Repositories aufbauen
- Teamarbeit verständlicher machen
- Rückfragen zu Änderungen besser beantworten
- Lernprojekte professioneller dokumentieren

Ein guter FISI nutzt Commits nicht nur als Pflichtschritt, sondern als technische Dokumentation der eigenen Arbeit.

---

## Kurze Zusammenfassung

Ein Commit ist ein gespeicherter Projektstand in Git.

Die Git-Historie zeigt, wie sich ein Projekt entwickelt hat. Gute Commits sind logisch, nicht zu groß und haben verständliche Nachrichten.

Wichtige Befehle sind `git status`, `git diff`, `git add`, `git commit`, `git log`, `git log --oneline`, `git show`, `git push`, `git revert` und vorsichtig `git reset`.

Für FISI ist dieses Kapitel wichtig, weil Dokumentation, Skripte, Konfigurationen und Projekte nachvollziehbar versioniert werden müssen.
