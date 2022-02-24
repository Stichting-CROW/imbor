Deze documentatie is opgedeeld in de verschillende metamodellagen die te onderscheiden vallen bij het toepassen van
LinkedData, zoals de NTA8035 dit specificeert.

Het M2 niveau (zoals geschetst in onderstaande plaat) betreft het Conceptueel Meta Model (CMM) van de NTA8035,
inclusief de taalbinding van de NTA8035 in RDF(S)/OWL en SHACL.
Hierover wordt niets expliciet beschreven, maar verwijzen we naar de NTA8035.
De M1 laag bestaat uit twee lagen namelijk M1 generiek en M1 specifiek.
_M1 generiek_ betreft het Conceptueel Top Level Model uit de NTA8035.
_M1 specifiek_ betreft het Conceptuele Domeinmodel, in dit geval IMBOR.
Deze laag bevat eigenlijk alle getransformeerde IMBOR informatie.

Als laatste wordt de M0 laag beschreven, hierin wordt uitleg gegeven van een (voorbeeld)dataset binnen van de IMBOR
ontologie. Elke laag sluit zich aan op de bovenliggende laag. Elke bovenliggende laag is het gegevensmodel voor de
onderliggende laag, en daarmee is elke onderliggende laag een gegevensset van een bovenliggende laag.

<figure>

![](img/M-lagen%20visualisatie%20IMBOR.png)

<figcaption>
Lagen NTA 8035 en IMBOR in piramidevorm.
Scope NTA 8035: M2 'Conceptueel metamodel (CMM)', M1 generiek 'Conceptueel toplevelmodel (CM)'.
Scope IMBOR: M1 generiek 'Conceptueel topolevelmodel (CM)', M1 specifiek 'Conceptuele domeinmodellen'.
M0 bevat gegevens.
</figcaption>
</figure>
