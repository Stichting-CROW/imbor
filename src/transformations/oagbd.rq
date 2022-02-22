prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

insert {
    graph <https://data.crow.nl/imbor/addendum/oagbd> {
    	?propShapeUri imbor-refmodels:levensfaseTypering ?OAGBD .
    }
}
WHERE {
    graph <csv:table/imborKern_K_KlassenAttributen> {
        [] csv:IMBORGUID ?IMBORGUID ;  # guid van de property shape
            csv:OAGBD ?OAGBD . 
    }
    
    BIND (URI(CONCAT(STR(imbor:), ?IMBORGUID)) AS ?propShapeUri)
}
