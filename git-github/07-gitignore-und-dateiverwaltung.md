# 7. `.gitignore` und Dateiverwaltung

In diesem Kapitel geht es um `.gitignore` und den sauberen Umgang mit Dateien in Git.

Nicht jede Datei in einem Projekt soll versioniert werden. Manche Dateien sind nur lokal wichtig, manche entstehen automatisch, manche enthalten private Informationen und manche würden das Repository unnötig groß oder unsicher machen. Mit `.gitignore` kann man festlegen, welche Dateien Git ignorieren soll.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil in IT-Projekten oft Skripte, Konfigurationen, Logs, Testdateien, virtuelle Umgebungen und private Daten vorkommen. Man muss wissen, was in ein Repository gehört und was nicht.

---

## Kurz erklärt

Die Datei `.gitignore` sagt Git, welche Dateien und Ordner nicht verfolgt werden sollen.

Typische Dateien, die ignoriert werden:

- temporäre Dateien
- Logdateien
- Cache-Dateien
- lokale Editor-Dateien
- virtuelle Python-Umgebungen
- private Notizen
- `.env`-Dateien
- Passwörter
- Tokens
- Build-Dateien
- automatisch erzeugte Dateien

Beispiel:

```gitignore
*.log
.env
.venv/
__pycache__/
.vscode/
private/
```

Wichtig:

`.gitignore` wirkt vor allem auf Dateien, die Git noch nicht verfolgt.

Wenn eine Datei bereits getrackt wird, wird sie nicht automatisch ignoriert.

---

## Warum `.gitignore` wichtig ist

Ein Git-Repository soll sauber, sicher und nachvollziehbar bleiben.

Ohne `.gitignore` können unnötige oder gefährliche Dateien ins Repository gelangen.

Beispiele:

- private Zugangsdaten
- API-Tokens
- `.env`-Dateien
- private SSH-Schlüssel
- Logdateien
- Cache-Ordner
- große generierte Dateien
- lokale IDE-Einstellungen
- Testdaten mit privaten Inhalten
- temporäre Dateien

Das kann zu Problemen führen:

| Problem                      | Beispiel                                           |
| ---------------------------- | -------------------------------------------------- |
| Sicherheitsrisiko            | Passwort wird veröffentlicht                       |
| unübersichtliches Repository | viele Cache-Dateien werden getrackt                |
| unnötig große Historie       | große Dateien landen in Git                        |
| Teamprobleme                 | lokale Editor-Einstellungen überschreiben sich     |
| Datenschutzproblem           | private oder personenbezogene Daten werden gepusht |

Eine gute `.gitignore` schützt vor vielen typischen Git-Problemen.

---

## Was gehört in ein Repository?

In ein Repository gehören Dateien, die für das Projekt wichtig sind.

Typische sinnvolle Dateien:

- Quellcode
- Markdown-Dokumentation
- README-Dateien
- Beispielkonfigurationen
- Skripte
- Projektstruktur
- kleine Beispieldaten
- Dockerfile
- docker-compose.yml
- requirements.txt
- Installationsanleitung
- Lizenzdatei
- `.gitignore`

Beispiele:

```text
README.md
docs/installation.md
scripts/check-system.sh
Dockerfile
docker-compose.yml
requirements.txt
.gitignore
```

Diese Dateien helfen, das Projekt zu verstehen, zu starten oder weiterzuentwickeln.

---

## Was gehört nicht in ein Repository?

Nicht ins Repository gehören Dateien, die privat, automatisch erzeugt oder lokal abhängig sind.

Typische Beispiele:

```text
.env
*.log
__pycache__/
.venv/
node_modules/
.vscode/
.idea/
private/
secrets/
id_rsa
id_ed25519
```

Besonders gefährlich sind:

- Passwörter
- Tokens
- private Schlüssel
- echte Kundendaten
- interne Dokumente
- personenbezogene Daten
- Zugangsdaten zu Servern
- private Screenshots
- sensible IP-Adressen oder Hostnamen

