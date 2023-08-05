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

Unlike extension content scripts and Tampermonkey userscripts, you must wrap all of your code inside a module default export:
```js
// Example userscript
export default async function ({ addon, console }) {
  console.log("Hello, " + await addon.auth.fetchUsername());
  console.log("How are you today?");
}
```

Remember that JavaScript allows functions to be declared inside other functions, for example:
```js
export default async function ({ addon, console }) {
  async function sayHelloToUser() {
    console.log("Hello, " + await addon.auth.fetchUsername());
  }

  await sayHelloToUser();
  console.log("How are you today?");
}
```

{{< admonition info >}}
You can access many `addon.*` API utilities from userscripts. For example, you can get the current username, wait until an element exists on the page, or get a reference to the Scratch VM object.

For more information, check the [API reference](/docs/reference/addon-api/).
{{< /admonition >}}


## Modifying the document HTML

Use [browser DOM APIs](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API) to customize the HTML of the page.

Here's an example:
```js
const myButton = document.createElement("button");
myButton.textContent = "Click me!";
myButton.classList.add("button");
myButton.setAttribute("title", "You're hovering a button");

const myContainer = document.querySelector(".container");
myContainer.append(myButton);
```

## Localizing userscripts

Addon userscripts sometimes need to reference English words or sentences. Make sure not to hardcode them, so that they can be part of the translation process.

{{< admonition error >}}
```js
// Don't do this:
document.querySelector(".sa-find-bar").placeholder = "Find blocks";
```
{{< /admonition >}}

To create a translatable string, follow these steps:
1. Create a file named `addon-id.json` inside the `/addon-l10n/en` folder.
2. Provide an ID for every string:
```json
{
  "addon-id/find": "Find blocks"
}
```
3. Make sure to import the `msg()` function in your userscript. The first line of your userscript should look like this:
```js
export default async function ({ addon, console, msg  }) {
                                              // ^^^
```
4. Use the `msg()` function in your code, instead of a hardcoded string:
```js
document.querySelector(".sa-find-bar").placeholder = msg("find");
```

{{< admonition info >}}
For more information about localizing userscripts, see [this page](/docs/localization/localizing-addons/).
{{</admonition >}}


## Technical details

Each userscript file is a JavaScript module that exports a function. Scratch Addons only imports the module if needed, and executes it after the page has fully loaded.

Userscripts are JavaScript modules, so they always run on ["strict mode"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). This also means that userscripts may use [top-level imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) to import other JavaScript files.

The order in which userscripts run may vary on each page load. After page load, the user might dynamically enable some addons in a custom order, so order of execution is never guaranteed. Some APIs like [`addon.tab.appendToSharedSpace`](/docs/reference/addon-api/addon.tab/addon.tab.appendtosharedspace/) attempt to fix any potential race conditions and unexpected behavior when dynamically enabling addons.

### runAtComplete

Userscripts may opt-in into being executed before the page has fully loaded by specifying `"runAtComplete": false` in the addon manifest, once for each userscript.

As of now, only `document.head` is guaranteed to exist when running a userscript early. In the future, `document.body` will also be guaranteed to exist, so no userscripts will ever run before the HTML document loaded enough to reach `</head> <body>`.
