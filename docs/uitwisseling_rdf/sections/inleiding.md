## Inleiding

Sinds het begin van het Informatiemodel Openbare Ruimte (<abbr title="Informatiemodel Openbare Ruimte">IMBOR</abbr>) wordt er gesproken over het uitwisselen van IMBOR-data tussen systemen. IMBOR beschrijft de registratie van assets en de informatie daarbij. Het is daarom ook logisch dat deze informatie in de vorm van data soms ook gedeeld moet worden. Dit delen van data geldt zowel binnen de organisatie als voor partijen daarbuiten. Vanuit softwareleveranciers en opdrachtgevers wordt er zodoende vaak gevraagd om een standaard 'IMBOR-uitwisselformaat'. CROW ziet juist kansen in een combinatie van een standaard ontologie (IMBOR) en open standaarden voor informatie delen (LinkedData, NEN2660-2). Om in een praktische oplossing te voorzien is deze 'best practice' geschreven. Hier wordt beschreven hoe data op basis van de open standaard <abbr title="Resource Description Framework">RDF</abbr>, in combinatie met de IMBOR-ontologie gedeeld, uitgewisseld en gevalideerd kan worden. 


### Toepassingsgebied

De best practice kan worden toegepast bij het delen van gegevens binnen het beheer van de openbare ruimte. Daarom wordt er gebruikt gemaakt van de IMBOR-ontologie. Het gaat dan om gegevens die buiten het areaalbeheerpakketpakket (lees: Beheerpakket) behandeld worden. Hiervoor worden de technieken van het semantisch web ingezet. 

De best practice beschrijft hoe men middels RDF IMBOR-gegevens kan delen, maar zegt (nog) _niets_ over:
* Hoe om te gaan met revisies op data;
* Welke metadata er verstrekt moet worden.

>NOTE "Geschikt voor meerdere (NEN2660-2) ontologieën"
>
>De manier van data delen, welke geclassificeerd is aan een ontologie, zoals in dit artikel beschreven wordt is niet nieuw en niet specifiek voor IMBOR. In de best practice worden alleen maar bestaande technieken gebruikt en IMBOR is een NEN2660-2 ontologie. Vandaar dat deze manier van data delen nu voor IMBOR is geschreven maar voor in principe elke LinkedData gebaseerde ontologie van toepassing is. Dit levert uiteraard schaal- en investeringsvoordelen op.
>
>Het OroX is het generieke opslagvorm ten behoeve van de uitwisseling volgens het Gegevenswoordenboek Stedelijk Water (GWSW). Het OroX is een ook specificatie gebaseerd op semantisch web standaarden. Het is daarmee als _een_ (andere) invulling van deze best practice te zien.

### Achtergrond
IMBOR 2020 sloot aan op de bestaande versie van IMGeo. In IMGeo 2.1.1 ontbraken bepaalde subclassificaties van objecten die wel in IMBOR voorkwamen. Om IMBOR-classificaties zonder gegevensverlies te kunnen delen tussen Geo- en BOR-afdelingen binnen een organisatie middels het StUF-Geo BOR berichtenverkeer is in 2020 de praktijkrichtlijn ["Uitbreiding domeinwaarden en attributen" uitgewerkt][1]. 

Deze praktijkrichtlijn beschrijft hoe met het mechanisme van StUF:aanvullendeElementen extra attributen en domeinwaarden aan IMGeo-objecten kunnen worden toegevoegd in de uitwisseling. Bij een Wegdeel kan bijvoorbeeld naast de IMGeo-classificaties ‘gesloten verharding’ en ‘asfalt’ het soort asfalt, (bijvoorbeeld) ZOAB, of datum van laatste onderhoud uit de BOR-registratie worden opgenomen. Of bij een VegetatieObject van het type ‘boom’  kan de soortnaam van de boom (bijvoorbeeld ‘Fagus sylvatica’) of het plantjaar worden opgenomen.

Geonovum en CROW hebben deze praktijkrichtlijn in 2020 gemaakt. Deze wordt/werd echter niet ten volle benut. Sinds 2022 is IMBOR ook in LinkedData beschikbaar en daarmee is de weg vrij om gebruik te maken van deze techniek die internationaal geadopteerd is. Vandaar dat nu deze 'best practice' beschreven is. Het ligt in de lijn der verwachtingen dat op termijn deze praktijkrichtlijn komt te vervallen.

### Uitwisselen versus Delen

Vaak wordt er over het 'uitwisselen van gegevens' gesproken. Deze uitspraak is ingewikkelder geworden sinds het publiceren van gegevens op internet nu ook 'data gebaseerd' kan, in tegenstelling tot 'document gebaseerd'. In de [NEN3610][3] wordt dit op de volgende manier toegelicht:
>
>EXAMPLE "Quote NEN3610; Uitwisselen en publiceren"
>
>"___Uitwisselen van gegevens___ _betreft een fysieke uitwisseling van data in vast ketens, waarbij data van een bron naar een afnemer gaan, bijvoorbeeld van een bronhouder naar een landelijke voorziening. ..."_
>
>"___Publiceren van gegevens___ _betreft het aanbieden van gegevens aan elke willekeurige datagebruiker. In dit geval zijn data op het web gepubliceerd en via webprotocollen vindbaar, toegangkelijk en bruikbaar, zonder dat de data naar de gebruiker getransporteerd (lees gekopieerd) wordt. ..."_
>

### Semantic Web
Deze best practice maakt gebruik van de principes van LinkedData, meer specifiek die van het [‘Semantic Web’][2]. Het semantisch web is een uitbreiding van het internet, waarmee gedeeld wordt op basis van data in tegenstelling tot het delen van documenten (HTML). Het semantisch web bestaat naast RDF uit verschillende elementen, zoals afgebeeld hieronder. Voor deze best practice worden enkele onderdelen van het semantisch web toegelicht in de volgende secties. 

<figure>
  <img src="img\update-semanticweb-stack.png" alt="Updated semantic web stack" />
  <figcaption>Updated Semantic Web stack (bron: <a href="https://medium.com/openlink-software-blog/semantic-web-layer-cake-tweak-explained-6ba5c6ac3fab" target="_blank">Medium</a>)</figcaption>
</figure>


[1]: https://geonovum.github.io/IMGeo/praktijkrichtlijn/uitwisseling-imbor-geobor/
[2]: https://www.w3.org/standards/semanticweb/
[3]: https://www.nen.nl/nen-3610-2022-nl-296137


