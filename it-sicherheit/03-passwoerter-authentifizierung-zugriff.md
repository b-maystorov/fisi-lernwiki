# 3. Passwörter, Authentifizierung und Zugriff

In diesem Kapitel geht es um Passwörter, Authentifizierung und Zugriffskontrolle.

Benutzerkonten und Zugriffsrechte gehören zu den wichtigsten Bereichen der IT-Sicherheit. Viele Sicherheitsvorfälle entstehen nicht dadurch, dass ein System technisch komplett kaputt ist, sondern weil ein Konto übernommen wurde, ein Passwort schwach war oder Benutzer mehr Rechte hatten als nötig.

Für Fachinformatiker für Systemintegration ist dieses Thema besonders wichtig, weil man in der Praxis Benutzer anlegt, Rechte vergibt, Gruppen pflegt, Adminzugriffe absichert und Zugriffe dokumentiert.

---

## Kurz erklärt

Wichtige Begriffe:

| Begriff | Bedeutung |
|---|---|
| Benutzerkonto | Identität eines Benutzers im System |
| Passwort | geheimer Nachweis für die Anmeldung |
| Authentifizierung | Prüfung der Identität |
| Autorisierung | Prüfung der Berechtigung |
| MFA | Anmeldung mit mehreren Faktoren |
| Rolle | Bündel von Berechtigungen |
| Gruppe | Sammlung von Benutzern |
| Least Privilege | nur notwendige Rechte vergeben |
| Need-to-know | Zugriff nur auf benötigte Informationen |

Einfach gesagt:

```text
Authentifizierung = Wer bist du?
Autorisierung = Was darfst du?
Logging = Was hast du getan?
```

---

## Warum Passwörter wichtig sind

Passwörter schützen den Zugang zu Benutzerkonten, Systemen und Daten.

Beispiele:

```text
Linux-Benutzerkonto
Windows-Domänenkonto
E-Mail-Konto
GitHub-Konto
VPN-Zugang
Datenbankzugang
Cloud-Konto
Admin-Konto
```

Wenn ein Passwort gestohlen oder erraten wird, kann ein Angreifer möglicherweise im Namen des Benutzers handeln.

Das ist gefährlich, weil viele Systeme dem Benutzerkonto vertrauen.

---

## Typische Passwortprobleme

Viele Sicherheitsprobleme entstehen durch schlechte Passwortnutzung.

Beispiele:

```text
zu kurze Passwörter
leicht zu erratende Passwörter
gleiche Passwörter für mehrere Dienste
Passwörter in Klartextdateien
Passwörter in Git-Repositories
Passwörter auf Zetteln am Monitor
Passwörter per Chat oder E-Mail geteilt
Standardpasswörter nicht geändert
```

Besonders gefährlich ist die Wiederverwendung von Passwörtern.

Wenn ein Dienst gehackt wird und das Passwort auch woanders genutzt wird, sind mehrere Konten gefährdet.

---

## Gute Passwörter

Ein gutes Passwort sollte vor allem lang sein.

Wichtige Eigenschaften:

```text
lang
nicht leicht zu erraten
nicht mehrfach verwendet
nicht öffentlich bekannt
nicht mit persönlichen Daten verbunden
nicht im Klartext gespeichert
```

Ein langes Passwort ist oft besser als ein kurzes, kompliziertes Passwort.

Beispiel schlecht:

```text
Sommer2026
Password123
Firma123!
```

Besser ist eine lange Passphrase.

Beispiel:

```text
kaffee-baum-fenster-wolke-regen
```

In echten Systemen sollte man trotzdem Passwortmanager und Richtlinien nutzen.

---

## Passwortmanager

Ein Passwortmanager hilft, viele sichere Passwörter zu verwalten.

Vorteile:

```text
für jeden Dienst eigenes Passwort
lange Passwörter möglich
weniger Wiederverwendung
Passwörter müssen nicht auswendig gelernt werden
sichere Speicherung in verschlüsselter Datenbank
```

Wichtig:

```text
Master-Passwort muss stark sein.
MFA für Passwortmanager ist sinnvoll.
Backups oder Wiederherstellung müssen geregelt sein.
```

