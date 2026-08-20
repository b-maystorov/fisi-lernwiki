# 6. GitHub und Zusammenarbeit

In diesem Kapitel geht es um GitHub und Zusammenarbeit in Git-Projekten.

Git selbst ist die Versionsverwaltung. GitHub ist eine Plattform, auf der Git-Repositories online gespeichert, geteilt und gemeinsam bearbeitet werden können. GitHub wird für Quellcode, Dokumentation, Issues, Pull Requests, Reviews, Projektorganisation und öffentliche Portfolios genutzt.

Für Fachinformatiker für Systemintegration ist GitHub wichtig, weil viele technische Arbeiten im Team oder öffentlich dokumentiert werden: Skripte, Linux-Dokumentation, Docker-Projekte, Konfigurationsbeispiele, Netzwerkdokumentation und Projekt-Repositories.

---

## Kurz erklärt

GitHub ist eine Online-Plattform für Git-Repositories.

Mit GitHub kann man:

- Repositories online speichern
- Projekte öffentlich oder privat verwalten
- mit anderen Personen zusammenarbeiten
- Änderungen über Pull Requests prüfen
- Issues für Aufgaben und Fehler nutzen
- README-Dateien als Projektstartseite verwenden
- Dokumentation pflegen
- Releases veröffentlichen
- Portfolio-Projekte zeigen
- Open-Source-Projekte nutzen oder beitragen

GitHub ersetzt Git nicht.

GitHub nutzt Git.

Wichtige Begriffe:

| Begriff      | Bedeutung                                    |
| ------------ | -------------------------------------------- |
| Repository   | Projekt auf GitHub                           |
| README       | Startseite und Erklärung eines Repositories  |
| Issue        | Aufgabe, Fehler oder Diskussion              |
| Pull Request | Vorschlag für eine Änderung                  |
| Review       | Prüfung eines Pull Requests                  |
| Fork         | eigene Kopie eines fremden Repositories      |
| Clone        | Repository lokal herunterladen               |
| Star         | Repository markieren                         |
| Watch        | Benachrichtigungen für Repository aktivieren |
| Release      | veröffentlichter Projektstand                |

---

## Git und GitHub unterscheiden

Git ist das Werkzeug auf dem eigenen Rechner.

GitHub ist die Plattform im Internet.

| Bereich          | Git                              | GitHub                                             |
| ---------------- | -------------------------------- | -------------------------------------------------- |
| Art              | Versionsverwaltung               | Online-Plattform                                   |
| Ort              | lokal auf dem Rechner            | online                                             |
| Aufgabe          | Änderungen speichern             | Repositories hosten und Zusammenarbeit ermöglichen |
| Befehl / Nutzung | Terminalbefehle wie `git commit` | Weboberfläche, Pull Requests, Issues               |
| Internet nötig   | nein, für lokale Commits nicht   | ja                                                 |
| Beispiel         | `git log`, `git status`          | Repository-Seite, Pull Request, Issue              |

Wichtig:

Ein Commit ist zuerst lokal.  
Erst mit `git push` erscheint er auf GitHub.

---

## Repository auf GitHub

Ein Repository auf GitHub ist ein Projekt.

Ein Repository kann enthalten:

- Quellcode
- Markdown-Dokumentation
- Skripte
- Konfigurationsdateien
- Diagramme
- Beispiele
- Projektbeschreibung
- Issues
- Pull Requests
- Releases
- Wiki oder Dokumentation

Ein gutes Repository sollte nicht nur Dateien enthalten, sondern auch erklären, worum es geht.

Die wichtigste Datei ist oft:

```text
README.md
```

GitHub zeigt die README-Datei automatisch auf der Startseite des Repositories an.

---

## README auf GitHub

Die README ist die Startseite eines Repositories.

Eine gute README erklärt:

- Was ist das Projekt?
- Warum existiert es?
- Welche Technik wird genutzt?
- Wie ist das Projekt aufgebaut?
- Wie startet oder nutzt man es?
- Welche Dateien sind wichtig?
- Was wurde gelernt?
- Welche Grenzen hat das Projekt?
- Welche nächsten Schritte sind möglich?

Für ein Portfolio ist die README besonders wichtig.

Wenn jemand das Repository öffnet, entscheidet die README oft, ob das Projekt professionell wirkt.

---

## Öffentliche und private Repositories

GitHub-Repositories können öffentlich oder privat sein.

