# 3.9 Geräte mit Strom versorgen und Green IT beachten

In diesem Kapitel geht es um die Stromversorgung von IT-Geräten und um den verantwortungsvollen Umgang mit Energie und Ressourcen.

IT-Systeme benötigen eine zuverlässige Stromversorgung. Ohne Strom funktionieren Clients, Server, Switches, Router, Firewalls, Access Points, Drucker und Speichersysteme nicht. Gleichzeitig verbrauchen IT-Systeme Energie, erzeugen Wärme und verursachen Kosten. Deshalb ist es wichtig, technische Anforderungen, Betriebssicherheit und Nachhaltigkeit gemeinsam zu betrachten.

Für Fachinformatiker für Systemintegration ist dieses Thema wichtig, weil Stromversorgung, Ausfallsicherheit, Energieverbrauch, Kühlung und Green IT direkte Auswirkungen auf Betrieb, Kosten und Verfügbarkeit haben.

---

## Kurz erklärt

Stromversorgung bedeutet, IT-Geräte sicher und zuverlässig mit elektrischer Energie zu versorgen.

Green IT bedeutet, IT-Systeme möglichst energieeffizient, ressourcenschonend und nachhaltig zu planen, zu betreiben und zu entsorgen.

Wichtige Themen sind:

- Netzteile
- Stromverbrauch
- USV
- PoE
- Serverraum-Stromversorgung
- Kühlung
- Energieeffizienz
- Energiesparfunktionen
- Lebensdauer von Hardware
- Recycling und Entsorgung
- nachhaltige Beschaffung
- Dokumentation

Ein IT-System soll nicht nur funktionieren, sondern auch sicher, effizient und langfristig sinnvoll betrieben werden.

---

## Grundbegriffe der Stromversorgung

Bei IT-Geräten sind einige elektrische Grundbegriffe wichtig.

| Begriff          | Bedeutung                                                            |
| ---------------- | -------------------------------------------------------------------- |
| Spannung         | elektrischer Druck, angegeben in Volt                                |
| Stromstärke      | Menge des fließenden Stroms, angegeben in Ampere                     |
| Leistung         | aufgenommene oder abgegebene Energie pro Zeit, angegeben in Watt     |
| Energieverbrauch | verbrauchte Energie über Zeit, angegeben in Kilowattstunden          |
| Netzteil         | wandelt Strom aus der Steckdose in passende Spannungen für Geräte um |
| Wirkungsgrad     | Verhältnis zwischen aufgenommener und nutzbarer Energie              |
| Abwärme          | Energieverlust, der als Wärme entsteht                               |

Für die Praxis ist besonders wichtig: Mehr Leistung bedeutet meistens auch mehr Stromverbrauch und mehr Abwärme.

---

## Leistung und Energieverbrauch

Die elektrische Leistung wird in Watt angegeben.

Beispiele:

| Gerät            | typischer Verbrauch                              |
| ---------------- | ------------------------------------------------ |
| einfacher Laptop | oft ca. 15 bis 65 Watt                           |
| Desktop-PC       | je nach Ausstattung ca. 50 bis 300 Watt          |
| Workstation      | je nach CPU/GPU deutlich mehr                    |
| Monitor          | ca. 15 bis 80 Watt                               |
| Switch           | abhängig von Portanzahl und PoE                  |
| Server           | je nach Ausstattung mehrere hundert Watt möglich |

Der Energieverbrauch wird meistens in Kilowattstunden angegeben.

Eine Kilowattstunde bedeutet:

```text
1.000 Watt für 1 Stunde = 1 kWh
```

Ein Gerät mit 100 Watt Verbrauch nutzt in 10 Stunden ungefähr 1 kWh Energie.

---

## Warum Stromverbrauch in der IT wichtig ist

Stromverbrauch ist in der IT aus mehreren Gründen wichtig.

Wichtige Auswirkungen:

- höhere Betriebskosten
- mehr Wärmeentwicklung
- mehr Kühlungsbedarf
- höhere Belastung der Stromversorgung
- größere Anforderungen an USV und Serverraum
- schlechtere Umweltbilanz
- kürzere Akkulaufzeit bei mobilen Geräten

Bei einzelnen Geräten wirkt der Verbrauch oft klein. In Unternehmen mit vielen Clients, Monitoren, Servern und Netzwerkgeräten kann der gesamte Verbrauch aber sehr hoch werden.

---

## Netzteile

Ein Netzteil versorgt ein IT-Gerät mit der passenden elektrischen Spannung.

