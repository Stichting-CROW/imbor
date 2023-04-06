prefix quantitykind: <http://qudt.org/vocab/quantitykind/>
prefix nen2660: <https://w3id.org/nen2660/def#>
prefix nen2660-term: <https://w3id.org/nen2660/term#>
prefix unit: <http://qudt.org/vocab/unit/>
prefix sh: <http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix owl: <http://www.w3.org/2002/07/owl#>
prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor-refmodels: <https://data.crow.nl/imbor-ref/def/>
prefix imbor-meta: <https://data.crow.nl/imbor/aanvullend-metamodel>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix mim: <http://bp4mc2.org/def/mim#>

insert data {
    graph <https://data.crow.nl/imbor/term/> {
        <https://data.crow.nl/imbor/term/> a owl:Ontology ;
            owl:imports skos: , nen2660-term: ;
            rdfs:comment "Dit normatieve gedeelte betreft de vocabulair van IMBOR"@nl ;
            rdfs:label "IMBOR Vocabulaire"@nl .
    }

    graph <https://data.crow.nl/imbor/def/> {
        <https://data.crow.nl/imbor/def/> a owl:Ontology ;
            owl:imports skos: , nen2660: , nen2660-term: , sh:, quantitykind: , unit: , imbor-term: , imbor-meta: ;
            rdfs:comment "Dit normatieve gedeelte betreft de kern (de ontologie) van IMBOR"@nl ;
            rdfs:label "IMBOR Kernmodel (ontologie)"@nl .
    }

    graph <https://data.crow.nl/imbor/id/domeinwaarden/> {
        <https://data.crow.nl/imbor/id/domeinwaarden/> a owl:Ontology ;
            owl:imports skos: , nen2660: , nen2660-term: , sh:, quantitykind: , unit: , imbor-term: , imbor: , imbor-meta: ;
            rdfs:comment "Dit normatieve gedeelte betreft alle domeinwaarden van IMBOR"@nl ;
            rdfs:label "IMBOR Domeinwaarden"@nl .
    }

    graph <https://data.crow.nl/imbor/aanvullend-metamodel> {
        <https://data.crow.nl/imbor/aanvullend-metamodel> a owl:Ontology ;
            owl:imports skos: ;
            rdfs:comment "Een aantal metaconcepten worden specifiek voor IMBOR gedefinieerd. Dit wordt gedaan middels het 'IMBOR Aanvullend Metamodel'. Dit betreft een kleine ontologie van beschrijfende concepten die er voor zorgen dat alle IMBOR specifieke properties netjes en navolgbaar gedefinieerd zijn."@nl ;
            rdfs:label "IMBOR Aanvullend metamodel"@nl .
    }

    graph <https://data.crow.nl/imbor/addendum/oagbd> {
        <https://data.crow.nl/imbor/addendum/oagbd> a owl:Ontology ;
            owl:imports skos: , nen2660: , nen2660-term: , sh:, quantitykind: , unit: , imbor-term: , imbor: , imbor-meta: ;
            rdfs:comment "Dit informatieve gedeelte van IMBOR geeft aan bij elke combinatie van klasse en attribuut in welke fase van de levenscyclus van het object de informatie doorgaans bekend is."@nl ;
            rdfs:label "IMBOR addendum OAGBD"@nl .
    }

    graph <https://data.crow.nl/imbor/addendum/geometrie> {
        <https://data.crow.nl/imbor/addendum/geometrie> a owl:Ontology ;
            owl:imports skos: , nen2660: , nen2660-term: , sh:, quantitykind: , unit: , imbor-term: , imbor: , imbor-meta: ;
            rdfs:comment "Dit informatieve gedeelte van IMBOR geeft aan welke soort geometrische vastlegging de voorkeur heeft en welke er meer mogelijk zijn."@nl ;
            rdfs:label "IMBOR addendum Geometrie"@nl .
    }

    graph <https://data.crow.nl/imbor/addendum/minimale-dataset> {
        <https://data.crow.nl/imbor/addendum/minimale-dataset> a owl:Ontology ;
            owl:imports skos: , nen2660: , nen2660-term: , sh:, quantitykind: , unit: , imbor-term: , imbor: , imbor-meta: ;
            rdfs:comment "Dit informatieve gedeelte van IMBOR geeft aan welke Objecttype - Attribuut combinaties relevant zijn voor een ander informatiemodel (doorgaans een 'Methodiek')."@nl ;
            rdfs:label "IMBOR addendum Minimale datasets"@nl .
    }

    graph <https://data.crow.nl/imbor/addendum/referentiemodellen> {
        <https://data.crow.nl/imbor/addendum/referentiemodellen> a owl:Ontology ;
            owl:imports skos: , nen2660: , nen2660-term: , sh:, quantitykind: , unit: , imbor-term: , imbor: , imbor-meta: ;
            rdfs:comment "Dit informatieve gedeelte van IMBOR bevat de concepten die de relaties naar andere modellen bevatten."@nl ;
            rdfs:label "IMBOR addendum Referentiemodellen"@nl .
    }
    
    graph <https://data.crow.nl/imbor/mim> {
        <https://data.crow.nl/imbor/mim> a owl:Ontology , mim:Informatiemodel ;
            owl:imports imbor: , mim: ;
            rdfs:comment "Dit informatieve gedeelte van IMBOR verrijkt de IMBOR Kern met MIM classificaties en properties. Het is geenszins een volledige MIM 'mapping'. Bijvoorbeeld de relaties tussen MIM metaClass's zijn niet opgenomen."@nl ;
            rdfs:label "IMBOR addendum MIM"@nl ;
            mim:naam "IMBOR addendum MIM"@nl;
            mim:informatiedomein "Beheer openbare ruimte"@nl ;
            mim:mimversie "1.1"@nl ;
            .
    }
}

