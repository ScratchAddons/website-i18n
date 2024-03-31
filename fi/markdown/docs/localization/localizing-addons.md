---
title: Lisäosien kotoistaminen
description: Lisäosien kotoistaminen on helppoa.
---
Lisäosien kotoistaminen on helppoa.

## Viestien lisääminen
Tee `LISÄOSA-ID.json`-niminen tiedosto kohtaan `addons-l10n/en/`. LISÄOSA_ID on lisäosan tunnus (kansion nimi). Kirjoita sinne viestit , jotka haluat kääntää:

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

### Paikkamerkit
Toisinaan viesteissä täytyy olla kohtia, jotka generoidaan dynaamisesti. Esimerkiksi kissojen lukumäärä tai syötekenttä. Tätä varten voit käyttää paikkamerkkejä, kuten `{paikkamerkinNimi}`. Paikkamerkin nimi saa sisältää ainoastaan kirjaimia (ei numeroita).

### Monikolliset muodot
Entä jos paikkamerkki on numero? Voimme käyttää monikollisia muotoja, kuten `{paikkamerkinNimi, plural, one {kun on yksi asia} other {kun on # asiaa}}`. Jos paikkamerkki on 1, näytetään kohta "kun on yksi asia". Muuten näytetään kohta "kun on (paikkamerkki) asiaa".

### Kehittäjän kommentit

Transifex will display the developer comment when a translator has selected the specified string. These comments are usually used to ask for a particular translation of the string or to provide additional information for languages that do not differentiate between uppercase and lowercase characters.

## Using the translations
Change your userscript's first line from something like:
```
export default async function ({ addon, console }) {
```

to:
```
export default async function ({ addon, console, msg }) {
```

The `msg` added is the function you use to get translations. For example, `text = "Meow"` can now be `text = msg("meow")`. The addon ID and the slash is omitted.

### Paikkamerkit
You can provide placeholder values:
```js
cat = msg("cats", {number: 1}) // shows "1 cat"
cats = msg("cats", {number: 3}) // shows "3 cats"
hungry = msg("eat", {food: "cod"}) // shows "I want to eat cod!"
```

You can also "nest" messages:
```js
hungry2 = msg("eat", {food: msg("salmon")}) // shows "I want to eat salmon!"
```

### Safety
If you are writing raw HTML, `msg` should be replaced with safer version of `safeMsg`.
