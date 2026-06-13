# Technieken

De professionele bouwtechnieken voor Fase 2. Pas toe wat de taak vraagt, niet alles tegelijk. Elke techniek staat met het waarom erbij, zodat je weet wanneer hij loont.

## Inhoud

1. Rolinstructie
2. Context en doel vooraan
3. Voorbeelden (few-shot)
4. Gestructureerde output
5. Stap voor stap laten redeneren
6. Succescriteria inbouwen
7. Negatieve voorbeelden en grenzen
8. Variabelen voor herbruikbaarheid
9. Volgorde en opmaak van de prompt

---

## 1. Rolinstructie

Geef de AI een heldere rol met passende expertise. "Je bent een ervaren tekstschrijver klantcommunicatie" stuurt toon en woordkeuze sterker dan een kale opdracht. Maak de rol specifiek voor de taak, niet algemeen.

## 2. Context en doel vooraan

Zet wie, wat en voor wie bovenaan, voordat de opdracht komt. De AI leest de instructie als geheel, maar context vooraan kleurt alles wat erna komt. Maak het doel concreet: niet "schrijf iets goeds" maar het resultaat dat de gebruiker voor zich ziet.

## 3. Voorbeelden (few-shot)

Eén voorbeeld van gewenste output stuurt krachtiger dan drie alinea's uitleg, zeker bij stijl, toon en format. Geef waar mogelijk een voorbeeld van goed en eventueel van slecht. Bij herbruikbare prompts: zet voorbeelden in de template zodat ze elke keer meewerken.

## 4. Gestructureerde output

Vraag om een vast format als de output verder verwerkt of vergeleken wordt:

- Voor mensen: kopjes, een vaste indeling, een lijst.
- Voor verdere verwerking door software: een schema met XML-achtige tags of JSON. Vraag dan expliciet om alleen dat format, zonder inleidende tekst eromheen.

Een vast format maakt output voorspelbaar en daarmee herbruikbaar.

## 5. Stap voor stap laten redeneren

Bij taken die denkwerk vragen (analyse, een lastige afweging, code): vraag de AI eerst stap voor stap te redeneren voordat hij een conclusie geeft. Direct om het eindantwoord vragen bij een complex probleem levert vaker een gok op. Voor eenvoudige taken is dit overbodig en maakt het de output alleen langer.

## 6. Succescriteria inbouwen

Verwerk de criteria waaraan een goede output voldoet ín de prompt, bijvoorbeeld: "De tekst is geslaagd als hij begrijpelijk is op B1-niveau en eindigt met een duidelijke vervolgstap." Dit geeft de AI een meetlat en geeft jou in Fase 3 iets om de proefoutput tegen af te zetten.

## 7. Negatieve voorbeelden en grenzen

Benoem expliciet wat niet mag: geen jargon, geen opsomming van features, geen toezeggingen buiten beleid, geen langer dan een bepaald aantal woorden. Grenzen sturen vaak net zo sterk als instructies.

## 8. Variabelen voor herbruikbaarheid

Dit maakt het verschil tussen een prompt voor nu en een asset voor honderd keer. Vervang elk stuk dat per keer verandert door een duidelijk gemarkeerde plaatshouder met accolades:

```
Schrijf een {berichttype} aan {doelgroep} over {onderwerp}.
Lengte: {lengte}. Toon: {toon}.
```

Houd de namen sprekend en consistent. Zet onderaan de template een lijstje van de variabelen, zodat de gebruiker weet wat hij invult.

## 9. Volgorde en opmaak van de prompt

Een volgorde die betrouwbaar werkt:

1. Rol en expertise.
2. Context: wie, wat, voor wie.
3. De opdracht en het doel, met succescriteria.
4. Kaders: lengte, toon, format, wat niet mag.
5. Voorbeeld of voorbeelden.
6. Eventueel: vraag om eerst te redeneren, dan pas te antwoorden.

Houd de prompt strak. Elke regel die niets stuurt, verzwakt de regels die dat wel doen.
