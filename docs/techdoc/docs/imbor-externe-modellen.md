## Relaties met andere modellen

IMBOR heeft relaties met andere modellen. IMBOR bevindt zich in een speelveld waar veel raakvlakken zijn met andere sectorstandaarden en nationale registraties. Deze relaties kunnen grofweg onderverdeeld worden in 'sterke' relaties en 'zwakke' relaties. 

### Modellen met sterke relatie

IMBOR heeft eigenlijk twee soorten sterke relaties met andere standaarden. Voor de [NEN2660-2:2022][nen2660:2022], [NEN3610:2022][nen3610:2022], het [MIM][11], [TOOI][15] en [[QUDT]] geldt dat IMBOR daadwerkelijk _gebruik maakt_ van deze standaarden om het eigen model op te bouwen. De andere soort sterke relatie betreffen _['alignments'](https://begrippen.crow.nl/ombk/nl/page/?uri=https%3A%2F%2Fdata.crow.nl%2Ftech-term%2Fterm%2FTT008)_. Deze alignments worden ontwikkeld volgens de principes beschreven in de whitepaper [Ontology Matching trough alignment and extension: a Best Practice](https://docs.crow.nl/ontology-alignment/whitepaper/). In de figuur hieronder wordt het huidige landschap betreffende alignements weergegeven. 

<figure>

![IMBOR_surroundings](img/IMBOR_surroundings.drawio.png)
<figcaption><figcaption>Het landschap van alignments vanuit IMBOR perspectief</figcaption></figcaption>
</figure>

Hieronder wordt per model de sterke relatie met IMBOR beschreven.

#### NEN2660-2

De [NEN2660-2:2022][nen2660:2022] vormt de belangrijkste leidraad voor IMBOR door twee belangrijke dingen te specificeren:
1. Een praktisch toplevelmodel waarin genoeg semantiek aangegeven wordt om IMBOR in uit te drukken
1. Een taalbinding (en daarmee de keuze voor) de LinkedData W3C standaarden. 
IMBOR maakt gebruik van deze twee keuzes en probeert daarom zo goed mogelijk aan te sluiten. In onderstaande figuur is ook te zien waar de [NEN2660-2:2022][nen2660:2022] zich op focust. IMBOR neemt plaats in de "M1: Informatie model" laag. 

<figure>

![NEN2660-2 scope](img/NEN2660-2_scope.png)
    
<figcaption><figcaption>NEN2660-2 scope in grijs grijze vlakken (bron: TNO)</figcaption></figcaption>
</figure>

In de sectie [IMBOR samenhang en hiërarchie](#imbor-samenhang-en-hierarchie) wordt de keuze en de interpretatie van het praktisch toplevelmodel toegelicht in detail. In de sectie [IMBOR in LinkedData](#imbor-in-linkeddata) wordt de toepassing van de LinkedData principes in detail toegelicht.

#### NEN3610

De [NEN3610:2022][nen3610:2022] is na de [NEN2660-2:2022][nen2660:2022] de belangrijkste leidraad voor IMBOR. Binnen de [NEN2660-2:2022][nen2660:2022] is reeds een relatie tussen de [NEN2660-2:2022][nen2660:2022] en de [NEN3610:2022][nen3610:2022] aangegeven. Het gaat hier alleen om een afstemming tussen de begrippenkaders. IMBOR heeft deze afstemming overgenomen in de [tophiërarchie](#imbor-top-hierarchie). Binnen IMBOR wordt daarmee zo veel mogelijk aangesloten op de semantiek van de [NEN3610:2022][nen3610:2022] (en daarmee de [NEN2660-2:2022][nen2660:2022]), maar wordt (nog) geen volledige sterke relatie met de rest van de norm [NEN3610:2022][nen3610:2022] beschreven. Er wordt zodoende ook niet beweerd dat er volledige compatibiliteit met de [NEN3610:2022][nen3610:2022] is (wel met de [NEN2660-2:2022][nen2660:2022]), maar dat puur de begrippenkaders voor nu met elkaar afgestemd zijn. De [NEN3610:2022][nen3610:2022] hiërarchie wordt tevens gebruikt om de verdeling van attributen binnen IMBOR te regelen. Naast dit onderdeel worden ook worden de attributen `identificatie` en `domein` (als verplicht vanuit de [NEN3610:2022][nen3610:2022]) volledige toegepast in IMBOR als identificerende attributen.
Vanaf IMBOR2025 is ook het Temporele Model en het Netwerk Model wat in [NEN3610:2022][nen3610:2022] beschreven wordt toegepast. 

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="997"><span></span></div>
  <div class="issue" data-number="1075"><span></span></div>
</details>

#### MIM

Het Metamodel Informatie Modellering ([MIM][11]) is een gemeenschappelijk vertrekpunt voor het maken van informatiemodellen. Het model bevat duidelijke afspraken over het vastleggen van gegevensspecificaties en biedt tegelijkertijd ruimte aan de verschillende niveaus van modellering. Het MIM is in 2020 uitgekomen en vormt een belangrijke leidraad voor IMBOR2022 ondanks dat er niet volledig aan alle facetten voldaan wordt. Twee belangrijke dingen passen we toe:
1. Het scheiden van soort informatiemodellen in niveaus. In deze context dus het onderscheid tussen het Begrippenkader en het Kernmodel. 
1. De inhoudelijke modellering van modelconcepten en de metagegevens ervan. Door IMBOR uit te drukken in het MIM is een standaard manier van vastleggen en uitleg geborgd. 

Het MIM gaat uit van een begrippenkader en een explicietere modellering van een informatiemodel. Binnen IMBOR is dit toegepast door alles één keer te definiëren in het IMBOR vocabulaire (die ook los te gebruiken is) en vervolgens relaties tussen objecten, tussen objecten en attributen, etc. te modelleren in een meer gedetailleerd logisch informatiemodel (kernmodel). Het kernmodel en het begrippenkader worden vervolgens gelinkt. Dit onderscheid is ook te zien in de fysieke datamodellen voor [Access](#imbor-in-ms-access) en [LinkedData](#imbor-in-linkeddata).

Het tweede hoofdprincipe van het MIM betreft het modelleren van het IMBOR binnen het metamodel dat het MIM specificeert. Dit is in detail te zien in de sectie [IMBOR in modellen](#imbor-in-modellen). Iedereen die het MIM kent kan zodoende lezen hoe het IMBOR gemodelleerd is. Tevens kunnen informatiemodellen die volgens het MIM worden gemodelleerd (bijvoorbeeld de SOR) makkelijker met elkaar vergeleken worden. 

De [RDF vertaling](https://docs.geostandaarden.nl/mim/mim/#metamodel-in-linked-data-ld) zoals gebruikt in het MIM wordt niet gebruikt. Mede omdat de MIM metaclasses binnen IMBOR de ontologie niet direct gebruikt worden, maar alleen in het metamodel. Er wordt bijvoorbeeld gesteld dat een `imbor:Objecttype` van de metaclass `mim:Objecttype` is, daardoor is de `imbor:Boom` (welke `rdf:type` is van `imbor:Objecttype`) wel (indirect) gerelateerd aan het MIM, maar geen voorkomen van. 

#### TOOI

[TOOI][15] staat voor "Thesauri en Ontologieën voor Overheidsinformatie". TOOI is een kennismodel. Het doel van dit kennismodel is het definiëren van een gemeenschappelijke taal waarmee data en metadata uitgedrukt kunnen worden, zodat overheidsinformatie beter vindbaar, toegankelijk, interoperabel en herbruikbaar (FAIR) wordt. IMBOR adopteert TOOI volledig waar dit kan. IMBOR zal de TOOI gaan gebruiken voor het standaardiseren van de klassen `Ministerie`, `Gemeente`, `Waterschap`, `Samenwerkingsorganisatie`, `Provincie` en `OverigeOverheidsorganisaties`. De URI's voor deze klassen worden overgenomen, (bijvoorbeeld `https://identifier.overheid.nl/tooi/def/ont/Gemeente` voor `Gemeente`) maar niet de registers voor gemeenten, provincies, etc. IMBOR-gebruikers kunnen instanties van de voorgenoemde klassen instantiëren en hiervoor de registers aanspreken, binnen het ['Register gemeenten'](https://standaarden.overheid.nl/tooi/waardelijsten/work?work_uri=https%3A%2F%2Fidentifier.overheid.nl%2Ftooi%2Fset%2Frwc_gemeenten_compleet) staat bijvoorbeeld: `https://identifier.overheid.nl/tooi/id/gemeente/gm0228` voor 'gemeente Ede' of `https://identifier.overheid.nl/tooi/id/oorg/oorg10004` voor Rijkswaterstaat. Deze bijbehorende URIs spelen dus een identificerende rol in de IMBOR-modellering, maar moet een IMBOR-toepassing zelf ophalen.

#### QUDT

Vanuit de NEN2660-2 wordt de [[QUDT]] ontologie aangewezen als de plek om alles rondom eenheden en grootheden vandaan te halen. Door hier naar te refereren i.p.v. iets nieuws te verzinnen wordt inspanning en verwarring bespaard. IMBOR tracht hier dan ook volledig bij aan te sluiten voor zover mogelijk. Tot IMBOR2022 werd een eigen lijst van grootheden en eenheden bijgehouden, maar sinds IMBOR2025 wordt [[QUDT]] gebruikt.

#### GWSW

De relatie met GWSW is al lange tijd binnen IMBOR aanwezig. Riolering wordt als één van de belangrijke 'zuilen' binnen het beheer van de openbare ruimte gezien. Vandaar dat er ook al vele gesprekken tussen Stichting Rioned en CROW geweest zijn om deze twee sectorstandaarden zo nauw mogelijk op elkaar aan te laten sluiten. GWSW is vanaf het begin al gedistribueerd volgens de LinkedData principes. IMBOR is dit pas vanaf 2021, vandaar dat de relatie altijd relatief impliciet is geweest. Sinds 2021 is de NEN2660-2 beschikbaar, juist om de samenhang tussen zulke standaarden meer te stroomlijnen. Vanaf IMBOR2025 is IMBOR Riolering vervangen door IMBOR Stedelijk Water. Dit onderdeel wordt geheel ingevuld vanuit het GWSW. 

Binnen GWSW worden objecttypen, attributen en relaties beschreven die gaan over zowel statische als dynamische gegevens. Met statische gegevens worden gegevens bedoeld die relatief weinig veranderen en vaak voor meer doeleinden nodig zijn dan alleen beheer van de riolering. Onder dynamische gegevens worden dan ook meer de gegevens verstaan die regelmatig worden verzameld voor het assetmanagement (denk aan inspecties, metingen en uitgevoerde onderhoudsmaatregelen) en gegevens die daaruit worden berekend (denk aan planjaren, verwachte maatregelen en kostenramingen). Deze gegevens worden vaak in beheersystemen vastgelegd die voor rioolbeheer gemaakt zijn. IMBOR heeft een focus op alleen de vaste gegevens van objecten in de openbare ruimte. Vandaar dat er de relatie tussen IMBOR en GWSW zich alleen toelegt op de objecttypen, relaties en attributen die vaste gegevens beschrijven. Het deel van GWSW dat vaste gegevens beschrijft wordt nu door Rioned aangeleverd aan IMBOR onder de noemer IMBOR Stedelijk Water. Zodoende is er sterke semantische relatie (alignment) tussen GWSW en IMBOR gerealiseerd. 

De opname van GWSW in IMBOR is voor de vaste gegevens dus 100%. Voor het dynamische deel van GWSW blijft de GWSW ontologie nodig.

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1210"><span></span></div>
</details>

#### BGT/IMGeo

De relatie tussen [BGT/IMGeo][9] en IMBOR is altijd noodzakelijk geweest. IMBOR maakt gebruik van de IMGeo-objecten (en daarmee dus de 'verrijkte' BGT objecten). Binnen veel organisaties levert de BGT in veel gevallen de geometrie die in IMBOR wordt verrijkt met beheerinformatie. Er is echter wel sprake van een relatief gecompliceerde relatie. IMBOR is door de jaren heen meer als eigen ontologie ontwikkeld en BGT/IMGeo is niet doorontwikkeld. Momenteel bevat IMBOR dan ook veel meer informatie over het beheer van de openbare ruimte dan BGT/IMGeo rijk is. Omdat de uitwisseling tussen Geo en BOR applicaties binnen veel organisaties nodig blijft is besloten om tussen IMBOR en IMGeo een sterke alignment uit te brengen. Deze zal dan uiteraard BGT/IMGeo volledig dekken in IMBOR, maar andersom is dit dan niet haalbaar.

<div class='note'>
De BGT/IMGeo en IMBOR alignment moet nog officieel worden uitgebracht. 
</div>

<div class='note' title="Praktijkrichtlijn 2020">
In 2020 is door CROW en Geonovum samen een <a href="https://docs.geostandaarden.nl/imgeo/def-pr-IMGeo-20200318/" target=_blank>praktijkrichtlijn</a> uitgebracht. IMBOR2020-08 sluit aan op versie van IMGeo, 2.1.1. In IMGeo 2.1.1 ontbreken bepaalde subclassificaties van objecten die wel in IMBOR voorkomen. Om IMBOR-classificaties zonder gegevensverlies te kunnen uitwisselen tussen Geo- en BOR-afdeling binnen een organisatie middels het StUF-Geo BOR berichtenverkeer is deze werkafspraak/praktijkrichtlijn ‘Uitbreiding domeinwaarden en attributen’ ontwikkeld. De relatie tussen IMBOR en IMGeo is met deze praktijkrichtlijn helemaal uitgewerkt in een mapping tabel. In de praktijk wordt deze helaas niet of nauwelijks toegepast. Binnen IMBOR2022 is daarom op een iets hoger niveau een relatief sterke semantische relatie gelegd naar IMGeo2.2. Vanaf IMBOR2025 geldt deze praktijkrichtlijn niet meer.
</div>

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1241"><span></span></div>
  <div class="issue" data-number="1359"><span></span></div>
  <div class="issue" data-number="1169"><span></span></div>
</details>

#### KOR 

De [KOR 2023][16] (Kwaliteitscatalogus Openbare Ruimte) bevat zo'n 200 beeldmeetlatten voor het meten van de kwaliteit van de buitenruimte. Dit is een apart product van CROW, maar heeft een sterkte relatie met IMBOR. De KOR2023 heeft een officiële alignment met IMBOR. IMBOR en de KOR kunnen, met gebruikmaking van deze alignment, zodoende samen met elkaar gebruikt worden. De KOR wordt tevens als LinkedData gedistribueerd. 

<div class='note'>
De KOR en IMBOR alignment moet nog officieel worden uitgebracht. 
</div>

#### BOR-MELD

[BOR-MELD][7] is een CROW-standaard voor het vastleggen van meldingen over de openbare ruimte. De systematiek beschrijft welke informatie van een melding wordt vastgelegd, zowel het door de burger of bedrijf gemelde probleem (de ‘voorkant’ van de melding) als de achterliggende oorzaak en genomen actie (de ‘achterkant’ van de melding). De relatie met IMBOR is nagenoeg gelijk aan die van [KOR](#kor). De uniforme categorisering van typen meldingen over de openbare ruimte is altijd gerelateerd aan één of meerdere IMBOR-objecttypen. Ofwel, elk objecttype binnen BOR-MELD kent een alignment naar een objecttype van IMBOR. IMBOR en BOR-MELD kunnen zodoende samen met elkaar gebruikt worden. 

<div class='note'>
De BOR-MELD en IMBOR alignment moet nog officieel worden uitgebracht. 
</div>

#### Wegbeheersystematiek

De Wegbeheersystematiek 2019 is een CROW publicatie. De relatie tussen IMBOR2020-08 en de Wegbeheersystematiek 2019 is [uitvoerig beschreven][13]. Uiteindelijk is de bedoeling dat de terminologie van IMBOR volledig wordt overgenomen in de Wegbeheersystematiek middels een alignment. In 2025 wordt verkend of de Wegbeheersystematiek ook gedistribueerd kan worden als informatiemodel in LinkedData. Wanneer dit gebeurt zal de expliciete sterke semantische relatie onderdeel zijn van de publicatie.

<div class='note'>
De Wegbeheersystematiek en IMBOR alignment moet nog officieel worden uitgebracht. 
</div>

#### GWSL

GWSL moet het GWSW voor openbare verlichting worden, gebaseerd op het IMBOR framework (en dus de [NEN2660-2:2022][nen2660:2022]). GWSL bevat objecttypen, relaties en attributen die gaan over zowel statische als dynamische gegevens. Net zoals bij GWSW en IMWV bevat IMBOR zodoende alleen het deel betreffende de statische gegevens van GWSL. In de praktijk is de `Zoekingang` 'Verlichting' binnen IMBOR dus 1-op-1 gelijk aan het deel van GWSL dat over de vaste (statische) gegevens gaat (overigens is dat ook het enige GWSL wat tot en met 2021 gerealiseerd is). IMBOR en GWSL zijn beiden volledig op de [NEN2660-2:2022][nen2660:2022] gebaseerd en wanneer GWSL in een eerste versie gereed is zal het beheer ook door CROW gedaan worden.

### Andere gerelateerde modellen

Naast deze sterke relaties heeft IMBOR raakvlakken/relaties met veel meer modellen. Er is getracht om de relatie die er vanuit IMBOR erkend wordt zo goed mogelijk aan te geven. Dit omdat de gebruiker van IMBOR dan zelf deze kennis kan beoordelen, eventueel gebruiken of verbeteren. Hieronder worden de relatie met andere standaarden beschreven. Van een aantal standaarden zijn ook binnen de IMBOR distributies gegevens overgenomen of zijn de relaties expliciet (met zwakke semantiek) aangegeven als ['externe link lijsten'](#externe-link-lijsten). Dit wordt dan ook vermeld. 

<div class='advisement'>
Vanwege de positie van IMBOR worden er veel relaties naar andere standaarden gelegd. Binnen IMBOR zijn gegevens soms 'van toepassing verklaard' in IMBOR (gekopieerd) om de relatie tussen de twee te kunnen aangeven. Dit is wat CROW betreft een <i>tijdelijke</i> situatie. Wanneer meer standaarden in LinkedData uitgedrukt worden EN er standaarden zijn hoe modellen op elkaar 'gemapt' kunnen worden zullen we sterke semantische relaties gaan leggen. Dan worden de gekopieerde gegevens ook daadwerkelijk bij de bron onderhouden en refereert IMBOR er alleen maar naar. 
</div>

#### NEN2767-4

De NEN2767 en IMBOR hebben een lange historie. Veel gebruikers van IMBOR gebruiken ook de NEN2767-4 Conditiemeting infrastructuur. Er is in 2020 ook besloten dat de afstemming tussen de twee duidelijker gemaakt moet worden. Hiervoor is een gezamenlijk project gestart [door de NEN en CROW][3]. Hier zijn nog geen tastbare resultaten van. Tot nu toe is daarom in IMBOR een zwakke semantische relatie gelegd vanuit het IMBOR perspectief. Voor de IMBOR objecttypen waar een equivalent erkend wordt in de NEN2767-4 is dit aangegeven. De relatie tussen de IMBOR concepten en de NEN concepten is niet meer dan een 'bekijk ook' relatie die door CROW vanuit het IMBOR perspectief uitgewerkt is. Deze vastlegging is gedaan zodat bekeken kan worden hoe de NEN2767-4 is opgenomen in IMBOR en geeft een aanzet voor een vertaling tussen de twee standaarden. Deze aanzet kan door een softwareleverancier of organisatie worden overgenomen of uitgewerkt. 

<div class='note'>
De NEN2767-4 en IMBOR alignment moet nog officieel worden uitgebracht. 
</div>

#### NLCS

De Nederlandse CAD standaard (NLCS) is de CAD-standaard van de Nederlandse GWW-sector. Deze open standaard bevat afspraken voor het omgaan met metadata, digitaal tekenen, het uiterlijk van de tekening en vooral de bestandsopbouw van tekenwerk. IMBOR heeft vooralsnog geen directe relatie met de NLCS. De IMBOR objecten bevatten doorgaans geometrie. Deze geometrie kan ook uitgedrukt worden in de NLCS. Dit is echter geen onderdeel van IMBOR. 
In 2025 wordt binnen het DOOR-programma een verkenning gedaan om de relatie tussen IMBOR en NLCS sterker te maken.

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1361"><span></span></div>
  <div class="issue" data-number="1287"><span></span></div>
  <div class="issue" data-number="1286"><span></span></div>
  <div class="issue" data-number="1284"><span></span></div>
  <div class="issue" data-number="1283"><span></span></div>
</details>

#### SOR

De SOR was in IMBOR 2022 aanwezig, maar is inmiddels niet verder ontwikkeld. In IMBOR2025 heeft deze geen plek meer. 

#### IMKL

Het informatiemodel Kabels en Leidingen ([IMKL][8]) vormt een gemeenschappelijk begrippenkader voor gegevensuitwisseling voor werkzaamheden aan Kabels en Leidingen en gerelateerd grondverzet. Het IMKL is gebaseerd op NEN3610 en daarmee onderdeel van de NEN3610 familie. De relatie tussen IMKL en IMBOR is eenvoudig, maar noodzakelijk. Binnen IMBOR wordt het `InformatieObject` 'IMKL-informatie' onderscheiden. Een aantal `Klasse` en daarmee `Objecttype`n hebben relaties met dit `InformatieObject`. Hiermee worden diverse attributen die binnen IMKL noodzakelijk zijn geregistreerd binnen IMBOR. Op termijn kan er een sterke semantische relatie (mapping) tussen het IMKL en IMBOR gerealiseerd worden. De huidige vastlegging is gedaan zodat bekeken kan worden hoe IMKL informatie is opgenomen in IMBOR en geeft een aanzet voor een vertaling tussen de twee. Deze aanzet kan door een softwareleverancier of organisatie worden overgenomen of uitgewerkt. 

#### IMWV

Het [IMWV][4] is een afsprakenstelsel dat beschrijft hoe naast objectgerichte gegevens ook verkeersgegevens voor verkeerskundige vraagstukken op uniforme wijze kunnen worden vastgelegd. Het bevat een beschrijving van de fysieke objecten en statische gegevens die aan de fysieke objecten gekoppeld kunnen worden. Inhoudelijk is er dan ook een sterke relatie met IMBOR en het is zelfs ontwikkeld binnen de beheeromgeving van het IMBOR. Het IMWV bevat net als in het IMBOR geen beschrijvingen/afspraken van dynamische gegevens (zoals realtime verkeersgegevens, wachttijden, openingstijden van bruggen, verkeersongevallen, etc.) of gegevensbehoefte van verkeerskundige vraagstukken ten aanzien van bijvoorbeeld parkeren en verkeersmanagement. 

Vanaf IMBOR2025 is het IMWV buiten IMBOR geplaatst. Op termijn wordt bekeken wat er met IMWV en de relatie tot IMBOR gedaan moet worden.

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1357"><span></span></div>
</details>

#### Aquo/IMWA

De [Aquo-standaard][12] (Aquo) is de Nederlandse standaard voor het uitwisselen van gegevens binnen de watersector, beheert door het Informatiehuis Water. Een onderdeel is het Informatiemodel Water (IMWA). IMBOR heeft geen directe relatie met Aquo (of het IMWA). Wel is de content van IMBOR geïnspireerd door de begrippenlijst (Aquo-lex) van Aquo. De metastructuur van IMBOR en Aquo zijn gelijk, want beiden zijn gebaseerd op het MIM. 

#### BAG

De Basisregistratie Adressen en Gebouwen (BAG) bevat gegevens van alle adressen en gebouwen in Nederland, zoals bouwjaar, oppervlakte, gebruiksdoel en locatie op de kaart. De BAG is onderdeel van het overheidsstelsel van basisregistraties. IMBOR heeft geen directe relatie met de BAG. Wel is het BAG onderdeel 'Pand', direct overgenomen als een in IMBOR te gebruiken `Objecttype`. Hiermee is binnen een organisatie eventueel een relatie te realiseren. De metastructuur van IMBOR en de BAG zijn gelijk, want beiden zijn gebaseerd op het MIM. 

#### BRK/IMKAD

Het Informatiemodel Kadaster (IMKAD) is de basis voor de uitwisseling van Kadaster-gegevens. Het geeft inzicht in de kenmerken van de gegevens uit de Basisregistratie Kadaster (BRK) en de onderlinge samenhang ervan. IMBOR heeft geen directe relatie met BRK/IMKAD. Er zijn relaties te herkennen tussen perceelinformatie en beheerinformatie. Deze zijn echter geen onderdeel van het IMBOR. De metastructuur van IMBOR en IMKAD zijn gelijk, want beiden zijn gebaseerd op het MIM. 

#### BRO

De Basisregistratie Ondergrond (BRO) is een centrale registratie met publieke gegevens over de Nederlandse ondergrond. Het is onderdeel van het overheidsstelsel van basisregistraties. IMBOR heeft geen directie relatie met de BRO. Er zijn relaties te herkennen tussen de BRO 'Grondwatermonintoringsput' en de IMBOR 'Peilbuis'. Deze zijn echter geen onderdeel van het IMBOR. De metastructuur van IMBOR en BRO zijn gelijk, want beiden zijn gebaseerd op het MIM.

#### IMGeluid

Het informatiemodel Geluid (IMGeluid) beschrijft de semantiek van digitale bestanden voor de Centrale Voorziening Geluidsgegevens. IMBOR heeft geen directe relatie met het IMGeluid. Er zijn echter wel raakvlakken te benoemen die op termijn in lijn met elkaar gebracht moeten worden. Het gaat hierbij met name om de taxonomie van Asfaltverharding en de materie van het wegdek. De [lijst zoals beschreven bij IMGeluid][14] zou kunnen worden afstemt op gebruik binnen IMBOR. De metastructuur van IMBOR en IMGeluid zijn gelijk, want beiden zijn gebaseerd op het MIM.

#### IMNa

Het Informatiemodel Natuur (IMNa) is de standaard voor uniforme digitale uitwisseling van natuurgegevens. IMBOR heeft geen directie relatie met het IMNa. Er zijn relaties te herkennen tussen de indeling van de terreindelen in het buitengebied. Deze zijn echter geen onderdeel van het IMBOR. 

#### NWB

Het Nationaal Wegenbestand (NWB) is een open databestand met alle openbare wegen in Nederland die een straatnaam of wegnummer hebben en in beheer zijn bij het Rijk, provincies, gemeenten en waterschappen. IMBOR heeft geen directe relatie met het NWB. Er zijn relaties te herkennen tussen de de NWB 'Wegas' en de IMBOR 'Wegas'. Deze zijn echter geen onderdeel van het IMBOR.

#### WeginfraNL

WeginfraNL is een voortvloeisel uit o.a. de PIM-OTL (Pavement Information Modelling). Het uiteindelijke doel was om PIM-OTL door te ontwikkelen tot een nationale referentieontologie voor het domein weginfrastructuur, nu aangeduid als de ontologie
voor WeginfraNL. Dit is in opdracht gedaan van het 'Transitiepad Duurzame Wegverharding'. De eerste fase van de ontologie voor WeginfraNL omvat concepten, relaties en attributen voor het registreren, structureren en delen van bouw- en assetmanagementgegevens (As Built-fase) tussen stakeholders (opdrachtgevers en aannemers) in de weginfrastructuur en wegenbouw. WeginfraNL en IMBOR hebben nog geen directe relatie. Maar voor 2025 wordt verwacht dat een officiële alignment tussen de twee wordt uitgebracht. 

#### WIBON

De Wet informatie-uitwisseling bovengrondse en ondergrondse netten en netwerken (WIBON). Deze wet schrijft de wijze van informatie-uitwisseling tussen netbeheerders en grondroerders voor. IMBOR heeft geen directe relatie met WIBON. Gegevens uit IMBOR kunnen echter wel gebruikt worden om te voorzien in de wettelijke eisen voor bijvoorbeeld het aanleveren van netinformatie. Tevens leunt WIBON sterk op het [IMKL](#imkl). 

## Externe link lijsten

Op de GitHub pagina van IMBOR worden 'externe link lijsten` geplaatst. Dit betreffen lijsten met linkjes naar concepten uit andere ontologieën ([zie definitie](https://begrippen.crow.nl/ombk/nl/page/?uri=https%3A%2F%2Fdata.crow.nl%2Ftech-term%2Fterm%2FTT002)). Dit zijn informele handreikingen vanuit IMBOR die geen status hebben. Deze lijsten kunnen gebruikt worden als startpunt om per project of implementatie een mapping te maken vanuit IMBOR naar de andere ontologie. Tegenover deze informele handreikingen staan officiële alignments. Dit betreffen [sterke semantische relaties](#modellen-met-sterke-relatie) die beheert worden en waaruit automatische kennis kan worden afgeleid. Deze worden anders gedistribueerd. 

De lijsten zijn op deze [GitHub pagina](https://github.com/Stichting-CROW/imbor/tree/master/data/informele%20handreiking/externe%20link%20lijst) te downloaden.

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1350"><span></span></div>
</details>

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
[15]: https://standaarden.overheid.nl/tooi
[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667
[16]: https://www.crow.nl/kennisproducten/kwaliteitscatalogus-openbare-ruimte-2023/