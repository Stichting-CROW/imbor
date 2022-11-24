prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-refmodels-id: <https://data.crow.nl/imbor-ref/id/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

insert {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen> {
        ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?a1 ?a2 ) , ( ?b1 ?b2 ) , ( ?c1 ?c2 ) .
    }
} where {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen-temp> {
        ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?aa ?bb ?cc ) .

        ?aa rdf:first ?a1 ; rdf:rest [ rdf:first ?a2 ; rdf:rest rdf:nil ] .
        ?bb rdf:first ?b1 ; rdf:rest [ rdf:first ?b2 ; rdf:rest rdf:nil ] .
        ?cc rdf:first ?c1 ; rdf:rest [ rdf:first ?c2 ; rdf:rest rdf:nil ] .
    }
} ; 
insert {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen> {
        ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?a1 ?a2 ) , ( ?b1 ?b2 ) .
    }
} where {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen-temp> {
        ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?aa ?bb ?cc ) .

        ?aa rdf:first ?a1 ; rdf:rest [ rdf:first ?a2 ; rdf:rest rdf:nil ] .
        ?bb rdf:first ?b1 ; rdf:rest [ rdf:first ?b2 ; rdf:rest rdf:nil ] .
        filter not exists {
            ?cc rdf:first ?c1 .
        }
    }
} ;
insert {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen> {
        ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?a1 ?a2 ) .
    }
} where {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen-temp> {
        ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?aa ?bb ?cc ) .

        ?aa rdf:first ?a1 ; rdf:rest [ rdf:first ?a2 ; rdf:rest rdf:nil ] .
        filter not exists {
            ?bb rdf:first ?b1 ; rdf:rest [ rdf:first ?b2 ; rdf:rest rdf:nil ] .
        }
    }
} ;
insert {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen> {
        # ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?aa ?bb ?cc ) .
    }
} where {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen-temp> {
        ?mapping imbor-refmodels:imborAttribuutDomeinwaarde ( ?aa ?bb ?cc ) .

        filter not exists {
            ?aa rdf:first ?a1 ; rdf:rest [ rdf:first ?a2 ; rdf:rest rdf:nil ] .
        }
    }
}