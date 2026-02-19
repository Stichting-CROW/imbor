## SHACL

<a href="https://www.w3.org/TR/shacl/">SHACL</a> is een krachtige W3C standaard om data te valideren. Binnen IMBOR wordt deze gebruikt om enkele beperkingen op te leggen. Dit wordt zowel bij semantische relaties als bij klasse-attribuut combinaties gebruikt.

### SHACL: structuur met (te valideren) regels

SHACL (Shapes Constraint Language) is geen uitbreiding van OWL, maar een aparte taal voor datavalidatie die eveneens voortbouwt op RDF en RDFS. Waar OWL zich richt op wat logisch mogelijk is, controleert SHACL of data daadwerkelijk aan regels voldoet.  
SHACL introduceert onder andere:

- Shapes (vormen): regels die beschrijven hoe data eruit moet zien, bijvoorbeeld:
  “elk Gebouw moet een bouwjaar hebben”.
- Concrete beperkingen, bijvoorbeeld:
  “het bouwjaar moet een jaartal tussen 1900 en 2024 zijn”.
- Foutmeldingen: wanneer data niet aan de regels voldoet, geeft SHACL aan wat er ontbreekt of incorrect is.
  SHACL werkt naast OWL en controleert of data voldoet aan de regels die zijn afgesproken. Je gebruikt SHACL bijvoorbeeld om data te valideren voordat deze wordt opgeslagen of uitgewisseld, of voor automatische kwaliteitscontrole (bijvoorbeeld in een Common Data Environment voor BIM).

Als vuistregel kun je onthouden dat SHACL uitgaat van een Closed World Assumption:
“als een eigenschap niet is ingevuld, is dat een fout”.
OWL gaat uit van een Open World Assumption:
“als een eigenschap niet is ingevuld, kan die informatie elders bestaan”.
SHACL doet geen logische afleidingen; dat is de taak van OWL.

### SHACL gebruik MDS

Voor de minimale dataset wordt één bepaalde functie van SHACL vooral gebruikt, namelijk de minCount. Met de minCount kan worden aangegeven hoeveel waarden er minimaal voor iets moeten zijn.

### Voorbeeld boom

Om te laten zien hoe SHACL ingezet kan worden om IMBOR-data te valideren gebruiken het voorbeeld van het objecttype 'Boom'. Het stuk voorbeeldata toont dat er een uniek object is data van de klasse 'boom' is, het heeft een aantal attributen met waarden:

- De boom heeft een URI
- De boom heeft een aanlegjaar, namelijk 1988.
- De boom heeft een kiemjaar, 1987.
- De boom heeft een waarde voor het attribuut 'onderstam', namelijk 'ja'.

###### Voorbeelddata 1: 'Boom'

```turtle
data:6fb4b2c7-69ec-4976-8489-6ad2d35d9e63 a imbor:83a942f7-5291-42f0-afb1-9a57d0fb2f15 ; #'Boom'
    nen2660:hasBoundary
    nen3610:identificatie "6fb4b2c7-69ec-4976-8489-6ad2d35d9e63"  ;     #'identificatie'
    imbor:534f07b8-9243-4848-a3d0-6ebeb321784c "1988"^^xsd:gYear    ;   #'Aanlegjaar' (1988)
    imbor:39231ace-3d00-4bcc-b4db-31dbb2c0bb6f "1987"^^xsd:gYear ;      #'kiemjaar' (1987)
    imbor:548157ad-adc0-4981-b851-00230f65f359 "true"^^xsd:boolean ; ;  #'onderstam' (ja)

```

Stel we willen deze data valideren op basis van bepaalde eisen die we stellen aan _boom_. Het is bijvoorbeeld verondersteld dat elke boom een:

- een URI/identificatie
- een aanlegjaar
- en een groeiwijze
  moet hebben.

P.S. _groeiwijze_ heeft **geen** waarde in de huidige dataset van _boom_.
Of de boom een kiemjaar en een onderstam heeft, is in dit geval informatie die niet essentieel is, maar wel in de dataset mag blijven. Dan kunnen we de volgende SHACL shape maken om de data van boom te valideren:

