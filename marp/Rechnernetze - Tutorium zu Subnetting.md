---
marp: true
theme: default #uncover #gaia #default
class: invert
paginate: true
headingDivider: true
footer: "HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, 2020"
---

# Rechnernetze - Tutorium

# zu Subnetting

Link zu den Folien :arrow_down:
https://github.com/blauwiggle/Rechnernetze-1-Tutorium

---

<!--footer: "" -->

# Fragen per E-Mail

- Übung "Subnetting Kommunikationsfluss": Skript Kapitel 3, Seite 40
- Übung "Longest Match Routing": Skript Kapitel 3, Seite 45
- Übung "Interpretation der Routing-Tabelle eines Hosts": Skript Kapitel 3, Seite 47

---

## Fall 1 mit /24

$A-Switch-B$ funktioniert
$A-Router-C$ funktioniert

## Fall 2 mit /16

$A-Switch-B$ funktioniert
$A-Router-C$ funktioniert nicht, da A denkt, dass C in seinem Subnetz ist und das Paket nicht an den Router sendet

![bg fit right:50%](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/05_frage_1.JPG?raw=true)

---

![bg fit](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/05_frage_2.JPG?raw=true)

---

| Route |       IP       |          |          |          |          | Match  |
| :---: | :------------: | :------: | :------: | :------: | :------: | :----: |
|       | 174.16.0.10/32 | 10101110 | 00010000 | 00000000 | 00001010 |        |
|   1   | 174.16.0.0 /12 | 10101110 | 00010000 | 00000000 | 00000000 | 12 Bit |
|   2   | 174.16.0.0 /18 | 10101110 | 00010000 | 00000000 | 00000000 | 18 Bit |
|   3   | 174.16.0.0 /27 | 10101110 | 00010000 | 00000000 | 00000000 | 27 Bit |
|   4   |  0.0.0.0 /12   | 00000000 | 00000000 | 00000000 | 00000000 | 0 Bit  |

## Route 3, mit 27 Bit Übereinstimmung wird genommen.

---

![bg fit](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/05_frage_3.JPG?raw=true)

---

- a) 141.62.66.177
- b) 141.62.66.250
- c) 224.0.0.0 ist ein Multicast Adressbereich, das bedeutet, dass ein Paket einfach ins Subnet abgegeben wird und irgendeine Instanz das Multicast Paket annimmt
- d) Ping auf ..
  google.de -> Netzwerkziel 209.85.129.147 -> Gateway 141.62.66.251
  google.com -> Netzwerkziel 209.85.129.99 -> kein Eintrag vorhanden, also 0.0.0.0 -> Gateway 141.62.66.250
- e) Ping zu ..
  127.0.0.1 -> Netzwerkziel 127.0.0.0 (Netz ID) -> Gateway 127.0.0.1 -> Schnittstelle 127.0.0.1 (der Ping verlässt das Netzwerk nicht)
  141.62.66.177 -> Netzwerkziel 141.62.66.177 -> Gateway 127.0.0.1 (Ping verlässt Netzwerk nicht)

---

# Weitere Fragen?

Bitte per E-Mail an [mv068@hdm-stuttgart.de](mailto:mv068@hdm-stuttgart.de) oder auf GitHub direkt.

# Bis nächste Woche :smile:

> `git pull` nicht vergessen
