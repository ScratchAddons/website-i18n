---
---

**Korkeamman kuvataajuuden tila** on lisäosa, jonka avulla käyttäjä voi kasvattaa projektin suoritusnopeuden haluamakseen.

Tavallisesti Scratch toistaa silmukan 30 kertaa sekunnissa, eli kuvataajuus on 30 ruutua/s (FPS). Tämän lisäosan avulla voi kasvattaa toistojen määrää ja samalla myös kuvataajuutta. Korkeampi kuvataajuus saa projektin animaatiot näyttämään tasaisemmilta mutta myös nopeuttaa niitä. Se, kuinka paljon projekti nopeutuu, on suhteessa valittuun kuvataajuuteen. Jos kuvataajuudeksi on valittu 60 ruutua/s, projekti suoritetaan kaksi kertaa nopeammin.

Jotkin projektit mukautuvat kuvataajuuden muutoksiin [delta-ajan](https://en.wikipedia.org/wiki/Delta_timing) kaltaisten tekniikoiden avulla, jotta ne toimisivat kunnolla ja animaatiot olisivat sujuvia.

Ominaisuuden voi kytkeä päälle tai pois pitämällä `alt` painettuna ja napauttamalla vihreää lippua. Lippu muuttuu siniseksi, ja keltainen pikakelauskuvake ilmestyy sen päälle. Tämä ilmaisee, että projekti suoritetaan nopeammin.

## Ominaisuudet

- Lisäosa on toiminnassa vain silloin, kun käyttäjä aktivoi sen pitämällä `alt`-näppäimen painettuna ja napauttamalla vihreää lippua. Lisäosa ei ole toiminnassa, kun sivu avataan tai kun se ladataan uudelleen.
- Lisäosa toimii sekä projektisivulla että editorissa.
- Lisäosa asettaa projektin kuvataajuudeksi (kun se on aktivoitu) oletusarvoisesti 60 ruutua/s. Kyseisen arvon voi vaihtaa lisäosan asetuksissa kokonaislukuun välillä 31–240.

## Asetukset

### Oma kuvataajuus

Asettaa projektin kuvataajuuden arvon, kun lisäosa on käytössä.

## Tulevaisuuden suunnitelmat

- Lisäosa saatetaan merkitä vaaralliseksi Scratch-verkkosivustolla hillitsemään projekteja, jotka edellyttävät tätä lisäosaa. [#6860](https://github.com/ScratchAddons/ScratchAddons/issues/6860)
- Koska lisäosan käyttö vaatii `alt`-näppäimen painamista, se ei ole yhteensopiva kosketusnäyttölaitteiden kanssa. Ratkaisuksi on ehdotettu pudotusvalikon lisäämistä vihreän lipun viereen tätä ja monia muita lisäosia varten. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230)

## Tekijät

Jeffalo loi alkuperäisen lisäosan, joka vain asetti projektisoittimen kuvataajuudeksi 60 ruutua/s. TheColaber lisäsi mahdollisuuden valita oma kuvataajuus ja korjasi lukuisia bugeja. JoanRiosiPla lisäsi vihreään lippuun helppolukuisen ilmaisimen, ennen kuin WorldLanguages muokkasi sitä.

## Muutosloki

- **v.1.1.0** **Soittimen 60 ruuutua/s -tila** -niminen lisäosa luotiin.
- **v.1.3.0** Lisäosa on nyt oletuksena käytösssä kaikilla käyttäjillä, ja sille annettiin Suositeltava-tunniste.
- **v1.7.0** Mahdollisuus valita oma kuvataajuus lisättiin. Ennen sitä ainut vaihtoehto oli 60.
- **v1.11.0** Lisäosan nimeksi vaihdettiin **Alt+Vihreä lippu 60FPS -soitintila**, ja siihen lisättiin lyhyt tietolaatikko. Omalle kuvataajuudelle lisättiin rajoitus, joka on nykyisin 31–240.
- **v1.13.0** `Alt`-näppäimen ja vihreän lipun yhdistelmän havaitsemiskoodia parannettiin. Nyt lisäosa voidaan kytkeä dynaamisesti päälle ja pois päältä.
- **v1.14.0** Lisäosalle annettiin Projektisoitin-tunniste.
- **v1.18.0** Lisäosan nimeksi vaihdettiin **60FPS-projektisoitintila**. Nyt lisäosa toimii myös upotetuissa projekteissa.
- **v1.24.0** Vika korjattu: Lisäosaa ei enää mene sekaisin siinä, missä tilassa se on, kun siirrytään projektisivulta editoriin.
- **v1.26.0** Vika korjattu: Lisäosa ei enää aiheuta sitä, että muuttujat eivät päivity visuaalisesti joissain tapauksissa.
- **v1.30.0** Lisäosa ei ole enää oletuksena käytössä kaikille käyttäjille.
- **v1.34.0** Saavutettavampi, keltainen pikakelauskuvake lisättiin vihreään lippuun merkiksi siitä, että lisäosa on käytössä. Tietolaatikko kirjoitettiin uudelleen, jotta olisi selvempää, että suurin osa projekteista ei toimi kunnolla, kun lisäosa on käytössä.
- **v1.36.0** Lisäosan nimeksi vaihdettiin **Korkeamman kuvataajuuden tila**. Lisäosan kuvaus ja tietolaatikko kirjoitettiin uudelleen selvyyden vuoksi.
- **v1.37.0** Toinen tietolaatikko lisättiin selittämään ongelmia, jotka liittyvät käyttäjän laitteen virransäästötilaan.

## Nippelitietoa

- Vaikka TurboWarpin lisäosissa ei ole tätä lisäosaa, projektin kuvataajuutta voi säätää samalla tavalla TurboWarpin edistyksellisissä projektiasetuksissa.
- Vaikka lisäosan kuvataajuusasetus on rajattu 31–240 ruutua/s, Scratchin projektisoitin toimii oikein hyvin rajoja pienemmillä ja suuremmilla arvoilla! On lukuisia tapoja näiden rajoitusten kiertämiseen, koska vain asetuksen syötekenttä rajaa arvon.
- Jeffalo lisäsi tämän lisäosan, koska "se on hiton siisti".[^1]
- On olemassa menetelmä, jonka avulla Scratch-projektit voivat karkeasti tunnistaa mukautetun kuvataajuuden, mikä voi viitata siihen, että lisäosa on käytössä.[^2]

## Galleria

{{< docs/stub-section >}}

## Aiheeseen liittyvät

{{< docs/stub-section >}}

[^1]: https://github.com/ScratchAddons/ScratchAddons/pull/383#issue-714126835
[^2]: https://en.scratch-wiki.info/wiki/Making_an_FPS_Counter