Bei Desktop-PCs wandelt das Netzteil Wechselstrom aus der Steckdose in verschiedene Gleichspannungen um, die Mainboard, CPU, RAM, SSD, Grafikkarte und andere Komponenten benötigen.

Wichtige Kriterien bei Netzteilen:

- ausreichende Leistung
- gute Effizienz
- passende Anschlüsse
- Schutzschaltungen
- Qualität der Spannungsversorgung
- Lautstärke
- Bauform
- Herstellerqualität

Ein schlechtes oder zu schwaches Netzteil kann zu Instabilität, Abstürzen oder Hardwareproblemen führen.

---

## Power over Ethernet

PoE bedeutet **Power over Ethernet**.

Dabei werden Daten und Strom über dasselbe Netzwerkkabel übertragen.

Typische PoE-Geräte:

- Access Points
- IP-Telefone
- Überwachungskameras
- kleine Netzwerkgeräte
- Sensoren

Vorteile von PoE:

- weniger separate Netzteile
- einfachere Installation
- zentrale Stromversorgung über Switch
- Geräte können über USV abgesichert werden
- flexiblere Platzierung von Access Points
- weniger Kabelchaos

PoE ist besonders praktisch bei Geräten, die an Decken, Wänden oder schwer erreichbaren Stellen montiert werden.

---

## PoE-Budget

Ein PoE-Switch kann nur eine begrenzte Gesamtleistung bereitstellen.

Diese Gesamtleistung nennt man PoE-Budget.

Beispiel:

Ein Switch hat 24 Ports, aber ein PoE-Budget von 180 Watt. Wenn viele Access Points, Kameras oder IP-Telefone angeschlossen werden, muss geprüft werden, ob die Gesamtleistung ausreicht.

Wichtige Punkte:

- Leistung pro Gerät
- Gesamtleistung des Switches
- PoE-Standard
- Kabelqualität
- Reserven für Erweiterung
- Priorisierung wichtiger Ports

Wenn das PoE-Budget überschritten wird, können Geräte ausfallen oder nicht starten.

---

## USV

USV bedeutet **Unterbrechungsfreie Stromversorgung**.

Eine USV versorgt Geräte bei Stromausfall kurzfristig weiter.

Sie wird häufig eingesetzt für:

- Server
- NAS-Systeme
- Firewalls
- Router
- Switches
- Storage-Systeme
- wichtige Netzwerkkomponenten

Eine USV soll nicht stundenlang den Betrieb ersetzen. Sie soll kurze Stromausfälle überbrücken oder genug Zeit geben, Systeme kontrolliert herunterzufahren.

---

## Aufgaben einer USV

Eine USV schützt IT-Systeme vor Stromproblemen.

Wichtige Aufgaben:

- kurze Stromausfälle überbrücken
- Spannungsschwankungen ausgleichen
- kontrolliertes Herunterfahren ermöglichen
- Datenverlust vermeiden
- Hardware vor plötzlichem Ausschalten schützen
- zentrale Netzwerkdienste kurzfristig verfügbar halten

Gerade Server und Speichersysteme sollten nicht plötzlich ohne Strom ausgehen, weil Daten beschädigt werden können.

---

## Stromversorgung im Serverraum

Ein Serverraum benötigt eine stabile und sichere Stromversorgung.

Wichtige Anforderungen:

- ausreichend dimensionierte Stromkreise
- USV
- Überspannungsschutz
- getrennte Stromkreise bei wichtigen Systemen
- redundante Netzteile bei Servern
- saubere Kabelführung
- Brandschutz
- Temperaturüberwachung
- Zugangskontrolle
- Dokumentation
- keine Überlastung von Steckdosenleisten

Serverräume sollten nicht wie normale Büroräume behandelt werden.

Ein Serverraum ist ein kritischer Bereich für den IT-Betrieb.

---

## Redundante Stromversorgung

Redundanz bedeutet, dass wichtige Komponenten mehrfach vorhanden sind.

Bei Stromversorgung kann das bedeuten:

- zwei Netzteile in einem Server
- zwei Stromkreise
- zwei USV-Systeme
- getrennte Stromleisten
- Notstromversorgung
- redundante Stromversorgung im Rechenzentrum

Redundante Stromversorgung erhöht die Verfügbarkeit.

Wichtig ist aber, dass Redundanz richtig angeschlossen wird. Zwei Netzteile bringen wenig, wenn beide an derselben fehlerhaften Steckdosenleiste hängen.

