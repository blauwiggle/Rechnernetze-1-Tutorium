---
marp: true
theme: default #uncover #gaia #default
class: invert
paginate: true
headingDivider: true
footer: "HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, 2020"
---

# Rechnernetze - Tutorium

# zu Kapitel 4

Link zu den Folien :arrow_down:
https://github.com/blauwiggle/Rechnernetze-1-Tutorium

---

<!--footer: "" -->

1. Welche Koppelelemente arbeiten auf welcher OSI-Schicht? Welche **_Veränderungen_** nimmt ein Switch an einem Rahmen vor? Benenne die Vor- und Nachteile der Netzkopplung mit Switches. Was versteht man unter einem **_Layer-7 Switch_**? Erläutere den Begriff **_Port Trunking_**.
2. Was versteht man unter **_Spanning-Tree_**? Wie funktioniert der **_Spanning-Tree Algorithmus_** zur Beseitigung von Schleifen im Netz?
3. **_Deep Packet Inspection_** (DPI). Argumentiere für und gegen das Verfahren.
4. Wie steht du zur **_Netzneutralität_**?
5. Zwei Stationen sind miteinander verbunden. Station 1 arbeitet mit **_Autonegotiation_**, bei Station 2 ist die **_Autonegotiation_** abgeschaltet (Duplex-Fehlanpassung). Beschreibe die Konsequenzen.

---

6. Erläutere die Begriffe **_Metrik_** und **_Autonomes System_**. Was versteht man unter **_Peering_**? Wozu benötigt man einen **_CIX_**?

---

# 1. Welche Koppelelemente arbeiten auf welcher OSI-Schicht? Welche **_Veränderungen_** nimmt ein Switch an einem Rahmen vor? Benenne die Vor- und Nachteile der Netzkopplung mit Switches. Was versteht man unter einem **_Layer-7 Switch_**? Erläutere den Begriff **_Port Trunking_**.

---

# Welche Koppelelemente arbeiten auf welcher OSI-Schicht?

- Repeater
- Hub
- Bridge
- Switch
- Multilayer Switch
- Router
- Gateway

---

| Layer          |      Repeater      |        Hub         |       Bridge       |       Switch       | Multilayer Switch  |       Router       |      Gateway       |
| -------------- | :----------------: | :----------------: | :----------------: | :----------------: | :----------------: | :----------------: | :----------------: |
| Application    |                    |                    |                    |                    | :white_check_mark: |                    | :white_check_mark: |
| Presentation   |                    |                    |                    |                    | :white_check_mark: |                    | :white_check_mark: |
| Session        |                    |                    |                    |                    | :white_check_mark: |                    | :white_check_mark: |
| Transport      |                    |                    |                    |                    | :white_check_mark: |                    | :white_check_mark: |
| Network        |                    |                    |                    |                    | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| Data Link      |                    |                    | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| Physical Layer | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |

---

# Repeater - OSI-Layer 1

- empfängt das Signal und sendet es in aufbereiteter Form weiter

---

# Hub - OSI-Layer 1

- keine Trennung der Kollisionsdomäne
  - Physikalisch ist es eine Sterntopologie
  - logisch ist es ein Bus
- Multiport Repeater
- sendet ein Signal an alle Ports weiter
- veraltet und wird fast nicht mehr eingesetzt

---

# Switch - OSI-Layer 2

- trennt Kollisionsdomänen
- treffen Weiterleitungsentscheidungen (FORWARD) anhand selbst gelernter MAC-Adressen (Source-Address-Table, SAT)
- SAT, besteht aus der MAC-Adresse und dem physikalischen Port (wo das Kabel drin steckt)

---

# Bridge - OSI-Layer 2

- gleiches Funktionsprinzip, nur veralteter Name
- aus Multiport Bridge wurde der bekannten Switch

---

# Switch/Bridge - Architekturen

