---
marp: true
theme: default #uncover #gaia #default
class: invert
paginate: true
headingDivider: true
footer: 'HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, 2020'
---

# Rechnernetze - Tutorium
# zu Vernissage SS 2020

Link zu den Folien :arrow_down: 
https://github.com/blauwiggle/Rechnernetze-1-Tutorium

---

# Aufgabe - Gruppe 1 (A und B)

Während der Entwurfsphase einer (fiktiven) neuen Netzwerkstruktur für die HdM stellt sich heraus, dass für Studiengänge, Abteilungen und erforderliche Reserven insgesamt 50 Subnetze benötigt werden. Die zur Verfügung stehende offizielle - im Internet bekannte Adresse - lautet **141.62.0.0**

---

1. Wieviele Stellen der Subnetzmaske müssen minimal reserviert werden?
2. Wie lautet die Subnetzmaske in der binären und dezimalen Schreibweise?
3. Wie viele Subnets können mit dieser Maske maximal adressiert werden?
4. Wieviele IP-Geräte sind pro Subnetz adressierbar?
5. Welcher Teil der IP-Adresse 141.62.13.13 ist für Router im Internet interessant?
6. Wie lautet im Beispiel die Netzwerk-Adresse für die IP-Adresse 141.62.13.200 ?

---

# 1. Wieviele Stellen der Subnetzmaske müssen minimal reserviert werden?

1. 50 Subnetze werden benötigt, ${2^5}$ sind 32 Subnetze ${2^6}$ sind 64 Subnetze.
2. Du nimmst ${2^6}$, weil dort die 50 Subnetze enthalten sind.
3. Weil die ersten beiden Byte 141.62. nicht verändert werden können, rechnest du ${8 (141)+8 (62)+6({2^6})}$ und kommst auf `/22` im 3. Oktett als `Netzanteil`.

---

# 2. Wie lautet die Subnetzmaske in der binären und dezimalen Schreibweise?

## $normal = 255.255.252.0$
## $binär = 11111111.11111111.11111100.00000000$
## $hexadezimal = FF.FF.FC.00$
## $dezimal = 4294966272$

---

# 3. Wie viele Subnets können mit dieser Maske maximal adressiert werden?

## ${2^6}$ sind 64 Subnetze

---

# 4. Wieviele IP-Geräte sind pro Subnetz adressierbar?

1. Wir haben den Netzanteil bereits ausgerechnet und kommen auf /22.
2. Du weißt, dass eine IPv4 32 bit hat.
3. Jetzt rechnest du $32 bit - 22 bit = 10 bit$ für den Hostanteil
4. ${2^{10}} = 1024 - 2 (Netz ID + BC) = 1022$ IP Geräte die pro Subnetz adressierbar sind.

---

# 5. Welcher Teil der IP-Adresse 141.62.13.13 ist für Router im Internet interessant?

## Die ersten zwei Oktets 141.62/22.

---

# 6. Wie lautet im Beispiel die Netzwerk-Adresse für die IP-Adresse 141.62.13.200 ?

---

## NA - Netz Adresse / ID: 141.62.0.0
## SM - Subnetzmaske: 255.255.252.0

|   IP  	| SM 1er = Netzanteil 	| SM 1er = Netzanteil 	| SM 1er = Subnetzanteil 	|          	|   Netz ID  	|
|:-----:	|:-------------------:	|:-------------------:	|:----------------------:	|:--------:	|:----------:	|
|   NA  	|       10001101      	|       00111110      	|        00000000        	| 00000000 	|            	|
|   SM  	|       11111111      	|       11111111      	|        111111-00       	| 00000000 	|            	|
| 1. NA 	|       11000000      	|       00111110      	|        000000-00       	| 00000000 	|  141.62.0  	|
| 2. NA 	|       11000000      	|       00111110      	|        000001-00       	| 00000000 	|  141.62.4  	|

---

|   IP  	| SM 1er = Netzanteil 	| SM 1er = Netzanteil 	| SM 1er = Subnetzanteil 	|          	|   Netz ID  	|
|:-----:	|:-------------------:	|:-------------------:	|:----------------------:	|:--------:	|:----------:	|
| 3. NA 	|       11000000      	|       00111110      	|        000010-00       	| 00000000 	|  141.62.8  	|
| 4. NA 	|       11000000      	|       00111110      	|        000011-00       	| 00000000 	|  141.62.12 	|
| n. NA 	|       11000000      	|       00111110      	|        111111-00       	| 00000000 	| 141.62.252 	|

---

# Schrittweite

## Die Schrittweite zu erkennen, erspart dir viel Rechnerei.

> Du musst hier auf das letzte Bit,
> des Subnetzanteils im 3. Oktett achten `000000-00`

:exclamation: Das ist hier 4, daher ist die Schrittweite immer 4 :arrow_right: 0, 4, 8, 12, 16 .. 252 :ok:

## Die IP 141.62.13.200 hat die Netz ID 141.62.12.0 mit der Broadcast Adresse 141.62.15.255, weil sie leicht erkennbar dazwichen liegt und übrigens eine IP von den oben genannten 1022 IPs von diesem Subnetz ist.

---

# Aufgabe - Gruppe 2 (C und D)

Untersuchen Sie nachfolgende IP-Adressen. Welche der Adressen können als Rechneradresse genutzt werden?

- 192.168.28.33 / 28
- 192.168.28.112 / 28
- 192.168.28.175 / 28

