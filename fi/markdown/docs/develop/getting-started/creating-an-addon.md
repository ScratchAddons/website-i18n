---
title: Lisäosan luominen
---
Vaaditut ohjelmistot: tekstieditori, Chrome.
Jos mahdollista, poista laajennuskaupasta lataamasi Scratch-lisäosat-laajennus ennen etenemistä ongelmien välttämiseksi.


{{< admonition info >}}
Jos ajattelit lähettää kehittämäsi lisäosan vetopyyntönä GitHub-tietosäilöön, lue ensin [osallistujien toimintaohjeet](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md).

Jos tietosäilössä ei ole uuteen lisäosaideaasi liittyvää GitHub-seikkaa, [luo sellainen](https://github.com/ScratchAddons/ScratchAddons/issues/new/choose). Jos on kuitenkin seikka, joka liittyy ominaisuusideaasi, suosittelemme, että jätät siihen kommentin ilmoittamaan aikeestasi kehittää lisäosa. Tällöin muut osallistujat voivat kertoa, voidaanko lisäosa hyväksyä vai tarvitaanko vielä lisäkeskustelua.

Jos kuitenkin teet lisäosan henkilökohtaiseen käyttöön, voit edetä tässä oppaassa.
{{< /admonition >}}

## Vaihe 1: Lue [lisäosien perusteista](/docs/develop/getting-started/addon-basics/)
Varmista, että luet artikkelin, jotta tunnet käsitteistön.

## Vaihe 2: Haarauta/kahdenna [tietosäilö](https://github.com/ScratchAddons/ScratchAddons)
Lataa lähdekoodi paikallisesti [näitä ohjeita](/docs/getting-started/installing/#from-source) noudattaen.

## Vaihe 3: Lataa laajennus Chromeen
*Huomaa: On suositeltavaa käyttää Chromea lisäosien parissa työskennellessä. Lisäosien kuitenkin odotetaan toimivan myös Firefoxissa ja Edgessä.*
Nyt kun sinulla on laajennus tiedostojärjestelmässäsi, siirry `chrome://extensions`-sivulle ja kytke "kehittäjätila" päälle.
Napauta "lataa pakkaamaton" -painiketta ja valitse sitten kansio, jossa Scratch-lisäosat sijaitsee. Jos sinulla on ongelmia tätä tehdessä, varmista, että valitset kansion, jossa `manifest.json` sijaitsee.
Siinä se, latasit laajennuksen! Nyt sen näyttää pitäisi tältä:
![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)
Huomaa: Voit rauhallisin mielin jättää huomiotta kohdat, jotka näytetään "virheinä". Se on vain varoitus tuntemattomasta manifest-avaimesta, jonka Firefox edellyttää.

## Vaihe 4: Mihin lisäosasi liittyy?
Tämä lienee se hauskin osuus!
Mitä sinun lisäosasi tekee? Keksi kuvaava lisäosatunnus (ei sanavälejä tai erikoismerkkejä, paitsi väliviivoja).
Joko keksit sellaisen?

## Vaihe 5: Luo lisäosalle kansio
Siirry tiedostonhallintaohjelmaa käyttäen kansioon, jossa Scratch-lisäosat sijaitsee tiedostojärjestelmässsi. Siirry `addons`-kansioon.
Luo sitten uusi kansio ja nimeä se lisäosatunnuksellasi.

## Vaihe 6: Lisää lisäosan manifest-tiedosto
Lisäosasi manifest-tiedosto kertoo Scratch-lisäosille, miten lisäosasi toimii. Varmista, että teet tämän oikein, jotta vältytään päänvaivalta.
Luo `addon.json`-tiedosto äsken luomaasi kansioon.
Tätä pohjaa voit käyttää koodaamisen aloittamiseen, kunhan muistat muokata sitä myöhemmin:
```json
{
  "name": "Paikanvaraajateksti lisäosan nimen kohdalla",
  "description": "Hei, kaikki! Tämä paikanvaraajateksti tulisi korvata kuvauksella.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Lisätietoja tiedoista, jotka voidaan määrittää manifest-tiedostossa, löytyy [tästä artikkelista](/docs/reference/addon-manifest/).


## Vaihe 7: Kerro Scratch-lisäosille, mikä lisäosatunnuksesi on
Scratch-lisäosat ei kykene löytämään uusia kansioita itse, joten sinun täytyy lisätä nimi eritystiedostoon.
Siirry `scratchAddonsFolder/addons/addons.json`-tiedostoon ja lisää lisäosasi tunnus taulukkoon.

## Vaihe 8: Testaus
Lisäosasi ei tee mitään tällä hetkellä, joten on hyvä hetki tarkastaa, toimiiko kaikki aiemmin tekemämme.
Siirry `chrome://extensions`-sivulle ja päivitä Scratch-lisäosat napauttamalla päivityskuvaketta sen kortissa.
Napauta Scratch-lisäosien kuvaketta hiiren kakkospainikkeella ja valitse "asetukset".
Lisäosasi pitäisi näkyä luettelossa! Kun olet löytänyt sen, ota se käyttöön ja säädä asetuksia, joita sinulla saattaa olla.

## Vaihe 9: Hauska osuus, koodi!
*Lue vaiheessa 1 linkitetty wikiartikkeli ennen kuin etenet.*

Nyt tulee hauska osuus: luo omat JS- ja CSS-tiedostosi!
Vinkki: Päivitä Scratch-lisäosat-laajennus tehtyäsi muutoksia lisäosaasi, kuten teit vaiheessa 8.

Tutustu nyt wikisivuihin, jotka liittyvät siihen, mitä lisäosasi tekee:
- [Käyttäjäskriptit](/docs/develop/userscripts)
- [Käyttäjätyylit](/docs/develop/userstyles)

## Vaihe 10: Tee lisäosastasi mukautettava
Voit halutessasi tehdä lisäosastasi mukautettavan!
Lisäosasi käyttäjät voivat säätää asetuksia, syöttää numeroita ja muuta!
Aloita lukemalla [lisäosan asetusten ilmoittamisesta manifest-tiedostossa](/docs/reference/addon-manifest/#settings-object).
Suuntaa sitten lukemaan [addon.settings:in ohjetta](/docs/reference/addon-api/addon.settings).

## Vaihe 11: Ennen lisäosan julkaisemista
Nyt kun lisäosasi toimii, varmistetaan, että se voidaan lisätä lisäosakirjastoon.
Varmista, että lisäosasi manifest-tiedosto on kelvollinen. [Lisätietoja täällä](/docs/reference/addon-manifest). Kiinnitä huomiota erityisesti nimeen, kuvaukseen ja lisäosasi tunnisteisiin. Aseta `"enabledByDefault"` arvoon `false` tai poista se.
Varmista, että lisäosasi ei riko muita lisäosia.
Huolehdi, että koodisi on ymmärrettävissä; mieluummin turhia kommentteja kuin ei lainkaan kommentteja.

## Vaihe 12: Lähetä vetopyyntö!
Noudata [osallistujien toimintaohjeissa](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md) kerrottuja vaiheita. Yksinkertaisesti sanottuna haarauta tietosäilö, jos et sitä vielä ole tehnyt, varastoi uusi lisäosasi ja lähetä vetopyyntö!
Muista, että saatamme pyytää sinua tekemään joitain muutoksia. Luultavasti kuitenkin hyväksymme lisäosasi, jos se täyttää vähimmäisvaatimukset.
