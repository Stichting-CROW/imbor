# Target-Graph: <https://data.crow.nl/imbor/def>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

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
        ?enumTypeUri a rdfs:Class ;
            rdfs:subClassOf nen2660:EnumerationType ;
            skos:prefLabel ?TermNL ;
            skos:definition ?DefinitieNL ;
            imbor:typeLijst ?LijstType ;
            rdfs:seeAlso ?termUri .

        ?propShapeUri sh:qualifiedValueShape [ ?AttribuutShapeWijze ?enumTypeUri ] .
    }
}
WHERE {
    graph <csv:table/imborKern_K_KlassenAttributen> {
        [] csv:Attribuut ?Attribuut ;
            csv:IMBORGUID ?IMBORGUID ;  #
            csv:Enumeratietype ?Enumeratietype .

        BIND (URI(CONCAT(STR(imbor:), ?IMBORGUID)) AS ?propShapeUri)

        graph <csv:table/imborKern_Attributen> {
            [] csv:Attribuut ?Attribuut ;
                csv:TypeAttribuut ?TypeAttribuut .

            VALUES (?TypeAttribuut ?AttribuutShapeWijze ?LijstType ) {
                ( 14484 sh:class "Suggestielijst"@nl )  # Referentie Open suggestie lijst
                ( 14481 sh:class "Enumeratielijst"@nl ) # Enumeratie Gesloten lijst
            }
        }

        graph <csv:table/imborVoc_Termen> {
            ?row1 csv:VocabulairID ?Enumeratietype ;
               csv:Term ?Term ;
               csv:VocabulairGUID ?VocabulairGUID ;
               csv:IMBORGUID ?enumTypeIMBORGUID .
            
            optional { ?row1 csv:Definitie ?Definitie . }

            BIND (URI(CONCAT(STR(imbor:), ?enumTypeIMBORGUID)) AS ?enumTypeUri)
            BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUID)) AS ?termUri)

            BIND (STRLANG(?Term, "nl") as ?TermNL)
            BIND (STRLANG(?Definitie, "nl") as ?DefinitieNL)
        }
            
    }
}
