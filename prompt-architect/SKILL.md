---
name: prompt-architect
description: >-
  De uitgebreide prompt-bouwer voor professioneel werk. Voert een diep, vakgericht interview, bouwt de prompt met professionele technieken (rol, voorbeelden, structuur, succescriteria), test hem proefdraaiend, beoordeelt het resultaat kritisch en itereert, en levert een herbruikbare template met variabelen. Gebruik deze skill wanneer de gebruiker termen gebruikt zoals "ultieme prompt", "herbruikbare prompt", "prompt-template", "een prompt die ik vaker gebruik", "test en verbeter deze prompt", "bouw een promptsysteem", "vakgerichte prompt voor [domein]", of wanneer iemand een prompt structureel inzet in plaats van eenmalig. Geschikt voor zwaarder werk: klantcommunicatie, cold outreach, contentmarketing, technische specs, analyse, klantenservice. Wil de gebruiker maar een snelle, eenmalige prompt, gebruik dan promptmaker. Het gesprek voer je in de taal van de gebruiker; de prompt zelf in de taal van de use-case.
---

# Prompt-architect

De diepe versie van de promptmaker. Waar de gratis promptmaker één goede prompt voor het moment maakt, levert de prompt-architect een prompt-asset: vakgericht opgebouwd, getest tegen echte output, verbeterd, en herbruikbaar gemaakt met variabelen. Het verschil zit niet in "een betere prompt", maar in een ander soort uitkomst, een systeem dat je honderd keer gebruikt.

De skill werkt in vier fases en gebruikt twee naslagbestanden:

- `references/domeinen.md` patronen per vakgebied: wat je extra moet uitvragen en hoe de prompt eruitziet.
- `references/technieken.md` de professionele bouwtechnieken (rol, voorbeelden, structuur, succescriteria, variabelen).

Lees het relevante deel van een naslagbestand op het moment dat je het nodig hebt, niet alles vooraf.

## Wanneer deze skill, wanneer de andere

Deze skill is de zware versie en hoort bij professioneel of herbruikbaar werk. Blijkt tijdens Fase 0 of Fase 1 dat de gebruiker eigenlijk maar een snelle, eenmalige prompt wil en niets hergebruikt of getest hoeft te worden, bied dan aan om over te schakelen naar de lichtere promptmaker in plaats van het volledige protocol over hem heen te storten. Voorbeeld: "Dit is een eenmalige klus. Wil je dat ik er snel een goede prompt van maak, of bouwen we toch het volledige, herbruikbare asset?"

## Vaste regels

1. Het gesprek voer je in de taal van de gebruiker.
2. De prompt-template en alle voorbeeldoutput lever je in de taal van de use-case, niet automatisch in de taal van het gesprek. Stel de doeltaal vast in Fase 0 en vraag het bij twijfel.
3. Geen em-dashes in de Nederlandse tekst. Gebruik komma's, dubbele punten of haakjes.
4. Doe de fases op volgorde. Sla niets stilzwijgend over.
5. Construeer niet op de gok. Als een fase informatie mist, vraag het of benoem de aanname expliciet.
6. De kwaliteitslus (Fase 3) is niet optioneel. Een ongeteste prompt is geen prompt-asset.
7. Lever de eindprompt als herbruikbare template met duidelijk gemarkeerde variabelen.

## Fase 0: Context, vakgebied en taal vaststellen

Bepaal drie dingen:

1. **Het vakgebied of de use-case.** Mail, klantcommunicatie, cold outreach, content, technische spec, analyse, klantenservice, iets anders? Lees vervolgens het bijbehorende blok in `references/domeinen.md`. Staat de use-case er niet bij, werk dan met het algemene raamwerk (Context, Doel, Kaders, Voorbeeld) en de technieken uit `references/technieken.md`.
2. **Herbruikbaarheid.** Is dit een prompt voor één keer of zet de gebruiker hem structureel in? Bij eenmalig gebruik, overweeg de overstap naar promptmaker (zie hierboven). Bij structureel gebruik bouw je later variabelen in.
3. **De doeltaal van de prompt.** Welke taal moet de uiteindelijke output hebben? Dit hoeft niet de taal van het gesprek te zijn.

## Fase 1: Diepte-interview

Stel de vragen die het domeinblok voorschrijft, plus deze vaste set waar relevant:

- Wie is de afzender en wie de ontvanger, en wat is hun relatie?
- Wat is het exacte doel, en waaraan zie je achteraf dat het gelukt is? (Dit worden later je succescriteria.)
- Welke kaders gelden: lengte, toon, format, taal, dingen die juist niet mogen?
- Zijn er voorbeelden van goede en van slechte output om naar te wijzen?
- Voor welk model of welke plek is de prompt bedoeld? (Een chatvenster, een geautomatiseerde stap, een document.)
- Welke variabelen veranderen per keer als de prompt herbruikbaar moet zijn?

Bundel de vragen verstandig. Vraag niet naar wat de gebruiker al gaf. Stel nooit meer dan zes vragen in één beurt. Is de prompt eenmalig, sla dan de vragen over herbruikbaarheid en variabelen over.

## Fase 2: Constructie

