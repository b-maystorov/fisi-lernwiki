# 3.6 Netzwerkfunktion prüfen und warten

In diesem Kapitel geht es darum, Netzwerkverbindungen, Netzwerkdienste und Netzwerkkomponenten zu prüfen, Fehler systematisch einzugrenzen und den laufenden Betrieb zu warten.

Ein Netzwerk muss nicht nur eingerichtet werden. Es muss dauerhaft zuverlässig, sicher und nachvollziehbar funktionieren. Dafür sind regelmäßige Prüfungen, Monitoring, Wartung, Dokumentation und strukturierte Fehlersuche notwendig.

Für Fachinformatiker für Systemintegration ist dieses Thema besonders wichtig, weil Netzwerkstörungen häufig viele Benutzer gleichzeitig betreffen können.

---

## Kurz erklärt

Netzwerkprüfung bedeutet, zu kontrollieren, ob Verbindungen, Dienste und Konfigurationen korrekt funktionieren.

Netzwerkwartung bedeutet, ein Netzwerk dauerhaft funktionsfähig, sicher und aktuell zu halten.

Dazu gehören:

- Verbindung testen
- IP-Konfiguration prüfen
- DNS und DHCP kontrollieren
- Erreichbarkeit von Servern testen
- Netzwerkgeräte überwachen
- Logs auswerten
- Updates und Firmware prüfen
- Dokumentation aktuell halten
- Störungen analysieren
- Sicherheitsstatus kontrollieren

Ein funktionierendes Netzwerk ist die Grundlage für fast alle IT-Dienste im Unternehmen.

---

## Warum Netzwerkprüfung wichtig ist

Viele IT-Probleme wirken für Benutzer gleich:

> “Das Internet geht nicht.”  
> “Der Server ist nicht erreichbar.”  
> “Der Drucker funktioniert nicht.”  
> “Die Anmeldung klappt nicht.”

Die Ursachen können aber sehr unterschiedlich sein.

Mögliche Ursachen:

- Netzwerkkabel defekt
- WLAN-Signal zu schwach
- falsche IP-Adresse
- DHCP funktioniert nicht
- DNS löst Namen nicht auf
- Gateway ist nicht erreichbar
- Firewall blockiert Verbindung
- Serverdienst läuft nicht
- Benutzerrechte fehlen
- Switch-Port ist falsch konfiguriert
- VLAN ist falsch zugeordnet

Deshalb muss ein FISI systematisch prüfen und nicht zufällig Einstellungen ändern.

---

## Systematische Fehlersuche

Eine strukturierte Fehlersuche hilft, Probleme schneller einzugrenzen.

Eine einfache Reihenfolge ist:

| Schritt | Prüfung                     |
| ------- | --------------------------- |
| 1       | Physische Verbindung prüfen |
| 2       | Linkstatus kontrollieren    |
| 3       | IP-Konfiguration prüfen     |
| 4       | Gateway testen              |
| 5       | DNS testen                  |
| 6       | Zielsystem prüfen           |
| 7       | Port oder Dienst prüfen     |
| 8       | Firewall und Rechte prüfen  |
| 9       | Logs auswerten              |
| 10      | Dokumentation vergleichen   |

Diese Reihenfolge orientiert sich grob am OSI-Modell: Man beginnt unten bei der physischen Verbindung und arbeitet sich nach oben zur Anwendung.

---

## Physische Verbindung prüfen

Die physische Verbindung ist die Grundlage jeder Netzwerkkommunikation.

Bei LAN sollte geprüft werden:

- Ist das Netzwerkkabel eingesteckt?
- Ist das Kabel beschädigt?
- Leuchten Link-LEDs an Netzwerkkarte oder Switch?
- Ist der richtige Switch-Port genutzt?
- Ist der Port aktiv?
- Ist das Patchkabel korrekt verbunden?
- Ist die Netzwerkdose korrekt gepatcht?
- Funktioniert ein anderes Kabel?
- Funktioniert ein anderer Port?

Bei WLAN sollte geprüft werden:

- Ist WLAN aktiviert?
- Ist die richtige SSID ausgewählt?
- Ist das Passwort korrekt?
- Ist das Signal stark genug?
- Gibt es Störungen?
- Ist der Access Point erreichbar?
- Ist das Gerät im richtigen WLAN oder Gastnetz?

Viele Fehler entstehen schon auf dieser grundlegenden Ebene.

---

## Linkstatus

Der Linkstatus zeigt, ob eine physische Netzwerkverbindung besteht.

Bei einer kabelgebundenen Verbindung bedeutet ein aktiver Link meistens:

- Netzwerkkarte erkennt Verbindung
- Switch-Port erkennt Verbindung
- elektrische Verbindung besteht
- Geschwindigkeit wurde ausgehandelt
- Duplex-Modus wurde ausgehandelt

Ein Link bedeutet aber noch nicht, dass IP, DNS oder Dienste funktionieren. Er zeigt nur, dass die lokale Verbindung auf physischer Ebene grundsätzlich aktiv ist.

---

## IP-Konfiguration prüfen

Ein Client braucht eine gültige IP-Konfiguration.

Wichtige Werte:

| Wert                  | Bedeutung                                |
| --------------------- | ---------------------------------------- |
| IP-Adresse            | Adresse des Clients                      |
| Subnetzmaske / Präfix | beschreibt das lokale Netzwerk           |
| Standardgateway       | Weg in andere Netzwerke                  |
| DNS-Server            | zuständig für Namensauflösung            |
| DHCP-Status           | automatische oder manuelle Konfiguration |

Typische Fehler:

- keine IP-Adresse
- APIPA-Adresse bei Windows
- falsche statische IP-Adresse
- falsche Subnetzmaske
- falsches Gateway
- falscher DNS-Server
- IP-Adresskonflikt
- Client im falschen VLAN

Eine falsche IP-Konfiguration kann dazu führen, dass lokale Kommunikation funktioniert, aber Internet oder Serverzugriff nicht möglich ist.

---

## APIPA

APIPA bedeutet **Automatic Private IP Addressing**.

Wenn ein Windows-Client keine Adresse per DHCP bekommt, kann er sich selbst eine Adresse aus dem Bereich `169.254.0.0/16` geben.

Beispiel:

```text
169.254.23.81
```
