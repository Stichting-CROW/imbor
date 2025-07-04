## Ontologie

De modelleerregels in deze sectie betreffen **interne regels**. Dit wil zeggen dat ze van toepassing zijn op het IMBOR zelf. In dit specifieke geval hebben ze betrekking op het maken en onderhouden van de `IMBOR Ontologie` (ook wel `IMBOR Kernmodel` genoemd).

### Discriminator semantiek gaat voor attributen indeling (R0043)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Bij het indelen van (nieuwe) Objecttypen wordt eerst gekeken naar de semantiek (waar in de klassestructuur deze ingedeeld zouden moeten worden. Pas daarna moet gekeken worden of de juiste attributen/relaties erbij horen. |
| *ID*    | R0043 *(f5a17556-2d50-432d-a091-d7c7c80d8fc0)*                                                                                                                                                                               |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* |  |
| {.index} | | 


### Elke GUID is uniek (R0014)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                           |
|---------|---------------------------------------------------------------------------|
| *Regel* | Elke VocabulairGUID in imborVoc_Termen is uniek. Elke IMBORGUID is uniek. |
| *ID*    | R0014 *(24177f9a-a179-6dee-3dc2-f55c255f30ac)*                            |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDubbeleGUIDsTermen; checkDubbeleIMBORGUIDs; checkIMBORGUIDTermen; checkVocabulairGUIDTermen |
| {.index} | | 


### Enumeratietypen moeten hergebruik faciliteren (R0046)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                                                                                                                                                                  |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Waar mogelijk moeten Enumeratietypen hergebruikt worden. Waardelijsten moeten dus zo veel mogelijk samengesteld worden zodat ze zo veel mogelijk herbruikbaar zijn. Namen voor Enumeratietypen hoeven dus ook niet aan een conventie te voldoen. |
| *ID*    | R0046 *(a020d7d9-64be-517a-0ff9-6e4103bc060f)*                                                                                                                                                                                                   |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* |  |
| {.index} | | 


### Relatie tussen datatype en eenheid moet consistent zijn (R0029)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------|
| *Regel* | Als een attribuut het datatype xsd:decimal heeft, dan moet het attribuut ook een gedefinieerde eenheid hebben. |
| *ID*    | R0029 *(0b62bb2a-21d5-631a-634c-0330d6112258)*                                                                 |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkAttributenEnEenheden |
| {.index} | | 


### Relatie tussen een Attribuut en een Klasse is 1:n (R0015)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                          |
|---------|------------------------------------------------------------------------------------------|
| *Regel* | Elk attribuut moet aan minstens één klasse worden toegewezen, maar dit mag aan meerdere. |
| *ID*    | R0015 *(1e0bbf6a-1f60-a5ff-9037-85b0e05d88de)*                                           |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkAttributenZonderKlasse |
| {.index} | | 


### Relatie tussen een Domeinwaarde en een Enumeratietype is 1:n (R0017)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------|
| *Regel* | Elke Domeinwaarde moet aan minstens één Enumeratietype zijn toegewezen, maar dit mag aan meerdere. |
| *ID*    | R0017 *(302cccc9-98d0-3049-0d8d-cf4deafe627b)*                                                     |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDomeinwaardenZonderEnumeratie; checkEnumeratietypesZonderDomeinwaarden; checkEnumeratietypesMetDomeinwaarden |
| {.index} | | 


### Relatie tussen een Enumeratietype en een Domeinwaarde is 1:1 (R0018)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                         |
|---------|-----------------------------------------------------------------------------------------|
| *Regel* | Binnen hetzelfde Enumeratietype mag één domeinwaarde één en slechts één keer voorkomen. |
| *ID*    | R0018 *(f459906c-5b6a-559b-1548-cb5aeb323e99)*                                          |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDubbeleEnumeratieDomeinwaarden;  |
| {.index} | | 


### Relatie tussen een Klasse en een Attribuut is 1:1 (R0020)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                             |
|---------|-----------------------------------------------------------------------------|
| *Regel* | Een attribuut mag één en slechts één keer aan een klasse worden toegewezen. |
| *ID*    | R0020 *(04c47ac7-5a91-3929-0f56-a789a7809e88)*                              |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDubbeleKlassenAttributen |
| {.index} | | 


