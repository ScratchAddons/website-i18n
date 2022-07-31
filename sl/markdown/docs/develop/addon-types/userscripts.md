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

## Kako izgleda datoteka JavaScript?
Datoteke JS uporabniških skript delujejo le, če so sestavljene na določen način.  
V uporabniških skriptah **mora** biti vsa koda v funkciji, ki izgleda nekako tako:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + await addon.auth.fetchUsername());
}
```
Če bi radi za lažje berljivo kodo napisali več funkcij, to naredite znotraj glavne funkcije.  
**To deluje:**
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
Uporabniške skripte lahko dostopajo do nekaterih vmesnikov `addon.*`. Za več informacij preberite dokumentacije.

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
**Vedno znova naložite Scratch Addons na strani `chrome://extensions`, potem ko spremenite vaš dodatek.**  
Pred razhroščevanjem se prepričajte, da je dodatek vključen.  
Potem pojdite na enega od URL-jev, na katerih naj bi se uporabniška skripta izvajala.  
Pritisnite Ctrl+Shift+J, da odprete konzolo.  
Tam boste videli izpise dodatkov, tudi vašega, in če ste profesionalni uporabnik orodja za razvijalce, ne boste imeli težav z dodajanjem prekinitev (breakpoints).  
Če bi radi preizkušali vmesnik `addon.*`, ne da bi vsakič spremenili skripto, uporabite `window.addon = addon;` (v glavni funkciji), da lahko iz konzole dostopate do svojega objekta `addon`. Ne pozabite te vrstice odstraniti, preden dodatek prispevate na GitHub! Uporabniške skripte ne smejo onesnažiti globalnega objekta.
