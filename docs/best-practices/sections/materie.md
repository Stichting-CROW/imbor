## Materie

***Gebaseerd op GitHub issue: [1576](https://github.com/Stichting-CROW/imbor/issues/1576) en [1582](https://github.com/Stichting-CROW/imbor/issues/1582)***

Vóór IMBOR2022 werden materialen als attributen van Objecttypen vastgelegd. Binnen de [[NEN2660-2]] is hiervoor een modelleerconstructie gegeven die IMBOR nu toepast. Er kan een relatie [`bestaatUit`][bestaatUit] gelegd worden tussen de klasse [`ReeelObject`][ReeelObject] en de klasse [`Materie`][Materie]. Dit betekent dat materialen dus ook een klasse zijn en ook als zodanig gemodelleerd zijn. Binnen IMBOR zijn allemaal soorten materialen opgenomen en met relaties verbonden aan ObjectTypen. Deze lijst is op basis van 'expert judgement' samengesteld door de jaren heen.

>ADVISEMENT
>Ter verduidelijking: IMBOR limiteert *niet* welke relaties er tussen een [`FysiekObject`][FysiekObject] en een `Materie` gelegd kunnen worden. We geven alleen 'voorstellen'. 

Dit modelleerpatroon gaat er vanuit de materialen dus *ook* geïnstanteerd worden en middels de relatie `bestaatUit` aan een `ReeelObject` of subklasse daarvan gekoppeld worden. 

Zie ook: [Techdoc | Materie](https://docs.crow.nl/imbor/techdoc/#materie)

### Toepassing materie in IMBOR

>EXAMPLE
>Gemeente X wil vastleggen dat een bepaalde lichtmast uit een stalen en hardhouten gedeelte bestaat. Om dit te doen dient de gemeente in hun systeem een lichtmast (`LM123`) vast te leggen van het type IMBOR Lichtmast. Vervolgens moet aangegeven worden middels de relatie `bestaatUit` dat deze deels hardhout en deels staal is. Dit kan gedaan worden door instantaties van de IMBOR klassen 'Hardhout' en 'Staal' te maken (`gemX:Paal123_hardhout` en `gemX:Paal123_staal`) en deze middels `bestaatUit` aan de `LM123` te linken. De gemeente wil ten behoeve van het materialenpaspoort aangegeven of het hergebruikte materialen betreft, wat het gewicht van het materiaal is en wat het hoofdmateriaal van de lichtmast is. Per materie worden zodoende de attributen `percentage` en `gewicht` aangegeven. Uit de percentages kan afgeleid worden dat het hoofdmateriaal 'hardhout' is. Als laatste wordt middels het attribuut `materiefase` aangegeven dat het hardhout één keer eerder gebruikt is (`Fase 1`) en het staal nieuw is (`Fase 0`).   
>
>Er zijn nu gegevens vastgelegd bij de instanties van de twee materialen. Deze zijn gelinkt aan de instantie van Lichtmast. Hierdoor kan er nu een materialenpaspoort gegenereerd / gepresenteerd worden van 'LM123'.

Dit is een voorbeelduitwerking in [[Turtle]]:

<pre><code class="turtle" data-include="data/materie.ttl" data-include-format="text"></code></pre>

[Materie]: https://w3id.org/nen2660/def#Matter
[ReeelObject]: https://w3id.org/nen2660/def#RealObject
[FysiekObject]: https://w3id.org/nen2660/def#PhysicalObject
[bestaatUit]: https://w3id.org/nen2660/def#consistsOf
