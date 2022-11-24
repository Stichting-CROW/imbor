prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-refmodels-id: <https://data.crow.nl/imbor-ref/id/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix s: <http://schema.org/>
prefix csv: <csv:>

insert {
    graph <https://data.crow.nl/imbor/addendum/referentiemodellen> {
        ?imUri a imbor-refmodels:Informatiemodel ;
            skos:prefLabel ?refInformatiemodel ;
            skos:definition ?DefinitieNL ;
            rdfs:seeAlso ?urlAnyURI ;
            dct:publisher ?Beheerder ;
            s:version ?Versie .
    }
} where {
    graph <csv:table/refModel_Informatiemodellen> {
        ?im csv:refInformatiemodelGUID ?refInformatiemodelGUID ;
            csv:refInformatiemodel ?refInformatiemodel .
        
        optional {?im csv:Definitie ?Definitie .}
        optional {?im csv:Beheerder ?Beheerder .}
        optional {?im csv:Versie ?Versie .}
        optional {?im csv:URL ?URL .}
    }

    BIND (STRDT(?URL, xsd:anyURI) as ?urlAnyURI)
    BIND (STRLANG(?Definitie, "nl") as ?DefinitieNL)
    BIND (URI(CONCAT(STR(imbor-refmodels-id:), ?refInformatiemodelGUID)) AS ?imUri)
}
