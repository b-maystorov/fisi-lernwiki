# 5.4 Prozess der Softwareentwicklung analysieren

In diesem Kapitel geht es darum, den Prozess der Softwareentwicklung zu verstehen und zu analysieren.

Softwareentwicklung ist ein Ablauf mit mehreren Schritten. Eine Software entsteht nicht nur durch Code, sondern durch Analyse, Planung, Umsetzung, Test, Dokumentation, Bereitstellung und Wartung. Wenn dieser Prozess nicht verstanden wird, entstehen schnell unklare Anforderungen, Fehler, Sicherheitsprobleme oder schwer wartbare Lösungen.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Software im Betrieb zuverlässig funktionieren muss. Auch wenn FISI nicht immer selbst große Anwendungen entwickeln, müssen sie Softwareprozesse verstehen, mit Entwicklern zusammenarbeiten, Anforderungen einordnen und den Betrieb vorbereiten.

---

## Kurz erklärt

Der Softwareentwicklungsprozess beschreibt den Weg von einer Idee bis zu einer nutzbaren Software.

Typische Schritte sind:

- Problem erkennen
- Anforderungen erfassen
- Lösung planen
- Daten und Abläufe modellieren
- Software entwickeln
- Software testen
- Fehler beheben
- Software dokumentieren
- Software bereitstellen
- Software betreiben
- Software warten und verbessern

Der Prozess hilft, Software nicht zufällig zu bauen, sondern nachvollziehbar und kontrolliert zu entwickeln.

---

## Warum ein Prozess wichtig ist

Ein klarer Entwicklungsprozess verhindert viele typische Probleme.

Ohne Prozess können entstehen:

- unklare Ziele
- unvollständige Anforderungen
- schlecht strukturierter Code
- fehlende Tests
- fehlende Dokumentation
- Sicherheitslücken
- falsche Datenstrukturen
- Probleme beim Betrieb
- schwierige Wartung
- unzufriedene Benutzer

Ein Prozess macht Softwareentwicklung planbarer.

Er sorgt dafür, dass nicht nur die Programmierung betrachtet wird, sondern auch Analyse, Qualität, Sicherheit, Betrieb und spätere Änderungen.

---

## Softwareentwicklung als Lebenszyklus

Software hat einen Lebenszyklus.

Sie wird geplant, erstellt, genutzt, geändert und irgendwann ersetzt oder abgeschaltet.

Typischer Lebenszyklus:

1. Idee oder Bedarf entsteht
2. Anforderungen werden gesammelt
3. Lösung wird geplant
4. Software wird entwickelt
5. Software wird getestet
6. Software wird eingeführt
7. Software wird betrieben
8. Software wird gewartet
9. Software wird erweitert
10. Software wird abgelöst oder gelöscht

Software ist also nicht einfach fertig, sobald die erste Version läuft.

Der Betrieb und die Wartung sind oft länger und aufwendiger als die erste Entwicklung.

---

## Phasen der Softwareentwicklung

Ein Softwareentwicklungsprozess kann in Phasen eingeteilt werden.

| Phase           | Aufgabe                                             |
| --------------- | --------------------------------------------------- |
| Analyse         | Problem, Ziel und Anforderungen verstehen           |
| Planung         | Lösung, Architektur, Daten und Aufgaben vorbereiten |
| Entwurf         | Struktur der Software und Datenmodelle festlegen    |
| Implementierung | Code schreiben und konfigurieren                    |
| Test            | Software prüfen und Fehler finden                   |
| Bereitstellung  | Software in Zielumgebung bringen                    |
| Betrieb         | Software nutzen, überwachen und unterstützen        |
| Wartung         | Fehler beheben und Verbesserungen einbauen          |
| Dokumentation   | Wissen und Entscheidungen festhalten                |

Diese Phasen können nacheinander oder mehrfach wiederholt ablaufen.

---

## Analysephase

In der Analysephase wird geklärt, welches Problem gelöst werden soll.

Wichtige Fragen:

- Was ist das aktuelle Problem?
- Wer ist betroffen?
- Wer nutzt die Software später?
- Welche Ziele gibt es?
- Welche Daten werden verarbeitet?
- Welche Systeme sind beteiligt?
- Welche Anforderungen gibt es?
- Welche Einschränkungen bestehen?
- Welche Risiken sind bekannt?

Die Analysephase ist wichtig, weil falsches Verständnis am Anfang später zu falscher Software führt.