| Verfahren   | Beschreibung                                                                               | Vorteile                                                     | Nachteile                                                                             |
| ----------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------------------------------- |
| Cut-Through | Der Switch leitet das Datenpaket sofort weiter, wenn er die Adresse des Ziels erhalten hat | Latenz zwischen Empfangen und Weiterleiten ist äußert gering | keine Erkennung fehlerhafter Datenpakete, werden trotzdem an Empfänger weitergeleitet |

---

| Verfahren         | Beschreibung                                                                         | Vorteile                                                                                  | Nachteile                                         |
| ----------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------- |
| Store and Forward | Gesamtes Paket wird vollständig eingelesen und nur bei Fehlerfreiheit weitergeleitet | Fehlerhafte Pakete werden herausgefiltert, daher gibt es vielfältige Filtermöglichkeiten | Relativ große Verzögerung, abhängig von der Größe |

---

| Verfahren          | Beschreibung                                                                                                                                    | Vorteile       | Nachteile                                                           |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ------------------------------------------------------------------- |
| Adaptive Switching | Es ist ein Mix aus Cut-Through und Store and Forward. Switch startet mit Store and Forward und schaltet bei wenigen Fehlern auf Cut Through um | sehr effizient | teuer                                                               |
| Fragment Free      | Der Switch liest die ersten 64 Byte des Frames ein und leitet dieses bei Fehlerfreiheit weiter                                                  | schnell        | Lässt fehlerhafte Pakete (fehlerhaft nach den ersten 64 Byte) durch |

---

# Router - OSI Layer 3

Ein Router leitet anhand von Metriken Daten weiter.

## Aufgaben

- Trennung von Netzsegmenten (Subnetze)
- Aufbau und Aktualisierung der Netztopologie
- Wegesuche
- Fragmentierung bei IPv4 (Anpassung der Daten an max. zulässige Layer-2 Paketlänge)
  - **_Wie hoch ist eine sehr bekannte MTU?_**

---

# Routing Tabelle

![bg right:70% fit](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/04_netstat.png?raw=true)

---

# Gateway

## Aufgaben

- Gateways konvertieren verschiedene Netzprotokolle
- Phillips Hue Lampen ZigBee <-> WLAN
- E-Mail zu Fax und umgekehrt

## Was ist mit dem Standard Gateway im Router?

- Keine Netzwerkprotokollkonvertierung
  - nur Weiterleitung von Nutzanfragen zwischen Subnetzen
- Ist im Computer als Adresse des Routers hinterlegt

---

# Welche **_Veränderungen_** nimmt ein Switch an einem Rahmen vor?

---

# Switch - OSI Layer 2

## Layer 2

- (fast) keine Veränderung am Rahmen
- verwirft ggf. Pakete
- kann VLAN-Tag an Rahmen anhängen

## Layer 3

- erst ab Layer 3 werden Veränderungen an Datenpaketen vorgenommen
  - durch Router
  - durch IP-Fragmentierung

---

# Benenne die **_Vor-_** und **_Nachteile_** der Netzkopplung mit Switches.

---

# Vorteile

- VLAN
- Puffer
- Sicherheit
- Datendurchsatz
- Reduzierung Netzlast
- Auftrennung von Kollisionsdomänen
- weniger Daten-Broadcasts als beim Hub

---

# Nachteile

- Latenz
- Spanning Tree Protocol (STP) bei mehreren Wegen notwendig
- Port Mirroring, aufwendige Suche benötigt

---

# Port Mirroring

Dabei wird Switch Port A and einen weiteren Port B gespiegelt. Dabei ist Port Mirroring ein Oberbegriff und hat verschiedene Namen bei den Herstellern. Bei Cisco Switched Port Analyzer (SPAN). Alle Pakete werden dabei kopiert und auf dem zweiten Port analysiert ohne den Verkehrt auf Port A nennenswert zu verlangsamen.

## Warum macht man das?

- um Diagnosen laufen zu lassen
- ein Debugging Tool zu verwenden
- einen Angriff abzuwehren

---

# Was versteht man unter einem **_Layer-7 Switch_**?

---

# Layer 7 Switch - OSI Layer 7

> Multilayer Switch

