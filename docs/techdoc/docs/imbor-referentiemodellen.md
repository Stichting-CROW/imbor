## Referentiemodellen

### Toelichting per referentiemodel

Binnen IMBOR zijn relaties opgenomen naar andere modellen. IMBOR bevindt zich in een speelveld waar veel raakvlakken zijn met andere sectorstandaarden en nationale registraties. Het betreft een onderdeel wat los staat van de 'normatieve' IMBOR onderdelen en mag gezien worden als een handreiking vanuit, en aan de IMBOR community. De exacte vorm van deze afhankelijkheden is nog niet formeel gemaakt. Ook binnen IMBOR2022 is nog geen formele 'mapping' gemaakt naar andere standaarden. Wel is getracht om de relatie die er vanuit IMBOR erkend wordt zo goed mogelijk aan te geven. Dit omdat de gebruiker van IMBOR dan zelf deze kennis kan beoordelen, eventueel gebruiken of verbeteren. Hieronder worden de relatie met andere standaarden beschreven. Van een aantal standaarden zijn ook binnen de IMBOR distributies gegevens overgenomen of zijn de relaties expliciet (met zwakke semantiek) aangegeven. Dit wordt dan ook vermeld. Hoe dit daadwerkelijk in de distributies zit is vermeld in deze sectie voor [IMBOR in Access](#referentiemodellen-in-ms-access) en [IMBOR-LD](#referentiemodellen-0).

<div class='advisement'>
Vanwege de positie van IMBOR worden er veel relaties naar andere standaarden gelegd. Binnen IMBOR zijn gegevens (bijvoorbeeld van GWSW) overgenomen in IMBOR (gekopieerd) om de relatie tussen de twee te kunnen aangeven. Dit is wat CROW betreft een <i>tijdelijke</i> situatie. Wanneer meer standaarden in LinkedData uitgedrukt worden EN er standaarden zijn hoe modellen op elkaar 'gemapt' kunnen worden zullen we sterke semantische relaties gaan leggen. Dan worden de gekopieerde gegevens ook daadwerkelijk bij de bron onderhouden en refereert IMBOR er alleen maar naar. 
</div>


#### NEN2660-2

De NEN2660-2 is in 2021 uitgekomen en vormt de belangrijkste leidraad voor IMBOR2022 door twee belangrijke dingen te specificeren:
1. Een praktisch toplevelmodel waarin genoeg semantiek aangegeven wordt om IMBOR in uit te drukken
1. Een taalbinding (en daarmee de keuze voor) de LinkedData W3C standaarden. 
IMBOR maakt gebruik van deze twee keuzes en probeert daarom zo goed mogelijk aan te sluiten. In onderstaande figuur is ook te zien waar de NEN2660-2 zich op focust. IMBOR neemt plaats in de "M1: Informatie model" laag. 

<figure>

![NEN2660-2 scope](img/NEN2660-2_scope.png)
    
<figcaption><figcaption>NEN2660-2 scope in grijs grijze vlakken (bron: TNO)</figcaption></figcaption>
</figure>

In de sectie [IMBOR samenhang en hiërarchie](#imbor-samenhang-en-hierarchie) wordt de keuze en de interpretatie van het praktisch toplevelmodel toegelicht in detail. In de sectie [IMBOR in LinkedData](#imbor-in-linkeddata) wordt de toepassing van de LinkedData principes in detail toegelicht. 

<div class='note'>
Er is nog geen definitieve versie van de nieuwe NEN2660 verschenen. Deze wordt in de loop van 2022 verwacht. Wanneer deze gepubliceerd wordt zal IMBOR zo goed als dat kan nog aangepast worden op deze principes. De verwachting is dat er weinig tot niets veranderd hoeft te worden. 
</div>

#### NEN3610

De NEN3610 is in 2021 herzien (t.o.v. 2011) en vormt de basis van de Samenhangende objecten registratie (SOR) die binnen het DiSGeo programma wordt opgetuigd. Binnen de NEN2660-2 is reeds een relatie tussen de NEN2660-2 en de NEN3610 aangegeven. Het gaat hier alleen om een afstemming tussen de begrippenkaders. IMBOR heeft deze afstemming overgenomen in de [tophiërarchie](#imbor-top-hierarchie). Binnen IMBOR wordt daarmee zo veel mogelijk aangesloten op de semantiek van de NEN3610 (en daarmee de NEN2660-2), maar wordt (nog) geen volledige sterke relatie met de rest van de norm NEN3610 beschreven. Er wordt zodoende ook niet beweerd dat er volledige compatibiliteit met de NEN3610 is (wel met de NEN2660-2), maar dat puur de begrippenkaders voor nu met elkaar afgestemd zijn. Dit is gedaan vanwege de te verwachten sterke relatie met de SOR die ongeveer hetzelfde doet. De NEN3610 hiërarchie wordt tevens gebruikt om de verdeling van attributen binnen IMBOR te regelen. 

<div class='note'>
Er is nog geen definitieve versie van de nieuwe NEN3610 verschenen. Deze wordt in de loop van 2021 verwacht. Wanneer deze gepubliceerd wordt zal IMBOR zo goed als dat kan nog aangepast worden op deze principes. De verwachting is dat er weinig tot niets veranderd hoeft te worden. 
De consultatie versie van de nieuwe NEN3610 is <a href="https://www.geonovum.nl/over-geonovum/actueel/nieuwe-versie-van-nen-3610-in-consultatieonsultatie">hier</a> te bekijken. 
</div>


#### MIM

Het Metamodel Informatie Modellering ([MIM][11]) is een gemeenschappelijk vertrekpunt voor het maken van informatiemodellen. Het model bevat duidelijke afspraken over het vastleggen van gegevensspecificaties en biedt tegelijkertijd ruimte aan de verschillende niveaus van modellering. Het MIM is in 2020 uitgekomen en vormt een belangrijke leidraad voor IMBOR2022 ondanks dat er niet volledig aan alle facetten voldaan wordt. Twee belangrijke dingen passen we toe:
1. Het scheiden van soort informatiemodellen in niveaus. In deze context dus het onderscheid tussen het Begrippenkader en het Kernmodel. 
1. De inhoudelijke modellering van modelconcepten en de metagegevens ervan. Door IMBOR uit te drukken in het MIM is een standaard manier van vastleggen en uitleg geborgd. 

Het MIM gaat uit van een begrippenkader en een explicietere modellering van een informatiemodel. Binnen IMBOR is dit toegepast door alles één keer te definiëren in het IMBOR vocabulaire (die ook los te gebruiken is) en vervolgens relaties tussen objecten, tussen objecten en attributen, etc. te modelleren in een meer gedetailleerd logisch informatiemodel (kernmodel). Het kernmodel en het begrippenkader worden vervolgens gelinkt. Dit onderscheid is ook te zien in de fysieke datamodellen voor [Access](#imbor-in-ms-access) en [LinkedData](#imbor-in-linkeddata).

Het tweede hoofdprincipe van het MIM betreft het modelleren van het IMBOR binnen het metamodel dat het MIM specificeert. Dit is in detail te zien in de sectie [IMBOR in modellen](#imbor-in-modellen). Iedereen die het MIM kent kan zodoende lezen hoe het IMBOR gemodelleerd is. Tevens kunnen informatiemodellen die volgens het MIM worden gemodelleerd (bijvoorbeeld de SOR) makkelijker met elkaar vergeleken worden. 

De [RDF vertaling](https://docs.geostandaarden.nl/mim/mim/#metamodel-in-linked-data-ld) zoals gebruikt in het MIM wordt niet gebruikt. Mede omdat de MIM metaclasses binnen IMBOR de ontologie niet direct gebruikt worden, maar alleen in het metamodel. Er wordt bijvoorbeeld gesteld dat een `imbor:Objecttype` van de metaclass `mim:Objecttype` is, daardoor is de `imbor:Boom` (welke `rdf:type` is van `imbor:Objecttype`) wel (indirect) gerelateerd aan het MIM, maar geen voorkomen van. 

#### GWSW

De relatie met GWSW is al lange tijd binnen IMBOR aanwezig. Riolering wordt als één van de belangrijke 'zuilen' binnen het beheer van de openbare ruimte gezien. Vandaar dat er ook al [vele gesprekken tussen Rioned en CROW][1] geweest zijn om deze twee sectorstandaarden zo nauw mogelijk op elkaar aan te laten sluiten. GWSW is vanaf het begin al gedistribueerd volgens de LinkedData principes. IMBOR is dit pas vanaf 2021, vandaar dat de relatie altijd relatief impliciet is geweest. Sinds 2021 is de NEN2660-2 beschikbaar, juist om de samenhang tussen zulke standaarden meer te stroomlijnen. Na september 2021 wordt verwacht dat ook GWSW de NEN2660-2 gaat toepassen (in navolging van IMBOR). Wanneer dit het geval is zullen Rioned en CROW trachten de standaarden op een zuivere manier exact op elkaar af te stemmen. Tot die tijd moet dit 'handmatig' gedaan worden. GWSW is dan ook één van de standaarden waar een relatie is opgenomen in de IMBOR distributies. 

##### GWSW als referentiemodel

Binnen GWSW worden objecttypen, attributen en relaties beschreven die gaan over zowel statische als dynamische gegevens. Met statische gegevens worden gegevens bedoeld die relatief weinig veranderen en vaak voor meer doeleinden nodig zijn dan alleen beheer van de riolering. Onder dynamische gegevens worden dan ook meer de gegevens verstaan die regelmatig worden verzameld voor het assetmanagement (denk aan inspecties, metingen en uitgevoerde onderhoudsmaatregelen) en gegevens die daaruit worden berekend (denk aan planjaren, verwachte maatregelen en kostenramingen). Deze gegevens worden vaak in beheersystemen vastgelegd die voor rioolbeheer gemaakt zijn. IMBOR heeft een focus op alleen de vaste gegevens van objecten in de openbare ruimte. Vandaar dat er de relatie tussen IMBOR en GWSW zich alleen toelegt op de objecttypen en attributen die vaste gegevens beschrijven. Het deel van GWSW dat vaste gegevens beschrijft is voor nu nog overgenomen in IMBOR(gekopieerd), maar dit moet in de toekomst een semantische relatie worden. De verwachting is dat in de loop van 2022 bij zowel IMBOR, GWSW en de sector voldoende inburgering van de LinkedData principes, de NEN2660-2 en de gedistribueerde vastlegging van informatiemodellen een feit is. Zodoende kan dan een sterke semantische relatie (mapping) tussen GWSW en IMBOR gerealiseerd worden, waardoor veel objecten van GWSW niet meer overgenomen hoeven te worden in IMBOR, maar dat er naar gelinkt wordt. In de tussentijd is dat nog niet het geval en is er dus sprake een 'kopie' van een deel van GWSW in IMBOR. De relatie tussen de IMBOR concepten en de GWSW concepten is nu niet meer dan een 'bekijk ook' relatie die door CROW vanuit het IMBOR perspectief uitgewerkt is. Deze vastlegging is gedaan zodat bekeken kan worden hoe GWSW is opgenomen in IMBOR en geeft een aanzet voor een vertaling tussen de twee standaarden. Deze aanzet kan door een softwareleverancier of organisatie worden overgenomen of uitgewerkt. 

#### NEN2767-4

De NEN2767 en IMBOR hebben ook een lange historie. Veel gebruikers van IMBOR gebruiken ook de NEN2767-4 Conditiemeting infrastructuur. Er is in 2020 ook besloten dat de afstemming tussen de twee duidelijker gemaakt moet worden. Hiervoor is een gezamenlijk project gestart [door de NEN en CROW][3]. Dit project is gestart, maar de resultaten hiervan worden in 2022 pas verwacht. Tot nu toe is daarom in IMBOR een zwakke semantische relatie gelegd vanuit het IMBOR perspectief. Voor de IMBOR objecttypen waar een equivalent erkend wordt in de NEN2767-4 is dit aangegeven.

##### NEN2767 als referentiemodel

Voor IMBOR objecttypen waar een NEN equivalent gezien wordt (zowel Beheerobject, Element als Bouwdeel) is dit aangegeven in IMBOR. Hiermee staat het NEN concept dus ook 'in' IMBOR. De verwachting is dat in de loop van 2022 bij het IMBOR en in de sector voldoende inburgering van de LinkedData principes, de NEN2660-2 en de gedistribueerde vastlegging van informatiemodellen een feit is. Als het ook lukt om de NEN2767-4 hierin door te ontwikkelen kan dan een sterke semantische relatie (mapping) tussen de NEN2767-4 en IMBOR gerealiseerd worden, waardoor veel objecten niet meer overgenomen hoeven te worden in IMBOR, maar dat er naar gelinkt wordt. In de tussentijd is dat nog niet het geval en is er dus sprake een 'kopie' van een deel van de NEN2767-4 in IMBOR. De relatie tussen de IMBOR concepten en de NEN concepten is niet meer dan een 'bekijk ook' relatie die door CROW vanuit het IMBOR perspectief uitgewerkt is. Deze vastlegging is gedaan zodat bekeken kan worden hoe de NEN2767-4 is opgenomen in IMBOR en geeft een aanzet voor een vertaling tussen de twee standaarden. Deze aanzet kan door een softwareleverancier of organisatie worden overgenomen of uitgewerkt. 

#### BGT/IMGeo

De relatie tussen BGT/[IMGeo][9] en IMBOR is altijd noodzakelijk geweest. IMBOR maakt gebruik van de IMGeo-objecten (en daarmee dus de 'verrijkte' BGT objecten). IMGeo levert de geometrie die in IMBOR wordt verrijkt met beheerinformatie. Er is echter wel sprake van een relatief gecompliceerde relatie. In 2020 is door CROW en Geonovum samen een [praktijkrichtlijn][10] uitgebracht. IMBOR2020-08 sluit aan op versie van IMGeo, 2.1.1. In IMGeo 2.1.1 ontbreken bepaalde subclassificaties van objecten die wel in IMBOR voorkomen. Om IMBOR-classificaties zonder gegevensverlies te kunnen uitwisselen tussen Geo- en BOR-afdeling binnen een organisatie middels het StUF-Geo BOR berichtenverkeer is deze werkafspraak/praktijkrichtlijn ‘Uitbreiding domeinwaarden en attributen’ ontwikkeld. De relatie tussen IMBOR en IMGeo is met deze praktijkrichtlijn helemaal uitgewerkt in een mapping tabel. In de praktijk wordt deze helaas niet of nauwelijks toegepast. Daarnaast is door de introductie van de SOR de toekomst van IMGeo helaas nog ongewis. Binnen IMBOR2022 is daarom op een iets hoger niveau een relatief sterke semantische relatie gelegd naar IMGeo2.2.

##### IMGeo als referentiemodel 

Binnen IMBOR is een 'mapping' opgenomen naar IMGeo die de 'uitdrukking in' semantiek kent. Hiermee is het mogelijk om IMBOR objecttypen vast te leggen met een IMGeo geometrie. De verwachting is dat in de loop van de tijd richting de ontwikkeling van de SOR bij zowel IMBOR, DisGeo en de sector voldoende inburgering van de LinkedData principes, de NEN2660-2 en de gedistribueerde vastlegging van informatiemodellen een feit is. Zodoende kan dan een sterke semantische relatie (mapping) tussen IMGeo (of de SOR) en IMBOR gerealiseerd worden. In de tussentijd is dat nog niet het geval en is er dus sprake een uitdrukking van IMBOR objecttypen in IMGeo geometrie. Deze vastlegging is gedaan zodat bekeken kan worden hoe IMGeo zich verhoudt tot IMBOR en geeft een aanzet voor een vertaling tussen de twee. Deze aanzet kan door een softwareleverancier of organisatie worden overgenomen of uitgewerkt. 

#### SOR

De SOR is een relatief nieuwe ontwikkeling die het landschap van standaarden en basisregistraties waarschijnlijk redelijk op zijn kop gaat zetten, hoewel de echte implicaties nog ongewis zijn. Binnen IMBOR is de verwachting dat IMBOR een 'uitklapmodel' van de SOR gaat worden. In objecttypen hiërarchie is daarom getracht om waar mogelijk de SOR begrippen te hanteren. Ook hier gaat het weer om het gebruik maken van het begrippenkader en nog niet persé de overig modelleerconstructies. Omdat de SOR praktisch een extensie van de NEN3610 is, is IMBOR voor zover mogelijk in lijn met de consultatieversie van de SOR gemaakt. Er is geen expliciete relatie gelegd. 

<div class='note'>
Er is nog geen definitieve versie van de SOR verschenen. Er is begin 2021 een <a href="https://www.geobasisregistraties.nl/basisregistraties/doorontwikkeling-in-samenhang/objectenregistratie">tweede consultatie</a> gedaan. De verwachting is dat de SOR nog wel een tijdje op zich laat wachten en dat de huidige registraties tot die tijd gewoon blijven gelden. IMBOR zal t.z.t. zich waar nodig aanpassen om aan te sluiten. 
</div>

#### IMKL

Het informatiemodel Kabels en Leidingen ([IMKL][8]) vormt een gemeenschappelijk begrippenkader voor gegevensuitwisseling voor werkzaamheden aan Kabels en Leidingen en gerelateerd grondverzet. Het IMKL is gebaseerd op NEN3610 en daarmee onderdeel van de NEN3610 familie. De relatie tussen IMKL en IMBOR is eenvoudig, maar noodzakelijk. Binnen IMBOR wordt de `Klasse` 'IMKLBasisObject' onderscheiden. Een aantal `Klasse` en daarmee `Objecttype`n zijn specialisaties van deze IMKL klasse. Daarmee worden diverse attributen die binnen IMKL noodzakelijk zijn geregistreerd binnen IMBOR. De verwachting is dat in de loop van 2022 bij zowel IMBOR, Geonovum en de sector voldoende inburgering van de LinkedData principes, de NEN2660-2 en de gedistribueerde vastlegging van informatiemodellen een feit is. Zodoende kan dan een sterke semantische relatie (mapping) tussen het IMKL en IMBOR gerealiseerd worden. De huidige vastlegging is gedaan zodat bekeken kan worden hoe IMKL informatie is opgenomen in IMBOR en geeft een aanzet voor een vertaling tussen de twee. Deze aanzet kan door een softwareleverancier of organisatie worden overgenomen of uitgewerkt. 

##### IMKL als referentiemodel

Binnen IMBOR is een 'mapping' opgenomen naar IMKL die de 'uitdrukking in' semantiek kent. Hiermee is het mogelijk om IMBOR objecttypen te vergelijken met de belangrijkste IMKL featuretypes. De verwachting is dat in de loop van de tijd  de ontwikkeling bij zowel IMBOR, IMKL en de sector voldoende inburgering van de LinkedData principes, de NEN2660-2 en de gedistribueerde vastlegging van informatiemodellen een feit is. Zodoende kan dan een sterke semantische relatie (mapping) tussen IMKL en IMBOR gerealiseerd worden. In de tussentijd is dat nog niet het geval en is er dus sprake van een zwakke semantische relaties. Deze vastlegging is gedaan zodat bekeken kan worden hoe IMKL zich verhoudt tot IMBOR en geeft een aanzet voor een vertaling tussen de twee. Deze aanzet kan door een softwareleverancier of organisatie worden overgenomen of uitgewerkt. 

#### IMWV

Het [IMWV][4] is een afsprakenstelsel dat beschrijft hoe naast objectgerichte gegevens ook verkeersgegevens voor verkeerskundige vraagstukken op uniforme wijze kunnen worden vastgelegd. Het bevat een beschrijving van de fysieke objecten en statische gegevens die aan de fysieke objecten gekoppeld kunnen worden. Inhoudelijk is er dan ook een sterke relatie met IMBOR en het is zelfs ontwikkeld binnen de beheeromgeving van het IMBOR. Het IMWV bevat net als in het IMBOR geen beschrijvingen/afspraken van dynamische gegevens (zoals realtime verkeersgegevens, wachttijden, openingstijden van bruggen, verkeersongevallen, etc.) of gegevensbehoefte van verkeerskundige vraagstukken ten aanzien van bijvoorbeeld parkeren en verkeersmanagement. In de praktijk komt het er op neer dat de `Vakdiscipline` 'Verkeer' binnen IMBOR 1-op-1 het IMWV is. De kritische lezer zal zien dat er toch een aantal dynamische gegevens (vanuit het IMWV) in IMBOR zitten (bijvoorbeeld over verkeersintensiteit). Dit is gedaan omdat er geen andere plaats van registratie is. De verwachting is dat in de loop van 2022 bij zowel IMBOR, IMWV en de sector voldoende inburgering van de LinkedData principes, de NEN2660-2 en de gedistribueerde vastlegging van informatiemodellen een feit is. Zodoende kan dan een sterke semantische relatie (mapping) tussen IMWV en IMBOR gerealiseerd worden waardoor er naar gelinkt wordt. In de tussentijd is dat nog niet het geval en is er dus sprake van een aantal attributen die formeel niet binnen de scope van IMBOR passen.  

#### KOR 

De KOR 2018 (Kwaliteitscatalogus Openbare Ruimte) bevat zo'n 200 beeldmeetlatten voor het meten van de kwaliteit van de buitenruimte. Dit is een apart product van CROW, maar heeft een sterkte relatie met IMBOR. Elke beeldmeetlat is gerelateerd aan één of meerdere IMBOR objecttypen. Ofwel, elk objecttype binnen de KOR kent een equivalent binnen IMBOR. IMBOR en de KOR kunnen zodoende samen met elkaar gebruikt worden. 

<div class='note'>
De KOR is in 2018 opnieuw uitgebracht. In 2021 wordt verkend of de KOR ook gedistribueerd kan worden als informatiemodel in LinkedData. Wanneer dit gebeurt zal de expliciete sterke semantische relatie onderdeel zijn van de publicatie.
</div>

#### BOR-MELD

[BOR-MELD][7] is een CROW-standaard voor het vastleggen van meldingen over de openbare ruimte. De systematiek beschrijft welke informatie van een melding wordt vastgelegd, zowel het door de burger of bedrijf gemelde probleem (de ‘voorkant’ van de melding) als de achterliggende oorzaak en genomen actie (de ‘achterkant’ van de melding). De relatie met IMBOR is nagenoeg gelijk aan die van [KOR](#kor). De uniforme categorisering van typen meldingen over de openbare ruimte is altijd gerelateerd aan één of meerdere IMBOR-objecttypen. Ofwel, elk objecttype binnen BOR-MELD kent een equivalent binnen IMBOR. IMBOR en BOR-MELD kunnen zodoende samen met elkaar gebruikt worden. 

<div class='note'>
In 2021 wordt verkend of de BOR-MELD ook gedistribueerd kan worden als informatiemodel in LinkedData. Wanneer dit gebeurt zal de expliciete sterke semantische relatie onderdeel zijn van de publicatie.
</div>

#### QUDT

Vanuit de NEN2660-2 wordt de [[QUDT]] ontologie aangewezen als de plek om alles rondom eenheden en grootheden vandaan te halen. Door hier naar te refereren i.p.v. iets nieuws te verzinnen wordt inspanning en verwarring bespaard. IMBOR tracht hier dan ook volledig bij aan te sluiten voor zover mogelijk. Omdat de QUDT in LinkedData vorm kent en IMBOR meerdere distributievormen kent, is er een tussenstap middels een referentiemodel. IMBOR houdt een eigen lijst van grootheden en eenheden bij, maar middels een referentiemodel wordt de semantisch sterke mapping vastgelegd. De LinkeData distributie van IMBOR is zodoende in lijn met hoe het gebruik van de QUDT ontologie in de NEN2660-2 bedoelt wordt. 

##### QUDT als referentiemodel

Binnen IMBOR wordt geregistreerd hoe de IMBOR `Eenheid` uitgedrukt worden in QUDT specificaties. Hiermee wordt de mogelijkheid geboden om, wanneer er in LinkedData gewerkt wordt, de QUDT ontologie te gebruiken.  

#### GWSL

GWSL moet het GWSW voor openbare verlichting worden, gebaseerd op het IMBOR framework (en dus de NEN2660-2). GWSL bevat objecttypen, relaties en attributen die gaan over zowel statische als dynamische gegevens. Net zoals bij GWSW en IMWV bevat IMBOR zodoende alleen het deel betreffende de statische gegevens van GWSL. In de praktijk is de `Vakdiscipline` 'Verlichting' binnen IMBOR dus 1-op-1 gelijk aan het deel van GWSL dat over de vaste (statische) gegevens gaat (overigens is dat ook het enige GWSL wat tot en met 2021 gerealiseerd is). IMBOR en GWSL zijn beiden volledig op de NEN2660-2 gebaseerd en wanneer GWSL in een eerste versie gereed is zal het beheer ook door CROW gedaan worden. 

<div class='note'>
Er is nog geen definitieve versie van GWSL verschenen. Er is <a href="https://www.crow.nl/over-crow/nieuws/2021/juni/voortgang-ontwikkeling-gegevenswoordenboek-stedeli">in 2021 hard gewerkt</a> aan een eerste versie.
</div>

#### Aquo/IMWA

De [Aquo-standaard][12] (Aquo) is de Nederlandse standaard voor het uitwisselen van gegevens binnen de watersector, beheert door het Informatiehuis Water. Een onderdeel is het Informatiemodel Water (IMWA). IMBOR heeft geen directe relatie met Aquo (of het IMWA). Wel is de content van IMBOR geïnspireerd door de begrippenlijst (Aquo-lex) van Aquo. De metastructuur van IMBOR en Aquo zijn gelijk, want beiden zijn gebaseerd op het MIM. 

#### BAG

De Basisregistratie Adressen en Gebouwen (BAG) bevat gegevens van alle adressen en gebouwen in Nederland, zoals bouwjaar, oppervlakte, gebruiksdoel en locatie op de kaart. De BAG is onderdeel van het overheidsstelsel van basisregistraties. IMBOR heeft geen directe relatie met de BAG. Wel is het BAG onderdeel 'Pand', direct overgenomen als een in IMBOR te gebruiken `Objecttype`. Hiermee is binnen een organisatie eventueel een relatie te realiseren. De metastructuur van IMBOR en de BAG zijn gelijk, want beiden zijn gebaseerd op het MIM. 

#### BRK/IMKAD

Het Informatiemodel Kadaster (IMKAD) is de basis voor de uitwisseling van Kadaster-gegevens. Het geeft inzicht in de kenmerken van de gegevens uit de Basisregistratie Kadaster (BRK) en de onderlinge samenhang ervan. IMBOR heeft geen directe relatie met BRK/IMKAD. Er zijn relaties te herkennen tussen perceelinformatie en beheerinformatie. Deze zijn echter geen onderdeel van het IMBOR. De metastructuur van IMBOR en IMKAD zijn gelijk, want beiden zijn gebaseerd op het MIM. 

#### BRO

De Basisregistratie Ondergrond (BRO) is een centrale registratie met publieke gegevens over de Nederlandse ondergrond. Het is onderdeel van het overheidsstelsel van basisregistraties. IMBOR heeft geen directie relatie met de BRO. Er zijn relaties te herkennen tussen de BRO 'Grondwatermonintoringsput' en de IMBOR 'Peilbuis'. Deze zijn echter geen onderdeel van het IMBOR. De metastructuur van IMBOR en BRO zijn gelijk, want beiden zijn gebaseerd op het MIM.

#### CB-NL

In de huidige staat van de CB-NL is er nog geen relatie tussen IMBOR en de CB-NL. Er wordt in 2021 gewerkt aan een CB-NL2.0. Deze zal volledig gebaseerd zijn op de NEN2660-2 principes. Daarmee wordt het een stuk makkelijker om de relatie te leggen naar IMBOR. Deze zal echter pas op zijn vroegst in 2022 verkend worden.

#### IMGeluid

Het informatiemodel Geluid (IMGeluid) beschrijft de semantiek van digitale bestanden voor de Centrale Voorziening Geluidgegevens. IMBOR heeft geen directe relatie met het IMGeluid. Er zijn echter wel raakvlakken te benoemen die op termijn in lijn met elkaar gebracht moeten worden. Het gaat hierbij met name om de taxonomie van Asfaltverharding en de materie van het wegdek. De [lijst zoals beschreven bij IMGeluid][14] zou kunnen worden afstemt op gebruik binnen IMBOR. De metastructuur van IMBOR en IMGeluid zijn gelijk, want beiden zijn gebaseerd op het MIM.

#### IMNa

Het Informatiemodel Natuur (IMNa) is de standaard voor uniforme digitale uitwisseling van natuurgegevens. IMBOR heeft geen directie relatie met het IMNa. Er zijn relaties te herkennen tussen de indeling van de terreindelen in het buitengebied. Deze zijn echter geen onderdeel van het IMBOR. 

#### NLCS

De Nederlandse CAD standaard (NLCS) is de CAD-standaard van de Nederlandse GWW-sector. Deze open standaard bevat afspraken voor het omgaan met metadata, digitaal tekenen, het uiterlijk van de tekening en vooral de bestandsopbouw van tekenwerk. IMBOR heeft geen directe relatie met de NLCS. De IMBOR objecten bevatten doorgaans geometrie. Deze geometrie kan ook uitgedrukt worden in de NLCS. Dit is echter geen onderdeel van IMBOR.
#### NWB

Het Nationaal Wegenbestand (NWB) is een open databestand met alle openbare wegen in Nederland die een straatnaam of wegnummer hebben en in beheer zijn bij het Rijk, provincies, gemeenten en waterschappen. IMBOR heeft geen directe relatie met het NWB. Er zijn relaties te herkennen tussen de de NWB 'Wegas' en de IMBOR 'Wegas'. Deze zijn echter geen onderdeel van het IMBOR.
#### PIM

PIM staat voor Pavement Information Modelling en wordt het centraal bedrijfsinformatiesysteem voor opdrachtnemers in de asfaltverhardingenbranche. PIM en IMBOR hebben nog geen directe (expliciete) relatie maar er zijn verregaande gesprekken bezig om de twee standaarden af te stemmen. De afstemming zal met name gedaan worden op de verschillende objecttypen binnen IMBOR. Uiteindelijk is de bedoeling dat IMBOR een vastlegging van asfaltconstructies en verhardingen nastreeft waar de gegevens die benodigd zijn voor PIM direct aan te relateren zijn. De verwachting is dat in de loop van 2022 bij zowel IMBOR, PIM en de sector voldoende inburgering van de LinkedData principes, de NEN2660-2 en de gedistribueerde vastlegging van informatiemodellen een feit is. Zodoende kan dan een sterke semantische relatie (mapping) tussen PIM en IMBOR gerealiseerd worden.

#### Wegbeheersystematiek

De Wegbeheersystematiek 2019 is een CROW publicatie. De relatie tussen IMBOR2020-08 en de Wegbeheersystematiek 2019 is [uitvoerig beschreven][13]. Uiteindelijk is de bedoeling dat de terminologie van IMBOR volledig wordt overgenomen in de Wegbeheersystematiek. In 2022 wordt verkend of de Wegbeheersystematiek ook gedistribueerd kan worden als informatiemodel in LinkedData. Wanneer dit gebeurt zal de expliciete sterke semantische relatie onderdeel zijn van de publicatie.

#### WIBON

De Wet informatie-uitwisseling bovengrondse en ondergrondse netten en netwerken (WIBON). Deze wet schrijft de wijze van informatie-uitwisseling tussen netbeheerders en grondroerders voor. IMBOR heeft geen directe relatie met Wibon. Gegevens uit IMBOR kunnen echter wel gebruikt worden om te voorzien in de wettelijke eisen voor bijvoorbeeld het aanleveren van netinformatie. Tevens leunt WIBON sterk op het [IMKL](#imkl). 

## Referentiemodellen in MS Access

In de Access distributie staan de informatieve tabellen die de relaties naar andere modellen bevatten. 

<div class='note'>
De manier waarop er nu relaties gelegd worden naar externe modellen wordt nog onder de loep genomen. Dit geldt zowel voor de manier waarop dat nu vastligt (met de refModel tabellen), maar ook voor de semantiek van deze relatie. De huidige mapping wordt omgeschreven in de kolom `RelatieInformatie`. Dit verschilt per model, maar er is nergens sprake van een sterke semantiek. 

Het is de bedoeling om later in 2022 te kijken of er semantisch sterkere relaties gelegd kunnen worden naar de verschillende referentiemodellen. En daarmee ook een 'volwaardige' mapping te maken. Hier loopt de techniek vooralsnog voor op de governance. Zie voor meer informatie ook [Toelichting per referentiemodel](#toelichting-per-referentiemodel)
</div>

### Tabelindeling

Dit betreffen alle tabellen die externe modellen representeren. We nemen niet de onderlinge relaties tussen Objecttypen, Attributen en Domeinwaarden over zoals deze vastgelegd zijn in de referentiemodellen. We zorgen dat we alleen de concepten opnemen in onze registratie zodat we een verwijzing kunnen maken.

#### refModel_Informatiemodellen
Hier wordt de meta-informatie opgenomen van de informatiemodellen die we aanhalen in IMBOR.
#### refModel_Objecttypen
In deze tabel worden de 'objecttypen' uit de referentiemodellen opgenomen zodat er aan gerelateerd kan worden.
#### refModel_Attributen
In deze tabel worden de 'attributen' uit de referentiemodellen opgenomen zodat er aan gerelateerd kan worden.
#### refModel_Domeinwaarden
In deze tabel worden de 'domeinwaarden' uit de referentiemodellen opgenomen zodat er aan gerelateerd kan worden.
#### refModel_Mapping
In deze tabel wordt de daadwerkelijk relatie gelegd tussen dus combinaties van Objecttypen, Attributen en Domeinwaarden in IMBOR en de Objecttypen, Attributen en Domeinwaarden uit een referentiemodel.
#### refModel_MinimaleDatasets
Dit is een nieuwe toevoeging vanaf IMBOR2022 en is nog in bèta. Met een minimale datasets wordt aangegeven welke `objecttype - attribuut` combinaties relevant zijn voor een bepaald informatiemodel (doorgaans een 'Methodiek')

## Referentiemodellen in LinkedData

In de LinkedData distributie staan de informatieve concepten die de relaties naar andere modellen bevatten. Deze staan in een aparte graaf en zodoende dus apart van de Vocabulaire en Kern (ontologie)

<div class='note'>
De manier waarop er nu relaties gelegd worden naar externe modellen wordt nog onder de loep genomen. Dit geldt zowel voor de manier waarop dat nu vastligt (met de 'mapping' classes), maar ook voor de semantiek van deze relatie. De huidige mapping wordt omgeschreven in de property `skos:scopeNote`. Dit verschilt per model, maar er is nergens sprake van een sterke semantiek. 

Het is de bedoeling om later in 2022 te kijken of er semantisch sterkere relaties gelegd kunnen worden naar de verschillende referentiemodellen. En daarmee ook een 'volwaardige' mapping te maken. Hier loopt de techniek vooralsnog voor op de governance. Zie voor meer informatie ook [Toelichting per referentiemodel](#toelichting-per-referentiemodel)
</div>

### Class indeling

Dit betreffen alle Classes in het de graaf 'Addendum Referentiemodellen'. We nemen niet de onderlinge relaties tussen Objecttypen, Attributen en Domeinwaarden over zoals deze vastgelegd zijn in de referentiemodellen. We zorgen dat we alleen de concepten opnemen in onze registratie zodat we een verwijzing kunnen maken.

#### ref:Informatiemodel
Hier wordt de meta-informatie opgenomen van de informatiemodellen die we aanhalen in IMBOR. Elk model heeft een eigen `GUID`, `skos:prefLabel` en `skos:definition`. Daarnaast wordt op de `rdfs:seeAlso` property de URL vastgelegd naar de website van het informatiemodel, op `dct:publiser` de beheerder van het informatiemodel en op `schema:version` een tekstuele vastlegging van de versie van het informatiemodel. 

Het informatiemodel wordt door zowel IMBOR kern concepten als door concepten uit de addenda als bron gerefereert middels `dct:source`.
#### ref:RefMapping
Dit betreft de Class die de link is tussen de IMBOR ontologie en de referentiemodellen (ofwel het normatieve en informatieve deel). De class heeft ook een `GUID`. Daarnaast is er ruimte voor een toelichting op de mapping in `skos:note` en wordt de relatie informatie op de `skos:scopeNote` beschreven. 

Middels de property `imborObjectype` wordt de relatie naar het IMBOR Objecttype gelegd en middels de property `refObjecttype` wordt de relatie naar het Objecttype uit het referentiemodel gelegd. 

Omdat in dit geval het attribuut en de domeinwaarde altijd samen voorkomen worden deze gegroepeerd in een `blanknode`. Middels de properties `imborAttribuutDomeinwaarde` en `refAttribuutDomeinwaarde` wordt de relatie gelegd tussen de `Mapping` en de `blanknode`. Vanuit de `blanknode` wordt middels een `rdf:List` constructie naar de verschillende attributen en domeinwaarden verwezen. 
#### ref:RefObjecttype
Dit betreffen de 'ObjectTypen' die in de referentiemodellen onderscheiden worden. 
#### ref:RefAttribuut
Dit betreffen de 'Attributen' die in de referentiemodellen onderscheiden worden. 
#### ref:RefDomeinwaarde
Dit betreffen de 'Domeinwaarden' die in de referentiemodellen onderscheiden worden. 










[1]: https://www.crow.nl/thema-s/management-openbare-ruimte/imbor/de-relatie-tussen-imbor-en-gwsw
[2]: https://www.geobasisregistraties.nl/basisregistraties/doorontwikkeling-in-samenhang/objectenregistratie
[3]: https://www.nen.nl/nieuws/conditiemeting/eerste-stap-eenduidige-aansluiting-tussen-imbor-en-nen-2767-gezet/
[4]: https://www.crow.nl/thema-s/wegontwerp/imwv-informatiemodel-wegen-en-verkeer
[5]: https://www.crow.nl/over-crow/nieuws/2021/juni/voortgang-ontwikkeling-gegevenswoordenboek-stedeli
[6]: http://www.qudt.org/2.1/catalog/qudt-catalog.html
[7]: https://www.crow.nl/thema-s/management-openbare-ruimte/beeldkwaliteit/bor-meld
[8]: https://www.geonovum.nl/geo-standaarden/informatiemodellen-nen3610-familie/informatiemodel-kabels-en-leidingen-imkl
[9]: https://docs.geostandaarden.nl/imgeo/catalogus/imgeo/
[10]: https://docs.geostandaarden.nl/imgeo/def-pr-IMGeo-20200318/
[11]: https://docs.geostandaarden.nl/mim/mim/
[12]: https://www.aquo.nl/index.php/Hoofdpagina
[13]: https://www.crow.nl/getattachment/Thema-s/Wegbeheer-en-wegonderhoud/Wegbeheersystematiek/Keurmerk-beheersoftware-voor-wegbeheer/Afstemming-IMBOR-en-Wegbeheersystematiek-2019.pdf.aspx?lang=nl-NL
[14]: https://docs.geostandaarden.nl/cvgg/img/#detail_class_IMGeluidAlgemeen_Wegdektype