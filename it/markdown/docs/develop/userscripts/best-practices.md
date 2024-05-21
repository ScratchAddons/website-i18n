---
title: Migliori Pratiche
description: Segui queste migliori pratiche quando scrivi o rivedi gli userstyle.
---

Segui queste migliori pratiche quando scrivi o rivedi gli userstyle.


## Manipolazione del DOM


### Usa addEventListener invece di "onevent"

Evita di definire le proprietà "onevent" degli elementi HTML, come ad esempio `onclick`. Usa invece `addEventListener`. Questo permette a più addon di registrare lo stesso evento sullo stesso elemento, senza creare conflitti.  
L'uso di "onevent" resta valido, ma solo per gli elementi che vengono creati dallo stesso addon che registra l'evento.  
In ogni caso, evita di definire gli attributi HTML "onevent", ad esempio `element.setAttribute("onclick", "non usare questo sistema")`.

{{< admonition error >}}
```js
// NON usare questo sistema:
document.querySelector(".remix-button").onclick = () => {
  prompt("Sei sicuro di voler creare un remix?");
};
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Usa invece QUESTO sistema:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Sei sicuro di voler creare un remix?");
});
```
{{< /admonition >}}

### Evita l'uso di innerHTML

Evita l'uso di `innerHTML`. Usa invece `innerText` o `textContent`.  
Dovrebbero essere evitate anche altre API che possono portare a vulnerabilità XSS, come ad esempio `insertAdjacentHTML`, `outerHTML`, `document.write()`, ecc.

{{< admonition error >}}
```js
// NON usare questo sistema:
document.querySelector(".sa-remix-button").innerHTML = `<span>Remix ${projectTitle}</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Usa invece QUESTO sistema:
const span = document.createElement("span");
span.textContent = `Remix ${projectTitle}`;
document.querySelector(".sa-remix-button").append(span);
```
{{< /admonition >}}

### Avoid using mousemove

Avoid using `mousemove` and similar DOM events that trigger very often since they are bad for performance, especially when used on the body. Use an alternative event on a child element instead whenever possible.

{{< admonition error >}}
```js
// Don't do this:
body.addEventListener("mousemove", (event) => {
  // ...
});
```
{{< /admonition >}}

### Nascondi gli elementi invece di rimuoverli

Evita di chiamare il metodo `.remove()` sugli elementi HTML in quanto, in casi estremi, può causare il blocco della pagina.  
Gli addon possono usarlo solo per gli elementi che creano essi stessi, in situazioni specifiche.

{{< admonition error >}}
```js
// NON usare questo sistema:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Usa invece QUESTO sistema:
document.querySelector(".remix-button").style.display = "none";

// Oppure questo sistema, con l'aiuto di uno userstyle:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Usa waitForElement solo quando necessario

Evita di utilizzare l'API `addon.tab.waitForElement` se è garantito che l'elemento esista. Funzionerà comunque e le prestazioni non ne risentiranno in modo significativo, ma potrebbe confondere gli altri sviluppatori che leggono il codice. L'uso di waitForElement dovrebbe di solito significare che c'è almeno uno scenario in cui l'elemento non esiste a quel punto dell'esecuzione.
Ad esempio, non è necessario utilizzare waitForElement quando si cerca di trovare i post nel forum, a meno che lo userscript non sia stato dichiarato con `"runAtComplete": false`. In quei casi, usa semplicemente `document.querySelectorAll()` normalmente.

### Usa element.closest() invece di abusare di parentElement

Evita di usare troppo spesso parentElement quando attraversi gli antenati di un elemento. Usa invece `element.closest()`, che funziona in modo molto simile a `element.querySelector()`.

