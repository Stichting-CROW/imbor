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

delete {
    graph ?g {
        ?s ?p ?originURI .
        ?ss ?originURI ?oo .
        ?originURI ?ppp ?ooo .
    }
}
insert {
    graph ?g {
        ?s ?p ?targetURI .
        ?ss ?targetURI ?oo .
        ?targetURI ?ppp ?ooo .
    }
} where {
    {
    select ?targetURI ?originURI where {
    graph <csv:table/refModel_Mapping> {
        # id vh ref_objecttype (nen2660:)
        [] csv:refInformatiemodel ?refInformatiemodel ;
            csv:Objecttype ?Objecttype ;
            csv:refObjecttype ?refObjecttype .

        # filter (?refInformatiemodel = 10 || ?refInformatiemodel = 17)
        # filter op informatiemodel: 17 (NEN 2660) en 10 (NEN 3610)
    }

    graph <csv:table/refModel_Objecttypen> {
        # uri van Activity

        [] csv:refObjecttypeID ?refObjecttype ;
            csv:URI ?targetURIString .

        bind (URI(?targetURIString) as ?targetURI)
    }

    graph <csv:table/imborVoc_Termen> {
        {
            # om imbor guid van "activiteit" te vinden
            [] csv:VocabulairID ?Objecttype ;
                csv:VocabulairGUID ?VocabulairGUID .

            BIND (URI(CONCAT(STR(imbor-term:), ?VocabulairGUID)) AS ?originURI)
        } UNION {
            [] csv:VocabulairID ?Objecttype ;
                csv:IMBORGUID ?ObjecttypeIMBORGUID .

            BIND (URI(CONCAT(STR(imbor:), ?ObjecttypeIMBORGUID)) AS ?originURI)
        }
    }
    }
    }

    graph ?g {
        filter (!CONTAINS(STR(?g), "csv:table/"))
        optional { ?s ?p ?originURI . }
        optional { ?ss ?originURI ?oo . }
        optional { ?originURI ?ppp ?ooo . }
    }
}
