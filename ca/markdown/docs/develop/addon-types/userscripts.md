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
**Això NO funcionarà:**
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

## [`addon.*` APIs](/docs/developing/addon-apis-reference)
You can access many `addon.*` APIs from userscripts. For more information, check the documentation.

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
**Make sure to refresh Scratch Addons from `chrome://extensions` after making any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to the repo! Userscripts must not pollute the global object.
