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

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix nen2660: <https://w3id.org/nen2660/def#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.
@prefix tooiGem: <https://identifier.overheid.nl/tooi/id/gemeente/>.
@prefix tooiont: <https://identifier.overheid.nl/tooi/def/ont/>.

tooiont:Gemeente rdfs:subClassOf imbor:5a60b993-5ff3-4b04-af83-c81bcb330d8d . 
# Gemeente Rotterdam neem tooiont:Gemeente op in hun systeem onder Publiekrechtelijk rechtspersoon

tooiGem:gm0599 a tooiont:Gemeente ; # gemeente Rotterdam
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "gm0599"^^xsd:string ;
    nen2660:hasPart gemX:AfdelingVastgoed ;
    .

gemX:AfdelingVastgoed   a imbor:5a60b993-5ff3-4b04-af83-c81bcb330d8d ; # Publiekrechtelijk rechtspersoon
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "AfdelingVastgoed"^^xsd:string ;
    imbor:speelt gemX:Beheerder123 ;
    .

gemX:Beheerder123 a imbor:8cb1bf27-67aa-47f5-a85c-b3b19e3f2ef2 ; # Beheerder
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "Beheerder123"^^xsd:string ;
    imbor:heeftBetrekkingOp gemX:Gebouw1 ;
    .

gemX:Gebouw1 a nen3610:Gebouw ;
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "Gebouw1"^^xsd:string ;
    imbor:4e721262-e6e2-41df-bb99-0b6693e32435  imbor-domeinwaarde:08fd8b4e-902f-4bce-8860-5bd5ad3dc28f ; # status / Vastgesteld
    imbor:16ce0662-115c-407f-88f8-948d587e04d6  imbor-domeinwaarde:f0f6fff4-1f2c-4724-b996-73fefdd84509 ; # aard / Vrijstaand
    .
```

### Combinatie met temporele aspecten

De reden dat rollen klassen zijn die geïnstanteerd kunnen worden is onder andere omdat er op het spelen van een rol vaak historie bijgehouden moet worden. Dit wordt toegelicht middels het volgende voorbeeld.

>EXAMPLE
>De gemeente Rotterdam wil vastleggen dat eerst de gemeente zelf beheerder was van de ondergrondse 'Afvalcontainer123', maar dat vanaf 22 mei 2025 de afvalbeheerder 'BakVol B.V.'  het beheer heeft overgenomen. In dit voorbeeld wordt gebruik gemaakt van de <a href="https://docs.crow.nl/imbor/best-practices/#optie-b-3-d-met-rdf-star">NEN3610 Temporele Aspecten - Optie B</a>.. 

Dit is een voorbeelduitwerking in [[Turtle]]:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix nen3610: <http://modellen.geostandaarden.nl/def/nen3610#>.
@prefix nen2660: <https://w3id.org/nen2660/def#>.
@prefix imbor: <https://data.crow.nl/imbor/def/>.
@prefix imbor-domeinwaarde: <https://data.crow.nl/imbor/id/domeinwaarden/>.
@prefix gemX: <http://voorbeeld.org/gemX#>.
@prefix gemX-regX: <http://voorbeeld.org/gemX-regX#> .
@prefix tooiGem: <https://identifier.overheid.nl/tooi/id/gemeente/>.
@prefix tooiont: <https://identifier.overheid.nl/tooi/def/ont/>.

tooiGem:gm0599 a tooiont:Gemeente ; # gemeente Rotterdam
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "gm0599"^^xsd:string ;
    imbor:speelt gemX:BeheerderAfvalContainer123 ;
    .
tooiGem:gm0599   imbor:speelt   gemX:BeheerderAfvalContainer123   {| nen3610:registratiegegevens   gemX-regX:1   |} .    

gemX:BakVolBV a imbor:e4e8e2bb-fd4f-4e42-878e-cbcac19c5105 ; # Privaatrechtelijk rechtspersoon
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "BakVolBV"^^xsd:string ;
    imbor:speelt gemX:BeheerderAfvalContainer123 ;
    .
gemX:BakVolBV   imbor:speelt   gemX:BeheerderAfvalContainer123   {| nen3610:registratiegegevens   gemX-regX:2   |} . 

gemX:BeheerderAfvalContainer123 a imbor:8cb1bf27-67aa-47f5-a85c-b3b19e3f2ef2 ; # Beheerder
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "BeheerderAfvalContainer123"^^xsd:string ;
    imbor:heeftBetrekkingOp gemX:Afvalcontainer123 ;
    .

gemX:Afvalcontainer123 a imbor:df3a7cac-4653-49b9-be3a-7fece9bf7a69 ;
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "Afvalcontainer123"^^xsd:string ;
    imbor:4e721262-e6e2-41df-bb99-0b6693e32435  imbor-domeinwaarde:08fd8b4e-902f-4bce-8860-5bd5ad3dc28f ; # status / Vastgesteld
    imbor:0da357fa-2f2a-4f16-aa3e-9dc8af1a187e  imbor-domeinwaarde:423ed74b-a124-4fbc-83f4-8d4c26a5f2ad ; # boven- of ondergronds / Ondergronds
    .

gemX-regX:1 a nen3610:Registratie ;
    nen3610:domein "http://voorbeeld.org/gemX-regX#" ;
    nen3610:identificatie "1"^^xsd:string ;
    nen3610:beginGeldigheid   "2006-06-02"^^xsd:date ;
    nen3610:eindGeldigheid    "2025-05-21"^^xsd:date ;
    .

gemX-regX:2 a nen3610:Registratie ;
    nen3610:domein "http://voorbeeld.org/gemX-regX#" ;
    nen3610:identificatie "2"^^xsd:string ;
    nen3610:beginGeldigheid   "2025-05-22"^^xsd:date ;
    .
```

