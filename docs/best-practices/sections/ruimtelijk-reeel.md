## Ruimtelijk (virtueel) vs. Reëel (fysiek)

***Gebaseerd op GitHub issue: [1290](https://github.com/Stichting-CROW/imbor/issues/1290) en [1718](https://github.com/Stichting-CROW/imbor/issues/1718).***

Vanaf IMBOR2022 is er een verschil gemaakt tussen Ruimtelijke en Reële objecten. 
Dit onderscheid is te herleiden naar zowel de [NEN2660][nen2660:2022] (2022, p. 24) als de [NEN3610][nen3610:2022] (2022, p. 60). 

### NEN2660 & NEN3610

**NEN2660**:
In de [NEN2660][nen2660:2022] worden fysieke objecten optioneel, niet-samenvallend opgedeeld in niet-direct tastbare `ruimtelijke gebieden` (bijvoorbeeld Rijbaan, Centrumgebied en Putschat) en tastbare `reële objecten` (bijvoorbeeld Beweegbare brug, Boom en Laagspanningskabel). 

**NEN3610**:
Reële objecten en virtuele ruimten kunnen onafhankelijk van elkaar geclassificeerd worden. Reële objecten zijn in de fysieke werkelijkheid aanwezig en kunnen geclassificeerd worden aan de hand van hun totstandkomingsproces, de samenstelling (fysiek voorkomen) en het eventuele beoogde gebruik. Een synoniem voor reële objecten is fysieke objecten. Virtuele ruimten zijn alleen in een registratie aanwezig en niet fysiek in de werkelijkheid. Ze kunnen worden geclassificeerd aan de hand van
abstracte mentale concepten, zoals bijvoorbeeld functie en regelgeving. Virtuele ruimten hebben begrenzingen die meestal in een administratiefproces zijn bepaald. Virtuele ruimten kunnen daarom reële objecten als harde begrenzing hebben. 

Het _NEN3610 reëel object_ komt overeen met het _NEN2660 technisch reëel object_. Dat betekent dat het hierbij gaat om de fysieke eigenschappen van het object. De _NEN3610 virtuele ruimte_ komt overeen met de _NEN2660 functionele ruimte_. Onderling kennen reële objecten en virtuele ruimten diverse typen relaties. Die relaties kunnen heel sterk zijn, waardoor het reële object en het virtuele object op elkaar kunnen lijken. Bijvoorbeeld een verblijfsobject (virtueel) dat dezelfde afbakening heeft als het gebouw (reëel) dat het verblijfsobject vormt (_realiseert_). Relaties tussen andere reële en virtuele objecten kunnen veel zwakker zijn. Zo kan bijvoorbeeld een gemeentegrens ooit zijn bepaald aan de hand van de reële objecten in de werkelijkheid, maar wordt het vervolgens niet meer noodzakelijkerwijs beïnvloed door wat er met de reële objecten gebeurt.

**`bevat` versus `isBegrensdDoor`**:
De [NEN2660][nen2660:2022] (2022, § 6.2) onderscheidt tussen een ruimtelijk gebied en de reële objecten eromheen twee verschillende relaties, die niet verward moeten worden. De relatie [`bevat`][bevat] drukt uit dat een [`ReeelObject`][ReeelObject] of een [`HoeveelheidBulkmaterie`][HoeveelheidBulkmaterie] zich ruimtelijk *in* het gebied of in de ruimte bevindt. De relatie [`isBegrensdDoor`][isBegrensdDoor] drukt daarentegen uit dat een reëel object het gebied *afbakent*. Een [`RuimtelijkGebied`][RuimtelijkGebied] heeft namelijk zelf geen vaste vorm; het zijn de tastbare, vormvaste reële objecten (in de [NEN2660][nen2660:2022] de specialisatie [`DiscreetObject`][DiscreetObject]) die de vorm ervan bepalen en zo als harde begrenzing dienen. Kortom: `bevat` gaat over wat er *ín* een ruimte/gebied ligt, `isBegrensdDoor` over wat de *vorm* van dat gebied bepaalt.

### Toepassing in IMBOR: de `bevat`-relatie
In IMBOR zijn ruimtelijke gebieden opgenomen zoals `WijkGrens`, `Buurtgrens` en `Recreatiegebied`. Deze ruimtelijke gebieden zijn in principe geometrische vlakken en kunnen ook in die hoedanigheid geïnstantieerd worden. Zodra deze entiteiten beschikbaar zijn, is geometrisch af te leiden of er reële objecten binnen de grenzen van deze entiteiten liggen. Er is dan in principe sprake van een `bevat` relatie. Een ruimtelijk gebied bevat dan een `reëel object`. Deze relatie kan expliciet worden gelegd. Dit kan handig zijn voor (geometrische) query's of voor de situatie waar nog geen geometrie bekend is van een entiteit. 

>EXAMPLE
>Binnen de gemeente X worden Abri's geregistreerd. Men wilt weten hoeveel Abri's er binnen een bepaalde wijk aanwezig zijn om de dichtheid te bekijken. Hiervoor kan een geometrische query gedaan worden en/of de relatie expliciet worden gelegd. In onderstaand geval zijn er twee Abri's (te weten: Abri1 en Abri2) die liggen binnen de wijk 'Heseveld'. 

Dit is een voorbeeld-uitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/ruimtelijk-reeel-bevat.ttl" data-include-format="text"></code></pre>

>ADVISEMENT
>IMBOR geeft voorbeelden van `bevat` relaties, maar het is uiteraard toegestaan om *elk* [`ReeelObject`][ReeelObject] te verbinden met een [`RuimtelijkGebied`][RuimtelijkGebied] volgens de [`bevat`][bevat]-relatie.

### Toepassing in IMBOR: de `isBegrensdDoor`-relatie

***Gebaseerd op GitHub issue: [1718](https://github.com/Stichting-CROW/imbor/issues/1718).***

Waar de `bevat`-relatie een ruimtelijk gebied koppelt aan de reële objecten die zich er *in* bevinden, beschrijft de [NEN2660][nen2660:2022] (2022, § 6.2) dat een ruimtelijk gebied ook *begrensd* wordt door reële objecten. Een ruimtelijk gebied heeft namelijk geen vaste vorm; die vorm wordt bepaald door de tastbare, reële objecten eromheen. Hiervoor bestaat de relatie [`isBegrensdDoor`][isBegrensdDoor]. Het patroon is dan: [`RuimtelijkGebied`][RuimtelijkGebied] → [`isBegrensdDoor`][isBegrensdDoor] → [`ReeelObject`][ReeelObject].

>ADVISEMENT
>De relatie [`isBegrensdDoor`][isBegrensdDoor] is bij de NEN2660-2 omzetting van IMBOR in 2022 bewust nog niet in de IMBOR-shapes en -documentatie opgenomen, omdat deze NEN2660-constructie destijds als te vroeg werd beschouwd. Het betreft echter een geldig NEN2660-patroon. Deze best practice introduceert het alsnog, zodat de koppeling tussen functionele ruimten en hun fysieke uitvoering expliciet vastgelegd kan worden.

Dit patroon lost een veelgestelde vraag op: *hoe leg ik vast welke verschijningsvorm (of soms: welk materiaal) een objecttype zoals 'voetpad' heeft?* Een `Voetpad` is in IMBOR een [`RuimtelijkGebied`][RuimtelijkGebied] een verkeerskundige/functionele zone en heeft zelf géén verschijningsvorm. Die eigenschap hoort bij het [`ReeelObject`][ReeelObject] dat het voetpad fysiek begrenst bijvoorbeeld een `Elementenverharding`. Dit resulteert in: `Voetpad` (`RuimtelijkGebied`) → `isBegrensdDoor` → `Elementenverharding` (`ReeelObject`) → `verschijningsvorm` → `Betontegels`

>EXAMPLE
>Gemeente X registreert een voetpad (`Voetpad1`) dat fysiek is uitgevoerd als elementenverharding (`Elementenverharding1`) van betontegels. Het voetpad (een `RuimtelijkGebied`) heeft zelf geen vaste vorm omdat het een functionele ruimte betreft en wordt daarom middels de relatie `isBegrensdDoor` gekoppeld aan de elementenverharding (een `ReeelObject`). Bij die elementenverharding wordt vervolgens via het attribuut `verschijningsvorm` de domeinwaarde `Betontegels` vastgelegd.

Dit is een voorbeeld-uitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/ruimtelijk-reeel-isbegrensddoor.ttl" data-include-format="text"></code></pre>

De [NEN2660][nen2660:2022] adviseert daarnaast om het fysieke materiaal als een aparte [`Materie`][Materie]-klasse vast te leggen via de relatie [`bestaatUit`][bestaatUit], bijvoorbeeld `Elementenverharding` → `bestaatUit` → `Betontegel` (`Materie`). Dit is een tweede manier om in de kern hetzelfde vast te leggen en is met name van belang voor materialenpaspoorten. Zie hiervoor de best practice [Materie](#materie).


[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667
[RuimtelijkGebied]: https://w3id.org/nen2660/def#SpatialRegion
[ReeelObject]: https://w3id.org/nen2660/def#RealObject
[DiscreetObject]: https://w3id.org/nen2660/def#DiscreteObject
[HoeveelheidBulkmaterie]: https://w3id.org/nen2660/def#AmountOfBulkMatter
[Materie]: https://w3id.org/nen2660/def#Matter
[isBegrensdDoor]: https://w3id.org/nen2660/def#isBoundBy
[bevat]: https://w3id.org/nen2660/def#contains
[bestaatUit]: https://w3id.org/nen2660/def#consistsOf
