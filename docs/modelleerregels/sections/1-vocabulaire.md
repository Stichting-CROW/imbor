## Vocabulaire

De modelleerregels in deze sectie betreffen ***interne regels***. Dit wil zeggen dat ze van toepassing zijn op het IMBOR zelf. In dit specifieke geval hebben ze betrekking op het maken en onderhouden van de `IMBOR Vocabulaire`.

### Elke term heeft een unieke definitie binnen een collectie (R0034)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Binnen een collectie van termen is een term uniek, dat wil zeggen, er is maar één definitie van de term en de term is maar één keer binnen de collectie vastgelegd. Twee niet identieke termen mogen niet één en dezelfde definitie hebben | 
| *ID* | R0034 *(9831d4d6-791e-0b82-1456-40bb877a7ea1)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/971  |
 |*Controle query* | checkDomeinwaarden; checkDubbeleKlassen; checkDubbeleTermen; checkObjecttypen; checkObjecttypen-ook-als-domeinwaarden; checkDubbeleTermenEnDefinities, checkAttributen |
| {.index} | | 


### Grammaticale correctheid van woorden en teksten (R0035)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Alle tekst in IMBOR moet grammaticaal correct zijn en goed gespeld, tenzij hier vanwege termen die buiten duidelijke grammaticale regels vallen van moet worden afgeweken. | 
| *ID* | R0035 *(7e49567b-8c09-3540-4378-52a05071041f)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/1074 |
 |*Controle query* |  |
| {.index} | | 


### Hergebruik van termen en definities uit andere modellen (R0036)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Openlijke tegenspraak met andere informatiemodellen in definities moet worden vermeden, tenzij de definitie uit het beschouwde gerelateerde informatiemodel niet past in de IMBOR context. | 
| *ID* | R0036 *(d1f9b4cc-7a93-8244-286a-e45dd26a73e9)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/213; https://github.com/Stichting-CROW/imbor/issues/334 |
 |*Controle query* |  |
| {.index} | | 


### Naamgeving Attributen 1 (R0037)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | De termen die Attributen representeren worden volgens de NEN2660-2 conventies beschreven. In dit geval geldt dat deze lower case zijn, spaties mogen bevatten en in enkelvoud beschreven worden. En daarnaast voldoende beschrijvend moeten zijn. | 
| *ID* | R0037 *(c86545f1-25f4-9264-6ce5-fbca43af1308)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/962 |
 |*Controle query* |  |
| {.index} | | 


### Naamgeving Attributen 2 (R0044)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Termen (vooral met betrekking tot attributen) moeten aansluiten bij de definitie en daarmee dus niet te algemeen zijn | 
| *ID* | R0044 *(db35e4f5-5c31-020c-8596-8d31a35f4f1b)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/1006  |
 |*Controle query* |  |
| {.index} | | 


### Naamgeving Domeinwaarden (R0038)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | De termen die Domeinwaarden representeren worden volgens de NEN2660-2 conventies beschreven. In dit geval geldt dat deze beginnen met een hoofdletter, spaties mogen bevatten en in enkelvoud beschreven worden. | 
| *ID* | R0038 *(d3182e34-97d8-2f33-1d41-1f33252a5def)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* |  |
 |*Controle query* |  |
| {.index} | | 


### Naamgeving Klassen (R0039)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | De termen die Klassen representeren (dus ook: Objecttype, InformatieObjecten, Materie, Functies, etc.) worden volgens de NEN2660-2 conventies beschreven. In dit geval geldt dat deze beginnen met een hoofdletter, spaties mogen bevatten en in enkelvoud beschreven worden. En daarnaast voldoende beschrijvend moeten zijn. | 
| *ID* | R0039 *(b9439077-2dc8-931f-54d7-9ed77ed41a94)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* |  |
 |*Controle query* |  |
| {.index} | | 


### Naamgeving Relaties (R0040)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | De termen die Relaties representeren worden volgens de NEN2660-2 conventies beschreven. In dit geval geldt dat deze lower case zijn, spaties mogen bevatten en in enkelvoud beschreven worden. En daarnaast voldoende beschrijvend moeten zijn. De enige relaties de gebruikt worden zijn uit de NEN2660-2, deze zijn vertaald in IMBOR naar NL. | 
| *ID* | R0040 *(f9f886bb-9456-6402-03e5-09485d2b9581)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* |  |
 |*Controle query* |  |
| {.index} | | 


### Overlap in semantiek moet vermeden worden 1 (R0041)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Hergebruik van elementen (bijvoorbeeld door toevoegen van synoniemen geniet de voorkeur. Er mogen geen twee verschillende terminologisch verschillende (term, dan wel definitie) attributen/ObjectTypen/Domeinwaarden bestaan om één en hetzelfde gegeven vast te leggen. Er mogen geen terminologisch verschillende termen semantische overlap hebben in hun definities die tot verwarring leidt.  | 
| *ID* | R0041 *(0567d53d-9d7c-31df-867f-b2d49d4e9e10)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/332; https://github.com/Stichting-CROW/imbor/issues/1023 |
 |*Controle query* |  |
| {.index} | | 


### Overlap in semantiek moet vermeden worden 2 (R0042)

Van toepassing op de `Vocabulaire`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Semantische conflicten tussen mogelijke invullingen van attributen en domeinwaarden en de definitie van een ObjectType of Type mogen niet voorkomen. Als ze wel voorkomen, moeten ze m.b.v. een best practice toegelicht worden. | 
| *ID* | R0042 *(1b7a4464-0daf-2fce-5b1e-f31254a799ca)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/882  |
 |*Controle query* |  |
| {.index} | | 


