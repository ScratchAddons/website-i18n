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

## Como tem que ser o arquivo JavaScript?
Userscripts precisam de uma estrutura específica para funcionar.  
Em userscripts, você **deve** colocar todo o seu código em uma função assim:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + await addon.auth.fetchUsername());
}
```
Se você quer escrever suas próprias funções para organizar o código, inclua todas dentro da função principal:
**Isso funciona:**
```js
export default async function ({ addon, global, console }) {
  // This works!
  sayHello();
  function sayHello() {
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
function sayHello() {
  console.log("Hello, " + await addon.auth.fetchUsername());
  // Error: addon is not defined!
}
```

## [APIs `addon.*`](/docs/developing/addon-apis-reference)
Você pode acessar algumas das APIs `addon.*` em userscripts. Para mais informações, leia a documentação.

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
**Lembre-se de recarregar o Scratch Addons em `chrome://extensions` depois de fazer mudanças ao seu addon.**
Para fazer depuração em userscripts, antes de tudo veja se seu addon está ativado.  
Aí, vá para um URL em que você especificou que seu addon rodará.
Abra o console apertando Ctrl+Shift+J.  
Você verá console logs de todos os addons, incluindo o seu. Se você for top nos devtools, pode facilmente colocar breakpoints (pontos de parada) no seu código.
Dica: se quiser testar a API `addon.*` sem mudar seu arquivo toda vez, coloque `window.addon = addon;` no seu código (dentro da função principal),  e você poderá acessar o objeto `addon` do seu addon através do console. Lembre-se de remover essa linha antes de contribuir ao repositório! Userscripts não devem poluir o objeto global.
