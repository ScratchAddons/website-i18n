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
- Используйте опциональное сцепление, если объект иногда может быть `null`.
К примеру, `document.querySelector(".remix-button")?.textContent`.
- Используйте циклы `for ... of` или `.forEach()`.
Избегайте циклов в стиле C, как `for (let i = 0; i < arr.length; i++)`.

### Только используйте "let" вместо "const", если переменная может быть переназначена

{{< admonition info >}}
Обычно, мы используем `camelCase` для названия переменных, не смотря, определены они были с помощью "let" или "const".
Для константных строк или чисел, мы обычно используем `SNAKE_CASE`.

Вот пример:
```js
let actionCounter = 0;
actionCounter++;

const remixButton = document.querySelector(".remix-button");

const DEFAULT_ZOOM = 1.20;
```
{{< /admonition >}}

Люди, читающие Ваш код могут предположить, что переменная, определенная через ключевое слово "let" может быть приравнена в какой-то другой точке в сценарии. Если это не случится, то лучше используйте ключевое слово "const".
Запомните, что в JavaScript, объявление объекта или массива как "const" не означает, что его значения заморожены. Значения в объекте всё ещё можно изменить, даже если саму переменную нельзя переназначить.

### Не устанавливайте глобальные переменные

Избегайте задавания свойств на общем объекте `window`, за исключением засорения глобальной функции, как `fetch()`.
Если нескольким дополнениям понадобилась совместная информация или общие функции, создайте модуль JS и импортируйте его с обеих пользовательских скриптов.

{{< admonition error >}}
```js
// Запрещается:
window.isDarkMode = true;
```
{{< /admonition >}}

### Не определяйте функции вне экспорта по умолчанию

Нет причины определять функции вне главной функции `export default async function(){}`. JavaScript разрешает функциям определяться внутри других.

Вы теперь можете перемещать функции в отдельные файлы модулей JS (которые не определены как пользовательские сценарии в манифесте дополнения) при подходящих ситуациях, но запомните, что те импортированные файлы не будут иметь доступ к объекту `addon`, если Вы не раскроете функцию предустановки, которая принимает его как аргумент, и не вызовите функции в начале пользовательского скрипта.

### Не обеззараживайте функции

Несколько дополнений могут захотеть загрязнить одну и ту же функцию, как методы виртуальной машины Scratch, `XMLHttpRequest`, `fetch()` или `FileReader()`.
В тех случаях, один из скриптов должен заразить настоящую функцию, пока другие будут загрязнять функции, которые уже были заражены. Если, к примеру, первый пользовательский сценарий, который заразил, решил обеззаразить (например, используя `window.fetch = realFetch`), то тогда все другие функции в "цепочке загрязнения" тоже будут потеряны, что очень непредсказуемо.
По этой причине, функции не должны быть обеззаражены. Вместо этого, передавайте аргументы оригинальной функции.

{{< admonition error >}}
```js
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // Так не делайте:
  vm.deleteSprite = oldDeleteSprite;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Лучше так:
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  if (addon.self.disabled) return oldDeleteSprite.apply(this, args);
  // ...
};
```
{{< /admonition >}}

## Интернационализация

### Используйте addon.tab.scratchMessage()

Если строка уже была переведена Scratch, то используйте [addon.tab.scratchMessage](/docs/reference/addon-api/addon.tab/#addontabscratchmessage) вместо добавления нового сообщения.

{{< admonition error >}}
```js
// Не надо писать так:
doneButton.innerText = msg("done");
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Так корректнее:
doneButton.innerText = addon.tab.scratchMessage("general.done");
```
{{< /admonition >}}
