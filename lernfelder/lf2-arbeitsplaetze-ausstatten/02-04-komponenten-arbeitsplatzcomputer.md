# 2.4 Komponenten eines Arbeitsplatzcomputers

In diesem Kapitel geht es um die wichtigsten Hardware-Komponenten eines Arbeitsplatzcomputers.

Ein Arbeitsplatzcomputer besteht aus mehreren Bauteilen, die zusammenarbeiten. Jede Komponente hat eine eigene Aufgabe. Für Fachinformatiker für Systemintegration ist wichtig zu verstehen, welche Komponente welche Funktion hat, wie sie sich auf die Leistung auswirkt und worauf man bei Auswahl, Wartung und Fehlersuche achten muss.

---

## Kurz erklärt

Ein Computer verarbeitet Daten mit Hilfe verschiedener Komponenten.

Die wichtigsten Bestandteile sind:

- Mainboard
- CPU
- RAM
- Massenspeicher
- Grafikkarte
- Netzteil
- Kühlung
- Gehäuse
- Schnittstellen
- Netzwerkkarte
- Monitor
- Eingabegeräte
- Drucker und Scanner

Diese Komponenten müssen technisch zusammenpassen. Ein schneller Prozessor bringt wenig, wenn zu wenig RAM vorhanden ist oder eine langsame Festplatte das System ausbremst.

---

## Überblick über die wichtigsten Komponenten

| Komponente        | Hauptaufgabe                                   |
| ----------------- | ---------------------------------------------- |
| Mainboard         | verbindet alle Komponenten miteinander         |
| CPU               | verarbeitet Befehle und Berechnungen           |
| RAM               | speichert Daten kurzfristig während der Arbeit |
| SSD / HDD         | speichert Daten dauerhaft                      |
| Grafikkarte       | berechnet Bildausgabe und Grafikleistung       |
| Netzteil          | versorgt alle Komponenten mit Strom            |
| Kühlung           | verhindert Überhitzung                         |
| Gehäuse           | schützt und organisiert die Hardware           |
| Netzwerkkarte     | verbindet den Computer mit dem Netzwerk        |
| Schnittstellen    | ermöglichen Anschluss externer Geräte          |
| Monitor           | zeigt die Ausgabe des Computers an             |
| Tastatur / Maus   | ermöglichen Eingabe durch den Benutzer         |
| Drucker / Scanner | geben Dokumente aus oder digitalisieren sie    |

---

## Mainboard

Das Mainboard ist die zentrale Platine eines Computers. Es verbindet CPU, RAM, Speicher, Grafikkarte, Netzteil und weitere Komponenten miteinander.

Ohne Mainboard können die einzelnen Bauteile nicht miteinander kommunizieren.

Wichtige Bestandteile eines Mainboards:

| Bestandteil        | Bedeutung                                          |
| ------------------ | -------------------------------------------------- |
| CPU-Sockel         | Steckplatz für den Prozessor                       |
| RAM-Steckplätze    | Steckplätze für Arbeitsspeicher                    |
| M.2-Steckplätze    | Anschluss für schnelle SSDs                        |
| SATA-Anschlüsse    | Anschluss für SSDs, HDDs oder Laufwerke            |
| PCIe-Steckplätze   | Anschluss für Grafikkarten oder Erweiterungskarten |
| Chipsatz           | steuert viele Verbindungen auf dem Mainboard       |
| UEFI/BIOS          | Firmware zum Starten und Konfigurieren des Systems |
| Stromanschlüsse    | Versorgung des Mainboards und der CPU              |
| interne Anschlüsse | Lüfter, USB, Frontpanel, Audio                     |

---

## Formfaktoren beim Mainboard

Der Formfaktor beschreibt die Größe und Bauform eines Mainboards.

Häufige Formfaktoren:

| Formfaktor         | Einsatz                                     |
| ------------------ | ------------------------------------------- |
| ATX                | normale Desktop-PCs, viele Anschlüsse       |
| Micro-ATX          | kleinere PCs, weniger Erweiterungsplätze    |
| Mini-ITX           | sehr kleine Systeme                         |
| proprietäre Formen | häufig bei Fertig-PCs oder Business-Geräten |

Der Formfaktor muss zum Gehäuse passen. Ein ATX-Mainboard passt nicht in jedes kleine Gehäuse.

---

## UEFI und BIOS

