prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

insert data {
    graph <https://data.crow.nl/imbor/aanvullend-metamodel> {
        imbor-refmodels:levensfaseTypering a rdf:Property ;
            skos:prefLabel "typering levensfase"@nl ;
            skos:definition "Dit attribuut is van toepassing op het (O)ntwerp, (A)anleg, (G)eovoorziening, (B)eheer, (D)ynamisch gegeven"@nl ;
            rdfs:range xsd:string ;
            .

        imbor-refmodels:Informatiemodel a rdfs:Class ;
            skos:prefLabel "Informatiemodel"@nl ;
            skos:definition "Externe informatiebron (of ontologie) ten behoeve van IMBOR."@nl ;
            .

        imbor-refmodels:imborAttribuutDomeinwaarde a rdf:Property ;
            skos:prefLabel "mapt naar IMBOR-attribuut-domeinwaarde"@nl ;
            skos:definition "Relateert van een mapping naar een attribuut-domeinwaarde-combinatie."@nl ;
            .
        imbor-refmodels:imborObjecttype a rdf:Property ;
            skos:prefLabel "mapt naar IMBOR-objecttype"@nl ;
            skos:definition "Relateert van een mapping naar naar dit IMBOR-objecttype."@nl ;
            .
        imbor-refmodels:RefAttribuut a rdfs:Class ;
            skos:prefLabel "Extern attribuut"@nl ;
            skos:definition "Representatie in de IMBOR-context van wat extern een attribuut is."@nl ;
            .
        imbor-refmodels:refAttribuutDomeinwaarde a rdf:Property ;
            skos:prefLabel "mapt naar extern attribuut-domeinwaarde"@nl ;
            skos:definition "Relateert van een mapping naar dit externe attribuut-domeinwaarde-combinatie."@nl ;
            .
        imbor-refmodels:RefDomeinwaarde a rdfs:Class ;
            skos:prefLabel "Externe domeinwaarde"@nl ;
            skos:definition "Representatie in de IMBOR-context van wat extern een domeinwaarde is."@nl ;
            .
        imbor-refmodels:RefMapping a rdfs:Class ;
            skos:prefLabel "Externe mapping"@nl ;
            skos:definition "Mapping van een extern informatiemodel van of naar IMBOR."@nl ;
            .
        imbor-refmodels:refObjecttype a rdf:Property ;
            skos:prefLabel "mapt naar extern objecttype"@nl ;
            skos:definition "Relateert van een mapping naar dit externe objecttype."@nl ;
            .
        imbor-refmodels:RefObjecttype a rdfs:Class ;
            skos:prefLabel "Extern objecttype"@nl ;
            skos:definition "Representatie in de IMBOR-context van wat extern een objecttype is."@nl ;
            .

        imbor:imborEenheid a rdf:Property ;
            skos:prefLabel "eenheid (IMBOR)"@nl ;
            skos:definition "De klasse van de IMBOR-specifieke eenheid waarin dit attribuut gemeten wordt."@nl ;
            rdfs:range rdfs:Class ;
            .

        imbor-domeinwaarde:bovenliggendeWaarde a rdf:Property ;
            skos:prefLabel "categorie domeinwaarde"@nl ;
            skos:definition "Domeinwaarden die in picklists van elkaar afhankelijk zijn."@nl ;
            rdfs:range xsd:string .

        imbor:typeLijst a rdf:Property ;
            skos:prefLabel "open/gesloten"@nl ;
            skos:definition "Of deze lijst een open suggestielijst is of een gesloten enumeratielijst."@nl ;
            rdfs:range xsd:string .
    }
}