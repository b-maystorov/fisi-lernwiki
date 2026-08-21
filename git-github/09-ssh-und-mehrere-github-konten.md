# 9. SSH und mehrere GitHub-Konten

In diesem Kapitel geht es um SSH und die Arbeit mit mehreren GitHub-Konten.

GitHub-Repositories können über HTTPS oder SSH genutzt werden. SSH ist besonders praktisch, weil man mit Schlüsseln arbeitet und nicht bei jedem `push` oder `pull` Zugangsdaten eingeben muss. Wenn man mehrere GitHub-Konten nutzt, zum Beispiel ein privates Konto und ein Schul- oder Arbeitskonto, muss die SSH-Konfiguration sauber getrennt sein.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil SSH nicht nur bei GitHub vorkommt. SSH wird auch für Serveradministration, Remote-Zugriff, Automatisierung und sichere Verbindungen genutzt.

---

## Kurz erklärt

SSH bedeutet Secure Shell.

Mit SSH kann man eine sichere Verbindung zu einem entfernten System herstellen.

Bei GitHub nutzt man SSH, um sich gegenüber GitHub zu authentifizieren.

Statt Benutzername und Passwort nutzt man ein Schlüsselpaar:

| Schlüssel              | Bedeutung                             |
| ---------------------- | ------------------------------------- |
| privater Schlüssel     | bleibt geheim auf dem eigenen Rechner |
| öffentlicher Schlüssel | wird bei GitHub hinterlegt            |

Der private Schlüssel darf niemals veröffentlicht werden.

Typischer SSH-Test:

```bash
ssh -T git@github.com
```

Bei mehreren GitHub-Konten nutzt man oft SSH-Aliase:

```bash
ssh -T git@github-private
ssh -T git@github-school
```

---

## Was ist SSH?

SSH ist ein Netzwerkprotokoll für sichere Verbindungen.

SSH wird häufig genutzt für:

- Serveradministration
- Login auf Linux-Server
- Remote-Terminal
- Dateiübertragung
- GitHub-Zugriff
- Automatisierung
- Skripte
- Admin-Aufgaben

Beispiel für Serverzugriff:

```bash
ssh user@server-ip
```

Beispiel für GitHub:

```bash
ssh -T git@github.com
```

Bei GitHub bekommt man keine normale Shell. Der SSH-Zugriff dient dort zur Authentifizierung für Git.

---

## SSH bei GitHub

GitHub nutzt SSH, damit Git prüfen kann:

```text
Darf dieser Rechner auf dieses Repository zugreifen?
```

Wenn SSH korrekt eingerichtet ist, kann man Befehle nutzen wie:

```bash
git clone git@github.com:user/repository.git
git pull
git push
```

Vorteile von SSH:

- kein Passwort bei jedem Push
- sicherer Zugriff über Schlüssel
- gut für Terminal-Arbeit
- praktisch bei mehreren Repositories
- gut für Automatisierung
- wichtig für professionelle Git-Arbeit

---

## SSH-Schlüsselpaar

Ein SSH-Schlüsselpaar besteht aus zwei Dateien.

Beispiel:

```text
id_ed25519
id_ed25519.pub
```

Bedeutung:

| Datei            | Bedeutung              |
| ---------------- | ---------------------- |
| `id_ed25519`     | privater Schlüssel     |
| `id_ed25519.pub` | öffentlicher Schlüssel |

Der private Schlüssel bleibt auf dem eigenen Rechner.

Der öffentliche Schlüssel wird bei GitHub eingetragen.

Merksatz:

```text
.pub darf zu GitHub.
ohne .pub bleibt geheim.
```

---

## Privater Schlüssel

Der private Schlüssel ist geheim.

Beispiel:

```text
~/.ssh/id_ed25519
```

Dieser Schlüssel darf nicht:

- in GitHub hochgeladen werden
- per Chat geteilt werden
- in ein Repository committed werden
- in Screenshots sichtbar sein
- per E-Mail verschickt werden
- auf fremden Systemen liegen

Wenn ein privater Schlüssel veröffentlicht wurde, sollte man ihn nicht weiterverwenden.

Dann sollte man:

- Schlüssel bei GitHub entfernen
- neuen Schlüssel erzeugen
- alten lokalen Schlüssel löschen oder archivieren
- Zugriffe prüfen

---

## Öffentlicher Schlüssel

Der öffentliche Schlüssel endet meistens auf `.pub`.

Beispiel:

```text
~/.ssh/id_ed25519.pub
```