Wenn ein Repository öffentlich ist, muss man besonders vorsichtig sein.

---

## `.gitignore` erstellen

Eine `.gitignore` liegt meistens im Hauptordner eines Repositories.

Beispiel:

```text
projekt/
├── README.md
├── .gitignore
├── scripts/
└── docs/
```

Datei erstellen:

```bash
touch .gitignore
```

Oder mit Editor öffnen:

```bash
nano .gitignore
```

Danach Regeln eintragen.

Beispiel:

```gitignore
*.log
.env
.venv/
__pycache__/
```

Dann committen:

```bash
git add .gitignore
git commit -m "Add gitignore"
git push
```

---

## Einfache `.gitignore`-Regeln

Eine `.gitignore` besteht aus Mustern.

Beispiele:

```gitignore
*.log
.env
private/
temp.txt
```

Bedeutung:

| Regel      | Bedeutung                          |
| ---------- | ---------------------------------- |
| `*.log`    | alle Dateien mit `.log` ignorieren |
| `.env`     | Datei `.env` ignorieren            |
| `private/` | Ordner `private` ignorieren        |
| `temp.txt` | Datei `temp.txt` ignorieren        |

Ordner erkennt man meistens am `/` am Ende.

---

## Kommentare in `.gitignore`

Kommentare beginnen mit `#`.

Beispiel:

```gitignore
# Python cache
__pycache__/
*.pyc

# Local environment files
.env
.venv/

# Logs
*.log
```

Kommentare helfen, die Datei später zu verstehen.

Eine gute `.gitignore` ist nicht nur eine Liste, sondern auch etwas dokumentiert.

---

## Wildcards

In `.gitignore` kann man Platzhalter nutzen.

| Muster  | Bedeutung                     |
| ------- | ----------------------------- |
| `*.log` | alle `.log`-Dateien           |
| `*.tmp` | alle `.tmp`-Dateien           |
| `test*` | alles, was mit `test` beginnt |
| `*.pyc` | Python-Bytecode-Dateien       |
| `*.bak` | Backup-Dateien                |

Beispiele:

```gitignore
*.log
*.tmp
*.bak
*.swp
```

Das ist praktisch für automatisch erzeugte oder temporäre Dateien.

---

## Ordner ignorieren

Ordner werden mit `/` am Ende ignoriert.

Beispiel:

```gitignore
.venv/
__pycache__/
node_modules/
private/
```

Bedeutung:

| Regel           | Bedeutung                               |
| --------------- | --------------------------------------- |
| `.venv/`        | virtuelle Python-Umgebung ignorieren    |
| `__pycache__/`  | Python-Cache ignorieren                 |
| `node_modules/` | JavaScript-Abhängigkeiten ignorieren    |
| `private/`      | private Notizen oder Dateien ignorieren |

Ordner mit vielen automatisch erzeugten Dateien sollten fast nie ins Repository.

---

## Bestimmte Datei erlauben

Manchmal möchte man einen Ordner ignorieren, aber eine bestimmte Datei darin behalten.

Dafür nutzt man `!`.

Beispiel:

```gitignore
logs/
!logs/.gitkeep
```

Bedeutung:

- der Ordner `logs/` wird ignoriert
- die Datei `logs/.gitkeep` wird trotzdem erlaubt

Das nutzt man manchmal, wenn ein leerer Ordner im Repository sichtbar bleiben soll.

Git speichert leere Ordner normalerweise nicht direkt.

Mit `.gitkeep` kann man einen Ordner trotzdem versionieren.

---

## Beispiel `.gitignore` für Python

Für Python-Projekte ist oft sinnvoll:

```gitignore
# Python cache
__pycache__/
*.pyc
*.pyo

# Virtual environments
.venv/
venv/

# Environment variables
.env

# Test and coverage output
.coverage
htmlcov/

# Editor files
.vscode/
.idea/

# Logs
*.log
```

Wichtig:

