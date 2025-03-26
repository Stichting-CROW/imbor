## Semantische relaties

***Gebaseerd op GitHub issues: [1541](https://github.com/Stichting-CROW/imbor/issues/1541), [1192](https://github.com/Stichting-CROW/imbor/issues/1192), [1101](https://github.com/Stichting-CROW/imbor/issues/1101) en [1546](https://github.com/Stichting-CROW/imbor/issues/1546)***

Vanaf IMBOR2022 is het concept 'Semantische relaties' geïntroduceerd. Dit wordt beschreven in de [technische documentatie](https://docs.crow.nl/imbor/techdoc/#semantische-relaties). Hierbij wordt de uitleg gegeven dat er in de IMBOR ontologie per `Klasse` een aanzet gegeven wordt van de belangrijkste relaties die voorkomen. Het staat de gebruiker van IMBOR vrij om binnen de gezette kaders meer relaties op `Objecttype`n te leggen. De gezette kaders betreffen de relaties zoals vastgelegd in de ontologie, beschreven in de technische documentatie en zoals ze afgebeeld zijn in de [top hiërarchie](https://docs.crow.nl/imbor/techdoc/#imbor-top-hierarchie). Onderstaande tabel zet deze op een rij.

| Relatie              | Bron                                                                                                                                                                   | Van               | Naar                         |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|------------------------------|
| `isSubtypeVan`       | [rdfs:subClassOf](http://www.w3.org/2000/01/rdf-schema#)                                                                                                               |                   |                              |
| `heeftDeel`          | [nen2660:hasPart](https://w3id.org/nen2660/def#hasPart)                                                                                                                | Object            | Object                       |
| `isVerbondenMet`     | [nen2660:isConnectedTo](https://w3id.org/nen2660/def#isConnectedTo)                                                                                                    | FysiekObject      | FysiekObject                 |
| `isBeschrevenDoor`   | [nen2660:isDescribedBy](https://w3id.org/nen2660/def#isDescribedBy)                                                                                                    | Object            | InformatieObject             |
| `bevat`              | [nen2660:contains](https://w3id.org/nen2660/def#contains)                                                                                                              | RuimtelijkeGebied | ReeelObject                  |
| `heeftBegrenzing`    | [nen2660:hasBoundary](https://w3id.org/nen2660/def#hasBoundary)                                                                                                        | FysiekObject      | GeometrischeRepresentatie    |
| `voertUit`           | [nen2660:executes](https://w3id.org/nen2660/def#executes)                                                                                                              | FysiekObject      | Functie                      |
| `bestaatUit`         | [nen2660:consistsOf](https://w3id.org/nen2660/def#consistsOf)                                                                                                          | ReeelObject       | Materie                      |
| `heeftBetrekkingOp`  | NEN2660-1                                                                                                                                                              | Rol               | Geo-Object; InformatieObject |
| `speelt`             | NEN2660-1                                                                                                                                                              | Actor             | Rol                          |
| `isGeregistreerdMet` | [registratiegegevens](https://modellen.geostandaarden.nl/def/nen3610-2022/index.html#registratiegegevens) uit de [[NEN3610]]                                           |                   |                              |
| `startNode`          | [net:startNode](https://github.com/inspire-eu-rdf/inspire-rdf-vocabularies/blob/7dde22fde631409957a445f97af5868299f2330e/net/net.ttl#L286) uit INSPIRE via [[NEN3610]] | NetwerkLink       | NetwerkNode                  |
| `endNode`            | [net:endNode](https://github.com/inspire-eu-rdf/inspire-rdf-vocabularies/blob/7dde22fde631409957a445f97af5868299f2330e/net/net.ttl#L66) uit INSPIRE via [[NEN3610]]    | NetwerkLink       | NetwerkNode                  |
| {.def}  | |

Voor de relatie `isGeregistreerdMet` geldt dat deze eigenlijk alleen gebruikt wordt voor registratiegegevens. Hiervoor wordt verwezen naar 'temporele aspecten' [techdoc](https://docs.crow.nl/imbor/techdoc/#temporele-aspecten) en in deze [best practice](#nen3610-temporele-aspecten)

### Overerving

De relatie `isSubtypeVan` is de allerbelangrijkste relatie hier, omdat deze tussen alles kan gelden (indien van hetzelfde type). Het principe van 'overervering' geldt hier. Doordat `FysiekObject` en subtype is van (of: hoort bij de klasse van) `Object` gelden alle relaties van `Object` ook voor `FysiekObject`. Deze hiërarchie (ofwel: taxonomie) is daarmee leidend voor de relaties die mogen voorkomen. Hier gelden deze hele belangrijke regels (aan de hand van een voorbeeld): 

* __Vanuit IMBOR wordt gesteld dat _alle_ dingen die direct of indirect een subtype zijn van een `Object` een `hasPart` relatie _mogen_ hebben naar _alle_ dingen die direct of indirect een subtype zijn van `Object`, maar dan ook _alleen_ van `Object`.__
* __IMBOR is dus _niet_ voorschrijvend welke tussen welke subtypen van `Object` deze `hasPart` relatie mag voorkomen.__

### Multipliciteit

Bij de relaties die in IMBOR worden aangegeven wordt altijd een multipliciteit (of: kardinaliteit) aangegeven. Hiermee worden soms dus _wel_ bepaalde beperkingen opgelegd. 'Kolk' en 'Deksel' zijn allebei `FysiekObject`. Dus is het mogelijk om een relatie `hasPart` tussen deze twee te leggen. In IMBOR wordt echter voorgeschreven dat deze relatie een multipliciteit van '1 op 1' heeft. Als er dus een instantie van een 'Kolk' bestaat _moet_ er ook een `hasPart` relatie zijn naar een instantie van een `Deksel`. 


### Toepassing semantische relaties in IMBOR

Een veel gebruikte relatie binnen assetbeheersystemen is de 'heeft deel' relatie. Hiermee worden onderdelen beschreven in de vorm van een decompositie (of meronomie). Deze relatie is één van de voorbeelden van de relaties die binnen IMBOR gebruikt (mogen) worden. Maar in deze best practice wordt deze als case genomen. 

>EXAMPLE
>Binnen IMBOR worden een aantal relaties beschreven over een 'Viaduct', waaronder: 'Viaduct heeft deel Dek' (1:N) en 'Viaduct heeft deel Pijler' (0:N). Maar er is geen relatie tussen 'Viaduct' en 'Muur' gedefinieerd. Er is uiteraard wel de mogelijkheid om een 'heeft deel' relatie te leggen tussen 'Viaduct' en 'Muur' omdat deze beiden subklassen zijn van `FysiekObject`. 
>
>Er bestaat in gemeente X een 'Viaduct' waar een 'Muur' op gebouwd wordt. Daarom wil gemeente X vastleggen dat dit bepaalde 'Viaduct 123' bestaat uit één dek, twee pijlers en één in aanleg zijnde muur. _Uiteraard is dit een gekunsteld voorbeeld. Om aan te tonen dat er vanuit IMBOR nooit alles voorspelt kan worden wat er in de praktijk nodig is_

Dit is een voorbeeld-uitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix nen2660: <https://w3id.org/nen2660/def#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.

gemX:Viaduct123 a   imbor:e13e2867-bc61-462a-bcba-a8570c863a75 ;                        # Viaduct
                imbor:ee97b257-d3b8-4d0c-9a42-c07d88b36d9f "Viaduct 123"@nl ;           # naam
                nen3610:domein  "http://voorbeeld.org/gemX#" ;              
                nen3610:identificatie   "Viaduct123" ;
                imbor:4e721262-e6e2-41df-bb99-0b6693e32435                              # status
                        imbor-domeinwaarde:01a31554-111c-4765-82cb-79f0b178eb8e         # in gebruik
                nen2660:hasPart   
                        gemX:Dek123, gemX:Pijler123a, gemX:Pijler123b, gemX:Muur123 ;   # heeft deel   
                .

gemX:Dek123      a  imbor:f3202a49-5227-45e2-92d0-826ce6cf5974 ;                        # Dek
                nen3610:domein  "http://voorbeeld.org/gemX#" ;
                nen3610:identificatie "Dek123" ;
                imbor:4e721262-e6e2-41df-bb99-0b6693e32435                              # status
                        imbor-domeinwaarde:01a31554-111c-4765-82cb-79f0b178eb8e ;       # in gebruik
                .

gemX:Pijler123a a   imbor:8fb333fc-e296-4619-a84b-fac4e8f704e8 ;                        # Pijler
                nen3610:domein  "http://voorbeeld.org/gemX#" ;
                nen3610:identificatie "Pijler123a" ;
                imbor:4e721262-e6e2-41df-bb99-0b6693e32435                              # status
                        imbor-domeinwaarde:01a31554-111c-4765-82cb-79f0b178eb8e ;       # in gebruik
                .

gemX:Pijler123b a   imbor:8fb333fc-e296-4619-a84b-fac4e8f704e8 ;                        # Pijler
                nen3610:domein  "http://voorbeeld.org/gemX#" ;
                nen3610:identificatie "Pijler123b" ;
                imbor:4e721262-e6e2-41df-bb99-0b6693e32435                              # status
                    imbor-domeinwaarde:01a31554-111c-4765-82cb-79f0b178eb8e ;           # in gebruik
                .

gemX:Muur123    a   imbor:9cbafabd-ef5f-4121-a63a-57da752300e5 ;                        # Muur
                nen3610:domein  "http://voorbeeld.org/gemX#" ;
                nen3610:identificatie "Muur123" ;
                imbor:4e721262-e6e2-41df-bb99-0b6693e32435                              # status
                    imbor-domeinwaarde:d759852d-910a-4faa-90c3-20ee9745925f ;           # in aanleg
                .

```