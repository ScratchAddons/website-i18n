---
title: Parhaat käytännöt
description: Noudata näitä parhaita käytäntöjä, kun kirjoitat tai tarkastat käyttäjäskriptin koodia.
---

Noudata näitä parhaita käytäntöjä, kun kirjoitat tai tarkastat käyttäjäskriptin koodia.


## DOM-manipulointi


### Käytä addEventListener-menetelmää "onevent"-menetelmän sijaan

Vältä "onevent"-arvojen, kuten `onclick`, asettamista HTML-elementeille. Käytä sen sijaan `addEventListener`-menetelmää. Tämän avulla useammat lisäosat voivat rekisteröidä saman tapahtuman samalle elementille ilman ristiriitoja.
On silti hyväksyttävää käyttää "onevent"-menetelmää, mutta vain elementeille, jotka sama tapahtuman rekisteröinyt lisäosa on luonut.
Vältä joka tapauksessa "onevent"-menetelmää HTML-määritteissä. Esimerkki: `element.setAttribute("onclick", "älä tee näin")`

{{< admonition error >}}
```js
// Älä tee näin:
document.querySelector(".remix-button").onclick = () => {
  prompt("Haluatko varmasti remiksata?");
};
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Haluatko varmasti remiksata?");
});
```
{{< /admonition >}}

### Vältä innerHTML-ominaisuuden käyttöä

Vältä `innerHTML`-ominaisuuden käyttöä. Käytä `innerText`- tai `textContent`-ominaisuutta sen sijaan.
Muitakin XSS-haavoittuvuuksia mahdollisesti aiheuttavia ohjelmointirajapintoja tulee välttää, kuten `insertAdjacentHTML`, `outerHTML`, `document.write()` jne.

{{< admonition error >}}
```js
// Älä tee näin:
document.querySelector(".sa-remix-button").innerHTML = `<span>Remiksaa ${projectTitle}</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
const span = document.createElement("span");
span.textContent = `Remiksaa ${projectTitle}`;
document.querySelector(".sa-remix-button").append(span);
```
{{< /admonition >}}

### Vältä mousemove-tapahtuman käyttöä

Vältä `mousemove`-tapahtuman ja muiden samanlaisten erittäin usein käynnistyvien DOM-tapahtumien käyttöä, koska ne heikentävät suorituskykyä, etenkin kun niitä käytetään body-elementillä. Käytä vaihtoehtoista tapahtumaa lapsielementillä aina, kun se on mahdollista.

{{< admonition error >}}
```js
// Älä tee näin:
body.addEventListener("mousemove", (event) => {
  // ...
});
```
{{< /admonition >}}

### Piilota elementit niiden poistamisen sijaan

Vältä `.remove()`-menetelmän käyttöä HTML-elementeille. Pahimmassa tapauksessa menetelmän käyttö voi aiheuttaa projektisivun kaatumisen.
Lisäosat voivat käyttää sitä vain erityistapauksissa itse luomilleen elementeille.

{{< admonition error >}}
```js
// Älä tee näin:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
document.querySelector(".remix-button").style.display = "none";

// Tai näin käyttäjätyylin avulla:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### Käytä waitForElement-rajapintaa vain, kun se on välttämätöntä

Vältä `addon.tab.waitForElement`-rajapinnan käyttöä, jos on elementin olemassaolo on taattu. Se toimii silti eikä vaikuta paljoakaan suorituskykyyn, mutta se saattaa hämmentää muita kehittäjiä, jotka lukevat koodia. waitForElement-rajapinnan käytön tulisi tarkoittaa sitä, että on olemassa ainakin yksi tilanne, jossa elementti ei ole olemassa koodin suoritushetkellä.
waitForElement-rajapinnan käyttö ei esimerkiksi ole välttämätöntä foorumiviestejä etsittäessä, ellei käyttäjäskriptiä ole määritelty arvolla `"runAtComplete": false`. Niissä tapauksissa `document.querySelectorAll()`-menetelmää käytetään tavalliseen tapaan.

### Käytä element.closest()-menetelmää parentElement-ominaisuuden väärinkäyttämisen sijaan

Vältä parentElement-ominaisuuden liiallisista käyttöä, kun käyt läpi elementin esivanhempia. Käytä sen sijaan `element.closest()`-menetelmää, joka toimii miltei samalla tavalla kuin `element.querySelector()`.

