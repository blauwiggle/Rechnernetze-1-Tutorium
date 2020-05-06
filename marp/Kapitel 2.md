---

theme: default
paginate: true
marp: true
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

# 3. Was versteht man unter dem Bandbreite-Längenprodukt einen LWL?

https://de.wikipedia.org/wiki/Bandbreitenlängenprodukt

---

# 4.
## Welche standardisierten optischen Wellenlängen werden in optischen Systemen verwendet?
## Was versteht man eigentlich unter DWDM?
## Wird bei einer DWDM-Übertragung Zeit- oder Frequenz Multiplex eingesetzt?

---

# 5. Beschreibe das Konzept der Strukturierten Verkabelung.

---

# 6. Ergänze den Typ des optischen Kabels und die Form der Lichtimpulse am Ausgang (Bild links). Mit welcher der beiden Glasfasertypen kann man eine größere Distanz überbrücken (Bild rechts)?

https://www.glasfaserkabel.de/Der-Unterschied-zwischen-Singlemode-und-Multimode-LWL-Kabeln:_:13.html