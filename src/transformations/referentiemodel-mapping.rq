prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>
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
        ?mappingUri a imbor-refmodels:RefMapping ;
            dct:source ?imUri ;
            skos:note ?ToelichtingNL ;
            skos:scopeNote ?RelatieInformatieNL ;
            
            imbor-refmodels:imborObjecttype ?ObjecttypeUri ;
            imbor-refmodels:refObjecttype ?refObjecttypeUri .
    }

    graph <https://data.crow.nl/imbor/addendum/referentiemodellen-temp> {
        ?mappingUri imbor-refmodels:imborAttribuutDomeinwaarde (
                ( ?Attribuut1Uri ?Domeinwaarde1Uri )
                ( ?Attribuut2Uri ?Domeinwaarde2Uri )
                ( ?Attribuut3Uri ?Domeinwaarde3Uri )
            ) ;

            imbor-refmodels:refAttribuutDomeinwaarde (
                ( ?refAttribuut1Uri ?refDomeinwaarde1Uri )
                ( ?refAttribuut2Uri ?refDomeinwaarde2Uri )
                ( ?refAttribuut3Uri ?refDomeinwaarde3Uri )
            )  .            
    }
} where {
    graph <csv:table/refModel_Mapping> {
        ?mapping 
            csv:MappingGUID ?MappingGUID ;
            csv:RelatieInformatie ?RelatieInformatie ;
            csv:refInformatiemodel ?refInformatiemodel ;
            csv:Objecttype ?Objecttype ; # IMBOR objecttype
            csv:refObjecttype ?refObjecttype ; # doel objecttype
            .

        filter (?refInformatiemodel NOT IN (10, 15, 17))  # QUDT, 2660, 3610

        optional { ?mapping csv:Toelichting ?Toelichting . }
        BIND ( STRLANG(?Toelichting, "nl") as ?ToelichtingNL )
        BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?MappingGUID)) AS ?mappingUri)

        # Attributen en domeinwaarden komen altijd samen voor (x3): beide zijn een VocabulairID. 
        optional { 
            ?mapping csv:Attribuut1 ?Attribuut1 ; csv:Domeinwaarde1 ?Domeinwaarde1 .

            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?Attribuut1 ; csv:IMBORGUID ?Attribuut1IMBORGUID .
                [] csv:VocabulairID ?Domeinwaarde1 ; csv:IMBORGUID ?Domeinwaarde1IMBORGUID .
                BIND (URI(CONCAT(STR(imbor:), ?Attribuut1IMBORGUID)) AS ?Attribuut1Uri)
                BIND (URI(CONCAT(STR(imbor-domeinwaarde:), ?Domeinwaarde1IMBORGUID)) AS ?Domeinwaarde1Uri)
            }
        }
        optional { 
            ?mapping csv:Attribuut2 ?Attribuut2 ; csv:Domeinwaarde2 ?Domeinwaarde2 .

            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?Attribuut2 ; csv:IMBORGUID ?Attribuut2IMBORGUID .
                [] csv:VocabulairID ?Domeinwaarde2 ; csv:IMBORGUID ?Domeinwaarde2IMBORGUID .
                BIND (URI(CONCAT(STR(imbor:), ?Attribuut2IMBORGUID)) AS ?Attribuut2Uri)
                BIND (URI(CONCAT(STR(imbor-domeinwaarde:), ?Domeinwaarde2IMBORGUID)) AS ?Domeinwaarde2Uri)
            }
        }
        optional { 
            ?mapping csv:Attribuut3 ?Attribuut3 ; csv:Domeinwaarde3 ?Domeinwaarde3 .

            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?Attribuut3 ; csv:IMBORGUID ?Attribuut3IMBORGUID .
                [] csv:VocabulairID ?Domeinwaarde3 ; csv:IMBORGUID ?Domeinwaarde3IMBORGUID .
                BIND (URI(CONCAT(STR(imbor:), ?Attribuut3IMBORGUID)) AS ?Attribuut3Uri)
                BIND (URI(CONCAT(STR(imbor-domeinwaarde:), ?Domeinwaarde3IMBORGUID)) AS ?Domeinwaarde3Uri)
            }
        }

        # refAttributen en refDomeinwaarden komen altijd samen voor (x3): 
        #   verwijzen naar refModel_Attributen.refAttribuut, refModel_Domeinwaarden.refDomeinwaarde. 
        optional { 
            ?mapping csv:refAttribuut1 ?refAttribuut1 ; csv:refDomeinwaarde1 ?refDomeinwaarde1 . 
            graph <csv:table/refModel_Attributen> {
                [] csv:refAttribuutID ?refAttribuut1 ; csv:refAttribuutGUID ?refAttribuut1GUID .
                BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refAttribuut1GUID)) AS ?refAttribuut1Uri)
            }
            graph <csv:table/refModel_Domeinwaarden> {
                [] csv:refDomeinwaardeID ?refDomeinwaarde1 ; csv:refDomeinwaardeGUID ?refDomeinwaarde1GUID .
                BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refDomeinwaarde1GUID)) AS ?refDomeinwaarde1Uri)
            }
        }
        optional { 
            ?mapping csv:refAttribuut2 ?refAttribuut2 ; csv:refDomeinwaarde2 ?refDomeinwaarde2 . 
            graph <csv:table/refModel_Attributen> {
                [] csv:refAttribuutID ?refAttribuut2 ; csv:refAttribuutGUID ?refAttribuut2GUID .
                BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refAttribuut2GUID)) AS ?refAttribuut2Uri)
            }
            graph <csv:table/refModel_Domeinwaarden> {
                [] csv:refDomeinwaardeID ?refDomeinwaarde2 ; csv:refDomeinwaardeGUID ?refDomeinwaarde2GUID .
                BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refDomeinwaarde2GUID)) AS ?refDomeinwaarde2Uri)
            }
        }
        optional { 
            ?mapping csv:refAttribuut3 ?refAttribuut3 ; csv:refDomeinwaarde3 ?refDomeinwaarde3 . 
            graph <csv:table/refModel_Attributen> {
                [] csv:refAttribuutID ?refAttribuut3 ; csv:refAttribuutGUID ?refAttribuut3GUID .
                BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refAttribuut3GUID)) AS ?refAttribuut3Uri)
            }
            graph <csv:table/refModel_Domeinwaarden> {
                [] csv:refDomeinwaardeID ?refDomeinwaarde3 ; csv:refDomeinwaardeGUID ?refDomeinwaarde3GUID .
                BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refDomeinwaarde3GUID)) AS ?refDomeinwaarde3Uri)
            }
        }
    }

    graph <csv:table/imborVoc_Termen> {
        [] csv:VocabulairID ?RelatieInformatie ; csv:Term ?RelatieInformatieTerm .
        BIND ( STRLANG(?RelatieInformatieTerm, "nl") as ?RelatieInformatieNL )

        [] csv:VocabulairID ?Objecttype ; csv:IMBORGUID ?ObjecttypeIMBORGUID .
        BIND (URI(CONCAT(STR(imbor:), ?ObjecttypeIMBORGUID)) AS ?ObjecttypeUri)

    }

    graph <csv:table/refModel_Objecttypen> {
        [] csv:refObjecttypeID ?refObjecttype ; csv:refObjecttypeGUID ?refObjecttypeGUID .

        BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refObjecttypeGUID)) AS ?refObjecttypeUri)
    }

    graph <csv:table/refModel_Informatiemodellen> {
        [] csv:refInformatiemodelID ?refInformatiemodel ; csv:refInformatiemodelGUID ?refInformatiemodelGUID .

        BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refInformatiemodelGUID)) AS ?imUri)
    }

}
