## SHACL Shapes

[[shacl]] is een krachtige W3C standaard om data te valideren. Binnen IMBOR wordt deze gebruikt om enkele beperkingen op te leggen. Dit wordt zowel bij semantische relaties als bij klasse-attribuut combinaties gebruikt. De [[shacl]] constructies zijn wel net iets anders. Hieronder worden ze toegelicht:

### Semantische relaties

De casus:
1.	Een Auto minimaal 1 motor moet hebben
2.	Een Auto minimaal 3 wielen moet hebben
3.	Beide via dezelfde relatie (hasPart) gaan
Gebruik `sh:qualifiedValueShape` met `sh:qualifiedMinCount`.

Waarom?
Met directe `sh:class` zou je aangeven dat ALLE hasPart relaties naar dezelfde klasse moeten wijzen, wat onmogelijk is als een auto zowel motoren als wielen heeft.

```turtle
ex:Auto
  a owl:Class, sh:NodeShape ;
  sh:property [
    sh:path bs:hasPart ;
    sh:qualifiedValueShape [ sh:class ex:Motor ] ;
    sh:qualifiedMinCount 1 ;
  ] ;
  sh:property [
    sh:path bs:hasPart ;
    sh:qualifiedValueShape [ sh:class ex:Wiel ] ;
    sh:qualifiedMinCount 3 ;
  ] .
```

Conclusie
Voor decomposities en andere gevallen waar één property naar instanties van verschillende klassen kan wijzen, is sh:qualifiedValueShape de juiste keuze. Dit is fundamenteel anders dan wanneer bijvoorbeeld alle waarden uit dezelfde domeinwaardelijst moeten komen.
Vuistregel:
Eén property, één toegestane klasse → gebruik sh:class
Eén property, meerdere toegestane klassen → gebruik sh:qualifiedValueShape


### Enumeratielijst

De casus:
1.	Het kenmerk "verschijningsvorm" mag maar 1 keer voorkomen bij een viaduct
2.	De waarde moet uit een specifieke domeinwaardelijst komen

Gebruik `sh:class` direct, niet `sh:qualifiedValueShape`.

```turtle
imbor:1285b98d-1caa-4147-b033-5e1248a67b5a
  a sh:PropertyShape ;
  skos:prefLabel "verschijningsvorm vastgezet op Viaduct"@nl ;
  sh:path imbor:e3e112b3-e46f-45c4-b2c9-b152e6f805a1 ;
  sh:maxCount 1 ;
  sh:class imbor:06d5a7ff-e7d0-4c38-867a-a1749133048e .
```

Conclusie
Voor attributen met vaste waardelijsten zoals "verschijningsvorm" is de directe `sh:class` benadering correct.
`sh:qualifiedValueShape` moet je alleen gebruiken wanneer:
Een property naar instanties van verschillende klassen kan wijzen (zoals hasPart dat zowel naar wielen als motoren kan wijzen)
Je wilt specificeren hoeveel instanties van elke specifieke klasse er moeten/mogen zijn
In jullie geval wil je juist dat ALLE waarden uit één specifieke domeinwaardelijst komen, dus gebruik sh:class.

>ADVISEMENT
>In IMBOR2022 wordt een extra beperking gelegd die zei: "De waarde MOET exact één van deze URI's zijn.". Dit werd gedaan door de `sh:in` constructie. Dit is correcter, maar dit leverde ook veel meer triples en een ingewikkeldere constructie op. Vandaar dat deze geschrapt is. 


### Suggestielijst

De casus:
1.	Het kenmerk "status" mag maar 1 keer voorkomen
2.	De waarde bij voorkeur uit een domeinwaardelijst komt
3.	Gebruikers mogen eigen waarden toevoegen

Gebruik `sh:qualifiedValueShape` met `sh:qualifiedMaxCount`.

Dit is een belangrijk verschil met de enumeratielijst. Je wilt:
* Suggereren welke waarden gewenst zijn
* Toestaan dat gebruikers afwijken
* Toch valideren dat er maximaal 1 waarde is

```turtle
imbor:StatusShape
  a sh:PropertyShape ;
  skos:prefLabel "status vastgezet op Viaduct"@nl ;
  sh:path imbor:heeftStatus ;
  sh:maxCount 1 ;  # Maximaal 1 status
  sh:qualifiedValueShape [
    sh:class imbor:StatusDomeinwaardelijst
  ] ;
  sh:qualifiedMaxCount 1 .  # Als het uit de lijst komt, ook max 1

# Domeinwaardelijst met IMBOR waarden
imbor:StatusDomeinwaardelijst a owl:Class ;
  rdfs:label "Status domeinwaardelijst"@nl .

imbor:WordtGebouwd a imbor:StatusDomeinwaardelijst ;
  skos:prefLabel "wordt gebouwd"@nl .

imbor:IsGebouwd a imbor:StatusDomeinwaardelijst ;
  skos:prefLabel "is gebouwd"@nl .
```

Hoe gebruikers waarden toevoegen

Eigen instantie zonder typering (eenvoudig)
ex:Viaduct1 a imbor:Viaduct ;
  imbor:heeftStatus ex:IsGesloopt .

ex:IsGesloopt 
  skos:prefLabel "is gesloopt"@nl .
  # Geen rdf:type declaratie!


Conclusie
Voor suggestielijsten is `sh:qualifiedValueShape` de juiste keuze omdat het:
Documenteert welke waarden aanbevolen zijn
Toestaat dat gebruikers afwijken
Valideert dat er niet teveel waarden zijn
Dit is een derde patroon naast:
1.	Verplichte enumeratie → sh:class
2.	Decompositie → sh:qualifiedValueShape met sh:qualifiedMinCount
3.	Suggestielijst → sh:qualifiedValueShape met sh:qualifiedMaxCount


### Datatypen

