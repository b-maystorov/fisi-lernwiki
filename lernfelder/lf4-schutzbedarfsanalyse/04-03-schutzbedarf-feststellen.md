# 4.3 Schutzbedarf feststellen und bewerten

In diesem Kapitel geht es darum, den Schutzbedarf von Informationen, IT-Systemen, Anwendungen und Arbeitsbereichen festzustellen.

Eine Schutzbedarfsfeststellung hilft dabei zu bewerten, wie wichtig ein System oder eine Information für ein Unternehmen ist. Dabei wird geprüft, welche Auswirkungen ein Schaden hätte, wenn Daten unbefugt gelesen, verändert oder nicht mehr verfügbar wären.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil viele technische Maßnahmen vom Schutzbedarf abhängen. Ein besonders kritisches System braucht stärkere Schutzmaßnahmen als ein einfaches Testsystem.

---

## Kurz erklärt

Schutzbedarf beschreibt, wie stark Informationen, Systeme oder Prozesse geschützt werden müssen.

Dabei werden meistens die drei Schutzziele betrachtet:

- Vertraulichkeit
- Integrität
- Verfügbarkeit

Für jedes Schutzziel wird bewertet, wie groß der Schaden wäre, wenn dieses Ziel verletzt wird.

Beispiele:

- Was passiert, wenn vertrauliche Daten öffentlich werden?
- Was passiert, wenn Daten manipuliert werden?
- Was passiert, wenn ein System mehrere Stunden oder Tage ausfällt?
- Welche rechtlichen Folgen können entstehen?
- Welche finanziellen Schäden können entstehen?
- Können Kunden, Mitarbeitende oder Partner betroffen sein?
- Wird der Geschäftsbetrieb eingeschränkt?

Die Schutzbedarfsfeststellung ist die Grundlage, um passende Sicherheitsmaßnahmen auszuwählen.

---

## Ziel der Schutzbedarfsfeststellung

Das Ziel ist, den benötigten Schutz für Informationen und Systeme nachvollziehbar zu bewerten.

Eine Schutzbedarfsfeststellung hilft bei:

- Auswahl passender Sicherheitsmaßnahmen
- Priorisierung wichtiger Systeme
- Bewertung von Risiken
- Planung von Backups
- Entscheidung über Verschlüsselung
- Entscheidung über Verfügbarkeit
- Rechtevergabe
- Netzwerksegmentierung
- Notfallplanung
- Dokumentation von Sicherheitsentscheidungen

Ohne Schutzbedarfsfeststellung werden Sicherheitsmaßnahmen oft zufällig gewählt.

Manche Systeme werden dann zu schwach geschützt, obwohl sie kritisch sind. Andere Systeme werden vielleicht unnötig stark abgesichert, obwohl der Aufwand nicht zum Risiko passt.

---

## Was wird bewertet?

Bei einer Schutzbedarfsfeststellung können verschiedene Objekte bewertet werden.

| Objekt             | Beispiele                                           |
| ------------------ | --------------------------------------------------- |
| Informationen      | Kundendaten, Personaldaten, Verträge, Zugangsdaten  |
| Anwendungen        | ERP-System, E-Mail-System, Ticketsystem, Datenbank  |
| IT-Systeme         | Server, Clients, Firewalls, Switches, NAS           |
| Prozesse           | Bestellung, Support, Abrechnung, Benutzerverwaltung |
| Räume              | Serverraum, Büro, Archiv, Empfang                   |
| Kommunikationswege | VPN, WLAN, E-Mail, Cloud-Zugriff                    |
| Dokumentationen    | Netzpläne, Passwortdokumente, Notfallpläne          |

Wichtig ist, nicht nur einzelne Geräte zu betrachten.

Ein Server ist nicht automatisch kritisch, weil er teuer ist. Entscheidend ist, welche Daten und Prozesse davon abhängig sind.

---

## Schutzziele als Grundlage

Der Schutzbedarf wird meistens anhand der drei wichtigsten Schutzziele bewertet.