| Sichtbarkeit | Bedeutung                             |
| ------------ | ------------------------------------- |
| Public       | öffentlich sichtbar                   |
| Private      | nur für berechtigte Personen sichtbar |

Öffentliche Repositories eignen sich für:

- Portfolio
- Lernprojekte
- Dokumentation ohne private Daten
- Open-Source-Projekte
- Beispielprojekte

Private Repositories eignen sich für:

- Schulprojekte mit internen Inhalten
- Kundendaten
- private Notizen
- Experimente mit sensiblen Daten
- Projekte mit Zugangsdaten oder geschützten Informationen

Wichtig:

In öffentlichen Repositories dürfen keine Passwörter, Tokens, privaten Schlüssel, Kundendaten oder internen Informationen stehen.

---

## GitHub als Portfolio

GitHub kann wie ein technisches Portfolio genutzt werden.

Ein gutes Portfolio zeigt nicht nur fertige Ergebnisse, sondern auch saubere Arbeitsweise.

Wichtig sind:

- klare Repository-Namen
- gute README-Dateien
- saubere Ordnerstruktur
- verständliche Commit-Nachrichten
- keine privaten Daten
- nachvollziehbare Dokumentation
- realistische Projekte
- einfache Sprache
- technische Tiefe
- regelmäßige Pflege

Für FISI sind gute Portfolio-Projekte zum Beispiel:

- Linux-Lernwiki
- Docker-Testumgebung
- Ubuntu-Installation
- Python-Konsolenprojekt
- Datenbankprojekt
- Netzwerkdokumentation
- Home-Lab-Dokumentation
- Shell-Skripte für Admin-Aufgaben

---

## Zusammenarbeit auf GitHub

GitHub wird häufig für Teamarbeit genutzt.

Typische Zusammenarbeit:

1. Repository klonen
2. Branch erstellen
3. Änderungen machen
4. Commit erstellen
5. Branch pushen
6. Pull Request öffnen
7. Review durchführen
8. Änderungen anpassen
9. Pull Request mergen
10. Branch aufräumen

Dieser Ablauf verhindert, dass alle Personen direkt ungeprüft auf dem Hauptbranch arbeiten.

---

## Rechte und Rollen

In GitHub-Repositories können Personen unterschiedliche Rechte haben.

Typische Rollen oder Berechtigungen:

| Rolle / Zugriff | Bedeutung                          |
| --------------- | ---------------------------------- |
| Read            | Repository lesen                   |
| Triage          | Issues und Pull Requests verwalten |
| Write           | Änderungen pushen                  |
| Maintain        | Repository verwalten               |
| Admin           | volle Verwaltung                   |

Nicht jede Person sollte Admin-Rechte haben.

Grundregel:

```text
Nur so viele Rechte wie nötig.
```

Das passt zum Sicherheitsprinzip der minimalen Rechte.

---

## Issues

Ein Issue ist eine Aufgabe, ein Fehlerbericht oder eine Diskussion in einem Repository.

Issues können genutzt werden für:

- Bugs
- neue Funktionen
- Dokumentationsaufgaben
- Verbesserungen
- Fragen
- Ideen
- To-do-Liste
- Planung

Beispiel für ein Issue:

```text
Titel: Linux README um Kapitelübersicht erweitern

Beschreibung:
Die README im Linux-Ordner soll eine Tabelle mit allen Kapiteln enthalten.
Zusätzlich soll kurz erklärt werden, warum Linux für FISI wichtig ist.
```

Issues helfen, Arbeit sichtbar und planbar zu machen.

---

## Gute Issues schreiben

Ein gutes Issue ist klar und konkret.

Es sollte enthalten:

- kurzer Titel
- Beschreibung des Problems oder Ziels
- betroffene Datei oder Funktion
- gewünschtes Ergebnis
- mögliche Hinweise
- keine privaten Daten

Schlecht:

```text
geht nicht
```

Besser:

```text
SSH-Dokumentation um Rechte für private Schlüssel ergänzen
```

Noch besser:

```text
Die Datei git-github/09-ssh-und-mehrere-github-konten.md soll erklären, warum private SSH-Schlüssel meistens chmod 600 benötigen.
```

Je genauer ein Issue ist, desto leichter kann man daran arbeiten.

---

## Labels

Labels helfen, Issues und Pull Requests zu sortieren.

Typische Labels:

| Label              | Bedeutung                 |
| ------------------ | ------------------------- |
| `bug`              | Fehler                    |
| `documentation`    | Dokumentation             |
| `enhancement`      | Verbesserung              |
| `question`         | Frage                     |
| `good first issue` | gute Aufgabe für Einstieg |
| `help wanted`      | Hilfe erwünscht           |
| `wontfix`          | wird nicht umgesetzt      |

Labels sind besonders nützlich bei größeren Projekten.

In kleinen Lernprojekten sind sie nicht zwingend nötig, aber sie können Ordnung schaffen.

---

## Pull Request

Ein Pull Request ist ein Vorschlag, Änderungen aus einem Branch in einen anderen Branch zu übernehmen.

Typischer Fall:

```text
Branch add-linux-chapter soll in main übernommen werden.
```

Ein Pull Request zeigt:

- welche Dateien geändert wurden
- welche Commits enthalten sind
- welche Unterschiede existieren
- Diskussionen und Kommentare
- Reviews
- Checks oder Tests, falls vorhanden

Pull Requests machen Änderungen prüfbar, bevor sie in den Hauptbranch kommen.

---

## Warum Pull Requests wichtig sind

Pull Requests helfen bei Qualität und Zusammenarbeit.

Vorteile:

- Änderungen werden sichtbar
- andere Personen können prüfen
- Fehler werden früher gefunden
- Diskussion ist direkt an der Änderung
- Code und Dokumentation bleiben sauberer
- große Änderungen werden kontrollierter
- Historie bleibt nachvollziehbar

Auch bei Dokumentation sind Pull Requests sinnvoll.

Beispiel:

Eine Person schreibt ein Kapitel.  
Eine andere Person prüft Rechtschreibung, Struktur und technische Korrektheit.  
Danach wird gemerged.

---

## Typischer Pull-Request-Ablauf

Ein einfacher Ablauf:

```bash
git switch main
git pull
git switch -c add-github-collaboration

# Dateien bearbeiten

git add git-github/06-github-und-zusammenarbeit.md
git commit -m "Add GitHub collaboration chapter"
git push -u origin add-github-collaboration
```

Danach öffnet man auf GitHub einen Pull Request.

Nach Review und Merge:

```bash
git switch main
git pull
git branch -d add-github-collaboration
```

Wenn der Remote-Branch nicht mehr gebraucht wird:

```bash
git push origin --delete add-github-collaboration
```

---

## Review

Ein Review ist die Prüfung eines Pull Requests.

Dabei wird kontrolliert:

- Ist die Änderung korrekt?
- Ist die Struktur sinnvoll?
- Gibt es Fehler?
- Ist die Dokumentation verständlich?
- Sind private Daten enthalten?
- Passt die Änderung zum Ziel?
- Gibt es technische Probleme?
- Sind Commit-Nachrichten sinnvoll?

Ein Review ist keine persönliche Kritik.

Ein Review soll die Qualität des Projekts verbessern.

---

## Gute Review-Kommentare

Gute Review-Kommentare sind konkret und respektvoll.

Schlecht:

```text
falsch
```

Besser:

```text
Der Befehl sollte hier mit sudo gezeigt werden, weil die Datei unter /etc liegt.
```

Schlecht:

```text
mach besser
```

Besser:

```text
Vielleicht wäre hier eine Tabelle sinnvoll, weil die Unterschiede zwischen pull und push dann klarer werden.
```

Gute Reviews helfen der anderen Person, die Änderung zu verbessern.

---

## Änderungen nach Review

Nach einem Review kann man Änderungen im gleichen Branch machen.

Ablauf:

```bash
# Datei bearbeiten
git status
git add datei.md
git commit -m "Improve explanation after review"
git push
```

Der Pull Request aktualisiert sich automatisch, wenn man neue Commits auf denselben Branch pusht.

Das ist praktisch, weil die Diskussion und die Änderung zusammenbleiben.

---

## Merge auf GitHub

Wenn ein Pull Request akzeptiert wurde, kann er gemerged werden.

GitHub bietet verschiedene Merge-Arten.

Typische Varianten:

| Variante         | Bedeutung                                      |
| ---------------- | ---------------------------------------------- |
| Merge commit     | erstellt einen Merge Commit                    |
| Squash and merge | fasst mehrere Commits zu einem Commit zusammen |
| Rebase and merge | übernimmt Commits linear ohne Merge Commit     |

Einfache Einordnung:

