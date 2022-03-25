# IMBOR (Informatiemodel Beheer Openbare Ruimte)

> Het IMBOR uniformeert begrippen voor het vakgebied ‘beheer openbare ruimte’. 
> [CROW](https://www.crow.nl/thema-s/management-openbare-ruimte/imbor/over-imbor)

Deze repo is gestart m.b.t. de documentatie omtrent de ontwikkeling en het gebruik van IMBOR in LinkedData-formaat. 
Medio 2021 is deze repo volledig overgegaan op _volledig_ IMBOR.

Deze repository wordt gebruikt voor de actieve ontwikkeling van IMBOR. 

Middels de GitHub Issues kunnen bug/features/aanbevelingen worden gegeven op IMBOR en de documentatie.

## Versiebeheer

CROW beraadt zich nog op een duurzame beheersstrategie ten aanzien van IMBOR in Linked data-formaat. 
Daar hoort ook versiebeheer bij. Zie ook issue [#2](https://github.com/Stichting-CROW/imbor/issues/2)

## Licentie

Deze repository en IMBOR worden beschikbaar gesteld onder verschillende licenties. Zie hiervoor: [Technische documentatie, sectie Licenties](https://docs.crow.nl/imbor/techdoc/#licenties).

## Benodigdheden transformatie

- Een beschikbaar SPARQL-endpoint dat werkt volgens de RDF4J-API, zoals bijv. GraphDB
- Pas de endpoints beschreven in [./sparql-query-runner.json] aan
- Zorg ervoor dat `npm` en `npx` beschikbaar zijn in `$PATH`
- Zorg ervoor dat de inputbestanden (sc. `IMBOR-2022*.accdb`)
- Voer uit: 

```sh
$ npx @rdmr-eu/sparql-query-runner
```

- Met Apache Jena's `riot` beschikbaar op `$PATH` worden ook de resulterende bestanden ge-pretty-format.
