## Doorlopen processtappen

In deze 'best practice' wordt het proces van gegevens aanmaken conform IMBOR tot en met het bevragen van deze gegevens met een query beschreven. Onderstaande figuur is een uitwerking van dit proces in hoofdstappen, inclusief manieren en middelen waarmee deze best practice tot stand is gekomen. De genoemde applicaties en formaten zijn slechts voorbeelden welke gebruikt zijn in deze exercitie. Ze zijn uitwisselbaar voor andere applicaties en formaten.

<figure>

![](img/proces1.png)

<figcaption>
Proces IMBOR-data in RDF
</figcaption>
</figure>

>ADVISEMENT
>QGIS is een open source geografisch informatiesysteem (GIS), waarmee geografische gegevens kunnen worden bekeken, bewerkt en geanalyseerd. Voor deze exercitie is het de 'stand-in' van het areaalbeheerpakket.

 De processtappen worden hierna in detail toegelicht.

### Data maken
Allereerst moet er (geo)data gemaakt worden. In de praktijk zal dit doorgaans in het beheerpakket worden gedaan of wordt dit aangeleverd en in het beheerpakket geïmporteerd. Bij de inrichting van het beheerpakket kan er rekening worden gehouden met de IMBOR-ontologie. Dit is geen vereiste, maar het vergemakkelijkt de communicatie over de gegevens en de transformatie naar een RDF conform IMBOR. Het figuur hieronder is de voorbeeld content waarmee gewerkt wordt.

>NOTE "Toekomstige implementaties"
>Voor succesvolle toepassing van deze werkwijze op de langere termijn is het te verwachten dat het areaalbeheerpakket niet centraal komt te staan, maar het gekozen registratiemodel (NEN2660-2). Deze flexibiliteit zou het beter mogelijk maken om snel om te kunnen gaan met opeenvolgende IMBOR versies, IMBOR uitbreidingen, subsets van IMBOR en gerelateerde standaarden (bijvoorbeeld GWSW) toepassen in samenhang met IMBOR.


<figure>

![](img/IMBOR_Exchange_Sample_Kaart.png)
<figcaption>
Assets/Objecten binnen het "IMBOR Exchange Sample"
</figcaption>
</figure>

