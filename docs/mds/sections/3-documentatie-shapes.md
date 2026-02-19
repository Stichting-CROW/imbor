### Doel

Deze documentatie beschrijft hoe je vanuit een Excel-bestand met objecttypen en attributen (de zogenaamde Minimale Dataset IMBOR) komt tot een set SHACL shapes. Die shapes kun je vervolgens gebruiken om met <a href="https://jena.apache.org/documentation/shacl/">Apache Jena</a> (als SHACL-engine) te valideren of aangeleverde data aan de minimale eisen voldoet.

##### Wat heb je nodig?

Je werkt met drie bronbestanden:

- Een Excel-bestand met de Minimale Dataset. Dit bevat rijen met telkens een combinatie van een objecttype (bijvoorbeeld "Boom"), een attribuut (bijvoorbeeld "Hoogte") en een kolom die aangeeft of dat attribuut verplicht is: Ja of Nee.

| Objecttype | Attribuut                    | MinimaleDataset (Ja/Nee) |
| ---------- | ---------------------------- | ------------------------ |
| Boom       | identificatie                | Ja                       |
| Boom       | domein                       | Ja                       |
| Boom       | aanlegjaar                   | Ja                       |
| Boom       | status                       | Ja                       |
| Boom       | geometrie                    | Ja                       |
| Boom       | identificatie geovoorziening | Ja                       |
| Boom       | naam                         | Nee                      |
| Boom       | nummer                       | Ja                       |
| Boom       | beheerafspraak               | Nee                      |
| Boom       | boomtype                     | Ja                       |
| Boom       | kiemjaar (boom)              | Nee                      |
| Boom       | beoogde opkroonhoogte        | Ja                       |

- Een CSV-bestand met objecttypen. Dit bevat per objecttype de naam én de bijbehorende URI, zoals die in IMBOR is vastgelegd.
- Een CSV-bestand met attributen. Zelfde opzet als hierboven, maar dan voor attributen: per attribuut de naam en de URI.

Zie [4-SPARQL-query-MDS.md] voor een instructie over het schrijven van een SPARQL query om deze CSV-bestanden te extraheren uit IMBOR.

### Stappen van Excel naar SHACL

##### Stap 1 — Namen normaliseren

De namen van objecttypen en attributen staan in drie losse bestanden die onafhankelijk van elkaar zijn opgesteld. Om ze betrouwbaar aan elkaar te koppelen, worden alle namen eerst genormaliseerd: hoofdletters worden kleine letters, en overbodige spaties worden verwijderd. Zo voorkom je dat "Boom" en "boom" als twee verschillende dingen worden gezien.

##### Stap 2 — URI's koppelen aan de Minimale Dataset

Het Excel-bestand met de Minimale Dataset bevat (waarschijnlijk) alleen namen, geen URI's. Die URI's zijn echter essentieel voor de SHACL shapes, want SHACL werkt op basis van linked data. Het zal waarschijnlijk zijn dat degenen die de Minimale Dataset gemaakt hebben (nog) geen gebruik maken van linked data. Daarom wordt elke objecttypenaam uit het Excel-bestand opgezocht in het objecttypen-CSV, en elke attribuutnaam in het attributen-CSV. Zo krijgt iedere rij in de dataset er twee URI's bij: één voor het objecttype en één voor het attribuut. Rijen waarvoor geen URI gevonden kan worden, worden gesignaleerd als foutmelding.

##### Stap 3 — Filteren op verplichte attributen

Niet alle combinaties in het Excel-bestand zijn verplicht. Alleen de rijen waar de kolom MinimaleDataset de waarde Ja heeft, worden meegenomen voor de SHACL shapes. De rest wordt genegeerd.

##### Stap 4 — Groeperen per objecttype

De gefilterde rijen worden gegroepeerd op objecttype. Per objecttype ontstaat zo een lijstje van attributen die minimaal aanwezig moeten zijn. Bijvoorbeeld: voor het objecttype "Boom" zijn de attributen "Hoogte", "Soortnaam" en "Plantjaar" verplicht.

##### Stap 5 — SHACL NodeShape aanmaken per objecttype

Per objecttype wordt een zogenaamde NodeShape aangemaakt. Dit is het centrale SHACL-element dat zegt: "Voor alle objecten van dit type gelden de volgende regels." De NodeShape bevat twee dingen: een verwijzing naar het objecttype (via sh:targetClass en de URI uit stap 2), en een verwijzing naar elke bijbehorende attribuutregel (de PropertyShapes uit de volgende stap). Elke NodeShape krijgt een uniek identificatienummer (een UUID) onder het mds_imbor:-prefix.

##### Stap 6 — SHACL PropertyShape aanmaken per attribuut

Voor elk verplicht attribuut binnen een objecttype wordt een PropertyShape aangemaakt. Deze shape drukt één simpele regel uit: "Dit attribuut moet minstens één keer voorkomen." Dat gebeurt met sh:minCount 1 in combinatie met sh:path, die verwijst naar de URI van het attribuut. Ook elke PropertyShape krijgt een eigen UUID als identificatie.

##### Stap 7 — Prefixes toevoegen en opslaan als Turtle-bestand

Bovenaan het bestand worden de standaard prefixes geplaatst. Dat zijn afkortingen voor veelgebruikte URI's (zoals imbor: voor IMBOR-definities en sh: voor SHACL-termen), zodat het bestand leesbaar en compact blijft. Het resultaat wordt opgeslagen als een Turtle-bestand (.ttl), het gangbare formaat voor linked data.

##### Hoe ziet het resultaat eruit?

Het Turtle-bestand bevat per objecttype een blok dat er conceptueel zo uitziet:

Een NodeShape die zegt: "Ik richt me op alle objecten van type X", gevolgd door verwijzingen naar één of meer PropertyShapes. Elke PropertyShape zegt: "Het attribuut Y moet minimaal één keer aanwezig zijn."

Concreet betekent dit dat als een object van type "Boom" wordt aangeleverd zonder het attribuut "Hoogte", de SHACL-validatie een foutmelding geeft.

### Valideren met Apache Jena

Om de gegenereerde shapes daadwerkelijk te gebruiken voor validatie, zetten we Apache Jena in als SHACL-engine. Jena kan het shapes-bestand inlezen samen met een databestand en rapporteert vervolgens welke objecten niet voldoen aan de gestelde minimale eisen. Het validatierapport geeft per overtreding aan welk object het betreft, welk attribuut ontbreekt, en bij welke shape de fout hoort.
We hebben gekozen om met Apache Jena te werken <a href="https://jena.apache.org/documentation/shacl/">Apache Jena</a> omdat deze engine het snelst is, een andere optie was <a href="https://github.com/RDFLib/pySHACL/">PySHACL</a>.

### Samenvatting van de keten

De volledige keten is: bronbestanden voorbereiden (Excel + twee CSV's) → namen normaliseren → URI's koppelen → filteren op verplichte attributen → groeperen per objecttype → per objecttype een NodeShape genereren → per verplicht attribuut een PropertyShape genereren → opslaan als Turtle → valideren met Apache Jena.