Ein Passwortmanager ist besser als eine ungeschützte Textdatei oder wiederverwendete Passwörter.

---

## Passwörter nicht in Git speichern

Ein häufiger Fehler ist das Speichern von Zugangsdaten in Git.

Gefährliche Beispiele:

```text
.env mit echten Passwörtern
Datenbankpasswort in docker-compose.yml
API-Key in README.md
SSH-Key im Repository
Passwort in Python-Datei
```

Besser:

```text
.env nicht committen
.env.example ohne echte Secrets nutzen
Secrets lokal oder in sicherer Umgebung speichern
.gitignore richtig pflegen
```

Beispiel `.gitignore`:

```gitignore
.env
*.key
*.pem
secrets/
```

Eine Datei aus Git zu löschen reicht nicht immer, wenn sie bereits in der Git-Historie gespeichert wurde.

---

## Standardpasswörter

Viele Geräte oder Dienste haben Standardzugänge.

Beispiele:

```text
admin / admin
admin / password
root / root
admin / 1234
```

Standardpasswörter müssen sofort geändert werden.

Typische Geräte:

```text
Router
Switches
Access Points
NAS-Systeme
Drucker
Weboberflächen
Testsysteme
Datenbanken
```

Ein Gerät mit Standardpasswort ist ein sehr leichtes Ziel.

---

## Passwort-Hashing

Passwörter sollten nicht im Klartext gespeichert werden.

Stattdessen werden Passwörter gehasht.

Ein Hash ist ein berechneter Wert aus dem Passwort.

Vereinfacht:

```text
Passwort -> Hashfunktion -> Hashwert
```

Beim Login wird das eingegebene Passwort erneut gehasht und mit dem gespeicherten Hash verglichen.

Wichtig:

```text
Systeme sollten Passwörter nie im Klartext speichern.
```

Für normale Administration muss man die mathematischen Details nicht perfekt kennen, aber das Prinzip ist wichtig.

---

## Salt kurz erklärt

Ein Salt ist ein zusätzlicher zufälliger Wert beim Passwort-Hashing.

Ziel:

```text
gleiche Passwörter erzeugen nicht automatisch gleiche Hashes
Angriffe mit vorberechneten Tabellen werden erschwert
```

Vereinfacht:

```text
Passwort + Salt -> Hash
```

Moderne Systeme nutzen dafür sichere Verfahren.

Für FISI ist wichtig:

```text
Passwörter gehören nicht in Klartextspeicher.
Sichere Systeme speichern Hashes, nicht echte Passwörter.
```

---

## Authentifizierung

Authentifizierung bedeutet:

```text
Das System prüft, wer du bist.
```

Beispiele:

```text
Login mit Benutzername und Passwort
SSH-Schlüssel
Smartcard
Fingerabdruck
MFA-App
Hardware-Key
```

Ohne Authentifizierung könnte jeder behaupten, ein bestimmter Benutzer zu sein.

Authentifizierung ist der erste Schritt beim Zugriff auf ein System.

---

## Authentifizierungsfaktoren

Es gibt verschiedene Arten von Faktoren.

| Faktor | Bedeutung | Beispiel |
|---|---|---|
| Wissen | etwas, das man weiß | Passwort, PIN |
| Besitz | etwas, das man besitzt | Smartphone, Hardware-Key |
| Sein | etwas, das man ist | Fingerabdruck, Gesicht |

Ein einzelnes Passwort ist nur ein Faktor.

MFA kombiniert mehrere Faktoren.

---

## Multi-Factor Authentication

MFA bedeutet:

```text
Multi-Factor Authentication
```

Dabei werden mindestens zwei verschiedene Faktoren kombiniert.

Beispiele:

```text
Passwort + App-Code
Passwort + Hardware-Key
Passwort + Push-Bestätigung
Passwort + Smartcard
```

MFA schützt besser, weil ein gestohlenes Passwort allein nicht reicht.

Besonders wichtig ist MFA für:

```text
Admin-Konten
E-Mail-Konten
VPN-Zugänge
Cloud-Konten
GitHub
Passwortmanager
Remote-Zugänge
```

---

## 2FA und MFA

