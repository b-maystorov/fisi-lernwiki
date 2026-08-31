# 6. Datenschutz und Dokumentation

In diesem Kapitel geht es um Datenschutz und Dokumentation.

Datenschutz und IT-Sicherheit hängen eng zusammen. IT-Sicherheit schützt Systeme, Netzwerke und Daten technisch. Datenschutz achtet besonders darauf, dass personenbezogene Daten nur erlaubt, notwendig und sicher verarbeitet werden.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil man in der Praxis mit Benutzerkonten, Logs, Backups, Tickets, Screenshots, Zugriffsrechten, Geräten, Netzwerkdaten und technischer Dokumentation arbeitet.

---

## Kurz erklärt

Datenschutz bedeutet:

```text
personenbezogene Daten schützen
Zugriffe begrenzen
Daten nicht unnötig speichern
Daten sicher verarbeiten
Daten nicht unkontrolliert weitergeben
Vorfälle korrekt melden und dokumentieren
```

Dokumentation bedeutet:

```text
technische Informationen sauber festhalten
Änderungen nachvollziehbar machen
Systeme verständlich beschreiben
Fehler und Lösungen festhalten
Verantwortlichkeiten sichtbar machen
```

Beides gehört zu professioneller IT-Arbeit.

---

## Personenbezogene Daten

Personenbezogene Daten sind Informationen, die sich auf eine bestimmte oder bestimmbare Person beziehen.

Beispiele:

```text
Name
Adresse
E-Mail-Adresse
Telefonnummer
Geburtsdatum
Kundennummer
Personalnummer
Benutzername
IP-Adresse
Login-Zeit
Gerätename
Standortdaten
Bewerbungsdaten
Support-Tickets
```

Auch technische Daten können personenbezogen sein, wenn sie einer Person zugeordnet werden können.

Beispiel:

```text
Benutzer max.mustermann meldet sich um 09:15 Uhr von IP-Adresse 192.168.10.55 an.
```

Das ist nicht nur eine technische Information, sondern auch ein personenbezogener Vorgang.

---

## Warum Datenschutz wichtig ist

Datenschutz schützt Menschen vor Missbrauch ihrer Daten.

Ohne Datenschutz könnten Daten unkontrolliert gesammelt, kopiert, gespeichert, weitergegeben oder ausgewertet werden.

Mögliche Folgen:

```text
Identitätsdiebstahl
unerlaubte Überwachung
finanzieller Schaden
Rufschaden
Verlust von Vertrauen
rechtliche Probleme
unberechtigter Zugriff auf private Informationen
```

In der IT bedeutet Datenschutz:

```text
nicht alles speichern, nur weil es technisch möglich ist
nicht jedem Zugriff geben, nur weil es bequem ist
nicht Daten kopieren, nur weil es schnell geht
nicht Logs öffentlich machen, nur weil sie hilfreich sind
```

---

## Datenschutz und IT-Sicherheit

Datenschutz und IT-Sicherheit sind nicht dasselbe, aber sie ergänzen sich.

| Bereich | Fokus |
|---|---|
| Datenschutz | Schutz personenbezogener Daten |
| IT-Sicherheit | Schutz von Systemen, Daten und Diensten |

Beispiel:

```text
Ein Dateiserver enthält Personaldaten.
```

Datenschutz fragt:

```text
Dürfen diese Daten verarbeitet werden?
Wer darf sie sehen?
Wie lange dürfen sie gespeichert werden?
```

IT-Sicherheit fragt:

```text
Sind Rechte korrekt gesetzt?
Sind Backups geschützt?
Gibt es Logs?
Ist der Server aktuell?
Ist der Zugriff abgesichert?
```

In der Praxis braucht man beide Perspektiven.

---

## Grundprinzip: Datenminimierung

Datenminimierung bedeutet:

```text
Nur die Daten verarbeiten, die wirklich benötigt werden.
```

Schlechtes Beispiel:

```text
Für ein einfaches Support-Ticket werden private Adresse, Geburtsdatum und Ausweiskopie gespeichert.
```

Besser:

```text
Es werden nur Benutzername, Gerätename, Fehlerbeschreibung und notwendige technische Informationen gespeichert.
```

Wichtige Frage:

```text
Brauchen wir diese Information wirklich für diese Aufgabe?
```

---

## Zweckbindung

