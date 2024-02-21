---
title: Lokalisering av tillegg
description: Lokalisering av tillegg er enkelt.
---
Lokalisering av tillegg er enkelt.

## Legg til meldinger
Under `addons-l10n/nb/`, lag en fil med navnet `ADDONID.json`, der ADDONID er tilleggets ID (mappenavnet). Skriv meldingene du ønsker å oversette der:

```json
{
  "ADDONID/meow": "Mjau",
  "ADDONID/cats": "{number, plural, one {1 katt} other {# katter}}",
  "ADDONID/eat": "Jeg vil spise {food}!",
  "ADDONID/salmon": "laks",
  "ADDONID/sardine": "sardin",
  "ADDONID/move-steps": {
    "string": "gå {number} steg",
    "developer_comment": "Vennligst oversett dette for å matche Scratchs offisielle oversettelse for blokken."
  }
}
```

### Plassholdere
Noen ganger trenger meldinger å ha ting som genereres dynamisk. For eksempel antall katter eller inndata. For å håndtere dette kan du bruke plassholdere som `{placeholderName}`. Plassholderens navn bør kun inneholde bokstaver (ingen tall).

### Flertall
Hva om plassenholderen er et tall? Vi kan bruke flertall som `{placeholderName, plural, one {når det er én ting} other {når det er # ting}}`. Hvis plassenholderen er 1, vil det vise "når det er én ting", ellers sier det "når det er (placeholder) ting".

### Utviklerkommentarer

Transifex vil vise utviklerkommentaren når en oversetter har valgt den angitte strengen. Disse kommentarene brukes vanligvis til å be om en spesifikk oversettelse av strengen eller for å gi tilleggsinformasjon for språk som ikke skiller mellom store og små bokstaver.

## Bruk av oversettelsene
Endre første linje i brukerskriptet ditt fra noe slikt:
```
export default async function ({ addon, console }) {
```

til:
```
export default async function ({ addon, console, msg }) {
```

`msg` er funksjonen du bruker for å få oversettelser. For eksempel kan `text = "Meow"` nå være `text = msg("meow")`. Addon-ID-en og skråstreken er utelatt.

### Plassholdere
Du kan gi plassholderverdier.
```js
katt = msg("katter", {number: 1}) // viser "1 katt"
katter = msg("katter", {number: 3}) // viser "3 katter"
sulten = msg("spise", {food: "torsk"}) // viser "Jeg vil spise torsk!"
```

Du kan også "nest" meldinger.
```js
hungry2 = msg("spis", {mat: msg("laks")}) // viser "Jeg vil spise laks!"
```

### Sikkerhet
Hvis du skriver rå HTML, bør `msg` erstattes med en tryggere versjon av `safeMsg`.