Bouw de prompt volgens `references/technieken.md`, in de doeltaal uit Fase 0. Verwerk minimaal:

- **Rolinstructie** geef de AI een heldere rol en expertise die bij de taak past.
- **Context en doel** expliciet, met de succescriteria erin verwerkt.
- **Structuur** vraag waar nuttig om een vast outputformaat (kopjes, een lijst, of een schema met tags of JSON als de output verder verwerkt wordt).
- **Voorbeelden** verwerk minstens één voorbeeld van gewenste output als de gebruiker er een gaf. Bij stijlgevoelig werk is dit de belangrijkste hefboom: bouw het voorbeeld ín de template zodat het elke keer meewerkt.
- **Kaders en negatieve voorbeelden** lengte, toon, en expliciet wat niet mag.
- **Variabelen** als de prompt herbruikbaar is, vervang de wisselende stukken door duidelijk gemarkeerde plaatshouders, bijvoorbeeld `{doelgroep}`, `{onderwerp}`, `{lengte}`.

Toon de eerste versie van de prompt aan de gebruiker.

## Fase 3: Kwaliteitslus

Dit is de kern van het verschil. Een prompt is pas af als hij getest is.

1. **Proefdraaien.** Draai de prompt zelf en genereer een voorbeeldoutput in de doeltaal. Heeft de gebruiker geen concrete invulling voor de variabelen gegeven, verzin dan zelf één realistische testinvoer en label die duidelijk als "voorbeeldinvoer", zodat de lus niet stilvalt. Laat invoer en output zien.
2. **Kritisch beoordelen.** Leg de output naast de succescriteria uit Fase 1. Wees streng, in de geest van scherp tegendenken. Drie vragen:
   - Doet de output precies wat het doel vroeg, of zit er drift in?
   - Waar is de output zwak, generiek, of mis je iets?
   - Welke instructie in de prompt veroorzaakte dat, en hoe pas je hem aan?
3. **Verbeteren.** Pas de prompt gericht aan op basis van wat de proefoutput liet zien. Draai indien nodig nog een keer.

Harde grens: maximaal twee iteraties. Is de prompt na twee rondes nog niet goed, stop dan en wees eerlijk. Lever de beste versie tot dan toe op met een korte notitie over wat nog niet opgelost is en waarom (bijvoorbeeld: de gebruiker moet eerst een echt voorbeeld aanleveren). Blijf niet eindeloos draaien.

Betrek de gebruiker: laat de proefoutput en je oordeel zien, en vraag of dit de goede kant op gaat voordat je de definitieve versie oplevert.

## Fase 4: Oplevering

Lever het volledige asset op:

- **De definitieve prompt-template** in een kopieerbaar blok, in de doeltaal, met de variabelen duidelijk gemarkeerd.
- **Gebruiksaanwijzing** een paar regels: welke variabelen je invult, en waar de prompt voor bedoeld is.
- **De succescriteria** kort, zodat de gebruiker zelf kan zien of een toekomstige output goed is.
- **Bibliotheek-notitie** een korte regel met een voorgestelde naam en categorie, zodat de gebruiker de prompt in zijn eigen verzameling kan opslaan en terugvinden.

## Outputstructuur

Het buitenste blok hieronder is alleen ter illustratie:

````
## Fase 0 en 1: Wat ik moet weten
[gerichte vragen, gegroepeerd]

[Na antwoorden:]

## Fase 2: Eerste versie
```
[prompt v1 met variabelen, in de doeltaal]
```

## Fase 3: Proef en beoordeling
**Voorbeeldinvoer:** [door gebruiker gegeven, of zelf gemaakt en als zodanig gelabeld]
**Proefoutput:** [voorbeeldresultaat]
**Oordeel:** [streng, tegen de succescriteria]
**Aanpassing:** [wat en waarom]

[eventueel een tweede iteratie, daarna stoppen]

## Fase 4: Je prompt-asset
```
[definitieve herbruikbare template]
```
**Variabelen:** [lijst met wat je invult]
**Bedoeld voor:** [korte gebruiksaanwijzing]
**Succescriteria:** [waaraan een goede output voldoet]
**Voor je bibliotheek:** [voorgestelde naam en categorie]
````

## Belangrijke uitvoeringsdetails en valkuilen

- De diepte zit in Fase 1 en Fase 3. Een diepte-interview zonder kwaliteitslus is een halve prompt-architect.
- Valkuil: het volledige protocol over een eenmalige klus heen storten. Bied dan promptmaker aan.
- Valkuil: blijven itereren in Fase 3. Twee rondes is de grens, daarna eerlijk zijn.
- Valkuil: stilvallen omdat er geen testinvoer is. Maak er zelf een, gelabeld als voorbeeld.
- Valkuil: de template in de taal van het gesprek leveren in plaats van de doeltaal van de use-case.
- Pretendeer geen objectiviteit in je oordeel. Het is een strenge tweede lezing, geen meetlat.
- Verzin geen succescriteria die de gebruiker niet impliceerde. Leid ze af uit het doel en check ze terug.
- Geen meta-opmerkingen over het proces aan het einde. De opgeleverde template sluit af.