---

## Kühlung und Abwärme

IT-Geräte erzeugen Wärme.

Je mehr Energie ein Gerät verbraucht, desto mehr Wärme muss abgeführt werden.

Wichtige Punkte:

- Luftstrom
- Lüfter
- Raumtemperatur
- Staub
- Abstand zwischen Geräten
- freie Lüftungsschlitze
- Klimatisierung im Serverraum
- Temperaturüberwachung
- keine blockierten Racks

Überhitzung kann zu Leistungseinbrüchen, Abstürzen oder Hardwaredefekten führen.

Kühlung ist daher ein Teil der Betriebssicherheit.

---

## Green IT

Green IT bedeutet, IT ressourcenschonend und energieeffizient zu planen, zu nutzen und zu entsorgen.

Green IT betrifft den gesamten Lebenszyklus von IT-Systemen:

- Beschaffung
- Nutzung
- Wartung
- Erweiterung
- Wiederverwendung
- Entsorgung

Ziel ist, Umweltbelastung zu reduzieren, Energie zu sparen und Ressourcen sinnvoll einzusetzen.

Green IT ist nicht nur Umweltschutz, sondern auch ein wirtschaftliches Thema.

---

## Energieeffizienz bei Clients

Bei Arbeitsplatzrechnern kann viel Energie gespart werden.

Maßnahmen:

- energieeffiziente Hardware auswählen
- SSD statt alter HDD nutzen
- moderne CPUs mit gutem Energiemanagement
- Monitore mit geringem Verbrauch
- Energiesparmodus aktivieren
- Bildschirm automatisch ausschalten
- Geräte nach Arbeitsende herunterfahren
- ungenutzte Geräte entfernen
- zentrale Energieprofile nutzen
- alte ineffiziente Hardware ersetzen

Besonders bei vielen Arbeitsplätzen kann Energieeinsparung wirtschaftlich relevant sein.

---

## Energieeffizienz bei Servern

Server laufen oft dauerhaft.

Deshalb ist Energieeffizienz hier besonders wichtig.

Wichtige Maßnahmen:

- Virtualisierung
- Konsolidierung von Diensten
- effiziente Netzteile
- moderne Hardware
- passende Dimensionierung
- Monitoring der Auslastung
- Abschaltung ungenutzter Systeme
- effiziente Kühlung
- Storage sinnvoll planen
- alte Hardware ersetzen

Ein Server, der dauerhaft kaum ausgelastet ist, kann durch Virtualisierung oder Zusammenlegung von Diensten effizienter genutzt werden.

---

## Virtualisierung und Green IT

Virtualisierung kann Green IT unterstützen.

Durch Virtualisierung können mehrere virtuelle Server auf einer physischen Hardware laufen.

Vorteile:

- bessere Ressourcenauslastung
- weniger physische Server
- geringerer Stromverbrauch
- weniger Abwärme
- weniger Platzbedarf
- einfachere Verwaltung
- schnellere Bereitstellung von Systemen

Virtualisierung spart aber nur dann Energie, wenn physische Systeme dadurch wirklich reduziert oder besser genutzt werden.

---

## Nachhaltige Beschaffung

Schon beim Kauf von IT-Geräten kann Nachhaltigkeit berücksichtigt werden.

Wichtige Kriterien:

- Energieverbrauch
- Reparierbarkeit
- Lebensdauer
- Ersatzteilverfügbarkeit
- Garantie
- Erweiterbarkeit
- Hersteller-Support
- Recyclingfähigkeit
- Verpackung
- Umweltzertifikate
- Möglichkeit zur Wiederverwendung

Ein langlebiges und reparierbares Gerät kann nachhaltiger sein als ein sehr günstiges Gerät, das schnell ersetzt werden muss.

---

## Lebensdauer von Hardware

Hardware sollte sinnvoll lange genutzt werden.

Dabei muss ein Gleichgewicht gefunden werden.

Zu frühes Ersetzen verursacht unnötige Kosten und Elektroschrott. Zu langes Nutzen alter Hardware kann Energie verschwenden, Sicherheitsrisiken erhöhen und Support erschweren.

Wichtige Faktoren:

- Leistung reicht noch aus
- Sicherheitsupdates verfügbar
- Betriebssystem wird unterstützt
- Ersatzteile erhältlich
- Stromverbrauch angemessen
- Ausfallrisiko vertretbar
- Benutzer können produktiv arbeiten

Die Lebensdauer sollte geplant und dokumentiert werden.

