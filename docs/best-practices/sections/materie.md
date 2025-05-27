## Materie

***Gebaseerd op GitHub issue: [1576](https://github.com/Stichting-CROW/imbor/issues/1576) en [1582](https://github.com/Stichting-CROW/imbor/issues/1582)***

Vóór IMBOR2022 werden materialen als attributen van Objecttypen vastgelegd. Binnen de [[NEN2660-2]] is hiervoor een modelleerconstructie gegeven die IMBOR nu toepast. Er kan een relatie `bestaatUit` gelegd worden tussen de klasse `ReeelObject` en de klasse `Materie`. Dit betekent dat materialen dus ook een klasse zijn en ook als zodanig gemodelleerd zijn. Binnen IMBOR zijn allemaal soorten materialen opgenomen en met relaties verbonden aan ObjectTypen. Deze lijst is op basis van 'expert judgement' samengesteld door de jaren heen.

>ADVISEMENT
>Ter verduidelijking: IMBOR limiteert *niet* welke relaties er tussen een `FysiekObject` en een `Materie` gelegd kunnen worden. We geven alleen 'voorstellen'. 

Dit modelleerpatroon gaat er vanuit de materialen dus *ook* geïnstanteerd worden en middels de relatie `nen2660:consistsOf` aan een `ReeelObject` of subklasse daarvan gekoppeld worden. 

Zie ook: [Techdoc | Materie](https://docs.crow.nl/imbor/techdoc/#materie)

### Toepassing materie IMBOR

>EXAMPLE
>Gemeente X wil vastleggen dat een bepaalde lichtmast uit een stalen en hardhouten gedeelte bestaat. Om dit te doen dient de gemeente in hun systeem een lichtmast (`LM123`) vast te leggen van het type IMBOR Lichtmast. Vervolgens moeten aangegeven worden middels de `nen2660:hasPart` dat deze deels hardhout en deels staal is. Dit kan gedaan worden door instantaties van de IMBOR klassen 'Hardhout' en 'Staal te maken (`gemX:Paal123_hardhout` en `gemX:Paal123_staal`) en deze middels de `nen2660:hasPart` aan de `LM123` te linken. De gemeente wil ten behoeve van het materialenpaspoort aangegeven of het hergebruikte materialen betreft, wat het gewicht van het materiaal is en wat het hoofdmateriaal van de lichtmast is. Per materie worden zodoende de attributen `percentage` en `gewicht` aangegeven. Uit de percentages kan afgeleid worden dat het hoofdmateriaal 'hardhout' is. Als laatste wordt middels het attribuut `materiefase` aangegeven dat het hardhout één keer eerder gebruikt is (`Fase 1`) en het staal nieuw is (`Fase 0`).   

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

gemX:LM123 a imbor:f6a897de-0abe-4fe0-95ed-96cf58c84ae8 ; # Paal
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "LM123"^^xsd:string ;
    imbor:e3e112b3-e46f-45c4-b2c9-b152e6f805a1  imbor-domeinwaarde:e5d5a58c-bb19-4d49-8bf0-d1ea48a5487e ; # verschijningsvorm / Lichtmast
    nen2660:consistsOf gemX:Paal123_hardhout, gemX:Paal123_staal ;
    .

gemX:Paal123_hardhout a imbor:dfe3117e-acb1-4d65-ba55-80b75f86c3c0 ; # Hardhout
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "Paal123_hardhout"^^xsd:string ;
    imbor:400fc25d-575d-43dc-a7ae-217b42375a85 "60"^^xsd:decimal ; # percentage / 60% hardhout
    imbor:1e36586b-e235-4d11-9430-abeee4a70821 "70,12"^^xsd:decimal ; # gewicht / 70,12 kg
    imbor:034dd69a-cba8-4552-ad9f-b743aa30bc8a imbor-domeinwaarde:b0ec993d-b6ed-437f-87e8-65e415f19592 ; # materiefase / Fase 1
    .

gemX:Paal123_staal a imbor:ce8aa2ed-1ec2-4ba9-adda-2fdb57dd39d9 ; # Staal
    nen3610:domein "http://voorbeeld.org/gemX#" ;
    nen3610:identificatie "Paal123_hardhout"^^xsd:string ;
    imbor:400fc25d-575d-43dc-a7ae-217b42375a85 "40"^^xsd:decimal ; # percentage / 40% staal
    imbor:1e36586b-e235-4d11-9430-abeee4a70821 "120,55"^^xsd:decimal ; # gewicht / 120,55 kg
    imbor:034dd69a-cba8-4552-ad9f-b743aa30bc8a imbor-domeinwaarde:64085404-a5ee-438a-b0bf-9bff70dd401f ; # materiefase / Fase 0
    .
```
