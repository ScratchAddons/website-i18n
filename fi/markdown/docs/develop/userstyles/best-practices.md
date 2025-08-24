---
title: Parhaat käytännöt
description: Noudata näitä parhaita käytäntöjä, kun kirjoitat tai tarkastat käyttäjäskriptejä.
---

Noudata näitä parhaita käytäntöjä, kun kirjoitat tai tarkastat käyttäjäskriptejä.


<!-- TEHTÄVÄÄ: ## Lisäosien tumman tilan tuki -->
<!-- editor-dark-mode-, dark-www- ja scratchr2-lisäosien CSS-muuttujiin viittaamisen esimerkit -->


## Kansainvälisyys

### Ota huomioon kielet, joiden sanat ovat pitkiä

Muista, että joissakin kielissä käyttöliittymäelementit, kuten painikkeet, voivat olla kapeampia tai leveämpiä.

<!-- TEHTÄVÄÄ: ### Oikealta vasemmalle (RTL) kirjoitettavien kielten tuki -->


## Tyylisääntöjen asettaminen Scratchin alkuperäisille elementeille


### Vältä tyylisääntöjen kohdentamista luokkien nimiin, jotka sisältävät hajautusarvon

Tavallisesti Scratchin projektieditori sisältää luokkien nimiä, jotka ovat `luokan_nimi_{hajautusarvo}`-muotoa. Esimerkiksi luokan nimi `green-flag_green-flag_1kiAo` on sellainen.

Koska hajautusarvot voivat muuttua tulevaisuudessa ja vaihdella Scratchin haarautusten välillä, niiden käyttöä käyttäjätyyleissä tulisi välttää.

{{< admonition error >}}
```css
/* Älä tee näin: */
.green-flag_green-flag_1kiAo {
  visibility: hidden;
}
```
{{< /admonition >}}

{{< admonition success >}}
```css
/* Tee sen sijaan näin: */
[class*="green-flag_green-flag_"] {
  visibility: hidden;
}
```
{{< /admonition >}}

### Käytä `!important`-ominaisuutta vain, jos on pakko

Jos mahdollista, käytä [CSS specificity](https://web.dev/learn/css/specificity/) -ominaisuuksia valitsimien tarkentamiseen `!important`-ominaisuuden käyttämisen sijaan.
<!-- Tämän pitäisi olla yksityiskohtaisempi -->


## Tyylisääntöjen asettaminen lisäosien lisäämille elementeille


### Aloita lisäosan määrittelemät luokkien nimet seuraavasti: `sa-`

{{< admonition info >}}
Käytämme aina `kebab-case`-tyyliä, kun määrittelemme omien luokkiemme nimiä.
{{< /admonition >}}

On suositeltavaa, että lisäosien märittelemät luokkien nimet aloitetaan tunnuksella `sa-`, jotta vältyttäisiin Scratchin ja muiden laajennusten luokkien nimien välisiltä ristiriidoilta.

Myös lisäosan tunnisteen (tai sen osan) sisällyttäminen luokan nimeen on suositeltavaa.

<!-- TEHTÄVÄÄ: ### täytyy selittää, miten z-indeksiä ja siihen liittyviä asioita käytetään Scratch-editorissa -->