UEFI oder BIOS ist die Firmware des Computers. Sie startet vor dem Betriebssystem und initialisiert die Hardware.

Aufgaben von UEFI/BIOS:

- Hardware erkennen
- Boot-Reihenfolge festlegen
- CPU, RAM und Laufwerke initialisieren
- Sicherheitseinstellungen verwalten
- Secure Boot aktivieren
- TPM verwalten
- Lüftersteuerung beeinflussen
- Firmware-Updates ermöglichen

Moderne Systeme verwenden meistens UEFI. BIOS ist der ältere Begriff, wird aber im Alltag noch oft verwendet.

Für FISI ist UEFI wichtig, weil viele Probleme schon vor dem Betriebssystem entstehen können, zum Beispiel falsche Boot-Reihenfolge, deaktiviertes TPM oder falsch konfigurierte Secure-Boot-Einstellungen.

---

## CPU

CPU bedeutet **Central Processing Unit**. Auf Deutsch sagt man meistens **Prozessor**.

Die CPU verarbeitet Befehle und führt Berechnungen aus. Sie ist eine der wichtigsten Komponenten für die allgemeine Systemleistung.

Typische Aufgaben der CPU:

- Programme ausführen
- Berechnungen durchführen
- Betriebssystemprozesse bearbeiten
- Daten verarbeiten
- mehrere Aufgaben gleichzeitig koordinieren
- virtuelle Maschinen unterstützen
- Komprimierung und Verschlüsselung berechnen

Die CPU arbeitet eng mit RAM, Mainboard, Speicher und Betriebssystem zusammen.

---

## Wichtige CPU-Begriffe

| Begriff            | Bedeutung                                              |
| ------------------ | ------------------------------------------------------ |
| Kerne              | unabhängige Recheneinheiten innerhalb der CPU          |
| Threads            | logische Verarbeitungseinheiten für parallele Aufgaben |
| Taktfrequenz       | Geschwindigkeit in GHz                                 |
| Cache              | sehr schneller Zwischenspeicher in der CPU             |
| Architektur        | technischer Aufbau der CPU                             |
| TDP                | ungefährer Wärme- und Energiebedarf                    |
| integrierte Grafik | einfache Grafikeinheit direkt in der CPU               |
| Virtualisierung    | Unterstützung für virtuelle Maschinen                  |

Mehr Kerne helfen besonders bei mehreren Programmen, Virtualisierung, Kompilierung oder rechenintensiven Aufgaben.

Eine hohe Taktfrequenz hilft oft bei Aufgaben, die stark von einzelner CPU-Leistung abhängig sind.

---

## CPU-Kerne und Threads

Moderne Prozessoren haben mehrere Kerne.

Ein Kern kann Aufgaben bearbeiten. Mehrere Kerne ermöglichen, dass mehrere Prozesse parallel ausgeführt werden können.

Threads sind logische Ausführungseinheiten. Durch Technologien wie Hyper-Threading oder SMT kann ein Kern mehrere Threads bearbeiten.

Beispielhafte Bedeutung:

- 4 Kerne: einfache Büro- und Alltagsaufgaben
- 6 bis 8 Kerne: gute Leistung für viele Arbeitsplätze
- 12 oder mehr Kerne: Entwicklung, Virtualisierung, Workstations, rechenintensive Aufgaben

Die genaue Bewertung hängt aber immer vom Einsatzzweck ab.

---

## CPU-Auswahl im Unternehmen

Bei der Auswahl einer CPU achtet man auf:

- benötigte Leistung
- Anzahl der Kerne
- Energieverbrauch
- Wärmeentwicklung
- Virtualisierungsunterstützung
- Kompatibilität mit Mainboard und Chipsatz
- Lebensdauer des Systems
- Preis-Leistungs-Verhältnis

Für normale Büroarbeit reicht oft eine Mittelklasse-CPU. Für Virtualisierung, Entwicklung, CAD oder Datenanalyse wird mehr Leistung benötigt.

---

## RAM

RAM bedeutet **Random Access Memory**. Auf Deutsch sagt man **Arbeitsspeicher**.

Der RAM speichert Daten, die der Computer gerade aktiv verwendet. Programme, geöffnete Dateien und laufende Prozesse benötigen Arbeitsspeicher.

RAM ist sehr schnell, aber flüchtig. Das bedeutet: Wenn der Computer ausgeschaltet wird, gehen die Daten im RAM verloren.

