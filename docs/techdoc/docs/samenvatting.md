Deze pagina beschrijft de _technische documentatie_ rondom IMBOR. Het IMBOR uniformeert begrippen voor het vakgebied ‘beheer openbare ruimte’ en voorziet in een ontologie die geschikt is voor zowel mens en machine. 

IMBOR bestaat uit drie delen:
- IMBOR Vocabulaire is het begrippenkader van IMBOR. Het beschrijft de universe of discourse van beheer van de openbare ruimte. De vocabulaire is een invulling van het 'model van begrippen' zoals dat gehanteerd wordt in het MIM. Het is tevens de invulling van het 'Toepassingstype 1' vanuit de [NEN2660-2:2022][nen2660:2022] (afstemming van termen en definities). De uitdrukking is volledig in [[skos-primer]].
- IMBOR Kern, ofwel de ontologie is het daadwerkelijke informatiemodel. Het betreft hier het logische informatiemodel zoals MIM dat erkend. De [NEN2660-2:2022][nen2660:2022] is volledig toegepast en daarmee is het de invulling van het 'Toepassingstype 3 (gegevensintegratie en innovatie). Vandaar dat de LinkedData expressie ook met [[rdf-schema]] en [[shacl]] gedaan wordt. De relatie tussen de vocabulaire en de ontologie ligt middels een `rdfs:seeAlso` systematiek zoals de [NEN2660-2:2022][nen2660:2022] dat voorschrijft. Elke concept in de ontologie heeft zodoende een definiëring in de vocabulaire. 
- IMBOR addenda zijn _informatieve_ delen van IMBOR. In tegenstelling tot de voorgaande twee onderdelen kan elke organisaties deze van toepassing verklaren of niet. De addenda zijn (nog) niet in MIM uitgedrukt, wel in LinkedData maar op een minder strikte wijze dan de normatieve delen. 

IMBOR wordt gepositioneerd als sectormodel. De focus ligt op de _vaste gegevens_ van objecten die herkend worden voor het beheer van de openbare ruimte. Kijkend naar het landschap waarin IMBOR wordt gebruikt zijn er veel raakvlakken met landelijke, maar ook andere sectorale modellen. Om deze afstemming zo optimaal te laten verlopen is getracht om de top van de IMBOR hiërarchie (ofwel de klassenindeling) zo veel mogelijk aan te laten sluiten op andere modellen. 

IMBOR wordt op twee manieren gedistribueerd, te weten in een Access database en in LinkedData. Van beiden distributiewijze worden detail uitleg gegeven en verschillende schema's gepresenteerd.  

Zie ook de [CROW site over IMBOR](https://www.crow.nl/Onderwerpen/Assetmanagement-en-beheer-openbare-ruimte/Data-en-informatie/imbor/). 

[nen3610:2022]: https://www.nen.nl/nen-3610-2022-nl-296137
[nen2660:2022]: https://www.nen.nl/nen-2660-2-2022-nl-291667