Zweckbindung bedeutet:

```text
Daten werden nur für den Zweck genutzt, für den sie erhoben wurden.
```

Beispiel:

```text
Eine E-Mail-Adresse wird für die Benutzerverwaltung gespeichert.
```

Dann sollte sie nicht einfach ohne passenden Grund für andere Zwecke genutzt werden.

In der IT-Praxis bedeutet das:

```text
Daten nicht unnötig kopieren
Produktivdaten nicht ungeprüft in Testsysteme übernehmen
Logs nicht für fremde Zwecke auswerten
Screenshots nicht unnötig weitergeben
```

---

## Zugriffsbeschränkung

Personenbezogene Daten dürfen nicht für jeden sichtbar sein.

Beispiele:

```text
HR-Daten nur für HR
Bewerbungsdaten nur für zuständige Personen
Kundendaten nur für berechtigte Rollen
Backups nur für Admins und Backup-Dienst
Logs nur für berechtigte IT-Mitarbeiter
```

Technische Maßnahmen:

```text
Benutzerrechte
Gruppen
Rollen
MFA
Verschlüsselung
Netztrennung
Logging
Need-to-know-Prinzip
Least Privilege
```

Wichtig:

```text
Nicht jeder Administrator braucht automatisch Zugriff auf alle Inhalte.
```

---

## Logs und Datenschutz

Logs sind wichtig für IT-Sicherheit und Fehlersuche.

Sie können aber personenbezogene Daten enthalten.

Beispiele:

```text
Benutzername
IP-Adresse
Login-Zeit
fehlgeschlagene Anmeldung
Gerätename
E-Mail-Adresse
Adminaktionen
aufgerufene interne Dienste
```

Deshalb müssen Logs geschützt werden.

Wichtige Fragen:

```text
Wer darf Logs lesen?
Wie lange werden Logs gespeichert?
Welche Daten stehen in Logs?
Sind Logs gegen Manipulation geschützt?
Werden sensible Daten unnötig geloggt?
```

Logs sind hilfreich, aber sie dürfen nicht unkontrolliert für alle sichtbar sein.

---

## Backups und Datenschutz

Backups enthalten oft dieselben sensiblen Daten wie Produktivsysteme.

Beispiele:

```text
Kundendaten
Personaldaten
E-Mails
Datenbanken
Konfigurationsdateien
Benutzerdateien
Tickets
```

Deshalb müssen Backups genauso geschützt werden wie die Originaldaten.

Maßnahmen:

```text
Zugriff auf Backups begrenzen
Backups verschlüsseln
Backup-Orte dokumentieren
Restore testen
alte Backups kontrolliert löschen
Backup-Logs prüfen
```

Wichtiger Satz:

```text
Ein Backup ist nicht weniger schützenswert als das Originalsystem.
```

---

## Testdaten

Testsysteme sollten nicht einfach echte personenbezogene Daten enthalten.

Schlechtes Beispiel:

```text
Produktivdatenbank wird komplett in eine Testumgebung kopiert.
Alle echten Kundendaten liegen jetzt im Testsystem.
```

Besser:

```text
anonymisierte Testdaten
synthetische Beispieldaten
nur notwendige Ausschnitte
Zugriffe auf Testsystem begrenzen
```

Testsysteme sind oft weniger geschützt als Produktivsysteme. Deshalb sind echte Daten dort besonders riskant.

---

## Anonymisierung und Pseudonymisierung

Anonymisierung bedeutet:

```text
Daten können keiner Person mehr zugeordnet werden.
```

Pseudonymisierung bedeutet:

```text
direkte Merkmale werden ersetzt, aber eine Zuordnung ist unter bestimmten Bedingungen noch möglich.
```

Beispiel Original:

```text
Bilgin Maystorov, bilgin@example.com, Kundennummer 12345
```

Pseudonymisiert:

```text
Benutzer A, kunden-id-xyz
```

Anonymisierung ist stärker, wenn keine realistische Zuordnung zur Person mehr möglich ist.

---

## Ticketsysteme und Datenschutz

Ticketsysteme enthalten oft viele Informationen.

Beispiele:

```text
Benutzername
Gerätename
Fehlerbeschreibung
Screenshots
IP-Adresse
Telefonnummer
E-Mail-Adresse
interne Systeme
Logs
```

Gute Arbeitsweise:

```text
nur notwendige Daten ins Ticket schreiben
keine Passwörter ins Ticket schreiben
Screenshots vorher prüfen
sensible Informationen schwärzen
Zugriffsrechte im Ticketsystem begrenzen
Lösung nachvollziehbar dokumentieren
```

Ein gutes Ticket hilft bei Support und Nachvollziehbarkeit, darf aber keine unnötigen privaten Daten sammeln.

---

## Screenshots

Screenshots können mehr zeigen als geplant.

Sichtbar sein können:

```text
E-Mail-Adressen
Kundendaten
Benutzernamen
IP-Adressen
interne URLs
Tokens
Passwörter
private Nachrichten
Fehlermeldungen mit Pfaden
```

Vor dem Teilen eines Screenshots prüfen:

```text
Sind personenbezogene Daten sichtbar?
Sind Passwörter oder Tokens sichtbar?
Sind interne Systeme sichtbar?
Muss etwas geschwärzt werden?
Ist der Screenshot wirklich nötig?
```

Oft ist eine textbasierte Erklärung sicherer als ein Screenshot.

---

## Passwörter und Secrets

Passwörter, Tokens und Schlüssel dürfen nicht in Dokumentation, Tickets oder Git gespeichert werden.

Gefährliche Beispiele:

```text
Passwort im Ticket
API-Key im README
SSH-Key im Repository
Datenbankpasswort in Screenshot
.env-Datei in GitHub
Token in Chatnachricht
```

Besser:

```text
Secrets sicher speichern
.env.example ohne echte Werte nutzen
Passwörter nur über sichere Wege weitergeben
Tokens regelmäßig prüfen
versehentlich veröffentlichte Secrets sofort austauschen
```

Dokumentation darf erklären, wo ein Secret sicher liegt, aber nicht das Secret selbst enthalten.

Beispiel gut:

```text
Datenbankpasswort liegt im Passwortmanager im Eintrag "PostgreSQL Produktion".
```

Beispiel schlecht:

```text
Datenbankpasswort: library123
```

---

## Dokumentation

Dokumentation ist ein wichtiger Teil professioneller IT-Arbeit.

Sie hilft bei:

```text
Fehlersuche
Übergabe
Wartung
Sicherheit
Audit
Schulung
Notfällen
Wiederherstellung
```

Ohne Dokumentation hängt Wissen nur in den Köpfen einzelner Personen.

Das ist riskant, wenn diese Personen krank sind, die Abteilung wechseln oder die Firma verlassen.

---

## Warum Dokumentation sicherheitsrelevant ist

Dokumentation ist nicht nur Ordnung.

Sie ist auch Sicherheit.

Beispiele:

```text
Firewall-Regeln sind dokumentiert.
Backup-Plan ist dokumentiert.
Admin-Konten sind dokumentiert.
IP-Adressen und VLANs sind dokumentiert.
Restore-Anleitung ist dokumentiert.
Notfallkontakte sind dokumentiert.
```

Wenn ein Problem entsteht, spart gute Dokumentation Zeit.

Schlechte oder fehlende Dokumentation führt zu Fehlern, doppelter Arbeit und unsicheren Änderungen.

---

## Was dokumentiert werden sollte

Typische IT-Dokumentation:

| Bereich | Inhalt |
|---|---|
| Netzwerk | IP-Plan, VLANs, Gateways, DNS, DHCP |
| Server | Hostname, IP, Dienste, Ports, Betriebssystem |
| Benutzer | Rollen, Gruppen, besondere Rechte |
| Firewall | Regeln, Quelle, Ziel, Port, Zweck |
| Backup | Zeitplan, Speicherort, Restore-Test |
| Anwendungen | Version, Konfiguration, Abhängigkeiten |
| Docker | Compose-Dateien, Volumes, Ports, Netzwerke |
| VMs | Netzwerkmodus, Ressourcen, Zweck |
| Änderungen | Was wurde geändert, wann und warum |
| Vorfälle | Was ist passiert, Ursache, Maßnahme |

---

## Gute technische Dokumentation

Gute Dokumentation sollte:

```text
klar
aktuell
verständlich
strukturiert
auffindbar
nachvollziehbar
nicht unnötig lang
frei von echten Secrets
```

Gute Dokumentation beantwortet:

