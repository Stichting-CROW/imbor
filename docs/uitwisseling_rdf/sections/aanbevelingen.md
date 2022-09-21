## Best practice

In deze sectie wordt de “CROW Best practice - IMBOR-gegevens delen middels RDF” gedefinieerd. De onderstaande onderdelen hebben betrekking op IMBOR-gegevens die _buiten_ het areaalbeheerpakketpakket behandeld wordt. De uitgangspunten zijn de elementaire keuzes waardoor deze best practice aan te bevelen is.

### Uitgangspunten

1. De gegevens in de gegevensset worden middels [[rdf11-primer]] (lees: RDF) in triples opgeslagen.
    * De dataset is een [[owl2-primer]] `owl:Ontology` en importeert IMBOR-ontologie (met SHACL-shapes) middels `owl:imports`;
    * De serialisatie is arbitrair. Voorkeur heeft [[turtle]] of [[json-ld]].
1. Gegevens worden geclassificeerd naar de [IMBOR-ontologie][4], die een extensie is van de [NEN2660-2-ontologie][3].
    * Deze vormen daarmee het ‘gegevensmodel’;
    * Alle objecten zijn instanties van [concrete IMBOR klassen][5] (lees:`IMBOR-ObjectType`);
    * Middels [[SHACL]] [validatie][6] _kan_ de conformiteit gecheckt worden.
1. De geometrie wordt middels [[geosparql]] opgeslagen.
    * Er wordt gebruikt gemaakt van de [WKT serialisatie][7];
    * De [GML serialisatie][8] is complexer; en daarmee vooralsnog _niet_ nodig.
1. Qua URI strategie van de `Objecten` (instanties van `ObjectTypen`) in de gegevensset wordt de [NEN3610][1], i.c.m. de [[NEN2660_2]] gevolgd.
    * In dit geval betekent dit: `{domein}/id/{identificatie}`;
    * `/id/` geeft aan dat het een 'individu' betreft;
    * Waarbij `{domein}` een correcte HTTP(S) URI moet zijn.

In de volgende secties worden hierop toelichting en voorbeelden gegeven en achtergrondinformatie uiteengezet. 

### Overwegingen

Bij het ontwikkelen en testen van deze best practice zijn er een aantal keuzes gemaakt. De belangrijkste overwegingen worden in de volgende sectie toegelicht.

#### Hergebruik van standaarden

Alle technieken en methoden die gebruikt worden in de best practice zijn gratis beschikbaar, de meesten zijn ook opensource en allen zijn goed gedocumenteerd. Deze overweging is gemaakt omdat zodoende deze best practice voor iedereen toegankelijk is. Uiteraard vergen sommige standaarden enige lering, maar omdat het hier een voor de beheer openbare ruimte sector nieuwe techniek betreft is dit logisch en billijk. Daarnaast zijn de gebruikte methoden en technieken niet alleen inzetbaar voor IMBOR-gegevens. Investeren in de kennis en kunde rondom deze standaarden zal lonen omdat deze breed toegepast kunnen en waarschijnlijk zullen gaan worden.

#### WKT vs GML

Bij het gebruik van GeoSPARQL moet een afweging gemaakt worden of de geometrie in een <abbr title="Well-known text">WKT-</abbr> of <abbr title="Geography Markup Language">GML-</abbr>serialisatie opgeslagen wordt. Hoewel ze onderling uitwisselbaar zijn verdient in deze best practice WKT de voorkeur. In essentie is namelijk het verschil dat bij WKT alle ‘Simple Feature geometrietypen’ uit de [[ISO19125]] gebruikt kunnen worden. De beperking is dat daardoor geen zaken als 3D, bogen, en dergelijk vastgelegd kunnen worden. In de GML-serialisatie kan dit wel want daar kunnen alle [[ISO19107]] geometrietypen gebruikt worden. Voor deze best practice, en waarschijnlijk de uitwisseling van IMBOR-gegevens op zich biedt WKT meer dan voldoende diepgang. Daarbij is de toepassing makkelijker en de ondersteuning breder. Zie voor nadere toelichting ook [uitleg van Geonovum][9] hierover. 

#### Metadata

IMBOR-gegevens gaan nagenoeg altijd over overheidsdata. Hierbij wordt geadviseerd om de [DCAT standaard toe te passen][12]. Deze standaard en het Nederlandse toepassingsprofiel daarbij zorgen ervoor dat gegevenssets overzichtelijk gepresenteerd kunnen worden en dat er gericht naar gezocht kan worden. Dit wordt gedaan door metadata per gegevensset vast te leggen. DCAT is ook een standaard van het W3C. 

In deze best practice is er voor gekozen om (nog) geen invulling te geven aan metadata. Deze overweging is gemaakt omdat deze best practice dan minder toegankelijk zou zijn, er gefocust is op de essentie en omdat de verschillende manieren van vastlegging nog niet goed genoeg onderzocht zijn. 

Mocht er toch dringende behoefte zijn, wordt er aanbevolen om deze minimale metadata op te nemen:
| Attribuut | URI | Datatype | 
| -------- | --- |------- | 
| identifier | dct:identifier | xsd:anyURI | 
| title | dct:title | xsd:string |
| description | dct:description | xsd:string | 
| modify | dct:modified | xsd:date | 
| publisher | dct:publisher | xsd:string |
| {.data} | | |

#### Revisies

Een belangrijke use case bij het delen van IMBOR-gegevens betreffen revisies. Daarmee wordt bedoeld dat de opdrachtgever een deel van zijn gegevensset van het areaal overdraagt aan een opdrachtnemer, die deze muteert en vervolgens teruglevert. Dit heeft te maken met versionering van gegevens en geldigheid. Dit valt vooralsnog buiten het domein van deze best practice. Deze overweging is gemaakt omdat deze best practice dan minder toegankelijk zou zijn, er gefocust is op de essentie en omdat de verschillende versionering nog niet goed genoeg onderzocht zijn. Voor achtergrond informatie hierover heeft CROW een [whitepaper][13] geschreven. 

[1]: https://geonovum.github.io/NEN3610-Linkeddata/#nen3610id
[2]: https://www.nen.nl/nen-2660-2-2022-nl-291667
[3]: https://w3id.org/nen2660/def/
[4]: https://docs.crow.nl/onto-verkenner/imbor/
[5]: https://docs.crow.nl/imbor/techdoc/#objecttypen
[6]: https://w3c.github.io/data-shapes/shacl/#validation-definition
[7]: https://opengeospatial.github.io/ogc-geosparql/geosparql11/spec.html#_well_known_text
[8]: https://opengeospatial.github.io/ogc-geosparql/geosparql11/spec.html#_geography_markup_language
[9]: https://docs.geostandaarden.nl/g4w/geox/#geometrie-encodings
[10]: https://www.ogc.org/standards/sfa
[11]: https://www.iso.org/standard/66175.html
[12]: https://data.overheid.nl/ondersteuning/open-data/dcat
[13]: https://docs.crow.nl/wp/ldversiebeheer/