---
title: Meilleures pratiques
description: Suivez ces bonne pratiques quand vous écrivez ou regarder le code "userscript"
---

Suivez ces bonne pratiques quand vous écrivez ou regarder le code "userscript"


## la manipulation de DOM (interface de programmation pour les documents HTML, XML et SVG)


### Utilise "addEventListener" au lieu de "onevent"

Évitez de définir des valeurs « onevent » sur des éléments HTML, comme « `onclick` ». Utilisez plutôt « `addEventListener` ». Cela permet à plusieurs addons d’enregistrer le même événement sur le même élément, sans entrer en conflit. 
Il est toujours valable d’utiliser "onevent", mais seulement pour les éléments créés par le même addon qui enregistre l’événement. 
Dans tous les cas, évitez de définir des attributs HTML "onevent", par exemple `element.setAttribute("onclick", "don’t do this")`.

{{< admonition error >}}
```js
// Don't do this:
document.querySelector(".remix-button").onclick = () => {
prompt("Êtes vous sur de vouloir en faire un remix?");
};
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Faites plutôt ça:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Are you sure you want to remix?");
});
```
{{< /admonition >}}

### Evitez l'utilisation de "innerHTML"

Evitez l'utilisation de `innerHTML`.Utilisez plutôt `innerText` ou `textContent` à la place.
D’autres API qui peuvent potentiellement conduire à des vulnérabilités XSS devraient également être évitées, telles que `insertAdjacentHTML`, `outerHTML`, `document.write()`, etc..

{{< admonition error >}}
```js
// Ne faites pas cela:
document.querySelector(".sa-remix-button").innerHTML = `<span>Remix ${projectTitle}</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Faites plutôt ça:
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

### Cachez les éléments au lieu de les enlevez

Évitez d’appeler `.remove()` sur des éléments HTML, ce qui, dans des cas extrêmes, peut provoquer le plantage de la page du projet. 
Les addons ne peuvent l’utiliser que pour des éléments qu’ils ont eux-mêmes créés, dans des situations spécifiques.

{{< admonition error >}}
```js
// Ne faites pas:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Faites plutôt ça:
document.querySelector(".remix-button").style.display = "none";

// ou faites ça, avec de l'aide venant d'un userstyle:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Utilisez "waitForElement" seulement quand c'est nécessaire

Évitez d’utiliser l’API  `addon.tab.waitForElement`  si l’élément est garanti. Il fonctionnera toujours, et les performances ne seront pas fortement affectées, mais il pourrait confondre d’autres développeurs qui lisent le code. L’utilisation de "waitForElement" devrait généralement signifier qu’il y a au moins 1 scénario où l’élément n’existe pas à ce point d’exécution. 
Par exemple, il n’est pas nécessaire d’utiliser waitForElement lors de la recherche de messages de forum, sauf si le script utilisateur a été déclaré avec `runAtComplete: false`. Dans ces cas, utilisez simplement `document.querySelectorAll()` normalement.

 

### Utilisez element.closest() au lieu d'abusez des parentElement

Évitez de trop utiliser parentElement lorsque vous traversez les ancêtres d’un élément. Utilisez plutôt `element.closest()` , qui fonctionne très similairement à  `element.querySelector()`.

{{< admonition error >}}
```js
// Ne faites pas ceci:
reportButton.addEventListener("click", (event) => {
const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Faites plutôt ceci:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Les meilleures utilisations du JavaScript


### Utilisez modern JavaScript

- Préférez les API plus récentes, telles que `fetch()` plutôt que `XMLHttpRequest`.
- N'utilisez pas `==` comme comparaisons, utilisez de préférence `===`.
- When listening to keyboard events, accessing `event.key` is the preferred way to know which key was pressed. In general, you should avoid `event.code` and `event.keyCode`.
- Utilisez le chaînage facultatif si un objet peut parfois être `null `. 
Par exemple,  `document.querySelector(".remix-button")?.textContent`.
- Utilisez `for ... of` loops ou `.forEach()`. 
Évitez les boucles de style C comme par exemple  `for (let i = 0; i < arr.length; i++)`.

### N’utilisez "let" sur "const" que si la variable peut être réaffectée

{{< admonition info >}}
Nous utilisons habituellement `camelCase` pour nommer les variables, qu’elles soient déclarées par « let » ou « const ». Pour les chaînes ou les nombres constants, nous utilisons habituellement `SNAKE_CASE`.

Voici un exemple:
```js
let actionCounter = 0;
actionCounter++;

const remixButton = document.querySelector(".remix-button");

const DEFAULT_ZOOM = 1.20;
```
{{< /admonition >}}

Les personnes lisant votre code peuvent supposer qu’une variable qui a été déclarée par le mot-clé "let" pourrait être réaffectée à un autre point du script. Si ce n’est pas le cas, utilisez le mot-clé "const" à la place. 
Rappelez-vous qu’en JavaScript, déclarer un objet ou un array comme "const" ne signifie pas que ses valeurs sont gelées. Les valeurs de l’objet peuvent toujours être modifiées, même si la variable elle-même ne peut pas être réaffectée.

### Ne définissez pas variables globales

Évitez de définir des propriétés sur l'objet global `window`, sauf si vous polluez une fonction globale telle que `fetch()`.
Si plusieurs addons ont besoin de partager des informations ou des fonctions entre eux, créez un fichier de module JS et importez-le à partir des deux scripts utilisateur.

{{< admonition error >}}
```js
// Ne faites pas ça:
window.isDarkMode = true;
```
{{< /admonition >}}

### Ne déclarez pas les fonctions en dehors de l'exportation faite par défault

Il n'y a aucune raison de déclarer les fonctions en dehors des  fonctions `export default async function(){}` . JavaScript autorise les fonctions à être déclarées à l'intérieur de d'autres fonctions.

Vous pouvez déplacer des fonctions vers des fichiers de modules JS distincts (qui ne sont pas déclarés comme des scripts d’utilisateur dans le manifeste d’addon), le cas échéant, mais gardez à l’esprit que ces fichiers importés n’auront pas accès à l’objet `addon`, à moins d’exposer une fonction de configuration qui l’accepte comme argument, et appeler la fonction dans le point d’entrée userscript.

### Ne pas dissocier les fonctions

Nombreux sont les addons peuvent vouloir polluer la même fonction, comme les méthodes Scratch VM, `XMLHttpRequest`, `fetch()` ou `FileReader()`. 
Dans ces cas, un des userscripts polluera la fonction réelle, tandis que les autres pollueront des fonctions qui étaient déjà polluées elles-mêmes. Si, par exemple, le premier userscript pollué décide de se désintoxiquer (par exemple, en faisant `window.fetch = realFetch`), alors toutes les autres fonctions de la "chaîne de pollution" sont également perdues, ce qui est inattendu. 
Pour cette raison, les fonctions ne doivent pas être non polluées. Passez plutôt les arguments à la fonction d’origine.

{{< admonition error >}}
```js
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // Ne pas faire:
  vm.deleteSprite = oldDeleteSprite;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Faites de préférence ça:
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  if (addon.self.disabled) return oldDeleteSprite.apply(this, args);
  // ...
};
```
{{< /admonition >}}

## Internationalisation

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
