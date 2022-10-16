---
title: Userscript
description: Gli userscript ti permettono di eseguire del codice all'interno delle pagine di Scratch - puoi aggiungere pulsanti, migliorare l'editor di Scratch e fare tutto quello che ti viene in mente.
---
## Cosa sono?
Gli userscript ti permettono di eseguire del codice all'interno delle pagine di Scratch - puoi aggiungere pulsanti, migliorare l'editor di Scratch e fare tutto quello che ti viene in mente.

## Come si fa ad aggiungere uno userscript?
**Assicurati di aggiornare Scratch Addon in `chrome://extensions` dopo avere apportato qualunque cambiamento al tuo addon.**  
Vai al manifest del tuo addon (addon.json) e aggiungi una proprietà chiamata `"userscripts"`.  
Questa proprietà deve essere un array.  
Ogni elemento dell'array deve avere le seguenti proprietà: `"url"` e `"matches"`.  
`"url"` deve essere un URL relativo ad un file JavaScript.  
`"matches"` deve essere un array di URL in cui vuoi eseguire il tuo userscript. Puoi usare asterischi come caratteri jolly.
Esempio di manifest:
```json
{
  "name": "Scratch Messaging",
  "description": "Ti permette di leggere e replicare facilmente ai messaggi Scratch.",
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
  // Questo funziona!
  sayHello();
  async function sayHello() {
    console.log("Hello, " + await addon.auth.fetchUsername());
  }
}
```
**Questo NON funziona:**
```js
export default async function ({ addon, global, console }) {
  // Questo NON funziona!
  sayHello();
}
async function sayHello() {
  console.log("Hello, " + await addon.auth.fetchUsername());
  // Errore: addon non è definito!
}
```

## [`addon.*` API](/docs/developing/addon-apis-reference)
You can access many `addon.*` APIs from userscripts. For more information, check the documentation.

## Aspetti tecnici degli userscript
Gli userscript vengono eseguiti dopo che la pagina Scratch è stata completamente caricata - in altre parole vengono eseguiti in modalità `defer`.
In termini tecnici, ogni userscript è un modulo JavaScript che esporta una funzione. I moduli JavaScript vengono sempre eseguiti in "strict mode".  
Questo significa che gli userscript dello stesso addon NON condividono variabili e funzioni! Se vuoi farlo devi usare l'oggetto `global` object (vedi qui sotto per ulteriori informazioni).
Scratch Addon chiama poi questi moduli funzione esportati, dando loro accesso alle API `addon.*` oltre ad alcuni speciali wrapper:
- `addon`: fornisce allo script persistente accesso alle [`addon.*` API](/docs/developing/addon-apis-reference).
- `global`: questo è un oggetto condiviso tra tutti gli userscript dello stesso addon. **Esempio di uso:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.fetchUsername());
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // Questo funziona se, nel manifest dell'addon, userscript-1.js è prima di userscript-2.js nell'array userscripts.
}
```
- `console`: questo wrapper ti permette di vedere facilmente quale addon ha attivato il log che stai guardando.

## Debug degli userscript
**Make sure to refresh Scratch Addons from `chrome://extensions` after making any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to the repo! Userscripts must not pollute the global object.
