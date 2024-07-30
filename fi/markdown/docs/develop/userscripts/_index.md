---
title: Käyttäjäskriptit
description: Käyttäjäskriptit ovat JavaScript-tiedostoja, jotka suoritetaan joka kerta, kun käyttäjä lataa Scratch-sivun. Niiden avulla voidaan muuttaa HTML-asiakirjaa, lisätä uusia painikkeita, muuttaa Scratch-editorin toimintaa ja paljon muuta.
---

Käyttäjäskriptit ovat JavaScript-tiedostoja, jotka suoritetaan joka kerta, kun käyttäjä lataa Scratch-sivun. Niiden avulla voidaan muuttaa HTML-asiakirjaa, lisätä uusia painikkeita, muuttaa Scratch-editorin toimintaa ja paljon muuta.

Tampermonkeyn tai Greasemonkeyn kaltaisten käyttäjäskriptien hallintapalveluista ladattavien käyttäjäskriptien tavoin Scratch-lisäosien käyttäskriptit koostuvat JavaScriptin palasista, jotka suoritetaan samassa suorituskontekstissa kuin Scratchin oma JavaScript-koodi. Selainlaajennussanastossa tätä suorituskontekstia kutsutaan usein "päämaailmaksi".

Vaikka Scratch-lisäosien käyttäjäskriptit ovat osa selainlaajennusta, nillä ei ole pääsyä `chrome.*`- tai `browser.*`-rajapintoihin. Niiden sijaan Scratch-lisäosat tarjoaa [`addon.*`-rajapinnan](/docs/reference/addon-api/).


## Käyttäjäskriptien ilmoittaminen lisäosan manifest-tiedostossa

{{< admonition warning >}}
**Jotkin muutokset vaativat laajennuksen päivittämistä** `chrome://extensions`-sivulla, jotta muutokset, kuten manifest-tiedoston päivitykset, astuvat voimaan.

Ei ole välttämätöntä päivittää laajennusta jo olemassa olevaa JavaScript-tiedostoa muuttaessa. Tällöin sivun uudelleenlataus riittää.
{{< /admonition >}}

Käyttäjäskriptit ilmoitetaan "userscripts"-taulukossa.

