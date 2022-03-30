---
title: Addons Lokaliseren
description: Addons lokaliseren is simpel.
---
Addons lokaliseren is simpel.

## Berichten toevoegen
Onder `addons-l10n/en/`, maak een bestand genaamd `ADDONID.json`, waar ADDONID het addon-ID is (de mapnaam). Schrijf hier je berichten die je wilt vertalen:

```json
{
  "ADDONID/meow": "Meow",
  "ADDONID/cats": "{getal, plural, one {1 kat} other {# katten}}",
  "ADDONID/eat": "Ik wil {food} eten!",
  "ADDONID/salmon": "zalm",
  "ADDONID/sardine": "sardien"
}
```

### Plaatsvervangers
Soms hebben berichten dingen nodig die dynamisch gegenereerd zijn. Bijvoorbeeld, het aantal katten, of een invoer. Om dit te doen, kun je plaatsvervangers gebruiken zoals `{plaatsvervangerNaam}`. Plaatsvervangernaam zou alleen letters moeten hebben (geen getallen).

### Meervouden
Wat als de plaatsvervanger een getal is? We kunnen meervouden gebruiken zoals `{plaatsvervangerNaam, plural, one {als er één ding is} other {als er # dingen zijn}}`. Als de plaatsvervanger 1 is, zal het "als er één ding is" staan, anders zegt het "wanneer er (plaatsvervanger) dingen zijn".

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
cat = msg("katten", {number: 1}) // laat "1 kat" zien
cats = msg("katten", {number: 3}) // laat "3 katten" zien
hungry = msg("eat", {food: "kabeljauw"}) // laat "Ik wil kabeljauw eten!" zien
```

Je kunt berichten ook "nesten":
```js
hungry2 = msg("eat", {food: msg("zalm")}) // laat "Ik wil zalm eten!" zien
```

### Veiligheid
Als je onbewerkte HTML schrijft, zou `msg` vervangen moeten worden met een veiligere versie van `safeMsg`.