Die virtuelle Umgebung enthält viele installierte Pakete und gehört normalerweise nicht ins Repository.

Stattdessen dokumentiert man Abhängigkeiten zum Beispiel in:

```text
requirements.txt
```

---

## Beispiel `.gitignore` für Linux- und Admin-Projekte

Für Linux-Dokumentation und Admin-Skripte kann eine `.gitignore` so aussehen:

```gitignore
# Logs
*.log

# Temporary files
*.tmp
*.bak
*.swp

# Private notes
private/
notes-private/

# Environment files
.env

# Editor folders
.vscode/
.idea/

# Local output
output/
reports/
```

Je nach Projekt können `output/` oder `reports/` auch sinnvoll sein, wenn sie nur automatisch erzeugte lokale Ergebnisse enthalten.

Wenn Reports Teil der Dokumentation sind, sollten sie nicht ignoriert werden.

---

## Beispiel `.gitignore` für Docker-Projekte

Für Docker-Projekte kann sinnvoll sein:

```gitignore
# Environment variables
.env

# Logs
*.log

# Local data
data/
tmp/

# Editor files
.vscode/
.idea/

# OS files
.DS_Store
Thumbs.db
```

Wichtig:

Bei Docker muss man genau überlegen, ob `data/` ignoriert werden soll.

Wenn dort echte Datenbanken, Volumes oder lokale Testdaten liegen, gehören sie meistens nicht ins Repository.

Wenn dort kleine Beispieldaten liegen, können sie sinnvoll sein.

---

## `.env`-Dateien

`.env`-Dateien enthalten oft Umgebungsvariablen.

Beispiel:

```env
DB_USER=admin
DB_PASSWORD=secret
API_TOKEN=abc123
```

Solche Dateien dürfen mit echten Werten nicht in öffentliche Repositories.

Deshalb häufig:

```gitignore
.env
```

Stattdessen kann man eine Beispieldatei nutzen:

```text
.env.example
```

Diese enthält keine echten Secrets.

Beispiel:

```env
DB_USER=example_user
DB_PASSWORD=change_me
API_TOKEN=your_token_here
```

`.env.example` darf ins Repository, wenn keine echten Daten enthalten sind.

---

## Private Schlüssel niemals committen

Private SSH-Schlüssel dürfen niemals in GitHub landen.

Typische private Schlüssel:

```text
id_rsa
id_ed25519
```

Öffentliche Schlüssel enden oft auf:

```text
.pub
```

Beispiel:

```text
id_ed25519
id_ed25519.pub
```

Der private Schlüssel ohne `.pub` muss geheim bleiben.

Wenn ein privater Schlüssel veröffentlicht wurde, sollte man ihn nicht mehr benutzen und einen neuen Schlüssel erzeugen.

---

## Bereits getrackte Dateien werden nicht automatisch ignoriert

Das ist einer der wichtigsten Punkte.

Wenn eine Datei schon von Git verfolgt wird, reicht ein Eintrag in `.gitignore` nicht.

Beispiel:

Die Datei `.env` wurde bereits committed.

Dann fügt man hinzu:

```gitignore
.env
```

Aber Git verfolgt `.env` trotzdem weiter.

Lösung:

```bash
git rm --cached .env
```

Danach committen:

```bash
git add .gitignore
git commit -m "Stop tracking env file"
git push
```

Die Datei bleibt lokal bestehen, wird aber nicht mehr von Git getrackt.

---

## `git rm --cached`

`git rm --cached` entfernt eine Datei aus dem Git-Tracking, löscht sie aber nicht lokal.

Beispiel:

```bash
git rm --cached .env
```

Bedeutung:

| Teil       | Bedeutung                                      |
| ---------- | ---------------------------------------------- |
| `git rm`   | Datei aus Git entfernen                        |
| `--cached` | nur aus Git-Tracking entfernen, lokal behalten |
| `.env`     | betroffene Datei                               |

Danach sollte die Datei in `.gitignore` stehen.

