## IMBOR samenhang en hiërarchie

IMBOR wordt gepositioneerd als sectormodel. De focus ligt op de vaste gegevens van objecten die herkend worden voor het beheer van de openbare ruimte. Kijkend naar het landschap waarin IMBOR wordt gebruikt zijn er veel raakvlakken met landelijke, maar ook andere sectorale modellen. Om deze afstemming zo optimaal te laten verlopen is getracht om de top van de IMBOR hiërarchie (ofwel de klassenindeling) zo veel mogelijk aan te laten sluiten op andere modellen. Dit is gedaan om enerzijds niet zaken zelf te verzinnen, maar zaken aan te vullen. En anderzijds om uiteindelijk een semantisch sterke mapping tussen de sectorale modellen mogelijk te kunnen maken. Wanneer sectorale modellen allemaal gebaseerd zijn op dezelfde uitgangspunten is het makkelijkere om onderin de boom de vergelijking te kunnen maken. Vandaar dat voor IMBOR gekozen is om gebruik te maken van een polyhiërarchie gebaseerd op respectievelijk de [NEN2660-2:2022][nen2660:2022] en de [NEN3610:2022][nen3610:2022]. 

### IMBOR Top hiërarchie

In onderstaand diagram is de top van de hiërarchie te vinden, met in kleur aangegeven waar de concepten vandaan komen. De relaties tussen de [NEN2660-2:2022][nen2660:2022] en de [NEN3610:2022][nen3610:2022] komen uit de [NEN2660-2:2022][nen2660:2022] documentatie zelf. Deze indeling zorgt ervoor dat voor alle IMBOR `Objecttype`n (niet afgebeeld) er een logische hiërarchie is, waarmee duidelijk is hoe deze zich verhoudt tot de landelijke standaarden. Te zien is dat er weinig IMBOR specifieke (hoofd)klassen geïntroduceerd hoeven te worden omdat bijna alles al voldoende gedefinieerd wordt. Alle `Objecttype`n` hebben worden aan één of meerdere van deze klassen gehangen en krijgen hiermee een landelijke semantische definitie. De hiërarchie wordt tevens gebruikt om de attributen mee te distribueren, maar deze hebben (nog) geen landelijk/sectoraal kader. Hiermee wordt bedoeld dat dit diagram meer gebruikt moet worden als 'begrippenkader'(lees: de semantische afstemming van de modellen) dan dat het daadwerkelijk als een volwaardige ontologie ingezet kan worden. Dit is niet per se mogelijk omdat er geen volledige afstemming is tussen de attributen en onderlinge relaties.

Al deze concepten kennen definities, omdat er anders geen semantische discussies gevoerd kunnen worden zonder dat de definities van de concepten bekend zijn. Alle definities kunnen ingezien worden in de [IMBOR viewer](https://imbor-viewer.apps.crow.nl//).

<figure>

![IMBOR Top hiërarchie](img/IMBOR-top.drawio.svg?raw=true)
    
<figcaption><figcaption>IMBOR Top van de ontologie -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption></figcaption>
</figure>


#### Totstandkoming

De uitgangspunten voor de totstandkoming van deze hiërarchie waren:
1. Hergebruiken wat er reeds is;
1. Aansluiten bij de meest recente versie van de standaarden;
1. [NEN2660-2:2022][nen2660:2022]gebruiken als uitgangspunt, inclusief de daarin vermelde relatie met de [NEN3610:2022][nen3610:2022];
1. Alleen de concepten vermelden waar gebruik van gemaakt wordt;
1. Meervoudige overerving is toegestaan;
1. Alle `Objecttype`n moeten een plek krijgen;
1. Termen en definities uit te standaarden hergebruiken (boven eigen gemaakte);
1. De gebruikte relaties alleen komen alleen uit de [NEN2660-2:2022][nen2660:2022], tenzij die niet in de behoefte voorzien;
1. Dan geniet het gebruiken van bestaande relaties de voorkeur boven eigen relaties;

#### Semantische relaties

Ten opzichte van IMBOR2020-08 is de introductie van semantische relaties een grote verandering. Middels relaties geadopteerd uit de [NEN2660-2:2022][nen2660:2022] wordt het mogelijk gemaakt om tussen concepten binnen IMBOR betekenisvolle relaties te leggen. De relaties betreffen:
1. `isSubtypeVan` (NEN2660-2: Is een verbijzondering van)
1. `heeftDeel` ([NEN2660-2:hasPart](https://w3id.org/nen2660/def#hasPart))
1. `isVerbondenMet` ([NEN2660-2:isConnectedTo](https://w3id.org/nen2660/def#isConnectedTo))
1. `isBeschrevenDoor` ([NEN2660-2:isDescribedBy](https://w3id.org/nen2660/def#isDescribedBy))
1. `bevat`([NEN2660-2:contains](https://w3id.org/nen2660/def#contains))
1. `heeftBegrenzing` ([NEN2660-2:hasBoundary](https://w3id.org/nen2660/def#hasBoundary))
1. `voertUit` ([NEN2660-2:executes](https://w3id.org/nen2660/def#executes))
1. `bestaatUit` ([NEN2660-2:consistsOf](https://w3id.org/nen2660/def#consistsOf))

Vanaf IMBOR2025 zijn daar de volgende relaties bijgekomen:
1. `heeftBetrekkingOp` (uit de NEN2660-1)
1. `speelt` (uit de NEN2660-1)
1. `isGeregistreerdMet` ([registratiegegevens](https://modellen.geostandaarden.nl/def/nen3610-2022/index.html#registratiegegevens) uit de [NEN3610:2022][nen3610:2022])
1. `startNode` ([net:startNode](https://github.com/inspire-eu-rdf/inspire-rdf-vocabularies/blob/7dde22fde631409957a445f97af5868299f2330e/net/net.ttl#L286) uit INSPIRE via [NEN3610:2022][nen3610:2022])
1. `endNode` ([net:endNode](https://github.com/inspire-eu-rdf/inspire-rdf-vocabularies/blob/7dde22fde631409957a445f97af5868299f2330e/net/net.ttl#L66) uit INSPIRE via [NEN3610:2022][nen3610:2022])


<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="997"><span></span></div>
  <div class="issue" data-number="1258"><span></span></div>
  <div class="issue" data-number="1075"><span></span></div>
</details>

<div class='advisement'>
In het schema is te zien tussen welke (top)concepten de relaties kunnen lopen. In de IMBOR ontologie (in Access en LinkedData) is vanuit IMBOR per `Klasse` een aanzet gegeven van de belangrijkste relaties die voorkomen. Het staat de gebruiker van IMBOR vrij om binnen de gezette kaders meer relaties op `Objecttype`n niveau te leggen. 
</div>

##### Inverse van relaties

In de [NEN2660-2:2022][nen2660:2022] is de `nen2660:hasPart` (heeftDeel) relatie niet-transitief. De 'isDeelVan'-relatie wordt niet expliciet gemodelleerd. In IMBOR is hier wel vraag naar, vandaar dat vanaf 2024 deze er binnen IMBOR een expliciete relatie `nen2660:isPartOf` relatie is gedefinieerd in het IMBOR aanvullend meta-model. Deze is de inverse van `nen2660:hasPart` en mag ook gebruikt worden op dezelfde manier, maar dan in de andere richting.

Eenzelfde constructie geldt voor `nen2660:contains` (bevat). Ook hier is in IMBOR vraag naar een expliciete modellering. Vandaar dat de `nen2660:isContainedBy` (bevindtZichIn) is toegevoegd in het IMBOR aanvullend meta-model. 
<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1255"><span></span></div>
  <div class="issue" data-number="1394"><span></span></div>

</details>

### IMBOR Bouwstenen
<!-- TODO: versie 2025 -->
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

Klasse is een begrip geïntroduceerd in IMBOR2022. Het kan gelijkgesteld worden aan het [NEN2660-2:2022][nen2660:2022] "Concept". Het is hiermee ook een supertype van bijvoorbeeld `Objecttype` en `InformatieObject`. 

`Objecttype` is een speciaal soort `Klasse`. Binnen IMBOR worden deze onderscheiden omdat de term 'Objecttype' erg ingeburgerd is. Technische gezien zijn het de enige 'concrete' `Klasse` (tegenover de rest welke 'abstracte' `Klasse` zijn). Hiermee wil IMBOR aangeven dat deze abstracte klassen niet geïnstanteerd kunnen worden en de 'concrete' `Objecttype` juist wel. `Objecttype` zijn als enige ook ingedeeld in `Zoekingangen`. 

De klassenstructuur is een polyhiërarchie. Dit betekent dat een child, meerdere parents kan hebben. Of in IMBOR termen gezegd: Een `Objecttype` of `Klasse` erft van meerdere `Klasse` attributen over. Dit is gedaan zodat we flexibeler om kunnen gaan bij welke klassen een `Objecttype` hoort en daarmee een `Objecttype` geen onnodige attributen krijgt. Er zullen een aantal `Klasse` 'disjoint' zijn, maar dat is nog niet expliciet opgenomen.

Tot IMBOR2022 was altijd het laagste niveau in de klasse hiërarchie een `Objecttype`. Vanaf IMBOR2025 is dit veranderd vanwege het feit dat dit alignments met externe modellen eenvoudiger en completer kunnen worden en het verdwijnen van de classificerende attributen `type`, `typeGedetailleerd` en `TypeExtraGedetailleerd`. Tevens ligt deze wijze van modelleren meer in lijn met de praktijk van modellen maken. Hierdoor kan het ook voorkomen dat subklassen (onder objecttypen) bestaan, die _niet_ `Objectentype`n zijn (dus niet instantiërbaar). Voor elke `Klasse` wordt nu apart bekeken of deze `concreet` (instantiërbaar) of `abstract` (niet instantiërbaar) is.

<div class='advisement'>
Klassen zijn een abstract concept. Ze staan daarmee tegenover bijvoorbeeld `Objecttype` en `InformatieObject` die wel 'concreet' zijn. Hiermee wil IMBOR aangeven dat deze klassen _niet geïnstanteerd_ kunnen worden.
</div>

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1432"><span></span></div>
</details>

#### InformatieObjecten

Speciale aandacht gaat uit naar de relaties tussen `Objecttype` en `InformatieObject`. Veel van de attributen die in IMBOR2020-08 aan een `Objecttype` hingen waren eigenlijk meer 'informatie over' dan een daadwerkelijk aspect van dat object. Vandaar dat vanaf IMBOR2022 is besloten om veel attributen te verhuizen naar `InformatieObject`. Hiermee is het dus wel van belang dat deze daadwerkelijk geïnstantieërd worden om de beschrijvende attributen vast te leggen. Dit is ook vastgelegd middels de multipliciteit. 

Deze keuze is enerzijds gemaakt vanwege de interpretatie dat een `InformatieObject` een ‘object’ op zichzelf is, welke informatie bevat over een object (vandaar de `isBeschrevenDoor` relatie). Hiermee wordt de informatie _van_ het 'object' gescheiden van de informatie _over_ het 'object'. Anderzijds betreffen het ook vaak attributen die op termijn uit andere registraties zouden moeten komen. 

<figure>

![Voorbeeld Informatieobject](img/vb-informatieobject.png?raw=true)
    
<figcaption>Voorbeeld InformatieObject</figcaption>
</figure>

##### Inwinning-informatie

`Inwinning-informatie` is een `InformatieObject` voor het vastleggen van informatie m.b.t. de inwinning van een objecttype. Een vergelijkbare entiteit is `Registratie-informatie`, omdat dit ook 'meta' informatie bevat. `Inwinning-informatie` is echter speciaal omdat hier een speciale afspraak gemaakt moet worden met betrekking tot twee attributen van deze klasse. De attributen `attribuut` en `domeinwaarde` zijn nu van het datatype `xsd:string`. Maar eigenlijk mogen hier alleen respectievelijk de IMBOR attributen en bijbehorende IMBOR domeinwaarden voorkomen. 

Een best practice hiervoor is te vinden in: [IMBOR best practices](https://docs.crow.nl/imbor/best-practices/).

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1389"><span></span></div>
</details>

#### Gebiedsindeling & andere afleidbare attributen

De `Klasse` 'Gebiedsindeling' was gemodelleerd vanwege een legacy behoefte binnen IMBOR. De klasse distribueerde een set van attributen welke allemaal afgeleid kunnen worden van de geografische locatie. De meeste waren ook dubbel te leggen met de semantische relatie `bevat`. Om deze reden is de klasse `Gebiedsindeling` dus komen te vervallen en wordt aangemoedigd om gebieden expliciet te modelleren als klassen.

In IMBOR2025 zijn alle afleidbare attributen (waar de waarden 'automatisch bepaald' konden worden) vervangen door semantische relaties. Dit is gedaan vanwege het feit dat in IMBOR2022 de modellering nog onvoldoende geconformeerd was aan de [NEN2660-2:2022][nen2660:2022]. Vele IMBOR-attributen behelzen namelijk (ruimtelijke) relaties tussen verschillende objecten (bijvoorbeeld tussen Ruimtelijke gebieden en Reële objecten). 

Het gebruik hiervan wordt gepropageerd vanuit de [NEN2660][nen2660:2022] en IMBOR adopteert dit volledig. Een best practice hiervoor (met het voorbeeld 'Ruimtelijk vs. Reëel')  is te vinden in: [IMBOR best practices](https://docs.crow.nl/imbor/best-practices/).

<figure>

![Voorbeeld Gebiedsindeling](img/vb-gebied.png?raw=true)
    
<figcaption>Voorbeeld gebiedsindeling</figcaption>
</figure>

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1101"><span></span></div>
  <div class="issue" data-number="1290"><span></span></div>
  <div class="issue" data-number="1306"><span></span></div>
</details>

#### Classificerende attributen

Omdat IMBOR uitgaat van onderscheidende kenmerken als vuistregel om een `Klasse` of `Objecttype` te introduceren is het attribuut `Verschijningsvorm` onderkent. Dit is een attribuut zoals beschreven in deze sectie van [MIM][1].  In de LinkedData theorie zouden dit subklassen kunnen zijn van de objecttypen waaraan ze hangen. Echter om geen exponentiële groei van objecttypen te veroorzaken wordt gebruik gemaakt van deze 'indicatie classificerend'. Dit zijn detailleringen van het `Objecttype` welke geen specifieke informatiebehoefte hebben. In theorie staat het de softwareleverancier of opdrachtgever vrij om van de attribuut waarden wel expliciete subklassen te maken indien nodig. Bij eventuele uitwisseling zal dan weer een conversie nodig zijn. De `indicatie classificerend' wordt in de MIM graaf aan de attributen (ofwel mim:Attribuutsoort) gehangen en kan vanuit daar ook geraadpleegd worden.  

