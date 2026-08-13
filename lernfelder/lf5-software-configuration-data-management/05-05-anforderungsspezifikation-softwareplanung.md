# 5.5 Anforderungsspezifikation und Softwareplanung

In diesem Kapitel geht es darum, Anforderungen an eine Softwarelösung zu beschreiben und daraus eine sinnvolle Planung abzuleiten.

Bevor Software entwickelt wird, muss klar sein, was die Software leisten soll, für wen sie gedacht ist, welche Daten verarbeitet werden, welche Rahmenbedingungen gelten und wie das Ergebnis später geprüft werden kann.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Software nicht nur programmiert, sondern auch geplant, betrieben, abgesichert, dokumentiert und in bestehende IT-Umgebungen integriert werden muss.

---

## Kurz erklärt

Eine Anforderung beschreibt, was eine Software können muss oder welche Eigenschaften sie haben soll.

Eine Softwareplanung beschreibt, wie diese Anforderungen technisch und organisatorisch umgesetzt werden sollen.

Dazu gehören:

- Ausgangssituation verstehen
- Ziel der Software klären
- Benutzer und Rollen bestimmen
- funktionale Anforderungen erfassen
- nicht-funktionale Anforderungen erfassen
- Daten und Datenquellen betrachten
- Schnittstellen erkennen
- Sicherheitsanforderungen beachten
- Datenschutz prüfen
- technische Umgebung planen
- Tests vorbereiten
- Dokumentation planen
- Abnahmekriterien festlegen

Gute Planung verhindert, dass man direkt Code schreibt, ohne das eigentliche Problem verstanden zu haben.

---

## Warum Anforderungen wichtig sind

Anforderungen sind die Grundlage für die Entwicklung.

Ohne klare Anforderungen entstehen häufig Probleme:

- Software erfüllt nicht den Bedarf
- wichtige Funktionen fehlen
- unnötige Funktionen werden gebaut
- Benutzer können die Software schlecht bedienen
- Sicherheit wird vergessen
- Datenstruktur passt nicht
- Tests sind schwer möglich
- Projekt dauert länger
- Änderungen werden chaotisch
- Ergebnis ist nicht eindeutig bewertbar

Anforderungen helfen also dabei, das Ziel greifbar zu machen.

Eine Software kann nur sinnvoll geprüft werden, wenn vorher festgelegt wurde, was sie leisten soll.

---

## Anforderungsspezifikation

Eine Anforderungsspezifikation ist eine strukturierte Beschreibung der Anforderungen.

Sie beschreibt möglichst genau, was die Software erfüllen muss.

Typische Inhalte:

- Ziel der Software
- Ausgangssituation
- Benutzergruppen
- funktionale Anforderungen
- nicht-funktionale Anforderungen
- Datenanforderungen
- Schnittstellen
- Sicherheitsanforderungen
- Datenschutzanforderungen
- technische Rahmenbedingungen
- Einschränkungen
- Abnahmekriterien
- offene Fragen

Die Spezifikation dient als gemeinsame Grundlage für Auftraggeber, Benutzer, Entwickler, Administratoren und Tester.

---

## Ziel einer Anforderungsspezifikation

Das Ziel ist, Missverständnisse zu vermeiden.

Eine gute Anforderungsspezifikation beantwortet Fragen wie:

- Was soll die Software tun?
- Wer nutzt die Software?
- Welche Daten werden verarbeitet?
- Welche Systeme sind beteiligt?
- Welche Rechte werden benötigt?
- Welche Sicherheitsanforderungen gelten?
- Wie schnell oder zuverlässig muss die Software sein?
- Wie wird getestet?
- Wann gilt die Software als fertig?
- Welche Grenzen hat das Projekt?

Je klarer diese Punkte sind, desto einfacher wird Planung, Umsetzung und Abnahme.

---

## Funktionale Anforderungen

Funktionale Anforderungen beschreiben, was die Software tun soll.

