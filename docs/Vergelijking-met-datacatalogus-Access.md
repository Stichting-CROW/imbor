# Vergelijking met datacatalogus (Access)

Bij de vertaling van de IMBOR datacatalogus (Acces) naar een publicatie in Linked Data, hebben we enkele ontwerpbeslissingen genomen (<https://github.com/Stichting-CROW/imbor/issues?q=is%3Aissue+label%3A%22design+decision%22+>). 
Beslissing #25, #11, #12, #13, #14 evalueren we hier. 

Deze ontwerpbeslissingen beperkten de te vertalen objecttypen, eigenschappen en vastewaardelijsten. 
Alleen wanneer die als informatiemodel IMBOR hadden, werden ze overgenomen. 
In Linked Data hoor je alleen zaken in je eigen beheer, te definiëren. 
Andere informatiestandaarden, zoals NEN 2767 of BGT/IMGeo, vallen daarbuiten. 

---

Om deze vergelijking herleidbaar te maken, wordt er gebruik gemaakt van SPARQL om antwoorden te krijgen op modelleerverschillen. 
De keuzes gemaakt in de bovengenoemde ontwerpbeslissingen zijn voornamelijk het bij vertaling filteren op informatiemodel. 
Daarom kunnen we gebruik maken van de output van de RML-transformaties zoals die in `data/rml` staan, dus voordat de filtering is gedaan.

## Aanwezige objecttypen (kunstwerken / imbor:OBB414)

Alle genoemde objecttypen komen zowel in de datacatalogus (Access) voor als in IMBOR in Linked Data-formaat. 

```sparql
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX imbor: <http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/objecttype/>
PREFIX imborp: <http://linkeddata.crow.nl/publication-v2/ns/crow/imbor/def/eigenschap/>
select * where { 
    [] imborp:ObjecttypeNiveau2 imbor:OBB414 ;
    	rdfs:label ?label
} order by str(?label)
```

