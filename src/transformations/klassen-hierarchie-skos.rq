# Target-Graph: <https://data.crow.nl/imbor/def>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

INSERT {
    GRAPH imbor-term: {
        ?childUri skos:broader ?parentUri .
    }
}
WHERE {
    graph <csv:table/imborKern_Klassenindeling> {
        [] csv:KlasseParent ?KlasseParent ;
           csv:KlasseChild ?KlasseChild . 
    }

    graph <csv:table/imborKern_Klassen> {
        [] csv:KlasseID ?KlasseParent ;
            csv:Klasse ?parentVocabID .

        [] csv:KlasseID ?KlasseChild ;
            csv:Klasse ?childVocabID .
    }

    graph <csv:table/imborVoc_Termen> {
        [] csv:VocabulairID ?parentVocabID ;
           csv:VocabulairGUID ?VocabulairGUIDParent .

        [] csv:VocabulairID ?childVocabID ;
           csv:VocabulairGUID ?VocabulairGUIDChild .

        BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUIDParent)) AS ?parentUri)
        BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUIDChild)) AS ?childUri)
    }
}