Sie beschreiben konkrete Funktionen oder Verhalten.

Beispiele:

- Benutzer können sich anmelden.
- Benutzer können neue Datensätze anlegen.
- Datensätze können gesucht werden.
- Datensätze können bearbeitet werden.
- Datensätze können gelöscht werden.
- Admins können Benutzer verwalten.
- Berichte können exportiert werden.
- Dateien können hochgeladen werden.
- System sendet Benachrichtigungen.
- Software prüft Eingaben auf Fehler.

Funktionale Anforderungen sind meistens direkt testbar.

Wenn eine Anforderung lautet, dass Benutzer Tickets nach Status filtern können, kann später geprüft werden, ob diese Funktion existiert und korrekt funktioniert.

---

## Nicht-funktionale Anforderungen

Nicht-funktionale Anforderungen beschreiben Eigenschaften der Software.

Sie sagen nicht direkt, welche Funktion vorhanden ist, sondern wie gut oder unter welchen Bedingungen die Software funktionieren soll.

Beispiele:

- Software soll einfach bedienbar sein.
- Anwendung soll innerhalb von zwei Sekunden reagieren.
- Daten sollen verschlüsselt übertragen werden.
- Software soll unter Linux laufen.
- Anwendung soll im Browser nutzbar sein.
- System soll mehrere Benutzer gleichzeitig unterstützen.
- Software soll wartbar sein.
- Lösung soll dokumentiert sein.
- Backups sollen möglich sein.
- Zugriff soll über Rollen gesteuert werden.

Nicht-funktionale Anforderungen sind sehr wichtig, weil eine Software trotz vorhandener Funktionen schlecht sein kann, wenn sie langsam, unsicher oder schwer bedienbar ist.

---

## Unterschied zwischen funktional und nicht-funktional

| Art              | Frage                       | Beispiel                                    |
| ---------------- | --------------------------- | ------------------------------------------- |
| funktional       | Was soll die Software tun?  | Benutzer kann Ticket erstellen              |
| nicht-funktional | Wie soll die Software sein? | Ticketübersicht lädt in unter zwei Sekunden |

Beide Arten gehören zusammen.

Eine Suchfunktion ist eine funktionale Anforderung.  
Dass die Suche schnell, zuverlässig und einfach nutzbar sein soll, ist eine nicht-funktionale Anforderung.

---

## Gute Anforderungen formulieren

Eine gute Anforderung sollte klar, verständlich und prüfbar sein.

Schlecht:

- Die Software soll gut sein.
- Das System soll modern wirken.
- Die Daten sollen irgendwie gespeichert werden.
- Die Anwendung soll schnell sein.

Besser:

- Benutzer können Geräte nach Hostname suchen.
- Admins können neue Benutzerkonten anlegen.
- Die Anwendung speichert Inventardaten in einer Datenbank.
- Die Suchergebnisse werden innerhalb von zwei Sekunden angezeigt.
- Nur berechtigte Benutzer dürfen Datensätze löschen.

Gute Anforderungen vermeiden unklare Wörter wie „irgendwie“, „modern“, „besser“ oder „schnell“, wenn diese nicht genauer definiert werden.

---

## Prüfbarkeit von Anforderungen

Anforderungen sollten testbar sein.

Eine testbare Anforderung lässt sich später eindeutig prüfen.

Beispiel:

Nicht gut prüfbar:

- Die Anwendung soll benutzerfreundlich sein.

Besser prüfbar:

- Ein neuer Benutzer soll innerhalb von fünf Minuten einen Supportfall erfassen können.
- Pflichtfelder werden deutlich markiert.
- Bei fehlerhafter Eingabe erscheint eine verständliche Fehlermeldung.
- Die Navigation besteht aus maximal fünf Hauptpunkten.

Prüfbarkeit ist wichtig, weil Anforderungen sonst schwer abgenommen werden können.

---

## Muss-, Soll- und Kann-Anforderungen

