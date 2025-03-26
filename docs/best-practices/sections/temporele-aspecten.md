## NEN3610 Temporele Aspecten

***Gebaseerd op GitHub issue: [1075](https://github.com/Stichting-CROW/imbor/issues/1075).***

In 2022 is de meest recente versie van de [[NEN3610]] uitgekomen. [[IMBOR]] gebruikt deze standaard [al sinds 2022](https://docs.crow.nl/imbor/techdoc/#nen3610) als één van de bepalende standaarden waarop [[IMBOR]] gebouwd is. In de 2024 versie van [[IMBOR]] zullen er nog veel meer aspecten uit de [[NEN3610]] toegepast worden. Eén van die aspecten is het 'Temporele aspecten model'. Dit betreft hoofdstuk 8.3 uit de [[NEN3610]]. De belangrijkste redenen dat [[IMBOR]] volledig het temporele aspecten model van de [[NEN3610]] adopteert en toepast zijn:

- [[NEN3610]] staat op de ['pas-toe-of-leg-uit' lijst](https://www.forumstandaardisatie.nl/open-standaarden/geo-standaarden) van het Forum Standaardisatie en is daarmee een verplichte voor Nederlandse overheden (Rijk, provincies, gemeenten en waterschappen) en instellingen uit de (semi-) publieke sector;
- Geen eigen zaken meer bedenken, maar verwijzen (hergebruiken van) naar de [[NEN3610]] voor temporele aspecten;
- Duidelijkheid ten behoeve van de implementatie in software;
- Consistentie in gebruik van attributen om temporele aspecten vast te leggen.

De [[NEN3610]] is binnen de norm duidelijk over de conceptuele beschrijving van het temporele model en geeft een toepassing daarvan in een registratie. Deze best practice beschrijft als aanvulling een toepassing van het temporele model in een graph. Deze best practice gaat er vanuit dat de lezer bekend is met hoofstuk 8.3 uit de [[NEN3610]]. Passages daaruit worden hier dan ook niet herhaald. 

### Toepassing temporele aspecten uit NEN3610 in graphs

Er worden twee opties uitgewerkt om het [[NEN3610]] temporele aspecten model toe te passen in een graph. Deze opties zijn generiek voor al het gebruik in LinkedData, RDF en/of Knowledge Graphs. 
- Het voorbeeld gaat echter uit van een toepassing in [[IMBOR]]
- De uitwerkingen zijn gebaseerd op werk dat gedaan is bij [TOOI](https://standaarden.overheid.nl/tooi)
    - Een gedetailleerde beschrijving is gedaan door [Jan Voskuil](https://www.linkedin.com/in/jan-voskuil/) in de blogpost: [[History-TOOI-KG]]
- Tevens wordt gebruik gemaakt van de [NEN3610-2022 Ontologie](https://modellen.geostandaarden.nl/def/nen3610-2022/index.html)
- Het [voorbeeld](#example-voorbeeldtoepassing-van-het-temporele-model) waarmee gewerkt wordt komt uit de [[NEN3610]]-Bijlage C: 'Voorbeeldtoepassing van het temporele model'

>EXAMPLE "Voorbeeldtoepassing van het temporele model"
>De tabel beschrijft alle versies `idl`, met de kennis zoals aanwezig en beschikbaar op `t5`:
>- Versie 1: ongewijzigd, bevat dezelfde gegevens en tijdlijngegevens als in de vorige tabel.
>- Versie 2: bevat dezelfde gegevens als in de vorige tabel, nu met meer tijdlijngegevens.
>- Versie 3: geeft nu, vanaf `t5`, de laatste actuele gegevens weer.
>
>Bij een tijdreis vanaf `t5` (tot de volgende mutatie) wordt het antwoord gegeven vanuit deze tabel. Bij een tijdreis naar welke gegevens er beschikbaar zijn op een tijdsmoment eerder dan `t5`: zie vorige tabellen, en vanuit een van de vorige tabellen wordt dan het antwoord gegeven.
>
><figure>
>
>![NEN3610:2022 Temporele aspecten 'vanaf t5' (p. 128)](img/nen3610-2022-p128.png?raw=true)
>    
><figcaption>Tabel van pagina 128 uit NEN3610:2022 | 'vanaf t5 (tot de volgende mutatie)'</figcaption>
></figure>

Vanuit de [[NEN3610]] wordt de klasse `nen3610:Registratie` gezien als de 'metadata' van een informatieobject (een setje bij elkaar horende gegevens). In de het [voorbeeld](#example-voorbeeldtoepassing-van-het-temporele-model) van de [[NEN3610]] is te zien dat op verandermomenten sommige gegevens wel zijn veranderd en sommige niet. De verandermomenten zijn vastgelegd op het hele setje gegevens (het informatieobject). Hiermee is echter _geen_ onderscheidt te maken van de tijdlijn per attribuut en moet uit de data worden afgeleid welke eigenschap(pen), ofwel gegevens, zijn veranderd. [Optie A](#optie-a-cloning) komt zodoende het meest overeen met het detailniveau van de [[NEN3610]].  

Bij [optie B](#optie-b-3-d-met-rdf-star) is op attribuutniveau de tijdlijn opgenomen. Deze optie kan wat [optie A](#optie-a-cloning) kan en meer. [Optie A](#optie-a-cloning) is ook uit [optie B](#optie-b-3-d-met-rdf-star) af te leiden. Hiermee is [optie B](#optie-b-3-d-met-rdf-star) dan ook [[NEN3610]] compliant. Deze optie is toepasbaar in graphs en zal niet snel in een UML model, XML of regulier JSON toepassing terechtkomen.

#### Optie A: Cloning

Klonen is een methode om tijdlijn informatie te modelleren door kopieën van informatieobject te maken op verschillende tijdstippen, met behulp van een ontologie zoals PROV-O. Telkens wanneer een eigenschap of een informatieobject verandert, wordt er een kloon gemaakt met een andere URI om de vorige staat te behouden. Elke kloon vertegenwoordigt een (historische) versie of een tijdsinterval van de informatieobject. Deze aanpak zorgt ervoor dat het modelleren additief blijft, wat betekent dat het toevoegen van historische informatie het oorspronkelijke gegevensmodel niet ingewikkelder maakt. Met klonen is het relatief eenvoudig om historische toestanden te reconstrueren en individuele toestandsveranderingen in de loop van de tijd bij te houden. Een nadeel is echter de potentie voor een aanzienlijke hoeveelheid dubbele gegevens, wat misschien niet geschikt is voor scenario's met frequente wijzigingen of grote datasets.

<figure>

![Temporele aspecten in graph | Optie A](img/NEN3610-TempAspects-OptieA.drawio.png?raw=true)
    
<figcaption>Temporele aspecten in graph | Optie A: Cloning</figcaption>
</figure>

Dit is de uitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix nen2660: <https://w3id.org/nen2660/def#>.
@prefix prov: <http://www.w3.org/ns/prov#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.
@prefix gemX-history: <http://voorbeeld.org/gemX-history#>.

nen3610:Registratie             a  rdfs:Class .
nen3610:IdentificeerbaarObject  a  rdfs:Class .
imbor:Gebouw                    a  rdfs:Class .

gemX:id1    a                           imbor:Gebouw, nen3610:IdentificeerbaarObject, nen3610:Registratie ;
            nen3610:identificatie       "id1" ;
            nen3610:domein              gemX: ;
            nen3610:beginGeldigheid     "2009-11-12"^^xsd:date ;
            nen3610:tijdstipRegistratie "2009-11-16T13:00"^^xsd:dateTime ;
            nen3610:versie              "3" ;
            imbor:adres                 "Peperstraat" ;
            imbor:gebruiksdoel          "logiesfunctie" .

[] prov:used gemX:id1 ;
        prov:invalidated gemX-history:id1_1 .

gemX-history:id1_1    a                 imbor:Gebouw, nen3610:IdentificeerbaarObject, nen3610:Registratie ;
            nen3610:identificatie       "id1" ;
            nen3610:domein              gemX-history: ;
            nen3610:beginGeldigheid     "2006-06-02"^^xsd:date ;
            nen3610:eindGeldigheid      "2009-11-12"^^xsd:date ;
            nen3610:tijdstipRegistratie "2006-06-04T08:00"^^xsd:dateTime ;
            nen3610:eindRegistratie     "2009-11-12T10:00"^^xsd:dateTime ;
            nen3610:versie              "1" ;
            imbor:adres                 "Peperstraat" ;
            imbor:gebruiksdoel          "kantoorfunctie" ;
            prov:specializationOf       gemX:id1 .

[] prov:used gemX:id1 ;
        prov:invalidated gemX-history:id1_2 .

gemX-history:id1_2    a                 imbor:Gebouw, nen3610:IdentificeerbaarObject, nen3610:Registratie ;
            nen3610:identificatie       "id1" ;
            nen3610:domein              gemX-history: ;
            nen3610:beginGeldigheid     "2009-11-12"^^xsd:date ;
            nen3610:eindGeldigheid      "2009-11-12"^^xsd:date ;
            nen3610:tijdstipRegistratie "2009-11-12T10:00"^^xsd:dateTime ;
            nen3610:eindRegistratie     "2009-11-16T13:00"^^xsd:dateTime ;
            nen3610:versie              "2" ;
            imbor:adres                 "Peperstraat" ;
            imbor:gebruiksdoel          "woonfunctie" ;
            prov:specializationOf       gemX:id1 .
```


#### Optie B: 3½-D met RDF-star

Optie B is de 3½-D-aanpak. In deze optie worden historische wijzigingen gemodelleerd door alle eigenschappen te objectiveren en start- en einddatums toe te voegen om aan te geven gedurende welke periode een eigenschapwaarde geldig was. Dit resulteert in een triple per eigenschap waarin de waarden aan de de tijdstippen worden gelinkt. Hoewel deze aanpak efficiënt gebruikmaakt van de mogelijkheden van graphs, is het niet additief.  Het modelleren van eigenschappen is minder conventioneel en daarmee vooralsnog ingewikkelder. Hiermee is bij het reconstrueren van historische gegevens SPARQL-star nodig.

<figure>

![Temporele aspecten in graph | Optie B](img/NEN3610-TempAspects-OptieB-RDF-Star.drawio.png?raw=true)
    
<figcaption>Temporele aspecten in graph | Optie B: 3½-D met RDF-star</figcaption>
</figure>

Dit is de uitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.

nen3610:Registratie             a  rdfs:Class .
nen3610:IdentificeerbaarObject  a  rdfs:Class .
imbor:Gebouw                    a  rdfs:Class .

gemX:id1  a                       imbor:Gebouw, nen3610:IdentificeerbaarObject ;
          nen3610:identificatie   "id1" ;
          nen3610:domein          gemX: .

<<gemX:id1  imbor:gebruiksdoel  "kantoorfunctie"  >>  nen3610:registratiegegevens  gemX-regX:id1_1 .
<<gemX:id1  imbor:gebruiksdoel  "woonfunctie"     >>  nen3610:registratiegegevens  gemX-regX:id1_2 .
<<gemX:id1  imbor:gebruiksdoel  "logiesfunctie"   >>  nen3610:registratiegegevens  gemX-regX:id1_3 .
<<gemX:id1  imbor:adres         "Peperstraat"     >>  nen3610:registratiegegevens  gemX-regX:id1_0 .

gemX-regX:id1_0 a nen3610:Registratie ;
            nen3610:beginGeldigheid     "2006-06-02"^^xsd:date ;
            nen3610:tijdstipRegistratie "2009-11-16T13:00"^^xsd:dateTime .
gemX-regX:id1_1 a nen3610:Registratie ;
            nen3610:beginGeldigheid     "2006-06-02"^^xsd:date ;
            nen3610:eindGeldigheid      "2009-11-12"^^xsd:date ;
            nen3610:tijdstipRegistratie "2006-06-04T08:00"^^xsd:dateTime ;
            nen3610:eindRegistratie     "2009-11-12T10:00"^^xsd:dateTime .
gemX-regX:id1_2 a nen3610:Registratie ;
            nen3610:beginGeldigheid     "2009-11-12"^^xsd:date ;
            nen3610:eindGeldigheid      "2009-11-12"^^xsd:date ;
            nen3610:tijdstipRegistratie "2009-11-12T10:00"^^xsd:dateTime ;
            nen3610:eindRegistratie     "2009-11-16T13:00"^^xsd:dateTime .
gemX-regX:id1_3 a nen3610:Registratie ;
            nen3610:beginGeldigheid     "2009-11-12"^^xsd:date ;
            nen3610:tijdstipRegistratie "2009-11-16T13:00"^^xsd:dateTime .
```


#### Optie B: 3½-D met RDF Reïficatie

Er is nog een variant van optie B zonder het gebruik van (het relatief nieuwe) RDF-star. In deze optie worden historische wijzigingen gemodelleerd door alle eigenschappen te reïficeren (in plaats van de triple-reïficatie zoals in de andere variant van optie B). Op deze manier wordt in de modellering expliciet gemaakt wat de semantiek is van deze statements (dit kan met of zonder blank nodes) . Bij deze variant kan worden volstaan met reguliere SPARQL. Verder geldt voor deze variant hetzelfde als de voorgaande.

<figure>

![Temporele aspecten in graph | Optie B](img/NEN3610-TempAspects-OptieB-Reification.drawio.png?raw=true)
    
<figcaption>Temporele aspecten in graph | Optie B: 3½-D met RDF Reïficatie</figcaption>
</figure>

Dit is de uitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.

nen3610:Registratie             a           rdfs:Class .
nen3610:IdentificeerbaarObject  a           rdfs:Class .
imbor:Gebouw                    a           rdfs:Class .
imbor:GebruiksdoelAspect        a           rdfs:Class .
imbor:AdresAspect               a           rdfs:Class .

gemX:id1        a                           imbor:Gebouw, nen3610:IdentificeerbaarObject ;
                nen3610:identificatie       "id1" ;
                nen3610:domein              gemX: ;
                imbor:gebruiksdoel          gemX-reg:id1_1 ;
                imbor:gebruiksdoel          gemX-reg:id1_2 ;            
                imbor:gebruiksdoel          gemX-reg:id1_3 ;
                imbor:adres                 gemX-reg:id1_0 .

gemX-reg:id1_1  a                           imbor:GebruiksdoelAspect ;
                rdf:value                   "kantoorfunctie" ;
                nen3610:beginGeldigheid     "2006-06-02"^^xsd:date ;
                nen3610:eindGeldigheid      "2009-11-12"^^xsd:date ;
                nen3610:tijdstipRegistratie "2006-06-04T08:00"^^xsd:dateTime ;
                nen3610:eindRegistratie     "2009-11-12T10:00"^^xsd:dateTime .
                                
gemX-reg:id1_2  a                           imbor:GebruiksdoelAspect ;
                rdf:value                   "woonfunctie" ;
                nen3610:beginGeldigheid     "2009-11-12"^^xsd:date ;
                nen3610:eindGeldigheid      "2009-11-12"^^xsd:date ;
                nen3610:tijdstipRegistratie "2009-11-12T10:00"^^xsd:dateTime ;
                nen3610:eindRegistratie     "2009-11-16T13:00"^^xsd:dateTime .
                                
gemX-reg:id1_3  a                           imbor:GebruiksdoelAspect ;
                rdf:value                   "logiesfunctie" ;
                nen3610:beginGeldigheid     "2009-11-12"^^xsd:date ;
                nen3610:tijdstipRegistratie "2009-11-16T13:00"^^xsd:dateTime .
  
gemX-reg:id1_0  a                           imbor:AdresAspect ;
                rdf:value                   "Peperstraat" ;
                nen3610:beginGeldigheid     "2006-06-02"^^xsd:date ;
                nen3610:tijdstipRegistratie "2009-11-16T13:00"^^xsd:dateTime .
```


### Toepassing van opties

De vraag rijst uiteraard wanneer welke optie toegepast moet worden. Dit ligt met name aan de toepassing. Er is namelijk een onderscheid te maken in een toepassing waar data gedeeld wordt tussen systemen en een toepassing welke alleen binnen één systeem geldt. Er is wat voor te zeggen dat [optie A](#optie-a-cloning) zou kunnen gelden wanneer data gedeeld moet worden en dat [optie B](#optie-b-3-d-met-rdf-star) vooral geldt binnen de registratie van een asset beheer pakket. Overigens is [optie B](#optie-b-3-d-met-rdf-star) ook prima toepasbaar om data mee te delen. 

Het verschil tussen de varianten in optie B heeft vooral te maken met of de gebruikte ontologie voldoende ver gemodelleerd is (in het voorbeeld: de gebruikte aspecten onderscheidt). En/of in de complimenterende systemen RDF-star ondersteund wordt.

|         | Data delen | Database implementatie in één systeem |
|---------|------------|---------------------------------------|
| Optie A | Ja         | Nee                                   |
| Optie B | Ja         | Ja                                    |
| {.data} |

### A-synchrone mutatie

In het geval van het 'versturen' van een mutatie tussen twee systemen, is het dan logisch om ook de `dateTime` van het registratieobject mee te sturen, of _is_ dat dit de `dateTime` waarop de mutatie daadwerkelijk wordt ontvangen en verwerkt? In het geval van de [[NEN3610]] zijn mutaties (de TijdlijnRegistratie) de momenten waarop gegevens in een registratie worden bijgewerkt en de service als het ware op de hoogte is van het tijdstip van de verandering in de registratie en daarop te bevragen is. De vraag 'wat weet de registratie', en een mogelijke afnemer op welk moment is van belang. Het is daarbij van belang om te definiëren welk systeem gezien moet worden als single-point-of-truth voor dat setje gegevens. Denk daarbij aan een scheiding tussen één front-office die gegevens van een registratie serveert en een back-office met verschillende beheersystemen.

Bijvoorbeeld in het geval dat er een 'centrale asset registratiesysteem' is en applicaties daarom heen die gegevens muteren is de mutatie in het centrale asset register leidend. Als er namelijk een centrale database is  waarin de gegevens worden opgeslagen en een beheerpakket synchroniseert met deze gegevens, dan kan er tijd zitten tussen het moment van mutatie in de beheerapplicatie en de verwerking ervan in het centrale asset register. Hier mag er vanuit gegaan worden dat het moment van verwerking in het centrale register het belangrijkste is om te delen, omdat dit het moment is waarop de verwerking operationeel wordt. In de [[NEN3610]] wordt namelijk gesteld `TijdstipRegistratie`: Tijdsaanduiding van het moment waarop deze versie van het informatieobject is opgenomen in de registratie. En `Registratie`: Geïdentificeerde en erkende gegevensverzameling. De TijdlijnRegistratie is bedoeld om aan te geven op welk moment een gegeven in de registratie is opgenomen en dus ook operationeel bevraagbaar, kenbaar gemaakt kan worden.
