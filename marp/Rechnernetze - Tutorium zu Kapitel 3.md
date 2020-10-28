---
marp: true
theme: default #uncover #gaia #default
class: invert
paginate: true
headingDivider: true
footer: 'HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, 2020'
---

# Rechnernetze - Tutorium
# zu Kapitel 3

Link zu den Folien :arrow_down: 
https://github.com/blauwiggle/Rechnernetze-1-Tutorium

---

1. Ist das CSMA/CD-Verfahren ein **_faires_** Zugriffsverfahren?
2. Beschreibe, wie sich bei CSMA/CD-Ethernet Distanz, Paketlänge und Bitrate
gegenseitig beeinflussen.
3. Wie wird die **_Taktsynchronisation_** zwischen zwei Stationen bei Ethernet gelöst?
4. Warum werden die Signale im Ethernet **_codiert_** übertragen?
5. An welchem Grundproblem leidet Gigabit-Ethernet und wie wird dieses Problem gelöst? Beschreibe die Folgen. Was versteht man unter **_Skew Delay_**?

---

6. Erläuter die Begriffe **_Flow Control_** und **_Link Aggregation_**.
7. Metro Ethernet, ein großes aktuelles Thema in den Carrier Netzen. Beurteile die Eignung von Ethernet in Metro Netzen.
8. Ethernet Frames (10 MBit/s Ethernet) sollen mit Hilfe eines Protokoll Sniffers (z.B. dem in der Vorlesung eingesetzten Wireshark) *eingefangen* und ausgewertet werden. Wie viele Rahmen pro Sekunde sind maximal zu erwarten? Berechne die Rahmenrate einer Station in Abhängigkeit von der Größe der Payload (kleinster und größter Wert der Payload-Länge). Berechne auch den eigentlichen Datendurchsatz (ab Layer 3).

---

# Lass uns erstmal ein paar Dinge vorab klären.

## Wer führt Standards ein, was sind Zugriffsverfahren, was ist ein Multiplex :scream_cat:

---

# Organistationen in der Netzwerktechnik (Standards)

Es gibt etliche Organisationen, die an der Entwicklung von Standards beteilt sind.

- IANA - Internet Assigned Numbers Authority
- ICANN - Internet Corporation for Assigned Names and Numbers
- IETF - Internet Engineering Task Force
- ISO - International Organization for Standardization
- IEEE - Institute of Electrical and Electronics Engineers
- IEC - International Electrotechnical Commission
- ITU - International Telecommunication Union

---

