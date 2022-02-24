## M1 generiek | IMBOR CM

Dit hoofdstuk beschrijft de toplaag (M1 generiek) van IMBOR, dit betreft dus het gegevensmodel (soms metamodel
genoemd).
Hieronder wordt uitleg gegeven en worden aanvullende regels beschreven.
Het is _belangrijk_ om aan te geven dat het IMBOR Conceptueel Top Level Model (IMBOR CM) een selectie is uit het CM
van de NTA8035 (en de taalbinding naar
de W3C standaarden) + de top van de IMBOR ontologie (gevisualiseerd door de groene scheidingslijn in het diagram
hieronder).
Dit model is een aparte/view weergave om het overzicht te creëren, maar in principe is het niet nodig om deze te
materialiseren.
Alle gegevens zitten eigenlijk in de NTA (BasisSemantics) gegevenssets en de IMBOR ontologie (IMBOR-LD gegevensset).

### Relatie met NTA8035

Het CM van de LinkedData versie van IMBOR is gebaseerd op de [NTA 8035][NTA8035].
Het M1 niveau van IMBOR bevat zo min mogelijk eigen semantiek en gebruikt in plaats daarvan:
RDF, RDFS, SHACL, OWL en stukjes van het CMM van NTA 8035.

### Toelichting CM
Het conceptueel model bestaat grofweg uit drie belangrijke secties:

* "(Fysieke)Objecten"
* "Eigenschappen en hun waardes"
* "Organiserende elementen

Qua Objecten wordt er volledig gebruik gemaakt van de ontologie van de NTA8035.
We kennen binnen de LinkedData versie van IMBOR voorlopig alleen maar `nta8035:PhysicalObject` voor objecten.
Alle objecten binnen de ontologie zijn daarmee `rdfs:subClassOf` het concept `nta8035:PhysicalObject`.

<div class="issue" data-number="89"></div>

Daarnaast hebben objecten een onderlinge relatie die binnen de IMBOR ontologie ook overgenomen wordt vanuit de
NTA8035. Dit
betreft `nta8035:hasPart` (uitgevoerd als SHACL shape).
Hiermee kan een meronomie geconstrueerd worden.
Qua attributes zijn minimaal de `rdfs:label`, `skos:prefLabel` en `skos:definiton` verplicht.
Er wordt gebruik gemaakt van `skos:notation` om de originele IMBOR GUID (vanuit Access) mee te geven.

Met betrekking tot eigenschappen en hun waardes wordt er, zoals de NTA8035 dit ook beschrijft, gebruik gemaakt van
SHACL shapes.
Alle eigenschappen in de ontologie zijn een `rdf:Property` en worden via een `sh:PropertyShape` aan
de `sh:NodeShape` van een `nta8035:PhysicalObject` gehangen waar dit van toepassing is.

De SHACL shape 'ObjectProperty' wordt gebruikt wanneer het een eigenschap betreft met
een voorgedefinieerde waardelijst. Daarom is de `sh:class` een `rdfs:subClassof` de klasse
`nta8035:EnumerationType`. De instanties van deze domeinwaarden staan in de ontologie en zijn daarmee de
keuzelijsten.

De SHACL shape 'DataProperty wordt gebruikt wanneer het een eigenschap betreft met een
waarde en/of een eenheid. Hier is de `sh:datatype` een waarde van het datatype
`xsd:...`. Op de eigenschap (de `rdf:property`) worden de properties `nta8035:unit` en `nta8035:quantityKind`
vastgelegd. Hiervoor wordt de QUDT ontologie gebruikt zoals de NTA8035 dat voorschrijft.
Hiernaast wordt ook nog de `rdfs:range` vastgelegd. Dit is altijd een instantie van `nta8035:QuantityValue` vaak in
de vorm van een blank node. Dit wordt gedaan zodat ook secundaire meta eigenschappen kunnen worden meegegeven
(bijvoorbeeld wie het heeft gemeten).

Bij SHACL wordt gebruik gemaakt van `rdf:list` wanneer er een 'combinatie' gemaakt moet worden van de eigenschap en
de te controleren waarde van deze eigenschap. De eerste waarde van de list is altijd de property waar op
gecontroleerd moet worden, de tweede waarde is de daadwerkelijke waarde.

<aside class='example'>

Voorbeeld van respectievelijk de SHACL shape die de instantie kan 'voorschrijven'.

