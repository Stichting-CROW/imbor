## IMBOR in modellen

Tot en met IMBOR2020-08 zat het metamodel van IMBOR in de content verwerkt. Vanaf 2021 is er expliciet gemaakt hoe IMBOR gemodelleerd is. Hierbij wordt gebruik gemaakt van de principes die het metamodel voor informatiemodellering ([MIM][MIM]) definieert. Hier worden vier 'lagen' van modellen gedefinieerd:
1. [Niveau 1][n1]: Model van begrippen
1. [Niveau 2][n2]: Conceptueel informatiemodel
1. [Niveau 3][n3]: Logisch informatiemodel
1. [Niveau 4][n4]: Fysiek datamodel

IMBOR acteert met name in niveau 1 en niveau 3. Niveau 2 wordt voor IMBOR over geslagen en bestaat alleen impliciet. Niveau 4 beschrijft IMBOR in het kader van de distributie. Dit is dus geen uitleg _hoe_ IMBOR geïmplementeerd moet worden in een database. Maar een uitleg hoe de onderdelen van IMBOR uitgedrukt worden in de MS Access distributie en de LinkedData distributie. 

### Begrippenkader

Het model van begrippen is in deze context gelijk aan een 'vocabulaire'. Het definieert het begrippenkader van IMBOR. Begrippen mogen in verschillende informatiemodellen gebruikt worden, maar worden op één plek, één keer gedefinieerd. Onderstaande figuur toont wat de begrippen structuur is. De begrippen zijn beschikbaar in [[skos-primer]]. Zowel het [MIM][MIM] als de [NEN2660-2:2022][nen2660:2022] bevelen dit aan. 

<div class='advisement'>
De IMBOR Vocabulaire is te verkennen op:

 <a href="https://begrippen.crow.nl/imbor/nl/" target="_blank">begrippen.crow.nl/IMBOR</a> 
</div>

<figure>

![IMBOR vocabulaire structuur](img/IMBOR-begrippen-structuur.drawio.png?raw=true)
    
<figcaption>IMBOR vocabulaire structuur -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption>
</figure>

### Informatiemodel

Binnen IMBOR gaan we uit van bestaande standaarden, te weten de [NEN2660-2:2022][nen2660:2022], de [NEN3610:2022][nen3610:2022] en het MIM. Daarom wordt naast de vocabulaire een ontologie onderscheiden. In deze ontologie maken we voornamelijk gebruik van het "NEN2660-2 Praktisch toplevelmodel". Alle concepten binnen de IMBOR ontologie worden beschreven binnen de context van de [NEN2660-2:2022][nen2660:2022]. Hiermee sluiten we aan bij de ordeningsregels en uiteindelijk ook de taalbinding die in de [NEN2660-2:2022][nen2660:2022]beschreven worden. Hiermee is het "NEN2660-2 praktisch toplevelmodel" ook de top van de IMBOR. Dit beschrijft de concepten, attributen en relaties binnen IMBOR. Onafhankelijk van de beheeromgeving waarin IMBOR beheert wordt zal deze leidend blijven. Waar mogelijk is dit in lijn met het [MIM][MIM] en de [NEN3610:2022][nen3610:2022], echter de [NEN2660-2:2022][nen2660:2022] blijft het voornaamste uitgangspunt.

Onderstaande figuur toont de structuur hoe IMBOR is opgebouwd. In de LinkedData versie wordt er middels een ETL-pipeline gezorgd dat het er correct volgens de [NEN2660-2:2022][nen2660:2022] en [MIM][MIM] taalbinding uit komt. Deze IMBOR structuur is door de jaren heen zo gevormd en herkenbaar geworden door met name het onderscheidt tussen `Klasse` en `Objecttype` en het feit dat er bijvoorbeeld een `Eenheid` aan een combinatie van `Attribuut` en `Klasse` hangt. Voor de (LinkedData) eindgebruiker is vooral de [NEN2660-2:2022][nen2660:2022] structuur van belang.

<figure>

![IMBOR structuur](img/IMBOR-structuur.drawio.png?raw=true)
    
<figcaption>IMBOR structuur' -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption>
</figure>