Jokaisella taulukon kohteella on oltava seuraavat ominaisuudet:
- `"url"`: suhteellinen URL-osoite JavaScript-tiedostoon
- `"matches"`: luettelo Scratch-sivuista, joilla käyttäjä skripti suoritetaan. Lue lisää [matches-ominaisuuden referensistä](/docs/reference/addon-manifest/#matches).

Esimerkki manifest-tiedostosta:
```json
{
  "name": "Copy link to comment button",
  "description": "Adds a \"Copy Link\" button to all comments on the website, next to the \"Report\" button.",
  "userscripts": [
    {
      "url": "userscript.js",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles", "studios"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Ensimmäisen käyttäjäskriptin luominen

Toisin kuin laajennusten sisältöskriptit ja Tampermonkey-käyttäjäskriptit, sinun on käärittävä kaikki koodisi moduulin oletusviennin sisään:
```js
// Esimerkki käyttäjäskriptistä
export default async function ({ addon, console }) {
  console.log("Hei, " + await addon.auth.fetchUsername());
  console.log("Mitä kuuluu?");
}
```

Muista, että JavaScriptissä funktiot voidaan ilmoittaa toisten funktioiden sisällä:
```js
export default async function ({ addon, console }) {
  async function sayHelloToUser() {
    console.log("Hei, " + await addon.auth.fetchUsername());
  }

  await sayHelloToUser();
  console.log("Mitä kuuluu?");
}
```

{{< admonition info >}}
Käyttäskripteillä on pääsy moniin `addon.*`-rajapintoihin. Voit esimerkiksi saada nykyisen käyttäjänimen, odottaa, kunnes elementti on olemassa sivulla tai saada viittauksen Scratch VM -olioon.

Lue lisää [rajapintareferenssistä](/docs/reference/addon-api/).
{{< /admonition >}}


## HTML-asiakirjan muuttaminen

Muuta sivun HTML-koodia käyttämällä [selaimen DOM-rajapintoja](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API) .

Tässä esimerkki:
```js
const myButton = document.createElement("button");
myButton.textContent = "Napauta!";
myButton.classList.add("button");
myButton.setAttribute("title", "Hiiri on painikkeen päällä");

const myContainer = document.querySelector(".container");
myContainer.append(myButton);
```

## Käyttäjäskriptien lokalisointi

Lisäosien käyttäjäskripteissä täytyy joskus viitata englannin- tai muunkielisiin sanoihin tai lauseisiin. Huolehdi, että et kirjoita niitä osaksi koodia, jotta ne voidaan kääntää käännösvaiheessa.

{{< admonition error >}}
```js
// Älä tee näin:
document.querySelector(".sa-find-bar").placeholder = "Etsi lohkoja";
```
{{< /admonition >}}

Luo käännettävä merkkijono noudattamalla näitä vaiheita:
1. Luo tiedosto nimeltä `lisäosan-nimitunniste.json` `/addon-l10n/en`-kansioon.
2. Nimeä jokainen merkkijono tunnisteella:
```json
{
  "addon-id/find": "Find blocks"
}
```
3. Varmista, että tuot `msg()`-funktion käyttäjäskriptiisi. Käyttäjäskriptin ensimmäisen rivin pitäisi näyttää tältä:
```js
export default async function ({ addon, console, msg  }) {
                                              // ^^^
```
4. Käytä `msg()`-funktiota koodissa sen sijaan, että kirjoittaisit sanat ja virkkeet osaksi koodia:
```js
document.querySelector(".sa-find-bar").placeholder = msg("find");
```

{{< admonition info >}}
Lisätietoja käyttäjäskriptien lokalisoinnista löytyy [tältä sivulta](/docs/localization/localizing-addons/).
{{</admonition >}}


## Tekniset tiedot

Jokainen käyttäjäskripti on JavaScript-moduuli, joka vie funktion. Scratch-lisäosat tuo moduulin tarvittaessa ja suorittaa sen sivun latauduttua täysin.

Käyttäjäskriptit ovat JavaScript-moduuleja, joten suoritetaan aina ["tiukassa tilassa"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). Tämä tarkoittaa myös sitä, että käyttäjäskriptit voivat käyttää [ylätason tuonteja](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) muiden JavaScript-tiedostojen tuomiseen.

Käyttäjäskriptien suoritusjärjestys voi vaihdella sivun jokaisella latauskerralla. Sivun latauduttua käyttäjä saattaa dynaamisesti ottaa lisäosia käyttöön valitsemassaan järjestyksessä, joten suoritusjärjestys ei ole koskaan taattu. Jotkin rajapinnat, kuten [`addon.tab.appendToSharedSpace`](/docs/reference/addon-api/addon.tab/addon.tab.appendtosharedspace/), yrittävät korjata mahdollisia ajoitusongelmia ja odottamatonta toimintaa, kun lisäosia otetaan dynaamisesti käyttöön.

### runAtComplete

Käyttäjäskriptit voivat valita suorittamisen ennen kuin sivu on täysin latautunut määrittämällä kohdan `"runAtComplete": false` lisäosan manifest-tiedostoon kerran kusssakin käyttäjäskriptissä.

Tällä hetkellä vain `document.head` on taatusti olemassa, kun käyttäjä skripti suoritetaan aikaisin. Tulevaisuudessa `document.body` tulee myös olemaan taatusti olemassa, joten yhtäkään käyttäjäskriptiä ei tulla suorittamaan ennen kuin HTML-asiakirja on latautunut tarpeeksi saavuuttaakseen kohdan `</head> <body>`.
