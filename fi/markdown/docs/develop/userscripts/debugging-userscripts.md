---
title: Virheenkorjausvinkkejä
description: Vinkkejä käyttäjäskripteissä esiintyvien vikojen helppoon korjaamiseen ja reunatapauksia huomioon otettaviksi.
---

Vinkkejä käyttäjäskripteissä esiintyvien vikojen helppoon korjaamiseen ja reunatapauksia huomioon otettaviksi.

## Vinkit

### Laajennusta ei aina tarvitse ladata uudelleen

Kun tekee muutoksia olemassa oleviin JavaScript- ja CSS-tiedostoihin, ei tarvitse ladata laajennusta uudelleen `chrome://extensions`-sivulla. Tuolloin pelkkä sivujen lataaminen uudelleen riittää.

### Käytä addon.*-rajapintaa konsolista

`addon`-olioon pääsee käsiksi selaimen konsolista globaalin `__addon`-muuttujan kautta, kun edes yksi lisäosa on käynnissä.

### Aseta keskeytyskohtia "debugger"-avainsanalla

JavaScriptin `debugger`-avainsana pysäyttää sivun suorituksen, kun kehittäjän työkalut ovat auki. Keskeytyskohtien asettaminen on hyödyllistä, kun tarkastellaan paikallisten muuttujien arvoja suorituksen aikana.

### Suodata konsoliviestejä lisäosatunnisteen perusteella

Kirjoita lisäosatunniste konsolin "suodata"-palkkiin, niin näet vain lokikirjauksia, varoituksia ja`console.error()`-funktiolla kirjattuja virheitä . Muista, että tämä piilottaa kaikki poikkeukset, ellet nimenomaan kirjaa niitä koodissasi.


## Reunatapaukset


### Scratchin projektisivu ja projektieditori


#### DOM tuhoutuu, kun käyttäjä siirtyy editoriin tai poistuu sieltä

Scratch luo kaikki HTML-elementit ja tuhoaa vanhat aina, kun käyttäjä napauttaa "katso sisälle"- tai "katso projektisivu" -painiketta.
Tämä voidaan korjata käyttämällä `addon.tab.waitForElement`- tai `urlChange`-tapahtumaa.

#### Scratch-editorin kieltä voidaan vaihtaa lataamatta sivua uudelleen

Toisin kuin Scratchin verkkosivusto Scratch-editori ei lataudu uudelleen käyttäjän vaihtaessa kieltä. Kun käyttäjä valitsee toisen kielen, Scratch saattaa tuhota ja luoda uudelleen joitakin HTML-elementtejä.

#### Muita huomioon otettavia tilanteita

- Projektieditoria voidaan käyttää ilman määriteltyä projektitunnusta (esimerkiksi kun käyttäjä ei ole kirjautunut sisään).
- Editori voi siirtyä LTR-suunnasta RTL-suuntaan (tai toisinpäin) lataamatta sivua uudelleen.


### Scratchin verkkosivusto

#### scratch-www-sivut eivät lataudu uudelleen sisäänkirjautumisen jälkeen

Toisin kuin scratchr2-sivut scratch-www-sivut eivät pakota sivua latautumaan uudelleen sisäänkirjautumisen jälkeen. Jos käyttäjä esimerkiksi siirtyy projektisivulle uloskirjautuneena ja kirjautuu sitten sisään, sivu ei lataudu uudelleen. Samoin toimivat myös studiot, viestisivu jne.
Kaikki Scratch-sivut kuitenkin latautuvat uudelleen uloskirjautumisen jälkeen.

#### Projektisivut eivät ikinä palauta tilakoodia 404

Vaikka projektia ei olisi jaettu tai vaikka sitä ei olisi olemassa, Scratch palauttaa HTTP-tilakoodin 200. Scratch lisää "palvelimemme raaputtaa päätään" -viestin sivulle dynaamisesti.

#### Muita huomioon otettavia tilanteita

- Jokaisella studion neljästä välilehdestä on eri URL-osoite, mutta välilehdeltä toiselle siirtyminen ei käynnistä uuden sivun latautumista. Lisäosat, jotka vaikuttavat johonkin näistä neljästä sivusta, tulee suorittaa riippumatta alkuperäisestä URL-osoitteesta.
