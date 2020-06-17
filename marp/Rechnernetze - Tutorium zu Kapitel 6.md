---
marp: true
theme: default #uncover #gaia #default
class: invert
paginate: true
headingDivider: true
footer: 'HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, 2020'
---

# Rechnernetze - Tutorium
# zu Kapitel 6
## 24. Juni 2020

Link zu den Folien :arrow_down: 
https://github.com/blauwiggle/Rechnernetze-1-Tutorium

---

1. Erläutere das Prinzip der IP Fragmentierung. Wer fragmentiert warum und wie? Wer setzt die Fragmente wieder zusammen?
2. Welche Vorteile hat der Einsatz von IPv6? Welche Hindernisse bei der Migration siehst du? Durch welche Ansätze versucht IPv6 die Veerarbeitungsgeschwindigkeit in Routern zu erhöhen?
3. Grenze MTU und MSS voneinander ab.
4. Definiere die Begriffe Root Name Server, DNS Prefetching und DNS Round Robin.
5. Erläutere den Aufbau des TCP Rahmens und die Funktion der einzelnen Felder.
6. Erläutere die Begriffe Port und Socket, Three Way Handshake, ISN, Sliding Windows und Piggybacking.

---

7. Beschreibe den Einsatz der TCP Flags.
8. Wie erkennen und reagieren TCP und UDP auf ...
    - in falscher Reihenfolge zugestellte Pakete
    - Paketverlust und Paketverdopplung
    - fehlerhaft adressierte Ports
9. Was versteht man unter der TCP Flusssteuerung?
10. Erläutere das in der Vorlesung vorgestellte TCP Zustanddiagramm.
11. Markiere die Felder des IP und TCP Header, die nach erfolgreichem Verbindungsaufbau während der Phase der Datenübertragung über das Internet nicht konstant bleiben.

---

# 1. 
# Erläutere das Prinzip der IP Fragmentierung. 
# Wer fragmentiert warum und wie? 
# Wer setzt die Fragmente wieder zusammen?

---

# 2. 
# Welche Vorteile hat der Einsatz von IPv6?
# Welche Hindernisse bei der Migration siehst du?
# Durch welche Ansätze versucht IPv6 die Veerarbeitungsgeschwindigkeit in Routern zu erhöhen?

---

# 3. Grenze MTU und MSS voneinander ab.

---

# 4. Definiere die Begriffe 

## Root Name Server
## DNS Prefetching
## DNS Round Robin.

---

# 5. Erläutere den Aufbau des TCP Rahmens und die Funktion der einzelnen Felder.

---

# 6. Erläutere die Begriffe 

## Port und Socket
## Three Way Handshake
## ISN
## Sliding Window
## Piggybacking

---

# 7. Beschreibe den Einsatz der TCP Flags.

Lass uns mal eine Tabelle füllen.

---

| TCP Flag 	|             	| Beschreibung                                                    	|
|----------	|-------------	|-----------------------------------------------------------------	|
| SYN      	| Synchronize 	| Verbindungsanforderung wird gesendet                            	|
| ACK      	| Acknowledge 	| Empfänger bestätigt den Erhalt der Daten                        	|
| FIN      	| Final       	| Verbindungsabbau wird eingeleitet                               	|
| RST      	| Reset       	| Abbruch einer Sitzung / Ablehnung einer Verbindungsanforderung  	|
| URG      	| Urgent      	| Pointer, welcher auf dringende Daten zeigt, dadurch Bevorzugung 	|
| PSH      	| Push        	| Daten sofort an höhere Protokolle (Layer) weiterleiten          	|

---

# 8. Wie erkennen und reagieren TCP und UDP auf ...
- ## in falscher Reihenfolge zugestellte Pakete
- ## Paketverlust und Paketverdopplung
- ## fehlerhaft adressierte Ports

---

| Szenario                       	| TCP                                                                                          	| UDP                                                  	|
|--------------------------------	|----------------------------------------------------------------------------------------------	|------------------------------------------------------	|
| falsche Reihenfolge          	| wird mit SEQ sortiert                                                                        	| nicht relevant                                       	|
| Paketverlust                 	| SEQ Erkennung fehlender Pakete<br>:arrow_right: Neuanforderung                               	| nicht relevant<br>:arrow_right: keine Neuanforderung 	|
| Doppelung                    	| SEQ Erkennung doppelter Pakete<br>:arrow_right: Nur 1 Paket wird verarbeitet, rest verworfen 	| nicht relevant<br>:arrow_right: wird nicht verworfen 	|
| Fehlerhaft adressierte Ports 	| Paket mit gesetztem RST Flag wird zurück gesendet                                            	| Paket wird verworfen                                 	|

---

# 9. Was versteht man unter der TCP Flusssteuerung?

---

# TCP Flusssteuerung
- Daten werden in einem Cache, beim Sender und auch beim Empfänger zwischen gespeichert
> Cache, Buffer, Puffer, ... hat man schon mal gehört
- Die aktuelle Cachegröße des Empfängers gibt an, wie viele Bytes der Sender unbestätigt senden darf
> Die Flusskontrolle sagt hier aus, das ist die "Aufnahmebereitschaft des Empfängers"
- Wenn der Cache voll ist, wird die Window Size auf `0` gesetzt.

---

# :exclamation: :sunny: geht auf

---

![bg fit](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/06_flusssteuerung.png?raw=true)

---

# 10. Erläutere das in der Vorlesung vorgestellte TCP Zustanddiagramm.

---

# 11. Nenne die Felder des IP und TCP Header, die nach erfolgreichem Verbindungsaufbau während der Phase der Datenübertragung über das Internet nicht konstant bleiben.

---

![bg right:70% fit](https://sun.iwu.edu/~jhaefner/CS390/Lecture16/ip_header.gif)

Bild Quelle https://sun.iwu.edu/~jhaefner/CS390/Lecture16/lec16.htm

---

# IP

- Paketlänge
- Ident
- MF
- Fragment Offset (wenn DF/MF aktiviert)
- Lebenszeit
- Prüfsumme

---

![bg right:70% fit](https://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/TCP_Header.svg/2560px-TCP_Header.svg.png)

Von Appaloosa 23:04, 6. Jul. 2007 (CEST) - drawn by me with inkscape, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=70129536

---

# TCP

- Sequence Number
- Acknowledgment Number
- Flags
- Window Size
- TCP Checksum
- Urgent Pointer
- Payload

---

# Weitere Fragen?

Bitte per E-Mail an [mv068@hdm-stuttgart.de](mailto:mv068@hdm-stuttgart.de) oder auf GitHub direkt.

# Bis nächste Woche oder jetzt schon viel Erfolg für die Prüfung? :smile:

> ```git pull``` nicht vergessen