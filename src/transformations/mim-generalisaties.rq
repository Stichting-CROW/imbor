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
prefix dash: <http://datashapes.org/dash#>

prefix mim: <http://bp4mc2.org/def/mim#>
prefix nen3610: <http://definities.geostandaarden.nl/def/nen3610#>
prefix nen2660: <https://w3id.org/nen2660/def#>


insert {
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMGeneralisatie   a   mim:Generalisatie ;
                            mim:naam    ?MIMGeneralisatieLabel ;
                            mim:datumOpname "2023-01-01"^^xsd:date ;
                            mim:supertype   ?MIMSuperKlasse ;
                            mim:subtype  ?MIMKlasse ;
        .
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?Klasse a rdfs:Class , sh:NodeShape ;
                skos:prefLabel  ?KlasseLabel ;
                rdfs:subClassOf     ?SuperKlasse .
        ?SuperKlasse    skos:prefLabel ?SuperKlasseLabel .

        BIND(
        IF(
        CONTAINS(STR(?Klasse),STR(nen2660:)),
        IRI(REPLACE(STR(?Klasse),"https://w3id.org/nen2660/def#","https://data.crow.nl/imbor/mim/mim-")),
        IF(
        CONTAINS(STR(?Klasse),STR(nen3610:)), 
        IRI(REPLACE(STR(?Klasse),"http://definities.geostandaarden.nl/def/nen3610#","https://data.crow.nl/imbor/mim/mim-")),   
        IF(
        CONTAINS(STR(?Klasse),STR(imbor:)),
        IRI(REPLACE(STR(?Klasse),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")), 
        "?" ))) 
        AS ?MIMKlasse)

        BIND(
        IF(
        CONTAINS(STR(?SuperKlasse),STR(nen2660:)),
        IRI(REPLACE(STR(?SuperKlasse),"https://w3id.org/nen2660/def#","https://data.crow.nl/imbor/mim/mim-")),
        IF(
        CONTAINS(STR(?SuperKlasse),STR(nen3610:)), 
        IRI(REPLACE(STR(?SuperKlasse),"http://definities.geostandaarden.nl/def/nen3610#","https://data.crow.nl/imbor/mim/mim-")),   
        IF(
        CONTAINS(STR(?SuperKlasse),STR(imbor:)),
        IRI(REPLACE(STR(?SuperKlasse),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")), 
        "?" ))) 
        AS ?MIMSuperKlasse)

        BIND(IRI(CONCAT("https://data.crow.nl/imbor/mim/",STRAFTER(STR(?MIMKlasse),"https://data.crow.nl/imbor/mim/"),"_",STRAFTER(STR(?MIMSuperKlasse),"https://data.crow.nl/imbor/mim/"))) AS ?MIMGeneralisatie)
        BIND(CONCAT(?SuperKlasseLabel, " is generalisatie van ", ?KlasseLabel) AS ?MIMGeneralisatieLabel )
    }
}
