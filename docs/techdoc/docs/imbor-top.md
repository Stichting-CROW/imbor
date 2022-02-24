## IMBOR samenhang en hiërarchie

IMBOR wordt gepositioneerd als sectormodel. De focus ligt op de vaste gegevens van objecten die herkend worden voor het beheer van de openbare ruimte. Kijkend naar het landschap waarin IMBOR wordt gebruikt zijn er veel raakvlakken met landelijke, maar ook andere sectorale modellen. Om deze afstemming zo optimaal te laten verlopen is getracht om de top van de IMBOR hiërarchie (ofwel de klassenindeling) zo veel mogelijk aan te laten sluiten op andere modellen. Dit is gedaan om enerzijds niet zaken zelf te verzinnen, maar zaken aan te vullen. En anderzijds om uiteindelijk een semantisch sterke mapping tussen de sectorale modellen mogelijk te kunnen maken. Wanneer sectorale modellen allemaal gebaseerd zijn op dezelfde uitgangspunten is het makkelijkere om onderin de boom de vergelijking te kunnen maken. Vandaar dat voor IMBOR2022 gekozen is om gebruik te maken van een polyhiërarchie gebaseerd op respectievelijk de NEN2660-2, de NEN3610, de SOR, het IMGeo2.2, het IMKL2.0 en het IMWV. 

### IMBOR Top hiërarchie

In onderstaand diagram is de top van de hiërarchie te vinden, met in kleur aangegeven waar de concepten vandaan komen. De relaties tussen de NEN2660-2 en de NEN3610 komen uit de NEN2660-2 documentatie zelf. En de relaties tussen de NEN3610 en de SOR komen uit de documentatie van de SOR zelf. Deze indeling zorgt ervoor dat voor alle IMBOR Objecttypen (niet afgebeeld) er een logische hiërarchie is, waarmee duidelijk is hoe deze zich verhoudt tot de landelijke standaarden. Te zien is dat er zeer weinig IMBOR specifieke klassen geïntroduceerd hoeven te worden omdat bijna alles al voldoende gedefinieerd wordt. Alle (ongeveer 500) Objecttypen hebben worden aan één of meerdere van deze klassen gehangen en krijgen hiermee een landelijke semantische definitie. De hiërarchie wordt tevens gebruikt om de attributen mee te distribueren, maar deze hebben (nog) geen landelijk/sectoraal kader. Hiermee wordt bedoeld dat dit diagram meer gebruikt moet worden als 'begrippenkader'(lees: de semantische afstemming van de modellen) dan dat het daadwerkelijk als een volwaardige ontologie ingezet kan worden. Dit is niet per se mogelijk omdat er geen volledige afstemming is tussen de attributen en onderlinge relaties.

<figure>

![IMBOR 2022 Top hiërarchie](img/IMBOR2022-top.drawio.svg?raw=true)
    
<figcaption><figcaption>IMBOR Top van de ontologie -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption></figcaption>
</figure>


#### Definities in hiërarchie

Al deze concepten kennen definities. Omdat er geen semantische discussies gevoerd kunnen worden zonder dat de definities van de concepten bekend zijn worden ze hieronder uiteengezet. _(Dit betreft een extract uit de SVG/XML)_

