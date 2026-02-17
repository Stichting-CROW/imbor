## Documenten en Memo's

***Gebaseerd op GitHub issue: [1628](https://github.com/Stichting-CROW/imbor/issues/1628)***

IMBOR kent de relatie `isBeschrevenDoor` vanuit de [[NEN2660-2]]. Deze loopt vanaf een (subklasse van) `Object` naar een `InformatieObject`. Twee van die speciaalsoorten `InformatieObject`en zijn:
- Document 
- Memo

Deze dienen verschillende doelen:

**Document**

De relatie naar Document wordt gebruikt om aan te geven dat er een relatie is tussen (een instantie) van Object en (een instantie) van Document. Met het attribuut `type document` kan aangegeven worden welk soort document het betreft (bijvoorbeeld 'Revisietekening') en met het attribuut `documentlocatie` kan een locatie (bijvoorbeeld een URL) naar het daadwerkelijke documenten gegeven worden. Tekeningen, Vergunningen, Rapporten, etc. uit een document management systeem kunnen op deze manier gelinkt worden aan de objecten. 

**Memo**

De relatie naar Memo wordt gebruikt om aan te geven dat er een relaties is tussen (een instantie) van Object en een (instantie van) Memo. Dit wordt gebruikt om notities vast te leggen over dat object. Met het attribuut `memoveld` kan dan een daadwerkelijke waarde (de notitie) worden vastgelegd. Doormiddel van het gebruiken van de [NEN3610 temporele aspecten](#nen3610-temporele-aspecten) kan op die manier een historie van memo's worden bijgehouden. 

