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

insert {
    graph imbor: {
        ?attribuutUri
            a rdf:Property ;
            skos:prefLabel ?TermNL ;
            skos:definition ?DefinitieNL ;
            skos:note ?AttribuutTypeTermNL ;
            rdfs:seeAlso ?termUri ;
            .

        ?attribuutUri rdfs:subPropertyOf ?attribuutParentUri .
    }
}
WHERE {
    graph <csv:table/imborKern_Attributen> {
        ?row 
            csv:AttribuutID ?AttribuutID ;
            csv:Attribuut ?Attribuut ;
            csv:TypeAttribuut ?TypeAttribuut ;  # GUID / Vrij invul / Enum ...
            # csv:Datatype ?Datatype ;  # hasQuantityKind / hasUnit 
            .

        graph <csv:table/imborVoc_Termen> {
            [] csv:VocabulairID ?TypeAttribuut ;
                csv:Term ?AttribuutTypeTerm .
        }

        optional {
            ?row csv:BovenliggendAttribuut/^csv:Attribuut/csv:Attribuut ?AttribuutTermCode .

            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?AttribuutTermCode ;
                    csv:IMBORGUID ?bovenliggendAttribuutIMBORGUID .
            }
        }
       
        graph <csv:table/imborVoc_Termen> {
            ?row4
                csv:VocabulairID ?Attribuut ;
                csv:VocabulairGUID ?VocabulairGUID ;
                csv:IMBORGUID ?IMBORGUID ;
                csv:Term ?Term ;
                .

            optional { ?row4 csv:Definitie ?Definitie . }
        }
    }
    
    BIND (URI(CONCAT(STR(imbor:), ?IMBORGUID)) AS ?attribuutUri)
    BIND (URI(CONCAT(STR(imbor:), ?bovenliggendAttribuutIMBORGUID)) AS ?attribuutParentUri)
    BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUID)) AS ?termUri)

    BIND (STRLANG(?Term, "nl") as ?TermNL)
    BIND (STRLANG(?Definitie, "nl") as ?DefinitieNL)
    BIND (STRLANG(?AttribuutTypeTerm, "nl") as ?AttribuutTypeTermNL)
}