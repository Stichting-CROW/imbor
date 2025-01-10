## Klassenstructuur

De modelleerregels in deze sectie betreffen ***interne regels***. Dit wil zeggen dat ze van toepassing zijn op het IMBOR zelf. In dit specifieke geval hebben ze betrekking op het maken en onderhouden van de klassenstructuur binnen de `IMBOR Ontologie`.

### Consistentie in overerving klasse structuur 1 (R0003)

Van toepassing op de `Klassenstructuur`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Elke klasse mag maar één keer aan dezelfde klasse als kind worden toegewezen. | 
| *ID* | R0003 (95e8d109-4deb-60f9-7e76-3d72ce43337e) |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
| {.index} | | 


### Consistentie in overerving klasse structuur 2 (R0004)

Van toepassing op de `Klassenstructuur`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Een objecttype mag niet van twee of meer verschillende klassen hetzelfde attribuut toegewezen krijgen. | 
| *ID* | R0004 (33a914e4-6c2f-2e37-02c7-36c8e4c99771) |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
| {.index} | | 


### Consistentie in overerving klasse structuur 1 (R0003)

Van toepassing op de `Klassenstructuur`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Elke klasse mag maar één keer aan dezelfde klasse als kind worden toegewezen. | 
| *ID* | R0003 *(95e8d109-4deb-60f9-7e76-3d72ce43337e)* |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDubbeleKlassenindeling |
| {.index} | | 


### Consistentie in overerving klasse structuur 2 (R0004)

Van toepassing op de `Klassenstructuur`, en valt binnen de categorie: `Model consistentie`

| | |
| ----- | ---- | 
| *Regel* | Een objecttype mag niet van twee of meer verschillende klassen hetzelfde attribuut toegewezen krijgen. | 
| *ID* | R0004 *(33a914e4-6c2f-2e37-02c7-36c8e4c99771)* |
| *Categorie* | Model consistentie
 |*Gerelateerd issue* |  |
 |*Controle query* | checkDubbeleObjecttypenAttributen |
| {.index} | | 


### Attributen zo hoog mogelijk in de hiërarchie (R0005)

Van toepassing op de `Klassenstructuur`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Attributen met een brede toepassing moeten op een zo abstract mogelijk niveau als zinnig is in de Klassenhiërarchie worden geïntroduceerd (dan wel als semantische relatie mogelijk zijn). | 
| *ID* | R0005 *(f9a1dde6-15ca-56f7-39f9-ff98b28f5c89)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* | https://github.com/Stichting-CROW/imbor/issues/1062 |
 |*Controle query* |  |
| {.index} | | 


### Indeling in TopConcepten (R0006)

Van toepassing op de `Klassenstructuur`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Elke klasse behalve de NEN 2660-2 klassen Object, FunctioneleEntiteit, TechnischeEntiteit, Activiteit en Geometrische representatie en de IMBOR-klassen Beheerd object en Gebiedsindeling heeft een ouderklasse. Oftewel elke klasse (de bovenstaand benoemde klassen uitgezonderd) moeten ook een ouder klasse hebben. | 
| *ID* | R0006 *(78f3dcb5-0ed5-1e83-00b3-bd97a8f4675f)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* |  |
 |*Controle query* | modChildHasParent; checkKlassenZonderOuder; checkObjecttypenAlsKind; checkObjecttypenKlassenindelingZonderMoeder |
| {.index} | | 


### Semantische expansieregel (R0007)

Van toepassing op de `Klassenstructuur`, en valt binnen de categorie: `Semantiek`

| | |
| ----- | ---- | 
| *Regel* | Een entiteit wordt dan en slechts dan aan de ontologie toegevoegd als daar: 1) een beargumenteerde aanleiding voor is gepresenteerd, 2) de aanleiding voldoende reden verschaft tot opname, 3) het onderwerp van de aanleiding niet al in de ontologie op een bepaalde manier is opgenomen (conflict met dit aspect kan leiden tot wijziging van de manier van opname). | 
| *ID* | R0007 *(7abfd2e4-1fb1-596b-5181-bd57f99e7fd7)* |
| *Categorie* | Semantiek
 |*Gerelateerd issue* |  |
 |*Controle query* |  |
| {.index} | | 


