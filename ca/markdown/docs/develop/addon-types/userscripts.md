---
title: Userscripts
description: "Els userscripts permeten executar codi a les pàgines de Scratch: pots fer coses com afegir botons, millorar l'editor de Scratch o qualsevol cosa que imaginis."
---
## Que són?
Els userscripts permeten executar codi a les pàgines de Scratch: pots fer coses com afegir botons, millorar l'editor de Scratch o qualsevol cosa que imaginis.

## Com puc afegir un userscript?
**Assegura't d'actualitzar el Scratch Addons des de `chrome://extensions` després de fer qualsevol canvi al teu addon.**
Vés al manifest del teu addon (addon.json) i afegeix una propietat anomenada `userscripts"`.
Aquesta propietat ha de ser a una matriu.
Cada element de la matriu ha de tenir les propietats següents: `"url"` i `"matches"`.
`"url"` ha de ser un URL relatiu a un fitxer JavaScript.
`"matches"` ha de ser una matriu d'URL on vols executar l'userscript. Pots utilitzar asteriscs.
Exemple de manifest:
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

## Com es veu el fitxer JavaScript?
Els fitxers Userscripts JS requereixen una estructura específica per funcionar.
Per als scripts d'usuari, **has** d'embolicar tot el teu codi dins d'una funció semblant a aquesta:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + await addon.auth.fetchUsername());
}
```
Si vols escriure les vostres pròpies funcions per tenir un codi més net, hauríes d'incloure-les dins de la funció principal:
**Això funcionarà:**
```js
export default async function ({ addon, global, console }) {
  // This works!
  sayHello();
  function sayHello() {
    console.log("Hello, " + await addon.auth.fetchUsername());
  }
}
```
**Això NO funcionarà:**
```js
export default async function ({ addon, global, console }) {
  // This WON'T work!
  sayHello();
}
function sayHello() {
  console.log("Hello, " + await addon.auth.fetchUsername());
  // Error: addon is not defined!
}
```

## [`addon.*` APIs](/docs/developing/addon-apis-reference)
Podeu accedir a algunes API `addon.*` des dels userscripts. Per a més informació, consulta la documentació.

## Aspectes tècnics dels userscripts
Userscripts s'executen després de que la pàgina Scratch s'hagi carregat completament, és a dir, s'executen en mode `defer`.
Tècnicament parlant, cada userscript és un mòdul JavaScript que exporta una funció. Els mòduls JavaScript sempre s'executen en "strict mode".
Això vol dir que els userscripts del mateix addon NO comparteixen variables i funcions! Si vols fer-ho, hauríes d'utilitzar l'objecte `global` (més informació a continuació).
A continuació, Scratch Addons crida als mòduls de funció exportats, donant-li accés a les API `addon.*`, així com a wrappers especials:
- `addon`: dóna accés als userscripts a les [`addon.*` API](/docs/developing/addon-apis-reference).
- `global`: aquest és un objecte compartit entre tots els userscripts del mateix complement. **Exemple d'ús:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.fetchUsername());
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // Això funciona, sempre que al manifest del addon, userscript-1.js estigui abans que userscript-2.js a la matriu userscripts.
}
```
- `console`: aquest és un wrapper que permet veure quin addon ha activat el registre que esteu veient fàcilment.

## Depuració d'userscripts
**Assegura't d'actualitzar els complements de Scratch des de `chrome://extensions` després de fer qualsevol canvi al teu addon.**
Per depurar els userscripts, primer assegura'ts que el teu addon estigui habilitat.
A continuació, vés a un URL on has especificat que s'hauria d'executar el vostre userscript.
Obre la consola prement Ctrl+Maj+J.
Hauríes de veure els registres de la consola dels addons, inclòs el teu. Si ets un professional del devtools, no tindrás cap problema per establir punts d'interrupció al teu codi.
Suggeriment: si vols provar l'API `addon.*` sense canviar el fitxer cada vegada, fes que el teu addon sigui `window.addon = addon;` (dins de la funció principal) i podrás accedir al `addon` del teuaddon objecte de complement des de la consola. Assegura't d'eliminar aquesta línia abans de contribuir a aquest repo! Els Userscripts no han de contaminar l'objecte global.