{{< admonition error >}}
```js
// Älä tee näin:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## Parhaat JavaScript-käytännöt


### Käytä uudenaikaista JavaScriptiä

- Käytä uudempia rajapintoja, kuten `fetch()`-rajapintaa `XMLHttpRequest`-olion sijaan.
- Älä koskaan käytä `==`-operaattoria vertailuissa. Käytä sen sijaan `===`-vertailuoperaattoria.
- Kun olet asettanut näppäintapahtumakuuntelijan, on suositeltavaa selvittää painettu näppäin `event.key`-arvolla. `event.code` ja `event.keyCode`-arvojen käyttöä kannattaa ylipäänsä välttää.
- Käytä valinnaista ketjutusta (eng. optional chaining), jos olion arvo voi joskus olla `null`.
Esimerkiksi `document.querySelector(".remix-button")?.textContent`.
- Käytä `for ... of`- tai `.forEach()`-silmukkaa. 
Vältä C-tyylisiä silmukoita, kuten `for (let i = 0; i < arr.length; i++)`.

### Käytä "let"-muuttujaa "const"-muuttujan sijaan vain, jos se saatetaan määritellä uudelleen.

{{< admonition info >}}
Nimeämme sekä "let"- että "const"-tyyppiset muuttujat yleensä `camelCase`-kirjaintyylillä.
Vakiomerkkijonojen ja -lukujen nimeämiseen käytämme yleensä `SNAKE_CASE`-kirjaintyyliä.

Tässä esimerkki:
```js
let actionCounter = 0;
actionCounter++;

const remixButton = document.querySelector(".remix-button");

const DEFAULT_ZOOM = 1.20;
```
{{< /admonition >}}

Koodiasi lukevat ihmiset voivat olettaa, että "let"-avainsanalla määritelty muuttuja saatetaan määritellä uudelleen jossakin koodin vaiheessa. Jos niin ei ole, käytä "const"-avainsanaa sen sijaan.
Muista, että JavaScriptissä "const"-avainsanalla määritellyn olion tai taulukon arvojen muuttaminen on mahdollista, vaikka itse muuttujaa ei voida määritellä uudelleen.

### Älä aseta globaaleja muuttujia

Vältä ominaisuuksien asettamista globaaliin `window`-olioon, ellei tarkoituksesi ole muuttaa jotakin globaalia funktiota, kuten `fetch()`.
Jos useiden lisäosien täytyy jakaa tietoja tai funktioita keskenään, luo erillinen JS-moduulitiedosto ja tuo se molempiin käyttäjäskripteihin.

{{< admonition error >}}
```js
// Älä tee näin:
window.isDarkMode = true;
```
{{< /admonition >}}

### Älä määrittele funktioita export default -funktion ulkopuolella

Ei ole syytä määritellä funktioita `export default async function(){}` -funktion ulkopuolella. JavaScript sallii funktioiden määrittelemisen muiden funktioiden sisällä.

Voit tarvittaessa siirtää funktioita erillisiin JS-moduulitietostoihin (joita ei ole määritelty käyttäjäskripteiksi lisäosan manifest-tiedostossa), mutta muista, että tuoduilla tiedostoilla ei ole pääsyä `addon`-olioon, ellei käytettäväksi tarjota alustustoimintoa, joka ottaa olion parametrina ja jota kutsutaan käyttäjäskriptin aloituspisteessä.

### Älä palauta funktioita alkuperäiseen tilaansa

Useat lisäosat saattavat haluta muuttaa (”pollute”) samaa funktiota, kuten esimerkiksi Scratch VM -meneltemiä, `XMLHttpRequest`-olioita, `fetch()`- tai `FileReader()`-funktioita.
Näissä tapauksissa yksi käyttäjäskripti muuttaa oikeaa funktiota, kun taas muut muuttavat jo valmiiksi muutettuja funktioita. Jos esimerkiksi ensimmäinen funktiota muuttanut käyttäjäskripti päättää palauttaa funktion alkuperäiseen tilaansa (esim. tekemällä `window.fetch = realFetch`), katoavat samalla kaikki muutokset, joita muut skriptit olivat tehneet samaan funktioon. Tämä on yleensä odottamatonta.

Tästä syystä funktioita ei pidä palauttaa alkuperäiseen tilaansa. Sen sijaan argumentit kannattaa välittää alkuperäiselle funktiolle suoraan.

{{< admonition error >}}
```js
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // Älä tee näin:
  vm.deleteSprite = oldDeleteSprite;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
const oldDeleteSprite = vm.deleteSprite;
const newDeleteSprite = function (...args) {
  if (addon.self.disabled) return oldDeleteSprite.apply(this, args);
  // ...
};
```
{{< /admonition >}}

## Kansainvälistäminen

### Käytä addon.tab.scratchMessage()-oliota

Jos tarvittava merkkijono on jo käännetty Scratchissa, käytä [addon.tab.scratchMessage](/docs/reference/addon-api/addon.tab/#addontabscratchmessage)-oliota uuden viestin lisäämisen sijaan.

{{< admonition error >}}
```js
// Älä tee näin:
doneButton.innerText = msg("done");
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Tee sen sijaan näin:
doneButton.innerText = addon.tab.scratchMessage("general.done");
```
{{< /admonition >}}