Den öffentlichen Schlüssel kann man anzeigen:

```bash
cat ~/.ssh/id_ed25519.pub
```

Der Inhalt wird bei GitHub hinterlegt.

Der öffentliche Schlüssel allein reicht nicht aus, um Zugriff zu bekommen. Er passt nur zum privaten Schlüssel.

GitHub prüft später:

```text
Passt der private Schlüssel auf dem Rechner zum öffentlichen Schlüssel bei GitHub?
```

---

## SSH-Schlüssel erzeugen

Einen neuen SSH-Schlüssel erzeugt man mit:

```bash
ssh-keygen -t ed25519 -C "example@example.com"
```

Beispiel mit Dateiname:

```bash
ssh-keygen -t ed25519 -C "private-github" -f ~/.ssh/id_ed25519_private
```

Bedeutung:

| Teil         | Bedeutung                     |
| ------------ | ----------------------------- |
| `ssh-keygen` | erstellt SSH-Schlüssel        |
| `-t ed25519` | moderner Schlüsseltyp         |
| `-C`         | Kommentar zur Wiedererkennung |
| `-f`         | Dateiname für den Schlüssel   |

Danach entstehen zwei Dateien:

```text
id_ed25519_private
id_ed25519_private.pub
```

---

## Mehrere SSH-Schlüssel

Bei mehreren GitHub-Konten ist es sinnvoll, getrennte SSH-Schlüssel zu nutzen.

Beispiel:

```text
~/.ssh/id_ed25519_private
~/.ssh/id_ed25519_private.pub

~/.ssh/id_ed25519_school
~/.ssh/id_ed25519_school.pub
```

Vorteil:

- private und schulische Projekte sind getrennt
- falsche Konten werden leichter vermieden
- Zugriffe bleiben übersichtlich
- Schlüssel können unabhängig entfernt werden
- GitHub erkennt das passende Konto über den Schlüssel

---

## SSH-Ordner prüfen

SSH-Dateien liegen meistens im Ordner:

```text
~/.ssh
```

Anzeigen:

```bash
ls -la ~/.ssh
```

Typische Dateien:

```text
id_ed25519
id_ed25519.pub
config
known_hosts
```

Bei mehreren Konten können weitere Schlüssel existieren:

```text
id_ed25519_private
id_ed25519_private.pub
id_ed25519_school
id_ed25519_school.pub
```

---

## Rechte für SSH-Dateien

SSH ist streng bei Dateirechten.

Der private Schlüssel sollte nicht für andere Benutzer lesbar sein.

Typische Rechte:

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519_private
chmod 600 ~/.ssh/id_ed25519_school
chmod 644 ~/.ssh/id_ed25519_private.pub
chmod 644 ~/.ssh/id_ed25519_school.pub
```

Bedeutung:

| Recht | Bedeutung                                           |
| ----- | --------------------------------------------------- |
| `700` | nur Besitzer darf Ordner lesen, schreiben, betreten |
| `600` | nur Besitzer darf Datei lesen und schreiben         |
| `644` | Besitzer darf schreiben, andere dürfen lesen        |

Wenn Rechte falsch sind, kann SSH den Schlüssel ablehnen.

---

## SSH-Agent

Der SSH-Agent kann private Schlüssel im Hintergrund verwalten.

Agent starten:

```bash
eval "$(ssh-agent -s)"
```

Schlüssel hinzufügen:

```bash
ssh-add ~/.ssh/id_ed25519_private
ssh-add ~/.ssh/id_ed25519_school
```

Geladene Schlüssel anzeigen:

```bash
ssh-add -l
```

Alle Schlüssel aus dem Agent entfernen:

```bash
ssh-add -D
```

Der SSH-Agent ist praktisch, wenn ein Schlüssel eine Passphrase hat oder wenn mehrere Schlüssel genutzt werden.

---

## Öffentlichen Schlüssel zu GitHub hinzufügen

Ablauf:

1. Öffentlichen Schlüssel anzeigen:

```bash
cat ~/.ssh/id_ed25519_private.pub
```

2. Inhalt kopieren.

3. In GitHub öffnen:

```text
Settings -> SSH and GPG keys -> New SSH key
```

4. Titel vergeben.

5. Öffentlichen Schlüssel einfügen.

6. Speichern.

Wichtig:

Nur die `.pub`-Datei einfügen.

Niemals den privaten Schlüssel einfügen.

---

## SSH-Verbindung testen

Standardtest:

```bash
ssh -T git@github.com
```

Wenn es funktioniert, zeigt GitHub eine Meldung wie:

```text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

