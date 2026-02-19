## Wat is een MDS

_Een minimale dataset is de kleinst mogelijk verzameling gegevens (dataspecificatie) die nodig is om de gegevens van een bepaald proces of informatieproduct vast te leggen. Een minimale dataset kan worden vastgelegd in de vorm van een conformiteitsklasse._

### Conformiteitsklasse

_Een conformiteitsklasse is een deelverzameling van, in een ontologie gespecificeerde, zaken gericht op een afgebakend proces. In een conformiteitsklasse zijn alleen die zaken over objecttypen, relaties en attributen opgenomen, die nodig zijn voor de kwaliteitsborging van de gegevens benodigd voor dat afgebakende proces. Met behulp van een conformiteitsklasse kan de, specifiek voor het afgebakende proces benodigde, kwaliteit en betrouwbaarheid van gegevens automatisch getoetst worden._

### Het doel van een MDS

Het doel van een minimale dataset is dus om bepaalde eisen te stellen aan data die opgelevert wordt. Om uit te leggen hoe een minimale dataset geconstruceerd kan worden, nemen we het voorbeeld van de minimale dataset van de DOOR-gemeenten. Deze gemeenten willen de door aannemers aangeleverde IMBOR-data voorafgaand aan het uitvoeren van bouwplannen valideren. Op die manier kunnen zij controleren of de aangeleverde gegevens voldoen aan hun eisen. Daarbij verifiëren zij of alle door hen gewenste attributen van de aangeleverde fysieke objecten daadwerkelijk aanwezig zijn.

Een objecttype in IMBOR is bijvoorbeeld 'Binnenspeelterrein'. Een binnenspeelterrein heeft volgens IMBOR standaard een aantal verplichte attributen, zoals 'identificate' - een URI, een domein, een identificatie geovoorziening, en een aanlegjaar. Deze gemeenten willen een check uitvoeren voorafgaand aan een bouw of verbouwing, waarmnee zij na kunnen gaan of de verplichte attributen voor voor de objecttypen aanwezig zijn.

### Valideren met SHACL

Om deze IMBOR-data te valideren gebruiken wij de <a href="https://www.w3.org/TR/shacl/">SHACL</a> Shapes Constraint Language. In het volgende hoofdstuk wordt deze taal uitgelegd.