| Schutzziel      | Fragestellung                                                           |
| --------------- | ----------------------------------------------------------------------- |
| Vertraulichkeit | Was passiert, wenn unberechtigte Personen die Information sehen?        |
| Integrität      | Was passiert, wenn die Information falsch oder manipuliert ist?         |
| Verfügbarkeit   | Was passiert, wenn die Information oder das System nicht verfügbar ist? |

Ein System kann bei jedem Schutzziel unterschiedlich kritisch sein.

Beispiel:

Ein öffentliches Webangebot braucht vielleicht keine sehr hohe Vertraulichkeit, weil die Inhalte öffentlich sind. Die Verfügbarkeit kann aber hoch sein, wenn Kunden darüber Bestellungen aufgeben.

---

## Schutzbedarfskategorien

Der Schutzbedarf wird oft in Kategorien eingeteilt.

Eine einfache Einteilung ist:

| Schutzbedarf | Bedeutung                                                                      |
| ------------ | ------------------------------------------------------------------------------ |
| normal       | Schaden ist begrenzt und beherrschbar                                          |
| hoch         | Schaden ist deutlich und kann den Betrieb stark beeinträchtigen                |
| sehr hoch    | Schaden kann existenzbedrohend, rechtlich sehr kritisch oder extrem teuer sein |

Diese Kategorien helfen, Systeme vergleichbar zu machen.

Wichtig ist, dass die Bewertung begründet und dokumentiert wird.

---

## Schutzbedarf normal

Ein normaler Schutzbedarf liegt vor, wenn ein Schaden begrenzt bleibt und mit normalen Mitteln beherrschbar ist.

Mögliche Merkmale:

- geringe finanzielle Auswirkung
- keine oder geringe rechtliche Folgen
- keine sensiblen Daten betroffen
- kurzer Ausfall ist akzeptabel
- Daten können einfach wiederhergestellt werden
- Auswirkungen auf wenige Benutzer begrenzt
- keine starke Beeinträchtigung des Betriebs

Beispiele:

- Testsystem ohne echte Kundendaten
- öffentlich verfügbare Informationen
- einfacher Schulungsclient
- interne Notizen ohne vertraulichen Inhalt

Normaler Schutzbedarf bedeutet nicht, dass keine Sicherheit nötig ist. Es bedeutet nur, dass Standardmaßnahmen meistens ausreichend sind.

---

## Schutzbedarf hoch

Ein hoher Schutzbedarf liegt vor, wenn ein Schaden deutliche Auswirkungen hätte.

Mögliche Merkmale:

- wichtige Geschäftsprozesse betroffen
- mehrere Benutzer oder Abteilungen betroffen
- personenbezogene Daten betroffen
- längerer Ausfall problematisch
- deutlicher finanzieller Schaden möglich
- rechtliche oder vertragliche Folgen möglich
- Wiederherstellung aufwendig
- Reputationsschaden möglich

Beispiele:

- Dateiserver mit Abteilungsdaten
- E-Mail-System
- Kundendatenbank
- produktives Ticketsystem
- VPN-Zugang für Mitarbeitende
- zentrale Benutzerverwaltung

Bei hohem Schutzbedarf sind stärkere Maßnahmen notwendig, zum Beispiel bessere Zugriffskontrolle, Backup, Monitoring, Verschlüsselung und klare Prozesse.

---

## Schutzbedarf sehr hoch

Ein sehr hoher Schutzbedarf liegt vor, wenn ein Schaden besonders schwerwiegend wäre.

Mögliche Merkmale:

- existenzbedrohender Schaden möglich
- sehr hohe rechtliche Risiken
- große Mengen sensibler Daten betroffen
- kritische Infrastruktur betroffen
- langer Ausfall nicht akzeptabel
- schwerer Vertrauensverlust möglich
- massive finanzielle Folgen
- Wiederherstellung sehr schwierig
- Sicherheitsvorfall könnte viele Personen betreffen

Beispiele:

- zentrale Produktionssysteme
- Systeme mit besonders sensiblen personenbezogenen Daten
- Administratorzugänge
- Backup-Infrastruktur
- zentrale Authentifizierung
- kritische Datenbanken
- medizinische oder finanzielle Systeme

Bei sehr hohem Schutzbedarf müssen Maßnahmen besonders sorgfältig geplant, umgesetzt, getestet und dokumentiert werden.