- Merge commit zeigt die Branch-Zusammenführung sichtbar.
- Squash macht aus mehreren kleinen Commits einen sauberen Commit.
- Rebase erzeugt eine lineare Historie.

Für den Anfang reicht es, Merge und Squash grundsätzlich zu verstehen.

---

## Konflikte auf GitHub

Auch Pull Requests können Konflikte haben.

Ein Konflikt bedeutet:

Git kann Änderungen nicht automatisch zusammenführen.

Typischer Grund:

- dieselbe Datei wurde in zwei Branches an derselben Stelle geändert
- Datei wurde in einem Branch gelöscht und im anderen geändert
- Struktur wurde gleichzeitig verändert

Konflikte müssen manuell gelöst werden.

Oft ist es einfacher, Konflikte lokal zu lösen:

```bash
git switch branchname
git pull --rebase origin main
# Konflikte lösen
git add datei.md
git rebase --continue
git push
```

Je nach Situation kann auch ein normaler Merge genutzt werden.

---

## Fork

Ein Fork ist eine eigene Kopie eines fremden Repositories auf GitHub.

Forks werden oft genutzt, wenn man keine direkten Schreibrechte auf das Originalprojekt hat.

Ablauf:

1. Repository forken
2. eigenen Fork klonen
3. Branch erstellen
4. Änderung machen
5. Push zum eigenen Fork
6. Pull Request zum Originalprojekt öffnen

Forks sind besonders wichtig bei Open-Source-Projekten.

---

## origin und upstream bei Forks

Bei Forks gibt es oft zwei Remotes.

| Remote     | Bedeutung           |
| ---------- | ------------------- |
| `origin`   | eigener Fork        |
| `upstream` | Original-Repository |

Beispiel:

```bash
git remote -v
```

Mögliche Ausgabe:

```text
origin    git@github.com:mein-user/projekt.git
upstream  git@github.com:original-user/projekt.git
```

Änderungen vom Original holen:

```bash
git fetch upstream
git switch main
git merge upstream/main
```

Oder mit Rebase:

```bash
git pull --rebase upstream main
```

Für einfache eigene Repositories braucht man `upstream` meistens nicht.

---

## Clone

Mit `git clone` lädt man ein Repository lokal herunter.

Beispiel:

```bash
git clone git@github.com:user/repository.git
```

Danach:

```bash
cd repository
git status
git remote -v
```

Beim Klonen wird normalerweise automatisch das Remote `origin` eingerichtet.

Clone ist wichtig, wenn man:

- ein GitHub-Projekt lokal bearbeiten möchte
- auf einem neuen Rechner arbeitet
- ein Schul- oder Teamprojekt herunterlädt
- einen Fork lokal nutzen möchte

---

## GitHub README und Markdown

GitHub stellt Markdown-Dateien direkt formatiert dar.

Typische Markdown-Dateien:

```text
README.md
docs/installation.md
linux/README.md
git-github/README.md
```

Markdown eignet sich gut für:

- Dokumentation
- Anleitungen
- Tabellen
- Codeblöcke
- Projektübersichten
- Lern-Wikis
- technische Notizen

Eine gute Markdown-Struktur macht Repositories deutlich professioneller.

---

## GitHub Issues für Lernprojekte

Auch eigene Lernprojekte können Issues nutzen.

Beispiele:

```text
Issue: Linux Kapitel zu Cronjobs ergänzen
Issue: README mit Kapitelübersicht verbessern
Issue: Docker Troubleshooting schreiben
Issue: SSH-Abschnitt um mehrere GitHub-Konten erweitern
```

Das wirkt nicht nur professionell, sondern hilft auch bei der Planung.

Man sieht:

- was erledigt ist
- was offen ist
- welche Aufgaben geplant sind
- welche Verbesserungen später kommen

---

## GitHub Projects

GitHub Projects kann zur Planung von Aufgaben genutzt werden.

Man kann Issues und Aufgaben in Spalten oder Boards organisieren.

Typische Spalten:

```text
To do
In progress
Done
```

Für kleine Lernprojekte ist das nicht unbedingt nötig.

Für größere Projekte oder Teamarbeit kann es sehr hilfreich sein.

Wichtig ist nicht das Tool selbst, sondern die saubere Organisation der Arbeit.

---

## Releases

Ein Release ist ein veröffentlichter Projektstand.

Releases werden häufig genutzt für:

- Softwareversionen
- fertige Projektstände
- Abgaben
- Downloads
- stabile Versionen

