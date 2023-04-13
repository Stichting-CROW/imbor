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
prefix dash: <http://datashapes.org/dash#>

prefix mim: <http://bp4mc2.org/def/mim#>
prefix nen3610: <http://definities.geostandaarden.nl/def/nen3610#>
prefix nen2660: <https://w3id.org/nen2660/def#>


insert {
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMKlasse a mim:Objecttype ;
            mim:naam ?KlasseNaam ;
            mim:definitie ?KlasseDef ;
            mim:begrip ?Begrip ;
            mim:begripsterm ?BegripsTerm ;
            mim:datumOpname "2023-01-01"^^xsd:date ;
            mim:indicatieAbstractObject ?abstract ;
            .
        
        ?Klasse     mim:equivalent  ?MIMKlasse .
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?Klasse a rdfs:Class , sh:NodeShape ;
            skos:prefLabel ?KlasseNaam ;
            skos:definition ?KlasseDef ;
            rdfs:seeAlso ?Begrip ;
            dash:abstract ?abstract ;
            .
        BIND(
        IF(
        CONTAINS(STR(?Klasse),STR(nen2660:)),
        IRI(REPLACE(STR(?Klasse),"https://w3id.org/nen2660/def#","https://data.crow.nl/imbor/mim/mim-")),
        IF(
        CONTAINS(STR(?Klasse),STR(nen3610:)), 
        IRI(REPLACE(STR(?Klasse),"http://definities.geostandaarden.nl/def/nen3610#","https://data.crow.nl/imbor/mim/mim-")),   
        IF(
        CONTAINS(STR(?Klasse),STR(imbor:)),
        IRI(REPLACE(STR(?Klasse),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")), 
        "?" ))) 
        AS ?MIMKlasse)
        
    }    
    ?Begrip skos:prefLabel ?BegripsTerm . 
}

;

insert {
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMKlasse  mim:herkomstDefinitie "IMBOR - Stichting CROW"@nl ;      
                    mim:herkomst "IMBOR - Stichting CROW"@nl ;
                    mim:locatie "https://data.crow.nl/imbor/def" ;
        .
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?Klasse a rdfs:Class , sh:NodeShape .
        filter contains(str(?Klasse), str(imbor:))

        BIND(IRI(REPLACE(STR(?Klasse),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMKlasse) 
    }
}

;

insert {
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMKlasse  mim:herkomstDefinitie "NEN3610 - Geonovum"@nl ;
                    mim:herkomst "NEN3610 - Geonovum"@nl ;
                    mim:locatie "http://modellen.geostandaarden.nl/def/nen3610-2022" ;
        .
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?Klasse a rdfs:Class , sh:NodeShape .
        filter contains(str(?Klasse), str(nen3610:))

        BIND(IRI(REPLACE(STR(?Klasse),"http://definities.geostandaarden.nl/def/nen3610#","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMKlasse) 
    }
}

;

insert {
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMKlasse  mim:herkomstDefinitie "NEN2660-2 - NEN"@nl ;
                    mim:herkomst "NEN2660-2 - NEN"@nl ;
                    mim:locatie "https://w3id.org/nen2660/def" ;
        .
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?Klasse a rdfs:Class , sh:NodeShape .
        filter contains(str(?Klasse), str(nen2660:))

        BIND(IRI(REPLACE(STR(?Klasse),"https://w3id.org/nen2660/def#","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMKlasse) 
    }
}

;
# Relatie tussen Klasse en Attribuut
insert { 
    graph <https://data.crow.nl/imbor/mim> {
        ?MIMKlasse  mim:attribuut   ?MIMAttribuutSoort .
        
    }
} where {
    GRAPH <https://data.crow.nl/imbor/def/> {
        ?Klasse a rdfs:Class , sh:NodeShape ;
                sh:property ?PropertyShape .
        ?PropertyShape  sh:path ?AttribuutSoort .
		FILTER (!CONTAINS(str(?AttribuutSoort),"nen2660"))
        # Om alleen attributen er uit te halen (geen relaties)

        BIND(IRI(REPLACE(STR(?Klasse),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMKlasse) 
        BIND(IRI(REPLACE(STR(?AttribuutSoort),"https://data.crow.nl/imbor/def/","https://data.crow.nl/imbor/mim/mim-")) AS ?MIMAttribuutSoort)  
    }
}