Das bedeutet:

- SSH funktioniert
- GitHub erkennt den Schlüssel
- normale Shell gibt es bei GitHub nicht

Das ist korrekt.

GitHub gibt über SSH keinen normalen Serverzugang.

---

## Mehrere GitHub-Konten mit SSH-Alias

Wenn man mehrere GitHub-Konten nutzt, reicht `git@github.com` oft nicht aus.

Dann kann SSH nicht immer eindeutig wissen, welcher Schlüssel genutzt werden soll.

Deshalb nutzt man Aliase in:

```text
~/.ssh/config
```

Beispiel:

```sshconfig
Host github-private
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_private
    IdentitiesOnly yes

Host github-school
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_school
    IdentitiesOnly yes
```

Danach nutzt man nicht mehr direkt `github.com`, sondern den Alias.

---

## SSH-Alias testen

Private Verbindung testen:

```bash
ssh -T git@github-private
```

Schul- oder Arbeitsverbindung testen:

```bash
ssh -T git@github-school
```

Wenn alles passt, meldet GitHub jeweils den passenden Account.

Das ist wichtig, um zu prüfen, ob der richtige Schlüssel und das richtige Konto verwendet werden.

---

## Remote-URL mit SSH-Alias

Bei mehreren Konten muss auch die Git-Remote-Adresse den Alias nutzen.

Beispiel private Repositories:

```text
git@github-private:user/repository.git
```

Beispiel Schul-Repositories:

```text
git@github-school:user/repository.git
```

Remote prüfen:

```bash
git remote -v
```

Remote ändern:

```bash
git remote set-url origin git@github-private:user/repository.git
```

Oder für Schul-Repository:

```bash
git remote set-url origin git@github-school:user/repository.git
```

Wichtig:

Der Host-Teil muss zum Alias aus `~/.ssh/config` passen.

---

## Beispiel: privates Repository klonen

Mit SSH-Alias:

```bash
git clone git@github-private:user/private-repository.git
```

Danach prüfen:

```bash
cd private-repository
git remote -v
git config user.name
git config user.email
```

Die Remote-Adresse sollte `github-private` enthalten.

Das verhindert, dass versehentlich der falsche SSH-Schlüssel genutzt wird.

---

## Beispiel: Schul-Repository klonen

Mit SSH-Alias:

```bash
git clone git@github-school:user/school-repository.git
```

Danach prüfen:

```bash
cd school-repository
git remote -v
git config user.name
git config user.email
```

Die Remote-Adresse sollte `github-school` enthalten.

So bleiben Schul- und Privatkonto sauber getrennt.

---

## Git-Identität und SSH sind getrennt

Wichtig:

SSH entscheidet, welches GitHub-Konto Zugriff bekommt.

Git-Konfiguration entscheidet, welcher Name und welche E-Mail in Commits stehen.

Das sind zwei verschiedene Dinge.

Prüfen:

```bash
git remote -v
git config user.name
git config user.email
ssh -T git@github-private
```

Mögliche Fehler:

| Problem                      | Ursache                                    |
| ---------------------------- | ------------------------------------------ |
| Push geht zum falschen Konto | falsche Remote-URL oder falscher SSH-Alias |
| Commit hat falschen Namen    | falsche Git-Konfiguration                  |
| Permission denied            | falscher oder fehlender SSH-Schlüssel      |
| Repository not found         | falsches Konto oder keine Rechte           |

---

## Git-Konfiguration pro Repository

Man kann Git-Identität lokal im Repository setzen.

```bash
git config user.name "Example Name"
git config user.email "example@example.com"
```

Diese Einstellung gilt nur für das aktuelle Repository.

Prüfen:

```bash
git config user.name
git config user.email
```

Das ist sinnvoll, wenn man ein einzelnes Repository bewusst mit einer bestimmten Identität verwenden möchte.

---

## Globale Git-Konfiguration

Globale Konfiguration gilt für den aktuellen Benutzer auf dem System.

```bash
git config --global user.name "Example Name"
git config --global user.email "example@example.com"
```

Anzeigen:

```bash
git config --global --list
```

Globale Werte können von lokalen Werten überschrieben werden.

Reihenfolge:

```text
local überschreibt global
global überschreibt system
```

---

## Ordnerbasierte Git-Konfiguration

Bei mehreren Arbeitsbereichen kann man Git-Konfiguration nach Ordner trennen.

Beispiel:

```text
~/github/private/
~/github/school/
```

Dafür kann man `includeIf` in der globalen Git-Konfiguration nutzen.

Beispiel:

```gitconfig
[includeIf "gitdir:~/github/private/"]
    path = ~/.gitconfig-private

[includeIf "gitdir:~/github/school/"]
    path = ~/.gitconfig-school
```

Dann kann jede Datei eigene Werte enthalten.

Beispiel `~/.gitconfig-private`:

```gitconfig
[user]
    name = Private User
    email = private@example.com
```

Beispiel `~/.gitconfig-school`:

```gitconfig
[user]
    name = School User
    email = school@example.com
```

Das ist sehr praktisch, wenn private und schulische Repositories sauber getrennt werden sollen.

---

## Konfiguration prüfen

In jedem Repository sollte man prüfen können:

```bash
git config user.name
git config user.email
git remote -v
```

Bei SSH zusätzlich:

```bash
ssh -T git@github-private
ssh -T git@github-school
```

Bei Unsicherheit:

```bash
git config --show-origin user.name
git config --show-origin user.email
```

Das zeigt, aus welcher Konfigurationsdatei der Wert kommt.

Beispiel:

```text
file:/home/user/.gitconfig-private    Private User
```

Das hilft bei der Fehlersuche.

---

## `~/.ssh/config`

Die Datei `~/.ssh/config` steuert SSH-Verbindungen.

Beispiel:

```sshconfig
Host github-private
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_private
    IdentitiesOnly yes

Host github-school
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_school
    IdentitiesOnly yes
```

Bedeutung:

| Zeile                 | Bedeutung                              |
| --------------------- | -------------------------------------- |
| `Host github-private` | Aliasname                              |
| `HostName github.com` | echter Zielserver                      |
| `User git`            | GitHub nutzt den SSH-Benutzer `git`    |
| `IdentityFile`        | welcher private Schlüssel genutzt wird |
| `IdentitiesOnly yes`  | nur diesen Schlüssel verwenden         |

Der Alias steht später in der Git-Remote-URL.

---

## Warum `User git`?

Bei GitHub verbindet man sich per SSH immer mit dem Benutzer:

```text
git
```

Deshalb sieht eine SSH-URL so aus:

```text
git@github.com:user/repository.git
```

oder mit Alias:

```text
git@github-private:user/repository.git
```

Das bedeutet nicht, dass der eigene GitHub-Benutzer `git` heißt.

`git` ist der technische SSH-Benutzer auf GitHub-Seite.

GitHub erkennt das echte Konto über den SSH-Schlüssel.

---

## `known_hosts`

Die Datei `known_hosts` speichert bekannte SSH-Server.

Pfad:

```text
~/.ssh/known_hosts
```

Beim ersten Verbinden fragt SSH oft, ob der Host akzeptiert werden soll.

Beispiel:

```text
Are you sure you want to continue connecting?
```

Wenn man bestätigt, wird der Server in `known_hosts` gespeichert.

Das schützt davor, dass man unbemerkt mit einem anderen Server verbunden wird.

Bei GitHub sollte man trotzdem bewusst prüfen, dass man wirklich mit GitHub verbunden ist.

---

## Permission denied publickey

Eine häufige Fehlermeldung:

```text
Permission denied (publickey).
```

Mögliche Ursachen:

- SSH-Schlüssel wurde nicht erstellt
- öffentlicher Schlüssel ist nicht bei GitHub hinterlegt
- falscher privater Schlüssel wird genutzt
- falscher SSH-Alias in der Remote-URL
- SSH-Agent kennt den Schlüssel nicht
- Repository gehört zu anderem GitHub-Konto
- keine Berechtigung auf das Repository
- Dateirechte im `.ssh`-Ordner sind falsch

Prüfen:

```bash
ssh -T git@github-private
git remote -v
ls -la ~/.ssh
ssh-add -l
```

---

## Repository not found

Meldung:

```text
Repository not found.
```

Das bedeutet nicht immer, dass das Repository wirklich fehlt.

Mögliche Ursachen:

- Repository-Name falsch geschrieben
- falscher GitHub-Benutzer in der URL
- Repository ist privat
- falsches GitHub-Konto wird über SSH genutzt
- kein Zugriff auf das Repository
- falscher SSH-Alias
- Remote-URL zeigt auf falsches Repository

Prüfen:

```bash
git remote -v
ssh -T git@github-private
ssh -T git@github-school
```

Wenn der SSH-Test den falschen Account zeigt, ist der Alias oder Schlüssel falsch.

