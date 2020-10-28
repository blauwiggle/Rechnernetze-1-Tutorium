---

theme: uncover #uncover #default #gaia
class: invert
paginate: true
marp: true
headingDivider: true
footer: 'HdM Stuttgart - Rechnernetze - Tutorium | Copyright © Michael Vanhee, mv068@hdm-stuttgart.de, 2020'

---

# Rechnernetze - Tutorium
# zu Kapitel 1
    Supplement Update

Link zu den Folien :arrow_down: 
https://github.com/blauwiggle/Rechnernetze-1-Tutorium

---

# Im letzten Tutorium sind Fragen aufgetaucht.

## Was ist Latenz?
## Was ist ein Hop?
## Was ist SDH/SONET?

---

# Latenz

Die Latenz beschreibt die Zeit, die ein Datenpaket innerhalb eines Netzwerks unterwegs ist.

Die Latenz entwickelt sich aus allen Leitungen, Funkstrecken, Koppelelementen, den Informationen ganz oben im Datenpaket (Header) und der Kodierung.

Zum Thema Netzneutralität, jedem Netzbetreiber steht es frei zu, welche Daten er wie priorisiert.

Somit ist räumliche Entfernung nicht unbedingt ausschlaggebend für eine hohe Latenz, sondern vielmehr die Anzahl an Hops.

---

# Hop

Ein Hop (engl. für "Hopser", "Etappe") ist ein Zwischenschritt eines Pakets auf dem Weg von einem Netzsegment (PC -> Switch -> Router) bzw. Subnetz (HdM -> Universität -> BelWü -> DE-CIX) zum jeweils nächsten. Das jeweilige Gerät (beispielsweise Router) definiert dann den **next hop**, wohin das Paket als nächstes gehen soll.

Die Anzahl der Hops können mit einem **Traceroute** ermittelt werden.

---

![bg fit](https://github.com/blauwiggle/Rechnernetze-1-Tutorium/blob/master/marp/images/01_traceroute.jpg?raw=true)

---

# SDH/SONET
## SDH (Synchrone Digitale Hierarchie) - DE
## SONET (Synchronous Optical Network) - US

---

Beides sind Weitverkehrsnetze, die nahezu identisch sind. Vor WhatsApp und Co. hatte man noch telefoniert :phone:. Dazu ergänzten beide Systeme in den 90er Jahren das Netz und ermöglichten so Geschwindigkeiten von bis zu 2,5 GBit / Sekunde. Die Strukturen bestehen aus DWDM-Ringstrukturen. DWDM besprechen wir im kommenden Kapitel. In den vermaschten Netzstrukturen sind vordefinierte Ersatzstrecken enthalten.

---

## Ergänzungen von Herr Kiefer

SDH/SONET waren und sind es immer noch, Layer 2 Alternativen. Vorwiegend heute im wo wirkliche Echtzeit benötigt wird, zum Beispiel werden Radarbilder der FLugsicherung über SDH übertragen. Einsatz auch im Bereich der Rettungskräfte (die eigene Netze haben).

Die Marktbedeutung hat nachgelassen, da sie zu teuer sind. Geschwindkeiten bis 40 GBit / Sekunde sind möglich, in Verbindung mit DWDM deutlich mehr.