Wenn das Problem nicht verstanden wurde, hilft auch sauberer Code nicht.

---

## Anforderungsanalyse

Die Anforderungsanalyse sammelt und beschreibt, was die Software leisten soll.

Anforderungen können kommen von:

- Kunden
- Benutzern
- Fachabteilungen
- IT-Abteilung
- Datenschutz
- Informationssicherheit
- Geschäftsführung
- gesetzlichen Vorgaben
- bestehenden Systemen

Man unterscheidet funktionale und nicht-funktionale Anforderungen.

| Art                             | Bedeutung                                     |
| ------------------------------- | --------------------------------------------- |
| funktionale Anforderungen       | Funktionen der Software                       |
| nicht-funktionale Anforderungen | Qualität, Sicherheit, Leistung, Bedienbarkeit |

Eine gute Anforderungsanalyse ist die Grundlage für Planung, Umsetzung und Tests.

---

## Funktionale Anforderungen

Funktionale Anforderungen beschreiben, was eine Software tun soll.

Beispiele:

- Benutzer kann sich anmelden
- Daten können gespeichert werden
- Datensätze können gesucht werden
- Berichte können exportiert werden
- Admin kann Benutzer verwalten
- System sendet Benachrichtigungen
- Datei kann hochgeladen werden
- Ticket kann geschlossen werden

Funktionale Anforderungen sind später oft direkt testbar.

Beispiel:

Wenn die Anforderung lautet „Benutzer kann Tickets nach Status filtern“, kann im Test geprüft werden, ob diese Funktion vorhanden ist.

---

## Nicht-funktionale Anforderungen

Nicht-funktionale Anforderungen beschreiben Eigenschaften der Software.

Beispiele:

- Anwendung soll schnell reagieren
- Daten müssen verschlüsselt übertragen werden
- Software soll einfach bedienbar sein
- System soll 100 Benutzer gleichzeitig unterstützen
- Anwendung soll unter Linux laufen
- Software soll gut dokumentiert sein
- Backup muss möglich sein
- System soll wartbar sein
- Anmeldung soll über MFA geschützt sein

Nicht-funktionale Anforderungen werden oft unterschätzt, sind aber sehr wichtig.

Eine Software kann alle Funktionen haben und trotzdem schlecht sein, wenn sie langsam, unsicher oder schwer bedienbar ist.

---

## Planungsphase

In der Planungsphase wird festgelegt, wie die Lösung umgesetzt werden soll.

Wichtige Punkte:

- technische Lösung auswählen
- Programmiersprache wählen
- Datenhaltung planen
- Schnittstellen bestimmen
- Aufgaben verteilen
- Zeitplan erstellen
- Werkzeuge festlegen
- Sicherheitsmaßnahmen planen
- Teststrategie überlegen
- Dokumentation vorbereiten
- Betrieb mitdenken

Planung bedeutet nicht, jedes Detail perfekt vorherzusagen.

Planung bedeutet, bewusst Entscheidungen zu treffen und Risiken früh zu erkennen.

---

## Entwurfsphase

In der Entwurfsphase wird die Struktur der Software geplant.

Dabei können Modelle und Diagramme helfen.

Beispiele:

- Datenmodell
- Entity-Relationship-Modell
- UML-Klassendiagramm
- Use-Case-Diagramm
- Ablaufdiagramm
- Programmstruktur
- Schnittstellenbeschreibung
- Architekturübersicht

Der Entwurf hilft, vor dem Programmieren über Struktur und Zusammenhänge nachzudenken.

Das reduziert spätere Fehler und macht die Software wartbarer.

---

## Datenmodellierung

Viele Anwendungen verarbeiten Daten.

Deshalb muss überlegt werden, wie Daten gespeichert und miteinander verbunden werden.

Wichtige Fragen:

- Welche Datenobjekte gibt es?
- Welche Attribute haben sie?
- Welche Beziehungen bestehen?
- Welche Daten müssen eindeutig sein?
- Welche Daten dürfen nicht leer sein?
- Welche Regeln gelten?
- Welche Daten werden häufig gesucht?
- Welche Daten müssen geschützt werden?

Ein gutes Datenmodell verhindert viele spätere Probleme.

Wenn Daten schlecht strukturiert sind, wird die Anwendung oft schwer erweiterbar.

---

## Implementierungsphase

In der Implementierungsphase wird die Software tatsächlich gebaut.

Dazu gehören:

- Code schreiben
- Datenbanktabellen erstellen
- Funktionen entwickeln
- Benutzeroberfläche erstellen
- Schnittstellen anbinden
- Konfiguration schreiben
- Fehlerbehandlung einbauen
- Logs einbauen
- Sicherheitsfunktionen umsetzen
- Versionierung nutzen

Implementierung sollte nicht unkontrolliert passieren.

Code sollte verständlich, testbar und wartbar geschrieben werden.

---

## Codequalität

Codequalität beschreibt, wie gut Code verständlich, wartbar und zuverlässig ist.

Wichtige Merkmale:

| Merkmal       | Bedeutung                            |
| ------------- | ------------------------------------ |
| Lesbarkeit    | Code ist verständlich geschrieben    |
| Struktur      | Code ist sinnvoll aufgeteilt         |
| Wartbarkeit   | Änderungen sind möglich              |
| Testbarkeit   | Funktionen können geprüft werden     |
| Einfachheit   | unnötige Komplexität wird vermieden  |
| Sicherheit    | Eingaben und Zugriffe werden geprüft |
| Dokumentation | wichtige Entscheidungen sind erklärt |

Guter Code ist nicht nur Code, der funktioniert.

Guter Code kann auch später verstanden, geändert und geprüft werden.

---

## Testphase

In der Testphase wird geprüft, ob die Software korrekt funktioniert.

Tests sollen Fehler finden, bevor Benutzer betroffen sind.

Testarten:

| Testart          | Bedeutung                                             |
| ---------------- | ----------------------------------------------------- |
| Unit-Test        | einzelne Funktion wird getestet                       |
| Integrationstest | Zusammenspiel mehrerer Teile wird geprüft             |
| Systemtest       | gesamte Anwendung wird getestet                       |
| Abnahmetest      | Kunde oder Benutzer prüft das Ergebnis                |
| Regressionstest  | alte Funktionen werden nach Änderungen erneut geprüft |
| Sicherheitstest  | mögliche Sicherheitsprobleme werden geprüft           |

Tests sind ein wichtiger Teil des Entwicklungsprozesses.

Eine Software ohne Tests ist schwer zuverlässig zu betreiben.

---

## Fehlerbehebung

Wenn Tests Fehler zeigen, müssen diese analysiert und behoben werden.

Wichtig ist:

- Fehler genau beschreiben
- Ursache verstehen
- Änderung durchführen
- Änderung testen
- prüfen, ob neue Fehler entstanden sind
- Fehlerlösung dokumentieren

Ein Fehler sollte nicht nur oberflächlich verschwinden.

Man sollte verstehen, warum er entstanden ist.

---

## Debugging

Debugging bedeutet Fehlersuche im Code oder System.

Dabei wird untersucht:

- wo ein Fehler entsteht
- welche Eingaben betroffen sind
- welche Variable falsche Werte hat
- welche Funktion nicht korrekt arbeitet
- welche Fehlermeldung erscheint
- welche Abhängigkeit fehlt
- welche Konfiguration falsch ist

Debugging ist ein normaler Teil der Softwareentwicklung.

Auch erfahrene Entwickler schreiben nicht sofort perfekten Code.

---

## Bereitstellung

Bereitstellung bedeutet, die Software in eine nutzbare Umgebung zu bringen.

Das kann bedeuten:

- Anwendung installieren
- Server vorbereiten
- Datenbank einrichten
- Konfiguration setzen
- Benutzerrechte einrichten
- Dienste starten
- Firewall-Regeln prüfen
- Zertifikate einrichten
- Monitoring aktivieren
- Backup einplanen
- Benutzer informieren

Bereitstellung ist besonders wichtig für FISI, weil hier Softwareentwicklung und Systembetrieb zusammenkommen.

---

## Deployment

Deployment bedeutet das Ausliefern oder Veröffentlichen einer Softwareversion.

Beispiele:

- neue Version auf Server kopieren
- Docker-Container aktualisieren
- Webanwendung ausrollen
- Skript auf Zielsystem bereitstellen
- Paket installieren
- Datenbankmigration ausführen
- Konfiguration aktualisieren

Deployment sollte kontrolliert erfolgen.

Unkontrollierte Änderungen direkt auf Produktivsystemen können Ausfälle verursachen.

---

## Entwicklungs-, Test- und Produktivumgebung

Software wird oft in getrennten Umgebungen betrieben.

