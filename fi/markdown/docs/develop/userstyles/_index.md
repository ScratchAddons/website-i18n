---
title: Käyttäjätyylit
description: Käyttäjätyylit ovat CSS-sääntöjä, jotka vaikuttavat Scratch-sivuihin. Ne voivat kohdistua joko Scratchissa valmiiksi oleviin elementteihin tai lisäosien sivulle lisäämiin elementteihin.
---

Käyttäjätyylit ovat CSS-sääntöjä, jotka vaikuttavat Scratch-sivuihin. Ne voivat kohdistua joko Scratchissa valmiiksi oleviin elementteihin tai lisäosien sivulle lisäämiin elementteihin.


## Käyttäjätyylien määritteleminen lisäosan manifest-tiedostossa

{{< admonition warning >}}
**Jotkin muutokset vaativat laajennuksen päivittämistä** `chrome://extensions`-sivulla, jotta muutokset, kuten manifest-tiedoston päivitykset, astuvat voimaan.

Kun teet muutoksia olemassa olevaan CSS-käyttäjätyylitiedostoon, sinun ei tarvitse ladata laajennusta uudelleen. Tuolloin pelkkä sivun lataaminen uudelleen riittää.
{{< /admonition >}}

Käyttäjätyylit määritellään "userstyles"-taulukossa, samalla tavalla kuin käyttäjäskriptit.

Jokaisella taulukon kohteella on oltava seuraavat ominaisuudet:
- `"url"`: suhteellinen URL-osoite CSS-tiedostoon
- `"matches"`: luettelo Scratch-sivuista, joilla käyttäjätyyli suoritetaan. Lue lisää [matches-ominaisuuden referenssistä](/docs/reference/addon-manifest/#matches).
- `if`: luettelo ehdoista, jotka voivat muuttaa sitä, onko käyttäjätyyli käytössä vai ei. Lue lisää [user.if-ominaisuuden referenssistä](https://scratchaddons.com/docs/reference/addon-manifest/#if).

Esimerkki manifest-tiedostosta:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "userstyles": [
    {
      "url": "styles.css",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles"]
    },
    {
      "url": "resize.css",
      "matches": ["projects"],
      "if": {
        "settings": {
          "resize": true
        }
      }
    },
  ],
  "settings": [
    {
      "name": "Resize messages",
      "id": "resize",
      "type": "boolean",
      "default": false
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```


## Käyttäjätyylin kytkeminen päälle tai pois sivun latautumisen jälkeen

Yleensä on turha käyttää JavaScript-käyttäjäskriptiä siihen, että ottaa käyttäjätyylin käyttöön tai poistaa sen käytöstä sen mukaan, miten käyttäjä muuttaa asetuksiaan.

- `dynamicEnable: true` -arvon sisällyttäminen lisäosan manifest-tiedostoon antaa laajennuksen lisätä käyttäjätyylejä dynaamisesti, jos lisäosa on otettu käyttöön (ensi kertaa) sivun lataamisen jälkeen.
- `dynamicDisable: true` -arvon sisällyttäminen lisäosan manifest-tiedostoon antaa laajennuksen poistaa tai lisätä uudelleen käyttäjätyylejä dynaamisesti vaatimatta sivua latautumaan uudelleen, jos lisäosa on kytketty päälle tai pois päältä.
- `updateUserstylesOnSettingsChange: true` -arvon sisällyttäminen lisäosan manifest-tiedostoon arvioi käyttäjän asetuksista riippuvat "if"-ehtolauseet uudelleen vaatimatta sivua latautumaan uudelleen. Laajennus poistaa ja lisää käyttäjätyylejä sen mukaisesti.


## Pääsy lisäosan asetuksiin CSS-koodista

Käyttäjätyylit voivat helposti hankkia väri- ja lukuasetuksia CSS-muuttujien avulla. Ne pääsevät käsiksi muidenkin käyttöönotettujen lisäosien asetuksiin.

CSS-muuttujat noudattavat aina `--lisäosanTunniste-asetuksenTunniste`-muotoa. Asetusten tunnisteet muunnetaan aina kebab-case-tyylistä camelCase-tyyliin.

Nämä CSS-muuttujat ovat aina kaikkien lisäosien saatavilla, eikä manifest-arvoja tarvita niiden käyttöön saamiseksi. CSS-muuttujat ja käyttäjän asetukset synkronoituvat lataamatta sivua uudelleen.

```css
.sa-progress-bar {
  /* Väriasetus */
  background-color: var(--progressBar-bgColor);

  /* Väriasetus, jolla on varmistusarvo */
  border-color: var(--editorDarkMode-border, #fc7c24);
  /* Jos editorin tumma tila -lisäosa ei ole käytössä, koodi käyttää muuttujan varmistusarvoa. */

  /* Lukuasetus */
  height: calc(1px * var(--progressBar-height));
}
```


## Omat CSS-muuttujat

Jos käyttäjätyylin täytyy valita kahden arvon väliltä taustavärin (tekstin kontrasti) tai lisäosan asetuksen perusteella, JavaScriptiä ei tarvita. Nämä ehdot, kuten monet muutkin, voidaan määritellä lisäosan manifest-tiedostossa [customCssVariables](/docs/reference/addon-manifest/#customcssvariables)-arvolla, jolloin käyttäjätyyli voi vain viitata määriteltyyn CSS-muuttujaan.


## Tyylien määrittäminen tiettyyn editorin tilaan

Laajennus vaihtaa `<html>`-elementin luokan nimeä automaattisesti, kun käyttäjä siirtyy projektieditoriin tai poistuu siitä.

Esimerkki, jossa `<input>`-elementeille on asettu eri tyylisäännöt editorin sisä- ja ulkopuolelle:
```css
.sa-editor input {
  /* Nämä tyylisäännöt ovat voimassa vain, jos `addon.tab.editorMode` on arvoltaan `editor` tai `fullscreen`. */
}

:root:not(.sa-editor) input {
  /* Nämä tyylisäännöt ovat voimassa vain, jos `addon.tab.editorMode` EI ole arvoltaan `editor` eikä `fullscreen`. */
}
```

Laajennus lisää `.sa-fullscreen`-luokan `<html>`-elementtiin vastaavasti, kun projekti on koko näytön tilassa:
```css
.sa-fullscreen [class*="green-flag_green-flag_"] {
  /* Nämä tyylisäännöt ovat voimassa vain, jos `addon.tab.editorMode` on arvoltaan `fullscreen`. */
}

:root:not(.sa-fullscreen) [class*="green-flag_green-flag_"] {
  /* Nämä tyylisäännöt ovat voimassa vain, jos `addon.tab.editorMode` EI ole arvoltaan `fullscreen`. */
}
```