<div class='note'>
De IMBOR Ontologie is te verkennen in de IMBOR viewer op:
 <a href="https://docs.crow.nl/onto-verkenner/imbor" target="_blank">https://imbor-viewer.apps.crow.nl/</a> 
</div>

<div class='advisement'>

 __Semantiek t.o.v. MIM__
 
 Het [MIM][MIM] wordt op meerdere plekken aangehaald binnen IMBOR. Omdat IMBOR in eerste instantie de [NEN2660-2:2022][nen2660:2022] volgt is de semantiek tussen IMBOR en het MIM soms wat verwarrend. Daarom volgt hier een nadere toelichting:
 
 Het `Object` in MIM is de instantie van het `Objecttype` in MIM. Deze zijn allebei een UML `Class`. In IMBOR zijn er `Klassen` onderscheiden, sommige `Klassen` krijgen het synoniem `Objecttype`. Dit betreffen de concrete klassen en vaak de 'bladeren van de boom', ofwel de onderste in de hiërarchie. Deze concrete klassen (ofwel `Objectypen`) zijn degene waar instanties van te verwachten zijn in de beheerpakketten. Deze instanties worden weer `Object` genoemd (in lijn met MIM). De vergelijking is te maken met `Classes` en `Instances`.
 
 Het `Attribuut` en de `Attribuutsoort` in MIM zijn vergelijkbaar (conceptueel) met het `Object` en het `Objecttype` in MIM (de een is dus instantie van de ander). In IMBOR (en de NEN2660-2/OTL wereld) hebben zaken net een andere betekenis. Het `Attribuut` betreft de te registreren kenmerk of eigenschap van een `Klasse`. De `Attribuutsoort` werd in IMBOR2020-08 gebruikt om aan te geven 'wat voor een soort attribuut het betrof. Dit is in IMBOR niet meer aanwezig.
 
 In MIM wordt met het `Datatype` aangegeven wat de structuur is waaraan een waarde, oftewel de data zelf, aan moet voldoen. In IMBOR2020-08 zat dit vermengd in de `Attribuutsoort` en het `Gegevenstype`. Dit is anders aangepakt vanaf IMBOR2022. `Gegevenstype` is dan ook vervangen door `Datatype`.
 
 `Multipliciteit` en `Kardinaliteit` zijn onderwerp van discussie in verschillende gremia. Ook het MIM is hier niet eenduidige in. Binnen IMBOR2022 wordt de volgende werkwijze gehanteerd:

_Simply put: a multiplicity is made up of a lower and an upper cardinality. A cardinality is how many elements are in a set. Thus, a multiplicity tells you the minimum and maximum allowed members of the set. They are not synonymous._ [Source](https://stackoverflow.com/questions/17877582/multiplicity-vs-cardinality)

`Multipliciteit` is dus de algemene term om aan te geven hoe vaak iets voorkomt. De getallen die daar ingevuld staan, betreffen de `Kardinaliteit`. Een voorbeeld: De relatie tussen een fiets en wielen heeft een `Multipliciteit` met een minimale `Kardinaliteit` van 2 en een maximale `Kardinaliteit` van 2.

</div>

### Fysiek datamodel

Omdat IMBOR nu nog gedistribueerd wordt in een MS Access database en LinkedData is het fysieke datamodel een beschrijving van hoe de IMBOR onderdelen uitgedrukt worden. Dit betekent geenszins dat IMBOR ook dit fysieke datamodel voorschrijft bij implementatie. Het geeft wel een goed inzicht in hoe de relaties lopen en welke verschillende (normatieve) onderdelen IMBOR kent. Het model wordt nader beschreven in de volgende secties.

Het fysieke datamodel in LinkedData kan gelijk worden gesteld aan de 'serialisatie'. In het geval van IMBOR is dit [[turtle]].





[MIM]: https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#typen-informatiemodellen
[n1]: https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#niveau-1-model-van-begrippen
[n2]: https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#niveau-2-conceptueel-informatiemodel
[n3]: https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#niveau-3-logisch-informatie-of-gegevensmodel
[n4]: https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#niveau-4-fysiek-of-technisch-gegevens-of-datamodel
[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667