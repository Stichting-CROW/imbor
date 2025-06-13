## InformatieObjecten (a.d.h.v. Inwinning-informatie)

***Gebaseerd op GitHub issue: [1389](https://github.com/Stichting-CROW/imbor/issues/1389).***

`Inwinning-informatie` is een `InformatieObject` voor het vastleggen van informatie m.b.t. de inwinning van (de eigenschappen van) een objecttype. 
Een vergelijkbare entiteit is `Registratie-informatie`, omdat dit ook 'meta' informatie bevat. 
`Inwinning-informatie` is echter speciaal omdat hier een speciale afspraak gemaakt moet worden met betrekking tot twee attributen van deze klasse. 
De attributen `attribuut` en `domeinwaarde` zijn nu van het datatype `xsd:string`.
Maar eigenlijk mogen hier alleen respectievelijk de IMBOR-attributen en bijbehorende IMBOR-domeinwaarden voorkomen. In principe mag hier dus elke waarde staan. Vanuit deze best practice wordt aanbevolen om de complete IMBOR URI (identifier) te vermelden.

Dit betreft een speciale modelleerconstructie en daarom wordt dit als best practice uitgewerkt. 

### Toepassing inwinning-informatie in IMBOR

Aan de hand van een voorbeeld wordt getoond hoe het InformatieObject `Inwinning-informatie` wordt toegepast.

>EXAMPLE
>Gemeente X wil vastleggen dat de de oppervlakte en de inhoudsklasse van een groeiplaats is ingewonnen op '12 december 2024', middels een inmeting. De oppervlakte is '3.1m2' en de inhoudsklasse is bepaalde op 'tot 5 m3'. Hiervoor moet een instantie van `imbor:9d932904-c4b1-44e0-b151-b6df78f44a92` (Groeiplaats) worden gemaakt. Deze bevat de attributen `oppervlakte` en `inhoudsklasse` met respectievelijk de waarden `3,1` en `imbor-domeinwaarde:0eeaaa8b-b6a7-40bb-9597-4e18fcf0c868`. Vervolgens worden er twee relaties (`nen2660:isDescribedBy`) naar twee instanties van het informatieobject `Inwinning-informatie` gelegd. De eerste (`gemX:GP1Inwininfo`) bevat de attributen `attribuut`, `inwinningsdatum` en `wijze van inwinnen` en beschrijft informatie over de inwinning van 'oppervlakte'. De tweede (`gemX:GP2Inwininfo`) bevat de metainformatie over de inwinning van de inhoudsklasse. 

Dit is een voorbeeld uitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix nen2660: <https://w3id.org/nen2660/def#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.

gemX:Groeiplaats1   a   imbor:9d932904-c4b1-44e0-b151-b6df78f44a92 ;                                                        # Groeiplaats
                    nen3610:domein  "http://voorbeeld.org/gemX#" ;              
                    nen3610:identificatie   "Groeiplaats1" ;
                    imbor:29ec4228-7a32-41db-ac73-b80db66ea743  "3.1"^^xsd:decimal ;                                        # oppervlakte
                    imbor:5b876aa9-3dc0-4aed-a843-6ce05ed9226a  imbor-domeinwaarde:0eeaaa8b-b6a7-40bb-9597-4e18fcf0c868 ;   # inhoudsklasse / "tot 5 m3"
                    nen2660:isDescribedBy   gemX:GP1Inwininfo , gemX:GP2Inwininfo ;                                         # isBeschrevenDoor
                    .

gemX:GP1Inwininfo   a   imbor:8ab0ac02-ee94-4086-9b14-d53ede3c4101 ;                                                        # Inwinning-informatie
                    nen3610:domein  "http://voorbeeld.org/gemX#" ;              
                    nen3610:identificatie   "GP1Inwininfo" ;
                    imbor:a0a2e052-7b48-4c57-a302-a8113b51b6cd  "https://data.crow/imbor/def/9ec4228-7a32-41db-ac73-b80db66ea743";  # attribuut / "oppervlakte"
                    imbor:aa6bd718-64a3-4e06-b147-a45a58deee45  "2024-12-12"^^xsd:date;                                             # inwinningsdatum
                    imbor:203344f2-1f6f-4730-bb1f-7b81025cecfc  imbor-domeinwaarde:04e39342-d5cd-4360-8bc4-2165ce3cbeeb ;           # wijze van inwinnen / "Inmeting"
                    .

gemX:GP2Inwininfo   a   imbor:8ab0ac02-ee94-4086-9b14-d53ede3c4101 ;                                                                                 # Inwinning-informatie
                    nen3610:domein  "http://voorbeeld.org/gemX#" ;              
                    nen3610:identificatie   "GP2Inwininfo" ;
                    imbor:a0a2e052-7b48-4c57-a302-a8113b51b6cd  "https://data.crow/imbor/def/5b876aa9-3dc0-4aed-a843-6ce05ed9226a" ;                 # attribuut / "inhoudsklasse"
                    imbor:d811c5d0-8fad-4346-a818-39be74c59b0a  "https://data.crow.nl/imbor/id/domeinwaarden/0eeaaa8b-b6a7-40bb-9597-4e18fcf0c868" ; # domeinwaarde / "tot 5 m3"
                    imbor:aa6bd718-64a3-4e06-b147-a45a58deee45  "2024-12-12"^^xsd:date ;                                                             # inwinningsdatum
                    imbor:203344f2-1f6f-4730-bb1f-7b81025cecfc  imbor-domeinwaarde:04e39342-d5cd-4360-8bc4-2165ce3cbeeb ;                            # wijze van inwinnen / "Inmeting"
                    .
```