- Content Switching (URL- Adresse, Cookies, ...)
  - trifft Switching Entscheidungen auf Basis des Dateninhalts
- unterstützt Deep Packet Inspection (DP)

---

# Multilayer Switch - OSI Layer 2 und 3

> Erfüllt die Funktion eines Layer 2 Switch und eines Layer 3 Routers gleichzeitig

- Kann zwischen Netzen gleichzeitig switchen und routen
- geringere Latenz
- höherere Datendurchsatz

---

# Erläutere den Begriff **_Port Trunking_**.

---

- Port, an dem ein Switch zu einem anderem Switch Daten von jedem VLAN senden kann
- Switch fügt an den Frame VLAN-Tag Information für Zielswitch hinzu
- VLAN-Tag wird vom Zielswitch wieder entfernt

![bg right:50% 90%](https://www.thomas-krenn.com/de/wikiDE/images/d/d0/VLAN-Grundlagen-Beispiel-2.png)

> Bild Quelle: https://www.thomas-krenn.com/de/wiki/VLAN_Grundlagen

---

# 2.

# Was versteht man unter **_Spanning-Tree_**?

# Wie funktioniert der **_Spanning-Tree Algorithmus_** zur Beseitigung von Schleifen im Netz?

---

## Welches **Problem** soll gelöst werden?

- Pakete kreisen in Endlosschleifen im Netz
- Netzüberlastung und Ausfall der Netze

## **Warum** ist es notwendig?

- Redundante Wege in größeren Netzen
- höhere Ausfallsicherheit durch Alternativwege

## Welche **Lösung** gibt es?

- Baumstruktur (Spanning Tree) aufbauen und Deaktivieren von überschüssigen Verbindungen (Spanning Tree Algorithmus)

---

# Spanning Tree Protocol

![bg right:50% 90%](https://www.networxsecurity.de/wp-content/uploads/2019/03/Rstp.jpeg)

> Bild Quelle: https://www.networxsecurity.de/?page_id=4128

---

# Port Zustände STP

## Blocked

Alle Ports beginnen im Blocked Modus um Bridging Schleifen zu verhindern. Der Port bleibt im Blocked Modus, wenn STA bestimmt, dass es zur Root Bridge einen besseren Weg durch einen anderen Port gibt

---

## Listen/Learn

Der Port hört nur zu, versendet oder empfängt aber keine Nutzdaten. Nachrichten von anderen Ports werden aktiv erkannt und weiter verarbeitet.

## Forward

In diesem Stadum kann der Port Daten senden und empfangen. Nicht zulässig, wenn noch überflüssige Links vorhanden oder der Weg noch nicht eindeutig ist.

## Disabled

Der Port ist gesperrt.

---

# 3. **_Deep Packet Inspection_** (DPI). Argumentiere für und gegen das Verfahren.

---

| Vorteile                            | Nachteile                                    |
| ----------------------------------- | -------------------------------------------- |
| Filter                              | DSGVO schwierig                              |
| Spam / Malware bekämpfe             | Zensur                                       |
| Terror- und Kriminalitätsbekämpfung | Diskriminierung                              |
| Überwachung von Überlastkontrollen  | Eigennütziges Verhalten der Carrier/Provider |
| Netzwerkmanagement                  | Verletzung des Fernmeldegeheimnisses         |
| Reduzierung des Datenverkehrs       |                                              |

---

![bg blur](https://heise.cloudimg.io/width/1220/q50.png-lossy-50.webp-lossy-50.foil1/_www-heise-de_/imgs/18/2/1/9/2/0/9/3/urn-newsml-dpa-com-20090101-141007-99-05511_large_4_3-e4a51c58d810cd38-79d3703788a5efb1.jpeg)
![](#fff)

# IT-Sicherheit: Bundestag erlaubt Deep Packet Inspection und Netzsperren

## Provider dürfen künftig im Kampf gegen Netzstörungen "Steuerdaten" auswerten und Datenverkehr unterbinden. Anlass für die Gesetzesnovelle war eine EU-Richtlinie zur Netzsicherheit.

https://www.heise.de/newsticker/meldung/IT-Sicherheit-Bundestag-erlaubt-Deep-Packet-Inspection-und-Netzsperren-3699426.html

---

# 4. Wie stehst du zur **_Netzneutralität_**?

## Pro - Content Provider **VS** Contra - Carrier

---

| Pro - Content Provider                            | Contra - Carrier                        |
| ------------------------------------------------- | --------------------------------------- |
| Chancengleichheit                                 | Selbstbestimmung der Carrier            |
| Meinungsfreiheit                                  | Vermeidung von Engpässen                |
| Offenes Internet                                  | Mehr Geld für Netzausbau                |
| Kein eigennütziges Verhalten der Carrier/Provider | Diversität (Vielfältigkeit) an Diensten |

---

| Pro - Content Provider                                                          | Contra - Carrier                                    |
| ------------------------------------------------------------------------------- | --------------------------------------------------- |
| Keine Einschränkung/Diskriminierung :arrow_right: Zweiklassengesellschaft droht | Carrier generieren mehr Umsatz                      |
| Netzzugang, muss ein Grundrecht unserer Gesellschaft werden                     | Erhöhung der Netzqualität und Übertragungseffizienz |
| Innovationsfreudig                                                              | Erhöhung der Ausfalltoleranz                        |
| Wissenszugang unabhängig von der finanziellen Situation                         |                                                     |

---

# 5. Zwei Stationen sind miteinander verbunden. Station 1 arbeitet mit **_Autonegotiation_** (**_Auto-sensing_**), bei Station 2 ist die **_Auto-sensing_** abgeschaltet (Duplex-Fehlanpassung). Beschreibe die Konsequenzen.

---

# Auto-sensing

- 2 Stationen handeln das Übertragungsprotokoll aus
- Ziel, die schnellstmögliche Übertragungsgeschwindigkeit finden

---

# Autonegotiation ist abgeschaltet bei Station 2

# daraus folgt :arrow_down:

- Auto-sensing funktioniert nicht
- Station 1 erkennt Geschwindigkeit von Station 2
  - aber nicht ob Half- oder Full-Duplex
- Station 1 nimmt eine Duplex-Fehlanpassung vor und nimmt dann Half-Duplex
  - Kommunikation ist möglich, jedoch mit sehr vielen Kollisionen

# :exclamation: **_ineffizient_**

---

# 6.

# Erläutere die Begriffe **_Metrik_** und **_Autonomes System_**.

# Was versteht man unter **_Peering_**?

# Wozu benötigt man einen **_CIX_**?

---

# **_Metrik_**

> Entscheidungskriterium für die Wahl einer Route

- Zahl der Hops
- MTU
- Kosten
- Auslastung
- Bandbreite
- Laufzeit
- Fehlerrate der Verbindung
- Zuverlässigkeit der Verbindung

---

# **_Autonomes System_**

- Verbund von Routern und Netzen von Unternehmen und Organisationen
- Ansammlung von IP Netzen, die als Einheit definiert werden

---

# **_Peering_**

- Zusammenschluss von Computernetzwerken zum Datenaustausch unter Providern und Carrier

## Ort des Geschehens?

## An Internetknotenpunkten (**IX**, **I**nternet e**X**change)

- ist ein Peering Point
- arbeitet nicht gewinnorientiert

---

# **_CIX_**

## **CIX** - **C**ommercial **I**nternet e**X**change

- ist ein Peering Point
- weltweit größter steht in Frankfurt (DE-CIX)
- weltweit über 300 CIX

## **Wozu** benötigt man einen CIX?

- höhere Stabilität des Internets
- Ümleitung über andere Provider Netze möglich
- Kostengünstiger und schneller Datenverkehr

---

# Weitere Fragen?

Bitte per E-Mail an [mv068@hdm-stuttgart.de](mailto:mv068@hdm-stuttgart.de) oder auf GitHub direkt.

# Bis nächste Woche :smile:

> `git pull` nicht vergessen