### Relatie tussen een ObjectType en een Vakdiscipline is 1:n (R0021)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                             |
|---------|-------------------------------------------------------------|
| *Regel* | Elk ObjectType is toegewezen aan minstens één Vakdiscipline |
| *ID*    | R0021 *(cd4fb6ba-6594-49c4-393f-4fcf10d0a307)*              |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkObjecttypenBinnenVakdiscipline; checkObjecttypenZonderVakdiscipline |
| {.index} | | 


### Relatie tussen een Vakdiscipline en een ObjectType is 1:1 (R0022)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                             |
|---------|---------------------------------------------------------------------------------------------|
| *Regel* | Binnen de mantel van één Vakdiscipline mag een ObjectType niet tweemaal of vaker voorkomen. |
| *ID*    | R0022 *(d6dd1d2c-a725-2266-5751-a4d0a659a54b)*                                              |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDubbeleVakdisciplineObjecttypen |
| {.index} | | 


### Relatie tussen IMBOR Concept en IMBOR Term is 1:n (R0023)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                               |
|---------|-------------------------------------------------------------------------------|
| *Regel* | Elk Klasse moet minimaal één relatie hebben naar een term uit de vocabulaire. |
| *ID*    | R0023 *(f90e3a6c-24c0-303a-4766-51ecae8a25a5)*                                |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkKlassenDieOntbreken; checkObjecttypenZonderKlasse |
| {.index} | | 


### Relatie tussen ObjectType een GM Klassen is 1:n (R0024)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                                                                         |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Aan elk ObjectType wordt minstens één geometrische representatie klasse gerelateerd, maar dit mogen er meerdere zijn (eentje is met multipliciteit 1:1) |
| *ID*    | R0024 *(994c9e3e-0318-50ce-4502-2173f6389e70)*                                                                                                          |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkObjecttypenGMDefault |
| {.index} | | 


### Semantische relaties worden alleen in dominante richting opgenomen (R0025)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                                                                                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Elke semantische relatie van de vorm aRb wordt maar één keer opgenomen, waarbij het omgekeerde, d.w.z. bRa niet als equivalent wordt beschouwd. (Semiotisch anders interpretabel vs. machineleesbaar equivalent). Vandaar dat de inverse dus ook expliciet opgenomen mag worden, als het nuttig is. |
| *ID*    | R0025 *(e976d9a8-2f8c-60ea-2463-764cc4587ecd)*                                                                                                                                                                                                                                                      |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDubbeleSemantischeRelaties |
| {.index} | | 


### Temporele aspecten worden gemodelleerd volgens de NEN3610 (R0045)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Alles met betrekking tot datums en tijdstippen zou volgens de NEN3610 temporele aspecten gemodelleerd moeten worden, tenzij. |
| *ID*    | R0045 *(b586e279-9956-8a52-0745-a336bdd8958f)*                                                                               |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* |  |
| {.index} | | 


### Wanneer het Attribuut 'Verschijningsvorm' gebruikt wordt, moet er een 1;1 zijn naar een corresponderend Enumeratietype (R0028)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Model consistentie`

|         |                                                                                                                                                                                                                                                                       |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Voor alle ObjectTypen met het attribuut Verschijningsvorm geldt dat er een Enumeratietype van de vorm [Objecttype]Verschijningsvorm moet bestaan en aan de combinatie van KlasseAttribuut is gekoppeld waarvoor geldt dat: Klasse = [Objecttype] en Attribuut = Type. |
| *ID*    | R0028 *(74296337-106b-2d1e-61a2-2fe747b03f6a)*                                                                                                                                                                                                                        |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkObjecttypenMetType |
| {.index} | | 


### Consistent toepassen van topmodellen (R0030)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Semantiek`

|         |                                                                                                                                                                                                                                                                                                                   |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Als IMBOR een modelleringsaspect van een bovenliggend model overneemt (NEN 3610; NEN 2660-2) dan is het streven datgene niet ook nog op andere manieren te modelleren. Bijvoorbeeld NEN 3610 temporele aspecten en hoe allerlei IMBOR-attributen die een temporeel aspect vastleggen daar een overlap mee hebben. |
| *ID*    | R0030 *(643b7868-0c64-0c3d-9926-8b1bc2da832e)*                                                                                                                                                                                                                                                                    |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/1075 |
 |*Controle query* |  |
| {.index} | | 


