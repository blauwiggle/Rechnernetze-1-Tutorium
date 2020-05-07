---
marp: true
theme: default #uncover #gaia #default
class: invert
paginate: true
headingDivider: true
footer: 'HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, Mai 2020'

---

# Rechnernetze - Tutorium
# zu Kapitel 2
## 13. Mai 2020

---

1. Warum wird in der Netzwerktechnik auf elektrischen Kabeln *symmetrisch* übertragen?
2. Wozu gibt es Kabelkategorien? Erläutere die Begriffe S/STP, S/UTP, ...
3. Was versteht man unter dem Bandbreite-Längenprodukt einen LWL?
4. 
    - Welche standardisierten optischen Wellenlängen werden in optischen Systemen verwendet?
    - Was versteht man eigentlich unter DWDM?
    - Wird bei einer DWDM-Übertragung Zeit- oder Frequenz Multiplex eingesetzt?
5. Beschreibe das Konzept der Strukturierten Verkabelung.
6. Ergänze den Typ des optischen Kabels und die Form der Lichtimpulse am Ausgang (Bild links). Mit welcher der beiden Glasfasertypen kann man eine größere Distanz überbrücken (Bild rechts)?

---

# 1. Warum wird in der Netzwerktechnik auf elektrischen Kabeln *symmetrisch* übertragen?

---

In das Kabel werden gleiche Signale mit gegensätzlicher Polarität eingespeist. Man bezeichnet das als differenzielle Signalübertragung. Das bedeutet, dass auf der einen Ader ein positives Signal und auf der anderen Ader das invertierte (das negative) Signal läuft. Auf dem Ponyhof, heben sich die symetrischen Amplituden rechnerisch auf. In der echten Welt gibt es jedoch geringe Störspannungen die um wenige µV abweichen. Da die Kabel jedoch verdrillt sind, wird die gegenseitige Beeinflussung unmöglich. Für die symetrische Datenübertragung benötigt man in jede Übertragungsrichtung zwei Adern. Insgesamt also 4 Adern oder wie der Fachmann es ausdrückt, 2 Doppeladern.

Das ist beispielsweise für ISDN oder Ethernet wichtig.

- Zwei Adern einer Doppelader liefern gegensätzliche Polarität
    :arrow_right: keine Strahlung, wenn die Summe der Signale *ideal* null ist
- Die Differenz der Signale bildet dann das eigentliche Datensignal

---

# Hier noch ein Bild vom Ponyhof

![bg 80% right:50%](https://www.elektronik-kompendium.de/sites/kom/bilder/10082712.gif)
[Quelle elektronik-kompendium.de](https://www.elektronik-kompendium.de/sites/kom/1008271.htm)


---

# 2. Wozu gibt es Kabelkategorien? Erläutere die Begriffe S/STP, S/UTP, ...

https://www.elektronik-kompendium.de/sites/net/0603191.htm

---

## Kategorien
- Kabel können so spezifiziert werden
- verschiedene Qualitätsanforderungen
    - man braucht kein Cat. 8 Kabel, für ISDN

## Mit steigender Kategorie
- mehr Kabelwindungen / cm
- bessere Isolierung
- weniger Crosstalk
- höhere Bandbreite

---

# :exclamation: Beachte bitte ...

Die verfügbare Bandbreite und die Länge des Kabels stehen in Korrelation. Übersteigt die Frequenz die Übertragung, reduziert sich auch die mögliche Kabellänge. Bei einer höheren Frequenz kann nur eine geringere Entfernung zurück gelegt werden. Danach ist das Signal murks.

---

# Übersicht der *unwichtigen* Kategorien

> Cat. 1 und Cat. 2 sind rein informell definiert worden

| Kategorie  	| Bandbreite  	| Anwendung  	|
|---	    |---:	|---	|
| Cat. 1  	| 0,4 kHz  	| Telefon- und Modemleitungen  	|
| Cat. 2  	| 4 MHz  	| Terminal-Systeme, ISDN   	|
| Cat. 3  	| 12,5 - 16 MHz  	| 10Base-T, 100Base-T4, ISDN, analoges Telefon 	|
| Cat. 4  	| 20 MHz  	| Token-Ring  	|

---

# Übersicht der **_wichtigen_** Kategorien

| Kategorie  	| Bandbreite  	| Anwendung  	|
|---	    |---:	|---	|
| Cat. 5  	| 100 MHz  	| 100Base-TX, SONET, SOH  	|
| Cat. 5e 	| 100 MHz  	| 1000Base-T  	|
| Cat. 6  	| 250 MHz  	| 1000Base-T, 155-MBit-ATM, 622-MBit-ATM  	|
| Cat. 6A  	| 500 MHz  	| 10GBase-T (bis 55 Meter)  	|
| Cat. 7  	| 600 MHz  	| 10GBase-T (bis 100 Meter)  	|
| Cat. 7A  	| 1000 MHz  	| 10GBase-T  	|
| Cat. 8  	| 1,6 - 2 GHz  	| 40GBase-T und 100GBase-T  	|

---

# Twisted-Pair-Kabel Bezeichnungssystem

![bg 90% right:50%](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/02_bezeichnungssystem.jpg?raw=true)

---

## XX steht für die Gesamtschirmung
- U = ohne Schirm (ungeschirmt)
- F = Folienschirm (beschichtete Kunststofffolie)
- S = Geflechtschirm (Drahtgeflecht)
- SF = Geflecht- und Folienschirm

---

## Y steht für die Aderpaarschirmung
- U = ohne Schirm (ungeschirmt)
- F = Folienschirm (beschichtete Kunststofffolie)
- S = Geflechtschirm (Drahtgeflecht)

---

## ZZ steht für die Verseilungsart
- TP = Twisted Pair (in der Regel)
- QP = Quad Pair

---

# XX/Y :exclamation: TP

Gesamtschirmung / Adernpaarschirmung als Twisted Pair

---

## U/UTP - Unscreened/Unshielded Twisted-Pair-Kabel

![bg fit right](https://www.elektronik-kompendium.de/sites/net/fotos/06031914.jpg)

---

## U/FTP - Unscreened/Foiled Twisted-Pair-Kabel

![bg fit right](https://www.elektronik-kompendium.de/sites/net/fotos/06031912.jpg)

---

## S/FTP - Screened/Foiled Twisted-Pair-Kabel

![bg fit right](https://www.elektronik-kompendium.de/sites/net/fotos/06031911.jpg)

---

bilder
evtl stecker

---

# 3. Was versteht man unter dem Bandbreite-Längenprodukt einen LWL?

https://de.wikipedia.org/wiki/Bandbreitenlängenprodukt

---

# 4.
## Welche standardisierten optischen Wellenlängen werden in optischen Systemen verwendet?
## Was versteht man eigentlich unter DWDM?
## Wird bei einer DWDM-Übertragung Zeit- oder Frequenz Multiplex eingesetzt?

---

# 5. Beschreibe das Konzept der Strukturierten Verkabelung.

https://www.elektronik-kompendium.de/sites/net/0908031.htm

---

# 6. Ergänze den Typ des optischen Kabels und die Form der Lichtimpulse am Ausgang (Bild links). Mit welcher der beiden Glasfasertypen kann man eine größere Distanz überbrücken (Bild rechts)?

https://www.glasfaserkabel.de/Der-Unterschied-zwischen-Singlemode-und-Multimode-LWL-Kabeln:_:13.html