# Domeinen

Patronen per vakgebied. Per domein: wat je extra uitvraagt in Fase 1, en hoe de prompt in Fase 2 wordt opgebouwd. Lees alleen het blok dat past bij de use-case van de gebruiker.

## Inhoud

- Klantcommunicatie (CCM)
- Cold outreach en sales
- Contentmarketing en social
- Technische spec en PRD
- Analyse en samenvatting
- Klantenservice en reacties

---

## Klantcommunicatie (CCM)

Brieven, mails, en berichten die een organisatie naar klanten stuurt. Vaak gebonden aan tone of voice, juridische correctheid en begrijpelijkheid.

**Extra uitvragen:**
- Welk type bericht: informatief, een afwijzing, een herinnering, een excuus, een wijziging?
- Geldt er een vaste tone of voice of huisstijl? Is er een voorbeeldbrief?
- Welk taalniveau moet de tekst hebben? (Vaak B1 voor een breed publiek.)
- Zijn er verplichte elementen: een juridische passage, een bezwaarmogelijkheid, een referentienummer?
- Moet het kunnen schalen over veel klanten met wisselende gegevens?

**Bouwwijze:**
- Rol: een ervaren tekstschrijver klantcommunicatie die schrijft op het gevraagde taalniveau.
- Verwerk de verplichte elementen als harde eisen.
- Vraag om een vaste structuur: aanleiding, kern, gevolg of actie, afsluiting.
- Variabelen voor alles wat per klant verschilt: `{klantnaam}`, `{referentie}`, `{bedrag}`, `{datum}`.
- Succescriterium vaak: correct, begrijpelijk op het gevraagde niveau, en in de juiste toon.

---

## Cold outreach en sales

Eerste benadering van een prospect via mail of bericht. Doel is een reactie, geen verkoop in één keer.

**Extra uitvragen:**
- Wie is de prospect en wat is zijn vermoedelijke pijn?
- Wat is de enige gewenste vervolgactie: een gesprek, een klik, een antwoord?
- Hoe warm is de lead? Is er een aanleiding of gedeelde context?
- Wat is het aanbod in één zin, en wat maakt het geloofwaardig?

**Bouwwijze:**
- Rol: iemand die scherpe, korte outreach schrijft die niet als template leest.
- Harde kaders: kort, één duidelijke vraag, geen opsomming van features.
- Voorbeeld van een goede en een slechte versie helpt enorm; vraag erom.
- Variabelen: `{prospect}`, `{aanleiding}`, `{pijnpunt}`, `{vervolgactie}`.
- Succescriterium: zou deze prospect hierop reageren, of klinkt het als de honderdste mail die hij kreeg?

---

## Contentmarketing en social

Posts, artikelen, nieuwsbrieven. Vaak in een herkenbare persoonlijke stem.

**Extra uitvragen:**
- Welk platform en welk formaat? (Een LinkedIn-post leest anders dan een blog.)
- Is er een eigen stem of stijl? Vraag om twee tot drie voorbeelden van eerder werk.
- Wat is de kernboodschap of het haakje?
- Wat moet de lezer voelen of doen na het lezen?

**Bouwwijze:**
- Stem vastleggen via voorbeelden is hier de belangrijkste hefboom. Zonder voorbeeld wordt het generiek.
- Vraag om een sterke opening, want de eerste regel bepaalt of iemand doorleest.
- Kaders: lengte, wel of geen hashtags, wel of geen emoji, toon.
- Variabelen: `{onderwerp}`, `{haakje}`, `{kernboodschap}`, `{call_to_action}`.
- Succescriterium: klinkt het als de gebruiker zelf, en houdt de opening de aandacht vast?

---

## Technische spec en PRD

Een specificatie, een product requirements document, of een technische uitleg.

**Extra uitvragen:**
- Wie leest dit: een ontwikkelaar, een opdrachtgever, een gemengd publiek?
- Welk detailniveau is nodig, en welke aannames mogen niet impliciet blijven?
- Is er een vaste sjabloonstructuur die gevolgd moet worden?
- Moeten edge cases, risico's of acceptatiecriteria expliciet benoemd worden?

**Bouwwijze:**
- Rol: een ervaren engineer of product owner die helder en volledig schrijft.
- Dwing een vaste structuur af met kopjes: doel, scope, eisen, edge cases, acceptatiecriteria.
- Vraag de AI om aannames expliciet te maken in plaats van stilzwijgend in te vullen.
- Variabelen: `{feature}`, `{doelgroep}`, `{scope}`.
- Succescriterium: kan een ontwikkelaar hiermee bouwen zonder terug te hoeven vragen?

---

## Analyse en samenvatting

Een document, dataset of tekst samenvatten of analyseren.

**Extra uitvragen:**
- Wat is de vraag achter de samenvatting? Een beslissing, een overzicht, een controle?
- Welke lengte en welk format: bullets, een managementsamenvatting, een tabel?
- Wat mag weg en wat moet absoluut behouden blijven?
- Moet de output een mening geven of strikt neutraal blijven?

**Bouwwijze:**
- Rol: een analist die hoofdzaken van bijzaken scheidt voor het gevraagde doel.
- Vraag om een vaste structuur die past bij de beslissing die erop volgt.
- Laat de AI eerst de kernvraag herhalen voordat hij samenvat, zodat de focus klopt.
- Variabelen: `{brontype}`, `{doel_van_samenvatting}`, `{lengte}`.
- Succescriterium: kan de lezer op basis hiervan de beslissing nemen waarvoor de samenvatting bedoeld was?

---

## Klantenservice en reacties

Antwoorden op klantvragen, klachten of reviews.

**Extra uitvragen:**
- Wat is de toon van het binnenkomende bericht: neutraal, boos, teleurgesteld?
- Wat mag wel en niet toegezegd worden? Zijn er beleidsgrenzen?
- Moet er een vervolgactie of compensatie in?
- Geldt er een huisstijl voor service-antwoorden?

**Bouwwijze:**
- Rol: een ervaren servicemedewerker die rustig, erkennend en oplossingsgericht reageert.
- Harde grens: nooit iets toezeggen buiten het opgegeven beleid.
- Structuur: erken, leg uit, bied een oplossing of vervolgstap, sluit warm af.
- Variabelen: `{klantbericht}`, `{beleidsruimte}`, `{vervolgactie}`.
- Succescriterium: voelt de klant zich gehoord en is de volgende stap duidelijk?