<div class='advisement'>
`Verschijningsvorm` is de vervanging van wat in vorige versie van IMBOR de attributen `Type`, `TypeGedetailleerd` en `TypeExtraGedetailleerd` waren. De hiërarchie die hier in zat is vervallen vanaf IMBOR2025. De waarden die `Verschijningsvorm` kan hebben zijn hiermee samengevoegd/opgeschoond tot één enkele lijst. 
</div>

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1267"><span></span></div>
</details>

#### Zoekingangen

Zoekingangen (voorheen 'Vakdisciplines) betreffen een groepering die ook niets meer is dan dat is. Binnen IMBOR wordt deze voornamelijk gebruikt als zoekingang of als structurering om de hoeveelheid `Objecttype` makkelijker te kunnen inzien. 

<div class='advisement'>
Ter verduidelijking: daadwerkelijke geregistreerde objecten (de instanties van `Objecttype`) kunnen in een beheersysteem zelf vervolgens ook tot meerdere `Zoekingangen` tegelijk behoren. IMBOR dwingt hier niets over af. Zoekingangen in IMBOR zijn een geste vanuit IMBOR om te zoeken. De indeling is daarmee niet per sé arbitrair te noemen, maar wel vanuit ons/één perspectief.
</div>

[1]: https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#metagegeven-indicatie-classificerend

#### Gekwalificeerde waardeshapes

In de LinkedData versie van IMBOR wordt `sh:class` gebruikt om bij de [semantische relaties](#semantische-relaties) en bij attributen die vaste waardelijst kennen aan te geven van welke klasse de waarde moet zijn (ofwel, waar de relatie naar toe loopt). Bijvoorbeeld bij een _Sluis heeftDeel Sluisdeur_ wordt aangegeven dat een bepaalde sluis een bepaalde sluisdeur als onderdeel kan hebben. In de consultatieronde is gebleken dat het directe gebruik van `sh:class` die beperkende factor ook inbrengt, maar tegelijk ook vereist dat als die relatie meerdere keren voorkomt per klasse, al die waarden aanwezig moeten zijn.
In het voorbeeld van een sluis, bestaat ook _Sluis heeftDeel Schutkolk_.  Met een modellering sec `sh:class`, vereist de SHACL-controle dat de schutkolken tegelijk ook sluisdeuren moeten zijn.

Dit is niet wat bedoelt wordt en dus onwenselijk. 
Daarom worden in IMBOR2022 `sh:class` klassebeperkingen via `sh:qualifiedValueShape` ingeleid, zodat deze voorgenoemde combinatorische betekenis niet voorkomt.
De klasse _Sluisdeur_ of _Schutkolk_ is namelijk één van de kwalificerende waardes voor _heeftDeel_ bij een _Sluis_.

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="626"><span></span></div>
</details>

#### Topologie & netwerkmodel

Binnen IMBOR zijn topologische elementen (als `TopologischElement`) toegevoegd als speciaal soort `GeometrischeRepresentatie`. Het betreffen namelijk schematische representaties van een daadwerkelijke (`FysiekObject`), net zoals de geometrie. Middels de `heeftBegrenzing` relatie zijn meerdere geometrische representaties vast te leggen (bijvoorbeeld: 2D, 3D of schematisch).

IMBOR voorziet vanaf versie 2025 tevens in een elementaire modellering van netwerken. Het gaat hierbij om een topologische uitdrukking van de geografische gegevens van de beheerobjecten uit IMBOR, dat wil zeggen: in termen van knooppunten en verbindingen die de eigenschappen van de plaatsen van IMBOR-objecten voorstellen. Deze modellering is gebaseerd op implementatie van de basisstructuren van het netwerkmodel uit de Europese standaard [INSPIRE][INSPIRE] die de [NEN3610:2022][nen3610:2022] voorschrijft. De [NEN3610:2022][nen3610:2022] adviseert INSPIRE toe te passen voor het modelleren van topologische dimensie parallel aan een geografische dimensie. 
 
Op hoofdlijnen heeft dit geleid tot de toevoeging van de klassen `Netwerk`, `NetwerkLink` en `NetwerkNode`. Deze klassen zijn subklassen gemaakt van `nen2660:GeometrischeRepresentatie`. Voor `NetwerkLink` en `NetwerkNode` geldt dat ze middels `nen2660:hasPart` gerelateert kunnen worden aan `Netwerk`. Tussen `NetwerkLink` en `NetwerkNode` lopen twee semantische relaties, namelijk `endNode` en `startNode`. Kortweg betekent dit dat een `NetwerkLink` een `NetwerkNode` als beginpunt of als eindpunt kan hebben. In de ontwikkeling van IMBOR2025 is ervoor gekozen om deze als `rdfs:subPropertOf` van `nen2660:hasPart` te declareren. 

<div class='example'>
Een voorbeeld gebruik van het netwerkmodel:

Voor een topologische representatie van een netwerk van waterwegen worden `imbor:Waternode` en `imbor:Waterlink` geïnstantieerd, met als onderlinge relaties `endNode` en `startNode`. Deze objecten maken deel uit van een bovenliggend `imbor:Netwerk`. De `imbor:Waternode` en `imbor:Waterlink` hebben `nen2660:isDescribedBy` met instanties van `nen2660:PhysicalObject`, zoals `imbor:Watergang` (bij een topologische representatie van reële objecten) of `imbor:Waterweg` (bij een topologische representatie van ruimtelijke gebieden). Dit standaardiseert dus de kern van de statische modellering van netwerken binnen het domein van de openbare ruimte. Gebruikers kunnen dit als kernmodellering gebruiken om hun specifieke netwerktoepassingen mee te realiseren. 
</div>

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="997"><span></span></div>
</details>


[INSPIRE]: https://www.geonovum.nl/geo-standaarden/inspire

#### Temporele aspecten
IMBOR implementeert vanaf versie 2025, in samenhang met de implementatie van [NEN2660-2:2022][nen2660:2022], de mogelijkheid uit [NEN3610:2022][nen3610:2022] om tijdlijnen voor de registratie van historische wijzigingen van objecten. 

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1075"><span></span></div>
</details>

##### Modellering 
[NEN3610:2022][nen3610:2022] faciliteert versionering van objecten door de tijd heen door twee tijdlijnen te introduceren: de **'TijdlijnRegistratie'** en de **'TijdlijnGeldigheid'**. Daarnaast is er de **'Levensduur'** van een object. Al deze zaken zijn binnen de [NEN3610:2022][nen3610:2022] eigenschappen van de klasse `nen3610:Registratie`. De IMBOR-implementatie van deze temporele aspecten schippert tussen de [NEN2660-2:2022][nen2660:2022] en de [NEN3610:2022][nen3610:2022]. IMBOR heeft namelijk niet alleen met `nen3610:GeoObject` te maken, maar ook met het onderscheid tussen `nen2660:InformationObject` en `nen2660:PhysicalObject`. Op `nen2660:PhysicalObject` past `nen3610:Registratie` in haar geheel en dit leidt tot een implementatie gelijk aan hoe [NEN3610:2022][nen3610:2022] dit voor `nen3610:GeoObject` voorschrijft, namelijk m.b.v. van de relatie `nen3610:registratiegegevens`, zodanig dat geldt dat: _`nen3610:GeoObject > nen3610:registratiegegevens > nen3610:Registratie`_. Echter is deze implementatie voor `nen2660:InformationObject` niet altijd nodig, omdat TijdlijnGeldigheid en Levensduur betrekking heeft op toestandswijzigingen van het beschreven object in de niet-virtuele werkelijkheid. `nen2660:InformationObject` is een object dat niet bestaat buiten de virtuele werkelijkheid van het computersysteem. Daarom is voor `nen2660:InformationObject` alleen gekozen voor het implementeren van **TijdlijnRegistratie** – er zijn immers wel tijdstippen aan te wijzen waarop een informatieobject wijzigt en vervalt.
 
De implementatie heeft geleid tot de introductie van de klasse `nen3610:Registratie`, die zelf een subklasse is van `nen2660:InformationObject`. Dit is dus een speciaal informatieobject voor het beschrijven van `nen2660:InformationObject` en `nen2660:PhysicalObject`. `nen3610:Registratie` heeft de volgende subklassen:
* `imbor:TijdlijnRegistratie` dient het vastleggen van wijzigingen door de tijd heen binnen de virtuele omgeving. 
* `imbor:TijdlijnGeldigheid` biedt de mogelijkheid tijdstippen vast te leggen waarop het virtuele object in representatie (d.w.z.: invulling van eigenschappen) overeenkomt met de werkelijkheid. 
* `imbor:Levensduur` is een afgeleide van `imbor:TijdlijnGeldigheid` die het vastleggen van de begin- en eindtijden van een object dient. 
* `imbor:Versie` legt vast op welke versie van het object in het computersysteem een toestand van een van de tijdlijnen betrekking heeft. 

Instanties van `nen2660:InformationObject` of `nen2660:PhysicalObject` zijn gerelateerd aan de voorgenoemde klassen m.b.v. de relatie `nen3610:registratiegegevens`, die in overleg met zowel de [NEN2660-2:2022][nen2660:2022] als de [NEN3610:2022][nen3610:2022] als subproperty van `nen2660:isDescribedBy` wordt beschouwd.
 
##### Gebruik

Deze temporele aspecten zijn een toevoeging aan IMBOR 2025, maar hebben ook een betere scheiding wat betreft temporele eigenschappen in het model mogelijk gemaakt. De klasse `imbor:Registratie-informatie` is komen te vervallen en de rol van deze klasse wordt overgenomen door `imbor:TijdlijnRegistratie`. Daarnaast hebben op diverse plaatsen in het model verwijderingen plaatsgevonden van temporele eigenschappen die overeenkomen met een van de eigenschappen van de tijdlijnen. Overige attributen die een tijdstip registeren kunnen door gebruikers naar wens gekoppeld worden aan attributen van een van de tijdlijnen, maar er is, vanwege de specifieke betekenis van zo’n attribuut of vanwege de manier van presenteren van informatie die zo’n attribuut verzorgt, geen sprake van equivalentie met een van de eigenschappen van de tijdlijnen.
 
Het gebruik van de klasse 'Registratie' is dat een configuratie van een object dat gelabeld is met `imbor:versie` (attribuut van `imbor:Versie`) als een momentopname van dat object kan worden beschouwd. Als zodanig wordt het voor gebruikers gestandaardiseerd hoe en via welke tijdlijnen momentopnamen die gelabeld zijn met `imbor:versie` elkaar opvolgen. Er kan als zodanig een parallelle progressie zijn van `imbor:TijdlijnRegistratie` en `imbor:TijdlijnGeldigheid`. Als voorbeeld: een object 'X' kan, in de voor IMBOR relevante opzichten, sinds de initiële `nen3610:beginGeldigheid` van 'X' in werkelijkheid ongewijzigd zijn, maar in de virtuele registratie van dit object wel wijzigingen hebben ondergaan. `imbor:tijdstipRegistratie` krijgt daarom een nieuwe waarde, `imbor:versie` wordt opgehoogd en er is sprake van een nieuwe momentopname van object 'X'.

Het gebruik hiervan wordt gepropageerd vanuit de [NEN3610:2022][nen3610:2022] en IMBOR adopteert dit volledig. Hoe de implementatie dan precies werkt wordt toegelicht in de [NEN3610:2022][nen3610:2022], maar specifiek voor graphs en IMBOR is een uitwerking te vinden in: [IMBOR best practice temporele aspecten](https://docs.crow.nl/imbor/best-practices/#nen3610-temporele-aspecten).


#### Materie

Vóór IMBOR2022 werden materialen als attributen van Objecttypen vastgelegd. Binnen de [NEN2660-2:2022][nen2660:2022] is hiervoor een modelleerconstructie gegeven die IMBOR nu toepast. Er kan een relatie `bestaatUit` gelegd worden tussen de klasse `ReeelObject` en de klasse `Materie`. Dit betekent dat materialen dus ook een klasse zijn en ook als zodanig gemodelleerd zijn. Binnen IMBOR2022 zijn allemaal soorten materialen opgenomen en met relaties verbonden aan de juiste ObjectTypen. Deze lijst is op basis van 'expert judgement' samengesteld door de jaren heen. Nu IMBOR zich committeert aan de [NEN2660-2:2022][nen2660:2022] en daarmee LinkedData wordt er gekeken of de materialen apart van IMBOR beheert kunnen gaan worden. Het liefst wordt in de toekomst aangesloten bij een bestaand(e) lijst/initiatief. 

<div class='advisement'>
Ter verduidelijking IMBOR limiteert niet welke relaties er tussen een `FysiekObject` en een `Materie` gelegd kunnen worden. We geven alleen 'voorstellen'.
</div>

#### Actoren en rollen

Vanaf IMBOR2025 is er een nieuw modelleerpatroon geïntroduceerd om relaties tussen klassen en actoren te modelleren, middels rollen. Deze constructie is ontleend uit de [NEN2660-1:2022][nen2660-1:2022]. Omdat de [NEN2660-2:2022][nen2660:2022] hier geen standaard oplossing voor biedt, is er een in IMBOR een modelleerconstructie die conform de [NEN2660-1:2022][nen2660-1:2022] gemaakt is. Het gaat hier om de introductie van `imbor:Actor` (als subklasse van `nen2660:PhysicalObject`) en `imbor:Rol`. Een `imbor:Actor` is een entiteit die in staat is om handelingen uit te voeren en een specifieke functie of positie te vervullen in een bepaalde context (bijvoorbeeld 'Gemeente X'). Met een `imbor:Rol` wordt een samenhangende verzameling van verwachtingen, verantwoordelijkheden, bevoegdheden en gedragingen die een Actor kan aannemen in relatie tot iets bedoelt (bijvoorbeeld 'Beheerder'). `imbor:Actor` wordt met de relatie `imbor:speelt` verbonden met een `imbor:Rol`. Welke op zijn beurt met een `imbor:heeftBetrekkingOp` relatie verbonden is met een `nen3610:GeoObject` of `nen2660:InformatieObject`. 

IMBOR definieert subklassen van `imbor:Actor`, te weten: `imbor:PublieksrechtelijkRechtspersoon` en `imbor:PrivaatrechtelijkRechtspersoon`. Voor de eerste worden TOOI subklassen gebruikt, welke toegelicht worden in [TOOI](#tooi). De laatste kan geïnstantieerd worden om organisaties zoals 'ProRail' of 'TenneT' aan te maken. 

De klasse `imbor:Rol` kent een aantal subklassen die herkenbaar zullen zijn voor de gemiddelde IMBOR gebruiker. Deze werden voorheen als attributen behandeld, maar zijn nu klassen. Voorbeelden hiervan zijn 'Beheerder', 'Eigenaar' en 'Fabrikant'. Deze klassen kunnen geïnstantieerd worden om de expliciete rol aan te geven. In onderstaande voorbeeld is in dikgedrukte letters de IMBOR modelleerconstructie te zien, daaronder een voorbeeld in de data.


| imbor:Actor  | imbor:speelt | imbor:Rol       | imbor:heeftBetrekkingOp | imbor:GeoObject |
|--------------|--------------|-----------------|-------------------------|-----------------|
| ex:GemeenteX | imbor:speelt | ex:Beheerder123 | imbor:heeftBetrekkingOp | ex:BoomX        |
| ex:GemeenteX | imbor:speelt | ex:Eigenaar321  | imbor:heeftBetrekkingOp | ex:BoomX        |
| { .data }    |              |                 |                         |                 |

<figure>

![Voorbeeld Actor en Rol](img/vb-actor-rol.png?raw=true)
    
<figcaption>Voorbeeld actor en rollen</figcaption>
</figure>


<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1258"><span></span></div>
  <div class="issue" data-number="1192"><span></span></div>
</details>

#### Hiërarchie van attributen

Vanaf IMBOR2025 is er een hiërarchie geïntroduceerd binnen de attributen. Dit is niet alleen overzichtelijker voor 'navigatie', maar het stelt gebruikers ook in staat algemenere bevragingen te doen op het gebied van de attributen. Inhoudelijk verandert dit niets, maar het betreft de introductie van een attribuut dat abstract is, en een parent is van een ander attribuut.

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1266"><span></span></div>
</details>

[viewer]: https://imbor-viewer.apps.crow.nl/
[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667
[nen2660-1:2022]: https://www.nen.nl/nen-2660-1-2022-nl-291666