2FA bedeutet:

```text
Two-Factor Authentication
```

MFA bedeutet:

```text
Multi-Factor Authentication
```

2FA ist ein Spezialfall von MFA mit genau zwei Faktoren.

In der Praxis werden beide Begriffe oft ähnlich benutzt.

Wichtig ist das Prinzip:

```text
Nicht nur ein Passwort.
```

---

## Gute und schwächere MFA-Methoden

Nicht jede MFA-Methode ist gleich stark.

| Methode | Bewertung |
|---|---|
| Hardware-Key | sehr stark |
| Authenticator-App | gut |
| Push-Bestätigung | gut, aber abhängig von Benutzerverhalten |
| SMS-Code | besser als nur Passwort, aber schwächer |
| E-Mail-Code | abhängig von Sicherheit des E-Mail-Kontos |

SMS ist besser als gar keine MFA, aber nicht die stärkste Methode.

Für wichtige Admin-Konten sind Hardware-Keys oder Authenticator-Apps oft besser.

---

## MFA-Fatigue

MFA-Fatigue bedeutet, dass Benutzer mit vielen MFA-Anfragen überlastet werden.

Ein Angreifer versucht dabei, viele Push-Anfragen auszulösen.

Der Benutzer klickt irgendwann vielleicht aus Versehen auf „Genehmigen“.

Schutz:

```text
MFA-Anfragen bewusst prüfen
Number Matching nutzen
ungewöhnliche Anfragen melden
MFA nicht blind bestätigen
Login-Benachrichtigungen beachten
```

Wichtig:

```text
Eine MFA-Anfrage nur bestätigen, wenn man sich wirklich gerade anmeldet.
```

---

## Autorisierung

Autorisierung bedeutet:

```text
Das System prüft, was du darfst.
```

Beispiel:

```text
Benutzer ist angemeldet.
Jetzt prüft das System, ob er einen Ordner öffnen darf.
```

Authentifizierung kommt zuerst.

Autorisierung kommt danach.

Beispiel:

```text
Benutzer Bilgin meldet sich an.
System erkennt: Bilgin ist authentifiziert.
System prüft: Darf Bilgin auf den Admin-Ordner zugreifen?
```

---

## Zugriffskontrolle

Zugriffskontrolle legt fest, wer auf welche Ressourcen zugreifen darf.

Ressourcen können sein:

```text
Dateien
Ordner
Server
Datenbanken
Anwendungen
Netzlaufwerke
Drucker
Cloud-Dienste
Git-Repositories
Admin-Oberflächen
```

Eine gute Zugriffskontrolle beantwortet:

```text
Wer darf lesen?
Wer darf schreiben?
Wer darf ändern?
Wer darf löschen?
Wer darf administrieren?
```

---

## Rechtearten

Typische Rechte sind:

| Recht | Bedeutung |
|---|---|
| Lesen | Daten anzeigen |
| Schreiben | Daten erstellen oder ändern |
| Ausführen | Programm oder Skript starten |
| Löschen | Daten entfernen |
| Administrieren | Einstellungen und Rechte ändern |

Bei Linux sieht man Rechte zum Beispiel mit:

```bash
ls -l
```

Beispiel:

```text
-rw-r--r--
```

Das zeigt, wer lesen, schreiben oder ausführen darf.

---

## Benutzer und Gruppen

Benutzer werden oft über Gruppen verwaltet.

Beispiel:

```text
Gruppe: buchhaltung
Gruppe: it-admins
Gruppe: vertrieb
Gruppe: praktikanten
```

Statt jedem Benutzer einzeln Rechte zu geben, gibt man Rechte an eine Gruppe.

Dann fügt man Benutzer zur passenden Gruppe hinzu.

Vorteil:

```text
einfachere Verwaltung
weniger Fehler
bessere Übersicht
klare Rollen
```

---

## Rollenbasierte Zugriffskontrolle

Rollenbasierte Zugriffskontrolle bedeutet:

```text
Rechte werden nach Rollen vergeben.
```

Beispiele:

| Rolle | Rechte |
|---|---|
| normaler Benutzer | eigene Dateien, Standardanwendungen |
| Support | Benutzerhilfe, bestimmte Admin-Tools |
| Administrator | Systemverwaltung |
| Entwickler | Zugriff auf Entwicklungsrepos |
| Buchhaltung | Zugriff auf Rechnungsdaten |

Das Ziel ist, dass Benutzer nicht direkt zufällig Rechte bekommen, sondern passend zu ihrer Aufgabe.

---

## RBAC

RBAC bedeutet:

```text
Role-Based Access Control
```

Dabei werden Rechte über Rollen gesteuert.

Beispiel:

```text
Benutzer -> Rolle -> Rechte
```

Vorteile:

```text
klare Struktur
einfachere Rechteprüfung
bessere Dokumentation
leichteres Onboarding
leichteres Offboarding
```

RBAC ist besonders in größeren Umgebungen wichtig.

---

## Least Privilege

Least Privilege bedeutet:

```text
Jeder Benutzer und jeder Dienst bekommt nur die Rechte, die wirklich notwendig sind.
```

Beispiele:

```text
normaler Benutzer bekommt keine Adminrechte
Webdienst bekommt nur Zugriff auf benötigte Ordner
Datenbankbenutzer bekommt nur Rechte für seine Datenbank
Praktikant bekommt keinen Zugriff auf alle Kundendaten
```

Vorteil:

```text
Wenn ein Konto kompromittiert wird, ist der Schaden begrenzt.
```

---

## Need-to-know

Need-to-know bedeutet:

```text
Benutzer bekommen nur Informationen, die sie für ihre Aufgabe brauchen.
```

Beispiel:

```text
HR braucht Personalakten.
IT braucht technische Systemdaten.
Buchhaltung braucht Rechnungen.
Gäste brauchen keinen Zugriff auf interne Dateien.
```

Need-to-know schützt besonders vertrauliche Daten.

Es ist eng mit Vertraulichkeit verbunden.

---

## Admin-Konten

Admin-Konten sind besonders kritisch.

Mit Adminrechten kann man oft:

```text
Software installieren
Benutzer ändern
Daten lesen oder löschen
Sicherheitsregeln ändern
Dienste starten oder stoppen
Systeme konfigurieren
Logs beeinflussen
```

Deshalb müssen Admin-Konten besonders geschützt werden.

Wichtige Regeln:

```text
MFA nutzen
starke Passwörter
keine gemeinsamen Admin-Konten
Adminrechte nur bei Bedarf
Admin-Konto getrennt vom normalen Benutzerkonto
Logins protokollieren
```

---

## Normales Konto und Admin-Konto trennen

In vielen Umgebungen ist es sinnvoll, normale Arbeit und Adminarbeit zu trennen.

Beispiel:

```text
bilgin.normal
bilgin.admin
```

Das normale Konto wird für E-Mail, Browser und Alltag genutzt.

Das Admin-Konto wird nur für administrative Aufgaben genutzt.

Vorteil:

```text
Wenn das normale Konto kompromittiert wird, hat der Angreifer nicht automatisch Adminrechte.
```

---

## Gemeinsame Konten vermeiden

Gemeinsame Konten sind problematisch.

Beispiel:

```text
admin
support
praktikum
teamuser
```

Problem:

```text
Man weiß später nicht genau, welche Person etwas getan hat.
Passwort wird häufiger geteilt.
Passwortwechsel ist schwieriger.
Verantwortung ist unklar.
```

Besser:

```text
jede Person hat eigenes Konto
Rechte über Gruppen oder Rollen
Adminaktionen werden protokolliert
```

---

## Dienstkonten

Dienstkonten werden von Diensten oder Anwendungen genutzt.

Beispiele:

```text
Datenbankdienst
Backup-Dienst
Webanwendung
Monitoring-Agent
CI/CD-System
```

Dienstkonten sollten ebenfalls nach Least Privilege arbeiten.

Wichtig:

```text
nur notwendige Rechte
kein interaktiver Login, wenn nicht nötig
Passwörter/Secrets sicher speichern
regelmäßige Prüfung
klare Dokumentation
```

Ein Dienstkonto mit zu vielen Rechten ist ein großes Risiko.

---

