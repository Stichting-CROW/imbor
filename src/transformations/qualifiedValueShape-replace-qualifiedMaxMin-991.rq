# Er zijn eigenschappen waarvoor wel een QualifiedMin/MaxCount wordt aangemaakt,
# maar waarvoor geen sh:qualifiedValueShape wordt gegenereerd. 
# Tracked in https://github.com/stichting-crow/imbor/issue/991

PREFIX sh: <http://www.w3.org/ns/shacl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX imbor: <https://data.crow.nl/imbor/def/>

DELETE {
	GRAPH imbor: {
    	?s ?qualifiedCount ?count .
	}
}  
INSERT {
	GRAPH imbor: {
		?s ?unqualifiedCount ?count .
	}
}  
WHERE { 
	?s a sh:PropertyShape ;
		?qualifiedCount ?count .
    FILTER NOT EXISTS {?s sh:qualifiedValueShape ?v .}

	VALUES (?qualifiedCount ?unqualifiedCount) {
		(sh:qualifiedMaxCount sh:maxCount )
		(sh:qualifiedMinCount sh:minCount )
	}
	
} 