---

## Warum RAM wichtig ist

Zu wenig RAM macht ein System langsam, weil das Betriebssystem Daten auf den Massenspeicher auslagern muss. Dieser Vorgang ist deutlich langsamer als direkter Zugriff auf RAM.

Typische Auswirkungen von zu wenig RAM:

- Programme starten langsam
- viele offene Tabs machen das System träge
- Wechsel zwischen Programmen dauert lange
- virtuelle Maschinen laufen schlecht
- das Betriebssystem nutzt Swap oder Auslagerungsdatei
- Programme können abstürzen oder einfrieren

---

## Wichtige RAM-Begriffe

| Begriff                | Bedeutung                                          |
| ---------------------- | -------------------------------------------------- |
| Kapazität              | Größe des RAM, zum Beispiel 8 GB, 16 GB oder 32 GB |
| DDR4 / DDR5            | Generation des Arbeitsspeichers                    |
| Takt / Geschwindigkeit | Datenrate des RAM                                  |
| Dual Channel           | RAM arbeitet über zwei Kanäle schneller            |
| ECC-RAM                | erkennt und korrigiert Speicherfehler              |
| SO-DIMM                | kleiner RAM-Typ für Laptops                        |
| DIMM                   | RAM-Typ für Desktop-PCs                            |

ECC-RAM wird vor allem bei Servern und Workstations eingesetzt, wenn hohe Zuverlässigkeit wichtig ist.

---

## RAM-Auswahl

Die passende RAM-Größe hängt von der Nutzung ab.

| Nutzung                      | Typischer RAM-Bedarf                       |
| ---------------------------- | ------------------------------------------ |
| einfache Büroarbeit          | 8 bis 16 GB                                |
| viele Programme gleichzeitig | 16 GB oder mehr                            |
| Entwicklung                  | 16 bis 32 GB                               |
| Virtualisierung              | 32 GB oder mehr                            |
| CAD, Grafik, Datenanalyse    | abhängig von Software, oft 32 GB oder mehr |

Für moderne IT-Arbeitsplätze sind 16 GB RAM häufig ein sinnvoller Standard.

---

## Massenspeicher

Massenspeicher speichert Daten dauerhaft.

Dort liegen zum Beispiel:

- Betriebssystem
- Programme
- Benutzerprofile
- Dokumente
- Bilder
- Videos
- Projektdaten
- virtuelle Maschinen
- Backups

Die wichtigsten Arten sind SSD und HDD.

---

## SSD

SSD bedeutet **Solid State Drive**.

Eine SSD speichert Daten elektronisch und hat keine beweglichen Teile. Dadurch ist sie deutlich schneller und robuster als eine klassische HDD.

Vorteile einer SSD:

- schneller Systemstart
- Programme starten schneller
- Dateien werden schneller geladen
- leiser Betrieb
- weniger empfindlich gegen Erschütterungen
- geringerer Stromverbrauch als viele HDDs

SSDs sind heute Standard für Arbeitsplatzcomputer.

---

## SATA-SSD und NVMe-SSD

Nicht jede SSD ist gleich schnell.

| SSD-Typ  | Erklärung                                            |
| -------- | ---------------------------------------------------- |
| SATA-SSD | nutzt SATA-Schnittstelle, deutlich schneller als HDD |
| NVMe-SSD | nutzt PCIe, sehr hohe Geschwindigkeit                |
| M.2      | Bauform, häufig für NVMe-SSDs genutzt                |

Eine NVMe-SSD ist besonders sinnvoll, wenn große Datenmengen verarbeitet werden oder viele Programme gleichzeitig arbeiten.

Für normale Büroarbeit reicht oft auch eine gute SATA-SSD, aber moderne Business-Geräte nutzen häufig NVMe.

---

## HDD

HDD bedeutet **Hard Disk Drive**.

Eine HDD speichert Daten magnetisch auf rotierenden Scheiben. Sie ist langsamer als eine SSD, aber oft günstiger bei sehr großen Speichermengen.

HDDs werden heute eher eingesetzt für:

- große Datenarchive
- Backups
- Netzwerkspeicher
- günstige Massenspeicherung
- ältere Systeme

Für das Betriebssystem eines Arbeitsplatzcomputers ist eine HDD heute meistens nicht mehr empfehlenswert.

---

## Wichtige Begriffe beim Speicher

