## Inleiding

Het IMBOR uniformeert begrippen en concepten voor het vakgebied ‘beheer openbare ruimte’. Zie ook [over IMBOR][1].

In 2021 is besloten om IMBOR grondig te herzien n.a.v. een aantal ontwikkelingen:
* IMBOR wordt in beheer genomen, i.p.v. in ontwikkeling te zijn
* Het beschikbaar komen van de [NEN2660-2:2022][nen2660:2022]
* Het beschikbaar komen van de herziende [NEN3610:2022][nen3610:2022]
* De vraag om LinkedData versies van sectorstandaarden
* De bredere adoptie van het [MIM][8]
* De adaptatie van het werken met ontologieën (vaak onder de noemer 'OTL-en' of 'Informatie modellen')
* De vraag om afstemming tussen standaarden (zoals [NLCS][6], [IMGEO][3], [GWSW][7], [GWSL][5] en [IMBOR-NEN2767-4][4])
* De wens om de beheeromgeving en beheerprocedures rondom IMBOR te concretiseren

Met werkgroepen is de inhoud medio 2020 voorlopig vastgesteld. Mede daarom is besloten om in 2021 een nieuwe release te doen die (minder) aanpassingen aan de inhoud heeft, maar vooral in modellering en structuur meer aansluiting vind bij de nieuwe standaarden en daardoor robuuster is. In de daaropvolgende versie is de inhoud waar nodig omgezet naar de nieuwe modellering en structuur.

Tot en met IMBOR2020-08 is zowel de publicatie van IMBOR en het beheer van de inhoud in Microsoft Access gedaan. Vanaf IMBOR2022 is een transitietraject ingegaan om IMBOR los te weken van de implementatie in Access. Hierdoor is IMBOR beschikbaar nu beschikbaar in zowel Access als in LinkedData. Het beheer van IMBOR wordt vooralsnog in Access gedaan, maar dit zal op termijn herzien worden.

### Normatief & informatief

Deze ReSpec is ingedeeld in secties. Alle secties zijn 'normatief' tenzij dit anders vermeld is door de zin: <i>"Dit onderdeel is niet normatief"</i>.

<div class='advisement'>
 Normatief wil in deze context zeggen dat de informatie onderdeel is van IMBOR en wanneer men zich 'committeert aan IMBOR' zich aan deze secties dient te houden. Sommige secties zijn zodoende informatief en mogen gezien worden als 'suggesties', 'aanvullingen' of 'best practices' vanuit IMBOR. Een organisatie kiest zelf dan ook of zij zich <i>ook</i> aan die sectie committeert.  
</div>

<figure>

![IMBOR Normatief & Informatief](img/IMBOR_info&normatief.drawio.png?raw=true)
    
<figcaption>IMBOR Normatief & Informatieve onderdelen</figcaption>
</figure>

### Toepassingsgebied

In het IMBOR zijn landelijke afspraken gemaakt over de objectgegevens voor het beheer van de openbare ruimte. Het is daarmee een belangrijk hulpmiddel dat beheerders ondersteunt bij de opzet en vulling van hun beheersystemen, bijvoorbeeld voor wegbeheer en groenbeheer. Hierdoor wordt integraal beheer van de openbare ruimte gemakkelijker en kunnen beheerder beter gegevens delen en hun data op orde houden.
* In het IMBOR staat alle informatie die nodig kan zijn voor het beheer vastgelegd bij objecttypen, hun onderlinge relaties en in hun attributen en bijbehorende domeinwaarden. Door gebruik van deze benamingen ontstaat uniformiteit in het vakgebied ‘beheer openbare ruimte’; dit bevordert de communicatie en uitwisseling van gegevens.
* De benamingen en indelingen zijn zoveel mogelijk afgestemd op de meest gebruikte standaarden, richtlijnen en normen voor het vakgebied openbare ruimte; het IMBOR zorgt er dus voordat deze eenvoudiger kunnen worden toegepast.

Met de IMBOR Vocabulaire is een 'taal' beschikbaar die gesproken kan worden in de BOR-(beheer openbare ruimte) sector. Deze kan in samenhang gebruikt worden met andere vocabulaires. Met de IMBOR Ontologie is een meer complete beschrijving van het model voor het beheer van de openbare ruimte beschikbaar. Hierin worden de informatiebehoeften beschreven, inclusief standaardisatie en de vastlegging daarvan voor gebruik in machines (computers). 

#### IMBOR (door)ontwikkeling in software