| Umgebung    | Zweck                                    |
| ----------- | ---------------------------------------- |
| Entwicklung | Code wird geschrieben und ausprobiert    |
| Test        | Funktionen werden geprüft                |
| Produktion  | echte Benutzer arbeiten mit echten Daten |

Diese Trennung reduziert Risiken.

Neue Funktionen sollten nicht direkt in der Produktivumgebung getestet werden.

Besonders bei echten Daten und Benutzern ist eine klare Trennung wichtig.

---

## Betrieb

Nach der Bereitstellung beginnt der Betrieb.

Betrieb bedeutet:

- Software überwachen
- Benutzer unterstützen
- Updates einspielen
- Logs prüfen
- Backups kontrollieren
- Fehler beheben
- Sicherheit prüfen
- Performance beobachten
- Dokumentation aktualisieren

Softwarebetrieb ist ein typisches FISI-Thema.

Eine Anwendung muss nicht nur entwickelt werden, sondern auch zuverlässig laufen.

---

## Wartung

Wartung bedeutet, Software nach der Einführung zu pflegen.

Arten von Wartung:

| Wartungsart        | Bedeutung                     |
| ------------------ | ----------------------------- |
| korrektive Wartung | Fehler beheben                |
| adaptive Wartung   | Anpassung an neue Umgebung    |
| perfektive Wartung | Verbesserung oder Erweiterung |
| präventive Wartung | Probleme vorbeugen            |

Software verändert sich mit der Zeit.

Betriebssysteme, Sicherheitsanforderungen, Benutzerwünsche und Schnittstellen ändern sich. Deshalb muss Software wartbar bleiben.

---

## Dokumentation im Prozess

Dokumentation begleitet den gesamten Entwicklungsprozess.

Wichtige Dokumente:

- Anforderungsdokumentation
- Entwurf
- Datenmodell
- Installationsanleitung
- Benutzeranleitung
- Betriebsdokumentation
- Testprotokolle
- Änderungsprotokoll
- Fehlerdokumentation
- Schnittstellenbeschreibung
- README
- Sicherheitskonzept

Dokumentation sollte nicht erst am Ende geschrieben werden.

Wenn Entscheidungen während des Projekts nicht dokumentiert werden, sind sie später schwer nachvollziehbar.

---

## Qualitätssicherung

Qualitätssicherung umfasst Maßnahmen, die Softwarequalität verbessern.

Dazu gehören:

- Anforderungen prüfen
- Code Reviews
- Tests
- Dokumentation
- Versionsverwaltung
- Sicherheitsprüfung
- Benutzerfeedback
- Standards
- automatisierte Prüfungen
- saubere Projektstruktur

Qualitätssicherung ist nicht nur Fehlersuche.

Sie sorgt dafür, dass Software verständlich, sicher, wartbar und passend zum Zweck bleibt.

---

## Code Review

Bei einem Code Review prüft eine andere Person den Code.

Geprüft werden kann:

- Verständlichkeit
- Logik
- Fehler
- Sicherheit
- Stil
- Tests
- Dokumentation
- Wartbarkeit

Code Reviews helfen nicht nur, Fehler zu finden.

Sie verbessern auch Wissen im Team, weil mehrere Personen den Code verstehen.

---

## Versionsverwaltung im Prozess

Versionsverwaltung gehört zum Entwicklungsprozess.

Git hilft dabei:

- Änderungen zu speichern
- Zwischenstände zu sichern
- Branches zu nutzen
- Fehler zurückzuverfolgen
- im Team zu arbeiten
- Releases zu markieren
- Änderungen zu dokumentieren

Jeder wichtige Projektstand sollte nachvollziehbar sein.

Das ist besonders wichtig, wenn später Fehler auftreten oder ältere Versionen benötigt werden.

---

## Automatisierung im Entwicklungsprozess

Viele Schritte können automatisiert werden.

Beispiele:

- Tests automatisch ausführen
- Code prüfen
- Anwendung bauen
- Container erstellen
- Paket veröffentlichen
- Deployment vorbereiten
- Dokumentation generieren
- Sicherheitsprüfungen starten

Automatisierung reduziert manuelle Fehler und spart Zeit.

In größeren Projekten wird dafür oft CI/CD genutzt.

---

## CI/CD

CI/CD steht für Continuous Integration und Continuous Delivery oder Continuous Deployment.

Die Grundidee:

- Codeänderungen werden regelmäßig integriert
- Tests laufen automatisch
- Fehler werden früh erkannt
- Software kann kontrolliert ausgeliefert werden

