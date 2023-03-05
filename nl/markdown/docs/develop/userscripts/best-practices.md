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

Avoid using the `addon.tab.waitForElement` API if the element is guaranteed to exist. It will still work, and performance will not be heavily impacted, but it might confuse other developers that are reading the code. The usage of waitForElement should usually mean that there is at least 1 scenario where the element doesn't exist at that execution point.  
For example, it's not necessary to use waitForElement when searching for forum posts, unless the userscript was declared with `"runAtComplete": false`. In those cases, simply use `document.querySelectorAll()` normally.


## JavaScript best practices


### Use modern JavaScript

- Prefer newer APIs, such as `fetch()` over `XMLHttpRequest`.
- Never use `==` for comparisons. Use `===` instead.
- Use optional chaining if an object can sometimes be `null`.  
For example, `document.querySelector(".remix-button")?.textContent`.
- Use `for ... of` loops or `.forEach()`.  
Avoid C style loops like `for (let i = 0; i < arr.length; i++)`.

### Only use "let" over "const" if the variable may be reassigned

{{< admonition info >}}
We usually use `camelCase` to name variables, no matter if they're declared with "let" or "const".  
For constant strings or numbers, we usually use `SNAKE_CASE`.

Here's an example:
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
