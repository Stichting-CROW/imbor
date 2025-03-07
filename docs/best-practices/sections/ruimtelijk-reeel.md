## Ruimtelijk (virtueel) vs. Reëel (fysiek)

***Gebaseerd op GitHub issue: [1290](https://github.com/Stichting-CROW/imbor/issues/1290).***

Vanaf IMBOR2022 is er een verschil gemaakt tussen Ruimtelijke en Reële objecten. 
Dit onderscheid is te herleiden naar zowel de [NEN2660][nen2660:2022] (2022, p. 24) als de [NEN3610][nen3610:2022] (2022, p. 60). 

### NEN2660 & NEN3610

**NEN2660**:
In de [NEN2660][nen2660:2022] worden fysieke objecten optioneel, niet-samenvallend opgedeeld in niet-direct tastbare `ruimtelijke gebieden` (bijvoorbeeld Rijbaan, Centrumgebied en Putschat) en tastbare `reële objecten` (bijvoorbeeld Beweegbare brug, Boom en Laagspanningskabel). De 'bevat'-relatie bij een ruimtelijk gebied kan worden gebruikt voor reële objecten die zich in dat gebied bevinden en voor de, typisch gasvormige, hoeveelheid bulkmaterie die zich in dat gebied bevindt.

**NEN3610**:
Reële objecten en virtuele ruimten kunnen onafhankelijk van elkaar geclassificeerd worden. Reële objecten zijn in de fysieke werkelijkheid aanwezig en kunnen geclassificeerd worden aan de hand van hun totstandkomingsproces, de samenstelling (fysiek voorkomen) en het eventuele beoogde gebruik. Een synoniem voor reële objecten is fysieke objecten. Virtuele ruimten zijn alleen in een registratie aanwezig en niet fysiek in de werkelijkheid. Ze kunnen worden geclassificeerd aan de hand van
abstracte mentale concepten, zoals bijvoorbeeld functie en regelgeving. Virtuele ruimten hebben begrenzingen die meestal in een administratiefproces zijn bepaald. Virtuele ruimten kunnen daarom reële objecten als harde begrenzing hebben. 

Het _NEN3610 reëel object_ komt overeen met het _NEN2660 technisch reëel object_. Dat betekent dat het hierbij gaat om de fysieke eigenschappen van het object. De _NEN3610 virtuele ruimte_ komt overeen met de _NEN2660 functionele ruimte_. Onderling kennen reële objecten en virtuele ruimten diverse typen relaties. Die relaties kunnen heel sterk zijn, waardoor het reële object en het virtuele object op elkaar kunnen lijken. Bijvoorbeeld een verblijfsobject (virtueel) dat dezelfde afbakening heeft als het gebouw (reëel) dat het verblijfsobject vormt (_realiseert_). Relaties tussen andere reële en virtuele objecten kunnen veel zwakker zijn. Zo kan bijvoorbeeld een gemeentegrens ooit zijn bepaald aan de hand van de reële objecten in de werkelijkheid, maar wordt het vervolgens niet meer noodzakelijkerwijs beïnvloed door wat er met de reële objecten gebeurt.

### Toepassing ruimtelijk en reëel in IMBOR
In IMBOR zijn ruimtelijke gebieden opgenomen zoals `WijkGrens`, `Buurtgrens` en `Recreatiegebied`. Deze ruimtelijke gebieden zijn in principe geometrische vlakken en kunnen ook in die hoedanigheid geïnstantieerd worden. Zodra deze entiteiten beschikbaar zijn, is geometrisch af te leiden of er reële objecten binnen de grenzen van deze entiteiten liggen. Er is dan in principe sprake van een `bevat` relatie. Een ruimtelijk gebied bevat dan een `reëel object`. Deze relatie kan expliciet worden gelegd. Dit kan handig zijn voor (geometrische) query's of voor de situatie waar nog geen geometrie bekend is van een entiteit. 

>EXAMPLE
>Binnen de gemeente X worden Abri's geregistreerd. Men wilt weten hoeveel Abri's er binnen een bepaalde wijk aanwezig zijn om de dichtheid te bekijken. Hiervoor kan een geometrische query gedaan worden en/of de relatie expliciet worden gelegd. In onderstaand geval zijn er twee Abri's (te weten: Abri1 en Abri2) die liggen binnen de wijk 'Heseveld'. 

Dit is een voorbeeld-uitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix nen2660: <https://w3id.org/nen2660/def#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.

gemX:Heseveld   a   imbor:b5947439-11e6-423e-b67b-671905610154 ;            # Wijkgrens
                imbor:ee97b257-d3b8-4d0c-9a42-c07d88b36d9f "Heseveld"@nl ;  # Objectnaam
                nen3610:domein  "http://voorbeeld.org/gemX#" ;              
                nen3610:identificatie   "Heseveld" ;
                nen2660:contains   gemX:Abri1, gemX:Abri2 ;                 # bevat 
                .

gemX:Abri1      a   imbor:c4522e75-7f0b-4bbe-a3c7-e93f34cc8b31 ;            # Abri
                nen3610:domein  "http://voorbeeld.org/gemX#" ;
                nen3610:identificatie "Abri1" ;
                imbor:a6424f8a-080e-4f85-a160-6fa4f0848ed8 "1" ;            # Objectnummer
                .

gemX:Abri2      a   imbor:c4522e75-7f0b-4bbe-a3c7-e93f34cc8b31 ;            # Abri
                nen3610:domein  "http://voorbeeld.org/gemX#" ;
                nen3610:identificatie "Abri2" ;
                imbor:a6424f8a-080e-4f85-a160-6fa4f0848ed8 "2" ;            # Objectnummer
                .

```

>ADVISEMENT
>IMBOR geeft voorbeelden van `bevat` relaties, maar het is uiteraard toegestaan om *elk* `nen2660:RealObject` te verbinden met een `nen2660:SpatialRegion` volgens de `nen2660:contains` relatie.



[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667