---

## Remote falsch gesetzt

Remote anzeigen:

```bash
git remote -v
```

Beispiel falsche Adresse:

```text
origin git@github.com:user/repository.git
```

Bei mehreren Konten ist besser:

```text
origin git@github-private:user/repository.git
```

Remote ändern:

```bash
git remote set-url origin git@github-private:user/repository.git
```

Danach prüfen:

```bash
git remote -v
```

---

## SSH und HTTPS nicht mischen

Ein Repository kann per HTTPS oder SSH verbunden sein.

HTTPS:

```text
https://github.com/user/repository.git
```

SSH:

```text
git@github.com:user/repository.git
```

Mit Alias:

```text
git@github-private:user/repository.git
```

Wenn man SSH-Aliase nutzt, sollte das Remote auch SSH verwenden.

Prüfen:

```bash
git remote -v
```

Wenn dort `https://` steht, nutzt das Repository nicht den SSH-Alias.

---

## Private Daten vermeiden

In öffentlichen GitHub-Repositories dürfen keine sensiblen Daten landen.

Nicht veröffentlichen:

- private SSH-Schlüssel
- Passwörter
- Tokens
- `.env` mit echten Daten
- private Kundendaten
- interne Schul- oder Firmendaten
- private Screenshots
- geheime Servernamen
- sensible IP-Adressen
- persönliche Dokumente

Besonders wichtig:

```text
Der private SSH-Schlüssel gehört niemals in Git.
```

`.gitignore` kann helfen:

```gitignore
.env
private/
*.key
id_rsa
id_ed25519
```

Aber der beste Schutz ist: vor jedem Commit `git status` prüfen.

---

## SSH bei Servern und GitHub unterscheiden

SSH zu einem Server:

```bash
ssh user@server-ip
```

SSH zu GitHub:

```bash
ssh -T git@github.com
```

Unterschied:

| Nutzung                 | Bedeutung                         |
| ----------------------- | --------------------------------- |
| Server-SSH              | Remote-Terminal auf einem Server  |
| GitHub-SSH              | Authentifizierung für Git         |
| `ssh user@server`       | Login auf Server                  |
| `ssh -T git@github.com` | Test der GitHub-Authentifizierung |

Bei GitHub bekommt man keine normale Shell.

Die Meldung, dass GitHub keinen Shell-Zugriff bietet, ist normal.

---

## Typischer Ablauf für neues GitHub-Konto

Ein sauberer Ablauf:

1. SSH-Schlüssel erstellen:

```bash
ssh-keygen -t ed25519 -C "account-name" -f ~/.ssh/id_ed25519_account
```

2. Öffentlichen Schlüssel anzeigen:

```bash
cat ~/.ssh/id_ed25519_account.pub
```

3. Öffentlichen Schlüssel in GitHub eintragen.

4. SSH-Config ergänzen:

```sshconfig
Host github-account
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_account
    IdentitiesOnly yes
```

5. Verbindung testen:

```bash
ssh -T git@github-account
```

6. Repository mit Alias klonen:

```bash
git clone git@github-account:user/repository.git
```

7. Im Repository prüfen:

```bash
git remote -v
git config user.name
git config user.email
```

---

## Typischer Ablauf vor `git push`

Vor jedem Push bei mehreren Konten:

```bash
git status
git remote -v
git config user.name
git config user.email
```

Wenn nötig SSH testen:

```bash
ssh -T git@github-private
```

Dann:

```bash
git push
```

Diese Prüfung verhindert viele Fehler.

Besonders wichtig ist das bei:

- neu geklonten Repositories
- neuen Projekten
- Schulprojekten
- privaten Portfolio-Projekten
- Repositories mit ähnlichen Namen
- mehreren GitHub-Konten auf einem Rechner

---

## Häufige Fehler

| Fehler                                           | Problem                                          |
| ------------------------------------------------ | ------------------------------------------------ |
| privaten Schlüssel veröffentlichen               | sehr großes Sicherheitsrisiko                    |
| `.pub` und private Datei verwechseln             | falscher Schlüssel wird geteilt                  |
| Remote nutzt `github.com` statt Alias            | falscher Account kann genutzt werden             |
| Git-Identität nicht prüfen                       | Commits haben falschen Namen oder falsche E-Mail |
| SSH-Test nicht machen                            | Fehler fällt erst bei Push auf                   |
| HTTPS und SSH verwechseln                        | Alias greift nicht                               |
| Schlüssel nicht bei GitHub hinterlegt            | Permission denied                                |
| falscher Schlüssel im Agent                      | GitHub erkennt falsches Konto                    |
| `.ssh/config` falsch eingerückt oder geschrieben | Alias funktioniert nicht                         |
| Repository im falschen Ordner                    | falsche Git-Konfiguration kann greifen           |

