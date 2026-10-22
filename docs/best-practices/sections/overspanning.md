## Samengestelde objecten (overspanning)

***Gebaseerd op GitHub issue: [1727](https://github.com/Stichting-CROW/imbor/issues/1727)***

IMBOR modelleert niet vanuit "wat de beheerder als één ding ervaart", maar vanuit fysieke objecten met een eigen levenscyclus, verbonden via [semantische relaties](#semantische-relaties). Een OVL-overspanning zoals op onderstaande foto, een spanmast met een spandraad waaraan een armatuur hangt, is daarom in IMBOR géén enkel object, maar een kleine decompositie van apart te beheren objecten. _Merk op dat dit voorbeeld uitgaat van IMBOR2022_. 

<figure>

![Foto van een overspanning](img/overspanning-issue-1727.png?raw=true)

<figcaption>Overspanning in de openbare ruimte (bron: GitHub issue 1727)</figcaption>
</figure>

De beheerder ervaart dit als "gewoon een overspanning", maar de spanmast heeft een andere faalwijze, een ander inspectieregime (stabiliteit, fundering, corrosie) en een ander vervangingsmoment dan de spandraad of het armatuur. Die zou je dus  wél apart kunnen willen volgen.

### Toepassing samengestelde objecten in IMBOR

>EXAMPLE
>De OVL-beheerder van gemeente X wil een overspanning registreren. Hiervoor legt de gemeente een `Paal` vast met verschijningsvorm `Spanmast`. Deze is via `isVerbondenMet` verbonden aan een `Spandraad`. De spandraad is op zijn beurt via `isVerbondenMet` verbonden aan een `Armatuur`, die via `heeftDeel` een `Lichtbron` als onderdeel heeft.

<figure>

![Samengesteld object | Overspanning](img/overspanning.drawio.svg?raw=true)

<figcaption>Overspanning | Spanmast, spandraad, armatuur en lichtbron</figcaption>
</figure>

Dit is een voorbeelduitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/overspanning.ttl" data-include-format="text"></code></pre>

>ADVISEMENT
>IMBOR is niet voorschrijvend in welk van deze objecten een eigen geometrie heeft. Zie het (niet-normatieve) [addendum Geometrie](https://docs.crow.nl/imbor/techdoc/#geometrie): daar staat per objecttype welke geometrie wordt aanbevolen. Een `Paal` heeft bijvoorbeeld minimaal een puntgeometrie, een `Spandraad` alleen een lijngeometrie. Het is aan de eigen organisatie om te bepalen wat administratief en wat ook geometrisch wordt vastgelegd.
