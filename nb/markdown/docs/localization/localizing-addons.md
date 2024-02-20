---
title: Lokalisering av tillegg
description: Lokalisering av tillegg er enkelt.
---
Lokalisering av tillegg er enkelt.

## Legg til meldinger
Under `addons-l10n/nb/`, lag en fil med navnet `ADDONID.json`, der ADDONID er tilleggets ID (mappenavnet). Skriv meldingene du ønsker å oversette der:

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

### Plassholdere
Noen ganger trenger meldinger å ha ting som genereres dynamisk. For eksempel antall katter eller inndata. For å håndtere dette kan du bruke plassholdere som `{placeholderName}`. Plassholderens navn bør kun inneholde bokstaver (ingen tall).

### Flertall
Hva om plassenholderen er et tall? Vi kan bruke flertall som `{placeholderName, plural, one {når det er én ting} other {når det er # ting}}`. Hvis plassenholderen er 1, vil det vise "når det er én ting", ellers sier det "når det er (placeholder) ting".

### Utviklerkommentarer

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

### Plassholdere
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
