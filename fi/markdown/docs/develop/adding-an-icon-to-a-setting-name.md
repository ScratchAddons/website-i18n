---
title: Kuvakkeen lisääminen asetuksen nimeen
---
Lisätäksesi kuvakkeen asetuksen nimeen ilman [kaatumisten](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54) [aiheutumista](https://github.com/ScratchAddons/ScratchAddons/pull/1529):

- Varmista, ettei kuvaketiedoston nimi sisällä väliviivoja
- Write `@ICONFILENAME.svg setting name` on `addon.json`
- Add `ICONFILENAME.svg` at `/images/icons/` if missing
- Edit `/background/load-addon-manifests.js` to add `iconfilenameIcon: "@ICONFILENAME.svg",`
- Edit `/addons/scratch-notifier/notifier.js` for Scratch Notifier settings