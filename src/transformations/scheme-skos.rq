# Target-Graph: <https://data.crow.nl/imbor/term>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>

prefix dct: <http://purl.org/dc/terms/>
prefix dc: <http://purl.org/dc/elements/1.1/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

INSERT {
    graph imbor-term: {
        imbor-term:term-schema a skos:ConceptScheme;
            skos:prefLabel "IMBOR Vocabulaire (Begrippenkader voor IMBOR)"@nl ;
            skos:hasTopConcept ?broader ;
            dc:creator "IMBOR - Stichting CROW"@nl ;
            dc:format "SKOS"@nl ;
            dc:language "Nederlands"@nl ;
            dc:description "Vanaf IMBOR2022 is IMBOR gesplitst in een aantal modules. De IMBOR Vocabulaire is er daar eentje van en dit betreft het begrippenkader (of model van begrippen). De vocabulaire bevat 1) de begrippen (concepten), 2) de termen (geprefereerde en alternatieve), 3) de definities, 4) eventuele toelichtingen en 5) een indeling van de begrippen in groepen. Deze afsplitsing is gemaakt zodat de vocabulaire op zichzelf gebruikt kan worden (zonder de uitgebreidere ontologie) en omdat de aanpassingsfrequentie van de ontologie en de vocabulaire kan verschillen. Zo kan er apart van elkaar gewerkt worden. Vanuit de IMBOR Ontologie wordt met rdfs:seeAlso verwezen naar het begrip in deze vocabulaire. Voor meer informatie zie de IMBOR technische documentatie" ;
            .

        ?termURI a skos:Concept ;
            skos:inScheme imbor-term:term-schema ;
            .

        }
}
WHERE {
    ?termURI a skos:Concept .
    OPTIONAL {
        ?termURI skos:broader ?broader .
        filter not exists { ?broader skos:broader ?parent }
    }
}