## Actoren en rollen

***Gebaseerd op GitHub issue: [1258](https://github.com/Stichting-CROW/imbor/issues/1258) en [1276](https://github.com/Stichting-CROW/imbor/issues/1276)***

Vanaf IMBOR2025 is er een nieuw modelleerpatroon geïntroduceerd om relaties tussen klassen en actoren te modelleren, middels rollen. Deze constructie is ontleend uit de [[NEN2660-1]]. 
Omdat de [[NEN2660-2]] hier geen standaardoplossing voor biedt, is er een in IMBOR een modelleerconstructie die conform de [[NEN2660-1]] gemaakt is.
Het gaat hier om de introductie van `imbor:Actor` (als subklasse van `nen2660:PhysicalObject`) en `imbor:Rol`. `imbor:Actor` wordt met de relatie `imbor:speelt` verbonden met een `imbor:Rol`. Welke op zijn beurt met een `imbor:heeftBetrekkingOp` relatie verbonden is met een `nen3610:GeoObject` of `nen2660:InformatieObject`. 



Voor meer toelichting zie: [Techdoc | Actoren en rollen](https://docs.crow.nl/imbor/techdoc/#actoren-en-rollen)

### Toepassing actor en rol in IMBOR

>EXAMPLE
>De gemeente Rotterdam wil vastleggen dat de afdeling 'Vastgoed' de beheerder is van een specifiek gebouw. Om dit te doen dient de gemeente eerst in hun systeem aan te geven dat ze de klasse `Gemeente` uit de TOOI ontologie adopteren in hun systeem (als subklasse van IMBOR actor). Vervolgens wordt de URI van de gemeente Rotterdam zoals TOOI dat voorschrijft gebruikt. Hierna dient de gemeente Rotterdam de afdeling 'Vastgoed' aan het maken (`gemX:AfdelingVastgoed`) en onderdeel van de gemeente te maken door de `nen2660:hasPart` relatie te gebruiken. Middels de relatie `imbor:speelt` kan vervolgens aangegeven worden dat deze de rol van 'Beheerder' speelt door de beheerder klasse uit IMBOR te instantiëren (`gemX:Beheerder123`). Aan deze rol kan middels de `imbor:heeftBetrekkingOp` relatie een relatie gelegd worden naar het daadwerkelijke gebouw (`gemX:Gebouw1`). 

Dit is een voorbeelduitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/actor-rol.ttl" data-include-format="text"></code></pre>

### Combinatie met temporele aspecten

De reden dat rollen klassen zijn die geïnstanteerd kunnen worden is onder andere omdat er op het spelen van een rol vaak historie bijgehouden moet worden. Dit wordt toegelicht middels het volgende voorbeeld.

>EXAMPLE
>De gemeente Rotterdam wil vastleggen dat eerst de gemeente zelf beheerder was van de ondergrondse 'Afvalcontainer123', maar dat vanaf 22 mei 2025 de afvalbeheerder 'BakVol B.V.'  het beheer heeft overgenomen. In dit voorbeeld wordt gebruik gemaakt van de <a href="https://docs.crow.nl/imbor/best-practices/#optie-b-3-d-met-rdf-star">NEN3610 Temporele Aspecten - Optie B</a>.. 

Dit is een voorbeelduitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/actor-rol-temporeel.ttls" data-include-format="text"></code></pre>

