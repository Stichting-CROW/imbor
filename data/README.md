# Data

IMBOR in Linked data-formaat conformeert zich aan de NEN NTA 8035. 
In [imbor.shapes.ttl][3] staan de expliciete modelleerkeuzes in Turtle-formaat. Er zijn uiteraard ook impliciete modelleerkeuzes (niet direct uit de data te halen), deze kunnen geraadpleegd worden in de [ReSpec][4].

**IMBOR zelf wordt niet openbaar gedistribueerd.**

De transformatieregels zijn wel gepubliceerd en terug te vinden in de submap [transformaties][5].

## Zelf een aangepaste transformatie uitvoeren

> Deze informatie is bedoeld voor geavanceerde gebruikers,
> bedreven in het gebruik van de commandoprompt evenals het aanpassen van systeemomgevingsvariabelen (`PATH` etc.).
> CROW verleent geen ondersteuning of hierop en wijst aansprakelijkheid af.

De transformatieregels werken op een CSV-export van _IMBOR in Access-formaat_, 
[verkrijgbaar bij CROW][1].
De regels werken op een map `data/externe-bronnen/` waarin per tabel een CSV-bestand staat, vernoemd naar de tabelnaam.

### RML en SPARQL Update

De transformatieregels zijn geschreven in [RML](http://rml.io/).
In de repo [rmlio/rmlmapper-java][2] staat beschreven hoe dit moet worden geïnstalleerd.

```
$ java -jar rmlmapper-java --mapping data/rml/rules.rml.ttl --output data/temp/imbor.ttl --serialization turtle
```

Vervolgens worden lokaal SPARQL Updates uitgevoerd op het door RML geconverteerde bestand. 
Deze kunnen door allerhande SPARQL systemen worden uitgevoerd.
Bijvoorbeeld [Apache Jena][jena].

```
$ update --data data/temp/imbor.nq --update "data/transformaties/150 Splits altLabel.rq" --dump
```

### SHACL

Met SHACL wordt beschreven hoe gegevens eruit moeten zien. 
Dit kan ook met [Apache Jena][jena] worden gecontroleerd.

```
$ shacl validate --shapes datamode.shapes.ttl --data imbor-ld.objecten.ttl
```

[1]: https://www.crow.nl/online-kennis-tools/kennismodule-imbor-en-imwv-plus
[2]: https://github.com/RMLio/rmlmapper-java
[jena]: http://jena.apache.org/
[3]: https://github.com/Stichting-CROW/imbor/blob/master/data/imbor.shapes.ttl
[4]: https://stichting-crow.github.io/imbor/
[5]: https://github.com/Stichting-CROW/imbor/tree/master/data/transformaties