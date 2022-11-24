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
        ?propShapeUri nen2660:hasUnit ?qudtUnit ;
            imbor:imborEenheid ?eenheidUri .
        ?attribuutUri nen2660:hasQuantityKind ?qudtQK .

        ?eenheidUri a rdfs:Class ;
            skos:prefLabel ?EenheidNaamNL ;
            skos:definition ?EenheidDefinitieNL ;
            rdfs:seeAlso ?eenheidVocabUri ;
            .
    }
}
WHERE {
    graph <csv:table/imborKern_K_KlassenAttributen> {
        [] csv:Attribuut ?Attribuut ;
            csv:IMBORGUID ?IMBORGUID ;  # guid van de property shape
            csv:Eenheid ?Eenheid ;
        	.
        
        graph <csv:table/imborVoc_Termen> {
            ?row3 csv:VocabulairID ?Eenheid ;
               csv:Term ?EenheidNaam ;
               csv:IMBORGUID ?EenheidIMBORGUID ;
               csv:VocabulairGUID ?EenheidVocabulairGUID .

            optional { ?row3 csv:Definitie ?EenheidDefinitie . }
            
            [] csv:VocabulairID ?Attribuut ;
               csv:Term ?AttribuutNaam ;
               csv:IMBORGUID ?AttribuutGUID .
            
            optional {
                graph <csv:table/refModel_Mapping> {
                    [] csv:Objecttype ?Eenheid ;
                       csv:refInformatiemodel 15 ;  # QUDT
                       csv:refAttribuut1 ?RefAttribuut1 ;
                       csv:refDomeinwaarde1 ?RefDomeinwaarde1 ;
                       .

                    graph <csv:table/refModel_Domeinwaarden> {
                        ?row2 csv:refDomeinwaardeID ?RefDomeinwaarde1 ;
                           csv:URI ?refDomeinwaardeURI . # eenheid
                    }

                    graph <csv:table/refModel_Attributen> {
                        ?row1 csv:refAttribuutID ?RefAttribuut1 ;
                           csv:URI ?grootheidURI .  # grootheid
                    }
                }
            }
        }
    }
    
    BIND (URI(CONCAT(STR(imbor:), ?IMBORGUID)) AS ?propShapeUri)
    BIND (URI(CONCAT(STR(imbor:), ?AttribuutGUID)) AS ?attribuutUri)
    BIND (URI(CONCAT(STR(imbor:), ?EenheidIMBORGUID)) AS ?eenheidUri)
    BIND (URI(CONCAT(STR(imbor-term:), ?EenheidVocabulairGUID)) AS ?eenheidVocabUri)
    BIND (URI(?refDomeinwaardeURI) as ?qudtUnit)
    BIND (URI(?grootheidURI) as ?qudtQK)

    BIND (STRLANG(?EenheidNaam, "nl") as ?EenheidNaamNL)
    BIND (STRLANG(?EenheidDefinitie, "nl") as ?EenheidDefinitieNL)
}