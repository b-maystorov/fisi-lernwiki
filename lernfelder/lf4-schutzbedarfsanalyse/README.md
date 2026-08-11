# LF4: Schutzbedarfsanalyse im eigenen Arbeitsbereich durchführen

In diesem Lernfeld geht es darum, IT-Systeme, Daten und Arbeitsbereiche nach ihrem Schutzbedarf zu bewerten.

Nicht jedes System ist gleich kritisch. Ein öffentliches Testsystem hat einen anderen Schutzbedarf als ein Dateiserver mit Kundendaten, ein Backup-System oder ein Benutzerkonto mit Administratorrechten. Deshalb muss in der IT geprüft werden, welche Informationen, Systeme und Prozesse besonders geschützt werden müssen.

Für Fachinformatiker für Systemintegration ist LF4 wichtig, weil Sicherheit nicht nur aus technischen Maßnahmen besteht. Man muss Risiken erkennen, Schutzbedarf bewerten, passende Maßnahmen auswählen und diese sauber dokumentieren.

---

## Ziel von LF4

Das Ziel von LF4 ist, den Schutzbedarf von Informationen, Systemen und Arbeitsbereichen einzuschätzen.

Dabei geht es um Fragen wie:

- Welche Daten werden verarbeitet?
- Welche Systeme sind besonders wichtig?
- Was passiert bei Datenverlust?
- Was passiert bei unbefugtem Zugriff?
- Was passiert bei Manipulation?
- Was passiert bei Ausfall?
- Welche Schutzmaßnahmen sind notwendig?
- Wer ist verantwortlich?
- Wie wird Sicherheit dokumentiert?

Eine Schutzbedarfsanalyse hilft dabei, Sicherheitsmaßnahmen sinnvoll zu planen. Nicht jedes System braucht die gleiche Schutzstufe, aber kritische Systeme dürfen nicht unterschätzt werden.

---

## Kapitelübersicht

| Kapitel                                                 | Thema                                        |
| ------------------------------------------------------- | -------------------------------------------- |
| [4.1](./04-01-grundlagen-informationssicherheit.md)     | Grundlagen der Informationssicherheit        |
| [4.2](./04-02-technisch-organisatorische-massnahmen.md) | Technisch-organisatorische Maßnahmen         |
| [4.3](./04-03-schutzbedarf-feststellen.md)              | Schutzbedarf feststellen und bewerten        |
| [4.4](./04-04-schutzbedarf-arbeitsbereiche.md)          | Schutzbedarf in Arbeitsbereichen analysieren |

---

## Warum LF4 wichtig ist

IT-Sicherheit betrifft fast alle Bereiche eines Unternehmens.

Daten, Systeme und Netzwerke müssen geschützt werden vor:

- unbefugtem Zugriff
- Datenverlust
- Manipulation
- Schadsoftware
- Ausfall
- Fehlbedienung
- Diebstahl
- technischen Defekten
- Naturereignissen
- organisatorischen Fehlern

Ein Unternehmen kann nur sicher arbeiten, wenn bekannt ist, welche Systeme und Daten besonders wichtig sind.

Ohne Schutzbedarfsanalyse werden Sicherheitsmaßnahmen oft falsch gesetzt. Manche wichtigen Systeme sind dann zu wenig geschützt, während unwichtige Bereiche unnötig viel Aufwand bekommen.

---

## Grundidee der Schutzbedarfsanalyse

Bei einer Schutzbedarfsanalyse wird bewertet, wie schlimm ein Schaden für ein Unternehmen wäre.

Dabei werden meistens die drei Schutzziele betrachtet:

| Schutzziel      | Bedeutung                                                         |
| --------------- | ----------------------------------------------------------------- |
| Vertraulichkeit | Informationen dürfen nur von berechtigten Personen gelesen werden |
| Integrität      | Informationen müssen korrekt und unverändert bleiben              |
| Verfügbarkeit   | Systeme und Daten müssen nutzbar sein, wenn sie gebraucht werden  |

