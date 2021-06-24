---
title: Userscript
description: Gli userscript ti permettono di eseguire del codice all'interno delle pagine di Scratch - puoi aggiungere pulsanti, migliorare l'editor di Scratch e fare tutto quello che ti viene in mente.
---
## Cosa sono?
Gli userscript ti permettono di eseguire del codice all'interno delle pagine di Scratch - puoi aggiungere pulsanti, migliorare l'editor di Scratch e fare tutto quello che ti viene in mente.

## Come si fa ad aggiungere uno userscript?
**Assicurati di aggiornare Scratch Addons in `chrome://extensions` dopo avere apportato qualunque cambiamento al tuo addon.**  
Vai al manifest del tuo addon (addon.json) e aggiungi una proprietà chiamata `userscripts"`.  
Questa proprietà deve essere un array.  
Ogni elemento dell'array deve avere le seguenti proprietà: `"url"` e `"matches"`.  
`"url"` deve essere un URL relativo ad un file JavaScript.  
`"matches"` deve essere un array di URL in cui vuoi eseguire il tuo userscript. Puoi usare asterischi come caratteri jolly.
Esempio di manifest:
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
  "enabled_by_default": false
}
```

## Come è fatto il file JavaScript?
Gli userscript JS per poter funzionare devono avere una precisa struttura.  
Per gli userscript **devi** inserire tutto il tuo codice all'interno di una funzione come questa:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + addon.auth.username);
}
```
Se vuoi scrivere le tue funzioni in modo che il codice sia più pulito, devi inserirle dentro la funzione principale:  
**Questo funziona:**
```js
export default async function ({ addon, global, console }) {
  // This works!
  sayHello();
  function sayHello() {
    console.log("Hello, " + addon.auth.username);
  }
}
```
**Questo NON funziona:**
```js
export default async function ({ addon, global, console }) {
  // Questo NON funziona!
  sayHello();
}
function sayHello() {
  console.log("Hello, " + addon.auth.username);
  // Errore: addon non è definito!
}
```

## [`addon.*` APIs](/docs/developing/addon-apis-reference)
Puoi accedere molte delle API `addon.*` negli userscript. Per ulteriori informazioni consulta la documentazione.

## Aspetti tecnici degli userscript
Gli userscript vengono eseguiti dopo che la pagina Scratch è stata completamente caricata - in altre parole vengono eseguiti in modalità `defer`.
In termini tecnici, ogni userscript è un modulo JavaScript che esporta una funzione. I moduli JavaScript vengono sempre eseguiti in "strict mode".  
Questo significa che gli userscript dello stesso addon NON condividono variabili e funzioni! Se vuoi farlo devi usare l'oggetto `global` object (vedi qui sotto per ulteriori informazioni).
Scratch Addon chiama questi moduli funzione esportati dando loro accesso alle API `addon.*` oltre ad alcuni wrapper speciali:  
- `addon`: fornisce allo script persistente accesso alla [`addon.*` APIs](/docs/developing/addon-apis-reference).
- `global`: questo è un oggetto condiviso tra tutti gli userscript dello stesso addon. **Esempio di uso:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.username);
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // Questo funziona se, nel manifest dell'addon, userscript-1.js è prima di userscript-2.js nell'array userscripts.
}
```
- `console`: questo wrapper ti permette di vedere facilmente quale addon ha attivato il log che stai guardando.

## Debug degli userscript
**Assicurati di aggiornare Scratch Addon alla pagina `chrome://extensions` dopo ogni cambiamento apportato al tuo addon.** 
Per debuggare gli userscript assicurati prima di tutto di abilitare il tuo addon. 
Poi vai all'URL dove il tuo userscript dovrebbe essere eseguito.
Apri la console premendo Ctrl+Shift+J. 
Dovresti vedere i logs degli addons, inclusi i tuoi. Se sei un professionista dei devtools non avrai problemi a definire i necessari breakpoint nel tuo codice. 
Suggerimento da professionisti: se vuoi testare la API `addon.*` senza modificare ogni volta il tuo file, inserisci nel tuo addon l'istruzione `window.addon = addon;` (dentro la funzione principale) così potrai accedere all'oggetto `addon` del tuo addon dalla console. Assicurati di rimuovere questa istruzione prima di rilasciare il tuo contributo in questo repository! Gli userscript non devono "sporcare" l'oggetto global.