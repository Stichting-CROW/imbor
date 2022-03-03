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

insert {
   GRAPH imbor: {
        ?vakdisciplineUri
            a rdfs:Container ;
            skos:prefLabel ?TermNL ;
            skos:definition ?DefinitieNL ;
            rdfs:seeAlso ?termUri ;
            .

        ?vakdisciplineUri rdfs:member ?objecttypeUri .

        imbor:Vakdiscipline 
            a rdfs:Container ;
            skos:prefLabel "Vakdisciplines"@nl ;
            skos:definition "Verzamelgroep van alle vakdisciplines"@nl ;
            rdfs:member ?vakdisciplineUri ;
            .
   }
}
WHERE {
    graph <csv:table/imborKern_K_VakdisciplinesObjecttypen> {
        []
#            csv:VakdisciplineObjecttypeID ?VakdisciplineObjecttypeID ;
            csv:Vakdiscipline ?Vakdiscipline ;
            csv:Objecttype ?Objecttype .
        
        graph <csv:table/imborVoc_Termen> {
            ?row1 csv:VocabulairID ?Vakdiscipline ;
               csv:Term ?Term ;
               csv:VocabulairGUID ?VocabulairGUID ;
               csv:IMBORGUID ?VakdisciplineIMBORGUID .
            
            optional { ?row1 csv:Definitie ?Definitie . }
            
            [] csv:VocabulairID ?Objecttype ;
               csv:IMBORGUID ?ObjecttypeIMBORGUID .
        }
    }

    BIND (URI(CONCAT(STR(imbor:), ?VakdisciplineIMBORGUID)) AS ?vakdisciplineUri)
    BIND (URI(CONCAT(STR(imbor:), ?ObjecttypeIMBORGUID)) AS ?objecttypeUri)
    BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUID)) AS ?termUri)

    BIND (STRLANG(?Term, "nl") as ?TermNL)
    BIND (STRLANG(?Definitie, "nl") as ?DefinitieNL)
}