---

## Praktische Beispiele

### Beispiel 1: SSH-Verbindung testen

```bash
ssh -T git@github.com
```

Mit Alias:

```bash
ssh -T git@github-private
```

Damit prüft man, ob GitHub den richtigen SSH-Schlüssel erkennt.

---

### Beispiel 2: Remote prüfen

```bash
git remote -v
```

Beispiel mit Alias:

```text
origin  git@github-private:user/repository.git (fetch)
origin  git@github-private:user/repository.git (push)
```

So sieht man, über welchen SSH-Host gepusht wird.

---

### Beispiel 3: Remote auf SSH-Alias ändern

```bash
git remote set-url origin git@github-private:user/repository.git
git remote -v
```

Damit nutzt das Repository den Alias aus `~/.ssh/config`.

---

### Beispiel 4: Git-Identität prüfen

```bash
git config user.name
git config user.email
git config --show-origin user.email
```

Damit sieht man, welche Identität Git für Commits nutzt und woher sie kommt.

---

## Nützliche Befehle

| Befehl                                | Bedeutung                                    |
| ------------------------------------- | -------------------------------------------- |
| `ssh-keygen -t ed25519`               | neuen SSH-Schlüssel erzeugen                 |
| `cat ~/.ssh/key.pub`                  | öffentlichen Schlüssel anzeigen              |
| `ls -la ~/.ssh`                       | SSH-Dateien anzeigen                         |
| `chmod 700 ~/.ssh`                    | sichere Rechte für SSH-Ordner setzen         |
| `chmod 600 ~/.ssh/key`                | sichere Rechte für privaten Schlüssel setzen |
| `eval "$(ssh-agent -s)"`              | SSH-Agent starten                            |
| `ssh-add ~/.ssh/key`                  | Schlüssel zum Agent hinzufügen               |
| `ssh-add -l`                          | geladene Schlüssel anzeigen                  |
| `ssh -T git@github.com`               | GitHub-SSH testen                            |
| `ssh -T git@github-private`           | GitHub-SSH über Alias testen                 |
| `git remote -v`                       | Remote-Adresse prüfen                        |
| `git remote set-url origin url`       | Remote-Adresse ändern                        |
| `git config user.name`                | Git-Benutzername prüfen                      |
| `git config user.email`               | Git-E-Mail prüfen                            |
| `git config --show-origin user.email` | Quelle der Konfiguration anzeigen            |
| `git clone git@alias:user/repo.git`   | Repository über SSH-Alias klonen             |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist SSH eine wichtige Grundlage.

In der Praxis bedeutet das:

- sichere Verbindung zu Servern herstellen
- GitHub-Repositories per SSH nutzen
- private und öffentliche Schlüssel unterscheiden
- private Schlüssel schützen
- Berechtigungen und Zugriffe verstehen
- mehrere Konten sauber trennen
- Remote-Adressen prüfen
- Fehler wie `Permission denied` analysieren
- Git-Identität korrekt konfigurieren
- sichere Arbeitsweise mit öffentlichen Repositories einhalten

Ein guter FISI versteht nicht nur den Befehl `git push`, sondern auch, welche Authentifizierung dahinter passiert und warum ein falscher Schlüssel oder ein falsches Remote zu Problemen führen kann.

---

## Kurze Zusammenfassung

SSH ermöglicht sichere Verbindungen und wird bei GitHub zur Authentifizierung genutzt.

Ein SSH-Schlüsselpaar besteht aus einem privaten und einem öffentlichen Schlüssel. Der private Schlüssel bleibt geheim. Der öffentliche Schlüssel wird bei GitHub hinterlegt.

Bei mehreren GitHub-Konten nutzt man am besten getrennte SSH-Schlüssel und SSH-Aliase in `~/.ssh/config`.

Wichtige Befehle sind `ssh-keygen`, `ssh-add`, `ssh -T`, `git remote -v`, `git remote set-url`, `git config user.name`, `git config user.email` und `git config --show-origin`.

Für FISI ist dieses Kapitel wichtig, weil SSH, Zugriffskontrolle, GitHub und sichere Repository-Arbeit in vielen IT-Projekten zusammengehören.