>EXAMPLE "Asset informatie in QGIS"
>
>_Bestand: [IMBOR_Exchange_Sample_Project.qgs](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/geo_files)_
>
>In QGIS zijn een aantal objecten, attributen en relaties aangemaakt. Per `ObjectType` zijn niet alle beschikbare attributen en relaties opgenomen vanwege de overzichtelijkheid, maar is er voor gekozen om een representatieve selectie te gebruiken. Het bestand (.qgs) is te openen met de gratis [QGIS software][qgis]. Hier is te zien dat er 7 layers gemaakt zijn. 
>
>| Laag                                          | Inhoud                                                             |
>| --------------------------------------------- | -------------------------------------------------------------------| 
>| IMBOR_Exchange_Sample_Armatuur                | De geometrische representaties van de IMBOR [Armatuur](https://data.crow.nl/imbor/def/38a36b34-a593-499d-b210-0c48fb40ca3b)               |
>| IMBOR_Exchange_Sample_Boom                    | De geometrische representaties van de IMBOR [Boom](https://data.crow.nl/imbor/def/83a942f7-5291-42f0-afb1-9a57d0fb2f15)                   |
>| IMBOR_Exchange_Sample_Groeiplaatsinrichting   | De geometrische representaties van de IMBOR [Groeiplaatsinrichting](https://data.crow.nl/imbor/def/9d932904-c4b1-44e0-b151-b6df78f44a92)  |
>| IMBOR_Exchange_Sample_Hek                     | De geometrische representaties van het IMBOR [Hek](https://data.crow.nl/imbor/def/d61e45b1-3651-4c01-9c63-b9bfadf25a16)                   |
>| IMBOR_Exchange_Sample_Speelterrein            | De geometrische representaties van het IMBOR [Speelterrein](https://data.crow.nl/imbor/def/941a17c1-a2b2-4cd1-8991-08b0ebcf0c2a)          |
>| Relations                                     | De (niet geometrische) relaties tussen de [objecten (conform NEN2660-2)]((https://docs.crow.nl/imbor/techdoc/#semantische-relaties)                                     |
>| Opentopo                                      | Een OpenstreetMap kaartlaag ter referentie                         |
>|{.index} | | 
>
>Deze lagen zijn allemaal representaties van IMBOR `ObjectTypen` met hun `attributen`, `domeinwaarden` en `relaties`. Voor de identificatie van attributen en domeinwaarden zijn de IMBOR-URI's gebruikt bij het aanmaken van de verschillende velden. QGIS biedt de optie om deze een 'alias' mee te geven. Daarmee verschijnt niet de IMBOR-URI als veldnaam (kolomnaam), maar de label van het IMBOR-attribuut. 
>
>De gegevens zelf zitten als gegevensset in een [OGC GeoPackage][geopackage]. Dit is een open formaat (.qpkg) voor de opslag van geografische gegevens.
> 
>_Bestand: [IMBOR_Exchange_Sample.qpkg](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/geo_files)_
>
>In de GeoPackage zit alle informatie met betrekking tot de assets en de geometrie ervan. Het bestand is met GQIS te openen, maar ook bijvoorbeeld met de gratis software [DB Browser for SQLite][dbbrowser]. In het bestand zijn allerlei tabellen te vinden, waaronder:
>
>| Tabel                                         | Inhoud                                                             |
>| --------------------------------------------- | -------------------------------------------------------------------| 
>| IMBOR_Exchange_Sample_Armatuur                | De tabel met de gegevens en attributen voor de Armaturen laag |
>| IMBOR_Exchange_Sample_Boom                    | De tabel met de gegevens en attributen voor de Bomen laag   |
>| IMBOR_Exchange_Sample_Groeiplaatsinrichting   | De tabel met de gegevens en attributen voor de Groeiplaatsinrichtingen laag |
>| IMBOR_Exchange_Sample_Hek                     | De tabel met de gegevens en attributen voor de Hekken laag |
>| IMBOR_Exchange_Sample_Speelterrein            | De tabel met de gegevens en attributen voor de Speelterreinen laag |
>| Relations                                     | De tabel met de gegevens over alle relaties |
>|{.index} | |

### Exporteren
Vervolgens moeten de gegevens geëxporteerd worden. Idealiter zou er in het beheerpakket een optie zitten om meteen RDF conform de IMBOR-ontologie te exporteren. In de huidige praktijk zijn daar nog geen standaard oplossingen voor, daarom wordt er naar een tussenformat geëxporteerd welke omgezet kan worden naar RDF. [GeoJSON][geojson] is een handig open formaat hiervoor omdat dit eenvoudig te lezen is door scripts en daarmee relatief makkelijk getransformeerd kan worden. Het open beschikbare [GeoPackage][geopackage] is ook een hele goede optie omdat het tabellen bevat die eenvoudig naar triples omgezet kunnen worden. 

>EXAMPLE "Asset gegevens in geo-formaten"
>
>_Bestand: [IMBOR_Exchange_Sample.qpkg](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/geo_files)_
>
>_Bestand: [IMBOR_Exchange_Sample.json](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/geo_files)_
>
>Vanuit QGIS kunnen beiden formaten geëxporteerd worden (de GeoPackage was al reeds beschikbaar als bestand omdat het de bron is). Het exporten kan op meerdere manieren, hoe dit precies moet is buiten de scope van dit document.

### Transformeren
De volgende stap is het vertalen van de export naar RDF. RDF kan in verschillende formaten geserialiseerd worden. De Turtle-serialisatie wordt veel gebruikt omdat het een compacte en relatief eenvoudig menselijk leesbaar formaat is. JSON-LD is een andere serialisatie die meer gebruikt wordt bij communicatie tussen machines. De transformatie hoeft in principe één keer gescript te worden. Zeker wanneer het beheerpakket reeds de juiste IMBOR-URI's bevat is het eenvoudig.

>EXAMPLE "Gegevens in RDF"
>
>_Bestand: [IMBOR_Exchange_Sample.ttl](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/ld_files)_
>
>_Bestand: [IMBOR_Exchange_Sample.jsonld](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/ld_files)_
>
>De gegevens uit de GeoPackage of de GeoJSON van de vorige stap zijn getransformeerd naar een Turtle-bestand (.ttl). Hiermee bevat het bestand nu alle, en alleen, gegevens over de `objecten` en hun `geometrie`, `attributen` en onderlinge `relaties`. Overige informatie vanuit GeoJSON of GeoPackage is niet nodig en wordt niet meegenomen. De transformatie-stap is nu handmatig gedaan vanwege de minimale hoeveelheid werk. Dit is echter zeer eenvoudig te scripten en daarmee te automatiseren. Dit is vooralsnog buiten de scope van dit document. Middels een automatische transformatie is vervolgens het JSON-LD-bestand (.jsonld) gemaakt. Deze bevatten exact dezelfde triples, echter in een andere serialisatie. 

### Valideren
Om zeker te weten dat de geëxporteerde en getransformeerde gegevens conform IMBOR zijn _kan_ een [SHACL validatie][shaclval] gedaan worden. Met SHACL worden alle statements (triples) in de gegevensset gecheckt tegen de constraints (NL: beperkingen) die opgelegd zijn door IMBOR. Er zijn verschillende opensource SHACL validators te downloaden. Ze werken in basis allemaal hetzelfde. De input betreft de 1) de datafile en 2) de IMBOR-ontologie (de ‘shapes’-file). De output betreft een rapport die een `conforms:True` geeft of een `conforms:False`. Indien het niet conform is wordt aangegeven waar de fout zit.

>EXAMPLE "SHACL validatie"
>
>_Bestand: [IMBOR_Exchange_Sample.ttl](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/ld_files)_
>
>Het is geen essentiële stap, maar het valideren van de gegevensset in triples (.ttl) verdient wel de voorkeur. Dit om zeker te weten dat gegevensset conform IMBOR is. 
>
>_Bestand: [imbor-gecombineerd-tbv-shaclvalidatie.ttl](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/ld_files)_
>
>Bij een SHACL-validatie worden gegevensset(s) en shapes-set(s) verwacht. SHACL noemt deze respectievelijk  `datafile` en `shapesfile`. Voor dit voorbeeld zijn de shapes sets gecombineerd in één Turtle-bestand. Dit betreffen: 
>
>| Shapes set          | Inhoud                                                       | URI                                                                                               |
>|---------------------|--------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
>| IMBOR Kern          | Normatieve IMBOR-ontologie, inclusief SHACL-shapes           | https://data.crow.nl/imbor/def/                                                                   |
>| IMBOR Domeinwaarden | Normatieve IMBOR domeinwaarden                               | https://data.crow.nl/imbor/id/domeinwaarden/                                                      |
>| NEN2660-2           | NEN2660-complete ontologie, inclusief SHACL-shapes           | https://bimloket.github.io/nen2660/data/concat/nen2660.ttl                                        |
>| NEN3610             | NEN3610-ontologie ter referentie (optioneel)                 | https://raw.githubusercontent.com/Geonovum/NEN3610-Linkeddata/gh-pages/NEN3610-LD/vocabulaire.ttl |
>| MIM                 | MIM-ontologie ter referentie (optioneel)                     | https://docs.geostandaarden.nl/mim/mim/media/mim.ttl                                              |
>| QUDT Units          | QUDT-eenheden (wordt vanuit IMBOR-ontologie naar verwezen)   | http://qudt.org/vocab/unit/                                                                       |
>| QUDT Quantitykinds  | QUDT-grootheden (wordt vanuit IMBOR-ontologie naar verwezen) | http://qudt.org/vocab/quantitykind/                                                               |
>| SHACL               | SHACL-ontologie met de SHACL regels                          | https://www.w3.org/ns/shacl.ttl                                                                   |
>| DASH                | DASH-ontologie met de aanvullende SHACL regels               | https://datashapes.org/dash.ttl                                                                   |
>| {.index}            |                                                              |                                                                                                   |

De SHACL-validatie kan met meerdere opensource software uitgevoerd worden. Binnen dit document is de Python-implementatie [PySHACL][pys] gebruikt. Het installeren en bedienen van deze Python Library is buiten de scope van dit document. De command die gebruikt wordt voor de validatie binnen de best practice is:

```$ pyshacl -s "...\imbor-gecombineerd-tbv-shaclvalidatie.ttl" -e "...\imbor-gecombineerd-tbv-shaclvalidatie.ttl" -i rdfs -a -f human "...\IMBOR_Exchange_Sample.ttl" ```

De resultaten van deze validatie zijn `conforms:False`, met 10 `Warnings` en 1 `Violation`:

| Error                        | Bericht                                                                                                                                                                                                                                      | Toelichting                                                                                                                                                                                                                        |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Warning` over `geometrie`     | Het attribuut geometrie is gelijk aan de waarde van nen2660:hasBoundary. Wanneer deze gevuld is met een geo:Geometry mag daarmee het attribuut 'Geometrie' leeg zijn.                                                                        | Er wordt hier aangegeven dat IMBOR verplicht dat de waarde voor het attribuut `geometrie` gevuld is. Omdat de geometrie in dit bestand echter wel gevuld is, maar niet op dit specifieke attribuut (maar in een triple) is dit ok. |
| `Warning` over `identificatie` | Omdat technische gezien de klasse 'Geometrische Representatie' ook een subklasse is van nen2660:Object moeten deze allemaal ook de property 'identificatie' hebben. Dit is niet persé nodig als het hier een zogenaamde 'blanknode' betreft. | Er wordt hier aangegeven dat IMBOR verplicht dat de waarde het attribuut `identificatie` gevuld is. Omdat de geometrie in LinkedData een op zich staand object zou dat ook hiervoor gelden. Dat is echter niet persé nodig.        |
| `Violation` over `hasPart`     | Constraint Violation in QualifiedValueShapeConstraintComponent                                                                                                                                                                               | Er wordt hier aangegeven dat IMBOR verplicht dat elke Armatuur een Lichtbron heeft. Er is geen instantie van Lichtbron gevonden.                                                                                                   |
| {.data}                     |                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                    |                                                            |                                                                                                   |


>NOTE "Verschillende SHACL validators"
>
>Er zijn verschillende SHACL validators gratis als opensource beschikbaar. Het valt buiten de scope van dit document om daar nader op in te gaan, hieronder worden wel een aantal voorbeelden gegeven.
>
>* TopQuadrant's [TopBraid SHACL API][tqs] in Java (inclusief <abbr title="command-line-interface">CLI</abbr>);
>* Zazuko's [rdf-validate-shacl][zs] in Javascript;
>* Zazuko's [SHACL Playground][zp] webapplicatie (gebaseerd op voorgaande);
>* Apacha's [Apache Jena SHACL][ajs] in Java (inclusief CLI);
>* RDFLib's [PySHACL][pys] in Python (Python library en CLI);
>* dotNetRDF's [dotNetRDF API][dns] in dotNet (dotNet library).



### Beschikbaar stellen
Dit betreft een optionele stap. LinkedData heeft als best practice dat de data altijd live te bevragen zijn via een SPARQL-Endpoint (i.t.t. het uitwisselen van een file). Het betreft hier het verschil tussen ‘file-based exchange’ en ‘common-data environment’. De statements die in de file staan kunnen eenvoudig worden geüpload in een triple store binnen een LinkedData platform. Hiermee ontstaat er de mogelijkheid om de data op een URL beschikbaar te stellen en daarmee bevraagbaar te maken via SPARQL. De Turtle- of JSON-LD-file kan hiermee vervallen. 

Er bestaat dus ook een mogelijkheid om direct de Turtle- of JSON-LD-file over te dragen als 'gewone' overdracht van een document. Dit onderscheidt wordt nader toegelicht in [de inleiding](#uitwisselen-versus-delen)

### Bevragen
Wanneer de data als triples beschikbaar is, kan met de standaard LinkedData query taal SPARQL alles bevraagd worden. Elke applicatie die SPARQL begrijpt kan vervolgens vragen stellen over de data. Hiermee is het niet nodig een IMBOR specifieke taal te kennen of API beschrijving te maken.  

>EXAMPLE "RDF bevragen met LinkedData platform"
>Het is buiten de scope van dit document om exact aan te geven welke LinkedData oplossingen er zijn en wat de voor- en nadelen hiervan zijn. Voor dit voorbeeld is gewerkt met de gratis versie van TriplyDB. In TriplyDB kunnen o.a. Turtle-files worden geüpload en daar wordt dan automatisch een SPARQL-Endpoint voor aangemaakt. Deze kunnen dan in deze webapplicatie bevraagt worden met SPARQL. Voor IMBOR-gegevens in TriplyDB met name interessant omdat er goede integratie met GeoSPARQL is en het een kaartview heeft.
>
>_Bestand: [IMBOR_Exchange_Sample.ttl](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/ld_files)_
>
>Het triple bestand is geüpload in TriplyDB als een nieuwe 'graaf'. En er is een 'service' aangemaakt waarmee het SPARQL-Endpoint beschikbaar is.
>
>_Bestand: [IMBOR_Exchange_Sample_GeoSparql_Query.rq](https://github.com/Stichting-CROW/imbor/tree/master/docs/uitwisseling_rdf/files/ld_files)_
>
>Vervolgens is er een 'query' aangemaakt. Wanneer deze query wordt afgevuurd is dit het resultaat:
>
>| ObjectURI                                                                   | ObjectType                                                          | objectnaam            | geometrie                                                                                                                                                                                                                                                                                                 |
>|-----------------------------------------------------------------------------|---------------------------------------------------------------------|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
>| http://example.com/gemeente/areaaldata/9a6f7b7f-db55-4929-b87d-ff0d7d1a6998 | https://data.crow.nl/imbor/def/38a36b34-a593-499d-b210-0c48fb40ca3b | Armatuur5238.1        | POINT(5.8319988952738 51.839086447705)                                                                                                                                                                                                                                                                    |
>| http://example.com/gemeente/areaaldata/4db2734b-2295-4030-a349-9b5b2804c20  | https://data.crow.nl/imbor/def/941a17c1-a2b2-4cd1-8991-08b0ebcf0c2a | Speeltuin Kometenpark | POLYGON((5.8326328942049 51.839153036533,5.832244320377 51.838897245403,5.8326375605908 51.838670645748,5.8327411150681 51.838738661846,5.8327971946425 51.838778208121,5.8327521915079 51.838808783143,5.8327502452168 51.838898248813,5.8329115828112 51.838987094333,5.8326328942049 51.839153036533)) |
>| http://example.com/gemeente/areaaldata/6daaff3c-abf4-49e2-9904-a7a11b57d878 | https://data.crow.nl/imbor/def/d61e45b1-3651-4c01-9c63-b9bfadf25a16 | Hek_kompark_speeltuin | LINESTRING(5.8318746087 51.839117322916,5.8322257441654 51.838927719981,5.8325953082922 51.839170135358)                                                                                                                                                                                                  |
>| http://example.com/gemeente/areaaldata/6fb4b2c7-69ec-4976-8489-6ad2d35d9e63 | https://data.crow.nl/imbor/def/83a942f7-5291-42f0-afb1-9a57d0fb2f15 | Boom5238              | POINT(5.8319988952738 51.839086447705)                                                                                                                                                                                                                                                                    |
>| http://example.com/gemeente/areaaldata/a946356a-21ec-4be0-9c14-631786921d3a | https://data.crow.nl/imbor/def/9d932904-c4b1-44e0-b151-b6df78f44a92 | gpi5238               | POLYGON((5.8319900662722 51.839112392991,5.8319512755869 51.839088208093,5.8319932134683 51.839062815997,5.832033503399 51.839091501112,5.8319900662722 51.839112392991))                                                                                                                                 |
>| {.index}                                                                     |                                                                     |                       |                                                                                                                                                                                                                                                                                                           |
>
> In de eerst kolom staan de unieke identifiers van de gegevens, in de tweede kolom de (klikbare) link naar het IMBOR-ObjectType, in de derde kolom de objectnaam en in de laatste kolom de geometrie gegevens. 
>
>![](img/screenshot_triply_leaflet.png)
><figcaption> Query-resultaten gepresenteerd op een kaart. </figcaption>
></figure>





[qgis]: https://www.qgis.org/en/site/
[geopackage]: https://www.geopackage.org/spec131/index.html
[dbbrowser]: https://sqlitebrowser.org/
[geojson]: https://geojson.org/
[shaclval]: https://w3c.github.io/data-shapes/shacl/#validation-definition
[tqs]: https://github.com/TopQuadrant/shacl
[zs]: https://github.com/zazuko/rdf-validate-shacl
[zp]: https://shacl-playground.zazuko.com/
[ajs]: https://jena.apache.org/documentation/shacl/index.html
[pys]: https://github.com/RDFLib/pySHACL
[dns]: https://github.com/dotnetrdf/dotnetrdf
[triply]: https://triplydb.com
