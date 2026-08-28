## InformatieObjecten (en Inwinning-informatie)

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

<pre><code class="turtle" data-include="data/inwinning-informatie.ttl" data-include-format="text"></code></pre>