```text
Was ist das System?
Wofür ist es da?
Wie ist es erreichbar?
Welche Dienste laufen?
Welche Abhängigkeiten gibt es?
Wie wird es gesichert?
Wie wird es wiederhergestellt?
Wer ist verantwortlich?
```

---

## Änderungsdokumentation

Änderungen sollten nachvollziehbar sein.

Dokumentiert werden sollte:

```text
Datum
System
Änderung
Grund
verantwortliche Person
Ticketnummer
Test nach Änderung
Rollback-Möglichkeit
```

Beispiel:

```text
2026-08-31
Server: web01
Änderung: nginx aktualisiert
Grund: Sicherheitsupdate
Test: Webseite erreichbar, Logs ohne Fehler
Rollback: VM-Snapshot vor Update
```

Das hilft bei späterer Fehlersuche.

---

## Tickets sauber schreiben

Ein schlechtes Ticket:

```text
Internet geht nicht.
```

Ein besseres Ticket:

```text
Client hat IP 192.168.10.55/24.
Gateway 192.168.10.1 ist erreichbar.
Ping auf 8.8.8.8 funktioniert.
DNS-Auflösung mit github.com schlägt fehl.
Vermutung: DNS-Problem.
```

Ein gutes Ticket beschreibt nicht nur das Problem, sondern auch die bereits geprüften Schritte.

---

## Incident-Dokumentation

Bei Sicherheitsvorfällen ist Dokumentation besonders wichtig.

Dokumentiert werden sollte:

```text
Was wurde gemeldet?
Wann wurde es gemeldet?
Welche Systeme sind betroffen?
Welche Benutzer sind betroffen?
Welche ersten Maßnahmen wurden durchgeführt?
Welche Logs wurden gesichert?
Welche Ursache wurde gefunden?
Welche Maßnahmen wurden umgesetzt?
Welche Lessons Learned gibt es?
```

Wichtig:

```text
Fakten und Vermutungen trennen.
Ruhig und sachlich dokumentieren.
Keine Beweise löschen.
```

---

## Datenschutzvorfall

Ein Datenschutzvorfall kann entstehen, wenn personenbezogene Daten unberechtigt offengelegt, verändert, verloren oder zugänglich gemacht werden.

Beispiele:

```text
E-Mail mit Kundendaten an falschen Empfänger
Laptop mit unverschlüsselten Daten verloren
Backup mit Personaldaten öffentlich erreichbar
falsche Rechte auf HR-Ordner
Datenbank mit personenbezogenen Daten im Internet erreichbar
```

Gute erste Reaktion:

```text
zuständige Stelle informieren
nicht vertuschen
Fakten dokumentieren
Auswirkungen begrenzen
keine Beweise löschen
interne Prozesse beachten
```

---

## Löschung und Aufbewahrung

Daten sollten nicht unbegrenzt gespeichert werden, wenn sie nicht mehr benötigt werden.

Das betrifft zum Beispiel:

```text
alte Benutzerkonten
alte Tickets
alte Logs
alte Backups
alte Exporte
alte Testdaten
alte Screenshots
```

Wichtige Fragen:

```text
Wie lange müssen Daten aufbewahrt werden?
Wann dürfen oder müssen Daten gelöscht werden?
Wer ist verantwortlich?
Wie wird Löschung dokumentiert?
Gibt es Daten noch in Backups?
```

---

## Öffentliche GitHub-Repositories

Bei öffentlichen Repositories muss man besonders vorsichtig sein.

Nicht veröffentlichen:

```text
echte IP-Pläne einer Firma
interne Hostnamen
Kundendaten
Passwörter
Tokens
private Screenshots
interne Tickets
personenbezogene Daten
private SSH-Keys
echte .env-Dateien
```

Besser:

```text
Beispieldaten nutzen
private Informationen entfernen
IP-Adressen aus Beispielbereichen verwenden
Namen anonymisieren
Screenshots prüfen oder vermeiden
.env.example ohne echte Secrets nutzen
```

Ein öffentliches Lern-Wiki soll zeigen, was man gelernt hat, aber keine vertraulichen Informationen veröffentlichen.

---

## Markdown für Dokumentation

Markdown ist gut für technische Dokumentation.

Vorteile:

```text
einfach zu schreiben
gut lesbar
funktioniert auf GitHub
Versionierung mit Git
Codeblöcke möglich
Tabellen möglich
Links möglich
```

