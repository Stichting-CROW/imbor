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
        ?MIMAttribuutSoort a mim:Attribuutsoort ;
            mim:naam ?AttribuutNaam ;
            mim:definitie ?AttribuutDef ;
            mim:begrip ?Begrip ;
            mim:begripsterm ?BegripsTerm ;
            mim:herkomst "IMBOR - Stichting CROW"@nl ;
            mim:herkomstDefinitie "IMBOR - Stichting CROW"@nl ;
            mim:datumOpname "2023-01-01"^^xsd:date ;
            mim:indicatieClassificerend ?Identificerend ;
            mim:kardinaliteit ?Kardinaliteit ;
            mim:toelichting ?Toelichting ;
            mim:locatie "https://data.crow.nl/imbor/def" ;
            .
        
        ?AttributeShape mim:equivalent ?MIMAttribuutSoort .
        ?AttribuutSoort mim:equivalent ?MIMAttribuutSoort .

        ?MIMAttribuutSoort  mim:type   ?MIMDatatype, ?MIMEnumeratieType  .

    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?AttribuutSoort a rdf:Property ;
            skos:prefLabel ?AttribuutNaam ;
            skos:definition ?AttribuutDef ;
            rdfs:seeAlso ?Begrip ;
            .
        
        BIND(IRI(REPLACE(STR(?AttribuutSoort),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMAttribuutSoort)  

        OPTIONAL    {?AttribuutShape sh:path ?AttribuutSoort .
        BIND(
            IF(?AttribuutSoort = imbor:c28b4e70-ea04-4ec2-875b-caf6c3521908, true,
                IF(?AttribuutSoort = imbor:e3e112b3-e46f-45c4-b2c9-b152e6f805a1, true,
                    IF(?AttribuutSoort = imbor:703dcaf1-98c7-4511-bf73-1a081538179c, true, 
                        false)))
            AS ?Identificerend)
                   }

        OPTIONAL {?AttribuutShape sh:minCount ?shmin}.
        OPTIONAL {?AttribuutShape sh:maxCount ?shmax}.
        OPTIONAL {?AttribuutShape sh:qualifiedMinCount ?shqmin}.
        OPTIONAL {?AttribuutShape sh:qualifiedMaxCount ?shqmax}.
        BIND(COALESCE(?shmin,?shqmin,0) AS ?min)
        BIND(COALESCE(?shmax,?shqmax,"*") AS ?max)
        BIND(CONCAT(STR(?min),"..",STR(?max)) AS ?Kardinaliteit)
        
        OPTIONAL {?AttribuutShape nen2660:hasUnit ?Toelichting}.
        OPTIONAL {?AttribuutShape sh:datatype      ?Datatype}.
        OPTIONAL {?AttribuutShape sh:qualifiedValueShape/sh:class      ?EnumeratieType}.

        BIND(IRI(REPLACE(STR(?EnumeratieType),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMEnumeratieType)  

        BIND(IF(CONTAINS(STR(?Datatype),"XML"),
                	IRI(REPLACE(STR(?Datatype),"http://www.w3.org/2001/XMLSchema#","https://data.crow.nl/imbor/mim/mim-")),
                		IRI(REPLACE(STR(?Datatype),"http://www.opengis.net/ont/geosparql#","https://data.crow.nl/imbor/mim/mim-"))) AS ?MIMDatatype) 
        
        }

    ?Begrip skos:prefLabel ?BegripsTerm .
}
