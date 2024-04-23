---
title: Kuvakkeen lisääminen asetuksen nimeen
---
Lisätäksesi kuvakkeen asetuksen nimeen ilman [kaatumisten](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54) [aiheutumista](https://github.com/ScratchAddons/ScratchAddons/pull/1529):

- Varmista, ettei kuvaketiedoston nimi sisällä väliviivoja
- Kirjoita `@KUVAKETIEDOSTONNIMI.svg setting name` `addon.json'`-tiedostoon
- Lisää `KUVAKETIEDOSTONNIMI.svg` `/images/icons/`-kohtaan, jos se puuttuu 
- Muokkaa `/background/load-addon-manifests.js`-tiedostoa ja lisää `iconfilenameIcon: "@KUVAKETIEDOSTONNIMI.svg",`
- Muokkaa Scratch-ilmoitusten asetuksia `/addons/scratch-notifier/notifier.js`-tiedostossa.