Sonst würde Git sie wieder als untracked anzeigen.

---

## Datei komplett aus Git und lokal löschen

Wenn eine Datei aus Git und vom lokalen Dateisystem gelöscht werden soll:

```bash
git rm datei.md
```

Danach committen:

```bash
git commit -m "Remove old file"
```

Unterschied:

| Befehl                  | Wirkung                                               |
| ----------------------- | ----------------------------------------------------- |
| `git rm datei`          | entfernt Datei aus Git und lokal                      |
| `git rm --cached datei` | entfernt Datei nur aus Git-Tracking, lokal bleibt sie |

Das ist wichtig bei sensiblen Dateien.

---

## Sensible Daten in der Historie

Wenn ein Passwort oder Token einmal committed wurde, kann es noch in der Git-Historie stehen.

Auch wenn man die Datei später löscht, kann der alte Commit die Information noch enthalten.

Deshalb gilt:

```text
Ein gepushtes Secret gilt als kompromittiert.
```

Man sollte dann:

- Passwort ändern
- Token widerrufen
- SSH-Schlüssel ersetzen
- betroffene Zugänge prüfen
- Repository-Historie bereinigen, wenn nötig
- Ursache dokumentieren

Das reine Löschen in einem neuen Commit reicht bei echten Secrets nicht aus.

---

## Dateistatus prüfen

Mit `git status` prüft man, welche Dateien Git sieht.

```bash
git status
```

Typische Zustände:

| Zustand   | Bedeutung                             |
| --------- | ------------------------------------- |
| untracked | Git kennt Datei noch nicht            |
| modified  | Datei wurde geändert                  |
| staged    | Datei ist für Commit vorgemerkt       |
| deleted   | Datei wurde gelöscht                  |
| renamed   | Datei wurde umbenannt oder verschoben |

Vor jedem Commit sollte man den Status prüfen.

So erkennt man auch, ob unerwartete Dateien auftauchen.

---

## Dateien gezielt adden

Besser als blind alles zu adden:

```bash
git add git-github/07-gitignore-und-dateiverwaltung.md
```

Oder mehrere gezielte Dateien:

```bash
git add README.md .gitignore
```

Alle Änderungen:

```bash
git add .
```

`git add .` ist nicht falsch, aber man sollte vorher wissen, was geändert wurde.

Sauberer Ablauf:

```bash
git status
git diff
git add datei.md
git status
git commit -m "Add chapter"
```

---

## Dateien umbenennen

Eine Datei kann mit `mv` umbenannt werden.

```bash
mv alter-name.md neuer-name.md
```

Danach:

```bash
git status
git add alter-name.md neuer-name.md
git commit -m "Rename file"
```

Oder direkt mit Git:

```bash
git mv alter-name.md neuer-name.md
git commit -m "Rename file"
```

`git mv` ist praktisch, weil Git die Umbenennung direkt vormerkt.

---

## Dateien verschieben

Dateien können in andere Ordner verschoben werden.

Beispiel:

```bash
mv notes.md docs/notes.md
```

Danach:

```bash
git status
git add notes.md docs/notes.md
git commit -m "Move notes to docs folder"
```

Oder:

```bash
git mv notes.md docs/notes.md
git commit -m "Move notes to docs folder"
```

Verschieben ist für Git eine Kombination aus Entfernen am alten Ort und Hinzufügen am neuen Ort.

---

## Dateien löschen

Datei löschen:

```bash
rm old-file.md
```

Danach Git informieren:

```bash
git add old-file.md
git commit -m "Remove old file"
```

Oder direkt mit Git:

```bash
git rm old-file.md
git commit -m "Remove old file"
```

Wichtig:

Auch das Löschen einer Datei ist eine Änderung, die committed werden muss.

---

## Große Dateien

Git ist nicht ideal für sehr große Dateien.

Problematische Dateien können sein:

- Videos
- große ZIP-Archive
- ISO-Dateien
- Datenbank-Dumps
- VM-Images
- große Logdateien
- große Binärdateien

