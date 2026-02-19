### Valideren met Apache Jena

##### Wat is een SHACL-engine?

Een SHACL-shapes-bestand op zichzelf doet nog niets: het beschrijft alleen de regels waaraan data moet voldoen. Om die regels daadwerkelijk toe te passen op een dataset, is een SHACL-engine nodig. Een SHACL-engine is een softwarecomponent die een shapes-bestand inleest samen met een RDF-databestand, de data systematisch langsloopt en controleert of elk object voldoet aan de shapes die erop van toepassing zijn. Het resultaat is een validatierapport dat precies aangeeft welke objecten de regels overtreden, welk attribuut ontbreekt of een ongeldige waarde heeft, en bij welke shape de fout hoort.

##### Waarom Apache Jena?

<a href="https://jena.apache.org/documentation/shacl/">Apache Jena</a> is een open-source Java-framework voor het bouwen van linked-data- en RDF-toepassingen. Het biedt onder andere tools voor het opslaan, bevragen (via SPARQL) en verwerken van RDF-data. Sinds versie 3.14 bevat Jena ook een ingebouwde SHACL-processor, waarmee shapes-validatie direct vanuit de command line of via de Java-API uitgevoerd kan worden.

Wij hebben gekozen voor Apache Jena omdat deze engine in de praktijk het snelst blijkt bij het valideren van grote datasets. Een alternatief is <a href="https://github.com/RDFLib/pySHACL/">PySHACL</a>, een Python-bibliotheek die dezelfde functionaliteit biedt maar bij omvangrijke bestanden merkbaar langzamer is.

##### Hoe werkt de validatie?

Jena kan via de command-line-tool shacl validate worden aangeroepen met twee bestanden als invoer: het shapes-bestand (de regels) en het databestand (de te controleren objecten). De engine loopt vervolgens elk object in de data langs, bepaalt op basis van het type van het object welke NodeShape van toepassing is, en controleert of alle bijbehorende PropertyShapes worden nageleefd. Het resultaat is een validatierapport in RDF-formaat dat per overtreding aangeeft welk object het betreft, welk attribuut ontbreekt of incorrect is, en bij welke shape de fout hoort.

##### Hoe ziet het shapes-bestand eruit?

Het Turtle-bestand bevat per objecttype een blok dat er conceptueel zo uitziet:

Een NodeShape die zegt: "Ik richt me op alle objecten van type X", gevolgd door verwijzingen naar één of meer PropertyShapes. Elke PropertyShape zegt: "Het attribuut Y moet minimaal één keer aanwezig zijn."

Concreet betekent dit dat als een object van type "Boom" wordt aangeleverd zonder het attribuut "Hoogte", de SHACL-validatie een foutmelding genereert die exact aangeeft welk object het betreft en welk attribuut ontbreekt.

##### Hoe ziet een validatierapport eruit?

Wanneer de validatie overtredingen vindt, produceert Jena een rapport in Turtle-formaat. Dit rapport bevat een overkoepelend resultaat dat aangeeft of de data als geheel wel of niet conform is (sh:conforms true of false). Bij elke overtreding wordt een apart resultaatblok opgenomen dat drie kerngegevens bevat: het object dat de regel overtreedt (het zogenoemde focus node), het attribuut dat ontbreekt of een ongeldige waarde heeft (het result path), en een leesbare foutmelding die beschrijft wat er mis is. Zo kan een rapport bijvoorbeeld melden dat het object imbor:Boom_42 niet voldoet aan de shape voor het type "Boom" omdat het verplichte attribuut "Hoogte" ontbreekt. Op die manier is in één oogopslag zichtbaar welke objecten aandacht nodig hebben en wat er precies moet worden aangevuld.