Typische Markdown-Elemente:

| Element | Beispiel |
|---|---|
| Überschrift | `# Überschrift` |
| Unterüberschrift | `## Unterüberschrift` |
| Codeblock | drei Backticks vor und nach dem Code |
| Tabelle | Spalten mit `|` trennen |
| Link | `[Text](ziel)` |

Markdown ist deshalb gut für Lernnotizen, Projekt-Dokumentation und technische Anleitungen.

---

## Praktische Checkliste Datenschutz

Vor dem Speichern oder Teilen von Informationen fragen:

```text
Sind personenbezogene Daten enthalten?
Brauchen wir diese Daten wirklich?
Wer darf diese Daten sehen?
Wie lange müssen sie gespeichert werden?
Sind sie geschützt?
Ist ein Screenshot notwendig?
Sind Passwörter oder Tokens sichtbar?
Ist das für ein öffentliches Repository geeignet?
```

---

## Praktische Checkliste Dokumentation

Eine gute technische Notiz beantwortet:

```text
Was wurde gemacht?
Warum wurde es gemacht?
Auf welchem System?
Wann wurde es gemacht?
Wer war beteiligt?
Welche Befehle wurden genutzt?
Was war das Ergebnis?
Gab es Fehler?
Wie wurde getestet?
Was ist der nächste Schritt?
```

Diese Fragen helfen besonders bei Support, Projekten und Prüfungsvorbereitung.

---

## Typische Fehler

| Fehler | Problem |
|---|---|
| Passwörter in Dokumentation | hohes Sicherheitsrisiko |
| echte Daten in Screenshots | Datenschutzproblem |
| Tickets mit zu vielen privaten Daten | unnötige Datensammlung |
| Logs für alle sichtbar | personenbezogene Daten offen |
| Backups nicht geschützt | viele Daten auf einmal gefährdet |
| alte Konten nicht dokumentiert | unnötige Zugriffe bleiben |
| Änderungen nicht dokumentiert | Fehler später schwer nachvollziehbar |
| öffentliche Repos mit internen Infos | vertrauliche Daten werden sichtbar |
| Testsysteme mit echten Daten | Datenschutzrisiko |
| Dokumentation veraltet | falsche Entscheidungen |

---

## Gute Arbeitsweise

Eine gute Arbeitsweise bei Datenschutz und Dokumentation:

```text
nur notwendige Daten speichern
Zugriffe begrenzen
keine Passwörter dokumentieren
Screenshots prüfen
Tickets sachlich schreiben
Änderungen dokumentieren
Backups und Logs schützen
alte Daten regelmäßig prüfen
öffentliche Repos sauber halten
Beispieldaten statt echte Daten nutzen
```

Wichtige Regel:

```text
Dokumentation soll helfen, aber keine neuen Sicherheitsprobleme erzeugen.
```

---

## FISI-Bezug

Datenschutz und Dokumentation gehören direkt zur FISI-Praxis.

Man braucht dieses Wissen für:

```text
Benutzerverwaltung
Support-Tickets
Serverbetrieb
Netzwerkdokumentation
Backup-Konzepte
Loganalyse
Rechteverwaltung
Sicherheitsvorfälle
öffentliche GitHub-Projekte
Projektübergaben
Prüfungsvorbereitung
technische Handbücher
```

Ein FISI muss nicht nur Systeme konfigurieren.

Ein FISI muss auch sauber dokumentieren, vertrauliche Informationen schützen und personenbezogene Daten bewusst behandeln.

---

## Kurze Zusammenfassung

Datenschutz schützt personenbezogene Daten vor unberechtigtem Zugriff, unnötiger Verarbeitung, Verlust und Missbrauch.

IT-Dokumentation macht Systeme, Änderungen, Fehler, Zugriffe und Prozesse nachvollziehbar.

Logs, Backups, Tickets, Screenshots und Git-Repositories können personenbezogene oder vertrauliche Informationen enthalten und müssen deshalb bewusst behandelt werden.

Gute Dokumentation hilft bei Betrieb, Sicherheit, Fehlersuche, Übergabe und Notfällen.

Für FISI ist dieses Thema wichtig, weil technische Arbeit ohne saubere Dokumentation und Datenschutzbewusstsein schnell unsicher und unprofessionell wird.