## SSH-Zugriff

SSH wird oft für Serveradministration genutzt.

Beispiel:

```bash
ssh user@server
```

SSH sollte sicher konfiguriert werden.

Wichtige Punkte:

```text
starke Passwörter oder SSH-Schlüssel
Firewall-Regeln prüfen
nur notwendige Benutzer erlauben
Root-Login vermeiden oder stark einschränken
Logs prüfen
Portfreigaben bewusst setzen
```

Status prüfen:

```bash
systemctl status ssh
```

Logs prüfen:

```bash
journalctl -u ssh
```

---

## SSH-Schlüssel

SSH-Schlüssel sind oft sicherer und praktischer als reine Passwortanmeldung.

Ein SSH-Schlüsselpaar besteht aus:

```text
privater Schlüssel
öffentlicher Schlüssel
```

Der private Schlüssel bleibt geheim.

Der öffentliche Schlüssel darf auf Servern oder GitHub hinterlegt werden.

Wichtig:

```text
privaten Schlüssel nie teilen
privaten Schlüssel nicht in Git speichern
Passphrase für Schlüssel nutzen
alte Schlüssel entfernen
```

---

## sudo

Unter Linux erlaubt `sudo`, einzelne Befehle mit erhöhten Rechten auszuführen.

Beispiel:

```bash
sudo apt update
```

Wichtig:

```text
sudo bewusst nutzen
nicht dauerhaft als root arbeiten
nur vertrauenswürdige Befehle mit sudo ausführen
sudo-Rechte nur passenden Benutzern geben
```

Prüfen, wer in der sudo-Gruppe ist:

```bash
getent group sudo
```

---

## Dateirechte unter Linux

Linux nutzt Rechte für Besitzer, Gruppe und andere.

Anzeigen:

```bash
ls -l
```

Beispiel:

```text
-rw-r----- 1 user gruppe datei.txt
```

Vereinfacht:

| Bereich | Bedeutung |
|---|---|
| Besitzer | Rechte für den Eigentümer |
| Gruppe | Rechte für Gruppenmitglieder |
| Andere | Rechte für alle anderen |

Rechte:

```text
r = read = lesen
w = write = schreiben
x = execute = ausführen
```

---

## chmod und chown

Mit `chmod` ändert man Rechte.

Beispiel:

```bash
chmod 600 datei.txt
```

Mit `chown` ändert man Besitzer.

Beispiel:

```bash
sudo chown user:gruppe datei.txt
```

Wichtig:

```text
Rechte nicht blind auf 777 setzen.
```

`777` bedeutet, dass jeder lesen, schreiben und ausführen darf.

Das ist meistens unsicher.

---

## Gefährliche Rechte

Ein typischer Fehler:

```bash
chmod 777 datei
```

Das gibt allen Benutzern volle Rechte.

Problem:

```text
jeder kann lesen
jeder kann ändern
jeder kann ausführen
```

Besser ist, gezielt zu überlegen:

```text
Wer braucht Zugriff?
Welche Gruppe braucht Zugriff?
Wird Schreibzugriff wirklich benötigt?
```

Beispiel für private SSH-Schlüssel:

```bash
chmod 600 ~/.ssh/id_ed25519
```

---

## Zugriff auf Netzlaufwerke

In Unternehmen werden häufig Netzlaufwerke genutzt.

Beispiele:

```text
Abteilungsordner
Projektordner
Home-Laufwerk
Austauschordner
Archiv
```

Wichtig:

```text
Rechte nach Gruppen vergeben
keine unnötigen Vollzugriffe
alte Benutzer entfernen
Zugriffe regelmäßig prüfen
sensible Daten getrennt speichern
```

Ein häufiger Fehler ist ein Austauschordner, der irgendwann für alles genutzt wird und zu viele Rechte bekommt.

---

## Onboarding

Onboarding bedeutet:

```text
Ein neuer Benutzer wird eingerichtet.
```

Dabei muss klar sein:

```text
Welche Konten braucht die Person?
Welche Gruppen?
Welche Anwendungen?
Welche Geräte?
Welche E-Mail-Adresse?
Welche Rechte?
Welche Sicherheitsregeln?
```

