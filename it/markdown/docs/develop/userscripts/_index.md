---
title: Userscript
description: Gli userscript sono file JavaScript che vengono eseguiti ogni volta che l'utente carica una pagina di Scratch. Possono modificare il codice HTML del documento, aggiungere nuovi pulsanti, personalizzare il comportamento dell'editor di Scratch e molto altro ancora.
---

Gli userscript sono file JavaScript che vengono eseguiti ogni volta che l'utente carica una pagina di Scratch. Possono modificare il codice HTML del documento, aggiungere nuovi pulsanti, personalizzare il comportamento dell'editor di Scratch e molto altro ancora.

In modo simile agli userscript che potresti scaricare per gestori di userscript come Tampermonkey o Greasemonkey, gli userscript di Scratch Addons consistono di porzioni di codice JavaScript che vengono eseguite nello stesso contesto di esecuzione del codice JavaScript di Scratch. Nelle terminologia delle estensioni del browser, questo contesto di esecuzione è spesso chiamato il "main world".

Anche se gli userscript di Scratch Addons fanno parte di un'estensione del browser, non possono accedere a nessuna API `chrome.*` or `browser.*`. Al contrario, Scratch Addons offre una [`API addon.*`](/docs/reference/addon-api/). 


## Dichiarazione di userscript nel file manifest dell'addon

{{< admonition warning >}}
Per avere effetto, **alcune modifiche richiedono di ricaricare l'estensione** da `chrome://extensions`. Ad esempio è necessario quando si modifica il file manifest dell'addon.

Quando cambi il sorgente di uno userscript JavaScript che esiste già non è necessario ricaricare l'estensione. In questi casi è sufficiente ricaricare la pagina.
{{< /admonition >}}

Gli userscript sono dichiarati nell'array "userscripts".

Ogni elemento dell'array deve avere le seguenti proprietà:
- `"url"`: l'URL relativo di un file Javascript.
- `"matches"`: la lista di pagine Scratch a cui lo userscript verrà eseguito. Per ulteriori informazioni vai a [matches](/docs/reference/addon-manifest/#matches).

Esempio di manifest:
```json
{
  "name": "Copy link to comment button",
  "description": "Adds a \"Copy Link\" button to all comments on the website, next to the \"Report\" button.",
  "userscripts": [
    {
      "url": "userscript.js",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles", "studios"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Creazione del tuo primo userscript

A differenza degli script di contenuto delle estensioni e degli userscript di Tampermonkey, è necessario inserire tutto il codice all'interno di default export di un modulo:
 
```js
// Userscript di esempio
export default async function ({ addon, console }) {
  console.log("Ciao, " + await addon.auth.fetchUsername());
  console.log("Come va oggi?");
}
```

Ricorda che JavaScript permette di dichiarare funzioni all'interno di altre funzioni, ad esempio:
```js
export default async function ({ addon, console }) {
  async function sayHelloToUser() {
    console.log("Ciao, " + await addon.auth.fetchUsername());
  }

  await sayHelloToUser();
  console.log("Come va oggi?");
}
```

{{< admonition info >}}
Da uno userscript puoi accedere molte funzioni della API `addon.*`. Ad esempio, puoi sapere lo username attuale, attendere fino a che un certo elemento è presente nella pagina o ricavare un riferimento all'oggetto Scratch VM.

Per ulteriori informazioni vai alla [guida di riferimento dell'API](/docs/reference/addon-api/).
{{< /admonition >}}


## Modificare il codice HTML del documento 

Per personalizzare il codice HTML della pagina usa le [API del DOM del browser](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API).

Ecco un esempio:
```js
const myButton = document.createElement("button");
myButton.textContent = "Cliccami!";
myButton.classList.add("button");
myButton.setAttribute("title", "Stai passando con il mouse sopra ad un pulsante");

const myContainer = document.querySelector(".container");
myContainer.append(myButton);
```

## Localizzazione degli userscript

Gli userscript degli addon a volte devono mostrare parole o frasi in inglese. Assicurati di non inserirle direttamente nel codice in modo che possano entrare a far parte integrante del processo di traduzione di Scratch Addons. 

{{< admonition error >}}
```js
// NON scrivere il codice il questo modo:
document.querySelector(".sa-find-bar").placeholder = "Find blocks";
```
{{< /admonition >}}

Per creare una scritta che possa essere tradotta, segui questi passi:
1. Crea un file chiamato `addon-id.json` dentro la cartella `/addon-l10n/en`.
2. Crea un ID per ogni stringa:
```json
{
  "addon-id/find": "Find blocks"
}
```
3. Assicurati di importare la funzione `msg()` nel tuo userscript. La prima linea del tuo userscript dovrebbe essere questa:
```js
export default async function ({ addon, console, msg  }) {
                                              // ^^^
```
4. Nel tuo codice usa la funzione `msg()` invece di una stringa cablata:
```js
document.querySelector(".sa-find-bar").placeholder = msg("find");
```

{{< admonition info >}}
Per ulteriori informazioni sulla localizzazione degli userscripts vai a [questa pagina](/docs/localization/localizing-addons/).
{{</admonition >}}


## Dettagli tecnici 

Il file di ogni userscript è un modulo JavaScript che esporta una funzione. Scratch Addons importa il modulo solo se è necessario e lo esegue dopo che la pagina è stata completamente caricata.

Gli userscript sono moduli JavaScript, quindi vengono sempre eseguiti in ["strict mode"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). Questo significa che gli userscript possono usare [importazioni top-level](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) per importare altri file JavaScript.

L'ordine in cui gli userscript vengono eseguiti varia ad ogni caricamento della pagina. Dopo che la pagina è stata caricata l'utente può abilitare dinamicamente alcuni addon nell'ordine che preferisce, quindi l'ordine di esecuzione non è mai garantitoa. Alcune API, come ad esempio [`addon.tab.appendToSharedSpace`](/docs/reference/addon-api/addon.tab/addon.tab.appendtosharedspace/), tentano di risolvere ogni race condition e ogni comportamento inatteso quando si caricano dinamicamente gli addon.

### runAtComplete

Gli userscript possono scegliere di essere eseguiti prima che la pagina sia completamente caricata specificando `"runAtComplete": false` nel file manifest dell'addon. Va fatto per ogni userscript.

Al momento, solo l'esistenza di `document.head` è garantita se si esegue uno userscript in anticipo. In futuro sarà garantita anche l'esistenza di `document.body`, quindi nessuno userscript verrà eseguito prima che il documento HTML sia stato caricato abbastanza da raggiungere `</head> <body>`.
