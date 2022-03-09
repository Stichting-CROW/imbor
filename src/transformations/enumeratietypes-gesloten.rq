# Met dank aan Wouter Lubbers
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix xsd: <http://www.w3.org/2001/XMLSchema#>
prefix nen2660: <https://w3id.org/nen2660/def#>

prefix imbor-term: <https://data.crow.nl/imbor/term/>
prefix imbor: <https://data.crow.nl/imbor/def/>
prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>

prefix dct: <http://purl.org/dc/terms/>
prefix geo: <http://www.opengis.net/ont/geosparql#>
prefix sh:	<http://www.w3.org/ns/shacl#>
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix prov: <http://www.w3.org/ns/prov#>
prefix csv: <csv:>

INSERT {
    graph imbor-domeinwaarde: {
        ?tgtList a rdf:List .
        ?tgtList rdf:first ?tgtElementUri .
        ?tgtList rdf:rest ?tgtRestList .
        
        ?propShapeUri sh:in ?tgtListFirst .
    }
}
WHERE {
    # Iets om te zorgen dat je het over één en dezelfde hebt
    graph <csv:table/imborKern_Attributen> {
        [] csv:Attribuut ?Attribuut ;
            csv:TypeAttribuut 14481 . # Enumeratie Gesloten lijst
    }

    graph <csv:table/imborKern_K_KlassenAttributen> {
        [] csv:Attribuut ?Attribuut ;
            csv:IMBORGUID ?IMBORGUID ;
            csv:Enumeratietype ?EnumeratietypeVocabID .

        BIND (URI(CONCAT(STR(imbor:), ?IMBORGUID)) AS ?propShapeUri)

        # ---

        graph <csv:table/imborKern_K_KlassenAttributen> {
            [] csv:KlasseAttribuutID ?Enumeratietype ;  # koppeling met EnumeratiesDomeinwaarden.Enumeratie
                csv:Enumeratietype ?EnumeratietypeVocabID ;
        }
        
        graph <csv:table/imborVoc_Termen> {
            [] csv:VocabulairID ?EnumeratietypeVocabID ;
               csv:IMBORGUID ?enumGuid .
        }
        
        bind ( uri(concat(str(imbor:), ?enumGuid)) as ?tgtEnumeratieType)
    }

	## Je hebt 2 lijstjes nodig (= 2 subqueries) per Enumeratietype:
	## 1x om alle domeinwaarden op te halen + van iedere domeinwaarde het aantal domeinwaarden wat 'kleiner' is (op basis van een string-vergelijking)
	## 1x om alle domeinwaarden op te halen + van iedere domeinwaarde het aantal domeinwaarden wat 'groter' is (op basis van een string-vergelijking)
	## Hiermee kun je uiteindelijk sorteren en onderaan deze query een lijstje opbouwen
	{
        SELECT
            ?Enumeratietype 
            ?domeinwaardeUri # was: ?domeinwaardeIMBORGUID
            ?domeinwaarde
            ((COUNT(?predecessor)) AS ?elementIndex)
        WHERE {
            graph <csv:table/imborKern_EnumeratiesDomeinwaarden> {
                [] csv:Enumeratietype ?Enumeratietype ;
                    csv:Domeinwaarde ?Domeinwaarde .
            }

            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?Domeinwaarde ;
                    csv:IMBORGUID ?domeinwaardeIMBORGUID .

                BIND (URI(CONCAT(STR(imbor-domeinwaarde:), ?domeinwaardeIMBORGUID)) AS ?domeinwaardeUri)
            }

            optional {
                graph <csv:table/imborKern_EnumeratiesDomeinwaarden> {
                    [] csv:Enumeratietype ?Enumeratietype ;  # zelfde
                        csv:Domeinwaarde ?andereDomeinwaarde .
                }

                graph <csv:table/imborVoc_Termen> {
                    [] csv:VocabulairID ?andereDomeinwaarde ;
                        csv:IMBORGUID ?predecessor .
                }

                FILTER (?predecessor < ?domeinwaardeIMBORGUID)
            }
        }
        GROUP BY ?Enumeratietype ?domeinwaardeUri ?domeinwaarde
    }
    {
        SELECT
            ?Enumeratietype 
            ?domeinwaardeUri # was: ?domeinwaardeIMBORGUID
            ?domeinwaarde
            ((COUNT(?successor) = 0) AS ?isLastElement)
        WHERE {
            graph <csv:table/imborKern_EnumeratiesDomeinwaarden> {
                [] csv:Enumeratietype ?Enumeratietype ;
                    csv:Domeinwaarde ?Domeinwaarde .
            }

            graph <csv:table/imborVoc_Termen> {
                [] csv:VocabulairID ?Domeinwaarde ;
                    csv:IMBORGUID ?domeinwaardeIMBORGUID .

                BIND (URI(CONCAT(STR(imbor-domeinwaarde:), ?domeinwaardeIMBORGUID)) AS ?domeinwaardeUri)
            }

            optional {
                graph <csv:table/imborKern_EnumeratiesDomeinwaarden> {
                    [] csv:Enumeratietype ?Enumeratietype ;  # zelfde
                        csv:Domeinwaarde ?andereDomeinwaarde .
                }

                graph <csv:table/imborVoc_Termen> {
                    [] csv:VocabulairID ?andereDomeinwaarde ;
                        csv:IMBORGUID ?successor .
                }

                FILTER (?successor > ?domeinwaardeIMBORGUID)
            }
        }
        GROUP BY ?Enumeratietype ?domeinwaardeUri ?domeinwaarde
    }

    BIND (?domeinwaardeUri AS ?tgtElementUri) .
	## Nu ga je de lijstjes gebruiken om je rdf:list op te bouwen
	## In dit geval worden de URIs voor de list opgebouwd uit: de URI van Enumeratietype + '-list-' + een volgnummer
    BIND (CONCAT(str(?tgtEnumeratieType), "-list-") AS ?listBase) .
	## Startpunt van de lijst is altijd 0
    BIND (IRI(CONCAT(?listBase, "0")) AS ?tgtListFirst) .
	## De eerste subquery geeft een volgnummer terug, die plak je in de URI
    BIND (IRI(CONCAT(?listBase, str(?elementIndex))) AS ?tgtList) .
	## De tweede subquery geeft aan hoeveel domeinwaarden nog te gaan zijn. Als dit 0 is kun je de rdf:list afsluiten met rdf:nil, anders wijst hij door naar de volgende volgnummer in de lijst
    BIND (IF(?isLastElement, rdf:nil, URI(CONCAT(?listBase, str((?elementIndex + 1))))) AS ?tgtRestList) .
}