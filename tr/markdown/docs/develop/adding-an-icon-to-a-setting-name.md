---
title: Bir Ayar için Simge Ekleme
---
Bir ayara, [çökmeye](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54) [neden olmadan](https://github.com/ScratchAddons/ScratchAddons/pull/1529) bir simge eklemek için

- Simge dosyasının adının kısa çizgi içermediğinden emin olun
- `addon.json` üzerine `@SIMGENINDOSYAADI.svg setting name` yazın
- Eksikse `/images/icons/` dizinine `SIMGENINDOSYAADI.svg` ekleyin
- `iconfilenameIcon: "@SIMGENINDOSYAADI.svg",` eklemek için `/background/load-addon-manifests.js` dosyasını düzenleyin
- Scratch Bildirimcisi ayarları için `/addons/scratch-notifier/notifier.js` dosyasını düzenleyin