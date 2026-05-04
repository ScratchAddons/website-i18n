---
title: Пользовательские скрипты
description: Пользовательские сценарии — это файлы JavaScript, которые воспроизводятся каждый раз при загрузке страницы Scratch. Они могут изменять HTML документа, добавлять новые кнопки, персонализировать поведение редактора Scratch и многое другое.
---

Пользовательские сценарии — это файлы JavaScript, которые воспроизводятся каждый раз при загрузке страницы Scratch. Они могут изменять HTML документа, добавлять новые кнопки, персонализировать поведение редактора Scratch и многое другое.

Также как и в пользовательских сценариях, которые Вы можете скачивать для таких менеджеров пользовательских сценариев, как Tampermonkey или Greasemonkey, пользовательские сценарии Scratch Addons составлены из кусочков JavaScript, исполняемых в том же контексте, что и код JavaScript из самого Scratch. В словаре браузерных расширений, этот контекст воспроизведения называют "основной мир".

Несмотря на то, что пользовательские сценарии Scratch Addons являются частью браузерного расширения, они не имеют доступ к интерфейсам `chrome.*` или `browser.*`. Вместо этого, Scratch Addons предоставляет [интерфейс `addon.*`](/docs/reference/addon-api/). 


## Объявление пользовательских сценариев в манифесте дополнения

{{< admonition warning >}}
**Некоторые изменения требуют перезагрузки расширения** со страницы `chrome://extensions` для применения, включая обновление файла манифеста дополнения.

Не обязательно перезагружать расширение при изменении исходника уже существующего JavaScript файла пользовательского сценария. В тех случаях, перезагрузки страницы достаточно.
{{< /admonition >}}

Пользовательские сценарии объявляются в массиве "userscripts"

Каждый предмет массива должен иметь следующие свойства:
- `"url"`: относительная гиперссылка к файлу JavaScript.
- `"matches"`: список страниц Scratch, где пользовательский сценарий будет воспроизводиться. Смотрите [совпадения](/docs/reference/addon-manifest/#matches) для исчерпывающей информации.

Примерный манифест:
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

## Создание Вашего первого пользовательского сценария

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

Вот пример:
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
