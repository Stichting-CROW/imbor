## Semantische relaties

***Gebaseerd op GitHub issues: [1541](https://github.com/Stichting-CROW/imbor/issues/1541), [1192](https://github.com/Stichting-CROW/imbor/issues/1192), [1101](https://github.com/Stichting-CROW/imbor/issues/1101), [1546](https://github.com/Stichting-CROW/imbor/issues/1546) en [1684](https://github.com/Stichting-CROW/imbor/issues/1684)***

Vanaf IMBOR2022 is het concept 'Semantische relaties' geïntroduceerd. Dit wordt beschreven in de [technische documentatie](https://docs.crow.nl/imbor/techdoc/#semantische-relaties). Hierbij wordt de uitleg gegeven dat er in de IMBOR ontologie per `Klasse` een aanzet gegeven wordt van de belangrijkste relaties die voorkomen. Het staat de gebruiker van IMBOR vrij om binnen de gezette kaders meer relaties op `Objecttype`n te leggen. De gezette kaders betreffen de relaties zoals vastgelegd in de ontologie, beschreven in de technische documentatie en zoals ze afgebeeld zijn in de [top hiërarchie](https://docs.crow.nl/imbor/techdoc/#imbor-top-hierarchie). Onderstaande tabel zet deze op een rij.

| Relatie              | Bron                                                                                                                                                                   | Van              | Naar                         |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|------------------------------|
| `isSubtypeVan`       | [rdfs:subClassOf](http://www.w3.org/2000/01/rdf-schema#)                                                                                                               |                  |                              |
| `heeftDeel`          | [nen2660:hasPart](https://w3id.org/nen2660/def#hasPart)                                                                                                                | Object           | Object                       |
| `isVerbondenMet`     | [nen2660:isConnectedTo](https://w3id.org/nen2660/def#isConnectedTo)                                                                                                    | FysiekObject     | FysiekObject                 |
| `isBeschrevenDoor`   | [nen2660:isDescribedBy](https://w3id.org/nen2660/def#isDescribedBy)                                                                                                    | Object           | InformatieObject             |
| `bevat`              | [nen2660:contains](https://w3id.org/nen2660/def#contains)                                                                                                              | RuimtelijkGebied | ReeelObject                  |
| `heeftBegrenzing`    | [nen2660:hasBoundary](https://w3id.org/nen2660/def#hasBoundary)                                                                                                        | FysiekObject     | GeometrischeRepresentatie    |
| `voertUit`           | [nen2660:executes](https://w3id.org/nen2660/def#executes)                                                                                                              | FysiekObject     | Functie                      |
| `bestaatUit`         | [nen2660:consistsOf](https://w3id.org/nen2660/def#consistsOf)                                                                                                          | ReeelObject      | Materie                      |
| `heeftBetrekkingOp`  | NEN2660-1                                                                                                                                                              | Rol              | Geo-Object; InformatieObject |
| `speelt`             | NEN2660-1                                                                                                                                                              | Actor            | Rol                          |
| `isGeregistreerdMet` | [registratiegegevens](https://modellen.geostandaarden.nl/def/nen3610-2022/index.html#registratiegegevens) uit de [[NEN3610]]                                           |                  |                              |
| `startNode`          | [net:startNode](https://github.com/inspire-eu-rdf/inspire-rdf-vocabularies/blob/7dde22fde631409957a445f97af5868299f2330e/net/net.ttl#L286) uit INSPIRE via [[NEN3610]] | NetwerkLink      | NetwerkNode                  |
| `endNode`            | [net:endNode](https://github.com/inspire-eu-rdf/inspire-rdf-vocabularies/blob/7dde22fde631409957a445f97af5868299f2330e/net/net.ttl#L66) uit INSPIRE via [[NEN3610]]    | NetwerkLink      | NetwerkNode                  |
| {.def}               |                                                                                                                                                                        |

Voor de relatie `isGeregistreerdMet` geldt dat deze eigenlijk alleen gebruikt wordt voor registratiegegevens. Hiervoor wordt verwezen naar 'temporele aspecten' [techdoc](https://docs.crow.nl/imbor/techdoc/#temporele-aspecten) en in deze [best practice](#nen3610-temporele-aspecten)

### Overerving

De relatie `isSubtypeVan` is de allerbelangrijkste relatie hier, omdat deze tussen alles kan gelden (indien van hetzelfde type). Het principe van 'overervering' geldt hier. Doordat `FysiekObject` en subtype is van (of: hoort bij de klasse van) `Object` gelden alle relaties van `Object` ook voor `FysiekObject`. Deze hiërarchie (ofwel: taxonomie) is daarmee leidend voor de relaties die mogen voorkomen. Hier gelden deze hele belangrijke regels (aan de hand van een voorbeeld): 

* __Vanuit IMBOR wordt gesteld dat _alle_ dingen die direct of indirect een subtype zijn van een `Object` een `hasPart` relatie _mogen_ hebben naar _alle_ dingen die direct of indirect een subtype zijn van `Object`, maar dan ook _alleen_ van `Object`.__
* __IMBOR is dus _niet_ voorschrijvend welke tussen welke subtypen van `Object` deze `hasPart` relatie mag voorkomen.__

### Relaties op abstracte klassen

Relaties liggen in IMBOR op het niveau van `Klasse`n. Daarbij is het onderscheid tussen *abstracte* en *concrete* entiteiten van belang (zie ook de [top hiërarchie](https://docs.crow.nl/imbor/techdoc/#imbor-top-hierarchie)):

* Een `Klasse` (bijvoorbeeld `FysiekObject` of `Verharding`) is **abstract** en kan niet geïnstantieerd worden.
* Een `Objecttype` (`Boom`, `Asfaltverharding`, `Elementenverharding`) of `InformatieObject` is **concreet** en wél instantieerbaar, bijvoorbeeld in een beheerpakket.

Een relatie wijst daardoor vaak naar een abstracte `Klasse`. Via [overerving](#overerving) is die dan toegestaan naar *elk* concreet subtype. Bij het vastleggen leg je de relatie echter altijd tussen twee **concrete** instanties, nooit naar een abstracte `Klasse`.

>EXAMPLE
>In IMBOR staat `Boom` → `isVerbondenMet` → `Verharding`. `Verharding` is abstract en niet instantieerbaar; leg de relatie daarom naar een concreet subtype, bijvoorbeeld `Boom123` → `isVerbondenMet` → `Asfaltverharding456`.

>ADVISEMENT
>Lees een relatie naar een abstracte `Klasse` dus als: "toegestaan naar alle concrete subtypen". Kies bij registratie het passende concrete `Objecttype`.

### Multipliciteit

Bij de relaties die in IMBOR worden aangegeven wordt altijd een multipliciteit (of: kardinaliteit) aangegeven. Hiermee worden soms dus _wel_ bepaalde beperkingen opgelegd. 'Kolk' en 'Deksel' zijn allebei `FysiekObject`. Dus is het mogelijk om een relatie `hasPart` tussen deze twee te leggen. In IMBOR wordt echter voorgeschreven dat deze relatie een multipliciteit van '1 op 1' heeft. Als er dus een instantie van een 'Kolk' bestaat _moet_ er ook een `hasPart` relatie zijn naar een instantie van een `Deksel`. 


### Toepassing semantische relaties

Een veel gebruikte relatie binnen assetbeheersystemen is de 'heeft deel' relatie. Hiermee worden onderdelen beschreven in de vorm van een decompositie (of meronomie). Deze relatie is één van de voorbeelden van de relaties die binnen IMBOR gebruikt (mogen) worden. Maar in deze best practice wordt deze als case genomen. 

>EXAMPLE
>Binnen IMBOR worden een aantal relaties beschreven over een 'Viaduct', waaronder: 'Viaduct heeft deel Dek' (1:N) en 'Viaduct heeft deel Pijler' (0:N). Maar er is geen relatie tussen 'Viaduct' en 'Muur' gedefinieerd. Er is uiteraard wel de mogelijkheid om een 'heeft deel' relatie te leggen tussen 'Viaduct' en 'Muur' omdat deze beiden subklassen zijn van `FysiekObject`. 
>
>Er bestaat in gemeente X een 'Viaduct' waar een 'Muur' op gebouwd wordt. Daarom wil gemeente X vastleggen dat dit bepaalde 'Viaduct 123' bestaat uit één dek, twee pijlers en één in aanleg zijnde muur. _Uiteraard is dit een gekunsteld voorbeeld. Om aan te tonen dat er vanuit IMBOR nooit alles voorspelt kan worden wat er in de praktijk nodig is_

Dit is een voorbeeld-uitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/semantische-relaties.ttl" data-include-format="text"></code></pre>