Beispiele für CI/CD-Werkzeuge:

- GitHub Actions
- GitLab CI
- Jenkins
- Azure DevOps

Für FISI ist CI/CD wichtig, weil moderne Software häufig automatisiert gebaut, getestet und bereitgestellt wird.

---

## Sicherheit im Entwicklungsprozess

Sicherheit sollte während des gesamten Prozesses berücksichtigt werden.

Wichtige Maßnahmen:

- Anforderungen an Sicherheit definieren
- Eingaben validieren
- Passwörter nicht im Code speichern
- sichere Authentifizierung nutzen
- Rechtekonzept planen
- Verschlüsselung nutzen
- Abhängigkeiten prüfen
- Sicherheitsupdates beachten
- Logs sicher behandeln
- Datenschutz prüfen
- Testdaten anonymisieren
- Code Reviews durchführen

Sicherheit am Ende nachzurüsten ist oft schwerer und teurer.

---

## Datenschutz im Entwicklungsprozess

Wenn personenbezogene Daten verarbeitet werden, muss Datenschutz früh beachtet werden.

Wichtige Fragen:

- Welche Daten werden gespeichert?
- Warum werden sie gespeichert?
- Wer darf darauf zugreifen?
- Wie lange werden sie gespeichert?
- Wie werden sie gelöscht?
- Werden echte Daten in Tests genutzt?
- Werden Daten verschlüsselt?
- Werden Daten in Logs geschrieben?
- Gibt es Exportfunktionen?
- Gibt es Cloud-Dienste?

Für öffentliche Lernprojekte oder GitHub-Repositories sollten keine echten personenbezogenen Daten genutzt werden.

Besser sind künstliche Testdaten.

---

## Änderungsmanagement

Änderungsmanagement beschreibt, wie Änderungen kontrolliert durchgeführt werden.

Wichtige Fragen:

- Was wird geändert?
- Warum wird es geändert?
- Welche Systeme sind betroffen?
- Welche Risiken gibt es?
- Wer muss zustimmen?
- Gibt es ein Backup?
- Gibt es einen Rückfallplan?
- Wurde getestet?
- Wurde dokumentiert?

Gerade in Produktivumgebungen sind kontrollierte Änderungen sehr wichtig.

Eine kleine Änderung kann große Auswirkungen haben.

---

## Abnahme

Abnahme bedeutet, dass das Ergebnis geprüft und akzeptiert wird.

Dabei wird kontrolliert:

- erfüllt die Software die Anforderungen?
- funktioniert sie im gewünschten Umfeld?
- wurden Tests durchgeführt?
- ist Dokumentation vorhanden?
- sind bekannte Fehler akzeptiert oder behoben?
- sind Benutzer informiert?
- ist der Betrieb vorbereitet?

Eine Abnahme macht das Projektergebnis offiziell.

Sie zeigt, dass das vereinbarte Ziel erreicht wurde oder welche offenen Punkte noch bestehen.

---

## Prozessanalyse

Einen Softwareentwicklungsprozess zu analysieren bedeutet, zu prüfen, wie gut der Ablauf funktioniert.

Wichtige Fragen:

- Sind Anforderungen klar?
- Werden Änderungen dokumentiert?
- Gibt es Tests?
- Gibt es Versionsverwaltung?
- Gibt es Code Reviews?
- Ist Dokumentation aktuell?
- Werden Sicherheitsaspekte beachtet?
- Funktioniert die Kommunikation?
- Sind Rollen klar?
- Werden Fehler systematisch bearbeitet?
- Ist der Betrieb vorbereitet?
- Gibt es Verbesserungsmöglichkeiten?

Prozessanalyse hilft, Softwareentwicklung zu verbessern.

---

## Typische Kennzahlen

In Softwareprojekten können Kennzahlen helfen.

Beispiele:

| Kennzahl                | Bedeutung                                     |
| ----------------------- | --------------------------------------------- |
| Anzahl offener Fehler   | zeigt Qualitätsprobleme oder Arbeitslast      |
| Testabdeckung           | zeigt, wie viel Code durch Tests geprüft wird |
| Durchlaufzeit           | Zeit von Aufgabe bis Fertigstellung           |
| Anzahl Änderungen       | zeigt Aktivität und Änderungsdruck            |
| Fehlerrate nach Release | zeigt Qualität vor Auslieferung               |
| Verfügbarkeit           | wichtig für Betrieb                           |
| Wiederherstellungszeit  | wichtig für Notfälle                          |
| Benutzerfeedback        | zeigt praktische Nutzbarkeit                  |

