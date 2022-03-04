# Target-Graph: <https://data.crow.nl/imbor/def>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
PREFIX dash: <http://datashapes.org/dash#>
prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

INSERT {
    GRAPH imbor: {
        ?klasseUri
            a rdfs:Class , sh:NodeShape ;
            dash:abstract ?KlasseTypeBool ;
            skos:prefLabel ?TermNL ;
            skos:definition ?DefinitieNL ;
            rdfs:seeAlso ?termUri ;
            skos:note ?ToelichtingNL ;
            .
    }
}
WHERE {
    graph <csv:table/imborKern_Klassen> {
        ?row 
            csv:Klasse ?Klasse ;  # vocabulairID
            csv:KlasseID ?KlasseID ;  # tabel 
            .
    }

    graph <csv:table/imborVoc_Termen> {
        VALUES (?KlasseType ?KlasseTypeNL ?KlasseTypeBool) {
            (14795 "Abstract"@nl true  )
            (14796 "Concreet"@nl false )
        }

        ?rowTerm
            csv:VocabulairID ?Klasse ;
            csv:VocabulairGUID ?VocabulairGUID ;
            csv:IMBORGUID ?IMBORGUID ;
            csv:Term ?Term ;
            csv:Collectie ?Collectie ;
            csv:KlasseType ?KlasseType ;
            .
        
        optional { ?rowTerm csv:Definitie ?Definitie . }
        optional { ?rowTerm csv:Toelichting ?Toelichting . }

        # 24 == enumeratietype
        filter ( ?Collectie != 24 )
    }

    BIND (URI(CONCAT(STR(imbor:), ?IMBORGUID)) AS ?klasseUri)
    BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUID)) AS ?termUri)

    BIND (STRLANG(?Term, "nl") as ?TermNL)
    BIND (STRLANG(?Toelichting, "nl") as ?ToelichtingNL)
    BIND (STRLANG(?Definitie, "nl") as ?DefinitieNL)
}