| Begriff                | Bedeutung                                       |
| ---------------------- | ----------------------------------------------- |
| Kapazität              | Speichergröße, zum Beispiel 512 GB oder 1 TB    |
| Lesegeschwindigkeit    | wie schnell Daten gelesen werden                |
| Schreibgeschwindigkeit | wie schnell Daten gespeichert werden            |
| IOPS                   | Anzahl kleiner Ein-/Ausgabevorgänge pro Sekunde |
| Schnittstelle          | SATA, PCIe, USB                                 |
| Formfaktor             | 2,5 Zoll, M.2                                   |
| SMART                  | Überwachung von Laufwerkszustand                |
| Verschlüsselung        | Schutz gespeicherter Daten                      |

Für Unternehmensgeräte ist auch wichtig, ob die SSD Verschlüsselung und zuverlässige Zustandsüberwachung unterstützt.

---

## Grafikkarte

Die Grafikkarte berechnet die Bildausgabe.

Sie sorgt dafür, dass Inhalte auf dem Monitor dargestellt werden. Bei einfachen Büroaufgaben reicht oft eine integrierte Grafikeinheit aus.

Es gibt zwei Hauptarten:

| Art                    | Erklärung                                                      |
| ---------------------- | -------------------------------------------------------------- |
| integrierte Grafik     | Grafikchip ist in CPU oder Mainboard integriert                |
| dedizierte Grafikkarte | separate Grafikkarte mit eigener Leistung und eigenem Speicher |

---

## Wann braucht man eine starke Grafikkarte?

Eine starke Grafikkarte wird benötigt für:

- CAD-Anwendungen
- 3D-Modellierung
- Videoschnitt
- Grafikdesign
- KI-Berechnungen
- Simulationen
- mehrere hochauflösende Monitore
- spezielle technische Software

Für normale Büroarbeit, Browser, E-Mail und Office ist eine dedizierte High-End-Grafikkarte meistens nicht notwendig.

---

## VRAM

VRAM ist der eigene Speicher einer Grafikkarte.

Er wird für Grafikdaten verwendet, zum Beispiel:

- Texturen
- 3D-Modelle
- Videodaten
- hochauflösende Bilddaten
- Berechnungen auf der GPU

Je nach Anwendung kann VRAM sehr wichtig sein. Für einfache Büroarbeit spielt er kaum eine Rolle.

---

## Netzteil

Das Netzteil versorgt den Computer mit Strom.

Es wandelt Wechselstrom aus der Steckdose in die Spannungen um, die die Komponenten benötigen.

Ein Netzteil muss ausreichend Leistung liefern und stabil arbeiten.

Wichtige Punkte:

- Watt-Leistung
- Effizienz
- Schutzschaltungen
- Qualität der Spannungsversorgung
- Lautstärke
- passende Anschlüsse
- Bauform

Ein schlechtes Netzteil kann Instabilität verursachen oder im schlimmsten Fall andere Komponenten beschädigen.

---

## Effizienz beim Netzteil

Netzteile haben unterschiedliche Effizienzklassen.

Eine höhere Effizienz bedeutet, dass weniger Energie als Wärme verloren geht.

Vorteile effizienter Netzteile:

- weniger Stromverbrauch
- weniger Abwärme
- leisere Kühlung möglich
- oft bessere Qualität
- sinnvoll für Green IT

Im Unternehmensumfeld ist Effizienz wichtig, weil viele Geräte zusammen viel Strom verbrauchen können.

---

## Kühlung

Computerkomponenten erzeugen Wärme. Diese Wärme muss abgeführt werden.

Wichtige Kühlkomponenten:

- CPU-Kühler
- Gehäuselüfter
- Grafikkartenkühlung
- Wärmeleitpaste
- Luftstrom im Gehäuse
- Kühlkörper

Wenn ein System zu heiß wird, kann es langsamer werden oder sich abschalten. Dieses Heruntertakten nennt man Thermal Throttling.

---

## Bedeutung guter Kühlung

Gute Kühlung sorgt für:

- stabile Leistung
- längere Lebensdauer
- weniger Abstürze
- leiseren Betrieb
- zuverlässigen Dauerbetrieb

Staub, blockierte Lüfter oder schlechte Luftführung können die Kühlung stark verschlechtern.

Für Wartung ist es wichtig, Geräte regelmäßig auf Staub, Lüftergeräusche und Temperaturprobleme zu prüfen.

