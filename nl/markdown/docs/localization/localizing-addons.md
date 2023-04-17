---
title: Addons Lokaliseren
description: Addons lokaliseren is simpel.
---
Addons lokaliseren is simpel.

## Berichten toevoegen
Maak onder `addons-l10n/en/` een bestand genaamd `ADDONID.json`, waar ADDONID het addon-ID is (de mapnaam). Schrijf hier je berichten die je wilt vertalen:

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

### Plaatsvervangers
Soms hebben berichten dingen nodig die dynamisch gegenereerd zijn. Bijvoorbeeld, het aantal katten, of een invoer. Om dit te doen, kun je plaatsvervangers gebruiken zoals `{placeholderName}`. Plaatsvervangernaam zou alleen letters moeten hebben (geen getallen).

### Meervouden
Wat als de plaatsvervanger een getal is? We kunnen meervouden gebruiken zoals `{placeholderName, plural, one {als er één ding is} other {als er # dingen zijn}}`. Als de plaatsvervanger 1 is, zal het "als er één ding is" staan, anders zegt het "wanneer er (plaatsvervanger) dingen zijn".

### Developer comments

Transifex will display the developer comment when a translator has selected the specified string. These comments are usually used to ask for a particular translation of the string or to provide additional information for languages that do not differentiate between uppercase and lowercase characters.

## De vertalingen gebruiken
Verander de eerste regel van je userscript van iets zoals:
```
export default async function ({ addon, console }) {
```

naar:
```
export default async function ({ addon, console, msg }) {
```

De nieuwe `msg` is de functie die je gebruikt voor vertalingen. Bijvoorbeeld, `tekst = "Miauw"` kan nu `tekst = msg("miauw")` zijn. Het addon-ID en de slash is weggelaten.

### Plaatsvervangers
Je kunt plaatsvervangende waardes geven:
```js
cat = msg("katten", {number: 1}) // toont "1 kat"
cats = msg("katten", {number: 3}) // toont "3 katten"
hungry = msg("eat", {food: "kabeljauw"}) // toont "Ik wil kabeljauw eten!"
```

Je kunt berichten ook "nesten":
```js
hungry2 = msg("eat", {food: msg("zalm")}) // toont "Ik wil zalm eten!"
```

### Veiligheid
Als je onbewerkte HTML schrijft, zou `msg` vervangen moeten worden met een veiligere versie van `safeMsg`.
