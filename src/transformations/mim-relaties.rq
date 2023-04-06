PREFIX sh: <http://www.w3.org/ns/shacl#>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-refmodels-id: <https://data.crow.nl/imbor-ref/id/>
prefix imbor-mim: <https://data.crow.nl/imbor/mim/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

prefix mim: <http://bp4mc2.org/def/mim#>
prefix nen3610: <http://definities.geostandaarden.nl/def/nen3610#>
prefix nen2660: <https://w3id.org/nen2660/def#>


insert {
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMRelatieSoort a mim:Relatiesoort ;
            mim:naam ?relatiesoortNaam ;
            mim:herkomst "IMBOR - Stichting CROW"@nl ;
            mim:herkomstDefinitie "IMBOR - Stichting CROW"@nl;
            mim:datumOpname "2023-01-01"^^xsd:date ;
            mim:kardinaliteit ?Kardinaliteit ;
            mim:unidirectioneel true ;
            mim:locatie "https://data.crow.nl/imbor/def" ;
            mim:bron  ?MIMVan ;
            mim:doel   ?MIMNaar ;
            .

        ?RelatieSoort     mim:equivalent  ?MIMRelatieSoort . 

        
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?RelatieSoort a sh:PropertyShape ;
            skos:prefLabel ?relatiesoortNaam ;
            sh:path ?path ;
            FILTER CONTAINS(str(?path),"nen2660") 
                        .
        
        BIND(IRI(REPLACE(STR(?RelatieSoort),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMRelatieSoort)  

        OPTIONAL {?RelatieSoort sh:minCount ?shmin}.
        OPTIONAL {?RelatieSoort sh:maxCount ?shmax}.
        OPTIONAL {?RelatieSoort sh:qualifiedMinCount ?shqmin}.
        OPTIONAL {?RelatieSoort sh:qualifiedMaxCount ?shqmax}.
        BIND(COALESCE(?shmin,?shqmin,0) AS ?min)
        BIND(COALESCE(?shmax,?shqmax,"*") AS ?max)
        BIND(CONCAT(STR(?min),"..",STR(?max)) AS ?Kardinaliteit)

        ?RelatieSoort   sh:qualifiedValueShape/sh:class ?Naar .
        ?Van            sh:property                     ?RelatieSoort .

        BIND(IRI(REPLACE(STR(?Naar),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMNaar)  
        BIND(IRI(REPLACE(STR(?Van),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMVan)  
     
     }
}
