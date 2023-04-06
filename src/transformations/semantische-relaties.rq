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
        ?Objecttype1Uri
            a sh:NodeShape ;
            sh:property ?propShapeUri .
        
        ?propShapeUri 
            a sh:PropertyShape ;
            skos:prefLabel ?propDescNL ;
            sh:path ?nen2660Rela ;
            sh:qualifiedValueShape [ sh:class ?Objecttype2Uri ] ;
            sh:qualifiedMinCount ?minCount ;
            sh:qualifiedMaxCount ?maxCount ;
            .

        nen2660:hasBoundary rdfs:subPropertyOf geo:hasGeometry 
        .
    }
}
WHERE {
    graph <csv:table/imborKern_K_ObjecttypenSemantischeRelaties> {
        [] csv:IMBORGUID ?IMBORGUID ;
            csv:Multipliciteit ?Multipliciteit ;
            csv:Objecttype1 ?Objecttype1 ;
            csv:SemantischeRelatie ?SemantischeRelatie ;
            csv:Objecttype2 ?Objecttype2 .
        
        VALUES (?SemantischeRelatie ?nen2660Rela ?nen2660RelaNL) {
            ( 14525 nen2660:contains "bevat"@nl )
            ( 14526 nen2660:hasPart "heeft deel"@nl )
            ( 14569 nen2660:isConnectedTo "is verbonden met"@nl )
            ( 14596 nen2660:isDescribedBy "is beschreven door"@nl )
            ( 14995 nen2660:executes "voert uit"@nl )
            ( 15169 nen2660:consistsOf "bestaat uit"@nl )
#            ( 15170 nen2660:hasBoundary "heeft begrenzing"@nl )
        }
        
        values (?Multipliciteit ?minCount ?maxCount) {
            (15167  UNDEF  1     )
            (15168  UNDEF  UNDEF )
            (14518  1      1     )
            (14519  1      UNDEF )
            (16750  UNDEF  2     )
            (16912  2      UNDEF )
        }
### TODO: Gaat dit wel helemaal goed?
        
        graph <csv:table/imborVoc_Termen> {
            [] csv:VocabulairID ?Objecttype1 ;
               csv:Term ?Objecttype1Naam ;
               csv:IMBORGUID ?Objecttype1GUID .
            
            [] csv:VocabulairID ?Objecttype2 ;
               csv:Term ?Objecttype2Naam ;
               csv:IMBORGUID ?Objecttype2GUID .

        }
    }
    
    BIND (URI(CONCAT(STR(imbor:), ?IMBORGUID)) AS ?propShapeUri)
    BIND (CONCAT(?Objecttype1Naam, " ", ?nen2660RelaNL, " ", ?Objecttype2Naam) as ?propDesc)
    BIND (STRLANG(?propDesc, "nl") as ?propDescNL)
    BIND (URI(CONCAT(STR(imbor:), ?Objecttype1GUID)) AS ?Objecttype1Uri)
    BIND (URI(CONCAT(STR(imbor:), ?Objecttype2GUID)) AS ?Objecttype2Uri)
}