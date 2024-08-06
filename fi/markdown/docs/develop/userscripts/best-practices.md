---
title: Parhaat käytännöt
description: Noudata näitä parhaita käytäntöjä, kun kirjoitat tai tarkastat käyttäjäskriptin koodia.
---

Noudata näitä parhaita käytäntöjä, kun kirjoitat tai tarkastat käyttäjäskriptin koodia.


## DOM-manipulointi


### Käytä addEventListener-menetelmää "onevent"-menetelmän sijaan

Vältä "onevent"-arvojen, kuten `onclick`, asettamista HTML-elementeille. Käytä sen sijaan `addEventListener`-menetelmää. Tämän avulla useammat lisäosat voivat rekisteröidä saman tapahtuman samalle elementille ilman ristiriitoja.
On silti hyväksyttävää käyttää "onevent"-menetelmää, mutta vain elementeille, jotka sama tapahtuman rekisteröinyt lisäosa on luonut.
Vältä joka tapauksessa "onevent"-menetelmää HTML-määritteissä. Esimerkki: `element.setAttribute("onclick", "älä tee näin")`

{{< admonition error >}}
```js
// Älä tee näin:
document.querySelector(".remix-button").onclick = () => {
  prompt("Haluatko varmasti remiksata?");
};
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Haluatko varmasti remiksata?");
});
```
{{< /admonition >}}

### Vältä innerHTML-ominaisuuden käyttöä

Vältä `innerHTML`-ominaisuuden käyttöä. Käytä `innerText`- tai `textContent`-ominaisuutta sen sijaan.
Muitakin XSS-haavoittuvuuksia mahdollisesti aiheuttavia ohjelmointirajapintoja tulee välttää, kuten `insertAdjacentHTML`, `outerHTML`, `document.write()` jne.

{{< admonition error >}}
```js
// Älä tee näin:
document.querySelector(".sa-remix-button").innerHTML = `<span>Remiksaa ${projectTitle}</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
const span = document.createElement("span");
span.textContent = `Remiksaa ${projectTitle}`;
document.querySelector(".sa-remix-button").append(span);
```
{{< /admonition >}}

### Vältä mousemove-tapahtuman käyttöä

Vältä `mousemove`-tapahtuman ja muiden samanlaisten erittäin usein käynnistyvien DOM-tapahtumien käyttöä, koska ne heikentävät suorituskykyä, etenkin kun niitä käytetään body-elementillä. Käytä vaihtoehtoista tapahtumaa lapsielementillä aina, kun se on mahdollista.

{{< admonition error >}}
```js
// Älä tee näin:
body.addEventListener("mousemove", (event) => {
  // ...
});
```
{{< /admonition >}}

### Piilota elementit niiden poistamisen sijaan

Vältä `.remove()`-menetelmän käyttöä HTML-elementeille. Pahimmassa tapauksessa menetelmän käyttö voi aiheuttaa projektisivun kaatumisen.
Lisäosat voivat käyttää sitä vain erityistapauksissa itse luomilleen elementeille.

{{< admonition error >}}
```js
// Älä tee näin:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
document.querySelector(".remix-button").style.display = "none";

// Tai näin käyttäjätyylin avulla:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Käytä waitForElement-rajapintaa vain, kun se on välttämätöntä

Vältä `addon.tab.waitForElement`-rajapinnan käyttöä, jos on elementin olemassaolo on taattu. Se toimii silti eikä vaikuta paljoakaan suorituskykyyn, mutta se saattaa hämmentää muita kehittäjiä, jotka lukevat koodia. waitForElement-rajapinnan käytön tulisi tarkoittaa sitä, että on olemassa ainakin yksi tilanne, jossa elementti ei ole olemassa koodin suoritushetkellä.
waitForElement-rajapinnan käyttö ei esimerkiksi ole välttämätöntä foorumiviestejä etsittäessä, ellei käyttäjäskriptiä ole ilmoitettu arvolla `"runAtComplete": false`. Niissä tapauksissa `document.querySelectorAll()`-menetelmää käytetään tavalliseen tapaan.

### Käytä element.closest()-menetelmää parentElement-ominaisuuden väärinkäyttämisen sijaan

Vältä parentElement-ominaisuuden liiallisista käyttöä, kun käyt läpi elementin esivanhempia. Käytä sen sijaan `element.closest()`-menetelmää, joka toimii miltei samalla tavalla kuin `element.querySelector()`.

{{< admonition error >}}
```js
// Älä tee näin:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Parhaat JavaScript-käytännöt


### Käytä uudenaikaista JavaScriptiä

- Käytä uudempia rajapintoja, kuten `fetch()`-rajapintaa `XMLHttpRequest`-olion sijaan.
- Älä koskaan käytä `==`-operaattoria vertailuissa. Käytä sen sijaan `===`-vertailuoperaattoria.
- When listening to keyboard events, accessing `event.key` is the preferred way to know which key was pressed. In general, you should avoid `event.code` and `event.keyCode`.
- Use optional chaining if an object can sometimes be `null`.  
For example, `document.querySelector(".remix-button")?.textContent`.
- Use `for ... of` loops or `.forEach()`.  
Avoid C style loops like `for (let i = 0; i < arr.length; i++)`.

### Only use "let" over "const" if the variable may be reassigned

{{< admonition info >}}
We usually use `camelCase` to name variables, no matter if they're declared with "let" or "const".  
For constant strings or numbers, we usually use `SNAKE_CASE`.

Tässä esimerkki:
```js
let actionCounter = 0;
actionCounter++;

const remixButton = document.querySelector(".remix-button");

const DEFAULT_ZOOM = 1.20;
```
{{< /admonition >}}

People reading your code may assume that a variable that was declared through the "let" keyword might be reassigned at some other point of the script. If that's not the case, use the "const" keyword instead.  
Remember that in JavaScript, declaring an object or an array as a "const", does not mean its values are frozen. Values in the object can still be changed, even if the variable itself cannot be reassigned.

### Do not set global variables

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

## Internationalization

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
