## Logging, versie- & deltamanagement

>ADVISEMENT
>Bij de tervisielegging van IMBOR2025 wordt specifiek aandacht gevraagd om feedback te geven welke methode geprefereerd wordt. IMBOR is niet voornemens alle logging, versie- & deltamanagement methoden te houden. Na input van de IMBOR2025 tervisielegging zal een keuze worden gemaakt.

Vanaf IMBOR2025 wordt er uitgebreid bijgehouden wat de wijzigingen zijn ten opzichte van de vorige versie. Dit wordt enerzijds gedaan voor de transparantie, anderzijds voor de (semi-)automatische verwerkingen van wijzigingen in de software die gebruik maakt van IMBOR. Er zijn meerdere manieren waarop deze wijzigingen bijgehouden en gedistribueerd worden. 

* GitHub issues: De meldingen, overwegingen en verwerking
* Logging tabel (MS Access): De wijziging in de beheeromgeving in tabel vorm. Inclusief metadata hierover zoals de gerelateerde GitHub issue en in welke categorie de wijziging valt
* Changelog (RDF): De wijziging in de beheeromgeving een triple vorm. Inclusief metadata hierover zoals de gerelateerde GitHub issue en in welke categorie de wijziging valt
* Diff (RDF): Een 'verschillen' bestand tussen twee versies van een IMBOR RDF bestand. De diff is in triples en kan zodoende gecombineerd worden met de changelog
* Diff (TSV): Een 'verschillen' bestand tussen twee versies van een IMBOR RDF bestand. De diff heeft de stijl van GitHub
* GitHub Diff: Binnen de imbor-development repository worden voor *elke* commit bijgehouden wat de wijzigingen zijn. Bij een commit wordt de AccesDB omgezet naar aparte [[IANA-TSV]] bestanden. Deze worden op regel niveau vergeleken door GitHub.
* Delta rapportages: Spreadsheets die op basis van de NEN2660-2 structuur rapporteren wat de wijzigingen zijn tussen twee versies van releases.

<details>
  <summary>
    <i>
    Zie ook gerelateerde issue(s) op GitHub:
    <span class="icon">👇</span>
    </i>
  </summary>
  <div class="issue" data-number="1401"><span></span></div>
</details>