```turtle
# Shape met rdf:list tussen haakjes in IMBOR-LD
shape:P659Shape  a   sh:PropertyShape ;
sh:group     groep:P9 ;
sh:maxCount  1 ;
sh:path      ( imborp:P659 rdf:value ) .

# Shape met rdf:list als instantie
:brug imborp:P659 :brugDikte . 
:brugDikte	a nta8035:QuantityValue ;
        rdf:value "300" ; 
        nta8035:unit unit:Millim .
```

</aside>

De SHACL shape 'AnnotationProperty' wordt gebruikt wanneer het een eigenschap betreft met tekstuele waarden.
Deze is nagenoeg hetzelfde als de 'DataProperty' alleen is de enige mogelijke waarde `xsd:string`.
Uiteraard worden de properties `nta8035:unit` en `nta8035:quantityKind` _niet_ vastgelegd.

Het laatste gedeelte van het CM gaat over het 'organiseren' van de concepten in een structuur.
We onderscheiden momenteel twee structuren (of: 'perspectieven'). De ene representeert de hiërarchie
zoals deze in IMBOR gebruikt wordt, de andere representeert de IMBOR vakdisciplines. Beiden zijn
`skos:collection` en hebben een 'top member'. Dit zijn respectievelijk
`groep:IMBORHierarchischeCollectie` en `groep:IMBORVakdisciplineCollectie`. Beiden hebben weer andere members
en al deze members kunnen een `nta8035:PhysicalObject` als member hebben. Op deze manier kan
een IMBOR representatie van de data gepresenteerd worden.
Beiden SKOS indelingen hebben dus geen _expliciete_ waarde/gebruik in de ontologie. Het is puur een manier om naar
de gebruikers van IMBOR een visualisatie te bieden. Er kunnen geen conclusies uit getrokken worden, of in LinkedData
termen: er kan geen reasoning op gedaan worden.

### Diagram

<figure>

![](img/IMBOR%20Metamodel.png?raw=true)
    
<figcaption>Visualisatie IMBOR metamodel</figcaption>
</figure>

### Regels

Om het model toe te passen zijn er, naast de expliciete regels in het model zelf, een aantal impliciete regels van
toepassing.

1. De `rdfs:domain` en `rdfs:range` worden niet gebruikt omdat deze te restrictief (met name omdat ze transitief)
zijn. In plaats hiervan worden SHACL shapes gebruikt voor het vastleggen van relaties tussen objecten en
eigenschappen en objecten onderling. De uitzondering hierop is dat de `rdfs:range` wel gebruikt wordt binnen de
SHACL shape omdat de NTA8035 voorschrijft dat aangegeven moet worden dat iets een `nta8035:QuantityValue` is.
1. De `nta8035:unit` en `nta8035:quantityKind` properties worden altijd gebruikt i.c.m. met een QUDT resource.
1. Er worden geen Individuals gemaakt in het model bij Objecten.
1. Een `nta8035:PhysicalObject` kan maar één `skos:member` relatie hebben met een member van de Hiërarchie
collectie.
1. Alle concepten hebben een `rdfs:label`, `skos:prefLabel` en `skos:definition`. Met daarin respectievelijk de data
gerelateerde naam, de IMBOR
naam in NL en de definitie in NL. De eerste twee zijn sowieso verplicht.


### Gemaakte keuzes

Bij het maken van de LinkedData versie van IMBOR zijn bepaalde keuzes gemaakt met betrekking tot onder andere:

* Interpretatie van de NTA8035
* Transformatie van de IMBOR Access database naar een LinkedData formaat
* Use cases voor de LinkedData versie van IMBOR

