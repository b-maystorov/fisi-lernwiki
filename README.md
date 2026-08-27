# FISI Lern-Wiki

![Status](https://img.shields.io/badge/Status-in%20Arbeit-blue)
![Ausbildung](https://img.shields.io/badge/Ausbildung-FISI-green)
![Fokus](https://img.shields.io/badge/Fokus-Linux%20%7C%20Git%20%7C%20Docker%20%7C%20SQL-orange)
![Sprache](https://img.shields.io/badge/Sprache-Deutsch-lightgrey)

Dieses Repository ist mein persönliches Lern-Wiki für die Umschulung zum **Fachinformatiker für Systemintegration**.

Ich dokumentiere hier wichtige IT-Grundlagen, praktische Übungen und eigene Zusammenfassungen zu Themen wie Linux, Git, GitHub, Docker, Datenbanken, Netzwerken, IT-Sicherheit und systemnaher Administration.

Der Fokus liegt darauf, technische Inhalte verständlich, sauber und öffentlich nachvollziehbar aufzubereiten.

---

## Ziel des Repositories

Dieses Wiki ist keine lose Notizensammlung, sondern eine strukturierte technische Wissensbasis.

Ziel ist es, Lerninhalte Schritt für Schritt aufzubauen und so zu dokumentieren, dass sie auch später noch verständlich und praktisch nutzbar sind.

Dabei geht es besonders um:

- IT-Grundlagen verständlich erklären
- praktische Befehle und Abläufe dokumentieren
- typische Fehler und Troubleshooting-Schritte sammeln
- Zusammenhänge zwischen Schule, Praxis und Home-Lab herstellen
- ein sauberes öffentliches Portfolio aufbauen
- Lernfortschritt nachvollziehbar machen
- technische Themen mit eigenen Worten wiederholen

---

## Aktueller Stand

| Bereich                                                         | Inhalt                                                  | Status                  |
| --------------------------------------------------------------- | ------------------------------------------------------- | ----------------------- |
| [LF1](./lernfelder/lf1-unternehmen-und-rolle/)                  | Unternehmen und eigene Rolle                            | Basis angelegt          |
| [LF2](./lernfelder/lf2-arbeitsplaetze-ausstatten/)              | Arbeitsplätze ausstatten                                | Version 1 abgeschlossen |
| [LF3](./lernfelder/lf3-clients-in-netzwerke-einbinden/)         | Clients in Netzwerke einbinden                          | Version 1 abgeschlossen |
| [LF4](./lernfelder/lf4-schutzbedarfsanalyse/)                   | Schutzbedarfsanalyse                                    | Version 1 abgeschlossen |
| [LF5](./lernfelder/lf5-software-configuration-data-management/) | Software zur Verwaltung von Daten anpassen              | Version 1 abgeschlossen |
| [Linux](./linux/)                                               | Linux-Grundlagen und Systemadministration               | Version 1 abgeschlossen |
| [Git & GitHub](./git-github/)                                   | Versionsverwaltung und GitHub-Workflows                 | Version 1 abgeschlossen |
| [Docker](./docker/)                                             | Container, Images, Volumes, Compose und Troubleshooting | Version 1 abgeschlossen |
| [Cheatsheets](./cheatsheets/)                                   | Kurze Befehlsübersichten für die Praxis                 | Version 1 abgeschlossen |
| [Datenbanken & SQL](./datenbanken-sql/)                         | SQL-Grundlagen und Datenbankbefehle                     | Version 1 abgeschlossen |            
| [Netzwerke](./netzwerke/)                                       | Netzwerkgrundlagen und Netzwerkdienste                  | Version 1 abgeschlossen |
| [IT-Sicherheit](./it-sicherheit/)                               | Sicherheitsgrundlagen und Schutzmaßnahmen               | geplant                 |
| [Virtualisierung](./virtualisierung/)                           | Virtuelle Maschinen und Laborumgebungen                 | geplant                 |

---

## Inhaltliche Schwerpunkte

### Linux

Der Linux-Bereich behandelt wichtige Grundlagen für Administration und Fehlersuche.

Dazu gehören unter anderem:

- Linux-Grundlagen
- Dateisystem und Pfade
- Dateien und Verzeichnisse
- Benutzer, Gruppen und Rechte
- Prozesse und Dienste
- Paketverwaltung
- Netzwerk unter Linux
- Logs und Fehlersuche
- Shell-Scripting
- praktische Systemadministration

[Zum Linux-Bereich](./linux/)

---

### Git und GitHub

Der Git/GitHub-Bereich dokumentiert die tägliche Arbeit mit Versionsverwaltung.

Dazu gehören unter anderem:

- Git-Grundlagen
- Repository und Arbeitsbereiche
- Commits und Historie
- Branches und Merge
- Remotes, Pull und Push
- GitHub-Zusammenarbeit
- `.gitignore` und Dateiverwaltung
- Fehlersuche und Wiederherstellung
- SSH und mehrere GitHub-Konten
- praktische Git-Workflows

[Zum Git/GitHub-Bereich](./git-github/)

---

### Docker

Der Docker-Bereich behandelt Container-Grundlagen und praktische Docker-Arbeit.

Dazu gehören unter anderem:

- Docker-Grundlagen
- Images und Container
- Volumes und Netzwerke
- Docker Compose
- Logs, Exec und Troubleshooting
- Docker in der FISI-Praxis

[Zum Docker-Bereich](./docker/)

---

### Cheatsheets

Der Cheatsheet-Bereich enthält kompakte Befehlsübersichten für die praktische Arbeit.

Aktuell enthalten sind:

- Linux-Befehle
- Git-Befehle
- Docker-Befehle
- Netzwerk-Befehle

[Zu den Cheatsheets](./cheatsheets/)

---

### Lernfelder

Die Lernfelder enthalten strukturierte Zusammenfassungen zu wichtigen Ausbildungsinhalten.

Aktuell sind besonders diese Bereiche ausgearbeitet:

- LF2: IT-Arbeitsplätze ausstatten
- LF3: Clients in Netzwerke einbinden
- LF4: Schutzbedarfsanalyse
- LF5: Software und Datenverwaltung

[Zu den Lernfeldern](./lernfelder/)

---

## Repository-Struktur

```text
fisi-lernwiki/
├── cheatsheets/
├── datenbanken-sql/
├── docker/
├── git-github/
├── it-sicherheit/
├── lernfelder/
│   ├── lf1-unternehmen-und-rolle/
│   ├── lf2-arbeitsplaetze-ausstatten/
│   ├── lf3-clients-in-netzwerke-einbinden/
│   ├── lf4-schutzbedarfsanalyse/
│   └── lf5-software-configuration-data-management/
├── linux/
├── netzwerke/
├── virtualisierung/
├── .gitignore
└── README.md
```

---

## Arbeitsweise

Dieses Repository wird schrittweise erweitert.

Neue Inhalte werden nicht unsortiert abgelegt, sondern in passende Themenbereiche eingeordnet. Dabei achte ich auf eine klare Struktur, verständliche Sprache und praktische Beispiele.

Typischer Aufbau vieler Kapitel:

```text
1. kurze Einführung
2. fachliche Erklärung
3. wichtige Begriffe
4. praktische Befehle oder Beispiele
5. typische Fehler
6. Bezug zur FISI-Praxis
7. kurze Zusammenfassung
```

Dadurch soll das Repository nicht nur beim Lernen helfen, sondern auch langfristig als Nachschlagewerk nutzbar bleiben.

---

## Was dieses Repository zeigt

Dieses Repository zeigt meinen Lernfortschritt in mehreren Bereichen der IT-Systemintegration.

Besonders sichtbar werden:

- technisches Grundverständnis
- strukturierte Dokumentation
- Arbeit mit Markdown
- Git- und GitHub-Nutzung
- Linux-Grundlagen
- Docker-Grundlagen
- SQL- und Datenbankbezug
- Netzwerk- und Sicherheitsbezug
- praxisnahes Lernen
- saubere Repository-Struktur
- regelmäßige Weiterentwicklung

Der Fokus liegt auf echtem Verständnis statt auf oberflächlichen Notizen.

---

## Praktischer Nutzen

Dieses Wiki soll mir helfen, wichtige Themen wiederzufinden und regelmäßig zu wiederholen.

Besonders nützlich ist es für:

| Situation              | Nutzen                                             |
| ---------------------- | -------------------------------------------------- |
| Lernen                 | Themen strukturiert wiederholen                    |
| Terminal-Praxis        | wichtige Befehle schnell nachschlagen              |
| Projekte               | eigene Arbeit sauber dokumentieren                 |
| GitHub-Portfolio       | technischen Fortschritt sichtbar machen            |
| Praktikumsvorbereitung | Linux, Git, Docker und Netzwerkgrundlagen festigen |
| Fehlersuche            | typische Fehler und Prüfwege nachvollziehen        |

---

## Geplante Erweiterungen

Als nächste Schritte sind geplant:

| Bereich           | Geplanter Inhalt                                            |
| ----------------- | ----------------------------------------------------------- |
| Netzwerke         | IP, Subnetting, DNS, DHCP, Routing, VLANs, WLAN             |
| IT-Sicherheit     | Schutzmaßnahmen, Bedrohungen, Zugriffsschutz, Backup        |
| Virtualisierung   | VMs, NAT, Bridge, Home-Lab, Serverumgebungen                |
| Datenbanken & SQL | SQL-Abfragen, Tabellen, Joins, Constraints, Praxisbeispiele |
| Docker            | spätere Erweiterung mit kleinen Laborprojekten              |
| Home-Lab          | praktische Server-, Netzwerk- und Containerübungen          |

---

## Hinweise

Dieses Repository enthält keine privaten Schulunterlagen, keine Zugangsdaten und keine internen Systeme.

Die Inhalte sind eigene Zusammenfassungen und praktische Lernnotizen. Sie werden regelmäßig angepasst, erweitert und verbessert.

Bei öffentlichen Beispielen nutze ich Platzhalter statt echter Zugangsdaten.

---

## Kurz zusammengefasst

Das **FISI Lern-Wiki** ist mein öffentliches technisches Lern- und Dokumentationsprojekt.

Es verbindet Ausbildungsinhalte, praktische IT-Grundlagen und eigene Übungsprojekte in einer sauberen GitHub-Struktur.

Der aktuelle Fokus liegt auf:

```text
Linux
Git & GitHub
Docker
Datenbanken & SQL
Lernfelder LF2 bis LF5
praktische Systemintegration
technische Dokumentation
```
