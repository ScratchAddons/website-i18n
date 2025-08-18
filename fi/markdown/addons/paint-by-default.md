---
---

**Piirrä asuste oletuksena** on lisäosa, joka muuttaa uuden hahmon, asuteen, taustan ja äänen lisäyspainikkeen toimintaa. Tavallisesti Scratch avaa resurssikirjaston, kun painiketta napautetaan. Tämän lisäosan avulla oletustoimintoa voidaan muuttaa lisäosan asetuksissa, jossa vaihtoehtoina ovat: kirjaston avaaminen (Scratchin oletus), piirtäminen tai äänitys, yllätys sekä oman tiedoston lataaminen.

## Tausta

Tämä lisäosa luotiin ajatellen sitä, että keskitason ja edistyneen tason scratchaajat käyttävät Scratchin resurssikirjaston resursseja vain harvoin. Näille käyttäjille on tavallista luoda uusi hahmo/asuste/tausta viemällä hiiri lisäyspainikkeen päälle ja sitten valitsemalla Piirrä-toiminto. Koska se vie aikaa, lisäosan oletusasetus vaihtaa lisäyspainikkeiden oletustoiminnoksi piirtoeditorin avaamisen eikä resurssikirjaston avaamista.

## Ominaisuudet

- Käyttäjä voi valita lisäosan asetuksista oletustoiminnon jokaiselle seuraavista painikkeista: "Valitse hahmo", "Valitse asuste", "Valitse tausta" ja "Valitse ääni".
- Jokaisella yllä olevista painikkeista on seuraavat neljä asetusvaihtoehtoa, jotka on saatu luettelosta, joka avautuu, kun hiiri viedään painikkeen päälle:
  - Kirjasto: Avaa Scratchin hahmo-, asuste-, tausta- tai äänikirjaston, riippuen siitä, mitä painiketta painetaan. (Scratchin oletus)
  - Piirrä/äänitä: Avaa heti asuste-editorin. Avaa äänitystyökalun "Valitse ääni" -painiketta napautettaessa.
  - Yllätä: Valitsee satunnaisen resurssin Scratchin hahmo-, asuste-, tausta- tai äänikirjastosta.
  - Lataa: Käyttäjä lataa haluamansa tiedoston.
- Vihjeteksti, joka näkyy, kun hiiri viedään lisäyspainikkeen päälle, näyttää myös oikean oletustoiminnon.

## Asetukset

### Lisää hahmo

- Asettaa hahmoruudun oikeassa alukulmassa olevan "Valitse hahmo" -painikkeen oletustoiminnon.

### Lisää asuste

- Asettaa asuste-editorin asusteluettelon alaosassa olevan "Valitse asuste" -painikkeen oletustoiminnon.

### Lisää tausta

- Asettaa esiintymislavan asuste-editorin taustaluettelon ja taustaruudun alaosassa olevan "Valitse tausta" -painikkeen oletustoiminnon.

### Lisää ääni

- Asettaa äänieditorin ääniluettelon alaosassa olevan "Valitse ääni" -painikkeen oletustoiminnon.

## Havaitut viat

- Painikkeen oletustoiminnoksi ei voi asettaa minkään Scratchin lisäosan lisäämää toimintoa. Sellainen on esimerkiksi _HD-kuvien lataaminen_ -lisäosan lisäämä "HD-lataus"-toiminto.
- Lisäosan nimi "Piirrä asuste oletuksena" ei kuvaa sen mahdollisuuksia vaihtaa sekä hahmo-, tausta- että äänipainikkeen toimintoja. Tätä ongelmaa ei päätetty ratkaista. [#6076](https://github.com/ScratchAddons/ScratchAddons/issues/6076)

## Tekijät

GarboMuffin kehitti lisäosan kokonaisuudessaan. WorldLanguages keksi sen lopullisen nimen, kirjoitti kuvauksen, lisäsi asetukset ja tunnisteet.

## Muutosloki

- **v1.19.0** **Piirrä asuste oletuksena** -lisäosa luotiin.
- **v1.19.1** Vika korjattu: Lisäosa ei enää kohtele "Valitse ääni" -painiketta "Valitse asuste" -painikkeen tavoin, jos valitulla hahmolla ei ole ääniä.

## Nippelitietoa

{{< docs/stub-section >}}

## Galleria

{{< docs/stub-section >}}

## Aiheeseen liittyvät

- [Alkuperäinen vetopyyntö (numero 3199)](https://github.com/ScratchAddons/ScratchAddons/pull/3199)