---

## Bewertung der Vertraulichkeit

Bei der Vertraulichkeit wird geprüft, welche Folgen ein unbefugter Zugriff hätte.

Wichtige Fragen:

- Enthält das System personenbezogene Daten?
- Enthält es Kundendaten?
- Enthält es Zugangsdaten?
- Enthält es Geschäftsgeheimnisse?
- Enthält es interne Dokumentation?
- Könnten Angreifer die Informationen missbrauchen?
- Gibt es rechtliche Folgen bei Offenlegung?
- Würde ein Datenabfluss dem Unternehmen schaden?

Beispiele für hohe Vertraulichkeit:

- Personaldaten
- Kundendaten
- Finanzdaten
- Passwörter
- Netzpläne
- Verträge
- Bewerbungsunterlagen
- Gesundheitsdaten

Je sensibler die Daten, desto höher ist meistens der Schutzbedarf bei Vertraulichkeit.

---

## Bewertung der Integrität

Bei der Integrität wird geprüft, welche Folgen falsche oder manipulierte Daten hätten.

Wichtige Fragen:

- Müssen die Daten korrekt sein?
- Können falsche Daten zu falschen Entscheidungen führen?
- Können manipulierte Daten finanzielle Schäden verursachen?
- Kann eine falsche Konfiguration Systeme gefährden?
- Können Daten unbemerkt verändert werden?
- Ist nachvollziehbar, wer Änderungen durchgeführt hat?
- Gibt es Kontrollmechanismen?

Beispiele für hohe Integrität:

- Rechnungsdaten
- Konfigurationsdateien
- Datenbanken
- Backupdaten
- Benutzer- und Rechteinformationen
- Bestelldaten
- Produktionsdaten
- Logdateien

Integrität ist besonders wichtig, wenn falsche Daten technische, rechtliche oder wirtschaftliche Folgen haben können.

---

## Bewertung der Verfügbarkeit

Bei der Verfügbarkeit wird geprüft, welche Folgen ein Ausfall hätte.

Wichtige Fragen:

- Wie lange darf das System ausfallen?
- Wie viele Benutzer sind betroffen?
- Welche Geschäftsprozesse hängen davon ab?
- Gibt es Ersatzprozesse?
- Können Daten später nachgetragen werden?
- Entsteht finanzieller Schaden?
- Können Kunden nicht bedient werden?
- Gibt es vertragliche Verpflichtungen?
- Gibt es Notfallpläne?

Beispiele für hohe Verfügbarkeit:

- Internetanbindung
- DNS
- DHCP
- Firewall
- E-Mail-System
- Dateiablagen
- zentrale Benutzeranmeldung
- produktive Datenbanken
- ERP-System
- Backup- und Restore-Systeme

Ein System kann wenig vertrauliche Daten enthalten, aber trotzdem eine hohe Verfügbarkeit benötigen.

---

## Schadensauswirkungen

Um den Schutzbedarf zu bewerten, werden mögliche Schadensauswirkungen betrachtet.

Typische Schadensbereiche:

| Schadensbereich           | Beispiel                                   |
| ------------------------- | ------------------------------------------ |
| finanzieller Schaden      | Umsatzverlust, Wiederherstellungskosten    |
| rechtlicher Schaden       | Datenschutzverstoß, Vertragsverletzung     |
| organisatorischer Schaden | Arbeitsprozesse stehen still               |
| technischer Schaden       | Systeme müssen neu aufgebaut werden        |
| Reputationsschaden        | Kunden verlieren Vertrauen                 |
| Personenschaden           | Mitarbeitende oder Kunden werden gefährdet |
| Datenverlust              | wichtige Informationen gehen verloren      |
| Sicherheitsfolgen         | Angreifer erhalten weiteren Zugriff        |

Je größer die mögliche Auswirkung, desto höher sollte der Schutzbedarf bewertet werden.

---

## Abhängigkeiten beachten

Systeme sind oft voneinander abhängig.

Ein scheinbar kleines System kann sehr wichtig sein, wenn viele andere Systeme davon abhängen.

Beispiele:

- DNS wirkt unscheinbar, ist aber für viele Dienste notwendig.
- DHCP ist wichtig, damit Clients automatisch IP-Adressen bekommen.
- Eine Firewall ist zentral für Netztrennung und Internetzugang.
- Ein Backupserver ist kritisch für Wiederherstellung.
- Ein Verzeichnisdienst ist wichtig für Anmeldung und Rechte.
- Ein Switch kann ganze Bereiche vom Netzwerk trennen.

Bei der Schutzbedarfsfeststellung müssen solche Abhängigkeiten beachtet werden.

Sonst wird der Schutzbedarf einzelner Systeme unterschätzt.

---

## Maximumprinzip

Das Maximumprinzip bedeutet:

> Der höchste Schutzbedarf eines abhängigen Objekts wird auf das unterstützende System übertragen.

Beispiel:

Eine Datenbank enthält sehr vertrauliche Kundendaten. Der Server, auf dem diese Datenbank läuft, benötigt deshalb ebenfalls einen hohen oder sehr hohen Schutzbedarf.

Auch Backup-Systeme können einen hohen Schutzbedarf haben, weil sie Kopien wichtiger Daten enthalten.

Das Maximumprinzip verhindert, dass technische Basissysteme zu niedrig bewertet werden.

---

## Kumulationseffekt

Der Kumulationseffekt bedeutet:

> Viele einzelne Informationen mit normalem Schutzbedarf können zusammen einen höheren Schutzbedarf ergeben.

Beispiel:

Ein einzelnes Dokument ist vielleicht nicht besonders kritisch. Eine große Sammlung vieler Dokumente kann aber sehr vertraulich sein, weil daraus ein umfassendes Bild über Kunden, Mitarbeitende oder Geschäftsprozesse entsteht.

Weitere Beispiele:

- viele einzelne Kundendatensätze
- viele Logdateien
- viele E-Mails
- viele Supporttickets
- viele interne Dokumente

Die Menge und Kombination von Daten kann den Schutzbedarf erhöhen.

---

## Verteilungseffekt

Der Verteilungseffekt bedeutet:

> Wenn Informationen oder Funktionen auf mehrere Systeme verteilt sind, kann sich der Schutzbedarf auf mehrere Systeme ausweiten.

Beispiel:

Eine Anwendung besteht aus Webserver, Datenbankserver, Dateiserver und Authentifizierungsdienst. Wenn die Anwendung kritisch ist, müssen alle beteiligten Komponenten betrachtet werden.

Der Schutzbedarf betrifft dann nicht nur die Anwendung selbst, sondern auch die unterstützende Infrastruktur.

Dazu gehören zum Beispiel:

- Server
- Datenbank
- Netzwerk
- Firewall-Regeln
- Benutzerverwaltung
- Backup
- Monitoring
- Schnittstellen

---

## Schutzbedarf und Risiko

Schutzbedarf und Risiko hängen zusammen, sind aber nicht dasselbe.

| Begriff      | Bedeutung                                                  |
| ------------ | ---------------------------------------------------------- |
| Schutzbedarf | wie wichtig der Schutz eines Objekts ist                   |
| Risiko       | Wahrscheinlichkeit und Auswirkung eines möglichen Schadens |
| Maßnahme     | Handlung zur Verringerung des Risikos                      |

Ein System kann hohen Schutzbedarf haben, auch wenn aktuell keine konkrete Bedrohung sichtbar ist.

Der Schutzbedarf beschreibt, wie schlimm ein Schaden wäre. Das Risiko betrachtet zusätzlich, wie wahrscheinlich der Schaden ist.

---

## Vorgehen bei der Schutzbedarfsfeststellung

Ein sinnvolles Vorgehen kann so aussehen:

1. Geltungsbereich festlegen
2. Informationen und Systeme erfassen
3. Geschäftsprozesse und Abhängigkeiten verstehen
4. Schutzziele betrachten
5. mögliche Schäden einschätzen
6. Schutzbedarf je Schutzziel bewerten
7. Maximumprinzip und Abhängigkeiten beachten
8. Maßnahmen ableiten
9. Ergebnis dokumentieren
10. Bewertung regelmäßig überprüfen

