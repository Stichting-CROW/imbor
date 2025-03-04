## IMBOR distributie 

Voor de gebruiker van IMBOR wordt een inkijkmogelijkheid (publicatie) van IMBOR op meerdere manieren gegeven:
* Via een online viewer: [imbor-viewer.apps.crow.nl](https://imbor-viewer.apps.crow.nl)
* Via formulieren in een MS Access database
* Via voor gedefinieerde query’s op de [CROW SPARQL webapplicatie](https://sparql.crow.nl/ldp)
* Via het [begrippen platform](https://begrippen.crow.nl/imbor/nl/) van CROW is het begrippenkader (vocabulaire) van IMBOR te raadplegen

Al deze vormen van publicatie zijn _zonder kosten_ te raadplegen. Voor de [CROW SPARQL webapplicatie](https://sparql.crow.nl/ldp) is wel een [MijnCROW account][mijncrow] nodig.

Wanneer IMBOR geïmplementeerd moet worden in software is uiteraard de gehele content beschikbaar. Hiervoor zijn ook twee distributiekanalen beschikbaar:
* IMBOR in LinkedData (TTL file en SPARQL-Endpoint)
* IMBOR tabellen in MS Access database

Alle informatie hierover en versies hiervan is/zijn via [GitHub releases](https://github.com/Stichting-CROW/imbor/releases) te raadplegen. Wat betreft het gebruik van IMBOR, raadplegen de sectie over [licenties](#licenties)

<div class='advisement'>
Al deze vormen van distributie zijn (voorlopig) zonder kosten te raadplegen; Namelijk voor de SPARQL-Endpoint geldt dat we deze voorlopig onder de noemer van 'pilot' verstrekken. Bij veel gebruik/op termijn wordt gekeken hoe we hier met de kosten gaan omgaan. 
</div>

<figure>

![IMBOR Beheer Distributie Publicatie](img/IMBOR_Beheer_Distributie_Publicatie.drawio.png?raw=true)
    
<figcaption>Overzicht IMBOR Beheer, Distributie en Publicatie</figcaption>
</figure>

### IMBOR in MS Access

IMBOR wordt momenteel beheerd in MS Access. In onderstaande diagram is een overzicht van de databasestructuur gegeven. 
Het betreft hier dus ___niet___ een voorgeschreven datamodel voor een beheerapplicatie.  

IMBOR is modulair opgebouwd, in Access wordt dit met de tabel prefixen vastgelegd.
- `imborVoc_*` zijn de tabellen die het begrippenkader (of vocabulaire) van IMBOR beschrijven
- `imborKern_*` zijn de tabellen die de (normatieve) elementen binnen de IMBOR ontologie beschrijven
- `imborKern_K_*` zijn koppeltabellen binnen de ontologie die eigenlijk predicaten beschrijven
- `refModel_*` zijn tabellen waarin externe ontologieën aangehaald worden. Hier staan de benodigde gegevens om relaties naar toe te kunnen leggen.
- `imbor_logging*` zijn tabellen die voor de logging gebruikt worden

<figure>

![IMBOR AccessDB structuur](img/IMBOR-AccessDB-Structuur.drawio.png?raw=true)
    
<figcaption>IMBOR AccessDB structuur -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption>
</figure>

Hieronder worden voor de vocabulaire en de het kernmodel een toelichting gegeven per tabel. De overige tabellen zijn voor de werking van de AccesDB zelf. 

#### Vocabulaire

Alle tabellen die invulling geven aan de IMBOR Vocabulaire.

##### imborVoc_Termen

Deze tabel is onderdeel van het begrippenkader van IMBOR kan gezien worden als de vocabulaire. Deze heeft deze binnen Access een speciale status omdat hier de `IMBORGUID` ook gedeclareerd wordt voor de meeste elementen. Bijna alle tabellen halen hier informatie op. De tabel geeft inrichting aan het Niveau 1 van MIM (Model van begrippen) en aan de SKOS taalbindingen uit de [NEN2660-2:2022][nen2660:2022]. 
Speciaal geval is ook de kolom `KlasseType`. Deze is gekoppeld aan de `IMBORGUID`  zoals hiervoor vermeld. `KlasseType` geeft aan of een IMBOR concept geïnstanteerd kan worden (`Concreet`) of niet (`Abstract`). 

##### imborVoc_Collecties

De enige andere tabel in het begrippenkader naast `imborVoc_Termen`. Dit betreft een overzicht van de collecties waarin de termen ingedeeld zijn. 

#### Kernmodel

Alle tabellen die invulling geven aan het IMBOR Kernmodel.

##### imborKern_Attributen

Deze tabel bevat alle attributen die in IMBOR voorkomen, inclusief hun `Datatype`. De datatype volgen het [[xmlschema11-1]] en waar van toepassing wordt aangegeven of het een `Enumeratie-` of `Referentie`lijst betreft. 

##### imborKern_EnumeratiesDomeinwaarden

In deze tabel staan alle `EnumeratieType` binnen IMBOR, inclusief de relatie naar de `Domeinwaarde`. Het EnumeratieType en de Domeinwaarde worden één keer gedefinieerd in `imborVoc_Termen` en worden hier middels 1-op-N relaties aan elkaar gekoppeld. 

De kolom BovenliggendeWaarde wordt gebruikt om aan te geven hoe de domeinwaarden zich tot elkaar hiërarchisch verhouden. Dit betreft een hulpkolom die nodig is om de formulieren op te bouwen en is niet normatief nodig.

##### imborKern_Hierachie

In deze simpele tabel wordt de polyhiërarchie van IMBOR beschreven. Concepten kunnen meerdere parents hebben. Door middel van de parent-child relatie wordt overerving geregeld. Alle childs krijgen ook de attributen van hun parents. Daarmee geldt dat ook alle `Objecttype`en die onder de klassen hangen ook op dezelfde manier attributen overerven.  Deze tabel is eigenlijk de vastlegging van het predicaat `isSubType`. Hier staat dus ook tot welke klasse een `Klasse`  of `Objecttype` behoord en daarmee zijn eigenschappen (lees: attributen) overerft. Sinds IMBOR2025 wordt hier ook de hiërarchie van `Attributen` en `Relaties` bijgehouden. Middels de kolom `HierarchieType` wordt aangegeven welke soort er hiërarchisch ingedeeld wordt.

##### imborKern_K_KlasseAttributen

Dit betreft een koppeltabel waarin de attributen aan de klassen gekoppeld worden. Inclusief een indicatie van de `Multipliciteit` en in welke `Eenheid` dit attribuut vastgelegd kan worden.

Er komen o.a. `Objecttype`n, `Klassen`, `ObjecttypeOnderdelen` en `Informatieobject`en voor in de kolom `Klasse`. Dit lijkt vreemd, maar is correct omdat het technisch gezien allemaal `Klasse` zijn (ofwel: subtypen van `Klasse`)

Daarnaast wordt de kolom `Informatiemodel` gebruikt om aan te geven in welk extern model er voor heeft gezorgd dat het betreffende attribuut is opgenomen in IMBOR. Hier wordt op termijn als nodig een mapping voor gemaakt. Nu is het 'beheerinformatie'.

De kolom OAGBD wordt gebruikt voor het informatieve deel dat beschreven wordt in het [OAGBD addendum](#oagbd).

Als laatste staat hier ook welke waardelijst van toepassing is. Dit staat in `EnumeratieType`.

##### imborKern_K_ObjecttypenSemantischeRelaties

In deze tabel zijn de relaties opgenomen die normerend zijn binnen de IMBOR ontologie (inclusief hun multipliciteit). De relaties zelf ontlenen hun semantiek aan de [NEN2660-2:2022][nen2660:2022]. 

<div class='advisement'>
Deze lijst is voorschrijvend, maar niet limitatief. In de implementatie mag een gebruiker zelf kiezen welke relaties er tussen de verschillende klassen aangegeven mag worden. Als er een relatie ontbreekt kan deze in de eigen implementatie gewoon gelegd worden. Uiteraard wil de IMBOR beheercommissie graag op de hoogte gehouden worden van deze inzichten.
</div>

##### imborKern_K_ZoekingangenObjecttypen

Met deze tabel wordt aangegeven binnen welke `Zoekingang` een `Objecttype` kan voorkomen. Het betreft hier groepering die ook niets meer dan dat is. Binnen IMBOR wordt deze voornamelijk gebruikt als zoekingang of als structurering om de hoeveelheid `Objecttype` makkelijker te kunnen inzien. 


### IMBOR in LinkedData

Naast de distributie in de relationele tabellen van Acces wordt ook een LinkedData variant aangeboden. Deze is gebaseerd op hetzelfde model als de Access versie. Omdat vooralsnog de Access database tevens als beheeromgeving voor IMBOR wordt gebruikt is de LinkedData versie een transformatie van de tabellen. De LinkedData versie wordt via een transformatie gepubliceerd uit de beheeromgeving. In de transformatie wordt de data getransformeerd naar het onderstaande structuur. 

<figure>

![IMBOR LD Structuur](img/IMBOR-LD-Structuur.drawio.png?raw=true)
    
<figcaption>IMBOR LinkedData Structuur -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption>
</figure>

#### Ontologie indeling (in grafen)

Ook de LinkedData versie van IMBOR (IMBOR-LD) is volgt de modulaire indeling. In IMBOR-LD wordt dit met verschillen grafen (gerepresenteerd via prefixen) vastgelegd.
- `imbor-term:*` zijn de concepten die het begrippenkader (of vocabulaire) van IMBOR beschrijven.
- `imbor:*` zijn de concepten die de (normatieve) elementen binnen de IMBOR ontologie beschrijven (dit staat gelijk aan de 'imborKern').
- `imbor-domeinwaarde:*` zijn alle domeinwaarden binnen IMBOR (dit zijn instanties). Deze staan in een aparte graaf vanwege de overzichtelijkheid.
- `imbor-refmodels:*` zijn de concepten waarin externe ontologien aangehaald worden. Hier staan de benodigde gegevens om relaties naar toe te kunnen leggen.

Omdat IMBOR een extensie is van de [NEN2660-2:2022][nen2660:2022] is de IMBOR kern direct 'gesubclassed' aan de [NEN2660-2:2022][nen2660:2022] concepten. Vandaar dat de concepten die we gebruiken uit de [NEN2660-2:2022][nen2660:2022] afgebeeld zijn met de prefix `nen2660:*`. 

<div class='note'>
In de <a href="https://www.nen.nl/nen-2660-2-2022-nl-291667">NEN2660-2:2022</a> zit een kleine inconsistentie met GeoSPARQL. Er wordt namelijk niet verteld hoe deze toegepast moet worden. Om dit praktisch op te lossen wordt in de IMBOR Kern gesteld dat: `nen2660:hasBoundary rdfs:subPropertyOf geo:hasGeometry`. Dit kan gezien worden als een verduidelijking van de <a href="https://www.nen.nl/nen-2660-2-2022-nl-291667">NEN2660-2:2022</a> voor de IMBOR context. Dit wordt opgelost in de Europese versie van de NEN2660-2, te weten de <a href="https://www.nen.nl/nen-en-17632-1-2022-en-304869">CEN17632</a>.
</div>

#### Begrippenkader

Dit zijn alle classes (concepten) die tezamen het vocabulaire vormen (e.g. de thesaurus).
##### imbor-term:Term

Op deze class worden alle attributen vastgelegd die het concept (conceptueel) definiëren in tekstuele zin en vormt daarmee de basis voor het vocabulaire.

##### imbor-term:Collectie

Deze class bevat alle collecties waarin de termen kunnen worden ingedeeld.
#### NEN2660

Dit zijn alle classes uit de [NEN2660-2:2022][nen2660:2022]2 waaraan wij ons committeren. De basis betreft met name het `nen2660:DiscreteObject` (buiten de [NEN2660-2:2022][nen2660:2022] wordt dit ook wel als een 'Fysieke Object' gezien) en de `nen2660:SpatialRegion` (ook wel het 'Ruimtelijk Gebied'). Daarnaast betrekken we het `nen2660:InformationObject` om beschrijvingen toe te voegen en `nen2660:Activity` om functies te kunnen definiëren. 

| NEN2660 Concept             | Definitie                                                                                                                                                                                                                            |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `nen2660:DiscreteObject`    | A real object consisting of a contiguous amount of form-retaining matter, held together primarily by internal forces (gravity, electromagnetic force)                                                                                |
| `nen2660:SpatialRegion`     | A physical object that encloses a certain area such as rooms, roads and rivers that is bound by real objects, other spatial regions or based on use or convention and that is empty or contains discrete or liquid or gaseous matter |
| `nen2660:InformationObject` | Thing that is a whole of information on itself and has an own identity                                                                                                                                                               |
| `nen2660:GeometricEntity`   | A spatial representation                                                                                                                                                                                                             |
| `nen2660:EnumerationType`   | A type having a fixed or extendable set of simple instances having no further attributes or relations                                                                                                                                |
| `nen2660:Activity`          | An activity is something possibly or actually happening in space and time                                                                                                                                                            |
| `nen2660:Matter`            | A pure chemical substance, chemical bonding or mixture from which real objects are made                                                                                                                                              |
| `imbor:Actor`               | Een entiteit die in staat is om handelingen uit te voeren en een specifieke functie of positie te vervullen in een bepaalde context.                                                                                                 |
| `imbor:Rol`                 | Een samenhangende verzameling van verwachtingen, verantwoordelijkheden, bevoegdheden en gedragingen die een Actor kan aannemen in relatie tot iets.                                                                                  |
| { .data }    |      

Vanaf IMBOR2025 is er een nieuw modelleerpatroon geïntroduceerd om relaties tussen klassen en actoren te modelleren, middels rollen. Deze constructie is ontleend uit de [NEN2660-1:2022](nen2660-1:2022). Zie hiervoor de sectie [Actoren en Rollen](#actoren-en-rollen). Verder bevat het IMBOR kernmodel niet veel meer dan 'Objecten', 'Attributen', 'Domeinwaarden' en 'Relaties'. Dit wordt nog aangevuld met `Zoekingangen`. Het kernmodel is uitgevoerd in [[rdf-schema]] en [[shacl]]. Dit is volgens de taalbinding van de NEN2660-2 gedaan. Daarom is voor ieder concept in het Kernmodel ook een `rdfs:seeAlso` relatie aanwezig die naar de term in de IMBOR Vocabulaire verwijst. Hieronder worden alle onderdelen beschreven. 

##### imbor:Klasse

Deze class betreft alle Klassen die IMBOR bevat. Met het attribuut `dash:abstract` wordt aangegeven of iets abstract (`true`) of concreet (`false`) is. Waarbij met concreet bedoeld wordt dat er in een beheersysteem of bij uitwisseling ook daadwerkelijk instanties van gemaakt zullen worden. Abstracte classes zullen voor eindgebruik niet heel belangrijk zijn en voor de meeste eindgebruikers ook niet zichtbaar zijn. De class heeft verder twee belangrijke relaties naar [NEN2660-2:2022][nen2660:2022] concepten. Dit betreffen `nen2660:isDescribedBy` die naar het `nen2660:InformationObject` loopt en `nen2660:hasBoundary` die naar de `nen2660:GeometricEntity` loopt. Met de eerste wordt dus aangegeven dat 'meer informatie over het de `imbor:Klasse` te vinden is bij het het `InformatieObject`. Met de tweede wordt aangegeven dat de (concrete) `imbor:Klasse` gebonden is door een geometrie. Ofwel, er kan een geometrie van vastgelegd worden. 
##### imbor:KlasseAttribuut

Deze class (die middels `sh:property` aan de `imbor:Klasse` hangt) is eigenlijk de koppeling tussen het 'Object' en het 'Attribuut'. Dit is een zogenaamde 'SHACL PropertyShape' en definieert dus welke attributen van toepassing zijn bij welk Objecttype en legt daar zaken over vast zoals: maximale kardinaliteit, in welke unit dit uitgedrukt moet worden van welke datatype het betreft. Er zijn in het schema twee beschrijvingen van `imbor:KlasseAttribuut` te zien. Dit komt omdat de property-shapes anders in elkaar zitten wanneer het een voorgedefinieerd datatype betreft (iets uit de [[xmlschema11-1]] lijn), dan wanneer het een waardelijst is.
##### imbor:Attribuut

Middels `sh:path` wordt de `imbor:KlasseAttribuut` verbonden met de daadwerkelijke `imbor:Attribuut`. Dit kan gezien worden als de 'conventionele' declaratie van het IMBOR attribuut. 
##### imbor:EnumeratieType

De `imbor:KlasseAttribuut` wordt middels `sh:class` verbonden aan de `imbor:EnumeratieType`. Dit is een `nen2660:EnumerationType`. Deze lijst bevat eigenlijk 'instanties' van de daadwerkelijke domeinwaarden.
##### imbor-domeinwaarde:Domeinwaarde

Dit zijn de daadwerkelijke domeinwaarden die middels een `rdf:type` aan de ``imbor:EnumeratieType` gehangen worden. Deze worden (volgens MIM gebruik) in een aparte graaf geplaatst zodat de kern niet te groot wordt en omdat deze domeinwaarden vaker aan verandering onderhevig zijn.
##### imbor:Zoekingang

De instanties van deze class zijn de IMBOR Vakdisciplines. Deze declareren middels een `rdfs:member` welke ObjectTypen uit `imbor:Klasse` binnen een vakdiscipline vallen.

#### Aanvullend 'metamodel'

Een aantal metaconcepten worden specifiek voor IMBOR gedefinieerd. Dit wordt gedaan middels het ['IMBOR Aanvullend Metamodel'](https://github.com/Stichting-CROW/imbor-development/blob/main/data/rdf/imbor-aanvullend-metamodel.ttl). Dit betreft een kleine ontologie van beschrijvende concepten die er voor zorgen dat alle IMBOR specifieke properties netjes en navolgbaar gedefinieerd zijn.
>ToDO juist link

[mijncrow]: https://crowsso.b2clogin.com/crowsso.onmicrosoft.com/B2C_1A_signup_signin/oauth2/v2.0/authorize?client_id=e0b429f6-ef7f-4d0e-be5f-2711b5d4393f&redirect_uri=https://crow.nl/Truelime/AzureADAuthenticationHandler.ashx&response_type=code&scope=openid&response_mode=query&state=eyJSZXR1cm5VcmwiOiIvTWlqbkNST1cvSG9tZSIsIlNob3BwaW5nQ2FydCI6IjAwMDAwMDAwLTAwMDAtMDAwMC0wMDAwLTAwMDAwMDAwMDAwMCIsIklkIjoiODQwYzBlYmMtZjBmOC00YmE5LTg3YzAtZGEwYThiZGUxYmMwIiwiU2lnbk91dCI6ZmFsc2V9
[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667