* __Aanschaf-informatie__: Verzameling van gegevens die te maken hebben met de monetaire waarde van een object.
* __Activiteit__: Iets dat mogelijk of daadwerkelijke gebeurt in ruimte en tijd.
* __Apparaat__: Een (vaak compact) mechanisch of elektronisch ding dat is gemaakt of toegepast voor een specifieke toepassing en doorgaans in één behuizing gevat is.
* __Bak__: Object met een permanent karakter dat dient om iets in te bergen of te verzamelen.
* __Begroeiing__: Planten die op natuurlijke wijze zijn ontstaan of door mensen zijn aangeplant.
* __Beheerd object__: Object welke door een organisatie beheerd wordt in de beheerfase van zijn levenscyclus.
* __Bereikbaarheid-informatie__: Registratie van gegevens die betrekking hebben op de bereikbaarheid van het object.
* __Bodem__: Bovenste begrenzing van het aardoppervlak, exclusief oppervlaktewater
* __Bord__: Een paneel waarop informatie wordt afgebeeld.
* __Bordopschrift__: Informatieobject voor het vastleggen van de informatie op een bord.
* __Bouwwerk__: Gegevens die specifiek zijn voor een met de aarde verbonden duurzaam bouwwerk, dat niet valt onder de definities van een pand of kunstwerk.
* __Certificering-informatie__: De verzameling van gegevens die gebruikt kan worden voor de wijze waarop een object gecertificeerd is.
* __Complex__: Functionele ruimte die een verzameling van één of meer gebouwen, constructies, verharding, water en begroeiing betreft die samen een eenheid vormen.
* __Constructie__: Gebouwd object dat direct of indirect met de grond is verbonden en bedoeld is om ter plaatse te functioneren.
* __Constructielaag__: Laagopbouw onder begroeiing of verharding.
* __Constructieonderdeel__: Constructieonderdeel, onderdeel van een objecttype die als zelfstandig objecttype beheerd kan worden.
* __DiscreetObject__: Reëel object dat bestaat uit een aaneengesloten hoeveelheid vormvaste materie, primair bijeengehouden door interne krachten (zwaartekracht of elektromagnetische kracht)
* __Document__: Informatieobject voor het registreren en koppelen van documenten aan objecttypes.
* __Ecologische zone__: Functionele ruimte speciaal voor het registreren van functionele aandachts- en onderzoeksgebieden.
* __Flora en fauna-informatie__: Verzameling van gegevens die te maken hebben met het beheer van Flora en Fauna.
* __Functie__: Een activiteit die het externe gedrag beschrijft van het object die de activiteit uitvoert.
* __Functioneel gebouwobject__: Een gebouw gerelateerde ruimte met een specifieke functie.
* __Functionele ruimte__: Ruimte met een specifieke functie.
* __Functionele zonering__: Een gebied met een specifieke functie.
* __FunctioneleEntiteit__: Entiteit waarbij het gaat om het externe gedrag waarbij de uitvoer bijdraagt aan doelstellingen van belanghebbenden geïmplementeerd/gespeeld door een of meer technische entiteiten.
* __FysiekObject__: Iets dat mogelijk of daadwerkelijk bestaat in ruimte en tijd, waarneembaar door de zintuigen.
* __GM*__: GML features
* __Gebiedsindeling__: Object welke gegevens kent betreffende de vastlegging binnen registratieve ruimten.
* __Gebouw__: Overdekte en geheel of gedeeltelijk met wanden omsloten constructief zelfstandige eenheid bedoeld voor het in een afgeschermde omgeving onderbrengen van mensen, dieren of voorwerpen of voor de productie van goederen.
* __Gebouwcomponent__: Component aan de buitenzijde van een gebouw, die het aanzicht van het gebouw mede bepaalt
* __Gebruikszone oppervlaktewater__: Begrensd oppervlaktewatergebied dat een bepaald gebruik kent
* __Geo-object__:  &#9;Een fenomeen in de werkelijkheid, dat direct of indirect is geassocieerd met een locatie relatief ten opzichte van de aarde.
* __Geografische ruimte__: Ruimte die bekend staat onder een vanuit de historie of in de volksmond bekende benaming of een fysisch-geografische samenhang kent.
* __GeometrischeRepresentatie__: Een ruimtelijke representatie van een object.
* __Groenobject__: Kleinste functioneel onafhankelijk stukje van een begroeid terrein dat er binnen het objecttype Begroeiing van NEN 3610 wordt onderscheiden, met aaneengesloten vegetatie.
* __Holle leiding__: Holle leiding voor het doorstromen van gassen, vloeistoffen of capsules, bestemd om hetzij gas, een vloeistof of capsules te transporteren, hetzij een vloeistof als intermediair te gebruiken voor het transport van warmte of een opgeloste of verpulverde stof.
* __Hulplijn__: Lijnvormig element wat vaak gebruik wordt in combinatie met andere objecttypen.
* __IMKLBasis object__:  Abstract data object dat de basis attributen bevat van de IMKL extensie. 
* __InformatieObject__: Thing that is a whole of information on itself and has an own identit
* __Installatie-informatie__: Gegevens die betrekking hebben op de installatie van een object.
* __Installatie__: Constructie die een technisch samenhangend systeem betreft dat een bepaald doel dient
* __Inwinning-informatie__: Informatieobject voor het vastleggen van informatie m.b.t. de inwinning van een objecttype.
* __Jaarverkeerstelling__: Het vastleggen van het resultaat van alle verkeerstellingen op een wegas per jaar.
* __Juridische ruimte__: Ruimte waar een juridisch instrument beleid of regelgeving toepast.
* __Kabel__: Een geheel van geleiders welke voorzien zijn van één ommanteling en bestemd is voor transport van energie of data.
* __Kast__: Constructie met een permanent karakter dat dient om iets in te bergen en te beschermen
* __Kering__: Voorziening met een kerende functie
* __Kunstwerk__: Civieltechnisch werk voor de infrastructuur van wegen, water, spoorbanen, waterkeringen en/of leidingen.
* __Kunstwerkdeel__:   Onderdeel van een civieltechnisch werk voor de infrastructuur van wegen, water, spoorbanen, waterkeringen en/of leidingen
* __Leiding__: Een geheel van geleiders of ruimte welke voorzien zijn van één ommanteling en bestemd is voor transport van materie, data of energie.
* __Luchtvaartzone__: Functionele ruimte die in gebruik is voor luchtvaart
* __Luchtvaartruimte__: Verkeerruimte voor voertuigen die zich door de lucht verplaatsen.
* __Mast__: Hoge draagconstructie voor een installatie of het transport van energie en elektromagnetische straling
* __Materie__: Zuivere stof, chemische verbinding of mengsel
* __Memo__: Informatieobject voor het gebruik en de registratie van memo's bij een objecttype.
* __Monument-informatie__: Registratie van gegevens van monumentale objecten.
* __Onbepaald terrein__: Fysiek begrensd en zichtbaar terrein dat bij een gebouw hoort, dat niet verder wordt gedetailleerd in andere reële objecten en dat bestaat uit een mengvorm van verharding, water, begroeiing en/of constructies.
* __Onderhoud-informatie__: Gegevens die nodig zijn voor het plannen en registreren van het onderhoud van objecten.
* __Ondertunneling__: Ondergrondse of onder water gelegen verbinding tussen twee punten, aan beide einden voorzien van een open bakconstructie.
* __Opening kunstwerk__: Gegevens die betrekking hebben op de oplevering van een object.
* __Oplever-informatie__: Gegevens die betrekking hebben op de oplevering van een object.
* __Overbrugging__: Kunstwerk dat een beweegbare of vaste verbinding tussen twee punten betreft, die door water, een weg of anderszins gescheiden zijn, bestaande uit een brugdek/-bak met landhoofden en veelal gesteund door pijlers
* __Paalconstructie__: Lage draagconstructie voor onder meer installaties of borden
* __Plaatsbepalingspunt__: Een Plaatsbepalingspunt is een punt dat is ingemeten en vervolgens gebruikt is bij en onderdeel uitmaakt van de begrenzing (geometrie) van reële objecten.
* __Put__: Gegraven of geboorde kokervormige diepte waarin zich (vloei)stoffen bevinden.
* __Randgroenobject__: Gegevens die betrekking hebben op de oplevering van een object.
* __Randverhardingsobject__: Gegevens die betrekking hebben op de oplevering van een object.
* __Recreatiezone__:   Functionele ruimte die in gebruik is voor openlucht recreatie
* __Reëel object__: Geo-object dat zich geheel materieel manifesteert
* __ReëelObject__: Fysiek object (vormvast of niet-vormvast) dat in de werkelijkheid tastbaar en zichtbaar is (of kan zijn), door de mens gemaakt of natuurlijk ontstaan.
* __Registratie-informatie__: Metagegevens voor het vastleggen van wijzigingen van de objectgegevens. Deze gegevens kunnen ook gebruikt worden voor het vastleggen van de historie.
* __Registratieve ruimte__: Op basis van wet- of regelgeving afgebakende ruimte die als eenheid geldt van politiek/bestuurlijke verantwoordelijkheid of voor bedrijfsvoering.
* __RuimtelijkGebied__: Fysiek object dat een bepaald gebied omsluit zoals een vertrek, rijbaan en rivier, die wordt begrensd door reële objecten of andere ruimtelijke gebieden (bijvoorbeeld op basis van gebruik of conventie) en dat voornamelijk vloeibare of gasvormige hoeveelheid materie bevat.
* __Rurale beheerzone__: Een afgebakend gebied voor generieke beheerdoeleinden binnen het landelijk gebied.
* __Samengesteld rioleringsobject__: Klasse van rioleringsobjecten waarbinnen meerdere reële objecten een samenhangend, functioneel, geheel vormen.
* __Scheepvaartruimte__: Transportruimte voor voertuigen die zich over water verplaatsen .
* __Scheiding__: Kunstmatig obstakel met een werende functie.
* __Sensor__: Apparaat voor de meting van een fysieke grootheid (bijv. temperatuur, licht, druk, elektriciteit).
* __Sluisdoorvaart__: Gegevens die betrekking hebben op de oplevering van een object.
* __Software__: Informatieobject voor de registratie van basisgegevens van het programma (software) die binnen of die in directe relatie met het objecttype gebruikt wordt.
* __Soortnaamgroenobject__: Gegevens die betrekking hebben op de oplevering van een object.
* __Spoorverkeerruimte__: Transportruimte voor voertuigen die zich over rails verplaatsen.
* __Spoorzone__: Functionele ruimte die in gebruik is voor spoorwegen
* __Straatmeubilair__: Een ruimtelijk object ter inrichting van de openbare ruimte.
* __TechnischEntiteit__: Entiteit waarbij het gaat om de technische eigenschappen die nul of meerdere functionele entiteiten implementeert of speelt.
* __TopologischElement__: Een topologisch element is een configuratie waarin vastgelegd wordt hoe objecten verbonden zijn of hoe ze relatief tot elkaar gepositioneerd zijn.
* __Transportruimte__: Natuurlijke of aangelegde transportlijnen of verbindingen met knooppunten waarlangs stromen zich verplaatsen.
* __Tunneldeel__: Onderdeel van een kunstmatig aangelegde, kokervormige onderdoorgang dat essentieel is voor de constructie.
* __Urbane beheerzone__: Een afgebakend gebied voor generieke beheerdoeleinden binnen het stedelijk gebied.
* __Valruimte-informatie__: Gegevens die de valruimte van een speel- of sporttoestel vastleggen.
* __Vegetatieobject__:   Solitair vegetatieobject of lijn- of vlakvormige groep gelijksoortige vegetatieobjecten met een beperkte omvang.
* __Verharding__: Een door egaliseren, verstevigen en/of verruwen voor het beoogde gebruik geschikt gemaakte oppervlak, bestaande uit in één of meer lagen over een ondergrond of onderliggende constructie aangelegd materiaal
* __Verkeerruimte__: Transportruimte voor verkeer via land, water of lucht.
* __Verkeersintensiteit__: Het vastleggen van de verkeersintensiteit per prognosejaar bij een wegas.
* __Verkeerskundig functionele zone__: Functionele ruimte die een verkeerskundige functie kent.
* __Verkeerstelling__: Het registreren van verkeerstellingen bij een Wegas.
* __Virtuele ruimte__:  &#9;Geo-object dat zich geheel of gedeeltelijk niet-materieel manifesteert en dus slechts in abstracte en/of geregistreerde vorm bestaat.
* __Water__: Massa van water dat de bodem bedekt of in normale omstandigheden kan bedekken
* __Waterbeheerzone__: Een afgebakend gebied specifiek van belang voor waterbeheer.
* __Waterinrichtingsobject__: Een ruimtelijk object ter inrichting van het water.
* __Waterverplaatsingruimte__: Transportruimte waardoor water zich verplaatst.
* __Waterstaatkundig kunstwerk__: Kunstwerk voor de beheersing van het oppervlaktewater en alles wat daarin voorkomt
* __Weginrichtingsobject__: Een ruimtelijk object dat dient voor de inrichting van de openbare weg.
* __Wegverkeerruimte__: Transportruimte voor voertuigen die zich over wegen verplaatsen .
* __Wegzone__: Functionele ruimte die in gebruik is voor weginrichting


