---
title: Scripts utilisateurs
description: Les scripts utilisateur vous permettent d'exécuter du code sur les pages de Scratch - vous pouvez y faire des choses comme ajouter des boutons, améliorer l'éditeur Scratch ou tout ce que vous pouvez imaginer.
---
## De quoi s’agit-il ?
Les scripts utilisateur vous permettent d'exécuter du code sur les pages de Scratch - vous pouvez y faire des choses comme ajouter des boutons, améliorer l'éditeur Scratch ou tout ce que vous pouvez imaginer.

## Comment puis-je ajouter un script utilisateur ?
**Assurez-vous d'actualiser Scratch Addons à partir de `chrome://extensions` après avoir apporté des modifications à votre addon.**
Accédez au manifeste de votre addon (addon.json) et ajoutez une propriété appelée `userscripts"`.
Cette propriété doit être un tableau.
Chaque élément du tableau doit avoir les propriétés suivantes : `"url"` et `"matches"`.
`"url"` doit être une URL relative vers un fichier JavaScript.
`"matches"` doit être un tableau d'URL sur lesquelles vous souhaitez exécuter le script utilisateur. Vous pouvez utiliser des astérisques.
Exemple de manifeste :
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
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
  "enabledByDefault": false
}
```

## What does the JavaScript file look like?
Userscript JS files require a specific structure to work.  
For userscripts, you **must** wrap all your code inside a function looking like this:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + await addon.auth.fetchUsername());
}
```
If you want to abstract code into functions for cleaner code, you should include them inside the main function:  
**This will work:**
```js
export default async function ({ addon, global, console }) {
  // This works!
  sayHello();
  async function sayHello() {
    console.log("Hello, " + await addon.auth.fetchUsername());
  }
}
```
**Ça Ne marchera PAS:**
```js
export default async function ({ addon, global, console }) {
  // This WON'T work!
  sayHello();
}
async function sayHello() {
  console.log("Hello, " + await addon.auth.fetchUsername());
  // Error: addon is not defined!
}
```

## [`addon.*` APIs](/docs/developing/addon-apis-reference)
You can access many `addon.*` APIs from userscripts. For more information, check the documentation.

## Aspects techniques des scripts utilisateur
Userscripts run after the Scratch page has fully loaded - in other words, they run in `defer` mode.
Technically speaking, each userscript is a JavaScript module that exports a function. JavaScript modules always run on "strict mode".  
This means that userscripts of the same addon DO NOT share variables and functions! If you want to do that, you should use the `global` object (more info below).
Scratch Addons then calls that function modules exported, giving it access to the `addon.*` APIs, as well as special wrappers:  
- `addon`: donne aux scripts utilisateurs l'accès à [`addon.*` APIs](/docs/developing/addon-apis-reference).
- `global`: this is a shared object between all userscripts of the same addon. **Example usage:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.fetchUsername());
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // This works, as long as in the addon manifest, userscript-1.js is before userscript-2.js in the userscripts array.
}
```
- `console`: this is a wrapper that allows you to see what addon triggered the log you're seeing easily.

## Débogage des scripts utilisateur
**Make sure to refresh Scratch Addons from `chrome://extensions` after making any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to the repo! Userscripts must not pollute the global object.
