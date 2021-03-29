---
theme: uncover #uncover #default #gaia
class: invert
paginate: true
marp: true
headingDivider: true
footer: "HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, 2021"
---

# Rechnernetze - Tutorium

# zu Kapitel 1

Link zu den Folien :arrow_down:
https://github.com/blauwiggle/Rechnernetze-1-Tutorium

---

<!--footer: "" -->

1. Welche Vor- und Nachteile haben die Netzstrukturen Bus, Ring und Stern?
2. Welche Variante (Paket- oder Leitungsvermittlung) ist für welche Verkehrsarten geeignet? Welche Variante wird sich warum zukünftig durchsetzen?
3. Erläutere ...
   1. Die Begriffe LAN, MAN, WAN
   2. Welche Technologien wo bevorzugt eingesetzt werden
   3. Warum ein Schichtenmodell eingeführt wurde.
4. Vergleichen Leitungsvermittlung und Paketvermittlung unter folgenden Gesichtspunkten _Adressierung/Zeitdauer_ für die _Übertragung/Wegewahl_ zwischen Netzknoten.
5. Erläutere die Begriffe _verbindungslos_ und _verbindungsorientiert_.

---

6. Erläutere die Adressierungsarten und benenne Einsatzgebiete
   1. unicast
   2. multicast
   3. anycast
   4. broadcast
7. Wozu benötigt man das OSI-Modell? Beschreibe die Funktion der Schichten. Welches sind die Unterschiede zwischen dem OSI- und dem TCP/IP-Modell?
8. Warum benötigt man individuelle Adressierungsverfahren auf den OSI-Ebenen 2, 3 und 4?
9. Ein US-Carrier nennt sich Layer2-Communications. Was kann man aus dem Namen bezüglich der Geschäftsmodelle ableiten?
10. Welches Kapitel der Vorlesung beschäftigt sich mit welcher Layer.

---

# 1. Welche Vor- und Nachteile haben die Netzstrukturen Bus, Ring und Stern?

---

# Bus

### Vorteile

- einfach installier- und erweiterbar
- kurze Leitungen und geringe Kabelmengen

### Nachteile

- Netzausdehnung begrenzt
- Ausfallanfällig
- keine Alternativwege
- Nur eine Station kann Daten senden

---

# Ring

### Vorteile

- Alle Stationen wirken als Repeater, Überbrückung großer Entfernungen möglich
- Gleiche Zugriffsmöglichkeiten
- bei Ringunterbrechung sind trotzdem noch alle Teilnehmer erreichbar

### Nachteile

- Hoher Verkabelungsaufwand
- Langsam bei vielen angeschlossenen Endgeräten
- Relativ hohe Latenzen

---

# Stern

### Vorteile

- Leicht erweiterbar
- Hohe Ausfallsicherheit
- Leichte Fehlersuche
- Einfache Vernetzung

### Nachteile

- Netzausfall bei Ausfall/Überlastung der Zentrale (Hub/Switch)
- Hoher Kabelaufwand

---

# Welche weitere Topologien kennst du?

---

# Baum

### Vorteile

- Erweiterbar
- Große Entfernungen realisierbar
- Gut geeignet für Algorithmen

### Nachteile

- Bei Verteilerausfall ist gesamter Unterbaum nicht erreichbar
- Bei zunehmender Tiefe -> zunehmende Latenz

---

# Vermascht

### Vorteile

- Sicherste Variante
- Hohe Konnektivität
- Sehr leistungsfähig

### Nachteile

- Hoher Kabelaufwand

---

# 2. Welche Variante (Paket- oder Leitungsvermittlung) ist für welche Verkehrsarten geeignet? Welche Variante wird sich warum zukünftig durchsetzen?

---

# Paketvermittelt

- Aufteilung der Daten in Pakete
- Pakete enthalten Adressinformationen
- Freier Routenwahl der Pakete
- Eigent sich für zeitunkritische Übertragungen und Übertragungen mit über der Zeit schwankenden Lastprofilen (bessere Ausnutzung der Übertragungskapazitäten)

---

# Leitungsvermittelt

- Verbindungsaufbau für Dauer der Übertragung
  - Aufbau - Übertragung - Abbau
- Ständiger Kontakt
- Feste Bandbreite
- Geringe Verzögerungszeiten
- Gut für Echtzeitanwendungen

---

# Was wird sich durchsetzen?

---

# Paketvermittlung

Obwohl ...

- Pakete in falscher Reihenfolge ankommen können
- keine konstante Datenrate garantiert wird
- es zu Überlastungen an einzelnen Vermittlungsstationen kommen kann