#### Totstandkoming

De uitgangspunten voor de totstandkoming van deze hiërarchie waren:
1. Hergebruiken wat er reeds is;
1. Aansluiten bij de meest recente versie van de standaarden;
1. NEN2660-2 gebruiken als uitgangspunt, inclusief de daarin vermelde relatie met de NEN3610;
1. Aansluiting eerst op de SOR (dan pas IMGeo), inclusief de daar in vermelde relatie met de NEN3610;
1. Alleen de concepten vermelden waar gebruik van gemaakt wordt;
1. Meervoudige overerving is toegestaan;
1. Alle ObjectTypen moeten een plek krijgen;
1. Termen en definities uit te standaarden hergebruiken (boven eigen gemaakte);
1. Type relaties alleen degene uit toegestaan uit NEN2660-2;
1. Vooralsnog alleen `FysiekObject`, `Activiteit`, `GeometrischeRepresentatie` en `InformatieObject` gebruiken uit de NEN2660-2 (en in IMBOR2022 daar verder op in gaan);
1. Verdeling van attributen over `Objecttype`n moet zo veel mogelijk gelijk blijven t.o.v. IMBOR2020-08 (afgezien van waar de koppeling al niet goed was);

#### Semantische relaties

Ten opzichte van IMBOR2020-08 is de introductie van semantische relaties een grote verandering. Middels relaties geadopteerd uit de NEN2660-2 wordt het mogelijk gemaakt om tussen concepten binnen IMBOR betekenisvolle relaties te leggen. De relaties betreffen:
1. `isSubtypeVan` (NEN2660-2: Is een verbijzondering van)
1. `heeftDeel` ([NEN2660-2:hasPart](https://w3id.org/nen2660/def#hasPart))
1. `isVerbondenMet` ([NEN2660-2:isConnectedTo](https://w3id.org/nen2660/def#isConnectedTo))
1. `isBeschrevenDoor` ([NEN2660-2:isDescribedBy](https://w3id.org/nen2660/def#isDescribedBy))
1. `bevat`([NEN2660-2:contains](https://w3id.org/nen2660/def#contains))
1. `heeftBegrenzing` ([NEN2660-2:hasBoundary](https://w3id.org/nen2660/def#hasBoundary))
1. `voertUit` ([NEN2660-2:executes](https://w3id.org/nen2660/def#executes))

<div class='advisement'>
In het schema is te zien tussen welke (top)concepten de relaties kunnen lopen. In de IMBOR ontologie (in Access en LinkedData) is vanuit IMBOR per `Klasse` een aanzet gegeven van de belangrijkste relaties die voorkomen. Het staat de gebruiker van IMBOR vrij om binnen de gezette kaders meer relaties op `Objecttype` niveau te leggen. 
</div>

### IMBOR Bouwstenen

Binnen de IMBOR cursus wordt uitgelegd wat de bouwstenen van IMBOR zijn. Deze ReSpec betreft de technische documentatie, maar de afbeeldingen die in de cursus gebruikt worden maken vrij goed duidelijk hoe een "ingewikkeld" technisch model simpel uitgelegd kan worden aan een assetmanager die uiteindelijk ook de opbouw van IMBOR moet begrijpen. Vandaar dat onderstaande figuren opgenomen zijn. Het eerste figuur illustreert simpel hoe het metamodel van IMBOR in elkaar zit, het tweede figuur illustreert dit met behulp van voorbeelden verder.

<figure>

![IMBOR Bouwstenen](img/Bouwstenen_IMBOR_cursus_1.png)
    
<figcaption><figcaption>IMBOR bouwstenen versimpeld</figcaption></figcaption>
</figure>
<figure>

![IMBOR Bouwstenen voorbeelden](img/Bouwstenen_IMBOR_cursus_2.png)
    
<figcaption><figcaption>IMBOR bouwstenen versimpeld met voorbeelden</figcaption></figcaption>
</figure>

### Speciale modelleerconstructies

Binnen IMBOR zijn er een aantal modelleerkeuzes gemaakt die extra uitleg verdienen. Deze kunnen geschaard worden onder de 'informele' modelleerregels
#### Objecttypen

`Objecttype` is een speciaal soort `Klasse`. Het betreft hier namelijk het blad van de klasseboom. Ofwel de onderste laag. Binnen IMBOR worden deze onderscheiden omdat de term 'Objecttype' erg ingeburgerd is. Technische gezien zijn het de enige 'concrete' `Klasse` (tegenover de rest welke 'abstracte' `Klasse` zijn). Hiermee wil IMBOR aangeven dat deze abstracte klassen niet geïnstanteerd mogen worden en de 'concrete' `Objecttype` juist wel. `Objecttype` zijn als enige ook ingedeeld in `Vakdiscipline`s. 

<div class='advisement'>
Klassen zijn een abstract concept. Ze staan daarmee tegenover bijvoorbeeld `Objecttype` en `InformatieObject` die wel 'concreet' zijn. Hiermee wil IMBOR aangeven dat deze klassen niet geïnstanteerd mogen worden.
</div>

#### InformatieObjecten

Speciale aandacht gaat uit naar de relaties tussen `Objecttype` en `InformatieObject`. Veel van de attributen die in IMBOR2020-08 aan een `Objecttype` hingen waren eigenlijk meer 'informatie over' dan een daadwerkelijk aspect van dat object. Vandaar dat in IMBOR2022 is besloten om veel attributen te verhuizen naar `InformatieObject`. Hiermee is het dus wel van belang dat deze daadwerkelijk geïnstantieërd worden in de beheersystemen om de beschrijvende attributen vast te leggen. Dit is ook vastgelegd middels de multipliciteit. 

Deze keuze is enerzijds gemaakt vanwege de interpretatie dat een `InformatieObject` een ‘object’ op zichzelf is, welke informatie bevat over een object (vandaar de `isBeschrevenDoor` relatie). Hiermee wordt de informatie _van_ het 'object' gescheiden van de informatie _over_ het 'object'. Anderzijds betreffen het ook vaak attributen die op termijn uit andere registraties zouden moeten komen. 

#### Gebiedsindeling

De `Klasse` 'Gebiedsindeling' is gemodelleerd vanwege een legacy behoefte binnen IMBOR. De klasse distribueert een set van attributen welke allemaal afgeleidt kunnen worden van de geografische locatie. De meeste zijn ook dubbel te leggen met de semantische relatie `bevat`. Bijna alle attributen hebben dan ook als waarde binnen `TypeAttribuut` de waarde 'Wordt automatisch bepaald'. Zie ook [Automatische waarden](#automatische-waarden).

Op termijn zal gekeken moeten worden of de expliciete modelleering via de semantische relaties hier ook afdoende voor is. 

#### Automatische waarden

Enkele attributen hebben als `TypeAttribuut` de waarde 'Wordt automatisch bepaald'. Hiermee wordt aangegeven dat bij de implementatie in een (GIS) systeem de daadwerkelijke waarde van het attribuut berekend wordt door het beheerpakket, maar expliciet opgeslagen wordt op dit attribuut. Elke organisatie of leverancier kan zelf kiezen hoe dit te implementeren, deze modellering binnen IMBOR geeft alleen maar aan dat het een 'afgeleid' attribuut betreft. Dit is (toentertijd) besloten omdat dit de query's binnen de systemen aanzienlijke sneller maakt en men zeker weet dat deze waarden expliciet bevraagbaar zijn. 

Op termijn zal gekeken moeten worden of de expliciete modelleering via de semantische relaties hier ook afdoende voor is. 

#### Classificerende attributen

Omdat IMBOR uitgaat van onderscheidende kenmerken als vuistregel om een `Klasse` of `Objecttype` te introduceren zijn er de attributen `Type`, `TypeGedetailleerd` en `TypeExtraGedetailleerd` onderkent. Dit zijn attributen zoals beschreven in deze sectie van [MIM][1]. In de LinkedData theorie zouden dit subklassen zijn van de objecttypen waaraan ze hangen. Echter om geen exponentiële groei van objecttypen te veroorzaken wordt gebruik gemaakt van deze 'indicatie classificerend'. Dit zijn detailleringen van het `Objecttype` welke geen specifieke informatiebehoefte hebben. Ten opzichte van IMBOR2020-08 zijn in IMBOR2022 veel waarden die eerst van het attribuut `Type` waren opgeschoven en 'gepromoveerd' naar een echt `Objecttype`. Bijvoorbeeld 'Beweegbare brug' en 'Vaste brug' zijn nu `Objecttype` in IMBOR2022, terwijl in IMBOR2020-08 deze een waarde waren binnen het `Type` attribuut. Hiermee zijn de `TypeExtraGedetailleerd` gepromoveerd naar `TypeGedetailleerd` en `TypeGedetailleerd` gepromoveerd naar `Type`. Er zijn dus veel `Objecttype`n bijgekomen, dit maakt IMBOR meer expliciet. In theorie staat het de softwareleverancier of opdrachtgever vrij om van de attribuut waarden wel expliciete subklassen te maken indien nodig. Bij eventuele uitwisseling zal dan weer een conversie nodig zijn. De `indicatie classificerend' wordt in de MIM graaf aan de attributen (ofwel mim:Attribuutsoort) gehangen en kan vanuit daar ook geraadpleegd worden. 

#### Vakdisciplines

Vakdisciplines betreffen een groepering die ook niets meer is dan dat is. Binnen IMBOR wordt deze voornamelijk gebruikt als zoekingang of als structurering om de hoeveelheid `Objecttype` makkelijker te kunnen inzien. 

<div class='advisement'>
Ter verduidelijking: daadwerkelijke geregistreerde objecten (de instanties van `Objecttype`) kunnen in een beheersysteem zelf vervolgens ook tot meerdere `Vakdiscipline` tegelijk behoren. IMBOR dwingt hier niets over af. Vakdisciplines in IMBOR zijn een geste vanuit IMBOR om te zoeken. De indeling is daarmee niet per sé arbitrair te noemen, maar wel vanuit ons/één perspectief.
</div>

[1]: https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#metagegeven-indicatie-classificerend

#### Gekwalificeerde waardeshapes

In de LinkedData versie van IMBOR wordt `sh:class` gebruikt om bij de [semantische relaties](#semantische-relaties) en bij attributen die vaste waardelijst kennen aan te geven van welke klasse de waarde moet zijn (ofwel, waar de relatie naar toe loopt). Bijvoorbeeld bij een _Sluis heeftDeel Sluisdeur_ wordt aangegeven dat een bepaalde sluis een bepaalde sluisdeur als onderdeel kan hebben. In de consultatieronde is [gebleken][626] dat het directe gebruik van `sh:class` die beperkende factor ook inbrengt, maar tegelijk ook vereist dat als die relatie meerdere keren voorkomt per klasse, al die waarden aanwezig moeten zijn.
In het voorbeeld van een sluis, bestaat ook _Sluis heeftDeel Schutkolk_.  Met een modellering sec `sh:class`, vereist de SHACL-controle dat de schutkolken tegelijk ook sluisdeuren moeten zijn.

Dit is niet wat bedoelt wordt en dus onwenselijk. 
Daarom worden in IMBOR2022 `sh:class` klassebeperkingen via `sh:qualifiedValueShape` ingeleid, zodat deze voorgenoemde combinatorische betekenis niet voorkomt.
De klasse _Sluisdeur_ of _Schutkolk_ is namelijk één van de kwalificerende waardes voor _heeftDeel_ bij een _Sluis_.

[626]: https://github.com/Stichting-CROW/imbor/issues/626

#### Topologische elementen

Binnen IMBOR2022 zijn topologische elementen (als `TopologischElement`) toegevoegd als speciaal soort `GeometrischeRepresentatie`. Het betreffen namelijk schematische representaties van een daadwerkelijke (`FysiekObject`), net zoals de geometrie. Middels de `heeftBegrenzing` relatie zijn meerdere geometrische representaties vast te leggen (bijvoorbeeld: 2D, 3D of schematisch). In IMBOR is er vooralsnog echter _geen_ aandacht gegeven aan topologie. De enige topologie die momenteel onder `TopologischElement` in IMBOR zit betreft hetgeen GWSW specificeert. Dit is gedaan om de relatie tussen GWSW en IMBOR zo overzichtelijk en compleet mogelijk te maken. Zie ook [GWSW als referentiemodel](#gwsw-als-referentiemodel). Er wordt niet uitgesloten dat IMBOR in de toekomst zelf ook specificaties van topologie gaat maken. 