- Für uns ist die IEEE hier besonders wichtig
- [RFCs](https://www.rfc-editor.org) (Request for Comments) schlagen Standards vor (nicht alle, nur einige)
    - IETF publiziert die RFCs
    - die Entwicklung des Internets wird vorangetrieben
    - die Genehmigung (als Stream bezeichnet) durchläuft verschiedene Stadien
    - fast alle wichtigen Internet Standards sind aus RFCs entstanden
        - [RFC 768 - UDP](https://www.rfc-editor.org/info/rfc768)
        - [RFC 1166 - IP Adresse](https://www.rfc-editor.org/info/rfc1166)


---

# 802.x beschäftigt sich mit lokalen Netzwerken
## Wichtige IEEE 802.x Standards
- 802.3 CSMA/CD
- 802.3u Fast Ethernet
- 802.3ab 1000 BASE-T
- 802.11 WLAN

---

# Zugriffsverfahren

---

## Zentralistisch
- Vermittlungsstelle organisiert Slot zur Datenübertragung

## Deterministisch
- Zugriff wird über Mechanismen geregelt, sodass keine Kollisionen auftreten können

## Nicht-Deterministisch
- Jede Station kann jederzeit zufällig senden
- Keine Regeln beim Senden (konkurrierend), bei Kollisionen wird erneut gesendet

---

# Was ist ein Multiplex?

---

![bg right:40% 90%](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Birch_plywood.jpg/800px-Birch_plywood.jpg)

Als Multiplex-Platten werden Furnier-Sperrholzplatten bezeichnet, welche mehr als 6,5 mm dick sind und aus mindestens fünf gleich starken Furnierlagen bestehen. Ist die Platte beidseitig mit Phenolharz beschichtet, so wird sie als Siebdruckplatte bezeichnet.

By Bystander - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=5863761

---

![bg fit](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/03_dafuq.jpg?raw=true)

---

# Multiplexverfahren sind Methoden zur Signal- und Nachrichtenübertragung. Dabei werden mehrere Signale gebündelt und übertragen.

---

## Raum Multiplex
- Übertragunskanäle werden zur parallelen Nutzung durch mehrere Sender und Empfänger gebündelt
    - Personen sprechen an verschiedenen Orten miteinander und stören sich bei genügend großem Abstand nicht.

---

## Frequenz Multiplex
- Die Signale werden in unterschiedliche Frequenz Bereiche getrennt
    - Eine Hundepfeife erzeugt unhörbare Geräusche. Nebenbei hörst du einen Podcast.

---

## Zeit Multiplex
- Signale werden zeitversertzt übertragen.
    - In der Ponyhof Schulklasse hat nur ein Sprecher gleichzeitig das Wort (asynchron). Auf der Google I/O hat jeder Redner einen Zeitslot bestimmter Länge (synchron).

---

## Code Multiplex
- Signale werden verschieden codiert
    - Wenn mehrere Gespräche in verschiedenen Sprachen in einem Raum stattfinden, hört man seine Muttersprache heraus. Bekannte Personen erkennt man am Klang ihrer Stimme

---

# Ethernet

- asynchrones Zeit Multiplex
- nach Bedarf
- dezentral
- konkurrierend

---

# 1. Ist das CSMA/CD-Verfahren ein **_faires_** Zugriffsverfahren?

---

![bg](https://cdn.dribbble.com/users/259812/screenshots/3131348/story_concept_800x600.jpg)

---

# Ja. 

## Da niemand beim Senden bevorzugt wird.

## Aber warum eigentlich?

---

# Für was steht CSMA/CD?

---

## CS - Carrier Sense (Träger Zustandserkennung)
Jede Station prüft, ob das Medium frei ist

## MA - Multiple Access (Mehrfachzugriff)
Mehrere Stationen teilen sich das Medium

## CD - Collision Detection (Kollisionserkennung)
Wenn mehrere Stationen gleichzeitig senden, erkennen sie die Kollision

---

# 2. Beschreibe, wie sich bei CSMA/CD-Ethernet Distanz, Paketlänge und Bitrate gegenseitig beeinflussen.

---

# :congratulations: (aka congratulations) der BEB Algorithmus ..

## .. ist nicht Prüfungsrelevant dieses Semester :raised_hands:

---

# Was jedoch wichtig ist, ist wie sich Distanz, Paketlänge und Bitrate gegenseitig beeinflussen.

## Hast du eine Idee, was es damit aufsich hat?

---

# Netzausdehnung und Laufzeitbudget
## Distanz, Paketlänge und Bitrate stehen im CSMA/CD Ethernet in direktem Zusammenhang!

---

## Beispiel
- Übertragungsgeschwindigkeit bei Ethernet mit 10 MBit / Sekunde
- Framelänge von 64 Byte (512 bit)

## Ziel
- Während des Sendens eine Kollision erkennen

---

# :fire: Formel - Zeitraum für die Kollisionserkennung

# $t_{frame}$ = $\frac{n\: [bit]}{b\: [\frac{bit}{s}]}$

# $t_{frame}$ = $\frac{(64 * 8)\: bit}{10*10^6\frac{bit}{s}} = 51,2\: µs$

## Das bedeutet, dass innerhalb von 51,2 µs die Kollision bei 10 MBit / Sekunde und einer Frame Größe von 64 Byte erkannt werden muss.

---

# Netzausdehnung und Laufzeitbudget

| Geschwindigkeit 	| Typ | Ausdehnung in Metern  	| Zeit  	|
|---:	    |:---:              |---:	            |---:	|
| 10 MBit  	| Ethernet  	    |* 5.000 Meter  	| 51,2 µs |
| 100 MBit  | Fast-Ethernet  	| 500 Meter             | 5,12 µs  	|
| 1.000 MBit| Gigabit-Ethernet  | 50 Meter              | 0,512 µs|

## * Kabeleigenschaften wie Dämpfung, Schirmung und Verarbeitungszeit begrenzen die maximale Ausdehnung auf 3.000 Meter. 

---

# 3. Wie wird die **_Taktsynchronisation_** zwischen zwei Stationen bei Ethernet gelöst?

---

# Präambel
- 7 Bytes
- dient der **_Takt Synchronisation_**
- alternierende Bitfolge *101010...1010*

# SFD
- 1 Byte
- auf diese folgt der Start Frame Delimiter (SFD) mit der Bitfolge *10101011*

Dann beginnt die MAC Adresse und somit der eigentliche Inhalt ...

---

# 4. Warum werden die Signale im Ethernet **_codiert_** übertragen?

---

# Codierte Übertragung

- Taktsynchronisation
- Vermeidung von großen Gleichstromanteil

![bg right:50% 90%](https://upload.wikimedia.org/wikipedia/commons/thumb/9/90/Manchester_encoding_both_conventions.svg/1024px-Manchester_encoding_both_conventions.svg.png)

Von Stefan Schmidt - Enhancement of Manchester Encoding, Gemeinfrei, https://commons.wikimedia.org/w/index.php?curid=1219799

---

# 5. An welchem Grundproblem leidet Gigabit-Ethernet und wie wird dieses Problem gelöst? Beschreibe die Folgen. 

---

# Problem
- es lässt Half-Duplex Verbindungen zu, daher wird
- CSMA/CD benötigt und es ist eine
- sehr geringe Längenausdehnung möglich
    - Zeit verkürzt sich, in der man Kollisionen erkennen kann

---

# Lösung
- Carrier-Extension
- Frame Bursting
- 4 Aderpaare Vollduplex
- Signalcodierung (PAM-5)

---

# PAM5 Signalcodierung

[Quelle itwissen.info und weitere Informationen zum PAM5 Verfahren](https://www.itwissen.info/PAM5-Verfahren-PAM5-method.html)

![bg right:50% 90%](https://www.itwissen.info/lex-images/pam5-codierung-mit-vier-bitkombinationen.png)

---

# Was versteht man unter **_Skew Delay_**?

---

# Skew Delay

- geringer Längenunterschied der Adernpaare im Twisted Pair Kabel
- gute Kabel haben eine kleine Skew Delay
- erfordert sorgfältiges *crimpen*
- hohe Qualitätsanforderungen an den Hersteller

---

# 6. Erläuter die Begriffe **_Flow Control_** und **_Link Aggregation_**.

---

# Flow Control (Flusssteuerung)
- Empfänger kann ein Pause Signal senden
    - falls der Sender zu viele Daten sendet
    - um einne Pufferüberlauf mit Datenverlust zu verhindern
- Verhinderung von Paketverlust
- Verhinderung von zu hoher Latenz

---

# Link Aggregation

- fast mehrere parallele Verbindungen zu einer logischen Verbindung zusammen
- einfaches Mittel um die Bandbreite und somit Datenrate zu vervielfachen

## Vorteile

- Ausfallsicherheit
- Lastverteilung
- Geringerer Konfigurations Aufwand (zum Beispiel nur eine IP-Adresse)

---

# 7. Metro Ethernet, ein großes aktuelles Thema in den Carrier Netzen. Beurteile die Eignung von Ethernet in Metro Netzen.

---

# Vorteile

- Skalierbar
- Quality of Service (QoS)
- Dienste
- Verfügbarkeit
- Verbindungsmanagement
- kostengünstig

---

# 8. Ethernet Frames (10 MBit/s Ethernet) sollen mit Hilfe eines Protokoll Sniffers (z.B. dem in der Vorlesung eingesetzten Wireshark) *eingefangen* und ausgewertet werden. Wie viele Rahmen pro Sekunde sind maximal zu erwarten? Berechne die Rahmenrate einer Station in Abhängigkeit von der Größe der Payload (kleinster und größter Wert der Payload-Länge). Berechne auch den eigentlichen Datendurchsatz (ab Layer 3).

---

# Paketlänge

## ${Umwandlung\:in\:Bit}$ = $\frac{10\:Mbit}{Sekunde}$ = $\frac{10.000.000\:Bit}{Sekunde}$

---

# Paketlänge (mit Präambel und Interframe Gap)

## ${Kleinster\: Payload}$ = $8 + 14 + 46 + 4 + 12$ = $84 \: byte$

## ${Größter\: Payload}$ = $8 + 14 + 1500 + 4 + 12$ = $1538 \: byte$

---

# Umwandlung der Paketlänge in Bit

## $84 \: byte * 8 = 672 \: bit$
## $1538 \: byte * 8 = 12304 \: bit$

---

# Rahmen pro Sekunde und Datendurchsatz bei 10 Mbit / Sekunde

## ${Kleinster\:Payload}$ = $\frac{10.000.000\:bit}{672\:bit}$ = $\frac{14.881\:Rahmen}{Sekunde}$

## ${Größter\:Payload}$ = $\frac{10.000.000\:bit}{12.304\:bit}$ = $\frac{813\:Rahmen}{Sekunde}$

---

# Datendurchsatz

## ${Kleinster\:Payload}$ = $\frac{14.881 * 46\:byte}{8\: (zurück \:zu \:byte)}$ = $\frac{684.625\:byte}{Sekunde}$

## ${Größter\:Payload}$ = $\frac{813 * 1500\:byte}{8}$ = $\frac{1.219.500\:byte}{Sekunde}$

---

# Weitere Fragen?

Bitte per E-Mail an [mv068@hdm-stuttgart.de](mailto:mv068@hdm-stuttgart.de) oder auf GitHub direkt.

# Bis nächste Woche :smile:

> ```git pull``` nicht vergessen