---

# Anleitung

> Ziel :arrow_right: Netz ID und BC bestimmen.

1. IP binär schreiben
2. /28 (255.255.255.240) binär schreiben


---


# 192.168.28.33 / 28

|  Netz ID 	|          	|           	|          	|
|:--------:	|:--------:	|:---------:	|:--------:	|
| 11000000 	| 10101000 	| 000111000 	| 00100001 	|
|   + AND  	|          	|           	|          	|
| 11111111 	| 11111111 	|  11111111 	| 11110000 	|
|     =    	|          	|           	|          	|
| 11000000 	| 10101000 	| 000111000 	|  0010000 	|
|    192   	|    168   	|     28    	|    32    	|

## Ja, die IP ist gültig.

---

# 192.168.28.112 / 28

|  Netz ID 	|          	|           	|          	|
|:--------:	|:--------:	|:---------:	|:--------:	|
| 11000000 	| 10101000 	| 000111000 	| 01110000 	|
|   + AND  	|          	|           	|          	|
| 11111111 	| 11111111 	|  11111111 	| 11110000 	|
|     =    	|          	|           	|          	|
| 11000000 	| 10101000 	| 000111000 	|  0111000 	|
|    192   	|    168   	|     28    	|    112   	|

## Nein, die IP ist nicht gültig für einen Host, da es die Netz ID ist.

---

# 192.168.28.175 / 28

## long story short, es ist nicht die Netz ID, also passt es ja.

---

# Oder nicht?

:exclamation: Broadcast Adresse checken, wenn es nicht die Netz ID ist.

---

| Broadcast 	|          	|              	|              	|
|:---------:	|:--------:	|:------------:	|:------------:	|
|  11000000 	| 10101000 	|   000111000  	|   10101111   	|
|    + OR   	|    mit   	| invertierter 	| Subnetzmaske 	|
|  00000000 	| 00000000 	|   00000000   	|   00001111   	|
|     =     	|          	|              	|              	|
|  11000000 	| 10101000 	|   000111000  	|   10101111   	|
|    192    	|    168   	|      28      	|      175     	|

## Nein, die IP ist nicht gültig für einen Host, da es die BC ist.

---

# Aufgabe - Gruppe 3 (E und F)

Ergänzen Sie für die angegebenen Subnetzmasken die fehlenden Broadcastadressen für die IP 9.5.2.30.

| Subnetzmaske  	| Broadcastadresse 	|
|---------------	|------------------	|
| 255.0.0.0     	| 9.255.255.255    	|
| 255.255.0.0   	| 9.5.255.255      	|
| 255.255.255.0 	| 9.5.2.255        	|
| 255.255.192.0 	| 9.5. ???         	|
| 255.255.224.0 	| 9.5. ???         	|

---

# Anleitung

1. IP binär schreiben
2. Subnetzmaske invertiert (auch Wildcard genannt) binär schreiben
3. Logische OR Verknüpfung anwenden

| Subnetzmaske  	| Broadcastadresse 	|
|---------------	|------------------	|
| 255.0.0.0     	| 9.255.255.255    	|
| 255.255.0.0   	| 9.5.255.255      	|
| 255.255.255.0 	| 9.5.2.255        	|
| 255.255.192.0 	| 9.5.63.255       	|
| 255.255.224.0 	| 9.5.31.255       	|

---

# Aufgabe - Gruppe 4 (G und H)

Geben Sie für die nachfolgende IP Adresse an.

- Netzklasse
- Subnetz Netz ID
- Subnetz Broadcast Adresse

## IP: 193.174.24.180
## SN: 255.255.255.240

---

# Netzklasse

## Klasse C geht von 192.0.0.0 bis 223.255.255.255, also ist es eine Klasse C IP.

---

# Anleitung - Netz ID bestimmen

1. IP binär schreiben
2. Subnetzmaske binär schreiben
3. Logische AND Verknüpfung anwenden

---

# Lösung - Netz ID bestimmen

## Netz ID 193.174.24.176

---

# Anleitung - Broadcast Adresse bestimmen

1. IP binär schreiben
2. Subnetzmaske invertiert (auch Wildcard genannt) binär schreiben
3. Logische OR Verknüpfung anwenden

---

# Lösung - Broadcast Adresse bestimmen

## 193.174.24.191

---

# Aufgabe - Gruppe 5 (I und J)

Bestimmen Sie die Subnetz-ID und die Broadcast-Adresse für das Subnetz, zu dem nachfolgende Adresse gehört:

- 200.200.200.45 / 27

---

# Anleitung - Subnetz ID bestimmen

1. IP binär schreiben
2. Subnetzmaske /27 (255.255.255.224) binär schreiben
3. Logische AND Verknüpfung anwenden

---

# Lösung - Subnetz ID bestimmen

## 200.200.200.32

---

# Anleitung - Broadcast Adresse bestimmen

1. IP binär schreiben
2. Subnetzmaske /27 (255.255.255.224) invertiert (Wildcard) binär schreiben
3. Logische OR Verknüpfung anwenden

---

# Lösung Broadcast Adresse bestimmen

## 200.200.200.63

---

# Weitere Fragen?

Bitte per E-Mail an [mv068@hdm-stuttgart.de](mailto:mv068@hdm-stuttgart.de) oder auf GitHub direkt.

# Bis nächste Woche :smile:

> ```git pull``` nicht vergessen