## M1 specifiek | IMBOR ontologie

### ObjectTypen

IMBOR in LinkedData kent een taxonomie van fysieke objecten, die begint bij `nta8035:PhysicalObject`. Alles is
hiermee een fysiek object volgens de NTA definitie:

> _Een FysiekObject is iets dat bestaat of zou kunnen bestaan in ruimte en tijd, een manifestatie en een afbakening
van materie en/of energie vormt en waarneembaar is door de zintuigen.
> Een fysiek object kan activiteiten uitvoeren en kan ook worden getransformeerd door activiteiten._

<div class="issue" data-number="5"></div>

Direct onder het `nta8035:PhysicalObject` vinden we het Beheerobject. Dit is een belangrijk object binnen IMBOR,
omdat eigenlijk alle 'te beheren' objecten hier onder vallen.
En daarmee alle eigenschappen van dat object, van toepassing zijn op alle andere objecten.
Alle andere objecten zijn dan ook `rdfs:subClassOf` dit object. Vanaf daaronder wordt de structuur gevolgd die IMBOR
kent als de 'IMBOR Hiërarchie'.
Naast het Beheerobject staan een aantal losse 'raakvlakobjecten' (of binnen IMBOR: 'hulpobjecten'). Dit zijn de
objecten die een rol spelen in de `nta8035:hasPart` relatie.

Een andere uitzondering betreffen een aantal bijzondere IMBOR objecten:

<div class="issue" data-number="27"></div>


### Eigenschappen

