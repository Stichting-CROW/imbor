# Als er in SHACL een qualifiedValueShape is, moet er blijkbaar een minimale (of maximale) hoeveelheid constraint aangegeven worden.
# Deze query zorgt dat er expliciet een minimale multipliciteit wordt geintroduceerd.

PREFIX sh: <http://www.w3.org/ns/shacl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX imbor: <https://data.crow.nl/imbor/def/>

INSERT {
     GRAPH imbor: {
    ?s sh:qualifiedMinCount 0  
     }
}

WHERE { 
	?s sh:qualifiedValueShape ?o .
    FILTER NOT EXISTS {?s sh:qualifiedMaxCount ?t}
    FILTER NOT EXISTS {?s sh:qualifiedMinCount ?t2}

} 
