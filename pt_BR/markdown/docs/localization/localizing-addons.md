---
title: Localizando Addons
description: Localizar addons é fácil.
---
Localizar addons é fácil.

## Adicionando mensagens
Em `addons-l10n/en/`, crie um arquivo chamado `ADDONID.json`, mas substitua ADDONID pelo ID do seu addon (mesmo nome da pasta). Escreva as mensagens que você quer traduzir lá:

```json
{
  "ADDONID/meow": "Meow",
  "ADDONID/cats": "{number, plural, one {1 cat} other {# cats}}",
  "ADDONID/eat": "I want to eat {food}!",
  "ADDONID/salmon": "salmon",
  "ADDONID/sardine": "sardine",
  "ADDONID/move-steps": {
    "string": "move {number} steps",
    "developer_comment": "Please translate this to match Scratch's official translation for the block."
  }
}
```

### Placeholders
Algumas mensagens precisam de partes geradas dinamicamente. Por exemplo, se você quiser mostrar o número de gatos, ou texto fornecido pelo usuário. Para lidar com isso, você pode usar placeholders assim `{nomeDoPlaceholder}`. O nome do placeholder deve conter apenas letras (sem números).

### Plurais
E se o placeholder for um número? Podemos usar plurais assim `{nomeDoPlaceholder, plural, one {aqui só tem uma coisa} other {aqui tem # coisas}}`. Se o placeholder for 1, a mensagem mostrada será "aqui só tem uma coisa", senão será "aqui tem (placeholder) coisas".

### Developer comments

Transifex will display the developer comment when a translator has selected the specified string. These comments are usually used to ask for a particular translation of the string or to provide additional information for languages that do not differentiate between uppercase and lowercase characters.

## Usando as traduções
Mude a primeira linha do seu userscript de:
```
export default async function ({ addon, console }) {
```

para:
```
export default async function ({ addon, console, msg }) {
```

O `msg` que foi adicionado é uma função que você pode usar para obter as traduções. Por exemplo, `text = "Meow"` pode ser substituído por `text = msg("meow")`. O ID do addon e a barra são omitidos.

### Placeholders
Você pode passar os valores dos placeholders para a função:
```js
cat = msg("cats", {number: 1}) // mostra "1 cat"
cats = msg("cats", {number: 3}) // mostra "3 cats"
hungry = msg("eat", {food: "cod"}) // mostra "I want to eat cod!"
```

Você também pode passar mensagens como valores de placeholder:
```js
hungry2 = msg("eat", {food: msg("salmon")}) // mostra "I want to eat salmon!"
```

### Segurança
Se você estiver escrevendo HTML puro, `msg` deve ser substituído pela versão mais segura `safeMsg`.
