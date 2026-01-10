---
title: Лучшие Практики
description: Следуйте эти лучшие практики при написании или подтверждении кода пользовательских сценариев.
---

Следуйте эти лучшие практики при написании или подтверждении кода пользовательских сценариев.


## Манипуляция DOM


### Используйте addEventListener вместо "onevent"

Избегайте настраивания значений "onevent" на элементах HTML, таких, как `onclick`. Вместо этого, используйте `addEventListener`. Это позволяет нескольким дополнениям регистрировать то же самое событие на том же самом элементе, без конфликтов.
Всё ещё действительно использовать "onevent", но только для элементов, которые созданы регистрирующим дополнением.
В любых случаях, избегайте настраивание атрибутов HTML "onevent", для примера `element.setAttribute("onclick", "не делайте так")`.

{{< admonition error >}}
```js
// Не делайте так:
document.querySelector(".remix-button").onclick = () => {
  prompt("Are you sure you want to remix?");
};
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Лучше делайте так:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Are you sure you want to remix?");
});
```
{{< /admonition >}}

### Избегайте использования innerHTML

Избегайте использования `innerHTML`. Лучше вместо этого использовать `innertext` или `textContent`. Другие интерфейсы, которые могут потенциально привести к уязвимостям XSS тоже надо избегать, такие, как `insertAdjacentHTML`, `outerHTML`, `document.write()` и т.д..

{{< admonition error >}}
```js
// Не рекомендовано:
document.querySelector(".sa-remix-button").innerHTML = `<span>Remix ${projectTitle}</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Лучший метод:
const span = document.createElement("span");
span.textContent = `Remix ${projectTitle}`;
document.querySelector(".sa-remix-button").append(span);
```
{{< /admonition >}}

### Избегайте использования mousemove

Не используйте `mousemove` и похожие события DOM, активирующиеся очень часто, ведь они ужасны для производительности, особенно при использовании на теле документа. Пользуйтесь альтернативными событиями на элементах потомках при любой возможности.

{{< admonition error >}}
```js
// Не писать:
body.addEventListener("mousemove", (event) => {
  // ...
});
```
{{< /admonition >}}

### Прячьте элементы вместо их удаления

Отходите от задействования `.remove()` на элементах HTML, которые в крайних случаях, могут привести к сбою всей страницы проекта.
Дополнения могут использовать её для своих же элементов в определённых ситуациях.

{{< admonition error >}}
```js
// Лучше не повторять:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// А так лучше:
document.querySelector(".remix-button").style.display = "none";

// Ну, или можно сделать вот так с помощью пользовательского скрипта:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Используйте waitForElement только, когда необходимо

Избегайте использования API `addon.tab.waitForElement`, если элемент гарантированно существует. Этот случай всё ещё работает, и производительность не сильно пострадает, но он всё ещё может запутать других разработчиков при прочтении и проверке кода. Использование waitForElement обычно означает, что есть хотя бы один сценарий, где элемент ещё не существует на том пункте воспроизведения.
Для примера, необязательно использовать waitForElement при поиске публикаций на форуме, если пользовательский сценарий был определён с `"runAtComplete": false`. В тех случаях, просто используйте `document.querySelectorAll()`, как обычно.

### Действуйте с element.closest(), а не злоупотребляйте parentElement

Избегайте переиспользования parentElement при проходе через предки элемента. Вместо этого, задействуйте `element.closest()`, что работает очень похожим способом на `element.querySelector()`.

{{< admonition error >}}
```js
// Так не действуйте:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Так намного лучше:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Лучшие практики JavaScript


### Используйте современный JavaScript

- Предпочитайте новейшие интерфейсы API, например, `fetch()` вместо `XMLHttpRequest`.
- Никогда не используйте `==` для сравнений. Используйте `===`.
- При доступе к событиям клавиатуры, обращение к `event.key` — предпочитаемый путь узнавания нажатий кнопки. В общем, Вам советуется остерегаться `event.code` и `event.keyCode`.
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

## Интернационализация

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
