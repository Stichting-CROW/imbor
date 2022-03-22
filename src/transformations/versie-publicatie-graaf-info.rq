# Omdat het hostingplatform van het SPARQL-endpoint geen grafen onderscheidt, 
# maar die voor sommige queries toch handig zijn, wordt dergelijk herkomst-info
# bewaard in een graaf/los bestand 'imbor/addendum/rest-api'.

prefix restapi: <https://data.crow.nl/rest-api/def#>
prefix coll: <https://data.crow.nl/rest-api/id#>

INSERT {
    GRAPH <https://data.crow.nl/imbor/addendum/rest-api> {
        <https://data.crow.nl/imbor/addendum/rest-api> a owl:Ontology ;
        rdfs:comment "Omdat het hostingplatform van het SPARQL-endpoint geen grafen onderscheidt, maar die voor sommige queries toch handig zijn, wordt dergelijk herkomst-info bewaard in een graaf/los bestand 'imbor/addendum/rest-api'"@nl ;
        rdfs:label "IMBOR REST-API Linkset"@nl ;
        .

        coll:IMBOR a restapi:Collectie ;
            rdfs:comment "Collectie om alles omtrent IMBOR uit de (gecombineerde) endpoints te filteren"@nl;
            restapi:hasMember ?s .

        coll:IMBOR-versie-2022 a restapi:Collectie ;
        rdfs:comment "Collectie om alles omtrent IMBOR versie 2022 uit de (gecombineerde) endpoints te filteren"@nl;
            restapi:hasMember ?s .

        ?g a restapi:Collectie ;
        rdfs:comment "Collectie om alles deze specifieke (IMBOR) graaf uit de (gecombineerde) endpoints te filteren"@nl;
            restapi:hasMember ?s .
    }
}
WHERE {
    GRAPH ?g {
        FILTER (!CONTAINS(STR(?g), "csv:table/"))
        ?s ?p ?o
    }
}

# select * where {
#     ?termUri a skos:Concept .
#     coll:IMBOR restapi:hasMember ?termUri .  # wel in IMBOR
#     FILTER NOT EXISTS { <https://data.crow.nl/imbor/id/domeinwaarden/> restapi:hasMember ?termUri }  # niet 
# }
