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
  "enabled_by_default": false
}
```

## Hoe ziet het JavaScript-bestand eruit?
Userscripts JS-bestanden hebben een specifieke structuur nodig om te werken. 
Voor userscripts **moet** je alle code in een functie zetten die er zo uitziet:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + addon.auth.username);
}
```
Als je je eigen functies wilt schrijven voor overzichtelijkere code, moet je ze in de hoofdfunctie doen: 
**Dit zal werken:**
```js
export default async function ({ addon, global, console }) {
  // Dit werkt!
  sayHello();
  function sayHello() {
    console.log("Hallo, " + addon.auth.username);
  }
}
```
**Dit zal NIET werken:**
```js
export default async function ({ addon, global, console }) {
  // Dit werkt NIET!
  sayHello();
}
function sayHello() {
  console.log("Hallo, " + addon.auth.username);
  // Error: addon is niet gedefinieerd!
}
```

## [`addon.*` API's](/docs/developing/addon-apis-reference)
Je kunt toegang krijgen tot sommige  `addon.*` API's van userscripts. Voor meer informatie, check de documentatie.

## Technische aspecten van userscripts
Userscripts run after the Scratch page has fully loaded - in other words, they run in `defer` mode.
Technically speaking, each userscript is a JavaScript module that exports a function. JavaScript modules always run on "strict mode".  
This means that userscripts of the same addon DO NOT share variables and functions! If you want to do that, you should use the `global` object (more info below).
Scratch Addons then calls that function modules exported, giving it access to the `addon.*` APIs, as well as special wrappers:  
- `addon`: gives userscripts access to the [`addon.*` APIs](/docs/developing/addon-apis-reference).
- `global`: this is a shared object between all userscripts of the same addon. **Example usage:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.username);
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // This works, as long as in the addon manifest, userscript-1.js is before userscript-2.js in the userscripts array.
}
```
- `console`: this is a wrapper that allows you to see what addon triggered the log you're seeing easily.

## Debugging userscripts
**Make sure to refresh Scratch Addons from `chrome://extensions` after doing any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to this repo! Userscripts must not pollute the global object.