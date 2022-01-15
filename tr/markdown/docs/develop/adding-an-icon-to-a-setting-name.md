---
title: Bir Ayar için Simge Ekleme
---
Bir ayara, [çökmeye](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54) [neden olmadan](https://github.com/ScratchAddons/ScratchAddons/pull/1529) bir simge eklemek için

- Simge dosyasının adının kısa çizgi içermediğinden emin olun
- `addon.json` üzerine `@ICONFILENAME.svg setting name` yazın
- Eksikse `/images/icons/` dizinine `ICONFILENAME.svg` ekleyin
- `iconfilenameIcon: "@ICONFILENAME.svg",` eklemek için `/background/load-addon-manifests.js` dosyasını düzenleyin
- Scratch Bildirimci ayarları için `/addons/scratch-notifier/background.js` dosyasını düzenleyin