Wichtig ist, dass die Bewertung nachvollziehbar ist.

Nicht nur das Ergebnis zählt, sondern auch die Begründung.

---

## Geltungsbereich festlegen

Zuerst muss geklärt werden, welcher Bereich betrachtet wird.

Beispiele für einen Geltungsbereich:

- ein Arbeitsplatzbereich
- eine Abteilung
- ein Server
- eine Anwendung
- ein Netzwerksegment
- ein Cloud-Dienst
- ein Geschäftsprozess
- ein Standort

Ohne klaren Geltungsbereich wird die Analyse unübersichtlich.

Man muss wissen, was betrachtet wird und was nicht betrachtet wird.

---

## Informationen und Systeme erfassen

Im nächsten Schritt werden relevante Informationen, Systeme und Dienste erfasst.

Mögliche Fragen:

- Welche Daten werden verarbeitet?
- Welche Anwendungen werden genutzt?
- Welche Server sind beteiligt?
- Welche Clients greifen darauf zu?
- Welche Benutzergruppen gibt es?
- Welche Netzwerkbereiche sind betroffen?
- Welche externen Dienste werden genutzt?
- Welche Schnittstellen gibt es?
- Welche Backups existieren?
- Welche Dokumentation ist vorhanden?

Diese Erfassung ist wichtig, weil man nur schützen kann, was man kennt.

---

## Geschäftsprozesse verstehen

IT-Systeme unterstützen Geschäftsprozesse.

Deshalb muss verstanden werden, wofür ein System genutzt wird.

Beispiele:

| Geschäftsprozess   | mögliche IT-Systeme                           |
| ------------------ | --------------------------------------------- |
| Personalverwaltung | HR-System, Dateiserver, E-Mail                |
| Kundensupport      | Ticketsystem, Wissensdatenbank, Telefonanlage |
| Verkauf            | CRM, ERP, E-Mail, Webshop                     |
| Buchhaltung        | Finanzsoftware, Datenbank, Backup             |
| IT-Betrieb         | Monitoring, Dokumentation, Adminzugänge       |
| Produktion         | Steuerungssysteme, Datenbanken, Netzwerk      |

Ein technisches System kann nur richtig bewertet werden, wenn seine Bedeutung für den Betrieb bekannt ist.

---

## Bewertung je Schutzziel

Für jedes Objekt sollte der Schutzbedarf je Schutzziel bewertet werden.

Beispielhafte Tabelle:

| Objekt                 | Vertraulichkeit | Integrität | Verfügbarkeit |
| ---------------------- | --------------- | ---------- | ------------- |
| öffentlicher Webserver | normal          | hoch       | hoch          |
| Personaldatenbank      | sehr hoch       | hoch       | hoch          |
| Testsystem             | normal          | normal     | normal        |
| Backupserver           | sehr hoch       | sehr hoch  | hoch          |
| DNS-Server             | normal          | hoch       | sehr hoch     |

Diese Tabelle zeigt, dass ein System nicht immer in allen Bereichen gleich bewertet wird.

---

## Gesamtbewertung

Nach der Einzelbewertung wird eine Gesamtbewertung gebildet.

Oft wird der höchste Wert übernommen.

Beispiel:

| Schutzziel      | Bewertung |
| --------------- | --------- |
| Vertraulichkeit | normal    |
| Integrität      | hoch      |
| Verfügbarkeit   | sehr hoch |

Gesamtbewertung:

| Gesamt | sehr hoch |
| ------ | --------- |

Der Grund ist, dass ein sehr hoher Schutzbedarf in einem Schutzziel schon ausreicht, um besondere Maßnahmen zu rechtfertigen.

---

## Maßnahmen aus dem Schutzbedarf ableiten

Aus dem Schutzbedarf werden passende Maßnahmen abgeleitet.

Beispiele:

| Schutzbedarf | mögliche Maßnahmen                                                                   |
| ------------ | ------------------------------------------------------------------------------------ |
| normal       | Standardpasswörter vermeiden, Updates, Basisbackup                                   |
| hoch         | MFA, Verschlüsselung, Monitoring, regelmäßige Rechteprüfung                          |
| sehr hoch    | starke Zugriffskontrolle, Hochverfügbarkeit, Notfallplan, erweiterte Protokollierung |

