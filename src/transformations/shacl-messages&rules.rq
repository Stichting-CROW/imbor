# Ten behoeve van de SHACL validatie zijn hier enkele expliciete uitzonderingen/opmerkingen gemaakt die helpen om het validatierapport goed te interpreteren.

prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-refmodels-id: <https://data.crow.nl/imbor-ref/id/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix owl:  <http://www.w3.org/2002/07/owl#> 
prefix csv:  <csv:>

INSERT DATA { 
    graph <https://data.crow.nl/imbor/def/> {
        imbor:70fa1e34-7061-4de3-940f-f51e0d3f1fa5 sh:message "Het attribuut geometrie is gelijk aan de waarde van nen2660:hasBoundary. Wanneer deze gevuld is met een geo:Geometry mag daarmee het attribuut 'Geometrie' leeg zijn." ;
            sh:severity sh:Warning .
        imbor:be58f6d4-593e-49e2-b5c6-22c4d5793125 sh:message "Omdat technische gezien de klasse 'Geometrische Representatie' ook een subklasse is van nen2660:Object moeten deze allemaal ook de property 'identificatie' hebben. Dit is niet persé nodig als het hier een zogenaamde 'blanknode' betreft.";
            sh:severity sh:Warning .
        imbor:  a owl:Ontology ;
                  owl:imports sh: ;
	              sh:entailment sh:Rules .
    }
}