---

## Gehäuse

Das Gehäuse schützt die Komponenten und sorgt für Ordnung, Kühlung und Erweiterbarkeit.

Wichtige Eigenschaften:

- passende Größe für Mainboard und Komponenten
- gute Luftzirkulation
- ausreichend Platz für Laufwerke
- Frontanschlüsse
- Staubfilter
- Kabelmanagement
- einfache Wartung
- Stabilität

Bei Business-PCs sind Gehäuse oft kompakt und wartungsfreundlich. Bei Workstations ist mehr Platz für Kühlung und Erweiterung wichtig.

---

## Netzwerkkarte

Die Netzwerkkarte verbindet den Computer mit einem Netzwerk.

Es gibt kabelgebundene und drahtlose Verbindungen.

| Verbindung | Erklärung                        |
| ---------- | -------------------------------- |
| LAN        | Verbindung über Netzwerkkabel    |
| WLAN       | drahtlose Verbindung über Funk   |
| Bluetooth  | kurze Funkverbindung für Zubehör |

LAN ist meistens stabiler und schneller als WLAN. WLAN ist flexibler, aber stärker abhängig von Signalqualität, Entfernung und Störungen.

---

## Wichtige Netzwerkbegriffe am Arbeitsplatz

| Begriff     | Bedeutung                                      |
| ----------- | ---------------------------------------------- |
| Ethernet    | Standard für kabelgebundene Netzwerke          |
| RJ45        | typischer Anschluss für Netzwerkkabel          |
| WLAN        | drahtloses Netzwerk                            |
| MAC-Adresse | eindeutige Hardwareadresse einer Netzwerkkarte |
| IP-Adresse  | Adresse eines Geräts im Netzwerk               |
| DNS         | Namensauflösung im Netzwerk                    |
| DHCP        | automatische Vergabe von Netzwerkeinstellungen |

Diese Begriffe werden in LF3 noch deutlich wichtiger.

---

## Schnittstellen und Anschlüsse

Schnittstellen verbinden den Computer mit anderen Geräten.

Wichtige Anschlüsse:

| Anschluss      | Nutzung                                      |
| -------------- | -------------------------------------------- |
| USB-A          | Tastatur, Maus, USB-Stick, Drucker           |
| USB-C          | moderne Geräte, Laden, Daten, Docking        |
| Thunderbolt    | schnelle Datenübertragung, Docking, Monitore |
| HDMI           | Bild und Ton zum Monitor oder Beamer         |
| DisplayPort    | Bildausgabe, häufig bei Business-Monitoren   |
| RJ45           | kabelgebundenes Netzwerk                     |
| Audio          | Headset, Lautsprecher, Mikrofon              |
| SD-Kartenleser | Speicherkarten                               |

Bei der Auswahl eines Arbeitsplatzcomputers muss geprüft werden, ob genug passende Anschlüsse vorhanden sind.

---

## Dockingstation

Eine Dockingstation erweitert einen Laptop um zusätzliche Anschlüsse.

Typische Funktionen:

- Anschluss mehrerer Monitore
- LAN-Anschluss
- USB-Anschlüsse
- Stromversorgung über USB-C
- Audio-Anschluss
- Tastatur und Maus
- schnelle Verbindung zum Arbeitsplatz

Dockingstations sind besonders wichtig bei mobilen Arbeitsplätzen und Homeoffice.

Der Benutzer kann den Laptop schnell anschließen und wie an einem festen Arbeitsplatz arbeiten.

---

## Monitor

Der Monitor ist ein wichtiges Ausgabegerät.

Er beeinflusst Ergonomie, Arbeitskomfort und Produktivität.

Wichtige Kriterien:

| Kriterium         | Bedeutung                                         |
| ----------------- | ------------------------------------------------- |
| Größe             | typische Größen sind 24 bis 32 Zoll               |
| Auflösung         | Full HD, WQHD, 4K                                 |
| Paneltyp          | beeinflusst Farben, Blickwinkel und Reaktionszeit |
| Helligkeit        | wichtig bei hellen Räumen                         |
| Ergonomie         | höhenverstellbar, neigbar, drehbar                |
| Anschlüsse        | HDMI, DisplayPort, USB-C                          |
| Farbdarstellung   | wichtig für Grafik und Design                     |
| Bildwiederholrate | wichtig für flüssige Darstellung                  |

