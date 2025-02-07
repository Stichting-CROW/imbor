## MIM addendum

Het MIM biedt een optie aan om een model in LinkedData uit te drukken. Het MIM uitgedrukt in LD houdt onder ander een ontologisch metamodel in. Dit betekent dat er voor elk van de modelelementen van het MIM een klasse en/of eigenschap gedefinieerd is in termen van [[rdf11-primer]], [[rdf-schema]], [[owl2-overview]] en [[shacl]]. De manier om dit te doen wordt beschreven in [MIM - Metamodel in LinkedData](https://docs.geostandaarden.nl/mim/def-st-mim-20201023/#metamodel-in-linked-data-ld). Middels deze specificatie is IMBOR zo ver mogelijk in MIM uitgedrukt. 

Dit is gedaan voor `imbor:Klasse`, `imbor:Attribuut`, `imbor:SemantischeRelatie`, `imbor:EnumeratieType` en `imbor:Domeinwaarde`. De onderlinge samenhang wordt niet in dit addendum genoemd omdat deze uit de IMBOR ontologie gehaald kan worden. De SHACL taalbinding van de NEN2660-2 lijkt op dezelfde manier als MIM dit doet. De enige toevoeging daarom is een verwijzing vanuit de `sh:PropertyShape` naar de `rdf:Property`, middels `mim:equivalent`. Dit is dubbel met `sh:path`, maar hierdoor wordt wel expliciet aangegeven dat MIM de relatie tussen het Objecttype en de Attribuutsoort toekent aan het Attribuutsoort. Verder zijn zo veel mogelijk (verplichte) MIM metagegevens ingevuld. 

De dataset is beschikbaar in een aparte graaf die, wanneer gewenst, bij de IMBOR ontologie kan worden ingeladen. 