Deze keuzes worden "design decisions" genoemd. Al deze keuzes worden gedocumenteerd en bijgehouden
op de GitHub bij de Issues, met het label "design decision". In [Annex A](#issue-summary) staan de issues die in
deze ReSpec worden aangehaald.
De volledige [lijst IMBOR-LD design decisions][design decisions] is ook beschikbaar.

### URI-strategie

De URI-strategie wordt overgenomen uit de NTA8035. Er is gekozen om alles onder /def/ te zetten omdat, ook de
individuals, in een TypeLibrary staan en geen aanwijsbare dingen in de echte wereld representeren.
Tevens kiezen we voor '/'' ipv '#'' want zo houden we opties open als we het dereferencable willen maken.
De NTA8035 schrijft dan voor:

> `http[s]://{internet domain}/[path]/def/[data model](/|#)[({concept}|{attribute}|{relation})]`

De NTA8035 adviseert human-readable identifiers. Bij IMBOR-LD doen we dat niet.
Na overleg met de NEN is duidelijk dat het een advies is (met name in situatie waarin ontologieen opgestart worden),
maar niet hoeft. Vanwege de hoeveelheid data en de vele dubbelingen in terminologie besluiten we voor IMBOR-LD
dat we betekenisloze codes aanhouden. Binnen de LinkedData versie van IMBOR wordt dan een voorbeeld:

<aside class='example'>

```turtle
http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/objecttype/OBB1051 a rdfs:Class ;
    rdfs:label       "Aanleginrichting"@nl-NL ;
    rdfs:subClassOf  imbor:OBB414 ;
    skos:definition  "De aanleginrichting is een brugdek dat aan één zijde scharnierend bevestigd is aan de wal en aan de andere zijde omhoog en omlaag kan bewegen. Bij wisselende waterstanden kunnen de veerboten zo altijd aanmeren en kunnen de mensen gemakkelijk van de wal op het schip komen. Hoog boven het brugdek staat, op vier palen, een ruimte met daarin de motor die het brugdek op en neer kan doen bewegen doormiddel van staalkabels."@nl-NL ;
    skos:notation    &lt;urn:uuid:D92E6993-5546-4B29-8CC5-25414E83C042&gt; ;
    skos:prefLabel   "Aanleginrichting"@nl-NL .
```

</aside>

Verder kiezen we ervoor om 5 verschillende grafen (evenals namespaces) te onderscheiden:

Graaf | Inhoud | Namespace
---------- | ---------- |---------
`graph:ObjectTypen` | Objecten en dus ook alle onderdelen van de taxonomie |
`http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/objecttype/`
`graph:Eigenschappen` | Eigenschappen (IMBOR:attributen) en hun informatie |
`http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/eigenschap/`
`graph:Domeinwaarden` | Vastewaardelijsten en hun mogelijk waarden |
`http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/domeinwaarde/`
`graph:Shapes` | SHACL shapes om Objecten te matchen met de eigenschappen en raakvlakken |
`http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/shape/`
`graph:Groeperingen` | De SKOS collecties voor de IMBOR hiërarchie en Vakdisciplines en versie |
`http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/groepering/`

Deze splitsing in grafen is gedaan op verzoek van gebruikers omdat dit makkelijker is bij het splitsen van de
ontologieën (men kan zo kiezen welke men wil gebruiken en welke niet)
en omdat er zo veel entiteiten zijn (en splitsing enig overzicht geeft).

### Versiebeheer

Versiebeheer is nog steeds onderwerp van discussie in de Semanticweb community. 
Ook CROW heeft [een document over versiebeheer][versiebeheer] gepubliceerd.

Binnen IMBOR-LD hebben we verschillende opties afgewogen. Dit is na te lezen binnen issue 88 (en de comments) op
GitHub:

<div class="issue" data-number="88"></div>

Grofweg kan gesteld worden dat we een TTL file op GitHub plaatsen en deze ook publiceren op het LDP. Hierin
introduceren we één klasse van het type `skos:collection` met daarin alle resources die een URI hebben als
`".../imbor/def/.../*"`. Daarnaast is er één `dcat:Distribution` class, hierop zetten we de daadwerkelijke versie
info. De `skos:collection` is gewoon een groep met alle Subjecten en Objecten in één versie. Welke versie dat is
wordt vermeld met een `rdfs:isDefinedBy` die als waarde de `dcat:Distribution` class heeft. Deze manier is simpel,
doeltreffend maar heel banaal. Nadat de TTL file wordt gepubliceerd op het LDP van CROW wordt de juiste
versieinformatie pas verkregen, dit voegen we dan wel toe in de TTL op GitHub. Dit is zeker ook geen mooie manier
van versiebeheer. Maar it-does-the-job voor de huidige use-cases. Daarnaast is iedereen bekent met SKOS, dus moet
het makkelijk te behandelen zijn. Onderstaande SPARQL voorbeeld geeft een manier om de juiste zaken op te vragen.

<aside class='example'>

```sparql
PREFIX groep:   &lt;http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/groepering/&gt;
SELECT * WHERE {
    ?s ?p ?o . 
FILTER ( groep:Versie2020-7 skos:member ?s || groep:Versie2020-7 skos:member ?o )
}
```

</aside>
