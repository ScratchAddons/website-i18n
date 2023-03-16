---
title: Optimale Praktijken
description: Volg deze optimale praktijken bij het schrijven of beoordelen van userscript-code.
---

Volg deze optimale praktijken bij het schrijven of beoordelen van userscript-code.


## DOM-manipulatie


### Gebruik addEventListener i.p.v. "onevent"

Vermijd het gebruik van "onevent"-waarden op HTML-elementen, zoals `onclick`. Gebruik in plaats daarvan `addEventListener`. Hierdoor kunnen meerdere addons tegelijkertijd dezelfde gebeurtenis op hetzelfde element waarnemen, zonder te conflicteren.
Het is alleen handig om "onevent" te gebruiken voor elementen die in dezelfde addon zijn gecreëerd die de gebeurtenis waarneemt.
Vermijd altijd het gebruik van "onevent" HTML-attributen, bijvoorbeeld `element.setAttribute("onclick", "doe dit niet")`.

{{< admonition error >}}
```js
// Doe dit niet:
document.querySelector(".remix-button").onclick = () => {
  prompt("Weet je zeker dat je wilt remixen?");
};
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Doe in plaats daarvan dit:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Weet je zeker dat je wilt remixen?");
});
```
{{< /admonition >}}

### Vermijd het gebruik van innerHTML

Vermijd het gebruik van `innerHTML`. Gebruik in plaats daarvan `innerText` of `textContent`.
Overige API's die mogelijk tot XSS-kwetsbaarheden kunnen leiden moeten ook worden vermeden, zoals `insertAdjacentHTML`, `outerHTML`, `document.write()`, etc.

{{< admonition error >}}
```js
// Doe dit niet:
document.querySelector(".sa-remix-button").innerHTML = `<span>Remix ${projectTitle}</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Doe in plaats daarvan dit:
const span = document.createElement("span");
span.textContent = `Remix ${projectTitle}`;
document.querySelector(".sa-remix-button").append(span);
```
{{< /admonition >}}

### Verberg elementen i.p.v. ze te verwijderen

Vermijd het gebruik van `.remove()` op HTML-elementen, omdat het in sommige extreme gevallen de pagina kan laten crashen.
In specifieke situaties mogen addons het alleen gebruiken voor elementen die ze zelf hebben gemaakt.

{{< admonition error >}}
```js
// Doe dit niet:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Doe in plaats daarvan dit:
document.querySelector(".remix-button").style.display = "none";

// Of doe dit, m.b.v. een userstyle:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Gebruik waitForElement alleen waar nodig

Vermijd het gebruik van de API `addon.tab.waitForElement` als het element gegarandeerd bestaat. Het zal nog steeds werken zonder een grote impact op prestaties te hebben, maar het kan anderen die de code lezen misschien verwarren. Het gebruik van waitForElement betekent meestal dat er minstens 1 situatie is waar het element niet bestaat op het moment van uitvoering.
Het is bijvoorbeeld niet nodig om waitForElement te gebruiken om naar forumposts te zoeken, behalve als de userscript is gedeclareerd met `"runAtComplete": false`. Gebruik in die gevallen gewoon `document.querySelectorAll()`.

### Use element.closest() instead of abusing parentElement

Avoid overusing parentElement when traversing an element's ancestors. Instead, use `element.closest()`, which works very similarly to `element.querySelector()`.

{{< admonition error >}}
```js
// Don't do this:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Do this instead:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Optimale praktijken in JavaScript


### Gebruik moderne JavaScript

- Gebruik liever nieuwere API's, zoals `fetch()` i.p.v. `XMLHttpRequest`.
- Gebruik nooit `==` voor vergelijkingen. Gebruik in plaats daarvan `===`.
- Gebruik optionele chaining als een object in sommige gevallen `null` kan zijn.
Bijvoorbeeld: `document.querySelector(".remix-button")?.textContent`.
- Gebruik `for ... of`-lussen of `.forEach()`.
Vermijd lussen in C-stijl zoals `for (let i = 0; < arr.length; i++)`.

### Gebruik alleen "let" i.p.v. "const" als de variabele opnieuw toegewezen kan worden

{{< admonition info >}}
We gebruiken meestal `camelCase` om variabelen een naam te geven, ongeacht of ze zijn toegewezen met "let" of "const".
Voor constante strings of getallen gebruiken we meestal `SNAKE_CASE`.

Hier is een voorbeeld:
```js
let actionCounter = 0;
actionCounter++;

const remixButton = document.querySelector(".remix-button");

const DEFAULT_ZOOM = 1.20;
```
{{< /admonition >}}

Als mensen je code lezen zouden ze kunnen denken dat een variabele die is gedeclareerd met "let" misschien ergens anders in het script opnieuw wordt toegewezen. Als dat niet het geval is, gebruik dan "const".
Onthoud dat objecten en arrays die zijn gedeclareerd als "const" geen bevroren waarden hebben. Waarden in het object kunnen nog steeds veranderen, ook al kan de variabele zelf niet opnieuw worden toegewezen.

### Stel geen globale variabelen in

Avoid setting properties on the global `window` object, unless you are polluting a global function such as `fetch()`.  
If multiple addons need to share information or functions between each other, create a JS module file and import it from both userscripts.

{{< admonition error >}}
```js
// Don't do this:
window.isDarkMode = true;
```
{{< /admonition >}}

### Do not declare functions outside of the default export

There's no reason to declare functions outside the `export default async function(){}` function. JavaScript allows functions to be declared inside other functions.

You may move functions to separate JS module files (which aren't declared as userscripts in the addon manifest) if appropriate, but keep in mind that those imported files won't have access to the `addon` object, unless you expose a setup function that accepts it as an argument, and call the function in the userscript entry point.

### Do not unpollute functions

Multiple addons might want to pollute the same function, such as Scratch VM methods, `XMLHttpRequest`, `fetch()` or `FileReader()`.  
In those cases, one of the userscripts will be polluting the real function, while the others will be polluting functions which were already polluted themselves. If, for example, the first userscript that polluted decides to unpollute (for example, by doing `window.fetch = realFetch`), then all other functions in the "pollution chain" are also lost, which is unexpected.  
For this reason, functions should not be unpolluted. Instead, pass the arguments to the original function.

{{< admonition error >}}
```js
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // Don't do this:
  vm.deleteSprite = oldDeleteSprite;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Do this instead:
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  if (addon.self.disabled) return oldDeleteSprite.apply(this, args);
  // ...
};
```
{{< /admonition >}}
