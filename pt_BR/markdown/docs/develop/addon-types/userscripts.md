---
title: Userscripts
description: Userscripts te deixam executar código em páginas do Scratch - você pode, por exemplo, adicionar botões, melhorar o editor do Scratch ou qualquer outra coisa que puder imaginar.
---
## O que são?
Userscripts te deixam executar código em páginas do Scratch - você pode, por exemplo, adicionar botões, melhorar o editor do Scratch ou qualquer outra coisa que puder imaginar.

## Como eu adiciono um userscript?
**Lembre-se de recarregar o Scratch Addons em `chrome://extensions` depois de fazer mudanças no seu addon.**
Vá para o manifest do seu addon (addon.json) e adicione uma propriedade chamada `"userscripts"`.  
Essa propriedade deve ser uma array (matriz/lista).  
Cada item da array deve ter as seguintes propriedades: `"url"` e `"matches"`.  
`"url"` deve ser um URL relativo que aponta a um arquivo JavaScript.  
`"matches"` deve ser uma array de URLs nos quais você quer executar o userscript. Você pode usar asteriscos.
Exemplo de manifest:
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
**Isso NÃO funciona:**
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

## [APIs `addon.*`](/docs/developing/addon-apis-reference)
You can access many `addon.*` APIs from userscripts. For more information, check the documentation.

## Aspectos técnicos de userscripts
Userscripts rodam depois que a página do Scratch estiver toda carregada - ou seja, eles rodam em modo `defer`.
Cada userscript é um módulo JavaScript que exporta uma função. Módulos JavaScript sempre rodam com "strict mode" ativado.  
Isso significa que scripts persistentes do mesmo addon NÃO compartilham os mesmos variáveis e funções! Se você quer fazer isso, use o objeto `global` (mais informações abaixo).
O Scratch Addons, então, executa a função exportada pelos módulos, o que dá a ela acesso às APIs `addon.*`, além de outros wrappers especiais:
- `addon`: dá ao userscript acesso às [APIs `addon.*`](/docs/developing/addon-apis-reference).
- `global`: isso é um objeto compartilhado por todos os userscripts no mesmo addon. **Exemplo de uso:**
```js
// userscript-1.js
export default async function ({ addon, global, console }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.fetchUsername());
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.digaOla();
  // Isso funciona, mas só se userscript-1.js estiver antes de userscript-2.js na array userscripts do manifest do addon.
}
```
- `console`: isso é um wrapper que te deixa ver qual addon escreveu o quê ao log facilmente.

## Depurando userscripts
**Make sure to refresh Scratch Addons from `chrome://extensions` after making any changes to your addon.**  
To debug userscripts, first of all make sure your addon is enabled.  
Then, go to a URL where you specified your userscript should run.  
Open the console by pressing Ctrl+Shift+J.  
You should see console logs by addons, including yours. If you're a devtools pro, you won't have any trouble setting breakpoints in your code.  
Protip: if you want to test the `addon.*` API without changing your file every time, make your addon `window.addon = addon;` (inside the main function), and you'll be able to access your addon's `addon` object from the console. Make sure to remove that line before contributing to the repo! Userscripts must not pollute the global object.