Die Maßnahmen müssen zum Risiko und zur Umgebung passen.

Ein hoher Schutzbedarf bedeutet nicht automatisch, dass jede mögliche Maßnahme umgesetzt werden muss. Maßnahmen müssen sinnvoll, wirksam und verhältnismäßig sein.

---

## Dokumentation der Schutzbedarfsfeststellung

Die Schutzbedarfsfeststellung muss dokumentiert werden.

Wichtige Inhalte:

- betrachtetes Objekt
- Geltungsbereich
- Verantwortliche Person
- verarbeitete Daten
- beteiligte Systeme
- Abhängigkeiten
- Bewertung der Vertraulichkeit
- Bewertung der Integrität
- Bewertung der Verfügbarkeit
- Begründung der Bewertung
- abgeleitete Maßnahmen
- offene Risiken
- Datum der Bewertung
- nächste Überprüfung

Eine gute Dokumentation macht Sicherheitsentscheidungen nachvollziehbar.

Sie hilft auch bei Audits, Übergaben, Support und späteren Änderungen.

---

## Regelmäßige Überprüfung

Schutzbedarf kann sich ändern.

Gründe dafür:

- neue Daten werden verarbeitet
- mehr Benutzer greifen auf ein System zu
- System wird produktiv statt nur testweise genutzt
- neue Schnittstellen entstehen
- Cloud-Dienste werden angebunden
- gesetzliche Anforderungen ändern sich
- neue Bedrohungen entstehen
- Geschäftsprozesse ändern sich
- Systeme werden wichtiger für den Betrieb

Deshalb muss der Schutzbedarf regelmäßig überprüft werden.

Eine alte Bewertung kann falsch werden, wenn sich die Umgebung verändert.

---

## Schutzbedarf bei Cloud-Diensten

Cloud-Dienste müssen ebenfalls bewertet werden.

Wichtige Fragen:

- Welche Daten liegen in der Cloud?
- Wer hat Zugriff?
- Wo werden Daten gespeichert?
- Gibt es MFA?
- Gibt es Protokollierung?
- Gibt es Backup oder Wiederherstellung?
- Gibt es Rollen und Rechte?
- Was passiert bei Ausfall des Cloud-Dienstes?
- Gibt es Datenschutzanforderungen?
- Gibt es Abhängigkeit von Internetverbindung?

Cloud bedeutet nicht automatisch weniger Verantwortung.

Auch bei Cloud-Diensten muss der Schutzbedarf bewertet und dokumentiert werden.

---

## Schutzbedarf bei mobilen Geräten

Mobile Geräte haben besondere Risiken.

Beispiele:

- Verlust
- Diebstahl
- Nutzung in fremden Netzwerken
- Zugriff von unterwegs
- private und geschäftliche Nutzung
- Cloud-Synchronisation
- ungeschützte WLANs
- defekte oder veraltete Geräte

Mögliche Maßnahmen:

- Festplattenverschlüsselung
- Gerätesperre
- MFA
- MDM
- VPN
- Remote-Wipe
- sichere Updateverwaltung
- keine lokalen sensiblen Daten, wenn möglich
- klare Nutzungsrichtlinien

Mobile Geräte haben oft erhöhten Schutzbedarf, weil sie außerhalb geschützter Unternehmensräume genutzt werden.

---

## Schutzbedarf bei Administratorzugängen

Administratorzugänge sind besonders kritisch.

Wenn ein Administratorzugang kompromittiert wird, können Angreifer großen Schaden verursachen.

Mögliche Folgen:

- Benutzerrechte verändern
- Daten kopieren oder löschen
- Sicherheitsmaßnahmen deaktivieren
- Systeme manipulieren
- Backups löschen
- neue Konten erstellen
- Malware verteilen
- Logs verändern

Mögliche Maßnahmen:

- getrennte Admin-Konten
- MFA
- starke Passwörter
- keine geteilten Konten
- Protokollierung
- Zugriff nur aus Managementnetz
- regelmäßige Rechteprüfung
- Prinzip der minimalen Rechte
- zeitlich begrenzte Adminrechte
- sichere Dokumentation

