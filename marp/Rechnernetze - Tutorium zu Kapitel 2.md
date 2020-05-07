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
6. Ergänze den Typ des optischen Kabels und die Form der Lichtimpulse am Ausgang. Mit welcher der beiden Glasfasertypen kann man eine größere Distanz überbrücken?

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

[Quelle elektronik-kompendium.de](https://www.elektronik-kompendium.de/sites/net/0603191.htm)

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
[Quelle elektronik-kompendium.de](https://www.elektronik-kompendium.de/sites/net/0603191.htm)

---

## U/FTP - Unscreened/Foiled Twisted-Pair-Kabel

![bg fit right](https://www.elektronik-kompendium.de/sites/net/fotos/06031912.jpg)
[Quelle elektronik-kompendium.de](https://www.elektronik-kompendium.de/sites/net/0603191.htm)

---

## S/FTP - Screened/Foiled Twisted-Pair-Kabel

![bg fit right](https://www.elektronik-kompendium.de/sites/net/fotos/06031911.jpg)
[Quelle elektronik-kompendium.de](https://www.elektronik-kompendium.de/sites/net/0603191.htm)

---

# Prüfungstipp

Schau dir vorab verschiedene Stecker Typen im Bereich der Netzwerktechnik an, wie beispielsweise RJ45, FDDI, SC-Duplex, usw. :stuck_out_tongue_winking_eye:

---

# 3. Was versteht man unter dem Bandbreite-Längenprodukt eines LWL?

---

Es ist ein wichtiger Kennwert bei Multimodefasern, da er zusätzlich neben der Dämpfung zu berücksichtigen ist. Dabei berechnet der Wert sich auf der maximalen Bandbreite und Länge des LWL. Bei Monomodefasern verzichtet man darauf, da diese in der Regel eine hohe Qualität besitzen.

> B`= Bandbreite * Länge (Einheit MHz * Kilometer)

Doch was heißt das jetzt genau?

---

## Das Bandbreite-Längenprodukt von 1.200 Mhz * 1.000m ist 1200 MHz / kM.

---

## :exclamation: Mit welcher **_Bandbreite_** kann man dann bei 500 Meter bzw. 2000 Meter **_Faserlänge_** übertragen, wenn die Bandbreite pro Kilometer 1.200 MHz beträgt?

---

> 500 Meter :arrow_right: 2.400 MHz
> 2.000 Meter :arrow_right: 600 MHz

---

![bg 90% right:50%](https://upload.wikimedia.org/wikipedia/commons/a/ab/Tempo-vs-Länge.svg)

Von Speed-vs-length.svg: Alexander.stohrderivative work: Biktora (talk) - Speed-vs-length.svg, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=11053402

---

# 4.
# Welche standardisierten optischen Wellenlängen werden in optischen Systemen verwendet?
# Was versteht man eigentlich unter DWDM?
# Wird bei einer DWDM-Übertragung Zeit- oder Frequenz Multiplex eingesetzt?

---

## Welche standardisierten optischen Wellenlängen werden in optischen Systemen verwendet?

---

- 850 Nanometer
- 1300 Nanometer
- 1550 Nanometer

---

## Was versteht man eigentlich unter DWDM?

---

## Dense Wavelength Division Multiplex


> Nerd Wissen

Das steht für Dichte Wellenlängen-Multiplex und gilt als zurzeit leistungsstärkste Variante der Übertragung. Durch die stabilisierten Laser (thermostatierte [DFB-Laserdioden](https://de.wikipedia.org/wiki/Distributed_Feedback_Laser)) und hochwertigen Filter, sind Übertragungsraten bis zu 100 Gbit / Sekunde pro Kanal bei bis zu 80 Kanälen möglich. Durch Kombination der verschiedenen Lichtbänder, sind bis zu 160 Kanäle möglich. Dabei sind alle 200 Kilometer Verstärker und alle 2.000 Kilometer elektrische Daten-Regeneratoren notwendig.

---

## Wird bei einer DWDM-Übertragung Zeit- oder Frequenz Multiplex eingesetzt?

---

## Frequenz Multiplex

---

# 5. Beschreibe das Konzept der Strukturierten Verkabelung.

---

## Nenne ein paar Ziele ...

---

- Flexible Erweiterbarkeit
- Ausfallsicherheit durch Stern Topologie
- Kapazitäten werden besser verteilt
- Einheitlicher Standard
- Unterstützung heutiger und zukünftiger Systeme

---

Von Deadlyhappen - Eigenes Werk, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=25174721

![bg 100% right:70%](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Strukturierte_Verkabelung.svg/1024px-Strukturierte_Verkabelung.svg.png)

---

# 6. Ergänze den Typ des optischen Kabels und die Form der Lichtimpulse am Ausgang.

[Quelle Bilder elektronik-kompendium.de](https://www.elektronik-kompendium.de/sites/kom/0301282.htm)

---

# :exclamation: Nicht erschrecken, gleich geht die :sunny: auf :smile:

---

<!-- _class: lead -->

![bg fit vertical](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/02_mono.jpeg?raw=true)
![bg](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/02_stufe.jpeg?raw=true)
![bg](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/02_gradient.jpeg?raw=true)

---

## Multimodefaser mit Gradientenindex Profil

- es werden mehrere Lichtwellen gleichzeitig geschickt
- an den Wänden der Faser wird das Signal weich reflektiert
- die Brechzahl des Kerns nimmt parabelförmig zum Mantel ab
- das Ausgangssignal ist noch sehr gut
- wird für Verbindungen von Gebäuden oder Etagen eingesetzt

![bg contain 80% right:40%](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/02_gradientfin.jpeg?raw=true)

---


## Multimodefaser mit Stufenindex Profil

- es werden mehrere Lichtwellen gleichzeitig geschickt
- an den Wänden der Faser wird das Signal hart reflektiert
- die Brechzahl fällt zwischen Kern und Mantel scharf ab
- wird für Verbindungskabel im Patchschrank verwendet

![bg contain 80% right:40%](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/02_stufefin.jpeg?raw=true)

---


## Monomodefaser

- es können weite Strecken überbrückt werden
- sind sehr teuer in der Herstellung
- wird für Stadt- und Zugangsnetze optimiert

![bg contain 80% right:40%](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/02_monofin.jpeg?raw=true)

---

# Mit welcher der Glasfasertypen kann man eine größere Distanz überbrücken?

---

## Monomodefaser

---

# Bis nächste Woche :smile:

> ```git pull``` nicht vergessen