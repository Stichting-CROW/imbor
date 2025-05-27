## Geometrie

***Gebaseerd op GitHub issue: [888](https://github.com/Stichting-CROW/imbor/issues/888), [1607](https://github.com/Stichting-CROW/imbor/issues/1607) en [1240](https://github.com/Stichting-CROW/imbor/issues/1240)***

IMBOR is primair bedoeld om te standaardiseren in type objecten en hun attributen (informatiebehoefte) betreffende vaste gegevens. De geometrische representatie wordt vaak ook als een vast gegeven gezien. De representatie van een object is echter één van de gegevens die geregistreerd wordt. Er zijn volgens IMBOR dan ook meerdere (geometrische)representaties mogelijk. In het addendum Geometrie van worden binnen IMBOR suggesties gegeven voor geometrische vastlegging. Het Geometrie addendum geeft aan welke soort geometrische vastlegging de voorkeur heeft en welke er meer mogelijk zijn. In het addendum wordt per Objecttype minimaal één relatie naar een GM_* klasse met de multipliciteit 1-1 meegegeven. Dit kan op Objecttype niveau geregistreerd worden of op de Klasse erboven (wanneer het voor allemaal geldt). Vervolgens worden eventueel meerdere relaties naar andere GM_* klassen meegegeven met een multipliciteit 0-1. Dit moet geïnterpreteerd worden als: "Wanneer het geometrie addendum van IMBOR van toepassing verklaard wordt, dan moet er minimaal één geometrie vastgelegd worden middels van het type dat de 1-1 multipliciteit heeft. 

Binnen LinkedData wordt gebruik gemaakt van de [[geosparql]] standaard om geometrie in RDF vast te leggen. Hiervoor zijn meerdere manieren. Binnen deze best practice wordt er met de [WKT serialisatie](https://opengeospatial.github.io/ogc-geosparql/geosparql11/document.html#rdfse_wkt) gewerkt. Meer uitleg hierover is ook te vinden in een andere best practice over [IMBOR gegevens delen middels RDF](https://docs.crow.nl/imbor/uitwisseling_rdf/).


>ADVISEMENT
> Er mag geometrie aangeleverd worden volgens de andere gespecificeerde vormen van geometrie, maar aanbevolen wordt de WKTLiteral in RDF. Bij uitwisseling middels Geopackage, Shapes, of andere bekende GIS-formaten werkt dit uiteraard anders.

Zie ook: [Techdoc | Geometrie](https://docs.crow.nl/imbor/techdoc/#geometrie)

### Toepassing materie IMBOR

>EXAMPLE
>Gemeente X wil vastleggen dat een bepaalde boom in een Natuurspeeltuin staat. Om dit te doen dient de gemeente in hun systeem een boom (`6fb4b2c7`) vast te leggen van het type IMBOR Boom, en een natuurspeeltuin (`4db2734b`) van het type IMBOR Natuurspeeltuin. Vervolgens wordt de geometrie van de natuurspeeltuin (een ruimte) vastgelegd als `polygone` (vlakgeometrie) en de geometrie van de boom als `point` (puntgeometrie). Hiervoor wordt de WKT serialisatie gebruikt. Deze geometrieën worden aan de objecten gekoppeld middels de `nen2660:hasBoundary` relatie. Deze gemeente wil tevens een expliciete relatie leggen tussen de natuurspeeltuin en de boom. Daarom wordt middels de `nen2660:contains` aangegeven dat deze boom in de natuurspeeltuin staat.

Dit is een voorbeelduitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix nen2660: <https://w3id.org/nen2660/def#>.
@prefix geo: <http://www.opengis.net/ont/geosparql#> .
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.

gemX:4db2734b a imbor:ace1a672-5cd7-4bac-a318-1296f6dabafe ; #'Natuurspeeltuin'
    nen2660:hasBoundary #  geo:hasGeometry
    [   a geo:Geometry ;
        geo:asWKT "<http://www.opengis.net/def/crs/EPSG/0/28992>POLYGON((185698.1621669908 427934.5411449945,185671.55693354324 427905.91937796044,185698.81266169614 427880.8753318056,185705.9030539841 427888.4861198579,185709.7409727455 427892.909483854,185706.61859815996 427896.2920563217,185706.42344974837 427906.2446253131,185717.4818597388 427916.1971943045,185698.1621669908 427934.5411449945))"^^geo:wktLiteral ;
    ]    ; #'geometrie'
    imbor:5f430c8d-7503-4a69-9e2f-f0b6e6c7f54e "4db2734b" ; #'identificatie'
    imbor:e0259ff5-4d44-4d5f-9fbf-666819ed78a5 "http://voorbeeld.org/gemX#"^^xsd:anyURI ; #'domein' (Voorbeeld gemeente data)   
    nen2660:contains gemX:6fb4b2c7 ; #'Natuurspeeltuin bevat Boom'
    .

gemX:6fb4b2c7 a imbor:83a942f7-5291-42f0-afb1-9a57d0fb2f15 ; #'Boom'
    nen2660:hasBoundary #  geo:hasGeometry
    [   a geo:Geometry ;
        geo:asWKT "<http://www.opengis.net/def/crs/EPSG/0/28992>POINT((185654.51397226387 427926.8653074717))"^^geo:wktLiteral ; 
    ]    ; #'geometrie'
    imbor:5f430c8d-7503-4a69-9e2f-f0b6e6c7f54e "6fb4b2c7" ; #'identificatie'
    imbor:e0259ff5-4d44-4d5f-9fbf-666819ed78a5 "http://voorbeeld.org/gemX#"^^xsd:anyURI ; #'domein' (Voorbeeld gemeente data)
    .
    .
```
