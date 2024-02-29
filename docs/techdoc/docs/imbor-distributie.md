## IMBOR distributie 

Voor de gebruiker van IMBOR wordt een inkijkmogelijkheid (publicatie) van IMBOR op meerdere manieren gegeven:
* De gedistribueerde Access database biedt middels formulieren de mogelijkheid om direct IMBOR te raadplegen
* Middels voorgedefinieerde queries op de CROW SPARQL webapplicatie
* De vocabulair van IMBOR is te raadplegen via het thesaurus platform van CROW [begrippen.crow.nl](https://begrippen.crow.nl/)
* In de loop van 2022 wordt een ontologie viewer ter beschikking gestelt

Al deze vormen van publicatie zijn zonder kosten te raadplegen. Voor de CROW SPARQL webapplicatie is wel een [MijnCROW account][mijncrow] nodig. 

Wanneer IMBOR geïmplementeerd moet worden in software is uiteraard de gehele content beschikbaar. Hiervoor zijn ook twee distributiekanalen:
* IMBOR tabellen in Access
* IMBOR in LinkedData (TTL file en SPARQL-Endpoint)

Al deze vormen van distributie zijn (voorlopig) zonder kosten te raadplegen; Namelijk voor de SPARQL-Endpoint geldt dat we deze voorlopig onder de noemer van 'pilot' verstrekken. Bij veel gebruik/op termijn wordt gekeken hoe we hier met de kosten gaan omgaan. 

Wat betreft het gebruik van IMBOR, raadplegen de sectie over [licenties](#licenties)

<figure>

![IMBOR Beheer Distributie Publicatie](img/IMBOR_Beheer_Distributie_Publicatie.drawio.png?raw=true)
    
<figcaption>Overzicht IMBOR Beheer, Distributie en Publicatie</figcaption>
</figure>

<div class='note'>

De IMBOR Ontologie viewer is nog in ontwikkeling en zal in de loop van 2022 klaar zijn. 

</div>


### IMBOR in MS Access

Omdat IMBOR momenteel nog beheerd wordt in MS Access is het fysieke datamodel hier van toepassing. Middels het fysieke datamodel diagram wordt een uitleg gegeven hoe deze geïnterpreteerd moet worden. 
Het betreft hier dus ___niet___ een voorgeschreven datamodel voor een beheerapplicatie.  

<figure>

![IMBOR fysiek datamodel Access](img/Modulaire%20opzet%20IMBOR-Fysiek%20Datamodel%20Access.drawio.png?raw=true)
    
<figcaption>IMBOR fysiek datamodel -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption>
</figure>

#### Tabelindeling

IMBOR is modulair opgebouwd, in Access wordt dit met de tabel prefixen vastgelegd.
- `imborVoc_*` zijn de tabellen die het begrippenkader (of vocabulaire) van IMBOR beschrijven
- `imborKern_*` zijn de tabellen die de (normatieve) elementen binnen de IMBOR ontologie beschrijven
- `imborKern_K_*` zijn koppeltabellen binnen de ontologie die eigenlijk predicaten beschrijven
- `refModel_*` zijn tabellen waarin externe ontologieën aangehaald worden. Hier staan de benodigde gegevens om relaties naar toe te kunnen leggen.

<div class='advisement'>

Er is gekozen om het fysieke datamodel van de MS Access database te versimpelen t.o.v. de theoretische uitwerking, dit is gedaan zodat in MS Access gemakkelijker query's opgezet kunnen worden. Een belangrijke keuze hier is om de IMBOR identifier (lees: `IMBORGUID`) te laten declareren in de `imborVoc_Termen` tabel. Zodoende wordt deze tabel de single-source-of-truth binnen de Access database. 

Dit geldt _niet_ voor de koppeltabellen, daar wordt wel de `IMBORGUID` gedeclareerd.

</div>

Door de versimpeling in Access zouden er tabellen ontstaan die niets meer zouden bevatten (omdat GUID, Label, Definitie, Synoniem en Toelichting in `imborVoc_Termen` zijn opgenomen) zijn deze tabellen weggelaten. Het gaat om:
1. `imborKern_Multipliciteit`
2. `imborKern_Eenheden`
3. `imborKern_TypeAttributen`
4. `imborKern_Datatypen`
5. `imborKern_Vakdisciplines`
6. `imborKern_SemantischeRelaties`
7. `imborKern_Objecttypen`
8. `imborKern_EnumeratieTypen`

In het diagram van het fysieke datamodel wordt dit ook aangegeven door de groene tekst van een datatype. Hier staat de theoretische tabel waar de waarde vandaan zou moeten komen. Echter in de Access database is dit versimpeld door deze op te halen uit `imborVoc_Termen`.

#### Begrippenkader

Alle tabellen die invulling geven aan de vocabulaire.
##### imborVoc_Termen

Deze tabel is onderdeel van het begrippenkader van IMBOR kan gezien worden als de vocabulaire. Zoals eerder vermeld heeft deze binnen Access een speciale status omdat hier de `IMBORGUID` ook gedeclareerd wordt voor de meeste elementen. Bijna alle tabellen halen hier informatie op. De tabel geeft inrichting aan het Niveau 1 van MIM (Model van begrippen) en aan de SKOS taalbindingen uit de NEN2660. 
Speciaal geval is ook de kolom `KlasseType`. Deze is gekoppeld aan de `IMBORGUID`  zoals hiervoor vermeld. `KlasseType` geeft aan of een IMBOR concept geïnstanteerd kan worden (`Concreet`) of niet (`Abstract`). 

##### imborVoc_Collecties

De enige andere tabel in het begrippenkader naast `imborVoc_Termen`. Dit betreft een overzicht van de collecties waarin de termen ingedeeld zijn. 

#### Kernmodel

Alle tabellen die invulling geven aan het IMBOR kernmodel.
##### imborKern_Klassen

Klasse is een nieuw begrip vanaf IMBOR2022. Het kan gelijkgesteld worden aan het NEN2660-2 "Concept". Het is hiermee ook een supertype van bijvoorbeeld `Objecttype` en `InformatieObject`. 

De klassenstructuur is een polyhiërarchie. Dit betekent dat een child, meerdere parents kan hebben. Of in IMBOR termen gezegd: Een `Objecttype` of `Klasse` erft van meerdere `Klasse` attributen over. Dit is gedaan zodat we flexibeler om kunnen gaan bij welke klassen een `Objecttype` hoort en daarmee een `Objecttype` geen onnodige attributen krijgt. Er zullen een aantal `Klasse` 'disjoint' zijn, maar dat is nog niet expliciet opgenomen.

Er zijn `Klasse` die 1-op-1 overeenkomen met een `Objecttype`. Dit is intentioneel. Dit maakt verder geen verschil, want een `Objecttype` is technisch gezien ook een `Klasse`. Op deze manier is gerealiseerd dat er geen attributen aan een `Objecttype` hoefden worden gehangen. Omdat de naam `Objecttype` zo ingeburgerd is in de IMBOR terminologie moest deze vooralsnog wel gehandhaafd worden. 

In `imborKern_Klassen` komen o.a. "Objecttypen", "Klassen", "ObjecttypeOnderdelen" en "Informatieobjecten" voor. Dit lijkt vreemd, maar is correct omdat het technisch gezien allemaal `Klasse` zijn (ofwel: subtypen van `Klasse`)

We nemen `InformatieObject` op als `Klasse`, daarmee kunnen we concrete 'klassen' introduceren zoals `document` en `memo`. Deze zijn dan te instantiëren en te relateren (doormiddel van de relatie `isBeschrevenDoor`) aan `Objecttype`n. Hiermee kan de klasse `InformatieObject` ook gerelateerd worden aan de NEN2660-2.

<div class='advisement'>

De kolom "Volgorde" in `imborKern_Klassen` is een beheertechnische kolom voor de Access formulieren. Daarmee geen normatief onderdeel van IMBOR. Dit is in het diagram ook te zien door de grijze tekst. Er kan dus ook geconcludeerd worden dat de tabel in principe geen toegevoegd waarde heeft voor de IMBOR kern, deze tabel zou dan eigenlijk ook in het lijstje kunnen staan dat vermeld staat in [Tabelindeling](#tabelindeling). maar de kolom 'Volgorde' zorgt voor deze uitzondering. 

</div>


##### imborKern_Klassenindeling

In deze simpele tabel wordt de polyhiërarchie van de IMBOR top beschreven. Klassen kunnen meerdere parents hebben. Door middel van de parent-child relatie wordt overerving geregeld. Alle childs krijgen ook de attributen van hun parents. Daarmee geldt dat ook alle `Objecttype`en die onder de klassen hangen ook op dezelfde manier attributen overerven.  Deze tabel is eigenlijk de vastlegging van het predicaat `isSubType`. Hier staat dus ook tot welke klasse een `Klasse`  of `Objecttype` behoord en daarmee zijn eigenschappen (lees: attributen) overerft.
##### imborKern_KlassenChildParent

Dit is een hulptabel Deze tabel wordt automatisch gegenereerd middels een AccessDB module die zich baseert op `imborKern_Klassenindeling`. Het betreft een hulptabel waarin voor ieder `Objecttype` apart wordt achterhaald van welke `Klasse`n hij de attributen moet overerven. De `ChildID` = `Objecttype`, de `ParentID` = de `Klasse`. De formulieren in de AccessDB baseren zich hierop. 
##### imborKern_Attributen

Deze tabel bevat alle attributen die in IMBOR voorkomen, inclusief hun `TypeAttribuut` en hun `Datatype`. De attribuutsoorten en datatypen zijn ook versimpeld t.o.v. IMBOR2020-08. De datatype volgens nu het [[xmlschema11-1]]. 

De kolom `BovenliggendAttribuut` wordt gebruikt om aan te geven hoe de attributen zich tot elkaar hiërarchisch verhouden. Dit betreft een kolom die nodig is om de formulieren op te bouwen en is niet normatief nodig (grijs in diagram). 
##### imborKern_EnumeratiesDomeinwaarden

In deze tabel staan alle `EnumeratieType` binnen IMBOR, inclusief de relatie naar de `Domeinwaarde`. Het EnumeratieType en de Domeinwaarde worden één keer gedefinieerd in `imborVoc_Termen` en worden hier middels 1-op-N relaties aan elkaar gekoppeld. 

De kolom BovenliggendeWaarde wordt gebruikt om aan te geven hoe de domeinwaarden zich tot elkaar hiërarchisch verhouden. Dit betreft een hulpkolom die nodig is om de formulieren op te bouwen en is niet normatief nodig (grijs in diagram).
##### imborKern_K_KlasseAttributen

Dit betreft een koppeltabel waarin de attributen aan de klassen gekoppeld worden. Inclusief een indicatie in welke `Eenheid` dit attribuut vastgelegd kan worden.

Er komen o.a. `Objecttype`n, `Klassen`, `ObjecttypeOnderdelen` en `Informatieobject`en voor in de kolom `Klasse`. Dit lijkt vreemd, maar is correct omdat het technisch gezien allemaal `Klasse` zijn (ofwel: subtypen van `Klasse`)

Daarnaast wordt de kolom `Informatiemodel` gebruikt om aan te geven in welk extern model er voor heeft gezorgd dat het betreffende attribuut is opgenomen in IMBOR. Hier wordt op termijn als nodig een mapping voor gemaakt. Nu is het 'beheerinformatie'.

De kolom OAGBD wordt gebruikt voor het informatieve deel dat beschreven wordt in het [OAGBD addendum](#oagbd).

Als laatste staat hier ook welke waardelijst van toepassing is. Dit staat in `EnumeratieType`.
##### imborKern_K_VakdisciplinesObjecttypen

Met deze tabel wordt aangegeven binnen welke `Vakdiscipline` een `Objecttype` kan voorkomen. Het betreft hier groepering die ook niets meer dan dat is. Binnen IMBOR wordt deze voornamelijk gebruikt als zoekingang of als structurering om de hoeveelheid `Objecttype` makkelijker te kunnen inzien. 

##### imborKern_K_ObjecttypenSemantischeRelaties

De introductie van semantische relaties (betekenisvolle relaties) is samen met de introductie van de klassen de grootste wijziging t.o.v. IMBOR2020-08. Met deze introductie is een generieke manier gecreëerd om relaties tussen `Klasse` te beschrijven. In deze tabel zijn de relaties opgenomen die normerend zijn binnen de IMBOR ontologie (inclusief hun multipliciteit). De relaties zelf ontlenen hun semantiek aan de NEN2660-2. 

<div class='advisement'>
Deze lijst is voorschrijvend, maar niet limitatief. In de implementatie mag een gebruiker zelf kiezen welke relaties er tussen de verschillende klassen aangegeven mag worden. Als er een relatie ontbreekt kan deze in de eigen implementatie gewoon gelegd worden. Uiteraard wil de IMBOR beheercommissie graag op de hoogte gehouden worden van deze inzichten.
</div>

#### Referentiemodellen

Omdat de referentiemodellen een informatief onderdeel van IMBOR zijn, worden deze beschreven in een [apart sectie](#referentiemodellen-in-ms-access). 

### IMBOR in LinkedData

Naast de distributie in de relationele tabellen van Acces wordt ook een LinkedData variant aangeboden. Deze is gebaseerd op hetzelfde logische model als de Access versie. Omdat vooralsnog de Access database tevens als beheeromgeving voor IMBOR wordt gebruikt is de LinkedData versie een transformatie van de tabellen. De LinkedData versie wordt via een transformatie getrokken uit de beheeromgeving. In de transformatie wordt de data getransformeerd naar het onderstaande fysieke datamodel. 

<figure>

![IMBOR fysiek datamodel LD](img/Modulaire%20opzet%20IMBOR-Fysiek%20Datamodel%20LD.drawio.png?raw=true)
    
<figcaption>IMBOR fysiek datamodel in LinkedData -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption>
</figure>

#### Ontologie indeling (in grafen)

Ook de LinkedData versie van IMBOR (IMBOR-LD) is volgt de modulaire indeling. In IMBOR-LD wordt dit met verschillen grafen (gerepresenteerd via prefixen) vastgelegd.
- `imbor-term:*` zijn de concepten die het begrippenkader (of vocabulaire) van IMBOR beschrijven.
- `imbor:*` zijn de concepten die de (normatieve) elementen binnen de IMBOR ontologie beschrijven (dit staat gelijk aan de 'imborKern').
- `imbor-domeinwaarde:*` zijn alle domeinwaarden binnen IMBOR (dit zijn instanties). Deze staan in een aparte graaf vanwege de overzichtelijkheid.
- `imbor-refmodels:*` zijn de concepten waarin externe ontologien aangehaald worden. Hier staan de benodigde gegevens om relaties naar toe te kunnen leggen.

Omdat IMBOR een extensie is van de NEN2660-2 is de IMBOR kern direct 'gesubclassed' aan de NEN2660-2 concepten. Vandaar dat de concepten die we gebruiken uit de NEN2660-2 afgebeeld zijn met de prefix `nen2660:*`. 

<div class='note'>
In de NEN2660-2 zit een kleine inconsistentie met GeoSPARQL. Er wordt namelijk niet verteld hoe deze toegepast moet worden. Om dit praktisch op te lossen wordt in de IMBOR Kern gesteld dat: `nen2660:hasBoundary rdfs:subPropertyOf geo:hasGeometry`. Dit kan gezien worden als een verduidelijking van de NEN2660 voor de IMBOR context.
</div>

#### Begrippenkader

Dit zijn alle classes (concepten) die tezamen het vocabulaire vormen (e.g. de thesaurus).
##### imbor-term:Term

Op deze class worden alle attributen vastgelegd die het concept (conceptueel) definiëren in tekstuele zin en vormt daarmee de basis voor het vocabulaire.
##### imbor-term:Collectie

Deze class bevat alle collecties waarin de termen kunnen worden ingedeeld.
#### NEN2660

Dit zijn alle classes uit de NEN2660-2 waaraan wij ons committeren. De basis betreft het `nen2660:DiscreteObject` (buiten de NEN2660-2 wordt dit ook wel als een 'Fysieke Object' gezien) en de `nen2660:SpatialRegion` (ook wel het 'Ruimtelijk Gebied'). Daarnaast betrekken we het `nen2660:InformationObject` om beschrijvingen toe te voegen en `nen2660:Activity` om functies te kunnen definiëren. 
##### nen2660:DiscreteObject

Gedefinieerd als: "A real object consisting of a contiguous amount of form-retaining matter, held together primarily by internal forces (gravity, electromagnetic force)"
##### nen2660:SpatialRegion

Gedefinieerd als: "A physical object that encloses a certain area such as rooms, roads and rivers that is bound by real objects, other spatial regions or based on use or convention and that is empty or contains discrete or liquid or gaseous matter"
##### nen2660:InformationObject

Gedefinieerd als: "Thing that is a whole of information on itself and has an own identity"
##### nen2660:GeometricEntity

Gedefinieerd als:  "A spatial representation"
##### nen2660:EnumerationType

Gedefinieerd als: "A type having a fixed or extendable set of simple instances having no further attributes or relations"
##### nen2660:Activity

Gedefinieerd als: "An activity is something possibly or actually happening in space and time"
##### nen2660:Matter

Gedefinieerd als: "A pure chemical substance, chemical bonding or mixture from which real objects are made"
#### Kernmodel

Het IMBOR kernmodel bevat niet veel meer dan 'Objecten', 'Attributen' en 'Domeinwaarden'. Dit wordt nog aangevuld met de `Vakdisciplines'. Het kernmodel is uitgevoerd in [[rdf-schema]] en [[shacl]]. Dit is volgens de taalbinding van de NEN2660-2 gedaan. Hieronder worden de onderdelen beschreven. 

##### imbor:Klasse

Deze class betreft alle Klassen, `InformatieObject`en en `Objecttype`en die IMBOR bevat. Met het attribuut `dash:abstract` wordt aangegeven of iets abstract (`true`) of concreet (`false`) is. Waarbij met concreet bedoeld wordt dat er in een beheersysteem of bij uitwisseling ook daadwerkelijk instanties van gemaakt zullen worden. Abstracte classes zullen voor eindgebruik niet heel belangrijk zijn en voor de meeste eindgebruikers ook niet zichtbaar zijn. De class heeft verder twee belangrijke relaties naar NEN2660 concepten. Dit betreffen `nen2660:isDescribedBy` die naar het `nen2660:InformationObject` loopt en `nen2660:hasBoundary` die naar de `nen2660:GeometricEntity` loopt. Met de eerste wordt dus aangegeven dat 'meer informatie over het de `imbor:Klasse` te vinden is bij het het `InformatieObject`. Met de tweede wordt aangegeven dat de (concrete) `imbor:Klasse` gebonden is door een geometrie. Ofwel, er kan een geometrie van vastgelegd worden. 
##### imbor:KlasseAttribuut

Deze class (die middels `sh:property` aan de `imbor:Klasse` hangt) is eigenlijk de koppeling tussen het 'Object' en het 'Attribuut'. Dit is een zogenaamde 'SHACL PropertyShape' en definieert dus welke attributen van toepassing zijn bij welk Objecttype en legt daar zaken over vast zoals: maximale kardinaliteit, in welke unit dit uitgedrukt moet worden van welke datatype het betreft. Er zijn in het schema twee beschrijvingen van `imbor:KlasseAttribuut` te zien. Dit komt omdat de property-shapes anders in elkaar zitten wanneer het een voorgedefinieerd datatype betreft (iets uit de [[xmlschema11-1]] lijn), dan wanneer het een waardelijst is.
##### imbor:Attribuut

Middels `sh:path` wordt de `imbor:KlasseAttribuut` verbonden met de daadwerkelijke `imbor:Attribuut`. Dit kan gezien worden als de 'conventionele' declaratie van het IMBOR attribuut. 
##### imbor:EnumeratieType

De `imbor:KlasseAttribuut` wordt middels `sh:class` verbonden aan de `imbor:EnumeratieType`. Dit is een `nen2660:EnumerationType`. Deze lijst bevat eigenlijk 'instanties' van de daadwerkelijke domeinwaarden.
##### imbor-domeinwaarde:Domeinwaarde

Dit zijn de daadwerkelijke domeinwaarden die middels een `rdf:type` aan de ``imbor:EnumeratieType` gehangen worden. Deze worden (volgens MIM gebruik) in een aparte graaf geplaatst zodat de kern niet te groot wordt en omdat deze domeinwaarden vaker aan verandering onderhevig zijn.
##### imbor:Vakdiscipline

De instanties van deze class zijn de IMBOR Vakdisciplines. Deze declareren middels een `rdfs:member` welke ObjectTypen uit `imbor:Klasse` binnen een vakdiscipline vallen.
#### Referentiemodellen

Omdat de referentiemodellen een informatief onderdeel van IMBOR zijn, worden deze beschreven in een [apart sectie](#referentiemodellen-in-linkeddata). 

#### Aanvullend 'metamodel'

Een aantal metaconcepten worden specifiek voor IMBOR gedefinieerd. Dit wordt gedaan middels het 'IMBOR Aanvullend Metamodel'. Dit betreft een kleine ontologie van beschrijfende concepten die er voor zorgen dat alle IMBOR specifieke properties netjes en navolgbaar gedefinieerd zijn.

[mijncrow]: https://crowsso.b2clogin.com/crowsso.onmicrosoft.com/B2C_1A_signup_signin/oauth2/v2.0/authorize?client_id=e0b429f6-ef7f-4d0e-be5f-2711b5d4393f&redirect_uri=https://crow.nl/Truelime/AzureADAuthenticationHandler.ashx&response_type=code&scope=openid&response_mode=query&state=eyJSZXR1cm5VcmwiOiIvTWlqbkNST1cvSG9tZSIsIlNob3BwaW5nQ2FydCI6IjAwMDAwMDAwLTAwMDAtMDAwMC0wMDAwLTAwMDAwMDAwMDAwMCIsIklkIjoiODQwYzBlYmMtZjBmOC00YmE5LTg3YzAtZGEwYThiZGUxYmMwIiwiU2lnbk91dCI6ZmFsc2V9