Gute Onboarding-Prozesse verhindern, dass Benutzer zu viele oder zu wenige Rechte bekommen.

---

## Offboarding

Offboarding bedeutet:

```text
Ein Benutzer verlässt die Organisation oder wechselt die Rolle.
```

Wichtig:

```text
Konto deaktivieren
Zugänge entfernen
Gruppenmitgliedschaften prüfen
Geräte zurückgeben
VPN-Zugang entfernen
MFA/Token zurücksetzen
Weiterleitungen prüfen
Datenübergabe regeln
```

Offboarding ist sicherheitskritisch.

Ein altes aktives Konto kann ein großes Risiko sein.

---

## Rollenwechsel

Nicht nur Eintritt und Austritt sind wichtig.

Auch Rollenwechsel müssen geprüft werden.

Beispiel:

```text
Mitarbeiter wechselt von Support zu Buchhaltung.
```

Dann sollte man prüfen:

```text
Welche alten Rechte müssen weg?
Welche neuen Rechte werden gebraucht?
Welche Gruppen müssen angepasst werden?
```

Sonst sammeln Benutzer über Jahre immer mehr Rechte.

Das nennt man oft Rechte-Wildwuchs.

---

## Rechteprüfung

Rechte sollten regelmäßig überprüft werden.

Fragen:

```text
Wer hat Adminrechte?
Wer ist in welchen Gruppen?
Welche alten Konten existieren noch?
Welche Dienstkonten gibt es?
Welche Freigaben sind offen?
Welche Rechte sind nicht mehr nötig?
```

Diese Prüfung hilft, unnötige Risiken zu reduzieren.

---

## Protokollierung von Zugriffen

Zugriffe und Änderungen sollten nachvollziehbar sein.

Beispiele:

```text
Login erfolgreich
Login fehlgeschlagen
Adminaktion durchgeführt
Benutzerkonto geändert
Firewall-Regel geändert
Datei gelöscht
Passwort geändert
```

Logs helfen bei:

```text
Fehlersuche
Sicherheitsvorfällen
Nachvollziehbarkeit
Audits
```

Wichtig:

```text
Logs müssen geschützt werden.
Logs dürfen nicht von jedem geändert werden.
```

---

## Zugriffsfreigaben dokumentieren

Zugriffsrechte sollten dokumentiert werden.

Beispiele:

```text
Wer hat Zugriff auf welchen Ordner?
Welche Gruppe darf auf welchen Server?
Wer hat Adminrechte?
Welche Dienstkonten existieren?
Wer hat Zugriff auf Backups?
Wer darf Firewall-Regeln ändern?
```

Ohne Dokumentation ist später schwer zu erkennen, ob ein Zugriff korrekt oder gefährlich ist.

---

## Beispiel: Dateiserver-Rechte

Ein einfacher Dateiserver könnte so aufgebaut sein:

| Ordner | Zugriff |
|---|---|
| `public` | alle Mitarbeiter lesen/schreiben |
| `hr` | nur HR |
| `it-admin` | nur IT-Admins |
| `projects` | Projektgruppen |
| `backup` | nur Backup-Dienst und Admins |

Wichtig:

```text
Nicht jeder braucht Zugriff auf alles.
```

---

## Beispiel: Adminzugriff auf Server

Ziel:

```text
Nur IT-Admins dürfen per SSH auf Server zugreifen.
```

Maßnahmen:

```text
eigene Admin-Konten
SSH-Schlüssel
MFA, wenn möglich
Firewall nur aus Admin-Netz
sudo-Rechte begrenzen
Logs prüfen
alte Admins entfernen
```

Prüfen:

```bash
getent group sudo
systemctl status ssh
journalctl -u ssh
sudo ufw status
```

---

## Beispiel: GitHub-Konto absichern

Für GitHub sind wichtig:

```text
starkes Passwort
MFA aktiv
SSH-Schlüssel geschützt
keine Secrets in Repositories
private und öffentliche Repos bewusst trennen
Zugriffsrechte auf Organisationen prüfen
alte Tokens löschen
```

Besonders gefährlich:

```text
API-Token oder .env-Datei öffentlich committen
```

