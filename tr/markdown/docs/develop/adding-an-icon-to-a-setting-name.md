---
title: Bir Ayar İçin Simge Ekleme
---
Bir ayar adına [neden](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [çöküyor](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54), bir simge eklemek için

- Simge dosyasının adının kısa çizgi içermediğinden emin olun
- `addon.json` üzerine `@ICONFILENAME.svg setting name` yazın
- Eksikse `/images/icons/` dizinine `ICONFILENAME.svg` ekleyin
- `iconfilenameIcon: "@ICONFILENAME.svg",` eklemek için `/background/load-addon-manifests.js` dosyasını düzenleyin
- Scratch Notifier ayarları için `/addons/scratch-notifier/background.js` dosyasını düzenleyin