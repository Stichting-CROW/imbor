## Mapping

De modelleerregels in deze sectie betreffen ***interne regels***. Dit wil zeggen dat ze van toepassing zijn op het IMBOR zelf. In dit specifieke geval hebben ze betrekking op het maken en onderhouden van de relaties die IMBOR onderhoudt met andere standaarden. Dit wordt ook wel de 'mapping' of 'alignment' genoemd.

### Consistentie in uniciteit mappingen 1 (R0008)

Van toepassing op de `Mapping`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Elke domeinwaarde die voorkomt in refModel_Mapping wordt in refModel_Domeinwaarden één keer gedefinieerd. | 
| *ID* | R0008 (5e35bb09-8cb8-5521-106e-863bfe4f1f9b) |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
| {.index} | | 


### Consistentie in uniciteit mappingen 2 (R0009)

Van toepassing op de `Mapping`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Binnen elke afstemming met een ander informatiemodel figureert een specifieke combinatie uit IMBOR één en slechts één keer, dan wel niet. | 
| *ID* | R0009 (6a29938f-8ef4-8dc6-7966-820a9d283a6f) |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
| {.index} | | 


### Consistentie in uniciteit mappingen 3 (R0010)

Van toepassing op de `Mapping`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Voor alle mogelijke mappingobjecttypen met GWSW moet die mapping zijn gedefinieerd in refModel_Mapping. | 
| *ID* | R0010 (cec03a86-3316-4fba-6432-eb2a71f30154) |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
| {.index} | | 


### Elk ObjectType moet een relatie hebben met IMGeo (R0011)

Van toepassing op de `Mapping`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Elk ObjectType moet figureren in de mapping met IMGeo. | 
| *ID* | R0011 (7522c1a9-1f0a-3324-9b4e-6c96dcdc1d12) |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
| {.index} | | 


### Relateren andere standaarden geniet de voorkeur boven includeren (R0012)

Van toepassing op de `Mapping`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | IMBOR neemt in principe geen aspecten over uit andere standaarden, maar gaat uit van mappingen. Maar IMBOR neemt alleen aspecten van andere standaarden over als hier (i) voldoende reden voor is; of (ii) de standaard geen informatiemodel is waar IMBOR aan gerelateerd kan worden. | 
| *ID* | R0012 (244dddc6-3bb0-a77b-7bee-414f32245c14) |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/306 |
| {.index} | | 


