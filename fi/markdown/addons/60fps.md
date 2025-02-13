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
- Because enabling the addon requires holding the `alt` key, it is not compatible with touchscreen devices. A proposed solution is to add a context menu to the green flag for this addon and several others. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230)

## Tekijät

Jeffalo created the original addon that only set the project player to 60 FPS. TheColaber added the custom FPS setting and various other bug fixes. The accessible green flag indicator was created by JoanRiosiPla before being tweaked by WorldLanguages.

## Muutosloki

- **v1.1.0** The **60FPS Player Mode** addon was created.
- **v1.3.0** The addon is now enabled by default for all users, and was given the Recommended tag.
- **v1.7.0** Option added to customize the target FPS, which was locked to 60 before.
- **v1.11.0** The addon was renamed to **Alt+GreenFlag 60FPS player mode**, and a brief information box was added. A limit was set on the custom FPS, which now ranges from 31 to 240.
- **v1.13.0** `Alt` + green flag click detection was improved. The addon can now be dynamically enabled and disabled.
- **v1.14.0** The addon was given the Project Player tag.
- **v1.18.0** The addon was renamed to **60FPS project player mode**. The addon can now run in project embeds.
- **v1.24.0** Bug fix: The addon no longer loses track of state when changing from project page to editor.
- **v1.26.0** Bug fix: The addon no longer causes variables to not visually update in some cases.
- **v1.30.0** The addon is no longer enabled by default for all users.
- **v1.34.0** A more accessible yellow fast-forward icon was added to the green flag indicator whenever the addon is toggled on. Information box was rewritten to clarify that most projects will not behave properly when addon is enabled.
- **v1.36.0** The addon was renamed to **Higher project framerate mode**. The addon's description and information box was rewritten for clarity.
- **v1.37.0** A second information box was added that explains issues with user devices' power saving mode.

## Nippelitietoa

- Although TurboWarp Addons does not have this addon, Turbowarp's advanced project settings allows you to customize the project's framerate in a similar way.
- Despite the addon's setting for customizing the FPS is limited from 31 to 240, the Scratch project player is perfectly fine with values both lower and higher than these limits! There are several ways to bypass this limit, as only the setting's input field sets the limit.
- Jeffalo added the addon because "its hecking cool"[^1]
- There is a method that allows Scratch projects to roughly detect a custom FPS, which may indicate that the addon is enabled.[^2]

## Galleria

{{< docs/stub-section >}}

## Aiheeseen liittyvät

{{< docs/stub-section >}}

[^1]: https://github.com/ScratchAddons/ScratchAddons/pull/383#issue-714126835
[^2]: https://en.scratch-wiki.info/wiki/Making_an_FPS_Counter
