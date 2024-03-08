---
title: Empfohlene Vorgehensweisen
description: Wenn du Code für Userscripts schreibst oder überprüfst, folge diesen empfohlenen Vorgehensweisen.
---

Wenn du Code für Userscripts schreibst oder überprüfst, folge diesen empfohlenen Vorgehensweisen.


## Manipulation der DOM


### Benutze addEventListener anstatt von "onevent"

Nutze "onevent"-Werte bei HTML-Elementen, wie `onclick`, lieber nicht. Nutze stattdessen `addEventListener`. Das erlaubt es, mehreren Addons das gleiche Ereignis zu registrieren ohne Konflikte zu haben.
Man kann immer noch "onevent" nutzen, aber nur für Elemente, die von demselben Addon erstellt wurde, das das Ereignis erstellt.
Nutze auf jeden Fall keine "onevent" HTML-Attribute, zum Beispiel:
`element.setAttribute("onclick", "mache das nicht")`

{{< admonition error >}}
```js
// Mache das nicht:
document.querySelector(".remix-button").onclick = () => {
  prompt("Bist du dir sicher, dass du remixen willst?");
}
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Mache das stattdessen:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Bist du dir sicher, dass du remixen willst?");
});
```
{{< /admonition >}}

### Nutze innerHTML nicht

Nutze `innerHTML` lieber nicht. Stattdessen, nutze `innerText` oder `textContent`.
Andere APIs die möglicherweise zu XSS-Schwachstellen führen können sollten auch nicht genutzt werden, wie zum Beispiel `insertAdjacentHTML`, `outerHTML`, `document.write()`, usw.

{{< admonition error >}}
```js
// Mache das nicht:
document.querySelector(".sa-remix-button").innerHTML = `<span>${projectTitle} remizen</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Mache das stattdessen:
const span = document.createElement("span");
span.textContent = `${projectTitle} remixen`;

```
{{< /admonition >}}

### Verstecke Elemente, anstelle sie zu entfernen

Nutze die Funktion `.remove()` bei HTML-Elemente nicht, da sie bei Extremfällen die Projektseite zum Abstürzen bringen kann.
Addons können sie nur für Elemente, die sie selber erstellt haben, in speziellen Situationen nutzen.

{{< admonition error >}}
```js
// Mache das nicht:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Mache das stattdessen
document.querySelector(".remix-button").style.display = "none";

// Oder das, mithilfe eines Userstyles:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Nur waitForElement nutzen, wenn nötig

Nutze die `addon.tab.waitForElement`-API nur, wenn das Element garantiert existiert. Es wird immernoch funktionieren, und die Performance wird stark beeinflusst werden, aber es könnte andere Entwickler verwirren, die den Code lesen. waitForElement sollte bedeuten, dass es zumindest 1 Szenario gibt, an dem das Element nicht existiert, wenn der Code ausgeführt wird.
Zum Beispiel ist es nicht wichtig, waitForElement zu nutzen, wenn man nach Forumposts sucht, außer wenn das Userscript mit `"runAtComplete": false` deklariert wurde. In diesen Fällen kann man einfach `document.querySelectorAll()` normal ausführen.

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


## JavaScript best practices


### Use modern JavaScript

- Prefer newer APIs, such as `fetch()` over `XMLHttpRequest`.
- Never use `==` for comparisons. Use `===` instead.
- When listening to keyboard events, accessing `event.key` is the preferred way to know which key was pressed. In general, you should avoid `event.code` and `event.keyCode`.
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
