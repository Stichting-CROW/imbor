# Wat is de Minimale dataset IMBOR?

_De term 'Minimale dataset' wordt in de context van IMBOR gebruikt. Daarin representeert het een set van veelgebruikte IMBOR-gegevens die nodig zijn om goed beheer uit te voeren, opgesteld door een aantal gemeenten._

## Het doel van de minimale dataset

De [minimale dataset](https://begrippen.crow.nl/ombk/nl/page/?uri=https%3A%2F%2Fdata.crow.nl%2Ftech-term%2Fterm%2FTT004) IMBOR representeert een set van veelgebruikte IMBOR-gegevens die nodig zijn om goed beheer uit te voeren, opgesteld door een aantal gemeenten. Deze set is op eigen initiatief opgesteld buiten de beheerders van IMBOR om en is een marktinitiatief. Vanuit IMBOR wordt de waarde van de set herkent en vandaar dat deze als informatief onderdeel is opgenomen.

De minimale dataset IMBOR wordt als spreadsheet via de website [Objectgericht.nl](https://www.objectgericht.nl/) gepubliceerd en kan daar opgevraagd worden. CROW heeft deze set vertaald naar [[shacl]] shapes als machineleesbaar formaat. Op deze manier kan deze set gebruikt worden in combinatie met de andere RDF sets van IMBOR. De set is opgesteld om aan te kunnen geven wat er minimaal aan gegevens nodig is om goed beheer uit te kunnen voeren. Een objecttype in IMBOR is bijvoorbeeld 'Binnenspeelterrein'. Een binnenspeelterrein heeft volgens IMBOR standaard enkel een viertal verplichte attributen, te weten `domein`, `geometrie`,`identificatie` en `status`. De Minimale dataset doet daar een schepje bovenop. De stelt dat de attributen `aanlegjaar`, `identificatie geovoorziening`, `oppervlakte`, `WAS` en `jaar herinrichting` _ook_ echt nodig zijn om goed beheer uit te kunnen voeren. 

## Valideren met SHACL

Om vervolgens IMBOR-data te valideren welke niet alleen aan standaard IMBOR voldoet, maar ook aan de optionele Minimale dataset IMBOR wordt de W3C standaard [[shacl]] gebruikt. In de volgende sectie wordt deze taal uitgelegd. Het bestand kan gedownload worden op de [GitHub omgeving van IMBOR](https://github.com/Stichting-CROW/imbor/tree/master/data/informele%20handreiking).
