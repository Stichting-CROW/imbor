## Logging, versie- & deltamanagement

Vanaf IMBOR2025 wordt er uitgebreid bijgehouden wat de wijzigingen zijn ten opzichte van de vorige versie. Dit wordt enerzijds gedaan voor de transparantie, anderzijds voor de (semi-)automatische verwerkingen van wijzigingen in de software die gebruik maakt van IMBOR. Er zijn meerdere manieren waarop deze wijzigingen bijgehouden en gedistribueerd worden.

* GitHub issues: De meldingen, overwegingen en verwerking
* Logging tabel (MS Access): De wijziging in de beheeromgeving in tabel vorm. Inclusief metadata hierover zoals de gerelateerde GitHub issue en in welke categorie de wijziging valt
* Changelog (RDF): De wijziging in de beheeromgeving een triple vorm. Inclusief metadata hierover zoals de gerelateerde GitHub issue en in welke categorie de wijziging valt
* Diff (RDF): Een 'verschillen' bestand tussen twee versies van een IMBOR RDF bestand. De diff is in triples en kan zodoende gecombineerd worden met de changelog
* Diff (TSV): Een 'verschillen' bestand tussen twee versies van een IMBOR RDF bestand. De diff heeft de stijl van GitHub
* GitHub Diff: Binnen de imbor-development repository worden voor elke commit bijgehouden wat de wijzigingen zijn. Bij een commit wordt de AccesDB omgezet naar aparte [IANA-TSV] bestanden. Deze worden op regel niveau vergeleken door GitHub.
* Delta rapportages: Spreadsheets die op basis van de NEN2660-2 structuur rapporteren wat de wijzigingen zijn tussen twee versies van releases.

De ***Changelog (RDF)***, ***Diff (RDF)***, ***Diff (TSV)*** en ***Delta rapportages*** zijn in deze folder te vinden. 

Voor meer en uitgebreidere informatie hierover wordt gerefereerd naar de [TechDoc](https://docs.crow.nl/imbor/techdoc/#logging-versie-deltamanagement)