Probleme:

- Repository wird langsam
- Klonen dauert lange
- Historie wird groß
- GitHub kann Größenlimits haben
- Änderungen an Binärdateien sind schwer nachvollziehbar

Für große Dateien nutzt man je nach Projekt andere Lösungen, zum Beispiel Releases, externe Speicherorte oder Git LFS.

---

## Git LFS kurz erklärt

Git LFS bedeutet Git Large File Storage.

Es ist für große Dateien gedacht.

Typische Nutzung:

- große Bilder
- Modelle
- Audiodateien
- Videos
- große Binärdateien

Für normale Markdown-, Linux-, Git- und Skriptprojekte braucht man Git LFS meistens nicht.

Für FISI-Lernprojekte ist es besser, große Dateien gar nicht erst ins Repository zu legen, wenn sie nicht nötig sind.

---

## Leere Ordner

Git speichert leere Ordner nicht direkt.

Wenn ein Ordner im Repository sichtbar sein soll, nutzt man oft eine Platzhalterdatei.

Beispiel:

```text
logs/.gitkeep
```

Dann:

```bash
git add logs/.gitkeep
git commit -m "Keep logs directory"
```

`.gitkeep` ist kein offizieller Git-Befehl, sondern eine übliche Konvention.

---

## `.gitkeep`

Eine `.gitkeep`-Datei ist eine leere Datei, die dafür sorgt, dass ein Ordner in Git sichtbar bleibt.

Beispiel:

```text
project/
└── logs/
    └── .gitkeep
```

`.gitignore` dazu:

```gitignore
logs/*
!logs/.gitkeep
```

Bedeutung:

- alles im Ordner `logs/` ignorieren
- aber `.gitkeep` behalten

Das ist praktisch für Ordner, die später lokal Dateien enthalten, aber im Repository leer bleiben sollen.

---

## Lokale Editor-Dateien

Editoren und IDEs erzeugen oft eigene Dateien.

Beispiele:

```text
.vscode/
.idea/
*.swp
```

Ob man `.vscode/` ignoriert, hängt vom Projekt ab.

Manchmal sind VS-Code-Einstellungen für ein Team sinnvoll.

In einfachen Lern- und Portfolio-Projekten ist es oft besser, lokale Editor-Dateien zu ignorieren.

Beispiel:

```gitignore
.vscode/
.idea/
*.swp
```

---

## Betriebssystem-Dateien

Betriebssysteme erzeugen manchmal eigene Dateien.

Beispiele:

```text
.DS_Store
Thumbs.db
```

Diese Dateien gehören normalerweise nicht ins Repository.

`.gitignore`:

```gitignore
.DS_Store
Thumbs.db
```

Das hält das Repository sauberer.

---

## Logs und temporäre Dateien

Logdateien und temporäre Dateien entstehen oft automatisch.

Beispiele:

```text
app.log
debug.log
temp.tmp
backup.bak
```

Meistens sollten sie ignoriert werden:

```gitignore
*.log
*.tmp
*.bak
```

Ausnahme:

Wenn eine kleine Beispiel-Logdatei bewusst Teil der Dokumentation ist, kann sie im Repository bleiben.

Dann sollte sie keine privaten Daten enthalten.

---

## Build- und Cache-Dateien

Viele Programme erzeugen Build- oder Cache-Dateien.

Beispiele:

```text
__pycache__/
*.pyc
dist/
build/
node_modules/
target/
```

Diese Dateien sind oft automatisch wiederherstellbar.

Sie gehören meistens nicht ins Repository.

Stattdessen werden Abhängigkeiten und Build-Schritte dokumentiert.

---

## Dateiverwaltung mit Git und Shell

Git arbeitet eng mit normalen Dateioperationen zusammen.

Normale Linux-Befehle:

```bash
touch file.md
mv file.md docs/file.md
rm old.md
mkdir docs
```

Git erkennt danach Änderungen.

