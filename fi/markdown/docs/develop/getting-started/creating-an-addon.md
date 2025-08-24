---
title: Lisäosan luominen
---

Tällä sivulla kuvataan perusteet lisäosan luomisesta Scratch-lisäosiin. Ennen kuin etenet, lue [lisäosien perusteista](../addon-basics/) ja poista käytöstä kaikki Scratch-lisäosien ilmentymät, jotta vältytään ristiriidoilta.

{{< admonition info >}}
Jos ajattelit lähettää kehittämäsi lisäosan vetopyyntönä GitHub-tietosäilöön, lue ensin [osallistujien toimintaohjeet](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md).
{{< /admonition >}}

## Vaatimukset
Scratch-lisäosien kehittämiseen ei vaadita muita tietokoneohjelmia kuin tekstieditori ja Chromium-pohjainen selain (121+). On kuitenkin suositeltavaa, että asennettuna on myös [Git](https://git-scm.com/), [Firefox](https://www.firefox.com/fi/) (121+) ja [Visual Studio Code](https://code.visualstudio.com/).

## Asennus
Asenna laajennus kehitystä varten [Asennus lähdekoodista](/docs/getting-started/installing/#from-source) -sivun ohjeiden mukaan.

## Lisäosakansion luominen
Jokaisella lisäosalla on oma sisäinen nimitunnisteensa, jota käyttävät laajennus ja muut lisäosat.

Lisäosien ei pidä käyttää nimitunnistetta, joka on ollut käytössä vakaassa versiossa, mutta sittemmin poistettu. Niitä ovat:

- `a11y`
- `data-category-tweaks`
- `featured-dangos`
- `fix-buttons`
- `forum-time-zones`
- `image-uploader`
- `redirect-mobile-forums`
- `scratchstats`
- `tutorials-button`

Avaa `addons.json`-tiedosto `addons`-kansiosta. Lisää uuden lisäosan nimitunniste tiedoston loppuosassa olevan `// NEW ADDONS ABOVE THIS ↑↑` -rivin ylle. Luo sitten samanniminen alakansio.

## Lisäosan manifest-tiedosto
Jokaisella lisäosalla on oma [manifest-tiedostonsa](/docs/reference/addon-manifest/), johon on kirjattu, miten lisäosa näytetään asetussivulla, kaikki lisäosan asetukset sekä suoritettavat käyttäjäskriptit tai -tyylit ja sivu, jolla ne suoritetaan.

Jokaisen lisäosan manifest-tiedoston nimi on `addon.json`, ja tiedosto sijaitsee lisäosan kansiossa.
Tässä on tiivistetty lisäosan manifest-tiedosto:
```json
{
  "name": "My addon",
  "description": "TODO",
  "tags": ["community"]
}
```

Lisätietoja tiedoista, jotka voidaan määritellä manifest-tiedostossa, löytyy [lisäosien manifest-tiedoston referenssistä](/docs/reference/addon-manifest/).

Lisäosa ei tee vielä mitään, mutta se näkyy ponnahdusikkunassa ja asetussivulla laajennuksen päivittämisen jälkeen.

## Käyttäjäskriptit ja käyttäjätyylit
[Käyttäjäskriptit](/docs/develop/userscripts/) ja [käyttäjätyylit](/docs/develop/userstyles/) saavat lisäosan toimimaan. Käyttäjäskriptit ajavat JavaScript-koodia ja käyttäjätyylit lisäävät CSS-tyylejä. Lisäosat voivat olla käyttäjätyylien ja -skriptien yhdistelmiä.

Käyttäjäskripteillä on pääsy [addon-rajapintoihin](/docs/reference/addon-api/), joiden avulla ne voivat suorittaa tiettyjä Scratchiin liittyviä tehtäviä helpommin, kuten hakea tällä hetkellä sisäänkirjautuneen käyttäjän.

Kun käyttäjäskripti tai -tyyli lisätään lisäosan kansioon, se täytyy määritellä lisäosan manifest-tiedostossa. Muuten sitä ei suoriteta.

## Lisäosan asetukset
Manifest-tiedoston [settings-olion](/docs/reference/addon-manifest/#settings-object) avulla lisäosalle voidaan lisätä asetuksia, kuten kytkimiä, tekstikenttiä tai värinvalitsimia, jotta käyttäjät voivat mukauttaa sitä asetussivulla.

Lue [addon.settings](/docs/reference/addon-api/addon.settings)-rajapinnan oppaasta, kuinka käyttäjäskripteistä ja -tyyleistä päästään käsiksi käyttäjän valintoihin.

## Ennen osallistumista
{{< admonition info >}}
Jos tietosäilössä ei ole uuteen lisäosaideaasi liittyvää GitHub-seikkaa, luo sellainen. Jos on kuitenkin seikka, joka liittyy ominaisuusideaasi, on suositeltavaa jättää siihen kommentti ilmoittamaan aikeestasi kehittää lisäosa. Tällöin muut osallistujat voivat kertoa, voidaanko lisäosa hyväksyä vai tarvitaanko vielä lisäkeskustelua.

Ota myös huomioon, että GitHubin käyttöehdot edellyttävät, että tilin luova käyttäjä on yli 13-vuotias.
{{< /admonition >}}

Jos haluat lähettää lisäosasi Scratch-lisäosien GitHub-tietosäilöön, jotta se voitaisiin lisätä lisäosakirjastoon, varmista, että se toimii odotetusti muiden lisäosien kanssa ja yksinään eikä se riko muita lisäosia. Lisäosan manifest-tiedostossa on oltava hyvä nimi ja kuvaus, `versionAdded`-kohdassa pitäisi olla laajennuksen seuraava versio ja lisäosan ei pidä olla oletuksena käytössä. Lisäosien tulisi tukea dynaamista käyttöönottoa ja käytöstäpoistoa, mutta sitä ei vaadita. 
Varmista, että koodi on ymmärrettävää: turhat kommentit ovat parempia kuin koodi ilman kommentteja.

## Vetopyynnön lähettäminen
Noudata [osallistujien toimintaohjeissa](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md) kerrottuja vaiheita. Yksinkertaisesti sanottuna haarauta tietosäilö, jos et sitä vielä ole tehnyt, varastoi uusi lisäosasi ja lähetä vetopyyntö.

Jos lisäosasi ei ole valmis tai tarvitset jossakin apua, luo luonnosvetopyyntö.

Muista, että sinua saatetaan pyytää tekemään joitain muutoksia ja tarkastusvaihe saattaa olla hidas. Luultavasti lisäosasi kuitenkin hyväksytään, jos se täyttää vähimmäisvaatimukset.