Beispiel:

```text
v1.0.0
```

Ein Release kann enthalten:

- Versionsnummer
- Beschreibung
- Changelog
- Dateien zum Download
- Quellcode-Archiv

Für reine Lern-Wikis sind Releases nicht immer nötig.

Für Softwareprojekte oder Tools sind sie sinnvoller.

---

## Tags

Ein Tag markiert einen bestimmten Commit.

Beispiel:

```bash
git tag v1.0.0
git push origin v1.0.0
```

Tags werden oft für Versionen genutzt.

Beispiel:

```text
v1.0.0
v1.1.0
v2.0.0
```

Ein Tag ist praktisch, wenn man einen bestimmten Projektstand dauerhaft markieren möchte.

---

## Wiki und Dokumentation

GitHub bietet auch Wiki-Funktionen, aber oft reicht eine normale Ordnerstruktur im Repository.

Beispiel:

```text
docs/
linux/
git-github/
netzwerke/
```

Vorteile von Dokumentation direkt im Repository:

- zusammen mit Projekt versioniert
- Pull Requests möglich
- Markdown-Dateien sichtbar
- einfacher lokal bearbeitbar
- gut für Portfolio
- klare Struktur

Für Lern- und Portfolio-Projekte ist Dokumentation im Repository meistens sehr sinnvoll.

---

## GitHub Actions kurz erklärt

GitHub Actions kann automatische Abläufe ausführen.

Beispiele:

- Tests ausführen
- Markdown prüfen
- Code formatieren
- Website bauen
- Docker-Image bauen
- Deployment starten

Für den Anfang ist GitHub Actions nicht zwingend notwendig.

Aber es ist gut zu wissen:

GitHub kann nicht nur Dateien speichern, sondern auch Automatisierung ausführen.

Für FISI kann das später im Bereich DevOps interessant werden.

---

## Sicherheit auf GitHub

Sicherheit ist bei GitHub sehr wichtig.

Nicht veröffentlichen:

- Passwörter
- private SSH-Schlüssel
- API-Tokens
- `.env` mit echten Zugangsdaten
- private Kundendaten
- interne Dokumente
- sensible Screenshots
- geheime URLs
- personenbezogene Daten

Auch gelöschte Dateien können noch in der Git-Historie existieren.

Wenn ein Secret gepusht wurde, sollte man es als kompromittiert betrachten und ersetzen.

---

## `.gitignore` bei GitHub-Projekten

Eine `.gitignore` hilft, unnötige oder sensible Dateien nicht zu committen.

Beispiel:

```gitignore
.env
*.log
__pycache__/
.venv/
private/
.vscode/
```

Wichtig:

`.gitignore` wirkt nicht automatisch auf Dateien, die bereits getrackt werden.

Wenn eine Datei schon im Repository ist:

```bash
git rm --cached datei
```

Danach committen:

```bash
git commit -m "Stop tracking private file"
```

---

## Gute Repository-Struktur

Eine gute Struktur macht ein Repository verständlich.

Beispiel für Dokumentation:

```text
repository/
├── README.md
├── linux/
├── git-github/
├── docker/
├── netzwerke/
└── cheatsheets/
```

Beispiel für ein Skriptprojekt:

```text
project/
├── README.md
├── scripts/
├── configs/
├── docs/
└── examples/
```

Eine klare Struktur hilft bei:

- Navigation
- Wartung
- Zusammenarbeit
- Reviews
- Portfolio-Wirkung
- späterer Fehlersuche

---

## Gute Zusammenarbeit

Gute Zusammenarbeit auf GitHub bedeutet nicht nur Befehle ausführen.

Wichtig sind:

- klare Aufgaben
- verständliche Issues
- kleine Pull Requests
- gute Commit-Nachrichten
- keine privaten Daten
- respektvolle Reviews
- aktuelle Branches
- Tests oder Prüfung nach Änderungen
- saubere Dokumentation
- klare Kommunikation

Technische Arbeit wird besser, wenn Kommunikation und Struktur sauber sind.

---

## Typischer Team-Workflow

Ein einfacher Team-Workflow:

```bash
git switch main
git pull
git switch -c fix-readme-links

# Änderung machen

git status
git diff
git add README.md
git commit -m "Fix README links"
git push -u origin fix-readme-links
```

Dann auf GitHub:

1. Pull Request öffnen
2. Beschreibung schreiben
3. Review abwarten
4. Änderungen bei Bedarf anpassen
5. Merge durchführen
6. Branch löschen

