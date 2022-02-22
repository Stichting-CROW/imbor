# Target-Graph: <https://data.crow.nl/imbor/term>
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
    graph imbor-term: {
        ?termUri a skos:Concept ;
            skos:prefLabel ?TermNL ;
            skos:definition ?DefinitieNL ;
            skos:note ?ToelichtingNL ;
            skos:altLabel ?SynoniemNL ;
            .

        ?collectieUri a skos:Collection ;
            skos:prefLabel ?TermCollectieNL ;
            skos:note ?ToelichtingCollectieNL ;
            skos:member ?termUri ;
            .
    }
}
WHERE {
    graph <csv:table/imborVoc_Termen> {
        ?row
            csv:Term ?Term ;
            csv:VocabulairGUID ?VocabulairGUID ;
            csv:Collectie ?CollectieID ;
            .

        optional { ?row csv:Definitie ?Definitie . }
        optional { ?row csv:Toelichting ?Toelichting . }
        optional { ?row csv:Synoniem ?Synoniem . }
    }

    graph <csv:table/imborVoc_Collecties> {
        ?row2
            csv:CollectieID ?CollectieID ;
            csv:CollectieGUID ?CollectieGUID ;
            csv:Term ?TermCollectie ;
            .

        optional {
            ?row2 csv:Toelichting ?ToelichtingCollectie .
        }
    }

    BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUID)) AS ?termUri)
    BIND (URI(CONCAT(STR(imbor-term:), ?CollectieGUID)) AS ?collectieUri)
    BIND (STRLANG(?Term, "nl") as ?TermNL)
    BIND (STRLANG(?Definitie, "nl") as ?DefinitieNL)
    BIND (STRLANG(?Toelichting, "nl") as ?ToelichtingNL)
    BIND (STRLANG(?Synoniem, "nl") as ?SynoniemNL)
    BIND (STRLANG(?TermCollectie, "nl") as ?TermCollectieNL)
    BIND (STRLANG(?ToelichtingCollectie, "nl") as ?ToelichtingCollectieNL)
}