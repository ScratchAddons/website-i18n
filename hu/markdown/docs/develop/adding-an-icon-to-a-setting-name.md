---
title: Ikon hozzáadása egy beállítás nevéhez
---
Hogy hozzáadj egy ikont egy beállítás nevéhez anélkül, hogy az [összeomlásokat](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54) [idézne elő](https://github.com/ScratchAddons/ScratchAddons/pull/1529)

- Győződjön meg róla, hogy az ikon fájlneve nem tartalmaz kötőjeleket
- Írja be a következőt: `@ICONFILENAME.svg setting name` az `addon.json` fájlba
- Add hozzá ide, ha hiányozna: `/images/icons/` a következőt: `IKONFÁJLNEVE.svg`
- Szerkessze a `/background/load-addon-manifests.js`-t, hogy hozzáadja a következőt: `iconfilenameIcon: "@ICONFILENAME.svg",`
- Szerkessze a `/addons/scratch-notifier/notifier.js`-t a Scratch Értesítő beállításaihoz.