Dieser Ablauf ist deutlich sauberer als direkt ungeprüft auf `main` zu pushen.

---

## Typische Fehler bei GitHub-Zusammenarbeit

| Fehler                          | Problem                              |
| ------------------------------- | ------------------------------------ |
| direkt auf `main` arbeiten      | Änderungen werden nicht geprüft      |
| Pull Request zu groß machen     | Review wird schwer                   |
| schlechte PR-Beschreibung       | Ziel der Änderung ist unklar         |
| Issues nicht nutzen             | Aufgaben gehen verloren              |
| keine README pflegen            | Repository wirkt unklar              |
| private Daten pushen            | Sicherheitsproblem                   |
| Konfliktmarker nicht entfernen  | Dateien wirken kaputt                |
| Branch nach Merge nicht löschen | Repository wird unübersichtlich      |
| Reviews persönlich nehmen       | Zusammenarbeit wird schlechter       |
| GitHub und Git verwechseln      | lokale und online Arbeit wird unklar |

---

## Praktische Beispiele

### Beispiel 1: Repository klonen

```bash
git clone git@github.com:user/repository.git
cd repository
git status
git remote -v
```

Damit lädt man ein GitHub-Repository lokal herunter und prüft die Verbindung.

### Beispiel 2: Branch für Pull Request erstellen

```bash
git switch main
git pull
git switch -c update-readme
```

Danach Dateien bearbeiten, committen und pushen:

```bash
git add README.md
git commit -m "Update README"
git push -u origin update-readme
```

### Beispiel 3: Pull Request nach Review aktualisieren

```bash
# Datei verbessern
git status
git add README.md
git commit -m "Improve README after review"
git push
```

Der Pull Request wird automatisch aktualisiert.

### Beispiel 4: Nach Merge aufräumen

```bash
git switch main
git pull
git branch -d update-readme
git push origin --delete update-readme
```

Damit ist der lokale und entfernte Branch aufgeräumt.

---

## Nützliche Befehle

| Befehl                            | Bedeutung                           |
| --------------------------------- | ----------------------------------- |
| `git clone url`                   | Repository herunterladen            |
| `git remote -v`                   | Remotes anzeigen                    |
| `git switch -c branch`            | neuen Branch erstellen              |
| `git push -u origin branch`       | Branch zu GitHub hochladen          |
| `git pull`                        | Änderungen von GitHub holen         |
| `git status`                      | lokalen Zustand prüfen              |
| `git diff`                        | Änderungen prüfen                   |
| `git branch`                      | lokale Branches anzeigen            |
| `git branch -a`                   | lokale und Remote-Branches anzeigen |
| `git branch -d branch`            | lokalen Branch löschen              |
| `git push origin --delete branch` | Remote-Branch löschen               |
| `git fetch upstream`              | Änderungen vom Original-Repo holen  |
| `git tag v1.0.0`                  | Tag erstellen                       |
| `git push origin v1.0.0`          | Tag hochladen                       |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist GitHub eine wichtige Plattform für technische Zusammenarbeit und Dokumentation.

In der Praxis bedeutet das:

- Repositories für Projekte nutzen
- technische Dokumentation sauber pflegen
- Skripte versionieren
- Konfigurationsbeispiele teilen
- Issues für Aufgaben nutzen
- Pull Requests verstehen
- Reviews durchführen
- private und öffentliche Repositories unterscheiden
- keine sensiblen Daten veröffentlichen
- GitHub als Portfolio sinnvoll einsetzen
- Teamarbeit nachvollziehbar gestalten

Ein guter FISI nutzt GitHub nicht nur als Dateiablage, sondern als Werkzeug für strukturierte Projektarbeit, Dokumentation und Zusammenarbeit.

---

## Kurze Zusammenfassung

GitHub ist eine Plattform für Git-Repositories.

Wichtige Funktionen sind Repositories, README-Dateien, Issues, Pull Requests, Reviews, Forks, Releases, Tags und Projektorganisation.

Für Zusammenarbeit sind Branches, Pull Requests und Reviews besonders wichtig. Dadurch können Änderungen geprüft werden, bevor sie in den Hauptbranch übernommen werden.

Für FISI ist GitHub wichtig, weil Dokumentation, Skripte, Konfigurationsbeispiele und Projekte sauber versioniert, geteilt und professionell präsentiert werden können.
