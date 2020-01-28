# Documentatie

Deze map bevat documentatie over IMBOR in Linked data-formaat.

- [index.html](https://stichting-crow.github.io/otl-bim-pro/index.html) bevat een proza en normatieve beschrijving van de OTL in ReSpec. 
Gebruik dit document om te lezen over hoe de OTL is gemodelleerd in de data, wat de betekenis van de gemaakte keuzes is en voor een grafisch overzicht van de OTL. 
Het bevat ook informatie die relateert aan de NTA 8035. 
Zie ook de [NTA issues](https://github.com/Stichting-CROW/otl-bim-pro/issues?utf8=%E2%9C%93&q=is%3Aissue+label%3Anta-8035) in deze repo. 

- [SPARQL-voorbeelden.ipynb](SPARQL-voorbeelden.ipynb) bevat voorbeelden van SPARQL-zoekvragen.
Deze voorbeelden tonen hoe je (de computer) kunt (laten) zoeken door de OTL-gegevens.
Bijvoorbeeld door het tonen van alle eigenschappen van een Hefbrug. 
De voorbeelden kunnen ook gebruikt worden op een aangepaste dataset van bijvoorbeeld een provincie. 
Dan verifieer je ook of je aan het OTL-datamodel voldoet. 

- [`Mapping OTL BIM Pro--BGT-IMGeo.tsv`](Mapping OTL BIM Pro--BGT-IMGeo.tsv) beschrijft het koppelvlak tussen OTL BIM Pro-objecten, attributen en domeinwaardes en BGT|IMGeo-objecten, attributen en domeinwaardes. Gebruik deze tabel om exporten naar BGT (geovoorziening) vanuit beheerssoftware die volgens OTL BIM Pro werkt. Het is gebaseerd op de IMBOR-Access-tabel `X_ObjecttypeRelaties`. 

- [`Mapping IMBOR 2 UCUM.csv`](Mapping IMBOR 2 UCUM.csv) beschrijft de eenheden uit IMBOR (tabel `X_Eenheden`) en koppelt ze aan [UCUM / CDT](https://ci.mines-stetienne.fr/lindt/v2/custom_datatypes.html)- en [QUDT](http://qudt.org/)-Linked data-eenheids-datatypes.  

- [`Datamodel - BIM PRo OTL.drawio`](Datamodel%20-%20BIM%20PRo%20OTL.drawio) toont het datamodel van OTL BIM Pro in het formaat van het online tekenprogramma [draw.io](http://draw.io/).

---

De SPARQL-voorbeelden zijn ook zelf uit te voeren. 
Dan is ook een SPARQL-endpoint benodigd, die ook lokaal (op de eigen computer) kan draaien.

1. Een SPARQL-endpoint, bijvoorbeeld met [GraphDB](http://ontotext.com/).  
1. Python en Juypter Notebook geïnstalleerd `$ pip install jupyterlab`. 
1. Een [SPARQL-kernel voor Jupyter](https://github.com/paulovn/sparql-kernel) `$ pip install sparqlkernel; jupyter sparqlkernel install --user`.
1. Activeer en open Jupyter `jupyter notebook` en open "SPARQL-voorbeelden.ipynb". 
1. Vervang de bovenste coderegel met de URL van het gewenste SPARQL-endpoint.
