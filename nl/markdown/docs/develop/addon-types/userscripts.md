---
title: Userscripts
description: Userscripts laten je code uitvoeren naast Scratchpagina's - je kunt dingen doen zoals knoppen toevoegen, de Scratcheditor verbeteren, of wat je maar ook kunt verzinnen.
---
## Wat zijn ze?
Userscripts laten je code uitvoeren naast Scratchpagina's - je kunt dingen doen zoals knoppen toevoegen, de Scratcheditor verbeteren, of wat je ook maar kunt verzinnen.

## Hoe voeg ik een userscript toe?
**Zorg ervoor dat je Scratch Addons ververst van `chrome://extensions` nadat je veranderingen maakt aan je addon.** 
Ga naar de manifest van je addon (addon.json) en voeg een eigenschap toe genaamd `userscripts"`. 
Deze eigenschap moet een array zijn. 
Elk item van de array moet de volgende eigenschappen hebben: `"url"` en `"matches"`. 
`"url"` moet een relatieve URL tot een JavaScript-bestand zijn. 
`"matches"` moet een array van URLs zijn waar je de userscript op wilt uitvoeren. Je kunt asterisken (sterretjes) gebruiken.
Voorbeeldmanifest:
```json
{
  "name": "Scratch Berichtgeving",
  "description": "Laat je makkelijker je Scratchberichten lezen en erop antwoorden.",
  "userscripts": [
    {
      "url": "userscript.js",
      "matches": ["https://scratch.mit.edu/*"]
    },
    {
      "url": "second_userscript.js",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Hoe ziet het JavaScript-bestand eruit?
Userscript JS-bestanden hebben een specifieke structuur nodig om te werken. 
Voor userscripts **moet** je alle code in een functie zetten die er zo uitziet:
```js
export default async function ({ addon, global, console }) {
  console.log("Hallo, " + await addon.auth.fetchUsername());
}
```
Als je code in functies wilt abstraheren om het overzichtelijker te maken, moet je ze includeren in de hoofdfunctie: 
**Dit zal werken:**
```js
export default async function ({ addon, global, console }) {
  // Dit werkt!
  zegHallo();
  async function zegHallo() {
    console.log("Hallo, " + await addon.auth.fetchUsername());
  }
}
```
**Dit zal NIET werken:**
```js
export default async function ({ addon, global, console }) {
  // Dit werkt NIET!
  zegHallo();
}
async function zegHallo() {
  console.log("Hallo, " + await addon.auth.fetchUsername());
  // Error: addon is niet gedefinieerd!
}
```

## [`addon.*` API's](/docs/developing/addon-apis-reference)
Je kunt toegang krijgen tot veel  `addon.*`-API's van userscripts. Voor meer informatie, check de documentatie.

## Technische aspecten van userscripts
Userscripts voeren uit nadat de Scratchpagina volledig is geladen - in andere woorden, ze voeren uit in de `defer`-stand.
Technisch gezien is elke userscript een JavaScript-module die een functie exporteert. JavaScript-modules voeren altijd uit op "stricte modus". 
Dit betekent dat userscripts van dezelfde addon GEEN variabelen en functies delen! Als je dat wilt doen, moet je het `global`-object gebruiken (meer informatie beneden).
Scratch Addons noemt dan die functiemodules geëxporteerd, waardoor het toegang krijgt tot de `addon.*`-API's, net zoals speciale wrappers:
- `addon`: geeft userscripts toegang tot de [`addon.*`-API's](/docs/developing/addon-apis-reference).
- `global`: dit een een gedeeld object tussen alle userscripts van dezelfde addon. **Voorbeeld:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.zegHallo = () => console.log("Hallo, " + addon.auth.fetchUsername());
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.zegHallo();
  // Dit werkt zolang userscript-1.js voor userscript-2.js in de userscripts-array staat in de addon-manifest.
}
```
- `console`: dit is een wrapper die je makkelijk laat zien welke addon de log die je ziet heeft getriggerd.

## Userscripts debuggen
**Zorg ervoor dat je Scratch Addons ververst van `chrome://extensions` na het maken van veranderingen aan je addon.**
Om userscripts te debuggen, zorg er eerst voor dat je addon aanstaat.
Ga dan naar een URL waar je hebt gespecificeerd waar je userscript zou moeten uitvoeren.
Open de console door Ctrl+Shift+J in te voeren.
Je zou console-logs moeten zien bij addons, inclusief de jouwe. Als je goed bent in devtools, zal je geen probleem hebben met breakpoints in je code zetten.
Pro-tip: als je de `addon.*`-API wilt testen zonder steeds je bestand te veranderen, maak dan je addon `window.addon = addon;` (binnen de hoofdfunctie), en je zou in de console toegang moeten hebben tot het `addon`-object van je addon. Zorg ervoor dat je die regel verwijdert voordat je bijdraagt aan het archief! Userscripts zouden het globale object niet moeten vervuilen.