IMBOR is begonnen als verrijking van het BGT|IMGeo, als specifiek informatiemodel voor het BOR domein. Inmiddels is het geëvolueerd naar een op zich zelf staande vocabulaire en ontologie. De titel 'informatiemodel' begint dan ook steeds minder te passen. Met de vernieuwde [NEN2660-2:2022][nen2660:2022] is er een duidelijke lijn hoe informatie rondom de gebouwde omgeving kan worden vastgelegd en gedeeld.  In het kader van de [NEN2660-2:2022][nen2660:2022] is IMBOR dan ook 'gewoon' een ontologie. Vanuit CROW wordt dit ook zo benaderd. De keuze voor LinkedData heeft hier dan ook mee te maken. BGT|IMGeo (en zodoende ook het begin van IMBOR) zijn gemaakt om software op te bouwen. Het zijn modellen die beschrijven hoe de data moet worden vastgelegd om deze zonder informatieverlies te kunnen delen. Met de komst van LinkedData is deze vastlegging gestandaardiseerd op internationaal niveau. Er wordt met IMBOR dan ook een toekomst voorzien dat men geen software meer maakt voor het vastleggen van 'Boom' of 'Wegas', maar software maakt voor het vastleggen van klassen uit de [NEN2660-2:2022][nen2660:2022], zoals 'DiscreetObject' en 'RuimtelijkObject'. Zodoende kan er veel meer dynamisch omgesprongen worden met de ontologie en hoeft software niet zo vaak aangepast te worden, maar is de gebruiker van de software (de kennishouder) in staat om zijn assets op de juiste manier te 'classificeren'. 

>NOTE "Beoogd gebruik in software"
>Dit zegt ook iets over de beoogde implementatie van IMBOR in software pakketten. Vanuit IMBOR en CROW worden software leveranciers dan ook geadviseerd om zich in te stellen op de principes van de [NEN2660-2:2022][nen2660:2022]. Zodat zij hun software kunnen gaan 'vullen' met ontologiën zoals IMBOR en andere modellen die op de [NEN2660-2:2022][nen2660:2022] gebaseerd zijn of gaan worden. Het toepassen van IMBOR betekent dan dat de klassen in softwarepakket worden 'gevuld' met de IMBOR-ontologie. Dit betekent ook dat toekomstige wijzigingen in nieuwe versies van het IMBOR relatief eenvoudig kunnen worden 'geconfigureerd' en dat geen herprogrammaring nodig is

#### Regie op standaarden
Met de modellering van IMBOR op basis van de [NEN2660-2:2022][nen2660:2022] wordt het voor organisaties die standaarden proberen te ontwikkelen zoals Stichting CROW, Stichting RIONED en Geonovum ook gemakkelijker om hun standaarden op elkaar af te stemmen en aan elkaar te relateren zodat dit dan niet meer bij de software leveranciers of opdrachtgevers komt te liggen. Deze kunnen de standaarden dan beter in samenhang gebruiken. Om dit te laten werken moeten deze organisaties onderling afspreken om:
* hun ontologie te baseren op de [NEN2660-2:2022][nen2660:2022] en de [NEN3610:2022][nen3610:2022],
* de modellering waar mogelijk te beschrijven volgens het MIM,
* de relaties met andere standaarden wederzijds te beschrijven en continue te bewaken,
* de ontologie (ook) als LinkedData te publiceren, en
* zo veel mogelijk via dezelfde technieken te ontsluiten.
Dit vraagt zodoende niet alleen technische inspanning, maar zeker ook proces en organisatie afstemming. 

### Doelgroep

Dit document is bedoeld als 'technische documentatie' rondom IMBOR. Het is dan ook primair bestemd voor informatiearchitecten, gegevensbeheerders of softwareleveranciers die IMBOR willen toepassen en er implementaties van maken. Enige kennis van informatiemodellering is daarom benodigd. IMBOR richt zich in het bijzonder op de informatievoorziening binnen het (overheidsdomein) beheer van de openbare ruimte.

>Er worden door de IMBOR modelleurs ook modelleerregels gehanteerd. Deze kunnen ook handig zijn voor diegene die IMBOR gebruiken en/of implementeren. Dit levende document is te vinden bij de IMBOR documentatie onder de noemer: [IMBOR Modelleerregels][11].

[1]: https://www.crow.nl/Onderwerpen/Assetmanagement-en-beheer-openbare-ruimte/Data-en-informatie/imbor/
[2]: https://www.nen.nl/nieuws/normontwerp-informatiemodellering-van-gebouwde-omgeving-ter-commentaar/
[3]: https://www.geonovum.nl/geo-standaarden/bgt-imgeo
[4]: https://www.nen.nl/nieuws/conditiemeting/eerste-stap-eenduidige-aansluiting-tussen-imbor-en-nen-2767-gezet/
[5]: https://www.linkedin.com/pulse/start-ontwikkeling-gegevenswoordenboek-stedelijk-licht-verhoeven?trk=read_related_article-card_title
[6]: https://www.digigo.nu/standaarden/nlcs/
[7]: https://www.crow.nl/thema-s/management-openbare-ruimte/imbor/de-relatie-tussen-imbor-en-gwsw
[8]: https://www.geonovum.nl/geo-standaarden/metamodel-informatiemodellering-mim
[9]: https://www.nen.nl/elasticsearch/?search=2660-2&sortmode=asc&viewmode=list
[10]: https://www.nen.nl/nen-3610-2022-nl-296137
[11]: https://docs.crow.nl/imbor/modelleerregels
[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667