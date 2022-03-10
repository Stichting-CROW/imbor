# Een aantal xsd datatypen staan niet goed. Hier staan onterecht decimals, terwijl de lengte van de waarde doubles impliceert. Deze query fixed dat voor degene boven 55 characters.
PREFIX qudt: <http://qudt.org/schema/qudt/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

DELETE {
    ?s  qudt:conversionMultiplier ?o .
}
INSERT {
    ?s  qudt:conversionMultiplier ?nieuwe_o .
}

WHERE { 
	?s  qudt:conversionMultiplier ?o .
    BIND(STRLEN(STR(?o)) AS ?i) 
    FILTER (?i > 55)

    BIND(STRDT(STR(?o), xsd:double) AS ?nieuwe_o)
} 