Kennzahlen müssen sinnvoll interpretiert werden.

Eine Zahl allein erklärt nicht immer die Ursache.

---

## Kontinuierliche Verbesserung

Softwareprozesse sollten regelmäßig verbessert werden.

Mögliche Verbesserungen:

- Anforderungen genauer erfassen
- bessere Tests schreiben
- Dokumentation früher beginnen
- Code Reviews einführen
- Deployment automatisieren
- Sicherheitsprüfungen ergänzen
- Fehler besser dokumentieren
- Benutzerfeedback einholen
- Projektstruktur verbessern
- Betrieb früher einbeziehen

Verbesserung bedeutet nicht, alles auf einmal zu ändern.

Kleine, regelmäßige Verbesserungen sind oft realistischer.

---

## Praxisbeispiele

### Beispiel 1: Python-Skript wird erweitert

Ein Python-Skript zur Logauswertung funktioniert lokal. Später soll es auf einem Server regelmäßig laufen. Dadurch werden neue Prozessschritte wichtig: Konfiguration, Logging, Fehlerbehandlung, Bereitstellung, Cronjob, Dokumentation und Monitoring.

### Beispiel 2: Datenbankanwendung

Eine kleine Anwendung speichert Inventardaten. Vor der Umsetzung werden Datenfelder, Tabellen, Benutzerrechte und Backupbedarf geplant. Danach wird die Anwendung getestet und dokumentiert.

### Beispiel 3: Fehler nach Update

Nach einem Update funktioniert eine Anwendung nicht mehr. Durch Versionsverwaltung, Logs, Testumgebung und Änderungsdokumentation kann die Ursache schneller gefunden und die alte Version bei Bedarf wiederhergestellt werden.

---

## Typische Fehler

| Fehler                                            | Problem                                    |
| ------------------------------------------------- | ------------------------------------------ |
| Anforderungen nicht sauber erfassen               | Software löst das falsche Problem          |
| Tests erst am Ende durchführen                    | Fehler werden spät entdeckt                |
| keine Trennung von Test und Produktion            | echte Benutzer oder Daten werden gefährdet |
| Dokumentation vergessen                           | Betrieb und Wartung werden schwierig       |
| Sicherheit erst nachträglich beachten             | Risiken entstehen im Design                |
| keine Versionsverwaltung nutzen                   | Änderungen sind nicht nachvollziehbar      |
| Deployment manuell und unkontrolliert durchführen | Ausfallrisiko steigt                       |
| keine Abnahme durchführen                         | Ergebnis bleibt unklar                     |
| Betrieb nicht einplanen                           | Software läuft später nicht zuverlässig    |
| keine Prozessverbesserung durchführen             | gleiche Fehler wiederholen sich            |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist der Softwareentwicklungsprozess wichtig, weil Software später in einer IT-Umgebung betrieben wird.

Ein FISI muss verstehen, wie Software entsteht und welche Anforderungen für den Betrieb wichtig sind.

In der Praxis bedeutet das:

- Anforderungen technisch einordnen
- Test- und Produktivumgebung unterscheiden
- Deployment verstehen
- Logs und Fehler analysieren
- Backups und Wiederherstellung planen
- Benutzerrechte und Sicherheit beachten
- Dokumentation prüfen
- mit Entwicklern zusammenarbeiten
- Betrieb und Monitoring vorbereiten
- Änderungen kontrolliert durchführen

Ein guter FISI sieht Software nicht nur als Programmcode, sondern als Teil eines gesamten Betriebsprozesses aus Infrastruktur, Daten, Benutzern, Sicherheit, Updates und Wartung.

---

## Kurze Zusammenfassung

Der Softwareentwicklungsprozess beschreibt den Weg von der Idee bis zum Betrieb und zur Wartung einer Software.

Wichtige Phasen sind Analyse, Anforderungsanalyse, Planung, Entwurf, Implementierung, Test, Bereitstellung, Betrieb, Wartung und Dokumentation.

Qualität, Sicherheit, Datenschutz, Versionsverwaltung, Tests, Deployment und kontinuierliche Verbesserung gehören zum Prozess dazu.

Für FISI ist dieses Kapitel wichtig, weil Software nicht isoliert existiert, sondern zuverlässig in IT-Infrastrukturen betrieben und gewartet werden muss.