Für Büroarbeit sind zwei Monitore oft sinnvoll, weil mehrere Programme gleichzeitig sichtbar sein können.

---

## Tastatur und Maus

Tastatur und Maus sind Eingabegeräte.

Sie wirken einfach, sind aber für die tägliche Arbeit wichtig.

Wichtige Kriterien:

- ergonomische Form
- passende Größe
- angenehmer Tastenanschlag
- zuverlässige Verbindung
- kabelgebunden oder kabellos
- Zusatztasten
- einfache Reinigung
- Barrierefreiheit

Schlechte Eingabegeräte können die Arbeit verlangsamen oder langfristig gesundheitliche Probleme verursachen.

---

## Drucker und Scanner

Drucker und Scanner gehören oft zur Arbeitsplatzumgebung.

Wichtige Druckerarten:

| Druckerart          | Eigenschaften                              |
| ------------------- | ------------------------------------------ |
| Laserdrucker        | schnell, gut für viele Textdokumente       |
| Tintenstrahldrucker | gut für Fotos, oft höhere Verbrauchskosten |
| Multifunktionsgerät | Drucken, Scannen, Kopieren, oft Fax        |
| Netzwerkdrucker     | von mehreren Benutzern im Netzwerk nutzbar |

Wichtige Auswahlkriterien:

- Druckgeschwindigkeit
- Druckqualität
- Toner- oder Tintenkosten
- Duplexdruck
- Netzwerkfähigkeit
- Treibersupport
- Benutzerverwaltung
- Sicherheitsfunktionen
- Wartungsaufwand

Im Unternehmen ist besonders wichtig, dass Drucker zuverlässig, sicher und einfach verwaltbar sind.

---

## Barrierefreiheit

Barrierefreiheit bedeutet, dass IT-Systeme auch von Menschen mit Einschränkungen gut genutzt werden können.

Beispiele für barrierefreie Ausstattung:

- große Monitore
- Bildschirmvergrößerung
- Screenreader
- spezielle Tastaturen
- ergonomische Mäuse
- Spracheingabe
- Untertitel bei Kommunikationstools
- höhenverstellbare Arbeitsplätze

Barrierefreiheit ist nicht nur ein Zusatz, sondern kann notwendig sein, damit alle Mitarbeiter gut arbeiten können.

---

## Zusammenspiel der Komponenten

Die Leistung eines Computers hängt nicht nur von einer einzelnen Komponente ab.

Ein System ist immer nur so gut wie das Zusammenspiel der Komponenten.

Beispiele:

- Eine starke CPU bringt wenig, wenn zu wenig RAM vorhanden ist.
- Eine schnelle SSD verbessert Startzeiten und Programmstarts deutlich.
- Eine starke Grafikkarte ist für Büroarbeit oft unnötig, aber für CAD wichtig.
- Schlechte Kühlung kann gute Hardware ausbremsen.
- Zu wenige Anschlüsse können im Alltag stören.
- Ein schlechtes Netzteil kann ein System instabil machen.

Bei der Planung muss daher das Gesamtsystem betrachtet werden.

---

## Auswahl nach Einsatzbereich

Unterschiedliche Aufgaben brauchen unterschiedliche Hardware.

| Einsatzbereich   | Wichtige Komponenten                                           |
| ---------------- | -------------------------------------------------------------- |
| Büroarbeit       | stabile CPU, 16 GB RAM, SSD, gute Dockinglösung                |
| Entwicklung      | mehr RAM, schnelle CPU, große SSD, mehrere Monitore            |
| Virtualisierung  | viele CPU-Kerne, viel RAM, schnelle SSD                        |
| Grafik / CAD     | starke CPU, dedizierte GPU, viel RAM, guter Monitor            |
| Schulung / Labor | einfache Wartung, Standardhardware, schnelle Wiederherstellung |
| Thin Client      | Netzwerk, zentrale Serverdienste, geringe lokale Leistung      |

Die Auswahl sollte immer aus den Anforderungen abgeleitet werden.

---

## Typische Hardwareprobleme