Eigenschappen in IMBOR bepalen welke informatie bij een object wordt opgeslagen.
Eigenschappen kunnen voorgedefinieerde waardes hebben (zie [Vastewaardelijsten](#vastewaardelijsten))
of een voorgedefinieerde eenheid ([Eenheden](#eenheden)) of eenheidloos bepaald zijn.
In dat geval zou de definitie van de eigenschap duidelijkheid moeten geven over de gewenste (tekstuele) waardes.
Deze eigenschappen worden respectievelijk ObjectProperty, DatatypeProperty en AnnotationProperty genoemd.
De daadwerkelijke eigenschappen worden vastgelegd in (SHACL) shapes.

#### Shapes

In IMBOR koppelen SHACL-shapes bepaalde eigenschappen aan bepaalde objecten.
[SHACL][SHACL] (afgekort met `sh:`) is een W3C aanbeveling voor het valideren van Linked
datasets.
De shapes die IMBOR bepaalt, zijn als een vormenstoof.
De areaalgegevens zijn als de blokken die erdoor passen (of niet).

Er zijn `sh:NodeShape`s en `sh:PropertyShape`s.
Een `sh:NodeShape` in IMBOR richt zich op instanties van bepaalde klasses, welke is te zien bij `sh:targetClass`.
Een `sh:PropertyShape` in IMBOR richt zich op de waardes van bepaalde eigenschappen, welke is te zien bij `sh:path`.
Een `sh:NodeShape` wordt vervolgens verbonden met de mogelijke `sh:PropertyShape` eigenschappen door de
`sh:property` relatie.
Er mag gesteld worden dat de `sh:NodeShape` altijd een paar vormt met een fysiek object, te weten:
`nta8035:PhysicalObject`
en dat de `sh:PropertyShape` altijd een paar vormt met de eigenschap, te weten: `rdf:property`.
De vele combinaties tussen de fysieke objecten en de eigenschappen worden zodoende vastgelegd middels de
`sh:property` relatie.

SHACL is bedoeld om Linked datasets te valideren en er bestaan dus programma's die geautomatiseerd een controle
doen.
Bijvoorbeeld TopQuadrant's [`shaclvalidate`][shaclvalidate] of Apache Jena's [`shacl`][shacl-cli].
Alle IMBOR klasses, eigenschappen en domeinwaardes voldoen ook aan de shapes die beschreven staat in
[`data/imbor.shapes.ttl`](/data/imbor.shapes.ttl).

> Met ShaclValidate geïnstalleerd op de commandoregelinterface, kunnen we controleren of IMBOR voldoet aan het
gespecificeerde metamodel.
>
> `$ shaclvalidate -datafile data/imbor-ld.ttl -shapesfile data/imbor.shapes.ttl`
>
> ```turtle
> [
> a sh:ValidationReport ;
> sh:conforms true
> ] .
> ```
>
> Het geleverde IMBOR in Linked databestand voldoet dus aan het metamodel.


#### Eenheden

Sommige objecttype-eigenschappen hebben eenheid en grootheid gedefinieerd.
Conform NTA 8035, zijn dit URIs uit de [QUDT](http://qudt.org/) vocabulaire.
Implementeerders wordt aangeraden die dataset in te laden om de juiste interpretatie te verbinden aan de een- en
grootheden.

1. `nta8035:unit` verwijst naar een eenheid, zoals 'millimeter'.
1. `nta8035:quantityKind` verwijst naar een grootheid, zoals 'lengte'.

#### Vastewaardelijsten

Ook wel enumeraties genoemd, hebben Vastewaardelijsten in IMBOR een wisselende status.
Voor sommige eigenschappen is de vastewaardelijst een sluitende en complete lijst van mogelijke waarden.
Voor andere eigenschappen is het eerder een suggestielijst. In de LinkedData IMBOR wordt hier vooralsnog geen
onderscheidt in gemaakt:

<div class="issue" data-number="42"></div>

Conform NTA 8035 zijn vastewaardelijsten geïmplementeerd met behulp van superclasses die geïnstantieerd worden door
de individuele waardes.


### Raakvlakken / onderdelen

IMBOR definieert een aantal relaties _tussen_ objecten, zoals beschreven in onderstaande tabel.

ObjectType | ObjectTypeNiveau1
---------- | -----------------
TerreindeelSoortnaam | Terreindeel
WegasVerkeersintensiteit | Wegas
WegasVerkeerstellingJaar | Wegas
WegasVerkeerstelling | Wegas
VerhardingsobjectRand | Verhardingsobject
GroenobjectConstructielaag | Groenobject
GroenobjectSoortnaam | Groenobject
GroenobjectRand | Groenobject
SluisDoorvaart | Sluis
KunstwerkOpening | Kunstwerk
VerhardingsobjectConstructielaag | Verhardingsobject

De objecttypen in de rechterkolom relateren aan de objecten (deze worden 'hulpobjecten' genoemd) uit de linkerkolom
doormiddel van de `nta8035:hasPart`.
Binnen IMBOR-LD hanteren we alle raakvlakken voorlopig als 'onderdeel van' (vandaar `nta8035:hasPart`):

<div class="issue" data-number="16"></div>

Doormiddel van SHACL shapes worden combinaties gemaakt voor ObjectType en (Hulp)ObjectType. Deze (Hulp)ObjectTypen
zijn bij IMBOR geen Beheerobject en staan daarmee voorlopig nog los in de taxonomie.
Voor de combinatie van fysieke objecten en hun onderdelen geldt nagenoeg dezelfde constructie als voor de
[eigenschappen](#shapes). Alleen verwijst de `sh:path` naar de `nta8035:hasPart`.

### Organiserende elementen

IMBOR bevat meerdere elementen die er voor zorgen dat de inhoud vanuit een bepaald perspectief geraadpleegd kan
worden. Twee van deze zijn overgenomen in de LinkedData versie.
* Vakdisciplines
* IMBOR hiërarchie
Binnen LinkedData wordt veel gebruik gemaakt van de [SKOS ontologie](https://www.w3.org/2004/02/skos/) (een W3C
aanbeveling) om simpele organiserende structuren op te zetten.
De NTA8035 beveelt het ook aan om op deze manier te doen.

#### Vakdisciplines

De IMBOR vakdisciplines zijn allemaal een `skos:collection` en `skos:member` van
`groep:IMBORVakdisciplineCollectie`. Zodoende is terug te vinden welke vakdisciplines er zijn.
Per vakdisciplines is vervolgens weer met `skos:member` aangeven welke fysieke objecten binnen die vakdisciplines
vallen. Objecten kunnen overigens in meerder vakdisciplines vallen.
Hoewel deze vastlegging semantisch weinig waarde heeft, kan het handig zijn om de IMBOR content te raadplegen.

#### IMBOR Hiërarchie

Alle objecten binnen IMBOR bestaan binnen een hiërarchie. Deze hiërarchie bestaat binnen IMBOR met name om aan te
geven wat objecttypen zijn en
om eigenschappen van toepassing te verklaren op alle onderliggende objecten. Binnen de LinkedData versie van IMBOR
wordt dit automatisch geregeld door `rdfs:subClassOf`.
Vandaar dat deze hiërarchie niet meer in die hoedanigheid terug te vinden is. Om wel de herkenbaarheid te behouden
zijn is de hiërarchie ook opgenomen middels SKOS.
Er bestaat de collectie: `groep:IMBORHierarchischeCollectie`, deze heeft de `skos:member`:
* `groep:Objecttypegroep`
* `groep:Objecttype`
* `groep:Type`
* `groep:TypeGedetailleerd`
* `groep:TypeExtraGedetailleerd`

Deze collecties hebben weer als `skos:member` fysieke objecten.
Hoewel deze vastlegging semantisch weinig waarde heeft, kan het handig zijn om de IMBOR content te raadplegen.

