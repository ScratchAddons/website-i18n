---
---

**Lisää lohkoja nimellä** on lisäosa, jonka avulla käyttäjät voivat koodata nopeammin kirjoittamalla lohkojen nimet ja lisäämällä ne hiiren osoittimen kohdalle. Tämä on helpompi tapa kuin lohkojen etsiminen valikosta. Ponnahdusikkuna avataan napauttamalla hiiren keskipainiketta työtilassa tai käyttämällä näppäinyhdistelmää `ctrl` + `välilyönti`. Tämän jälkeen lohkoja voidaan hakea niiden nimillä ja niitä voidaan raahata hiirellä ulos ponnahdusikkunasta.

## Tausta

Griffpatch teki lisäosan alkuperäisen version Kehittäjän työkalut -laajennusta varten. Tästä lisäosasta tehtiin oma lisäosansa samalla, kun _Kehittäjän työkaluja_ hajotettiin erillisiksi lisäosiksi.

## Ominaisuudet

- Hakutoiminto tukee kaikkia työtilassa olevia lohkoja. Tähän kuuluvat mukautetut lohkot sekä laajennus- ja lista-/muuttujalohkot.
- Lohkoja voidaan lisätä entistäkin nopeammin navigoimalla hakutuloksissa nuolinäppäimillä.
- Kun hakutulos on korostettuna, voidaan haku automaattisesti täyttää vastaamaan kyseistä lohkoa painamalla sarkainta.
- Ponnahdusikkunan avulla voidaan lisätä useita sisäkkäisiä lohkoja samaan aikaan kirjoittamalla esimerkiksi jotakin tällaista "liiku muuttujani + 10 askelta".
- Matematiikkalohkoissa laskutoimitukset järjestellään oletuksen mukaan, mutta järjestystä voidaan muuttaa hakasulkeilla.
- Hakutoiminto voidaan pakottaa olemaan muuttamatta tekstiä lohkoiksi ympäröimällä teksti kaksinkertaisilla lainausmerkeillä. Tästä on hyötyä tilanteissa, joissa yritetään sanoa teksti "x-sijainti" sen sijaan, että sanoittaisiin muuttuja `x-sijainti`, jolloin kirjoitettaisiin "x-sijainti".

## Asetukset

### Ponnahdusikkunan lohkojen koko

Määrittää, kuinka suuria valikon sisällä olevat lohkot ovat. Luku on yksittäisen lohkon korkeus pikseleinä.

### Ponnahdusikkunan leveys

Määrittää, kuinka leveä ponnahdusikkuna on. Luku on prosenttiosuus koko ikkunasta.

### Ponnahdusikkunan enimmäiskorkeus

Määrittää, kuinka pitkä ponnahdusikkuna voi olla, kunnes vierityspalkki tulee näkyviin. Luku on prosenttiosuus koko ikkunan korkeudesta.

## Tulevaisuuden suunnitelmat

- Ponnahdusikkunan koon pitäisi olla muutettavissa editorissa yhtä sen kulmaa raahaamalla sen sijaan, että pitäisi muuttaa asetusta.
- Merkkijonointerpoloinnin lisääminen lainausmerkeissä oleviin merkkijonoihin auttaisi erityisesti tilanteissa, joissa suuri määrä yhdistämislohkoja normaalisti järjestellään ikävällä tavalla.

## Havaitut viat

- Tämän laajennuksen ponnahdusikkunan sisällä olevat lohkot eivät toimi *Mukautettava lohkon muoto* -lisäosan mukaisesti.
- Hakutulosten järjestelemiseen käytetty algoritmi vaatii vielä paljon työstämistä. Toisinaan käyttäjän etsimät tulokset ovat piilossa lukuisten huonojen tulosten alla.

## Tekijät

Tacodiva teki suurimman osan nykyisin toiminnassa olevasta lisäosasta. Lisäksi Griffpatch auttoi paljon antamalla palautetta ja etsimällä bugeja uudistetusta versiosta.

## Muutosloki

{{< docs/outdated-section >}}

- **v1.30.0** Lisää lohkoja nimellä -lisäosa luotiin.
- **v1.31.0** Lisäosa uudistettiin täysin, ja sisäkkäisten lohkojen hakeminen, automaattinen täyttö ja ponnahdusikkunan lohkojen ulkonäön muuttaminen tehtiin mahdolliseksi.
- **v1.31.1** Hakualgoritmia muutettiin ja monia bugeja korjattiin.

## Nippelitietoa

- Ensimmäinen lisäosaoppaan sivu kirjoitettiin tästä lisäosasta!
- Hiiren keskipainikkeella avautuva ponnahdusikkuna on yksi Scratch-lisäosien vanhimmista ominaisuuksista. Vaikka siitä tehtiin vasta hiljattain oma lisäosansa, se oli alusta asti osa kehittäjän työkaluja.
- Griffpatch teki ponnahdusikkunan alkuperäisen koodin vuonna 2019 eli ennen kuin Scratch-lisäosat edes oli olemassa.
- Kun Tacodiva uudisti lisäosan versioon 1.31.0, koodiin oli lisätty miltei 2 800 riviä koodia ja tehty 149 pysyvää muutosta!
- Uudistuksen Git-haaran nimi oli `idk-what-im-doing` (suomeksi "en tiedä mitä teen").
- Tacodivalla oli vaikeuksia erään ongelman korjaamisessa, joten huolimatta siitä, että CST1229 korjasi ongelman kirjoittamalla vain kaksi riviä CSS-koodia, hänenkin nimensä mainitaan lisäosan tekijöiden joukossa!

## Galleria

{{< docs/stub-section >}}

## Aiheeseen liittyvät

{{< docs/stub-section >}}