{{< admonition error >}}
```js
// NON usare questo sistema:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Usa invece QUESTO sistema:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Migliori pratiche JavaScript


### Usa lo stile più moderno di JavaScript

- Dai la preferenza alle API più recenti, usando ad esempio `fetch()` invece di `XMLHttpRequest`.
- Non usare mai `==` per i confronti. Usa invece `===`.
- When listening to keyboard events, accessing `event.key` is the preferred way to know which key was pressed. In general, you should avoid `event.code` and `event.keyCode`.
- Usa la concatenazione opzionale se un oggetto potrebbe essere `null`.  
Ad esempio, `document.querySelector(".remix-button")?.textContent`.
- Usa cicli `for ... of` o usa `.forEach()`.  
Evita cicli in stile C come `for (let i = 0; i < arr.length; i++)`.

### Usa "let" invece di "const" se il valore della variabili può venire modificato

{{< admonition info >}}
Solitamente usiamo il formato `camelCase` per i nomi della variabili, senza fare differenze se sono state dichiarate con "let" o "const".  
Per i nomi delle costanti, sia che siano stringhe o numeri, solitamente usiamo il formato `SNAKE_CASE`.

Ecco un esempio:
```js
let actionCounter = 0;
actionCounter++;

const remixButton = document.querySelector(".remix-button");

const DEFAULT_ZOOM = 1.20;
```
{{< /admonition >}}

Le persone che leggono il tuo codice potrebbero supporre che una variabile dichiarata con la parola chiave "let" potrebbe essere riassegnata in un altro punto dello script. Se ciò non è vero, usa invece la parola chiave "const".
Ricorda che in JavaScript dichiarare un oggetto o un array come "const" non significa che i suoi valori siano immodificabili. I valori all'interno dell'oggetto possono ancora essere modificati, anche se la variabile stessa non può essere riassegnata.

### Non definire variabili globali

Evita di impostare proprietà dell'oggetto globale `window`, a meno che tu non stia estendendo una funzione globale come `fetch()`. 
Se più addon devono condividere informazioni o funzioni tra di loro, crea un file modulo JavaScript e importalo in entrambi gli userscript.

{{< admonition error >}}
```js
// NON usare questo sistema:
window.isDarkMode = true;
```
{{< /admonition >}}

### Non dichiarare funzioni al di fuori del default export

Non c'è nessuna necessità di dichiarare funzioni fuori dalla funzione `export default async function(){}`. JavaScript permette infatti di dichiarare funzioni all'interno di altre funzioni.

Nel caso in cui sia appropriato, puoi spostare le funzioni in file di modulo di JS separati (che non sono dichiarati come userscript nel manifesto dell'addon) ma tieni presente che i file importati non avranno accesso all'oggetto `addon`, a meno che tu non esponga una funzione di configurazione che lo prenda come argomento e chiami poi questa funzione nell'entry point dello userscript.
 

### Non rimuovere le estensioni delle funzioni

In alcuni casi, più addon potrebbero voler estendere la stessa funzione, come ad esempio i metodi di Scratch VM `XMLHttpRequest`, `fetch()` o `FileReader()`.
In questi casi uno degli userscript estenderà la funzione originale, mentre gli altri estenderanno funzioni che erano già state estese da altri. Se, ad esempio, il primo userscript che ha esteso la funzione decide di ripristinare la funzione originale (ad esempio, eseguendo  `window.fetch = realFetch`), allora tutte le altre funzioni nella "catena di estensioni" vengono perse in modo imprevisto.
Per questo motivo, le funzioni non dovrebbero essere mai ripristinate. Invece di farlo, passa gli argomenti alla funzione originale.

{{< admonition error >}}
```js
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // NON usare questo sistema:
  vm.deleteSprite = oldDeleteSprite;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Usa invece QUESTO sistema:
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  if (addon.self.disabled) return oldDeleteSprite.apply(this, args);
  // ...
};
```
{{< /admonition >}}

## Internazionalizzazione

### Use addon.tab.scratchMessage()

If a string has already been translated by Scratch use [addon.tab.scratchMessage](/docs/reference/addon-api/addon.tab/#addontabscratchmessage) instead of adding a new message.

{{< admonition error >}}
```js
// Don't do this:
doneButton.innerText = msg("done");
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Do this instead:
doneButton.innerText = addon.tab.scratchMessage("general.done");
```
{{< /admonition >}}