Prüfen:

```bash
git status
```

Danach entscheidet man:

```bash
git add
git commit
```

Git ersetzt nicht das Dateisystem. Git verfolgt Änderungen im Dateisystem.

---

## `git clean`

`git clean` kann untracked Dateien löschen.

Untracked Dateien anzeigen, die gelöscht würden:

```bash
git clean -n
```

Untracked Dateien löschen:

```bash
git clean -f
```

Auch untracked Ordner löschen:

```bash
git clean -fd
```

Wichtig:

`git clean` kann Dateien endgültig löschen, die noch nie committed wurden.

Deshalb zuerst immer:

```bash
git clean -n
```

Das ist die Vorschau.

---

## `git clean` und `.gitignore`

Standardmäßig löscht `git clean` nicht unbedingt ignorierte Dateien.

Ignorierte Dateien mit einbeziehen:

```bash
git clean -fdx
```

Sehr vorsichtig:

```bash
git clean -fdx
```

Das kann zum Beispiel löschen:

- `.venv/`
- Build-Ordner
- Cache
- lokale Dateien
- ignorierte Testdateien

Vorher immer prüfen:

```bash
git clean -fdx -n
```

Erst wenn die Vorschau korrekt ist, ausführen.

---

## Dateien aus Git entfernen, aber lokal behalten

Typischer Fall:

Eine Datei wurde versehentlich getrackt, soll aber lokal bleiben.

Beispiel:

```bash
git rm --cached private-notes.md
```

Dann in `.gitignore`:

```gitignore
private-notes.md
```

Danach committen:

```bash
git add .gitignore
git commit -m "Ignore private notes"
```

So bleibt die Datei lokal, wird aber nicht weiter von Git verfolgt.

---

## `.gitignore` prüfen

Man kann prüfen, warum eine Datei ignoriert wird.

```bash
git check-ignore -v datei
```

Beispiel:

```bash
git check-ignore -v .env
```

Die Ausgabe zeigt, welche Regel aus welcher `.gitignore` greift.

Das ist hilfreich, wenn man nicht versteht, warum eine Datei nicht bei `git status` auftaucht.

---

## Globale `.gitignore`

Neben der `.gitignore` im Projekt kann es auch eine globale Ignore-Datei geben.

Diese gilt für den Benutzer auf dem System.

Beispiel:

```bash
git config --global core.excludesfile ~/.gitignore_global
```

Globale Ignore-Datei bearbeiten:

```bash
nano ~/.gitignore_global
```

Typische Inhalte:

```gitignore
.DS_Store
Thumbs.db
*.swp
```

Eine globale `.gitignore` ist sinnvoll für persönliche oder systemweite Dateien, die in keinem Projekt auftauchen sollen.

---

## Repository sauber halten

Ein sauberes Repository enthält nur relevante Dateien.

Gute Fragen vor einem Commit:

- Gehört diese Datei wirklich zum Projekt?
- Enthält sie private Informationen?
- Kann sie automatisch neu erzeugt werden?
- Ist sie zu groß?
- Ist sie nur lokal für meinen Rechner?
- Ist sie für andere nützlich?
- Ist sie dokumentiert?
- Sollte sie lieber als Beispiel-Datei gespeichert werden?
- Sollte sie in `.gitignore` stehen?

Diese Fragen verhindern viele spätere Probleme.

---

## Typische Fehler

| Fehler                                            | Problem                                   |
| ------------------------------------------------- | ----------------------------------------- |
| `.gitignore` vergessen                            | unnötige Dateien werden getrackt          |
| `.env` committen                                  | Zugangsdaten können veröffentlicht werden |
| private SSH-Schlüssel committen                   | sehr hohes Sicherheitsrisiko              |
| glauben, `.gitignore` wirkt auf getrackte Dateien | Datei wird trotzdem weiter verfolgt       |
| `git rm` statt `git rm --cached` nutzen           | Datei wird lokal gelöscht                 |
| `git clean -f` blind nutzen                       | uncommitted Dateien können verloren gehen |
| große Dateien committen                           | Repository wird langsam und groß          |
| Logs committen                                    | unnötige oder sensible Daten im Repo      |
| lokale Editor-Dateien committen                   | Team- oder Projektstruktur wird unsauber  |
| keine Beispiel-Dateien nutzen                     | Projekt ist schwer nachzubauen            |

