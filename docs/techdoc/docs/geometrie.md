## Geometrie

IMBOR is primair bedoeld om te standaardiseren in type objecten en hun attributen (informatiebehoefte) betreffende vaste gegevens. De geometrische representatie wordt vaak ook als een vast gegeven gezien. De representatie van een object is echter _één_ van de gegevens die geregistreerd wordt. Vanuit de GIS systemen wordt het echter herkend als _het_ gegeven van het object. Er zijn echter meerdere (geometrische)representaties mogelijk. Per toepassing zal de meest geschikte representatie worden gekozen en dus gaat IMBOR daar geen bindende uitspraken over doen. Temeer omdat IMBOR vaak in combinatie met de landelijke registratie BGT/IMGeo gebruikt wordt en die al uitweidt over de geometrische vastlegging. 

Er is wel een addendum beschikbaar binnen IMBOR  waarin suggesties worden gegeven voor geometrische vastlegging. Het Geometrie addendum geeft aan welke soort geometrische vastlegging de voorkeur heeft en welke er meer mogelijk zijn. Indien een organisatie zich committeert aan het Geometrie addendum, dan betekent dit dat de geometrische vastlegging zoals voorgesteld wordt toegepast in die context. In Access is het addendum verwerkt middels de Klasse `GeometrischeEntiteit` (en zijn subklassen) en de relatie `heeft begrenzing`. Hetzelfde geldt voor de LinkedData versie, echter staat de informatie daar in een aparte graaf. 

In het addendum wordt per `Objecttype` minimaal één relatie naar een GM_* klasse met de multipliciteit 1-1 meegegeven. Dit kan op `Objecttype` niveau geregistreerd worden of op de `Klasse` erboven (wanneer het voor allemaal geldt). Vervolgens worden eventueel meerdere relaties naar andere GM_* klassen meegegeven met een multipliciteit 0-1. Dit moet geïnterpreteerd worden als: "Wanneer het geometrie addendum van IMBOR van toepassing verklaard wordt, dan moet er minimaal één 
geometrie vastgelegd worden middels van het type dat de 1-1 multipliciteit heeft. Er _mag_ vervolgens ook geometrie aangeleverd worden volgens de andere gespecificeerde vormen van geometrie."