Anforderungen können nach Wichtigkeit eingeteilt werden.

| Kategorie        | Bedeutung                            |
| ---------------- | ------------------------------------ |
| Muss-Anforderung | unbedingt notwendig                  |
| Soll-Anforderung | wichtig, aber nicht absolut zwingend |
| Kann-Anforderung | wünschenswert, aber optional         |

Beispiel für ein Ticketsystem:

| Kategorie | Anforderung                                      |
| --------- | ------------------------------------------------ |
| Muss      | Benutzer kann ein Ticket erstellen               |
| Muss      | Ticket erhält automatisch eine eindeutige Nummer |
| Soll      | Benutzer kann Dateien anhängen                   |
| Soll      | Tickets können nach Priorität gefiltert werden   |
| Kann      | Dashboard zeigt Statistiken grafisch an          |

Diese Einteilung hilft bei Zeitplanung und Priorisierung.

---

## Priorisierung von Anforderungen

Nicht alle Anforderungen sind gleich wichtig.

Priorisierung hilft zu entscheiden, was zuerst umgesetzt wird.

Gründe für Priorisierung:

- Zeit ist begrenzt
- Budget ist begrenzt
- manche Funktionen sind wichtiger als andere
- Sicherheitsfunktionen dürfen nicht warten
- Grundfunktionen müssen zuerst vorhanden sein
- optionale Funktionen können später folgen

Eine häufige Denkweise ist:

Zuerst muss die Software ihre Kernaufgabe sicher erfüllen. Danach können Komfortfunktionen ergänzt werden.

---

## Benutzerrollen

Viele Anwendungen haben unterschiedliche Benutzerrollen.

Beispiele:

| Rolle         | Bedeutung                                       |
| ------------- | ----------------------------------------------- |
| Gast          | darf nur öffentliche Inhalte sehen              |
| Benutzer      | darf eigene Daten nutzen                        |
| Bearbeiter    | darf Vorgänge bearbeiten                        |
| Teamleitung   | darf Berichte sehen                             |
| Administrator | darf Benutzer und Einstellungen verwalten       |
| Auditor       | darf Informationen prüfen, aber nicht verändern |

Benutzerrollen sind wichtig für Berechtigungen, Sicherheit und Bedienung.

Nicht jeder Benutzer soll alle Funktionen sehen oder nutzen können.

---

## Use Cases

Ein Use Case beschreibt, was ein Benutzer mit der Software tun möchte.

Beispiele:

- Benutzer erstellt ein Ticket.
- Admin legt einen neuen Benutzer an.
- Mitarbeiter sucht ein Gerät im Inventar.
- Supporter ändert den Status eines Tickets.
- Teamleitung exportiert einen Bericht.

Use Cases helfen, Anforderungen aus Sicht der Benutzer zu verstehen.

Sie zeigen nicht nur technische Funktionen, sondern konkrete Nutzungssituationen.

---

## User Stories

Eine User Story beschreibt eine Anforderung aus Sicht eines Benutzers.

Typische Form:

Als Benutzer möchte ich eine Funktion, damit ich ein Ziel erreiche.

Beispiel:

Als Support-Mitarbeiter möchte ich Tickets nach Priorität filtern, damit ich dringende Probleme zuerst bearbeiten kann.

User Stories helfen, den Nutzen einer Funktion zu verstehen.

Sie sind besonders nützlich, wenn Anforderungen aus Anwendersicht beschrieben werden sollen.

---

## Akzeptanzkriterien

Akzeptanzkriterien beschreiben, wann eine Anforderung erfüllt ist.

Beispiel User Story:

Als Benutzer möchte ich ein Ticket erstellen, damit mein Problem vom Support bearbeitet werden kann.

Mögliche Akzeptanzkriterien:

- Benutzer kann Titel und Beschreibung eingeben.
- Titel ist ein Pflichtfeld.
- Beschreibung ist ein Pflichtfeld.
- Nach dem Speichern erhält das Ticket eine eindeutige Nummer.
- Das Ticket erscheint in der Ticketübersicht.
- Bei fehlenden Pflichtfeldern erscheint eine Fehlermeldung.

Akzeptanzkriterien machen Anforderungen prüfbar.

---

## Datenanforderungen

Software arbeitet häufig mit Daten.

Datenanforderungen beschreiben, welche Daten gespeichert, verarbeitet oder ausgegeben werden.

Wichtige Fragen:

- Welche Daten werden erfasst?
- Welche Felder sind Pflichtfelder?
- Welche Daten dürfen leer sein?
- Welche Datentypen werden benötigt?
- Welche Daten müssen eindeutig sein?
- Welche Beziehungen gibt es?
- Wie lange werden Daten gespeichert?
- Wer darf welche Daten sehen?
- Wer darf Daten ändern oder löschen?
- Müssen Daten exportiert werden?
- Gibt es Datenschutzanforderungen?

Datenanforderungen sind wichtig für Datenmodell, Datenbank und Validierung.

---

## Beispiel für Datenanforderungen

Für eine einfache Inventarverwaltung könnten Datenanforderungen so aussehen:

| Datenfeld      | Bedeutung                         | Pflichtfeld |
| -------------- | --------------------------------- | ----------- |
| Inventarnummer | eindeutige Nummer des Geräts      | ja          |
| Hostname       | Gerätename im Netzwerk            | ja          |
| Gerätetyp      | Laptop, Desktop, Monitor, Drucker | ja          |
| Seriennummer   | Hersteller-Seriennummer           | ja          |
| Standort       | Raum oder Abteilung               | ja          |
| Benutzer       | zugeordnete Person                | nein        |
| Kaufdatum      | Datum der Beschaffung             | nein        |
| Status         | aktiv, defekt, ausgemustert       | ja          |

Solche Anforderungen helfen später beim Datenmodell und bei der Eingabeprüfung.

---

## Schnittstellenanforderungen

Schnittstellen verbinden Software mit anderen Systemen.

Beispiele:

- Datenbank
- API
- E-Mail-System
- Authentifizierung
- Dateiimport
- Dateiexport
- Drucker
- Cloud-Dienst
- Monitoring
- Ticketsystem

Wichtige Fragen:

- Welche Systeme müssen verbunden werden?
- Welche Daten werden übertragen?
- In welchem Format werden Daten übertragen?
- Wie oft findet der Austausch statt?
- Wie wird die Verbindung geschützt?
- Was passiert bei Fehlern?
- Wer darf die Schnittstelle nutzen?
- Werden Übertragungen protokolliert?

Schnittstellen müssen gut geplant werden, weil Fehler dort mehrere Systeme betreffen können.

---

## Sicherheitsanforderungen

Sicherheit muss bereits in der Anforderungsspezifikation berücksichtigt werden.

Wichtige Fragen:

- Wer darf sich anmelden?
- Wie erfolgt Authentifizierung?
- Gibt es MFA?
- Welche Rollen und Rechte gibt es?
- Werden Daten verschlüsselt?
- Werden Passwörter sicher gespeichert?
- Werden Eingaben geprüft?
- Gibt es Schutz vor Missbrauch?
- Werden sicherheitsrelevante Ereignisse protokolliert?
- Gibt es Backups?
- Gibt es Notfallprozesse?

Sicherheitsanforderungen dürfen nicht erst am Ende ergänzt werden.

Wenn Sicherheit früh eingeplant wird, ist die Umsetzung meistens sauberer und einfacher.

---

## Datenschutzanforderungen

Wenn personenbezogene Daten verarbeitet werden, müssen Datenschutzanforderungen beachtet werden.

Wichtige Fragen:

- Welche personenbezogenen Daten werden gespeichert?
- Warum werden diese Daten benötigt?
- Wer darf darauf zugreifen?
- Wie lange werden Daten gespeichert?
- Wie werden Daten gelöscht?
- Werden Daten exportiert?
- Werden Daten in Logs geschrieben?
- Werden Daten in der Cloud verarbeitet?
- Werden Testdaten anonymisiert?
- Gibt es Lösch- und Auskunftsprozesse?

Für Lernprojekte und öffentliche GitHub-Repositories sollten keine echten personenbezogenen Daten verwendet werden.

Besser sind künstliche Beispieldaten.

---

## Technische Rahmenbedingungen

Die Software muss zur Zielumgebung passen.

Wichtige Fragen:

- Auf welchem Betriebssystem läuft die Software?
- Wird Linux, Windows oder beides genutzt?
- Soll die Software lokal oder im Browser laufen?
- Wird eine Datenbank benötigt?
- Welche Programmiersprache passt?
- Welche Bibliotheken dürfen genutzt werden?
- Gibt es Netzwerkbeschränkungen?
- Gibt es Proxy, Firewall oder VPN?
- Wie wird die Software installiert?
- Wie werden Updates eingespielt?
- Wie wird die Software überwacht?
- Wie werden Backups durchgeführt?

Technische Rahmenbedingungen beeinflussen Architektur, Werkzeuge und Betrieb.

---

## Softwareplanung

Softwareplanung beschreibt, wie eine Softwarelösung umgesetzt werden soll.

Dazu gehören:

- Projektstruktur
- Programmstruktur
- Datenmodell
- Benutzerrollen
- Schnittstellen
- technische Umgebung
- Werkzeuge
- Sicherheitsmaßnahmen
- Testplanung
- Dokumentation
- Zeitplanung
- Aufgabenplanung
- Betriebskonzept

Die Planung verbindet Anforderungen mit konkreter Umsetzung.

---

## Projektstruktur planen

Eine klare Projektstruktur hilft bei Übersicht und Wartung.

Beispiel für ein kleines Python-Projekt:

| Bereich       | Zweck                    |
| ------------- | ------------------------ |
| Hauptprogramm | Startpunkt der Anwendung |
| Module        | einzelne Programmteile   |
| Tests         | Prüfung von Funktionen   |
| Dokumentation | Erklärung und Nutzung    |
| Beispieldaten | Testdaten                |
| Konfiguration | Einstellungen            |
| README        | Projektüberblick         |
| .gitignore    | ignorierte Dateien       |

Eine gute Struktur macht es leichter, das Projekt später zu verstehen und zu erweitern.

---

## Programmstruktur planen

Die Programmstruktur beschreibt, wie die Software intern aufgebaut ist.

Wichtige Fragen:

- Welche Hauptfunktionen gibt es?
- Welche Dateien oder Module werden benötigt?
- Welche Aufgaben gehören zusammen?
- Welche Funktionen sollen wiederverwendbar sein?
- Welche Daten werden übergeben?
- Wo findet Eingabe statt?
- Wo findet Verarbeitung statt?
- Wo findet Ausgabe statt?
- Wo wird Fehlerbehandlung umgesetzt?

Eine einfache Grundidee ist EVA:

| Teil         | Bedeutung                                            |
| ------------ | ---------------------------------------------------- |
| Eingabe      | Daten kommen in das Programm                         |
| Verarbeitung | Daten werden geprüft und verarbeitet                 |
| Ausgabe      | Ergebnis wird angezeigt, gespeichert oder übertragen |

Diese Denkweise hilft besonders bei kleinen Programmen.

---

## Datenmodell planen

Wenn Software Daten speichert, muss ein Datenmodell geplant werden.

Wichtige Fragen:

- Welche Objekte gibt es?
- Welche Eigenschaften haben diese Objekte?
- Welche Beziehungen bestehen?
- Welche Daten müssen eindeutig sein?
- Welche Pflichtfelder gibt es?
- Welche Datentypen werden benötigt?
- Welche Regeln gelten?
- Welche Daten müssen geschützt werden?

Beispiel:

Eine Inventarverwaltung braucht Geräte, Benutzer, Standorte und Zuordnungen.

Daraus können später Tabellen, Klassen oder Datenstrukturen entstehen.

---

## Ablauf planen

Ein Ablauf beschreibt, welche Schritte eine Software ausführt.

Beispiel: Ticket erstellen

1. Benutzer öffnet Formular.
2. Benutzer gibt Titel und Beschreibung ein.
3. Software prüft Pflichtfelder.
4. Software speichert Ticket.
5. Ticket erhält eine Nummer.
6. Benutzer erhält Bestätigung.
7. Ticket erscheint in der Übersicht.

Solche Abläufe helfen, Funktionen vor dem Programmieren zu verstehen.

Sie können auch als Ablaufdiagramm, PAP, Struktogramm oder einfache Schrittfolge dargestellt werden.

---

## Fehlerfälle planen

Softwareplanung sollte nicht nur den normalen Ablauf betrachten.

Auch Fehlerfälle müssen berücksichtigt werden.

Beispiele:

- Pflichtfeld fehlt
- Datei existiert nicht
- Datenbank ist nicht erreichbar
- Benutzer hat keine Rechte
- Netzwerkverbindung bricht ab
- Eingabe hat falsches Format
- Datensatz existiert bereits
- Speicherplatz ist voll
- Schnittstelle antwortet nicht
- Benutzer bricht Vorgang ab

Gute Software gibt verständliche Fehlermeldungen aus und geht kontrolliert mit Fehlern um.

---

## Testplanung

Tests sollten schon während der Planung vorbereitet werden.

Wichtige Fragen:

- Welche Anforderungen müssen getestet werden?
- Welche Eingaben sind gültig?
- Welche Eingaben sind ungültig?
- Welche Fehlerfälle müssen geprüft werden?
- Wer testet?
- Welche Testdaten werden genutzt?
- Wie wird das Ergebnis dokumentiert?
- Was gilt als bestanden?
- Was passiert bei Fehlern?

Tests sind einfacher, wenn Anforderungen klar und prüfbar formuliert wurden.

---

## Dokumentation planen

Dokumentation sollte nicht erst ganz am Ende entstehen.

Wichtige Dokumentation:

- README
- Anforderungen
- Installationsanleitung
- Benutzeranleitung
- technische Beschreibung
- Datenmodell
- Schnittstellenbeschreibung
- Testprotokoll
- Änderungsprotokoll
- Betriebsanleitung

Welche Dokumentation nötig ist, hängt vom Projekt ab.

Ein kleines Skript braucht vielleicht nur README und Kommentare. Eine produktive Anwendung braucht deutlich mehr Dokumentation.

---

## Betrieb planen

Software muss später betrieben werden.

Für den Betrieb sind wichtige Fragen:

- Wo läuft die Software?
- Wer installiert sie?
- Wer aktualisiert sie?
- Wer betreut Benutzer?
- Wo liegen Logs?
- Wie werden Fehler gemeldet?
- Wie werden Backups gemacht?
- Wer verwaltet Zugriffe?
- Wie wird Sicherheit geprüft?
- Wie wird die Software überwacht?
- Was passiert bei Ausfall?

Gerade für FISI ist dieser Punkt sehr wichtig.

Eine Software ist nicht fertig, wenn der Code läuft. Sie muss auch zuverlässig betrieben werden können.

---

## Wartung planen

Software verändert sich nach der ersten Version.

Typische Gründe:

- Fehler werden gefunden
- Anforderungen ändern sich
- Benutzer wünschen Verbesserungen
- Betriebssystem oder Abhängigkeiten ändern sich
- Sicherheitsupdates sind notwendig
- Datenbankstruktur muss angepasst werden
- Schnittstellen ändern sich
- Dokumentation muss aktualisiert werden

Deshalb sollte schon bei der Planung auf Wartbarkeit geachtet werden.

Wartbare Software ist verständlich, strukturiert, dokumentiert und testbar.

