---
title: Scripts d'utilisateurs
description: Les scripts d'utilisateurs vous permettent de jouer du code sur les pages de Scratch - vous pouvez y faire des choses comme ajouter des boutons, améliore l'éditeur Scratch ou tous ce que vous pouvez imaginer.
---
## De quoi s’agit-il ?
Les scripts d'utilisateurs vous permettent de jouer du code sur les pages de Scratch - vous pouvez y faire des choses comme ajouter des boutons, améliore l'éditeur Scratch ou tous ce que vous pouvez imaginer.

## Comment puis-je ajouter un script d'utilisateur?
**Soyez sûre de rafraichir Scratch Addons from `chrome://extensions` après avoir ajouter n'importe quel modification à votre addons.** 
Allez à votre "manifest" de votre addon (addon.json) et ajouter une propriété nommé `userscripts"`.
Cette propriété doit être tableau.
Chacun des choses du tableau doit avoir des propriétés comme celle-ci: `"url"` et `"matches"`.
`"url"`  doit être relatif à URL du ficher JavaScript.
 `"matches"` doit être un tableau des URLs où vous voulez faire jouer le script d'utilisateur. Vous pouvez utiliser des astérisques.
Exemples d'un manifest
  ```json
{
"name": "Messages Scratch",
"description": "Facilite la possibilité de lire et répondre aux messages Scratch",
"userscripts": [
{
"url": "userscript.js",
"matches": ["https://scratch.mit.edu/*"]
},
{
"url": "second_userscript.js",
"matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
}
],
"tags": ["community"],
"enabled_by_default": false
}
```

## À quoi un fichier JavaScript ressemble?
Userscripts JS files require a specific structure to work.  
For userscripts, you **must** wrap all your code inside a function looking like this:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + addon.auth.username);
}
```
If you want to write your own functions to have cleaner code, you should include them inside the main function:  
**This will work:**
```js
export default async function ({ addon, global, console }) {
  // This works!
  sayHello();
  function sayHello() {
    console.log("Hello, " + addon.auth.username);
  }
}
```
**Ça Ne marchera PAS:**
```js
export default async function ({ addon, global, console }) {
  // This WON'T work!
  sayHello();
}
function sayHello() {
  console.log("Hello, " + addon.auth.username);
  // Error: addon is not defined!
}
```

## [`addon.*` APIs](/docs/developing/addon-apis-reference)
You can access some `addon.*` APIs from userscripts. For more information, check the documentation.

## Aspect thecnique d'un script d'utilisateur
Userscripts run after the Scratch page has fully loaded - in other words, they run in `defer` mode.
Technically speaking, each userscript is a JavaScript module that exports a function. JavaScript modules always run on "strict mode".  
This means that userscripts of the same addon DO NOT share variables and functions! If you want to do that, you should use the `global` object (more info below).
Scratch Addons then calls that function modules exported, giving it access to the `addon.*` APIs, as well as special wrappers:  
- `addon`: gives userscripts access to the [`addon.*` APIs](/docs/developing/addon-apis-reference).
- `global`: this is a shared object between all userscripts of the same addon. **Example usage:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.username);
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // This works, as long as in the addon manifest, userscript-1.js is before userscript-2.js in the userscripts array.
}
```
- `console`: this is a wrapper that allows you to see what addon triggered the log you're seeing easily.

## Debugging userscripts
**Make sure to refresh Scratch Addons from `chrome://extensions` after doing any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to this repo! Userscripts must not pollute the global object.