###### Voorbeeld SHACL-shapes 1: 'Boom'

```turtle
mds_imbor:shape-8f93708d-a155-4f36-97de-f89c9da34429 a sh:NodeShape ;       # URI van de shape
  sh:targetClass imbor:83a942f7-5291-42f0-afb1-9a57d0fb2f15 ;               # Shape geldt voor het objecttype 'Boom'
  sh:property mds_imbor:prop-8671f897-fbbd-4681-8cf3-face207d8327           # 'Boom' heeft het attribuut 'identificatie'
  sh:property mds_imbor:prop-f7ca9110-c8b9-485f-a5d1-54420deed52a           # 'Boom' heeft het attribuut 'aanlegjaar'
  sh:property mds_imbor:prop-92ace226-90e5-40ff-a4b2-c5c247adc138           # 'Boom' heeft het attribuut 'groeiwijze'

mds_imbor:prop-8671f897-fbbd-4681-8cf3-face207d8327 a sh:PropertyShape ;    # 'Boom' heeft tenminste één waarde voor het attribuut 'identificatie'
  sh:minCount 1 ;
  sh:path <http://modellen.geostandaarden.nl/def/nen3610-2022#identificatie> .

mds_imbor:prop-f7ca9110-c8b9-485f-a5d1-54420deed52a a sh:PropertyShape ;    # 'Boom' heeft tenminste één waarde voor het attribuut 'aanlegjaar'
  sh:minCount 1 ;
  sh:path imbor:534f07b8-9243-4848-a3d0-6ebeb321784c .

mds_imbor:prop-92ace226-90e5-40ff-a4b2-c5c247adc138 a sh:PropertyShape ;    # 'Boom' heeft tenminste één waarde voor het attribuut 'groeiwijze'
  sh:minCount 1 ;
  sh:path imbor:c3ab0c99-806c-4743-9e68-1b452ee94b73 .
```

De volgende stap is validatie. SHACL maakt een validatierapport waarin, dit is een uittreksel van mogelijke fouten die door de SHACL shapes in de dataset gevonden zijn. We lopen door het validatierapport van de dataset heen.

###### Voorbeeld validatierapport SHACL 1: 'Boom'

```turtle
  sh:result    [ rdf:type                      sh:ValidationResult;                                                 # Er is een validatieresultaat
                 sh:focusNode                  data:6fb4b2c7-69ec-4976-8489-6ad2d35d9e63;                           # Het object waar de fout is gevonden (deze specifieke boom), dit object voldoet dus niet aan een bepaalde regel
                 sh:resultMessage              "minCount[1]: Invalid cardinality: expected min 1: Got count = 0";   # De property moet minimaal één keer voorkomen, maar in de data is hij 0 keer aanwezig
                 sh:resultPath                 imbor:c3ab0c99-806c-4743-9e68-1b452ee94b73;                          # De property van het object waar de fout is gevonden
                 sh:resultSeverity             sh:Violation;                                                        # De ernst van de fout, in dit geval voldoet de data niet aan de eisen van de minimale dataset
                 sh:sourceConstraintComponent  sh:MinCountConstraintComponent;                                      # De overtreding komt door een regel over het minimumaantal.
                 sh:sourceShape                mds_imbor:prop-92ace226-90e5-40ff-a4b2-c5c247adc138                  # De URI van de exacte SHACL PropertyShape die deze verplichting definieert
               ];
```

SHACL geeft dus één foutmelding, omdat alleen _groeiwijze_ als attribuut ontbreekt. _Identificatie_ en _aanlegjaar_ worden niet genoemd omdat daar wel de verwachte waarden voor bestaan. _Kiemjaar_ en _onderstam_ worden niet genoemd in het rapport omdat deze attributen niet verplicht zijn, en er daarom dus ook geen SHACL shapes voor zijn. We zien dus de Closed World Assumption van SHACL terug in dit rapport, SHACL toetst de data aan de hand van gegeven regels.