---

## Prioritäten und Umfang

In der Planung muss entschieden werden, was wirklich zur ersten Version gehört.

Eine erste Version muss nicht alles können.

Wichtig ist, zuerst die Kernfunktion sauber umzusetzen.

Beispiel Inventarverwaltung:

Erste Version:

- Geräte erfassen
- Geräte anzeigen
- Geräte bearbeiten
- Geräte suchen

Spätere Erweiterung:

- Exportfunktion
- Benutzerrollen
- automatische Berichte
- QR-Code-Etiketten
- Statistik-Dashboard

Diese Trennung verhindert, dass ein Projekt zu groß und unübersichtlich wird.

---

## MVP

MVP bedeutet **Minimum Viable Product**.

Damit ist eine erste nutzbare Version gemeint, die die wichtigste Kernfunktion erfüllt.

Ein MVP ist nicht perfekt, aber sinnvoll nutzbar.

Beispiel:

Für ein Ticketsystem wäre ein MVP:

- Ticket erstellen
- Ticket anzeigen
- Status ändern
- Ticket schließen

Nicht unbedingt nötig für die erste Version:

- Dashboard
- automatische SLA-Berichte
- komplexe Rechteverwaltung
- Design-Anpassungen
- E-Mail-Vorlagen

Ein MVP hilft, schnell ein nutzbares Ergebnis zu bekommen und danach gezielt zu verbessern.

---

## Risiken in der Planung

Schon bei der Planung sollten Risiken erkannt werden.

Mögliche Risiken:

| Risiko                  | Beispiel                                     |
| ----------------------- | -------------------------------------------- |
| technische Unsicherheit | Schnittstelle ist schlecht dokumentiert      |
| Zeitrisiko              | Aufwand wird unterschätzt                    |
| Datenrisiko             | Datenqualität ist schlecht                   |
| Sicherheitsrisiko       | sensible Daten werden verarbeitet            |
| Datenschutzrisiko       | personenbezogene Daten werden falsch genutzt |
| Betriebsrisiko          | Zielumgebung ist nicht vorbereitet           |
| Abhängigkeitsrisiko     | externe Bibliothek wird nicht gepflegt       |
| Kommunikationsrisiko    | Benutzeranforderungen sind unklar            |

Risiken sollten nicht ignoriert werden.

Besser ist, sie früh zu dokumentieren und Gegenmaßnahmen zu überlegen.

---

## Änderungsanforderungen

Während eines Projekts können neue Anforderungen entstehen.

Das ist normal, muss aber kontrolliert werden.

Wichtige Fragen bei Änderungen:

- Was soll geändert werden?
- Warum ist die Änderung nötig?
- Welche Auswirkungen hat sie?
- Betrifft sie Zeit, Kosten oder Sicherheit?
- Muss die Datenstruktur angepasst werden?
- Müssen Tests geändert werden?
- Muss Dokumentation angepasst werden?
- Ist die Änderung für die erste Version notwendig?

Ohne Kontrolle können Projekte durch immer neue Anforderungen unübersichtlich werden.

---

## Abnahmekriterien

Abnahmekriterien beschreiben, wann das Ergebnis akzeptiert wird.

Beispiele:

- alle Muss-Anforderungen sind erfüllt
- Kernfunktionen wurden getestet
- keine kritischen Fehler sind offen
- Dokumentation ist vorhanden
- Installation wurde beschrieben
- Benutzer kann Hauptaufgabe durchführen
- Sicherheitsanforderungen sind umgesetzt
- Daten werden korrekt gespeichert
- Backup oder Export ist möglich, wenn gefordert

Abnahmekriterien müssen vor der Abnahme bekannt sein.

Sonst ist unklar, wann das Projekt fertig ist.

---

## Praxisbeispiele

### Beispiel 1: Inventarverwaltung

