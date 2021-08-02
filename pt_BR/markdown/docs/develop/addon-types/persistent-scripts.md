---
title: Scripts Persistentes
description: Scripts persistentes te deixam rodar JavaScript em segundo plano! Eles são super úteis para notificar o usuário sobre alguma coisa, ou pré-carregar dados até que o usuário precise.
---

> **Recomendamos você evitar de usar scripts persistentes o máximo possível. Uma migração futura para o [Manifest V3](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-migration/#background-service-workers) necessitará que nós usemos service workers ao invés de páginas rodando em segundo plano, o que deixa a criação de scripts persistentes mais difícil. Quanto menos scripts persistentes houver até migrarmos, melhor será.**

## O que são?
Scripts persistentes te deixam rodar JavaScript em segundo plano! Eles são super úteis para notificar o usuário sobre alguma coisa, ou pré-carregar dados até que o usuário precise.

## Como eu adiciono um script persistente?
**Lembre-se de recarregar o Scratch Addons em `chrome://extensions` depois de fazer mudanças no seu addon.**
Vá para o manifest do seu addon (addon.json) e adicione uma propriedade chamada `"persistent_scripts"`.  
Essa propriedade deve ser uma array (matriz/lista), mesmo que o seu addon use só um script persistente. 
Cada item da array deve ser um URL relativo apontando para um arquivo JS.
Exemplo de manifest:
```json
{
  "name": "Mensagens do Scratch",
  "description": "Te deixa facilmente ler e responder suas mensagens do Scratch",
  "persistent_scripts": ["background.js"],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## Como tem que ser o arquivo JavaScript?
Scripts persistentes, assim como userscripts, precisam de uma estrutura específica para funcionar.
Em scripts persistentes, você **deve** colocar todo o seu código em uma função assim:
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  console.log("Olá, " + addon.auth.username);
}
```
Se você quer escrever suas próprias funções para organizar o código, inclua todas dentro da função principal:
**Isso funciona:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // Isso funcionará!
  digaOla();
  function digaOla() {
    console.log("Olá, " + addon.auth.username);
  }
}
```
**Isso NÃO funciona:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // Isso NÃO funcionará!
  digaOla();
}
function digaOla() {
  console.log("Olá, " + addon.auth.username);
  // Erro: addon não foi definido!
}
```

## [APIs `addon.*`](/docs/developing/addon-apis-reference)
Você pode acessar a maioria das APIs `addon.*` em scripts persistentes. Para mais informações, leia a documentação.

## Aspectos técnicos de scripts persistentes
Cada script persistente é um módulo JavaScript que exporta uma função. Módulos JavaScript sempre rodam com "strict mode" ativado.    
Isso significa que scripts persistentes do mesmo addon NÃO compartilham os mesmos variáveis e funções! Se você quer fazer isso, use o objeto `global` (mais informações abaixo).
O Scratch Addons, então, executa a função exportada pelos módulos, o que dá a ela acesso às APIs `addon.*`, além de outros wrappers especiais:
- `addon`: dá ao script persistente acesso às [APIs `addon.*`](/docs/developing/addon-apis-reference).
- `global`: isso é um objeto compartilhado por todos os scripts persistentes no mesmo addon. **Exemplo de uso:**
```js
// background-1.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.digaOla = () => console.log("Olá, " + addon.auth.username);
}

// background-2.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.digaOla();
  // Isso funciona, mas só se background-1.js estiver antes de background-2.js na array persistent_scripts do manifest do addon.
}
```
- `console`: isso é um wrapper que te deixa ver qual addon escreveu o quê ao log facilmente.
- `setTimeout` e `setInterval`: se o seu addon for desabilitado enquanto está rodando, o Scratch Addons precisa esperar até que todos os timeouts e intervalos parem. Para que isso seja possível, os addons precisam usar essas wrappers, ao invés de usar `window.setTimeout` e `window.setInterval`.
- `clearTimeout` e `clearInterval`: você precisa usar esses wrappers também para evitar vazamento de memória - o Scratch Addons não teria como saber que você limpou um timeout ou intervalo, e ficaria guardando o ID do timeout/intervalo sem motivo. Por isso você também não deve usar `window.clearTimeout` ou `window.clearInterval`.

## Depurando scripts persistentes
**Lembre-se de recarregar o Scratch Addons em `chrome://extensions` depois de fazer mudanças ao seu addon.**
Para fazer depuração em scripts persistentes, antes de tudo veja se seu addon está ativado.  
Aí, vá para `chrome://extensions`, ative o modo de desenvolvedor, e encontre o Scratch Addons.  
Clique onde diz "Inspecionar modos de exibição: background/background.html".  
Só isso - todos os console logs do seu addon estarão lá, e se você for top nos devtools, pode facilmente colocar breakpoints (pontos de parada) no seu código.
Dica: se quiser testar a API `addon.*` sem mudar seu arquivo toda vez, coloque `window.addon = addon;` no seu código (dentro da função principal),  e você poderá acessar o objeto `addon` do seu addon através do console. Lembre-se de remover essa linha antes de contribuir ao repositório! Scripts persistentes não devem poluir o objeto global.