Wieso dann?

- Effizientere Auslastung mehrere Nutzer/Dienster die gleichzeitig kommunizieren können
- Faire Aufteilung der Ressourcen unter den Teilnehmern
- Transparente Umleitung des Datenstroms möglich, bei Ausfall einer Vermittlungsstation

---

# 3. Erläutere ...

## 1. Die Begriffe LAN, MAN, WAN

## 2. Welche Technologien wo bevorzugt eingesetzt werden

## 3. Warum ein Schichtenmodell eingeführt wurde.

---

## 1. Räunliche Ausdehnung

- LAN - Local Area Network (Raum, Gebäude)
- MAN - Metropolitan Area Network (City-Netz)
- WAN - Wide Area Network (Weitverkehr, Internet)

---

## 2. Technologien in Netzen

- LAN - Ethernet, Wireless
- Access - xDSL, ISDN, Cable, Ethernet, Wireless
- Metro - SDH/SONET, Ethernet, Ringnetz nur DWDM
- WAN - SDH/SONET, Maschennetz mit DWDM

---

## 3. OSI

Das verschieben wir einfach mal auf Frage 7 :arrow_down:

---

# 4. Vergleichen Sie Leitungsvermittlung und Paketvermittlung unter folgenden Gesichtspunkten _Adressierung/Zeitdauer_ für die _Übertragung/Wegewahl_ zwischen Netzknoten.

---

Dabei kann es sich auch um Multiplexing einer Leitung handeln. Stell dir vor, dir werden 64 kBit / Sekunde zugeordnet, nachdem du dein mobiles Datenvolumen aufgebraucht hast. Übertragen wird jedoch innerhalb dieser Struktur beispielsweise mit LTE.

|              | Leitung                                               | Paket                                             |
| ------------ | ----------------------------------------------------- | ------------------------------------------------- |
| Adressierung | Provider schaltet eine direkte, physikalische Leitung | Jedes Paket beinhaltet die Ziel- und Quelladresse |
| Zeit         | konstant                                              | variiert                                          |
| Wegewahl     | konstante Route                                       | Route variiert (unter Umständen)                  |

---

# 5. Erläutere die Begriffe _verbindungslos_ und _verbindungsorientiert_.

---

## Verbindungslos

- kein Verbindungsaufbau, direkte Datenübertragung

Zum Beispiel IP.

## Verbindungsorientiert

1. Verbindungsaufbau
2. Datenübertragung
3. Verbindungsabbau

Zum Beispiel telefonieren.

---

# 6. Erläutere die Adressierungsarten und benenne Einsatzgebiete

## 1. unicast

## 2. multicast

## 3. anycast

## 4. broadcast

---

# unicast