Administratorzugänge haben fast immer hohen oder sehr hohen Schutzbedarf.

---

## Praxisbeispiele

### Beispiel 1: Dateiserver mit Abteilungsdaten

Ein Dateiserver enthält Projektdaten, Kundendokumente und interne Unterlagen. Die Vertraulichkeit ist hoch, weil unbefugter Zugriff problematisch wäre. Die Integrität ist hoch, weil falsche oder gelöschte Dateien den Betrieb stören. Die Verfügbarkeit ist ebenfalls hoch, weil mehrere Abteilungen täglich damit arbeiten.

### Beispiel 2: Öffentliches Informationssystem

Ein öffentliches System enthält nur allgemeine Informationen. Die Vertraulichkeit ist normal, weil die Inhalte öffentlich sind. Die Integrität ist hoch, weil falsche Inhalte dem Unternehmen schaden könnten. Die Verfügbarkeit kann hoch sein, wenn Kunden das System regelmäßig nutzen.

### Beispiel 3: Backupserver

Ein Backupserver enthält Kopien vieler wichtiger Systeme. Die Vertraulichkeit ist sehr hoch, weil viele Daten gesammelt gespeichert sind. Die Integrität ist sehr hoch, weil beschädigte Backups im Notfall wertlos sind. Die Verfügbarkeit ist hoch, weil Wiederherstellung schnell möglich sein muss.

---

## Typische Fehler

| Fehler                                   | Problem                                              |
| ---------------------------------------- | ---------------------------------------------------- |
| nur einzelne Geräte bewerten             | Daten, Prozesse und Abhängigkeiten werden übersehen  |
| Schutzbedarf nicht begründen             | Bewertung ist später nicht nachvollziehbar           |
| DNS, DHCP oder Backup unterschätzen      | Basissysteme können sehr kritisch sein               |
| Cloud-Dienste nicht betrachten           | wichtige Daten und Abhängigkeiten bleiben unbewertet |
| Administratorzugänge zu niedrig bewerten | hohes Schadenspotenzial wird unterschätzt            |
| Schutzbedarf nie aktualisieren           | Bewertung passt nicht mehr zur Realität              |
| nur Vertraulichkeit betrachten           | Integrität und Verfügbarkeit werden vergessen        |
| alle Systeme gleich bewerten             | wichtige Unterschiede werden nicht erkannt           |
| keine Maßnahmen ableiten                 | Analyse bleibt ohne praktischen Nutzen               |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist die Schutzbedarfsfeststellung eine wichtige Grundlage für sichere IT-Systeme.

Ein FISI muss verstehen, welche Systeme und Daten kritisch sind und welche Schutzmaßnahmen daraus folgen.

In der Praxis bedeutet das:

- Systeme und Daten erfassen
- Abhängigkeiten erkennen
- Vertraulichkeit, Integrität und Verfügbarkeit bewerten
- Schutzbedarf begründen
- Backupbedarf einschätzen
- Rechte und Zugriffe bewerten
- Cloud- und mobile Geräte berücksichtigen
- Administratorzugänge besonders schützen
- Maßnahmen dokumentieren
- Bewertungen regelmäßig prüfen

Ein guter FISI fragt nicht nur:

> Welche Technik ist vorhanden?

sondern auch:

> Welche Daten und Prozesse hängen daran, welcher Schaden wäre möglich und wie stark muss das System geschützt werden?

---

## Kurze Zusammenfassung

Die Schutzbedarfsfeststellung bewertet, wie stark Informationen, Systeme und Prozesse geschützt werden müssen.

Grundlage sind die Schutzziele Vertraulichkeit, Integrität und Verfügbarkeit.

Der Schutzbedarf wird meistens in normal, hoch und sehr hoch eingeteilt.

Wichtige Punkte sind Schadensauswirkungen, Abhängigkeiten, Maximumprinzip, Kumulationseffekt, Verteilungseffekt, Dokumentation und regelmäßige Überprüfung.

Für FISI ist dieses Thema wichtig, weil technische Sicherheitsmaßnahmen nur sinnvoll geplant werden können, wenn der Schutzbedarf bekannt ist.
