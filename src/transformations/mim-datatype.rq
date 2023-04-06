PREFIX sh: <http://www.w3.org/ns/shacl#>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-refmodels-id: <https://data.crow.nl/imbor-ref/id/>
prefix imbor-mim: <https://data.crow.nl/imbor/mim/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

prefix mim: <http://bp4mc2.org/def/mim#>
prefix nen3610: <http://definities.geostandaarden.nl/def/nen3610#>
prefix nen2660: <https://w3id.org/nen2660/def#>


insert {
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMDatatype a ?MIMModelDatatype ;
            mim:naam ?MIMModelDatatypeNaam ;
            mim:definitie "Zie corresponderende specificatie"@nl ;
            mim:herkomst ?MIMModelDatatypeHerkomst ;
            mim:locatie ?MIMModelDatatypeHerkomst ;
            mim:datumOpname "2023-01-01"^^xsd:date ;
            
            .
        
        ?AttributeShape mim:equivalent ?MIMAttribuutSoort .
        ?AttribuutSoort mim:equivalent ?MIMAttribuutSoort .

        ?MIMAttribuutSoort mim:type ?MIMDatatype .
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?AttribuutSoort a rdf:Property .

        ?AttribuutShape sh:path ?AttribuutSoort ;
                        sh:datatype ?Datatype .
        
         BIND(IF(CONTAINS(STR(?Datatype),"XML"),
                	IRI(REPLACE(STR(?Datatype),"http://www.w3.org/2001/XMLSchema#","https://data.crow.nl/imbor/mim/mim-")),
                		IRI(REPLACE(STR(?Datatype),"http://www.opengis.net/ont/geosparql#","https://data.crow.nl/imbor/mim/mim-"))) AS ?MIMDatatype) 
   		
         VALUES 
            (?MIMDatatype                                           ?MIMModelDatatype       ?MIMModelDatatypeNaam    ?MIMModelDatatypeHerkomst               )
            {   
            (<https://data.crow.nl/imbor/mim/mim-string>             mim:CharacterString    "CharacterString"@nl     "https://www.w3.org/2001/XMLSchema"      )
            (<https://data.crow.nl/imbor/mim/mim-positiveInteger>    mim:Integer            "Integer"@nl             "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-integer>            mim:Integer            "Integer"@nl             "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-decimal>            mim:Decimal            "Decimal"@nl             "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-boolean>            mim:Boolean            "Boolean"@nl             "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-date>               mim:Date               "Date"@nl                "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-dateTime>           mim:DateTime           "DateTime"@nl            "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-gYear>              mim:Year               "Year"@nl                "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-anyURI>             mim:URI                "URI"@nl                 "https://www.w3.org/2001/XMLSchema"      ) 
            (<https://data.crow.nl/imbor/mim/mim-duration>           mim:Datatype           "Datatype"@nl            "https://www.w3.org/2001/XMLSchema"      ) 
# Hier is MIM nog geen standaard Primitief datatype voor. Dit zou eigenlijk wel moeten zijn. Is issue bij MIM. Voor nu zelf converteren naar xsd:duration
            (<https://data.crow.nl/imbor/mim/mim-wktLiteral> 	     mim:CharacterString    "CharacterString"@nl     "http://www.opengis.net/ont/geosparql"   ) 
# In IMBOR volgen wij niet de OGC splitsing. Daarom vertalen we geo:wktLiteral een string. Je kunt de discussie hebben of dit waardevol is, maar volgens mij is het niet ‘fout’.
            }
        }
}