Für jedes System oder jede Information wird geprüft, wie hoch der Schutzbedarf bei diesen Schutzzielen ist.

Ein System kann zum Beispiel bei Vertraulichkeit sehr kritisch sein, aber bei Verfügbarkeit weniger kritisch. Ein anderes System kann besonders bei Verfügbarkeit wichtig sein, zum Beispiel ein zentraler Server für den täglichen Betrieb.

---

## Typische Schutzbedarfskategorien

Der Schutzbedarf kann in Stufen eingeteilt werden.

| Schutzbedarf | Bedeutung                                                              |
| ------------ | ---------------------------------------------------------------------- |
| normal       | ein Schaden wäre begrenzt und beherrschbar                             |
| hoch         | ein Schaden hätte deutliche Auswirkungen                               |
| sehr hoch    | ein Schaden könnte existenzbedrohend oder rechtlich sehr kritisch sein |

Diese Einteilung hilft, passende Maßnahmen auszuwählen.

Je höher der Schutzbedarf, desto stärker müssen Schutzmaßnahmen, Kontrolle, Dokumentation und Wiederherstellung geplant werden.

---

## Beispiele für schützenswerte Bereiche

In Unternehmen können viele Bereiche schutzbedürftig sein.

Beispiele:

- Benutzerkonten
- Administratorzugänge
- Kundendaten
- Personaldaten
- Finanzdaten
- E-Mail-Systeme
- Dateiablagen
- Datenbanken
- Backup-Systeme
- Netzwerkkomponenten
- Server
- Clients
- mobile Geräte
- Cloud-Dienste
- WLAN und VPN
- Dokumentationen
- Zugangsdaten

Auch Dokumentationen können kritisch sein, weil sie Informationen über Netzwerkstruktur, IP-Adressen, Benutzer, Systeme oder Sicherheitsmaßnahmen enthalten können.

---

## Typische Aufgaben in LF4

Typische Aufgaben in diesem Lernfeld sind:

- Schutzziele erklären
- Bedrohungen erkennen
- Risiken einschätzen
- Schutzbedarf bewerten
- technische Maßnahmen auswählen
- organisatorische Maßnahmen beschreiben
- Arbeitsbereiche analysieren
- Datenschutz beachten
- Sicherheitskonzepte verstehen
- Maßnahmen dokumentieren
- Ergebnisse präsentieren

LF4 verbindet technisches Wissen mit organisatorischem Denken.

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Schutzbedarfsanalyse wichtig, weil viele technische Entscheidungen davon abhängen.

Beispiele:

- Muss ein Server besonders abgesichert werden?
- Braucht ein Laptop Festplattenverschlüsselung?
- Müssen Backups häufiger erstellt werden?
- Braucht ein System hohe Verfügbarkeit?
- Darf ein Benutzer lokale Administratorrechte haben?
- Muss ein Netzwerkbereich getrennt werden?
- Welche Firewall-Regeln sind notwendig?
- Wie kritisch ist ein Ausfall?
- Welche Daten dürfen in die Cloud?
- Wie wird ein Notfall vorbereitet?

Ein FISI muss nicht nur Systeme installieren, sondern auch verstehen, welche Risiken entstehen und welche Schutzmaßnahmen sinnvoll sind.

---

## Kurze Zusammenfassung

LF4 behandelt die Bewertung des Schutzbedarfs von Daten, Systemen und Arbeitsbereichen.

Wichtige Grundlagen sind Vertraulichkeit, Integrität und Verfügbarkeit.

Eine Schutzbedarfsanalyse hilft dabei, Risiken zu erkennen und passende technische sowie organisatorische Maßnahmen zu planen.

Für FISI ist dieses Lernfeld wichtig, weil IT-Systeme nicht nur funktionieren müssen, sondern auch sicher, verfügbar, nachvollziehbar und rechtlich sauber betrieben werden sollen.