| Problem                     | Mögliche Ursache                                   |
| --------------------------- | -------------------------------------------------- |
| Computer startet nicht      | Netzteil, Mainboard, RAM oder Stromversorgung      |
| System ist langsam          | zu wenig RAM, alte HDD, CPU-Auslastung             |
| Programme hängen            | RAM voll, Speicher langsam, Softwareproblem        |
| Monitor zeigt kein Bild     | Kabel, Eingang, Grafikkarte oder Monitor           |
| Netzwerk funktioniert nicht | Netzwerkkarte, Kabel, WLAN, IP-Konfiguration       |
| Gerät wird laut             | Lüfter, Staub, hohe Temperatur                     |
| System schaltet ab          | Überhitzung oder Stromproblem                      |
| Drucker funktioniert nicht  | Treiber, Netzwerk, Warteschlange oder Berechtigung |

Für FISI ist wichtig, Probleme logisch einzugrenzen und nicht wahllos Teile auszutauschen.

---

## Vorgehen bei Hardware-Auswahl

Eine sinnvolle Hardware-Auswahl läuft meistens in Schritten ab:

1. Anforderungen aufnehmen
2. Einsatzbereich bestimmen
3. Mindestanforderungen prüfen
4. passende Komponenten auswählen
5. Kompatibilität prüfen
6. Wirtschaftlichkeit bewerten
7. Sicherheit und Support prüfen
8. Lösung dokumentieren
9. System testen
10. Übergabe vorbereiten

Dieses strukturierte Vorgehen hilft, Fehlentscheidungen zu vermeiden.

---

## Praxisbeispiele

### Beispiel 1: Büroarbeitsplatz

Für einen normalen Büroarbeitsplatz sind eine zuverlässige CPU, 16 GB RAM, SSD, Dockingstation, Monitor, Tastatur, Maus und Sicherheitsfunktionen wichtiger als maximale Grafikleistung.

### Beispiel 2: Entwicklungsarbeitsplatz

Ein Entwicklungsarbeitsplatz benötigt oft mehr RAM, eine schnelle CPU, große SSD, mehrere Monitore und Unterstützung für Tools wie Git, virtuelle Maschinen oder Container.

### Beispiel 3: CAD-Arbeitsplatz

Ein CAD-Arbeitsplatz braucht meistens eine starke CPU, dedizierte Grafikkarte, viel RAM, schnelle SSD und einen hochwertigen Monitor.

---

## FISI-Bezug

Für Fachinformatiker für Systemintegration ist Hardwarewissen eine Grundlage.

Man muss Komponenten nicht nur benennen können, sondern verstehen, wie sie zusammenarbeiten und welche Bedeutung sie für Betrieb, Wartung und Fehlersuche haben.

In der Praxis muss ein FISI:

- Anforderungen analysieren
- passende Hardware auswählen
- Kompatibilität prüfen
- Systeme installieren
- Treiber und Firmware beachten
- Fehler eingrenzen
- Hardware dokumentieren
- Benutzer beraten
- wirtschaftliche Aspekte berücksichtigen

Ein guter IT-Arbeitsplatz ist nicht einfach der teuerste Computer, sondern ein sinnvoll geplantes Gesamtsystem.

---

## Typische Fehler bei der Planung

| Fehler                               | Problem                                     |
| ------------------------------------ | ------------------------------------------- |
| nur CPU-Leistung betrachten          | andere Engpässe werden übersehen            |
| zu wenig RAM einplanen               | System wird bei mehreren Programmen langsam |
| HDD statt SSD verwenden              | System fühlt sich langsam an                |
| Netzteil zu knapp wählen             | Instabilität möglich                        |
| Anschlüsse nicht prüfen              | Zubehör kann nicht genutzt werden           |
| Kühlung ignorieren                   | Leistung sinkt oder System wird laut        |
| keine Ersatzteile einplanen          | Wartung wird schwieriger                    |
| Benutzeranforderungen nicht beachten | Arbeitsplatz passt nicht zur Aufgabe        |

---

## Kurze Zusammenfassung

Ein Arbeitsplatzcomputer besteht aus vielen Komponenten, die zusammenarbeiten.

Wichtige Bauteile sind Mainboard, CPU, RAM, Massenspeicher, Grafikkarte, Netzteil, Kühlung, Gehäuse, Netzwerkkarte, Schnittstellen und Peripheriegeräte.

Für FISI ist entscheidend, die Funktion der Komponenten zu verstehen und sie passend zum Einsatzbereich auszuwählen.

Eine gute Hardware-Auswahl berücksichtigt Leistung, Kompatibilität, Sicherheit, Wartbarkeit, Wirtschaftlichkeit und den späteren Betrieb.
