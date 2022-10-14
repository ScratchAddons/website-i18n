---
title: ユーザースクリプト
description: ユーザースクリプトを使うと、Scratchページでコードを実行できます。ボタンを追加したり、Scratchエディターを強化したり、その他なんでもできます。
---
## これは何ですか?
ユーザースクリプトを使うと、Scratchページでコードを実行できます。ボタンを追加したり、Scratchエディターを強化したり、その他なんでもできます。

## ユーザースタイルの追加方法
**アドオンへの変更後はScratch Addonsを `chrome://extensions` から再読み込みしてください。**
アドオン・マニフェスト(addon.json)にて `userscripts` プロパティを追加してください。
これは配列でないといけません。
各項目には `url` と `matches` プロパティが必要です。
`url` はJavaScriptファイルへの相対URLです。
`matches` はユーザースクリプトを実行するURLの配列です。アスタリスクが使用できます。
例:
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
**This will NOT work:**
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

## ユーザースクリプトの技術的側面
Userscripts run after the Scratch page has fully loaded - in other words, they run in `defer` mode.
Technically speaking, each userscript is a JavaScript module that exports a function. JavaScript modules always run on "strict mode".  
This means that userscripts of the same addon DO NOT share variables and functions! If you want to do that, you should use the `global` object (more info below).
Scratch Addons then calls that function modules exported, giving it access to the `addon.*` APIs, as well as special wrappers:  
- `addon`: [`addon.*` API](/docs/developing/addon-apis-reference) へアクセスできるようにします。
- `global`: これは同じアドオンで共有されているオブジェクトです。 **使用例**:
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

## ユーザースクリプトのデバッグ
**Make sure to refresh Scratch Addons from `chrome://extensions` after making any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to the repo! Userscripts must not pollute the global object.
