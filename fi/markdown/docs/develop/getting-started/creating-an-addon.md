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
Käsitätkö?

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

Here comes the fun part: create your own JS or CSS files!  
Protip: after making any change to your addon, make sure to refresh the Scratch Addons extension like you did in step 8.  

Depending on what you want your addon to do, you should now check these wiki pages:
- [Userscripts](/docs/develop/userscripts)
- [Userstyles](/docs/develop/userstyles)

## Step 10: Make your addon customizable
If you want, you can make your addon customizable!  
Users of your addon will be able to toggle settings, enter numbers, and more!  
To get started, see [how to declare settings in the addon manifest](/docs/reference/addon-manifest/#settings-object).  
Then, head to the [addon.settings documentation](/docs/reference/addon-api/addon.settings) to learn how to access user choices from userscripts.

## Step 11: Before publishing your addon
Now that your addon works, let's make sure we can add it to the addon library.  
Make sure your addon's manifest is suitable, [more info here](/docs/reference/addon-manifest). Keep close attention to the name, description and tags of your addon. Make sure to set `"enabledByDefault"` to `false` or remove it.  
Make sure your addon doesn't break other addons.  
Make sure your code is understandable; having unnecessary comments is better than no comments.

## Step 12: Send a pull request!
Follow the steps on our [contributing guidelines](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Simply put, fork the repo if you haven't already, commit your new addon and send a PR!  
Keep in mind we might request you to make some changes, however, we will probably accept your addon as long as it's minimally suitable.
