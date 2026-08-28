## SHACL Shapes

***Gebaseerd op GitHub issue: [1606](https://github.com/Stichting-CROW/imbor/issues/1606).***

[[shacl]] (SHapes Constraint Language) is een W3C-standaard om te valideren of data aan bepaalde regels voldoet. IMBOR conformeert zich aan de [[NEN2660-2]] en levert zodoende deze regels mee: elke IMBOR-`Klasse` is naast een `rdfs:Class` ook een `sh:NodeShape`, met daaraan gekoppelde `sh:PropertyShape`s die de beperkingen vastleggen. Zo kan een beheerder valideren of zijn geregistreerde data conform IMBOR is.

De beperkingen vallen in twee soorten uiteen:

* **Attribuut-beperkingen** (klasse-attribuut-combinaties): welk datatype een waarde heeft, hoe vaak een attribuut mag voorkomen (multipliciteit) en uit welke domeinwaardenlijst de waarde moet komen.
* **Relatie-beperkingen** (zie [Semantische relaties](#semantische-relaties)): naar welke doelklasse(n) een relatie mag wijzen en hoe vaak.

Voor het correct opleggen van deze beperkingen kent IMBOR drie terugkerende [[shacl]]-patronen. Wélk patroon gekozen is hangt af van wat je wilt afdwingen; dat luistert nauw, want een verkeerd patroon valideert vaak *niet* wat je bedoelt. Deze best practice licht de drie patronen toe. Zie ook de [technische documentatie](https://docs.crow.nl/imbor/techdoc/#semantische-relaties).

| Situatie                                                  | [[shacl]]-patroon                                 |
|-----------------------------------------------------------|---------------------------------------------------|
| [Enumeratielijst (verplichte domeinwaardenlijst)](#enumeratielijst): álle waarden uit één lijst | `sh:class` (met `sh:maxCount`)                    |
| [Suggestielijst](#suggestielijst): aanbevolen waarden, afwijken toegestaan   | `sh:qualifiedValueShape` + `sh:qualifiedMaxCount` |
| [Decompositie](#decompositie): één relatie naar meerdere doelklassen       | `sh:qualifiedValueShape` + `sh:qualifiedMinCount` |
| {.def}                                                    |                                                   |

### Enumeratielijst

Het meest voorkomende geval bij attributen: een attribuut mag beperkt voorkomen en de waarde *moet* uit een vaste domeinwaardenlijst komen. Ofwel: een _verplichte domeinwaardenlijst_.

>EXAMPLE
>Het attribuut `verschijningsvorm` mag bij een `Viaduct` maximaal één keer voorkomen, en de waarde moet uit de bijbehorende domeinwaardenlijst komen.

Hiervoor gebruikt IMBOR `sh:class` in combinatie met `sh:maxCount`, maar dus *niet* `sh:qualifiedValueShape`:

<pre><code class="turtle" data-include="data/shacl-enumeratie.ttl" data-include-format="text"></code></pre>

`sh:qualifiedValueShape` beperkt namelijk alleen de *gekwalificeerde* deelverzameling: het zegt "als er een waarde in de opgegeven klasse zit, dan maximaal één". Een waarde *buiten* de domeinwaardenlijst levert dan géén overtreding op en dat is precies niet de bedoeling bij een verplichte lijst. `sh:class` dwingt daarentegen af dat *elke* waarde van het attribuut uit die klasse (de domeinwaardenlijst) komt, en `sh:maxCount 1` dat het er hooguit één is.

>ADVISEMENT
>In IMBOR2022 werd een strengere beperking gelegd, namelijk: "de waarde MOET exact één van deze URI's zijn" via de `sh:in`-constructie. Dat is nóg preciezer, maar leverde veel meer triples en een ingewikkeldere constructie op. Daarom is van IMBOR2025 `sh:in` geschrapt ten gunste van `sh:class`.

### Suggestielijst

Een tweede geval: een attribuut mag beperkt voorkomen en er is een *aanbevolen* domeinwaardenlijst, maar gebruikers mogen ook een eigen waarde opgeven. Ofwel een _referentielijst_.

>EXAMPLE
>Het attribuut `herbeoordeelde belastingklasse` mag maximaal één keer voorkomen. De waarde komt bij voorkeur uit de domeinwaardenlijst, maar een gebruiker mag een eigen waarde toevoegen.

Gebruik hiervoor `sh:maxCount` samen met `sh:qualifiedValueShape` en `sh:qualifiedMaxCount`:

<pre><code class="turtle" data-include="data/shacl-suggestielijst.ttl" data-include-format="text"></code></pre>

`sh:maxCount 1` dwingt af dat er hoogstens één herbeoordeelde belastingklasse is. De `sh:qualifiedValueShape` naar de domeinwaardenlijst *documenteert* vervolgens welke waarden aanbevolen zijn, zónder ze te verplichten: een waarde buiten de lijst valt buiten de gekwalificeerde vorm en levert geen overtreding op. Ken zo'n eigen waarde daarom géén type uit de domeinwaardenlijst toe, maar wel een `skos:prefLabel`.

### Decompositie

Soms wijst één en dezelfde relatie naar objecten van *verschillende* klassen, met per klasse een eigen multipliciteit. Dit speelt vooral bij decomposities via `heeftDeel`.

>EXAMPLE
>Een `Viaduct` heeft via de relatie `heeftDeel` minimaal één `Dek`, terwijl `Pijler`s optioneel zijn (0..n). Beide gaan via dezelfde relatie.

Gebruik hiervoor per doelklasse een `sh:qualifiedValueShape` met `sh:qualifiedMinCount`:

<pre><code class="turtle" data-include="data/shacl-semantische-relaties.ttl" data-include-format="text"></code></pre>

Met een directe `sh:class` zou je afdwingen dat *álle* `heeftDeel`-relaties naar dezelfde klasse wijzen. Dat is niet mogelijk als een viaduct zowel dekken als pijlers (en bijvoorbeeld landhoofden) kan hebben. `sh:qualifiedValueShape` maakt het juist mogelijk om per doelklasse een eigen aantal te eisen.