### Semantische relaties genieten de voorkeur boven Attributen 1 (R0031)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Semantiek`

|         |                                                                                                                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Een object in de openbare ruimte wordt wanneer mogelijk als ObjectType gemodelleerd; attributen die een decompositie verbergen moeten worden vermeden. Synoniemen mogen niet als separate ObjectTypen bestaan. |
| *ID*    | R0031 *(51da3c18-784e-363a-6f00-4a6d68404bb2)*                                                                                                                                                                 |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/984 |
 |*Controle query* |  |
| {.index} | | 


### Toevoegen van nieuwe Klassen (en Objecttypen) 1 (R0032)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Semantiek`

|         |                                                                                                                                                                                                                                                                                                                                          |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Er worden alleen Typen toegevoegd aan de IMBOR-taxonomie als: 1) Het Type niet uit te drukken valt m.b.v. een bestaand attribuut; 2) Het Type logischerwijs in meer dan één geval voorkomt in de werkelijkheid; 3) Het Type binnen de scope van IMBOR valt; en 4) De toepassing van het Type niet te niche is binnen de scope van IMBOR. |
| *ID*    | R0032 *(117825ad-3435-05e3-4af6-59b374ec7932)*                                                                                                                                                                                                                                                                                           |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/976 |
 |*Controle query* |  |
| {.index} | | 


### Toevoegen van nieuwe Klassen (en Objecttypen) 2 (R0033)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Semantiek`

|         |                                                                                                                                                                                                                                                                                                             |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Een Type wordt alleen aan een ObjectType toegevoegd als er (i) geen beter ObjectType denkbaar is om het Type toe te voegen; (ii) het Type niet beter zelf als ObjectType gemodelleerd kan worden; en (iii) er geen attribuut beschikbaar is voor een volwaardige expressie voor de semantiek van het Type.’ |
| *ID*    | R0033 *(df512f1d-8d42-87a0-419f-50ff71163421)*                                                                                                                                                                                                                                                              |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/152  |
 |*Controle query* |  |
| {.index} | | 


### Semantische relaties genieten de voorkeur boven Attributen 2 (R0043)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Semantiek`

|         |                                                                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Wanneer gegevens afgeleidt kunnen worden van de geometrie (bv. Gemeente, Gebiedsindeling e.d.) wordt dit niet in een Attribuut gedaan, maar middels een semantische relatie. |
| *ID*    | R0043 *(f944afcf-5783-3ff5-9da2-3d9a89de0bd2)*                                                                                                                               |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/1101 |
 |*Controle query* |  |
| {.index} | | 


### ObjectTypen hoeven niet persé de bladeren van de hierarchie te zijn (R0044)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Semantiek`

|         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Binnen IMBOR laten wij het principe los dat alleen bladeren van de hiërarchie Objecttypen (lees: instantiërbaar) zijn.  Daar staat tegenover dat wij zelf gaan bepalen welke niveau in de hiërarchie wij Objecttypen (Concrete klassen) vinden.  Hierdoor kan het dan voorkomen dat wij subklassen introduceren (onder objecttypen), die niet Objectentypen zijn (dus niet instantiërbare abstracte klassen). En dat er ObjectTypen onder ObjectTypen hangen Dit houdt onder andere in dat wij de externe soorten boom (zoals die van GWSW) 1-op-1 overnemen; Maar wij vervolgens aangeven welke volgens de IMBOR context Objecttypen zijn |
| *ID*    | R0044 *(1e2f7efb-66e3-3b88-3b44-e539fb234c04)*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/1432 |
 |*Controle query* |  |
| {.index} | | 


### Afleidbare attributen worden niet in IMBOR opgenomen.  (R0045)

Van toepassing op de `Ontologie`, en valt binnen de categorie: `Semantiek`

|         |                                                                                                                                                                                                                                                                 |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Regel* | Attributen die afleidbaar zijn door GIS acties of afleidingen op basis van externe datasets worden niet in IMBOR opgenomen. Om IMBOR klein en zuiver te houden worden deze niet toegestaan. Het gaat bijvoorbeeld om gebiedstype, grondsoort, wijk, buurt, etc. |
| *ID*    | R0045 *(1c6ed2da-9fce-4080-985b-502bf0298712)*                                                                                                                                                                                                                  |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/1101 |
 |*Controle query* |  |
| {.index} | | 


