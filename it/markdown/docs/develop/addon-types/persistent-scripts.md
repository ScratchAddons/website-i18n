---
title: Script Persistenti
description: Gli script persistenti ti permettono di eseguire JavaScript in background! Sono eccezionali per notificare qualcosa all'utente o per precaricare i dati in modo che siano pronti quando l'utente ne ha bisogno.
---

> **Raccomandiamo di evitare l'uso degli script persistenti ogni volta che è possibile. La futura migrazione a  [Manifest V3](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-migration/#background-service-workers) richiederà di usare i service workers invece delle pagine in background, rendendo gli script persistenti una sfida. Meno script persistenti ci saranno quando migreremo, più semplice sarà la migrazione.**

## Cosa sono?
Gli script persistenti ti permettono di eseguire JavaScript in background! Sono eccezionali per notificare qualcosa all'utente o per precaricare i dati in modo che siano pronti quando l'utente ne ha bisogno.

## Come faccio ad aggiungere uno script persistente?
**Assicurati di aggiornare Scratch Addon in `chrome://extensions` dopo avere apportato qualunque cambiamento al tuo addon.**  
Vai al manifest del tuo addon (addon.json) e aggiungi una proprietà chiamata `"persistent_scripts"`.  
Questa proprietà deve essere un array anche se il tuo addon userà un solo script persistente.  
Ogni elemento dell'array deve essere un URL relativo che punti a un file JS.
Esempio di manifest:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "persistent_scripts": ["background.js"],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## Come è fatto il file JavaScript?
Gli script persistenti, così come gli userscript, richiedono una specifica struttura per funzionare.  
Per gli script persistenti **devi** inserire tutto il codice dentro una funzione come questa:
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  console.log("Hello, " + addon.auth.username);
}
```
Se vuoi scrivere le tue funzioni in modo che il codice sia più pulito, devi inserirle dentro la funzione principale:  
**Questo funziona:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // Questo funziona!
  sayHello();
  function sayHello() {
    console.log("Hello, " + addon.auth.username);
  }
}
```
**Questo NON funziona:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // Questo NON funziona!
  sayHello();
}
function sayHello() {
  console.log("Hello, " + addon.auth.username);
  // Errore: addon non è definito!
}
```

## [`addon.*` API](/docs/developing/addon-apis-reference)
Attraverso gli script persistenti puoi accedere molte delle API `addon.*`. Per ulteriori informazioni consulta la documentazione.

## Aspetti tecnici degli script persistenti
In termini tecnici, ogni script persistente è un modulo JavaScript che esporta una funzione. I moduli JavaScript vengono sempre eseguiti in "strict mode".    
Questo vuol dire che gli script persistenti dello stesso addon NON condividono variabili e funzioni! Se vuoi che vengano condivisi devi usare l'oggetto `global` (vedi sotto per ulteriori informazioni).
Scratch Addon chiama poi questi moduli funzione esportati, dando loro accesso alle API `addon.*` oltre a speciali wrapper:  
- `addon`: fornisce allo script persistente accesso alle [`addon.*` API](/docs/developing/addon-apis-reference).
- `global`: questo è un oggetto condiviso tra tutti gli script persistenti dello stesso addon. **Esempio di uso:**
```js
// background-1.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.username);
}

// background-2.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayHello();
  // Questo funziona se, nel manifest dell'addon, background-1.js è prima di background-2.js nell'array persistent_scripts.
}
```
- `console`: questo wrapper ti permette di vedere facilmente quale addon ha attivato il log che stai guardando.
- `setTimeout` e `setInterval`: se il tuo addon viene disabilitato mentre viene eseguito, Scratch Addon deve attendere per arrestare tutti i timeouts e gli intervals pendenti. Per raggiungere questo obiettivo gli addon devono usare questi wrappers invece di `window.setTimeout` e `window.setInterval`.
- `clearTimeout` e `clearInterval`: anche per queste è necessario definire dei wrapper per evitare leak di memoria - Scratch Addon non saprebbe infatti che hai cancellato un timeout o un intervallo, e continuerebbe a memorizzare il suo timeout/interval ID senza ragione. Non usare né `window.clearTimeout` né `window.clearInterval`.

## Debug degli script persistenti
**Assicurati di aggiornare Scratch Addon alla pagina `chrome://extensions` dopo ogni cambiamento apportato al tuo addon.**  
Per debuggare gli script persistenti assicurati prima di tutto di abilitare il tuo addon.  
Poi vai alla pagina `chrome://extensions`, assicurati che la modalità sviluppatore sia attivata e cerca Scratch Addon.  
Clicca dove dice "inspect views: background/background.html".  
E' tutto - troverai lì tutti i log alla console del tuo addon e, se sei un professionista dei devtools, non avrai alcun problema ad inserire dei breakpoints nel tuo codice.  
Suggerimento da professionisti: se vuoi testare la API `addon.*` senza modificare ogni volta il tuo file, esegui nel tuo addon `window.addon = addon;` (dentro la funzione principale) così potrai accedere all'oggetto  `addon` del tuo addon dalla console. Assicurati di rimuovere questa istruzione prima di rilasciare il tuo contributo a questo repository! Gli script persistenti non devono "sporcare" l'oggetto global.