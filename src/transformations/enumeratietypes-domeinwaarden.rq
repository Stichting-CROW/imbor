# Target-Graph: <https://data.crow.nl/imbor/def>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

insert {
    graph imbor-domeinwaarde: {
        ?domeinwaardeUri a ?enumTypeUri ;
            skos:prefLabel ?TermNL ;
            skos:definition ?DefinitieNL ;
            rdfs:seeAlso ?termUri ;
            imbor-domeinwaarde:bovenliggendeWaarde ?bovenliggendeTermNL .
    }
}
WHERE {
    graph <csv:table/imborKern_EnumeratiesDomeinwaarden> {
        ?row2 #csv:EnumeratieDomeinwaardeID ?EnumeratieDomeinwaardeID ;
            csv:Enumeratietype ?Enumeratietype ;
            csv:Domeinwaarde ?Domeinwaarde .

        optional {
            ?row2 csv:Bovenliggendewaarde ?BovenliggendewaardeID . 

            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?BovenliggendewaardeID ;
                    csv:Term ?bovenliggendeTerm .
            }
        }

        BIND (STRLANG( ?bovenliggendeTerm, "nl" ) AS ?bovenliggendeTermNL)
    }

    graph <csv:table/imborKern_K_KlassenAttributen> {
        [] csv:KlasseAttribuutID ?Enumeratietype ;  # koppeling met EnumeratiesDomeinwaarden.Enumeratie
            csv:Enumeratietype ?EnumeratietypeVocabID .
    }
    
    graph <csv:table/imborVoc_Termen> {
        [] csv:VocabulairID ?EnumeratietypeVocabID ;
            csv:IMBORGUID ?enumTypeIMBORGUID .
        
        BIND (URI(CONCAT(STR(imbor:), ?enumTypeIMBORGUID)) AS ?enumTypeUri)

        ?row1 csv:VocabulairID ?Domeinwaarde ;
            csv:IMBORGUID ?domeinwaardeIMBORGUID ;
            csv:Term ?Term ;
            csv:VocabulairGUID ?VocabulairGUID .

        optional { ?row1 csv:Definitie ?Definitie . }

        BIND (URI(CONCAT(STR(imbor-domeinwaarde:), ?domeinwaardeIMBORGUID)) AS ?domeinwaardeUri)
        BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUID)) AS ?termUri)

        BIND (STRLANG(?Term, "nl") as ?TermNL)
        BIND (STRLANG(?Definitie, "nl") as ?DefinitieNL)
    }
}