---

## Praktische Beispiele

### Beispiel 1: `.env` ignorieren

```bash
echo ".env" >> .gitignore
git add .gitignore
git commit -m "Ignore environment file"
git push
```

Damit wird verhindert, dass eine neue `.env`-Datei getrackt wird.

### Beispiel 2: Bereits getrackte `.env` entfernen

```bash
git rm --cached .env
echo ".env" >> .gitignore
git add .gitignore
git commit -m "Stop tracking environment file"
git push
```

Die Datei bleibt lokal, wird aber nicht mehr von Git verfolgt.

### Beispiel 3: Untracked Dateien prüfen

```bash
git status
git clean -n
```

Damit sieht man, welche untracked Dateien existieren und was `git clean` löschen würde.

### Beispiel 4: Datei umbenennen

```bash
git mv old-name.md new-name.md
git commit -m "Rename documentation file"
git push
```

Damit wird eine Umbenennung sauber in Git gespeichert.

---

## Nützliche Befehle

| Befehl                      | Bedeutung                                           |
| --------------------------- | --------------------------------------------------- |
| `git status`                | Dateistatus anzeigen                                |
| `git add datei`             | Datei vormerken                                     |
| `git add .gitignore`        | `.gitignore` vormerken                              |
| `git rm datei`              | Datei aus Git und lokal löschen                     |
| `git rm --cached datei`     | Datei aus Git entfernen, lokal behalten             |
| `git mv alt neu`            | Datei umbenennen oder verschieben                   |
| `git clean -n`              | Vorschau auf untracked Dateien, die gelöscht würden |
| `git clean -f`              | untracked Dateien löschen                           |
| `git clean -fd`             | untracked Dateien und Ordner löschen                |
| `git clean -fdx -n`         | Vorschau inklusive ignorierter Dateien              |
| `git check-ignore -v datei` | prüfen, warum Datei ignoriert wird                  |
| `git diff`                  | Änderungen anzeigen                                 |
| `git diff --staged`         | staged Änderungen anzeigen                          |
| `git commit -m "Text"`      | Commit erstellen                                    |
| `git push`                  | Änderungen hochladen                                |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist `.gitignore` wichtig, weil technische Projekte oft viele Dateien enthalten, die nicht veröffentlicht oder versioniert werden sollen.

In der Praxis bedeutet das:

- Skripte sauber versionieren
- Logdateien ignorieren
- lokale Testdaten ausschließen
- `.env`-Dateien schützen
- private Schlüssel niemals committen
- Konfigurationsbeispiele ohne echte Secrets bereitstellen
- Repository übersichtlich halten
- unnötige Dateien vermeiden
- GitHub-Projekte professionell pflegen
- Sicherheitsrisiken durch falsche Dateien verhindern

Ein guter FISI prüft vor einem Commit nicht nur, ob der Befehl funktioniert, sondern auch, welche Dateien wirklich ins Repository gehören.

---

## Kurze Zusammenfassung

`.gitignore` legt fest, welche Dateien und Ordner Git ignorieren soll.

Typische ignorierte Dateien sind Logs, temporäre Dateien, Cache-Ordner, virtuelle Umgebungen, `.env`-Dateien, Editor-Dateien und private Notizen.

Wichtig ist: `.gitignore` wirkt nicht automatisch auf Dateien, die bereits getrackt werden. Dafür nutzt man `git rm --cached`.

Für FISI ist dieses Kapitel wichtig, weil saubere Dateiverwaltung in Git hilft, Repositories sicher, übersichtlich und professionell zu halten.
