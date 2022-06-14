## Inleiding

Sinds het begin van het Informatiemodel Openbare Ruimte (<abbr title="Informatiemodel Openbare Ruimte">IMBOR</abbr>) wordt er gesproken over het uitwisselen van IMBOR data tussen systemen. IMBOR beschrijft de registratie van assets en de informatie daarbij. Het is daarom ook logisch dat deze informatie in de vorm van data soms ook gedeeld moet worden. Dit delen van data geldt zowel binnen de organisatie als met partijen daarbuiten. Vanuit softwareleveranciers en opdrachtgevers wordt er zodoende vaak gevraagd om een standaard IMBOR uitwisselformaat. CROW ziet dit niet direct als een taak omdat het gelooft in de filosofie van LinkedData. Om in een praktische oplossing te voorzien is deze 'Best practice' geschreven. Hier wordt beschreven hoe data op basis van de openstandaard <abbr title="Resource Description Framework">RDF</abbr>, in combinatie met de IMBOR ontologie gedeeld, uitgewisseld en gevalideerd kan worden. 

### Toepassingsgebied

De Best practice kan worden toegepast bij het delen van gegevens binnen het beheer van de openbare ruimte. Daarom wordt er gebruikt gemaakt van de IMBOR ontologie. Het gaat dan om gegevens die buiten het assetmanagementpakket (né: Beheerpakket) behandeld worden. Hiervoor worden de technieken van het semantisch web ingezet. 

De Best practice beschrijft hoe men middels RDF IMBOR gegevens kan delen, maar zegt (nog) _niets_ over:
* Hoe om te gaan met revisies op data
* Welke metadata er verstrekt moet worden

### Achtergrond
IMBOR 2020 sloot aan op de bestaande versie van IMGeo. In IMGeo 2.1.1 ontbraken bepaalde subclassificaties van objecten die wel in IMBOR voorkwamen. Om IMBOR-classificaties zonder gegevensverlies te kunnen uitwisselen tussen Geo- en BOR-afdeling binnen een organisatie middels het StUF-Geo BOR berichtenverkeer is in 2020 de werkafspraak [‘Uitbreiding domeinwaarden en attributen’ uitgewerkt][1]. 

Deze werkafspraak beschrijft hoe met het mechanisme van StUF:aanvullendeElementen extra attributen en domeinwaarden aan IMGeo-objecten kunnen worden toegevoegd in de uitwisseling. Bijvoorbeeld bij een Wegdeel kan naast de IMGeo-classificaties ‘gesloten verharding’ en ‘asfalt’ het soort asfalt (bijvoorbeeld) ZOAB) of datum van laatste onderhoud uit de BOR-registratie worden opgenomen. Of bij een VegetatieObject van het type ‘boom’ kan het soort boom (bijvoorbeeld ‘beuk’) of het plantjaar worden opgenomen.

Geonovum en CROW hebben deze praktijkrichtlijn in 2020 gemaakt. Deze wordt/werd echter niet ten volle benut. Sinds 2022 is IMBOR ook in LinkedData beschikbaar en daarmee is de weg vrij om gebruik te maken van deze techniek die internationaal geadopteerd is. Vandaar dat nu deze 'best practice' beschreven is. Het ligt in de lijn der verwachtingen dat op termijn deze praktijkrichtlijn komt te vervallen.

### Semantic Web
Deze best practice maakt gebruik van de principes van LinkedData, meer specifiek die van het ["Semantic Web"][2]. Het semantisch web is een uitbreiding van het internet, waarmee uitwisseling op basis van data gedaan kan worden in tegenstelling tot het uitwisselen van documenten (HTML). Het semantisch web bestaat naast RDF uit verschillende elementen, zoals afgebeeld hieronder. Voor deze best practice worden enkele onderdelen van het semantisch web toegelicht in de volgende secties. 

<figure>
  <img src="img\update-semanticweb-stack.png" alt="Updated semantic web stack" />
  <figcaption>Updated Semantic Web stack (bron: <a href="https://medium.com/openlink-software-blog/semantic-web-layer-cake-tweak-explained-6ba5c6ac3fab" target="_blank">Medium</a>)</figcaption>
</figure>


[1]: https://geonovum.github.io/IMGeo/praktijkrichtlijn/uitwisseling-imbor-geobor/
[2]: https://www.w3.org/standards/semanticweb/