### GitHub issues
Op de GitHub pagina van IMBOR kunnen issues worden ingediend welke kunnen leiden tot wijzigingen. Deze kunnen door iedereen worden ingediend, inclusief de IMBOR teamleden zelf. Deze issues dienen als startpunt voor een wijziging. Voor IMBOR2025 is een ['milestone'](https://github.com/Stichting-CROW/imbor/milestone/3) gemaakt. Alle issues die aan deze milestone hangen zijn verwerkt in de 2025 versie. Hiermee is dus meteen inzichtelijke wat er allemaal verwerkt en veranderd is. Deze kan gezien worden als _zeer uitgebreide_ releasenotes, waarbij ook duidelijk is waarom, hoe en door wie iets gewijzigd is.

Locatie: [GitHub issues](https://github.com/Stichting-CROW/imbor/milestone/3)

### Logging tabel
IMBOR gebruikt vooralsnog een Access database als de beheeromgeving. Binnen deze beheeromgeving is een uitgebreide logging aanwezig. In principe worden alle wijzigingen die doorgevoerd worden in IMBOR hier gelogd. Deze tabel bestaat uit de volgende onderdelen. 

| Kolom            | Uitleg                                                                          |
|------------------|---------------------------------------------------------------------------------|
| `LoggingGUID`    | Unieke identifier voor de logging regel                                         |
| `VocabulairGUID` | GUID van de term uit de vocabulaire, indien deze beïnvloed is door de wijziging |
| `IMBORGUID`      | GUID van de het IMBOR concept wat beïnvloed is door de wijziging                |
| `GitHub-issueID` | Identifier van het gerelateerde GitHub issue                                    |
| `Omschrijving`   | Titel van de wijziging                                                          |
| `Terugkoppeling` | Gedetailleerde beschrijving van de wijziging zelf                               |
| `Loggingsdatum`  | Datum waarop de wijziging is gelogd                                             |
| `StatusID`       | Create = Toevoeging, Delete = Verwijdering, Update = Gewijzigd                  |
| `AardAanpassing` | Aard van de aanpassing                                                          |
| `CollectieID`    | Scope waartoe de wijziging behoort                                              |
| `LoggingType`    | Type van de logging                                                             |
| `VervangGUID`    | Indien van toepassing de GUID van het concept waarnaartoe gewijzigd is          |
| { .data }        |                                                                                 |

Deze tabel vormt ook de bron voor de changelog in RDF.

### Changelog (RDF)
IMBOR (en CROW) willen eenduidiger zijn in hoe kennis naar de markt gedistribueerd wordt. Er is gekozen om alle producten in (NEN2660) RDF te verstrekken. Op deze manier hoeft de markt maar één manier te programmeren om CROW kennis in hun systemen en processen te verwerken. In 2025 is dit uitgebreid met het eenduidig verstrekken van de changelogs. Hiervoor is het [[activitystreams-core]] standaard geadopteerd. [[activitystreams-core]] is een protocol voor het beschrijven van activiteiten en interacties op het web in een gestandaardiseerd formaat. Het wordt o.a. gebruikt voor activiteitenlogboeken. 

Locatie: [Changelog in RDF][changelogging] 

Elke `Log-item` wordt geclassificeerd als een `crow_change:ChangeItem` en als een van de klassen: `as:Delete`, `as:Create` of `as:Update`. Hiermee is snel inzichtelijk welke soort wijzigingen er zijn. Elk item heeft vervolgens de volgende eigenschappen:

| Eigenschap        | Uitleg                                            |
|-------------------|---------------------------------------------------|
| `rdfs:comment`    | Gedetailleerde beschrijving van de wijziging zelf |
| `rdfs:label`      | Titel van de wijziging                            |
| `rdfs:seeAlso`    | URL van het gerelateerde GitHub issue             |
| `skos:changeNote` | Aard van de aanpassing                            |
| `skos:scopeNote`  | Scope waartoe de wijziging behoort                |
| `as:name`         | Titel van de wijziging                            |
| `as:published `   | Datum waarop de wijziging is gelogd               |
| `as:summary`      | Gedetailleerde beschrijving van de wijziging zelf |
| `as:to `          | URI('s) waar de wijziging betrekking op heeft     |
| { .data }         |                                                   |

Deze structuur zit als volgt in elkaar. 

<figure>

![Changelog structuur](img/Changelog.drawio.png)
    
<figcaption><figcaption>Changelog structuur</figcaption></figcaption>
</figure>


<div class='note'>
De vorm van deze changelog wordt voor alle CROW producten geadopteerd in de komende jaren.
</div>

### Diff (RDF)
IMBOR (en CROW) willen eenduidiger zijn in hoe kennis naar de markt gedistribueerd wordt. Er is gekozen om alle producten in (NEN2660) RDF te verstrekken. Op deze manier hoeft de markt maar één manier te programmeren om CROW kennis in hun systemen en processen te verwerken. In 2025 is dit uitgebreid met het eenduidig verstrekken van de diff's (verschil bestanden) in RDF. Omdat bij CROW de standaard voor kennisverstrekking RDF wordt, geldt dit ook voor de diff's. Hiervoor is het [[activitystreams-core]] standaard geadopteerd. [[activitystreams-core]] is een protocol voor het beschrijven van activiteiten en interacties op het web in een gestandaardiseerd formaat. Het wordt o.a. gebruikt voor activiteitenlogboeken. 

Locatie: [Diff in RDF][changelogging]

In deze diff bestanden worden de verschillen uiteengezet per IMBOR graph (of: IMBOR bestand). In de diff zitten `rdf:Statement`'s. Deze statement zijn geclassificeerd als een `as:Delete` of `as:Create`. Deze bevatten drie eigenschappen die samen de triple vormen die gewijzigd is: `rdf:subject`, `rdf:predicate`, `rdf:object`. Zo is precies op triple niveau te zijn wat er weg is, of erbij is gekomen. 

<figure>

![ChangeStatement Structuur](img/ChangeStatement.drawio.png)
    
<figcaption><figcaption>Change statements structuur</figcaption></figcaption>
</figure>

<div class='note'>
De vorm van deze diff wordt voor alle CROW producten geadopteerd in de komende jaren.
</div>

#### Diff (TSV)
Voor diegene die RDF ingewikkeld vinden worden dezelfde wijzigingen als in de sectie hiervoor beschreven in een [[IANA-TSV]] bestand. Voor elke regel staat een `+` voor *Create* en een `-` voor *Delete*. Deze stijl is afkomstig van GitHub.

Locatie: [Diff in TSV][changelogging]

### GitHub Diff
CROW gebruikt GitHub voor de ontwikkeling van IMBOR. Binnen de [`imbor-development`](https://github.com/Stichting-CROW/imbor-development) repository worden voor *elke* commit bijgehouden wat de wijzigingen zijn. De folder [tsv](https://github.com/Stichting-CROW/imbor-development/tree/main/data/tsv) bevat automatisch gegenereerde [[IANA-TSV]] bestanden door 'GitHub actions'. Bij elke nieuwe commit van de AccessDB worden automatische de tabellen uit de database omgezet naar [[IANA-TSV]]. Daardoor kan op regel niveau bekeken worden wat er gewijzigd is omdat GitHub dit nu bijhoudt.

Locatie: [GitHub diff](https://github.com/Stichting-CROW/imbor-development/tree/main/data/tsv)

### Delta rapportage
IMBOR (en CROW) willen eenduidiger zijn in hoe kennis naar de markt gedistribueerd wordt. Er is gekozen om alle producten in (NEN2660) RDF te verstrekken. Op deze manier hoeft de markt maar één manier te programmeren om CROW kennis in hun systemen en processen te verwerken. In 2025 is dit uitgebreid met het eenduidig verstrekken van de delta rapportages. Deze delta rapportages zijn (grotendeels) gebaseerd op de topstructuur van de NEN2660-2. In principe kan dus iedere ontologie die gebaseerd is op de NEN2660-2 vergeleken worden en in deze rapportages worden gepresenteerd. 

Locatie: [Delta rapportage][changelogging]

De delta rapportage heeft de volgende structuur:

| Onderdeel          | Uitleg                                                                                                                                  |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Klassen            | Wijzigingen in de classes                                                                                                               |
| Hierarchie         | Wijzigingen in de hierarchie van classes                                                                                                |
| Attributen         | Wijzigingen in de attributen, inclusief de grootheid (quantitykind)                                                                     |
| Klassen-Attributen | Wijzigingen in de relatie tussen een klasse en een attribuut, inclusief de eenheid (unit), het datatype en de eventuele enumeratielijst |
| Klassen-Relaties   | Wijzigingen in de relaties tussen klassen                                                                                               |
| Enumeraties        | Wijzigingen in de enumeratietype, inclusief het type enumeratie en de bijbehorende domeinwaarden                                        |
| Collecties         | Wijzigingen in de collecties ('zoekingangen')                                                                                           |
| Collecties-Leden   | Wijzigingen in leden (objecttypen) van de collecties ('zoekingangen')                                                                   |
| { .data }          |                                                                                                                                         |

De rapportage toont in de kolom `changeStatus` of iets `NEW`, `DELETED`, `MODIFIED` of `UNCHANGED` is. De rijen worden ook respectievelijk groen, rood, geel en grijs gemarkeerd. 
In het geval van `MODIFIED` wordt in feller geel extra aangegeven _wat_ er dan specifiek aangepast is. In de kolomnaam is de postfix `_old` en `_new` toegevoegd om het verschil te kunnen zien.

<div class='example' title='Delta rapportage `MODIFIED` voorbeeld'>
<figure>

![Delta rapportage voorbeeld](img/delta-rapportages-voorbeeld.png)
    
<figcaption><figcaption>Snippet van delta rapportage -- rechtermuisknop "Openen in nieuw tabblad" voor leesbare versie</figcaption></figcaption>
</figure>

In dit voorbeeld is het volgende te zien:
- Op rij 1 staat een attribuut waarvan alleen de _naam_ is gewijzigd
- Op rij 2 staat een ander attribuut waarvan een aanpassing is geweest in de _definitie_
- Op rij 3 staat weer een ander attribuut waarvan een grootheid (quantitykind) is toegevoegd
</div>

<div class='note'>
De vorm van deze delta rapportages wordt voor alle CROW producten geadopteerd in de komende jaren.
</div>

[changelogging]: https://github.com/Stichting-CROW/imbor/tree/master/data/changelogging