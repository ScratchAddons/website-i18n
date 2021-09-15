---
title: Skripte v ozadju
description: Skripte v ozadju omogočajo izvajanje kode JavaScript v ozadju, neodvisno od odprtih Scratchevih strani! Lahko obvestijo uporabnika o stvareh ali pa vnaprej naložijo podatke, da so pripravljeni, ko jih uporabnik potrebuje.
---

> **Če je mogoče, prosimo, da se skriptam v ozadju izogibate. Ko bomo začeli uporabljati [Manifest V3](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-migration/#background-service-workers), bomo morali namesto strani v ozadju uporabiti vmesnik Service Workers, zato bo delo s skriptami v ozadju težje. Najbolje je, da je skript v ozadju čim manj.**

## Kaj to so?
Skripte v ozadju omogočajo izvajanje kode JavaScript v ozadju, neodvisno od odprtih Scratchevih strani! Lahko obvestijo uporabnika o stvareh ali pa vnaprej naložijo podatke, da so pripravljeni, ko jih uporabnik potrebuje.

## Kako dodam skripto v ozadju?
**Vedno znova naložite Scratch Addons na strani `chrome://extensions`, potem ko spremenite vaš dodatek.**  
Odprite datoteko addon.json in dodajte lastnost `"persistent_scripts"`.  
Ta lastnost mora biti seznam, tudi če bo imel dodatek samo eno skripto v ozadju.  
Vsak element seznama mora biti relativna pot do datoteke JS.
Primer datoteke addon.json:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "persistent_scripts": ["background.js"],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## Kako izgleda datoteka JavaScript?
Skripte v ozadju, tako kot tudi uporabniške skripte, delujejo le, če so sestavljene na določen način.  
V skriptah v ozadju **mora** biti vsa koda v funkciji, ki izgleda nekako tako:
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  console.log("Hello, " + addon.auth.username);
}
```
Če bi radi za lažje berljivo kodo napisali več funkcij, to naredite znotraj glavne funkcije.  
**To deluje:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // To deluje!
  sayHello();
  function sayHello() {
    console.log("Hello, " + addon.auth.username);
  }
}
```
**To NE bo delovalo:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // To NE deluje!
  sayHello();
}
function sayHello() {
  console.log("Hello, " + addon.auth.username);
  // Napaka: addon ni definiran!
}
```

## [Vmesniki `addon.*`](/docs/developing/addon-apis-reference)
Skripte v ozadju lahko dostopajo do večine vmesnikov `addon.*`. Za več informacij preberite dokumentacijo.

## Tehnične lastnosti skript v ozadju
Vsaka skripta v ozadju je modul JavaScript, ki izvozi funkcijo. Moduli JavaScript se vedno izvajajo v "strogem načinu".  
To pomeni, da si skripte v ozadju istega dodatka NE delijo spremenljivk in funkcij! Če to potrebujete, uporabite objekt `global` (več informacij je spodaj).
Scratch Addons pokliče funkcijo, ki jo je modul izvozil, ter ji da dostop do vmesnikov `addon.*` in posebnih objektov:
- `addon`: skriptam v ozadju omogoči dostop do [vmesnikov `addon.*`](/docs/developing/addon-apis-reference).
- `global`: ta objekt si delijo vse skripte v ozadju istega dodatka. **Primer uporabe:**
```js
// background-1.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.username);
}

// background-2.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayHello();
  // To deluje, če je v seznamu persistent_scripts v datoteki addon.json background-1.js pred background-2.js.
}
```
- `console`: omogoči, da v brskalnikovem orodju za razvijalce vidite, kateri dodatek je kaj izpisal.
- `setTimeout` in `setInterval`: če je dodatek izključen med delovanjem, mora Scratch Addons ustaviti vse čakajoče zamike. Da to lahko naredi, morajo dodatki namesto `window.setTimeout` in `window.setInterval` uporabiti ti dve funkciji.
- `clearTimeout` in `clearInterval`: tudi ti dve funkciji sta zamenjani zaradi porabe spomina - Scratch Addons ne bi vedel, da ste odstranili zamik, zato bi ID tega ostal shranjen brez razloga. Funkcij `window.clearTimeout` in `window.clearInterval` ne uporabljajte.

## Razhroščevanje skript v ozadju
**Vedno znova naložite Scratch Addons na strani `chrome://extensions`, potem ko spremenite vaš dodatek.**  
Pred razhroščevanjem se prepričajte, da je dodatek vključen.  
Potem pojdite na stran `chrome://extensions`. Prepričajte se, da je vključen način za razvijalce, in poiščite Scratch Addons.  
Kliknite povezavo "inspect views: background/background.html".  
To je vse - tam bodo vsi izpisi vašega dodatka, in če ste profesionalni uporabnik orodja za razvijalce, ne boste imeli težav z dodajanjem prekinitev (breakpoints).  
Če bi radi preizkušali vmesnik `addon.*`, ne da bi vsakič spremenili skripto, uporabite `window.addon = addon;` (v glavni funkciji), da lahko iz konzole dostopate do svojega objekta `addon`. Ne pozabite te vrstice odstranite, preden dodatek prispevate na GitHub! Skripte v ozadju ne smejo onesnažiti globalnega objekta.