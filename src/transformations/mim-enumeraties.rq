PREFIX sh: <http://www.w3.org/ns/shacl#>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-refmodels-id: <https://data.crow.nl/imbor-ref/id/>

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
        ?MIMEnumeratieType a ?Type ;
            mim:naam ?EnumNaam ;
            mim:definitie ?EnumDef ;
            mim:begrip ?Begrip ;
            mim:begripsterm ?BegripsTerm ;
            mim:herkomst "IMBOR - Stichting CROW"@nl ;
            mim:herkomstDefinitie "IMBOR - Stichting CROW"@nl;
            mim:datumOpname "2023-01-01"^^xsd:date ;
            mim:locatie ?TypeLocatie ;
            .

        ?EnumeratieType mim:equivalent  ?MIMEnumeratieType .
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?EnumeratieType a rdfs:Class ;
            rdfs:subClassOf nen2660:EnumerationType ;
            skos:prefLabel ?EnumNaam ;
            skos:definition ?EnumDef ;
            imbor:typeLijst ?TypeLijst ;
            rdfs:seeAlso ?Begrip ;
            .
        BIND(IRI(REPLACE(STR(?EnumeratieType),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMEnumeratieType)  

        BIND(IF(?TypeLijst = "Suggestielijst"@nl, mim:Referentielijst, 
                    IF(?TypeLijst = "Enumeratielijst"@nl, mim:Enumeratie, 
                        ""))  as ?Type)
        
        BIND(IF(?TypeLijst = "Suggestielijst"@nl, "Voorlopig gedefinieerd binnen IMBOR op https://data.crow.nl/imbor/def"@nl, 
                    IF(?TypeLijst = "Enumeratielijst"@nl, "https://data.crow.nl/imbor/def", 
                        ""))  as ?TypeLocatie)
     }

     ?Begrip skos:prefLabel ?BegripsTerm .
}