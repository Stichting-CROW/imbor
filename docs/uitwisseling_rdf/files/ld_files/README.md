# IMBOR gegevens delen met RDF - LinkedData files

Deze folder bevat alle LinkedData files die bij het uitwissel voorbeeld horen:

* IMBOR_Exchange_Sample.ttl
    * De gegevenset met voorbeeld data in Turtle serialisatie
* IMBOR_Exchange_Sample.jsonld
    * De gegevenset met voorbeeld data in JSON-LD serialisatie
* IMBOR_Exchange_Sample_GeoSparql_Query.rq
    * SPARQL query om de gegevens te bevragen
* imbor-gecombineerd-tbv-shaclvalidatie.ttl
    * Gecombineerd IMBOR model, inclusief de SHACL shape en de IMBOR ontologie

## TTL naar JSON-LD

De JSON-LD file is gemaakt door de TTL file om te zetten met [Apache Jena's ](https://jena.apache.org/documentation/io/) `riot`
``` sh
$ riot --output=JSONLD **.ttl >**.jsonld
```
Vervolgens op https://json-ld.org/playground/ de *.jsonld als input te geven.

Compacted output te vragen, tezamen met onderstaande 'context' als "New JSON-LD Context" 
https://tinyurl.com/mrythu26

En als laatste handmatig nog de apart geïdentificeerde blanknodes, vervangen door json-objects 

``` json
{
  "@context": {
    "imbor": "https://data.crow.nl/imbor/def/",
    "imbor-domeinwaarde": "https://data.crow.nl/imbor/id/domeinwaarden/",
    "nen2660": "https://w3id.org/nen2660/def#",
    "geo": "http://www.opengis.net/ont/geosparql#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "sh": "http://www.w3.org/ns/shacl#",
    "data": "http://example.com/gemeente/areaaldata/",
    "geo:asWKT": {
      "@type": "geo:wktLiteral"
    }
  }
}
```