Für eine Inventarverwaltung werden Anforderungen gesammelt. Geräte sollen mit Inventarnummer, Hostname, Typ, Standort und Status gespeichert werden. Benutzer sollen Geräte suchen und bearbeiten können. Admins dürfen Geräte löschen. Die erste Version konzentriert sich auf Erfassung, Suche und Bearbeitung.

### Beispiel 2: Logfile-Auswertung

Ein Python-Skript soll Logdateien nach Fehlermeldungen durchsuchen. Anforderungen sind: Datei einlesen, Suchwort angeben, Treffer zählen, Treffer ausgeben und Fehler anzeigen, wenn die Datei nicht existiert. Geplant werden Eingabe, Verarbeitung, Ausgabe, Fehlerbehandlung und README.

### Beispiel 3: Supportticket-System

Ein Ticketsystem soll Supportfälle erfassen. Anforderungen sind Ticketnummer, Titel, Beschreibung, Priorität, Status und Bearbeiter. Zusätzlich müssen Benutzerrollen, Datenschutz, Suchfunktion, Benachrichtigung und Testfälle geplant werden.

---

## Typische Fehler

| Fehler                               | Problem                                      |
| ------------------------------------ | -------------------------------------------- |
| Anforderungen zu ungenau formulieren | Umsetzung und Test werden schwierig          |
| Benutzer nicht einbeziehen           | Software passt nicht zum Arbeitsalltag       |
| nur Funktionen betrachten            | Sicherheit, Bedienbarkeit und Betrieb fehlen |
| Datenmodell nicht planen             | spätere Änderungen werden schwer             |
| Fehlerfälle ignorieren               | Software reagiert schlecht auf Probleme      |
| Datenschutz zu spät prüfen           | rechtliche und technische Risiken entstehen  |
| keine Prioritäten setzen             | Projekt wird zu groß                         |
| Abnahmekriterien fehlen              | Fertigstellung ist unklar                    |
| Dokumentation erst am Ende anfangen  | wichtige Entscheidungen gehen verloren       |
| Betrieb nicht mitdenken              | Software läuft später nicht zuverlässig      |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Anforderungsspezifikation und Softwareplanung wichtig, weil Software immer in eine technische Umgebung eingebunden wird.

Ein FISI muss verstehen, welche Anforderungen Auswirkungen auf Infrastruktur, Datenbanken, Rechte, Sicherheit, Netzwerk, Backup und Betrieb haben.

In der Praxis bedeutet das:

- Anforderungen technisch einordnen
- Benutzerrollen und Rechte verstehen
- Datenanforderungen erkennen
- Schnittstellen berücksichtigen
- Sicherheits- und Datenschutzanforderungen beachten
- Test- und Produktivumgebung unterscheiden
- Betrieb und Wartung planen
- Dokumentation erstellen
- Abnahmekriterien prüfen
- kleine Softwarelösungen strukturiert vorbereiten

Ein guter FISI denkt bei Softwareplanung nicht nur an Funktionen, sondern auch an Daten, Sicherheit, Betrieb, Wartung und Nachvollziehbarkeit.

---

## Kurze Zusammenfassung

Eine Anforderungsspezifikation beschreibt, was eine Software leisten soll und welche Eigenschaften sie haben muss.

Wichtige Bestandteile sind funktionale Anforderungen, nicht-funktionale Anforderungen, Benutzerrollen, Use Cases, User Stories, Akzeptanzkriterien, Datenanforderungen, Schnittstellen, Sicherheit, Datenschutz und technische Rahmenbedingungen.

Softwareplanung beschreibt, wie diese Anforderungen umgesetzt werden.

Dazu gehören Projektstruktur, Programmstruktur, Datenmodell, Ablaufplanung, Fehlerfälle, Tests, Dokumentation, Betrieb, Wartung, Priorisierung und Abnahmekriterien.

Für FISI ist dieses Kapitel wichtig, weil Softwarelösungen nur dann zuverlässig betrieben werden können, wenn Anforderungen und Planung sauber geklärt sind.