---

## Reparatur und Erweiterung

Nachhaltigkeit kann verbessert werden, wenn Geräte repariert oder erweitert werden können.

Beispiele:

- RAM erweitern
- SSD austauschen
- Akku tauschen
- Netzteil ersetzen
- Lüfter reinigen
- Tastatur oder Display reparieren
- Dockingstation weiterverwenden

Geräte, bei denen Komponenten nicht austauschbar sind, können schneller zu Elektroschrott werden.

Für Unternehmen ist Wartbarkeit deshalb ein wichtiges Auswahlkriterium.

---

## Wiederverwendung

Nicht jedes alte Gerät muss sofort entsorgt werden.

Mögliche Weiterverwendung:

- Schulungsgerät
- Testgerät
- Ersatzgerät
- Laborumgebung
- Thin Client
- Spende nach sicherer Datenlöschung
- internes Zweitgerät

Vor Wiederverwendung müssen Daten sicher gelöscht und Lizenzen geprüft werden.

Ein Gerät, das für eine Aufgabe zu schwach ist, kann für eine andere Aufgabe noch ausreichend sein.

---

## Recycling und Entsorgung

IT-Geräte enthalten wertvolle Rohstoffe, aber auch problematische Stoffe.

Deshalb dürfen sie nicht einfach im normalen Müll entsorgt werden.

Wichtige Punkte:

- Elektroschrott fachgerecht entsorgen
- Akkus getrennt behandeln
- Datenträger sicher löschen oder vernichten
- Entsorgung dokumentieren
- zertifizierte Entsorgungsdienstleister nutzen
- Datenschutz beachten
- Recyclingmöglichkeiten prüfen

Besonders Datenträger müssen vor Entsorgung sicher behandelt werden, weil dort noch sensible Daten gespeichert sein können.

---

## Sichere Datenlöschung vor Entsorgung

Vor Entsorgung, Verkauf oder Weitergabe müssen Daten sicher entfernt werden.

Normales Löschen reicht oft nicht aus.

Mögliche Maßnahmen:

- sichere Löschverfahren
- vollständige Verschlüsselung vor Nutzung
- Zurücksetzen mit sicherer Löschung
- physische Vernichtung bei sensiblen Daten
- Löschprotokoll
- zertifizierte Datenvernichtung

Datenschutz gilt auch am Ende des Gerätelebenszyklus.

Ein alter Laptop oder eine alte Festplatte kann ein Sicherheitsrisiko sein, wenn Daten nicht korrekt gelöscht wurden.

---

## Green IT im Betrieb

Green IT endet nicht beim Kauf.

Auch der laufende Betrieb ist wichtig.

Maßnahmen im Betrieb:

- Energieprofile nutzen
- Geräte bei Nichtnutzung ausschalten
- Monitoring von Verbrauch und Auslastung
- Server konsolidieren
- Druckverhalten reduzieren
- Cloud-Dienste bewusst nutzen
- alte Geräte austauschen, wenn sinnvoll
- Kühlung optimieren
- unnötige Hardware entfernen
- Benutzer sensibilisieren

Viele kleine Maßnahmen können in Summe eine große Wirkung haben.

---

## Drucker und Green IT

Drucker sind ein typisches Green-IT-Thema.

Maßnahmen:

- Duplexdruck standardmäßig aktivieren
- Schwarzweißdruck als Standard
- Follow-Me-Printing
- unnötige Ausdrucke vermeiden
- digitale Dokumente nutzen
- Toner und Tinte richtig entsorgen
- energieeffiziente Drucker einsetzen
- Geräte konsolidieren
- Druckvolumen überwachen

Weniger Drucken spart Papier, Toner, Energie und Kosten.

---

## Dokumentation der Stromversorgung

Stromversorgung sollte dokumentiert werden, besonders in Serverräumen und Netzwerkschränken.

Wichtige Informationen:

- welches Gerät hängt an welcher Steckdose
- welcher Stromkreis versorgt welche Geräte
- welche Geräte hängen an der USV
- Leistung der USV
- Batteriezustand
- Laufzeit der USV
- Netzteile und Redundanz
- PoE-Budget
- Stromverbrauch wichtiger Systeme
- Wartungstermine
- Austauschdatum von Akkus

Dokumentation hilft bei Wartung, Fehlersuche und Notfällen.

---

## Sicherheit bei Strom und IT-Geräten

Bei Stromversorgung muss Sicherheit beachtet werden.

Wichtige Regeln:

- keine beschädigten Kabel verwenden
- Steckdosenleisten nicht überlasten
- Kabel ordentlich verlegen
- keine Stolperfallen schaffen
- Lüftungsschlitze frei halten
- Geräte nicht unsachgemäß öffnen
- Netzteile passend verwenden
- Flüssigkeiten von Geräten fernhalten
- Serverräume vor unbefugtem Zugriff schützen
- elektrische Arbeiten nur durch qualifizierte Personen durchführen lassen

FISI muss Stromversorgung verstehen und beachten, aber nicht jede elektrische Arbeit selbst durchführen. Arbeiten an Elektroinstallationen gehören zu Fachbereichen mit entsprechenden Qualifikationen.

---

## Praxisbeispiele

### Beispiel 1: Access Points mit PoE

Ein Unternehmen montiert Access Points an der Decke. Die Geräte erhalten Daten und Strom über Netzwerkkabel vom PoE-Switch. Dadurch werden keine separaten Steckdosen an der Decke benötigt.

### Beispiel 2: Server mit USV

Ein Server und ein NAS hängen an einer USV. Bei kurzem Stromausfall laufen die Geräte weiter. Bei längerem Ausfall fährt die USV die Systeme kontrolliert herunter, um Datenverlust zu vermeiden.

### Beispiel 3: Green IT bei Arbeitsplatzrechnern

Ein Unternehmen aktiviert Energieprofile, automatische Bildschirmabschaltung und ersetzt alte HDD-PCs durch effizientere Geräte mit SSD. Dadurch sinken Stromverbrauch, Wärmeentwicklung und Supportaufwand.

---

## Typische Fehler

| Fehler                                 | Problem                                   |
| -------------------------------------- | ----------------------------------------- |
| PoE-Budget nicht berechnen             | Geräte starten nicht oder fallen aus      |
| USV nicht testen                       | Schutz funktioniert im Ernstfall nicht    |
| alte USV-Akkus nicht tauschen          | Laufzeit ist viel kürzer als erwartet     |
| Steckdosenleisten überlasten           | Sicherheitsrisiko                         |
| Stromversorgung nicht dokumentieren    | Fehlersuche und Wartung werden schwierig  |
| Kühlung ignorieren                     | Hardware wird instabil oder fällt aus     |
| Geräte dauerhaft unnötig laufen lassen | höhere Kosten und Energieverbrauch        |
| alte Datenträger unsicher entsorgen    | Datenschutzrisiko                         |
| Green IT nur als Umweltthema sehen     | wirtschaftliche Vorteile werden übersehen |

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Stromversorgung ein wichtiger Teil des sicheren IT-Betriebs.

Ein FISI muss wissen, welche Geräte zuverlässig mit Strom versorgt werden müssen, wo USV oder PoE sinnvoll sind und wie Stromausfälle, Überhitzung oder ineffiziente Hardware den Betrieb beeinflussen.

Green IT ist ebenfalls praxisrelevant, weil IT-Systeme Kosten, Energieverbrauch und Ressourcen verursachen.

In der Praxis bedeutet das:

- Strombedarf von Geräten einschätzen
- PoE-Budget beachten
- USV sinnvoll einplanen
- Serverräume und Netzwerkschränke verstehen
- Kühlung berücksichtigen
- energieeffiziente Hardware auswählen
- Energiesparfunktionen nutzen
- Lebenszyklus von Hardware planen
- sichere Entsorgung beachten
- Stromversorgung dokumentieren

Ein guter FISI betrachtet IT-Systeme nicht nur technisch, sondern auch betrieblich, wirtschaftlich und nachhaltig.

---

## Kurze Zusammenfassung

IT-Geräte benötigen eine zuverlässige und sichere Stromversorgung.

Wichtige Themen sind Netzteile, Leistung, Energieverbrauch, PoE, USV, Serverraum-Stromversorgung, Redundanz, Kühlung und Dokumentation.

Green IT bedeutet, IT-Systeme energieeffizient, ressourcenschonend und nachhaltig zu planen, zu betreiben und zu entsorgen.

Dazu gehören nachhaltige Beschaffung, längere Nutzungsdauer, Reparatur, Wiederverwendung, Recycling, sichere Datenlöschung und bewusster Energieverbrauch.

Für FISI ist dieses Kapitel wichtig, weil Stromversorgung und Green IT direkte Auswirkungen auf Verfügbarkeit, Sicherheit, Kosten und professionellen IT-Betrieb haben.
