# Documentatie

Deze map bevat twee vormen van documentatie van de OTL.

- [index.html](https://stichting-crow.github.io/otl-bim-pro/index.html) bevat een proza en normatieve beschrijving van de ontologie in ReSpec. 
Gebruik dit document om te lezen over hoe de ontoloie is gemodelleerd in de data, wat de betekenis van de gemaakte keuzes is en voor een grafisch overzicht. 
Het bevat ook informatie die relateert aan de NTA 8035. 
Zie ook de [NTA issues](https://github.com/Stichting-CROW/otl-bim-pro/issues?utf8=%E2%9C%93&q=is%3Aissue+label%3Anta-8035) in deze repo. 

- [SPARQL-voorbeelden.ipynb](SPARQL-voorbeelden.ipynb) bevat voorbeelden van SPARQL-zoekvragen op de ontologie.
Deze voorbeelden tonen hoe je (de computer) kunt (laten) zoeken door de gegevens.
Bijvoorbeeld door het tonen van alle eigenschappen van een Brug. 
De voorbeelden kunnen ook gebruikt worden op een aangepaste dataset van bijvoorbeeld een provincie. 
Dan verifieer je ook of je aan het datamodel voldoet. 

_Deze voorbeeld queries zijn bedoeld om te lezen. Ze kunnen uiteraard eenvoudig gekopieerd worden naar een lokale SPARQL engine. Hieronder staat een beschrijving om dit met dit Jupyter notebook te doen. Maar in eerste instantie is deze pagina er voor read-only op Github_

---

De SPARQL-voorbeelden zijn ook zelf uit te voeren. 
Dan is ook een SPARQL-endpoint benodigd, die ook lokaal (op de eigen computer) kan draaien. Zodra de LinkedData versie van IMBOR gereleased wordt, kan de live endpoint gebruikt worden.

1. Een SPARQL-endpoint, bijvoorbeeld met [GraphDB](http://ontotext.com/).  
1. Python en Jupyter Notebook geïnstalleerd `$ pip install jupyterlab`. 
1. Een [SPARQL-kernel voor Jupyter](https://github.com/paulovn/sparql-kernel) `$ pip install sparqlkernel; jupyter sparqlkernel install --user`.
1. Activeer en open Jupyter `Jupyter notebook` en open "SPARQL-voorbeelden.ipynb". 
1. Vervang de bovenste coderegel met de URL van het gewenste SPARQL-endpoint.

---

Het Voorbeeld_Queries_op_turtle_file notebook werkt direct op de ttl file.

Let op dat de queries in dit geval subtiel anders zijn, namelijk met subClassOf* om te zorgen dat alle subklassen meegenomen worden.

Dit notebook kun je ook 'in de cloud' uitvoeren bij colab bijvoorbeeld. In dat geval hoef je niets op je eigen machine te installeren.


