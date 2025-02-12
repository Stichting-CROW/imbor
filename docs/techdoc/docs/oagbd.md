## OAGBD

OAGBD is een addendum welke in IMBOR zit vanaf 2021. De eerste versie is de resultante van een onderzoek wat de gemeenten Almelo en Utrecht hebben gedaan. Het onderzoek heeft gekeken naar informatieverlies tijdens de 'levensfases' van een object. In dit geval is de opeenvolging van objectlevensfases:
__>> Ontwerp >> Aanleg >> Geo >> Beheer__

De letters staan dan ook voor:
- O = Ontwerp
- A = Aanleg
- G = Geovoorziening
- B = Beheer
- D = Dynamisch gegeven

Binnen het onderzoek is bij elke combinatie van klasse en attribuut in IMBOR2022 aangegeven in welke levensfase van het object de informatie doorgaans bekend is. Zo is inzichtelijk gemaakt dat veel informatie reeds beschikbaar is in vroege fasen van het object en dat er getracht kan worden deze informatie mee te nemen naar volgende fasen. 

Binnen IMBOR in Access is de tabel met klassen en attributen hiervoor uitgebreid met een extra veld: OAGBD. Binnen de LinkedData versie is de beschikbaar als een aparte graaf.

De bovenstaande conceptualisering van objectlevensfases is ontwikkeld voor de onderverdeling van IMBOR-attributen. Binnen de [NEN2660-2:2022][nen2660:2022] wordt door het begrip ‘levenscyclus’ onderscheid gemaakt tussen geplande en gerealiseerde entiteiten. De wisselwerking tussen gepland en gerealiseerd heeft de volgende relatie met OAGBD. In het lineaire doorlopen van OAGBD komt het object in `O` overeen met een geplande entiteit. Vanaf `A` bestaat het object in de werkelijkheid en is het als zodanig een gerealiseerde entiteit. Echter, mocht de opeenvolging van levensfases cyclisch worden, dat wil zeggen, `B` gaat over naar `D`, bijvoorbeeld wanneer een object wordt herzien, wordt aangepast, wordt verplaatst etc., dan gaat een gerealiseerde entiteit over naar een geplande entiteit, om in `A` wederom een gerealiseerde entiteit te worden.

OAGBD kan dus gezien worden als een situatiespecifieke verbijzondering van de algemene wisselwerking tussen geplande en gerealiseerde entiteiten uit [NEN2660-2:2022][nen2660:2022].

[2]: https://www.nen.nl/nieuws/normontwerp-informatiemodellering-van-gebouwde-omgeving-ter-commentaar/
[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667
