---
title: Uporabniške skripte
description: Uporabniške skripte omogočajo izvajanje kode na Scratchevi spletni strani - z njimi lahko dodate gumbe, izboljšate Scratchev urejevalnik, in sploh vse, kar si lahko predstavljate.
---
## Kaj to so?
Uporabniške skripte omogočajo izvajanje kode na Scratchevi spletni strani - z njimi lahko dodate gumbe, izboljšate Scratchev urejevalnik, in sploh vse, kar si lahko predstavljate.

## Kako dodam uporabniško skripto?
**Vedno znova naložite Scratch Addons na strani `chrome://extensions`, potem ko spremenite vaš dodatek.**  
Odprite datoteko addon.json in dodajte lastnost `userscripts"`.  
Ta lastnost mora biti seznam.  
Vsak element seznama mora imeti naslednji lastnosti: `"url"` in `"matches"`.  
`"url"` mora biti relativen URL datoteke JavaScript.  
`"matches"` mora biti seznam URL-jev, na katerih se naj uporabniška skripta izvaja. Lahko uporabite zvezdice.
Primer datoteke addon.json:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
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

## What does the JavaScript file look like?
Userscript JS files require a specific structure to work.  
For userscripts, you **must** wrap all your code inside a function looking like this:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + await addon.auth.fetchUsername());
}
```
If you want to abstract code into functions for cleaner code, you should include them inside the main function:  
**This will work:**
```js
export default async function ({ addon, global, console }) {
  // This works!
  sayHello();
  async function sayHello() {
    console.log("Hello, " + await addon.auth.fetchUsername());
  }
}
```
**To NE bo delovalo:**
```js
export default async function ({ addon, global, console }) {
  // This WON'T work!
  sayHello();
}
async function sayHello() {
  console.log("Hello, " + await addon.auth.fetchUsername());
  // Error: addon is not defined!
}
```

## [Vmesniki `addon.*`](/docs/developing/addon-apis-reference)
You can access many `addon.*` APIs from userscripts. For more information, check the documentation.

## Tehnične lastnosti uporabniških skript
Uporabniške skripte se začnejo izvajati, ko se je stran do konca naložila - z drugimi besedami: delujejo v načinu `defer`.
Vsaka uporabniška skripta je modul JavaScript, ki izvozi funkcijo. Moduli JavaScript se vedno izvajajo v "strogem načinu".  
To pomeni, da si uporabniške skripte istega dodatka NE delijo spremenljivk in funkcij! Če to potrebujete, uporabite objekt `global` (več informacij je spodaj).
Scratch Addons pokliče funkcijo, ki jo je modul izvozil, ter ji da dostop do vmesnikov `addon.*` in posebnih objektov:
- `addon`: uporabniškim skriptam omogoči dostop do [vmesnikov `addon.*`](/docs/developing/addon-apis-reference).
- `global`: ta objekt si delijo vse uporabniške skripte istega dodatka. **Primer uporabe:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.fetchUsername());
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // To deluje, če je v seznamu uporabniških skript v datoteki addon.json userscript-1.js pred userscript-2.js.
}
```
- `console`: omogoči, da v brskalnikovem orodju za razvijalce vidite, kateri dodatek je kaj izpisal.

## Razhroščevanje uporabniških skript
**Make sure to refresh Scratch Addons from `chrome://extensions` after making any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to the repo! Userscripts must not pollute the global object.
