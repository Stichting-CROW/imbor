prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-refmodels-id: <https://data.crow.nl/imbor-ref/id/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

insert {
    graph <https://data.crow.nl/imbor/addendum/minimale-dataset> {
        ?nodeShapeUri a sh:NodeShape ;
            dct:source ?imUri ;
            sh:targetClass ?klasseUri ;
            sh:property ?propShapeUri .
        ?propShapeUri a sh:PropertyShape ;
            dct:source ?imUri ;
            sh:path ?attribuutUri ;
            sh:minCount 1 .
        }
}
WHERE {
    graph <csv:table/refModel_MinimaleDatasets> {
        ?md csv:refInformatiemodel ?refInformatiemodel ;
           csv:refMinimaleDatasetGUID ?refMinimaleDatasetGUID ;
           csv:IMBORObjecttypeID ?IMBORObjecttypeID .
                
        optional {
            ?md csv:IMBORAttribuutID ?IMBORAttribuutID .
        
            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?IMBORAttribuutID ;
                   csv:IMBORGUID ?AttribuutGUID ;
            	   csv:Term ?Term2 .
        	}

		}
        
        graph <csv:table/imborVoc_Termen> {
            [] csv:VocabulairID ?IMBORObjecttypeID ;
               csv:IMBORGUID ?KlasseGUID ;
               csv:Term ?Term .
        }

        graph <csv:table/refModel_Informatiemodellen> {
            ?im csv:refInformatiemodelID ?refInformatiemodel ;
                csv:refInformatiemodelGUID ?refInformatiemodelGUID .

            BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refInformatiemodelGUID)) AS ?imUri)
        }
    }
    
    BIND (URI(CONCAT(STR(imbor-refmodels:), ?refMinimaleDatasetGUID)) AS ?nodeShapeUri)
    BIND (IF(BOUND(?IMBORAttribuutID), URI(CONCAT(STR(imbor-refmodels:), STRUUID())), ?IMBORAttribuutID) AS ?propShapeUri)
    BIND (URI(CONCAT(STR(imbor:), ?AttribuutGUID)) AS ?attribuutUri)
    BIND (URI(CONCAT(STR(imbor:), ?KlasseGUID)) AS ?klasseUri)
}