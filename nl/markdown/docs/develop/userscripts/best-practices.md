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

### Gebruik element.closest() i.p.v. parentElement te misbruiken

Gebruik parentElement niet te vaak wanneer je kijkt naar voorouderen van een element. Gebruik in plaats daarvan `element.closest()`. Het werkt bijna hetzelfde als `element.querySelector()`.

{{< admonition error >}}
```js
// Doe dit niet:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Doe in plaats daarvan dit:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Optimale praktijken in JavaScript


### Gebruik moderne JavaScript

- Gebruik liever nieuwere API's, zoals `fetch()` i.p.v. `XMLHttpRequest`.
- Gebruik nooit `==` voor vergelijkingen. Gebruik in plaats daarvan `===`.
- Wanneer je toetsenbordevenementen wilt detecteren, gaat de voorkeur uit naar `event.key` om te weten welke toets is ingedrukt. Over het algemeen is het slim om `event.code` en `event.keyCode` te vermijden.
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

Vermijd het instellen van eigenschappen op het globale `window`-object, behalve als je een globale functie, zoals `fetch()`, aan het polluten bent.
Als meerdere addons informatie of functies met elkaar moeten delen, maak dan een JS-modulebestand en importeer het vanaf beide userscripts.

{{< admonition error >}}
```js
// Doe dit niet:
window.isDarkMode = true;
```
{{< /admonition >}}

### Verklaar geen functies buiten de standaardexport

Er is geen reden om functies buiten de `export default async function(){}`-functie te verklaren. JavaScript geeft je de mogelijkheid om functies binnen andere functies te verklaren.

Indien gepast mag je functies verplaatsen naar aparte JS module bestanden (welke niet zijn verklaard als userscripts in de addon manifest), maar onthoud dat die geïmporteerde bestanden geen toegang hebben tot het `addon`-object, tenzij je een setupfunctie "exposet" die het als een argument accepteert, en roep de functie op in het ingangspunt van de userscript.

### Onpollute functies niet

Meerdere addons willen misschien dezelfde functie polluten, zoals Scratch VM-methoden, `XMLHttpRequest`, `fetch()` of `FileReader()`.
In die gevallen zal één van de userscripts de echte functie aan het polluten zijn, terwijl de anderen functies zullen polluten die zelf al gepollute waren. Als bijvoorbeeld de eerste userscript die pollute, besluit om te onpolluten (bijvoorbeeld met `window.fetch = realFetch`), dan zijn alle functies in de "pollution-keten" ook verdwenen, wat onverwacht is.
Voor deze reden moeten functies niet geonpollute worden. Geef in plaats daarvan de argumenten aan de originele functie.

{{< admonition error >}}
```js
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // Doe dit NIET:
  vm.deleteSprite = oldDeleteSprite;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Doe in plaats daarvan dit:
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  if (addon.self.disabled) return oldDeleteSprite.apply(this, args);
  // ...
};
```
{{< /admonition >}}

## Internationalisatie

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
