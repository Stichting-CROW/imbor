## Geometrie

***Gebaseerd op GitHub issue: [888](https://github.com/Stichting-CROW/imbor/issues/888), [1607](https://github.com/Stichting-CROW/imbor/issues/1607) en [1240](https://github.com/Stichting-CROW/imbor/issues/1240)***

IMBOR is primair bedoeld om te standaardiseren in type objecten en hun attributen (informatiebehoefte) betreffende vaste gegevens. De geometrische representatie wordt vaak ook als een vast gegeven gezien. De representatie van een object is echter één van de gegevens die geregistreerd wordt. Er zijn volgens IMBOR dan ook meerdere (geometrische)representaties mogelijk. In het addendum Geometrie van worden binnen IMBOR suggesties gegeven voor geometrische vastlegging. Het Geometrie addendum geeft aan welke soort geometrische vastlegging de voorkeur heeft en welke er meer mogelijk zijn. In het addendum wordt per Objecttype minimaal één relatie naar een geometrie klasse uit [Simple Features](https://opengeospatial.github.io/ogc-geosparql/geosparql11/sf_geometries.html) met de multipliciteit 1-1 meegegeven. Dit kan op Objecttype niveau geregistreerd worden of op de Klasse erboven (wanneer het voor allemaal geldt). Vervolgens worden eventueel meerdere relaties naar andere geometrie klassen meegegeven met een multipliciteit 0-1. Dit moet geïnterpreteerd worden als: "Wanneer het geometrie addendum van IMBOR van toepassing verklaard wordt, dan moet er minimaal één geometrie vastgelegd worden middels van het type dat de 1-1 multipliciteit heeft. 

Binnen LinkedData wordt gebruik gemaakt van de [[geosparql]] standaard om geometrie in RDF vast te leggen. Hiervoor zijn meerdere manieren. Binnen deze best practice wordt er met de [WKT serialisatie](https://opengeospatial.github.io/ogc-geosparql/geosparql11/document.html#rdfse_wkt) gewerkt. Meer uitleg hierover is ook te vinden in een andere best practice over [IMBOR gegevens delen middels RDF](https://docs.crow.nl/imbor/uitwisseling_rdf/).


>ADVISEMENT
> Er mag geometrie aangeleverd worden volgens de andere gespecificeerde vormen van geometrie, maar aanbevolen wordt de WKTLiteral in RDF. Bij uitwisseling middels Geopackage, Shapes, of andere bekende GIS-formaten werkt dit uiteraard anders.

Zie ook: [Techdoc | Geometrie](https://docs.crow.nl/imbor/techdoc/#geometrie)

### Toepassing geometrie in IMBOR

>EXAMPLE
>Gemeente X wil vastleggen dat een bepaalde boom in een Natuurspeeltuin staat. Om dit te doen dient de gemeente in hun systeem een boom (`6fb4b2c7`) vast te leggen van het type IMBOR Boom, en een natuurspeeltuin (`4db2734b`) van het type IMBOR Natuurspeeltuin. Vervolgens wordt de geometrie van de natuurspeeltuin (een ruimte) vastgelegd als `polygone` (vlakgeometrie) en de geometrie van de boom als `point` (puntgeometrie). Hiervoor wordt de WKT serialisatie gebruikt. Deze geometrieën worden aan de objecten gekoppeld middels de `nen2660:hasBoundary` relatie. Deze gemeente wil tevens een expliciete relatie leggen tussen de natuurspeeltuin en de boom. Daarom wordt middels de `nen2660:contains` aangegeven dat deze boom in de natuurspeeltuin staat.

Dit is een voorbeelduitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/geometrie.ttl" data-include-format="text"></code></pre>
