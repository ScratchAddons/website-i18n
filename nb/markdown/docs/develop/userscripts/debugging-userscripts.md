---
title: Feilsøkingstips
description: Tips for enkel feilsøking av brukerskript, og kanttilfeller å vurdere.
---

Tips for enkel feilsøking av brukerskript, og kanttilfeller å vurdere.

## Tips

### Det er ikke alltid nødvendig å laste inn utvidelsen på nytt.

Det er ikke nødvendig å laste inn utvidelsen på nytt ved å gå til `chrome://extensions` når du endrer kilden til allerede eksisterende JavaScript- eller CSS-filer. I slike tilfeller er det nok å laste inn siden på nytt.

### Bruk addon.* API fra konsollen.

For utvikling kan du velge å eksponere `addon`-objektet som en global variabel, slik at det kan nås innenfor nettleserkonsollen.

```js
export default async function ({ addon, console }) {
  window.addon = addon;
  // ...
}
```

### Sett inn pauser med nøkkelordet "debugger"

`debugger;`-nøkkelordet i JavaScript vil fryse siden når det kjøres, hvis utviklerverktøyene er åpne. Å sette opp pauser er nyttig for å inspisere verdien av lokale variabler under utførelse.

### Filtrer konsollmeldinger etter tilleggs-ID

Skriv inn tilleggs-ID-en i søkefeltet "filter" på konsollen for å bare vise logger og advarsler, samt feil som er logget med `console.error()`. Husk at dette vil skjule alle unntak, med mindre du logger dem eksplisitt i koden din.


## Edge tilfeller


### Scratch prosjektside og redigeringsverktøy


#### DOM-en blir ødelagt etter å ha gått inn eller ut av redigeringsprogrammet.

Scratch oppretter alle HTML-elementer hver gang brukeren klikker på "se inni" eller "se prosjektsiden", og ødelegger de gamle. Dette kan vanligvis løses ved å bruke `addon.tab.waitForElement` eller `urlChange`-hendelsen.

#### Scratch-redigeringsprogrammet språk kan endres uten å laste på nytt

I motsetning til Scratch-nettstedet, vil ikke Scratch-redigereren laste inn på nytt når språket endres. Når du velger et annet språk, kan Scratch ødelegge og opprette noen HTML-elementer på nytt.

#### Andre situasjoner å vurdere

- Prosjektredigeringsverktøyet kan brukes uten en definert prosjekt-ID (for eksempel når du er logget ut).
- Redaktøren kan bytte fra LTR til RTL (eller omvendt) uten å kreve en sideoppdatering.


### Scratch nettsted

#### scratch-www-sider lastes ikke på nytt etter innlogging

I motsetning til scratchr2-sider, tvinger ikke scratch-www-sider en sideoppdatering etter innlogging. For eksempel, hvis du går til en prosjektside mens du er logget ut, og deretter logger inn, vil ikke siden lastes på nytt. Dette påvirker også studioer, meldingssiden osv.
I motsetning til dette lastes alle Scratch-sider på nytt etter utlogging.

#### Prosjektsider returnerer aldri 404-feil.

Selv om prosjektet ikke deles eller ikke eksisterer, returnerer Scratch en HTTP-statuskode 200. Meldingen "vår server klør seg i hodet" legges dynamisk til siden av Scratch.

#### Andre situasjoner å vurdere

- Hver av de 4 fanene inne i studioene har forskjellige URL-er, men utløser ikke en nettlesernavigasjon. Tillegg som påvirker noen av de 4 sidene, bør kjøre, uavhengig av den opprinnelige URL-en.