---

## Beispiel: Datenbankzugriff

Datenbanken sollten nicht mit einem einzigen Superuser für alles genutzt werden.

Besser:

```text
eigener Benutzer für Anwendung
nur benötigte Datenbankrechte
kein unnötiger externer Zugriff
starkes Passwort oder Secret-Verwaltung
Backups geschützt
Zugriffe dokumentiert
```

Beispiel schlecht:

```text
App nutzt postgres-Superuser für alles.
```

Besser:

```text
App nutzt eigenen Datenbankbenutzer mit begrenzten Rechten.
```

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| gleiche Passwörter mehrfach verwenden | ein Leak gefährdet mehrere Konten |
| MFA nicht aktivieren | Passwortdiebstahl reicht aus |
| Adminrechte für normale Benutzer | Schaden bei Fehlern oder Malware größer |
| gemeinsame Admin-Konten nutzen | keine klare Nachvollziehbarkeit |
| alte Konten aktiv lassen | unnötiger Zugriff bleibt bestehen |
| Rechte nie prüfen | Rechte-Wildwuchs |
| `chmod 777` verwenden | zu offene Dateirechte |
| Secrets in Git speichern | Zugangsdaten können öffentlich werden |
| Dienstkonten zu mächtig machen | hoher Schaden bei Kompromittierung |
| Zugriffe nicht dokumentieren | spätere Kontrolle schwierig |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Passwörtern, Authentifizierung und Zugriff:

```text
starke und einzigartige Passwörter nutzen
Passwortmanager verwenden
MFA für wichtige Konten aktivieren
Adminrechte sparsam vergeben
normale und administrative Konten trennen
Gruppen und Rollen statt Einzelrechte nutzen
alte Konten deaktivieren
Rechte regelmäßig prüfen
Secrets nicht in Git speichern
Zugriffe dokumentieren
```

Wichtige Regel:

```text
So wenig Rechte wie möglich, so viele wie nötig.
```

---

## Praktische Befehle unter Linux

### Aktuellen Benutzer anzeigen

```bash
whoami
```

### Gruppen des aktuellen Benutzers anzeigen

```bash
groups
```

### Benutzerinformationen anzeigen

```bash
id
```

### sudo-Gruppe anzeigen

```bash
getent group sudo
```

### Dateirechte anzeigen

```bash
ls -l
```

### Besitzer ändern

```bash
sudo chown user:gruppe datei
```

### Rechte ändern

```bash
chmod 600 datei
chmod 700 verzeichnis
```

### SSH-Status prüfen

```bash
systemctl status ssh
```

### SSH-Logs prüfen

```bash
journalctl -u ssh
```

---

## FISI-Bezug

Passwörter, Authentifizierung und Zugriffskontrolle gehören direkt zur FISI-Praxis.

Man braucht dieses Wissen für:

```text
Benutzerkonten verwalten
Gruppen und Rechte pflegen
Adminzugänge absichern
SSH-Zugriff konfigurieren
Dateirechte prüfen
Netzlaufwerke berechtigen
Dienstkonten einordnen
MFA erklären
Offboarding durchführen
Secrets schützen
Zugriffe dokumentieren
```

Ein FISI muss verstehen, dass Zugriff nicht nur technisch funktionieren muss.

Zugriff muss auch sicher, nachvollziehbar und auf das notwendige Maß begrenzt sein.

---

## Kurze Zusammenfassung

Passwörter schützen Benutzerkonten, sind aber allein oft nicht genug.

MFA erhöht die Sicherheit, weil ein gestohlenes Passwort allein nicht ausreicht.

Authentifizierung prüft die Identität eines Benutzers. Autorisierung prüft, was dieser Benutzer tun darf.

Zugriffsrechte sollten nach Rollen, Gruppen, Least Privilege und Need-to-know vergeben werden.

Admin-Konten, Dienstkonten, SSH-Zugänge, Dateirechte und Secrets müssen besonders geschützt werden.

Für FISI ist dieses Thema sehr wichtig, weil Benutzerverwaltung, Rechtevergabe und Zugriffskontrolle tägliche Aufgaben in der Systemintegration sind.