![bg w:400 h:400 right](https://upload.wikimedia.org/wikipedia/commons/thumb/7/75/Unicast.svg/100px-Unicast.svg.png)

Ein Sender und ein Empfänger

Beispiel:

- Telefon

---

# multicast

![bg w:400 h:400 right](https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Multicast.svg/100px-Multicast.svg.png)

Ein Sender und mehrere Empfänger

Beispiele:

- Zoom
- BigBlueButton

---

# anycast

![bg w:400 h:400 right](https://upload.wikimedia.org/wikipedia/commons/thumb/4/43/Anycast.svg/100px-Anycast.svg.png)

Ein Sender ein beliebiger Empfänger innerhalb einer Gruppe

- Update von Routingtabellen
- Aktuell genutzt für DNS, soll in IPv6 stärker zum Einsatz kommen

---

# broadcast

![bg w:400 h:400 right](https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Broadcast.svg/100px-Broadcast.svg.png)

Ein Sender und alle empfangen

Beispiel:

- TV

---

# 3. Erläutere ...

## 3. Warum ein Schichtenmodell eingeführt wurde.

# 7. Wozu benötigt man das OSI-Modell? Beschreibe die Funktion der Schichten. Welches sind die Unterschiede zwischen dem OSI- und dem TCP/IP-Modell?

---

# Warum war es notwendig das OSI Modell zu entwerfen?

- Netze wurden immer größer
- Unterschiedliche Hard- und Software Lösungen waren untereinander nicht kompatibel
- keine einheitliche Lösung
- Modell zur Darstellung der Datenkommunikation
- Grundlage für Weiterentwicklungen und Normen

Dabei stellt jede Schicht der übergeordneten Schicht seine Dienste zur Verfügung und nimmt die Dienste der untergeordneten Schicht in Anspruch.

---

# OSI Layer

## Allgemein

---

| Layer | Type         | Dienste                                                                                        |
| ----- | ------------ | ---------------------------------------------------------------------------------------------- |
| 7     | Application  | Netzwerkdienste wie E-Mail, Datentransfer                                                      |
| 6     | Presentation | Übersetzer zwischen verschiedenen Datenformaten, Kompression, Verschlüsselung                  |
| 5     | Session      | regelt Ablauf einer Session, Sende- und Empfangsrecht, Dialogkontrolle, Prozesssynchronisation |
| 4     | Transport    | transparente Datenübertragung zwischen Endsystemen                                             |
| 3     | Network      | Adressierung und Wegewahl zwischen zwei Hosts, logische Netzstrukturierung                     |
| 2     | Data Link    | Datentransport über einen einzelnen Übermittlungsabschnitt                                     |
| 1     | Physical     | physikalischer Transport (Stecker, Strom, Spannung, etc.)                                      |

---

# OSI Layer

## Protokoll Beispiele und Koppelelement

---

| Layer                          | Protokoll Beispiel | Koppelelement           |
| ------------------------------ | ------------------ | ----------------------- |
| 7 - Anwendung (Application)    | HTTP, FTP, SSH     | Gateway, Content-Switch |
| 6 - Darstellung (Presentation) | JPEG, MP3, MPEG    | Gateway, Content-Switch |
| 5 - Sitzung                    | SIP, RTP, RTCP     | Gateway, Content-Switch |
| 4 - Transport (Transport)      | TCP, UDP           | Gateway, Content-Switch |
| 3 - Vermittlung (Network)      | IP, ICMP           | Router                  |
| 2 - Sicherung (Data Link)      | Ethernet           | Switch, Bridge          |
| 1 - Bitübertragung (Physical)  | :x:                | Repeater, Hub           |

---

# TCP/IP Modell

Das TCP/IP Modell dient zur Beschreibung der Kommunikation über das Internet.

![bg 90% right](https://www.guru99.com/images/1/102219_1135_TCPIPvsOSIM1.png)

---

# 8. Warum benötigt man individuelle Adressierungsverfahren auf den OSI-Ebenen 2, 3 und 4?

---

# Individuelle Adressierungen

- Logische Strukturierung
  - Jede Ebene bietet unterschiedliche Möglichkeiten zur Netzeinteilung
- Sicherheit
- Sockets
  - Mehrere verschiedene Verbindungen zwischen zwei Teilnehmern möglich
- Wenn nur eine Adressierung vorhanden
  - Riesige globale Routingtabellen

---

# 9. Ein US-Carrier nennt sich Layer2-Communications. Was kann man aus dem Namen bezüglich der Geschäftsmodelle ableiten?

---

![bg 50% right:30%](https://www.layer2communications.com/wp-content/uploads/2017/10/L2logo-2.jpg)

## Layer2 Communications

> Headquartered in Houston, Texas, Layer2 Communications, Inc. is an Internet Service Provider (ISP) and global technology aggregator specializing in data, internet, voice and hardware solutions. We collaborate with over 155 suppliers in more than 83 countries around the world to deliver private network solutions to help multi-location companies communicate with ease.

https://www.layer2communications.com/about-us/

---

## Layer2 Communications

- Bietet Dienstleistungen nah an der Hardware
- Liefert Metro-Ethernet-Dienste für Gebäudestandorte
- Arbeitet mit dem Ethernet-Protokoll

---

# 10. Welches Kapitel der Vorlesung beschäftigt sich mit welcher Layer.

| Kapitel   | Layer 1            | Layer 2            | Layer 3            | Layer 4            |
| --------- | ------------------ | ------------------ | ------------------ | ------------------ |
| Kapitel 2 | :white_check_mark: |                    |                    |                    |
| Kapitel 3 | :white_check_mark: |                    |                    |                    |
| Kapitel 4 |                    | :white_check_mark: |                    |                    |
| Kapitel 5 |                    | :white_check_mark: |                    |                    |
| Kapitel 6 |                    |                    | :white_check_mark: |                    |
| Kapitel 7 |                    |                    |                    | :white_check_mark: |

---

# Weitere Fragen?

Bitte per E-Mail an [cr099@hdm-stuttgart.de](cr099@hdm-stuttgart.de), [mv068@hdm-stuttgart.de](mailto:mv068@hdm-stuttgart.de) oder auf GitHub direkt. Wir beantworten die dann im kommenden Meeting ausführlich.

# Bis nächste Woche :smile:

> `git pull` nicht vergessen
