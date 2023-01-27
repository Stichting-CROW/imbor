## (Open)standaarden

Deze best practice maakt _alleen_ gebruik van (inter)nationale open standaarden en bestaande technieken. Hieronder wordt elke standaard/techniek toegelicht en wordt er verwezen naar de plek waar de standaard/techniek gevonden kan worden.

### RDF
‘Resource Description Framework’ (RDF) [[rdf11-primer]] is een standaard van het ‘World Wide Web Consortium’ (<abbr title="World Wide Web Consortium">W3C</abbr>), welke wordt gebruikt om data voor te delen en uit te wisselen. Met RDF worden statements gemaakt in de vorm van een drieledige subject-predicaat-object-structuur (in RDF-termen een triple). Het subject is in essentie de resource die beschreven wordt. Het predicaat is welk kenmerk of aspect van die bron beschreven wordt. Het object ten slotte is wat de waarde van dat kenmerk is. Het is ontworpen om gebaseerd op de bestaande web technieken eenduidig en software onafhankelijk data te delen. RDF is één van de belangrijkste onderdelen van het semantisch web. 

### RDFS
‘RDF Schema’ (<abbr title="RDF Schema">RDFS</abbr>)[[rdf-schema]] is een uitbreiding op RDF [[rdf11-primer]]. Het is een set van klassen met bepaalde eigenschappen. Het voorziet in basiselementen voor een ontologie, bijvoorbeeld de belangrijke `rdfs:subClassOf`.

### SHACL
De ‘Shapes Constraint Language’ (<abbr title="Shapes Constraint Language">SHACL</abbr>) [[shacl]] is een taal voor het definiëren van data schema's, waarmee de toegestane/geldige structuur en inhoud van RDF-data met behulp van SHACL-shapes in detail gespecificeerd kan worden. Het gebruikt RDFS en is ook een standaard van W3C en is wijd geadopteerd. Om zeker te weten dat de geëxporteerde en getransformeerde gegevens conform zijn kan een SHACL-validatie gedaan worden.

### SPARQL
‘SPARQL Protocol And RDF Query Language’ (<abbr title="SPARQL Protocol And RDF Query Language">SPARQL</abbr>) [[rdf-sparql-query]] is de tegenhanger van het meer bekende SQL. Met SPARQL kunnen zoekopdrachten (queries) op RDF gebaseerde data afgevuurd worden. Het is ook een standaard van W3C en is wijd geadopteerd. 

### GeoSPARQL
‘GeoSPARQL’ [[geosparql]] is zowel een beknopte ontologie voor geo-informatie als een uitbreiding op SPARQL met functionaliteit voor ruimtelijke vragen (in de buurt van, overlapt met, etc.). GeoSPARQL is gestandaardiseerd bij het Open Geospatial Consortium in samenwerking met het W3C. 

### WKT
[‘Well-known text’(WKT)][5] is een tekstmarkeertaal voor het representeren van objecten met een (vector)-geometrie. In essentie betreft het een uitleg hoe men een tekst string moet opbouwen om verschillende soorten geometrie te kunnen representeren. Het is gestandaardiseerd bij het Open Geospatial Consortium. 

### Turtle
‘Terse RDF Triple Language’ (<abbr title="Terse RDF Triple Language">Turtle</abbr>) [[turtle]], is een serialisatieformaat voor RDF. Turtle biedt een systematiek om drie URI's steeds te groeperen tot een triple en op die manier informatie op te bouwen en de onderlinge relaties aan te geven. Het is ook een standaard van W3C en is wijd geadopteerd. 

### JSON-LD
<abbr title="JavaScript Object Notation for Linked Data">JSON-LD</abbr> [[json-ld]], of ‘JavaScript Object Notation for Linked Data’, is een methode om LinkedData over te dragen via JSON. Ofwel een serialisatieformaat voor RDF.  Het is een eenvoudige omzetting van <abbr title="JavaScript Object Notation">JSON</abbr> naar een semantisch formaat. Zo kunnen gegevens op vergelijkbare wijze met de traditionele JSON worden geserialiseerd. Het is een ook W3C standaard.

>ADVISEMENT "Keuze voor serialisatie"
> 
>Het is absoluut arbitrair voor welke serialisatie er gekozen wordt. Het voordeel van RDF is dat de data (de statements, of de triples) altijd helemaal hetzelfde zijn. 

### NEN2660-2
<abbr title="Regels voor informatiemodellering van de gebouwde omgeving - Deel 2: Praktische configuratie, extensie en implementatie van NEN 2660-1  ">NEN2660-2</abbr> [[NEN2660_2]] is een praktische invulling van [[NEN2660_1]]. In deel 1 zijn meer theoretische/conceptuele en bouw- en taalonafhankelijke modelleerpatronen vastgelegd. Deze norm is vrij beschikbaar bij de NEN en is ontwikkeld in een samenwerking tussen overheden, adviesbureau's en kennisinstituten. Het heeft als doel de standaard te zijn voor de ontwikkeling van ontologieën in de gebouwde omgeving. Het bevat drie belangrijke (hoofd)onderdelen:
* Een praktisch toplevelmodel waarin genoeg semantiek aangegeven wordt om IMBOR in uit te drukken;
* Extensies hierop voor de meest gebruikt toepassingen in de gebouwde omgeving;
* Taalbinding naar (en daarmee de keuze voor) de semantisch web W3C talen: <abbr title="Simple Knowledge Organization System">SKOS</abbr> [[skos-primer]], RDFS [[rdf-schema]], <abbr title="Web Ontology Language">OWL</abbr> [[owl2-primer]] en SHACL [[shacl]].

IMBOR volgt volledig deze norm (zie [toelichting][3]) en daarmee is het ook aan te bevelen de [NEN2660-2][1] goed door te nemen en te volgen.

### IMBOR
 
De [IMBOR-ontologie][4] is een extensie van het NEN2660-2 praktisch toplevel model. De relatie tussen IMBOR en de NEN2660-2 wordt in de [technische documentatie][2] van IMBOR toegelicht. De IMBOR-ontologie bevat alle klassen, attributen, domeinwaarden, relaties, etc. die nodig zijn om een gegevensset te maken voor areaaldata. 

[1]: https://www.nen.nl/nen-2660-2-2022-nl-291667
[2]: https://docs.crow.nl/imbor/techdoc/#imbor-samenhang-en-hierarchie
[3]: https://docs.crow.nl/imbor/techdoc/#nen2660-2
[4]: https://docs.crow.nl/onto-verkenner/imbor/
[5]: https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry