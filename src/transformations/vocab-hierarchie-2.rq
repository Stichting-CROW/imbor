prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix nen2660: <https://w3id.org/nen2660/def#>
prefix nen2660-term: <https://w3id.org/nen2660/term#>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

delete {
    graph <https://data.crow.nl/imbor/term/> {
        ?orig_s ?orig_p ?orig_o .
    }
}
insert {
    graph <https://data.crow.nl/imbor/term/> {
        ?orig_s ?orig_p ?new_o .
    }
}
where {
    graph <https://data.crow.nl/imbor/term/> {
        ?orig_s ?orig_p ?orig_o .
    }
    filter ( STRSTARTS(str(?orig_o), str(nen2660:) ) )
    bind( uri( replace( str(?orig_o), str(nen2660:), str(nen2660-term:) ) ) as ?new_o)
}
